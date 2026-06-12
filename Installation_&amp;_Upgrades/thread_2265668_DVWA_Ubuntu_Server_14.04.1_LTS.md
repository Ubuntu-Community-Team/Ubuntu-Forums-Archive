---
title: "DVWA Ubuntu Server 14.04.1 LTS"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by CrAzY12 on 2015-02-16
I am installing DVWA on a ubuntu server, everything is up and running but it seems like when I try to create my database set up DVWA has failed to connect to the database. My first thought; mysql is not running but it is is and I have checked the config file: Please see attachments to better explain the problem I am having. 

Attachment 1: Screenshot of Ubuntu Server config file and status of mysql
Attachment 2: Screenshot of the DVWA "could not connect to the database-please check the config file" 

I am looking into the config file and the only think I changed was '10.10.20.100', it set to 'localhost' before.. still had the same problem. Any suggestions is greatly appreciated!

---

### Post by MAFoElffen on 2015-02-17
Hopefully a Mod comes along to move this to the server section, but...

If you check the default file at /htdocs/dvwa/config/config.inc.php you should see something simular to this:
```

$_DVWA[ 'db_server' ] = 'localhost';


$_DVWA[ 'db_database' ] = 'dvwa';


$_DVWA[ 'db_user' ] = 'root';


$_DVWA[ 'db_password' ] = '[COLOR=#ff0000]p@ssw0rd'[/COLOR];

```
That file sets the default vars for DVWA, one of which (the last) is where you tell DVWA what to use as the dB password. Where indicated above in red, you should replace that to what your MySQL database password is... That should resolve your permissions refusal issue. 

If you didn't set that up yet, then you get that error. ...And from your first posted picture, I can see it is still set to the install default, instead of anything changed... (no need to post your db password here)

---

### Post by CrAzY12 on 2015-02-17
I just found out running apache2 & xampp is a conflict between the two but anyways I have changed the .php script to my respective mysql password and still received the same error on the client-side:

> "could not connect to the database - please check the config file" 

So obviously the problem is in the config file. And I am pretty sure it is having trouble connecting to mysql (I have verified my credentials to log into mysql is the same as the config file.). 

Maybe the problems resides in the setup.php script? The screenshot I took of the setup.php script might help out?? 

Any other troubleshooting ideas I could look into?

---

### Post by MAFoElffen on 2015-02-17
Make sure your db is listening on the correct port
```

netstat -vln

```
Look for listening on port 3306

Then look at your /etc/mysql/my.cnf file and ensure that your bind address is set to what you have as $_DVWA[ 'db_server' ] in your  /htdocs/dvwa/config/config.inc.php file... you have yours set to 10.10.20.100... at least in your DVWA config file. Can you connect from a MySql client on your local net using that IP address? Note: the reason the defualt was local, is that you don't want that on a public IP. (Permissions if Local, would be if local, the webpages, via your php scripts could connect to the db. Outside users only have access to the pages, via the public IP.)

---

### Post by CrAzY12 on 2015-02-18
Yes my bind address is set to localhost and port 3306 is listening on the localhost as well. Should I change my.cnf at the bind address = localhost to bind address =10.10.20.100? 

I can see what I did wrong. I might have changed my DVWA inc.php script to be at 10.10.20.100 but I did not change mysql bind address to 10.10.20.100 and would cause a datebase connection error corect?
( I have a malware lab set up) So this is not a public facing Ip address.

---

