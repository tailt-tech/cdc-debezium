# cdc-debezium
## 1. File docker compose.yaml
## 2. Setup drive mysql connect debezium
 ### 2.1  Install plugins
        Example: mkdir plugins
        cd plugins
        wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-mysql/2.3.0.Final/debezium-connector-mysql-2.3.0.Final-plugin.tar.gz
        tar -xvzf debezium-connector-mysql-2.3.0.Final-plugin.tar.gz
        rm debezium-connector-mysql-2.3.0.Final-plugin.tar.gz
     
## 3. Run docker compose and test:
    curl -X POST -H "Accept:application/json" -H "Content-Type:application/json" localhost:8083/connectors/ -d @register-mysql.json


### Note: Enable CDC in MySQL to read binlog (Required for user of debezium)
    SET GLOBAL binlog_format = 'ROW';
    SET GLOBAL binlog_row_image = 'FULL';
    GRANT SELECT, RELOAD, SHOW DATABASES, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'debezium'@'%';
    FLUSH PRIVILEGES;