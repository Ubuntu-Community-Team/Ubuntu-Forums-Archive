---
title: "Apache2 mysql-server php5 Database error"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by arturo322 on 2011-11-07
I've Installed these applications by doing

sudo su
Password: ********
apt-get update
apt-get upgrade
apt-get install apache2 mysql-server mysql-client php5


after installation

i tried typing localhost on my browser it printed
IT WORKS!

so assuming everything was right i copied my sourced codes on /var/www/Mysourcecodes
when i opened it by typing /localhost/Mysourcecodes it gives me a blank screen. i searched the internet for possible errors it's said that its a mysql error on php so i removed my sourcecode for connecting to the database server and retyped localhost/Mysourcecodes and yeah my expected page popped out BUT it cannot connect to the database since i removed my sourcecode



here is the source code i made

Conn.php
<?php 
 
$HOST = "localhost"; 
$USER = "root"; 
$DBUSERPASS = "pass"; 
$DBNAME= "dbname"; 
 
$connect= mysql_connect($HOST,$USER,$DBUSERPASS); 
 
if(isset($connect)){ 
    $dbselect = mysql_select_db($DBNAME,$connect); 
    if(isset($dbselect)){} 
    else echo "Invalid Database Name"; 
}else echo "Cannot Connect to Database"; 
?>



Heres how i called the connection file.

sample.php
<?php 
include("db/conn.php"); 
session_start(); 
?>

---

