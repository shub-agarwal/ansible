# ansible

Install FirewallD

sudo yum install -y firewalld
sudo service firewalld start
sudo systemctl enable firewalld

nstall MariaDB

sudo yum install -y mariadb-server
sudo vi /etc/my.cnf
sudo service mariadb start
sudo systemctl enable mariadb

Configure firewall for Database

sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload

Configure Database
$ mysql
MariaDB > CREATE DATABASE ecomdb;
MariaDB > CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';
MariaDB > GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';
MariaDB > FLUSH PRIVILEGES;

mysql < db-load-script.sql
Install required packages
sudo yum install -y httpd php php-mysql
sudo firewall-cmd --permanent --zone=public --add-port=443/tcp
sudo firewall-cmd --reload
Start httpd
sudo service httpd start
sudo systemctl enable httpd
curl http://localhost
