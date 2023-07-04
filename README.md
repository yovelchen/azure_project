# azure_project
[Module 07 - Azure Project.pdf](https://github.com/yovelchen/azure_project/files/11929569/Module.07.-.Azure.Project.pdf)

steps db: 

install postgres:
1.sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
2. wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
3. sudo apt-get update
4. sudo apt-get -y install postgresql

create user: 
1. sudo -i -u postgres
2. ALTER USER postgres PASSWORD 'PASSWORD';
3. \q

enable remote connection: 
1. ss -nlt >> ADDRESS:PORT
2. sudo find / -name "postgresql.conf"
3. sudo vi /etc/postgresql/15/main/postgresql.conf >> change #listen_addresses = 'localhost' to listen_addresses = '*' 
3. sudo systemctl restart postgresql
4. ss -nlt >> * 

allow client connections to all databases:
1. sudo vi /etc/postgresql/14/main/pg_hba.conf >> add line at the end of the file:
"#Allow client connections to all data bases and users 
host    all          all            0.0.0.0/0  md5"

steps web: 
1. sudo apt-get install postgresql-client
2. psql -h 10.0.2.4 -U postgres
3. mkdir flaskApp 
4. cd flaskApp 
5. create vim azureApp.py >> file azureApp.py 
6. pip install psycopg2-binary
7. python3 azureApp.py

credits:
1. (https://devopscube.com/install-postgresql-on-ubuntu/)
