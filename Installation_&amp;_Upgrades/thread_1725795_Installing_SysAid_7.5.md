---
title: "Installing SysAid 7.5"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-04-10
Hello,

I recently installed the SysAid 7.5 "free" version on my Laptop which has both LAMP and Tomcat6.  I correctly created the MySql database, and verified that I could login from the terminal; however, when I executed the install script "init-sysaid.sh" after deploying the ".war" file to "webapps" I received the following errors:

sophie@sophie-laptop:~/Downloads/sysaid-server-linux$ ./init-sysaid.sh '/var/lib/tomcat6/webapps/sysaid' 
Welcome to the SysAid initialization script!
This script will configure the database connection and initialize the database.
Please enter the host name or IP address of the MySQL server [localhost]:
localhost
Please enter the database name that should contain the SysAid data (please create an empty database with this name) [ilient]:
sysaid
Please enter the database login user name [mysql]:
sysaid_user
Please enter the database login password [mysql]:
xxxxxxxxxxxxx
Please confirm your input:
Host name: localhost
Database name: sysaid
Database user name: sysaid_user
Database password: xxxxxxxxxxxxx
Would you like to proceed (y/n) ?
y
Would you like to check connection (y/n) ?
n
log4j:WARN No appenders could be found for logger (com.ilient).
log4j:WARN Please initialize the log4j system properly.
Error on defining operating time appender appender logger.java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/logs/OperatingHours.log (Permission denied)
Error on defining operating time appender appender logger.java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/logs/DBImpl.log (Permission denied)
2011-04-10 09:44:08.276 GMT Thread[main,5,main] java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/db/derby.log (Permission denied)
2011-04-10 09:44:08.996 GMT : Apache Derby Network Server - 10.5.3.0 - (802917) started and ready to accept connections on port 1527
Validating license .....
log4j:WARN No appenders could be found for logger (com.ilient).
log4j:WARN Please initialize the log4j system properly.
Error on defining operating time appender appender logger.java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/logs/OperatingHours.log (Permission denied)
Error on defining operating time appender appender logger.java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/logs/DBImpl.log (Permission denied)
2011-04-10 09:44:11.423 GMT Thread[main,5,main] java.io.FileNotFoundException: /var/lib/tomcat6/webapps/sysaid/WEB-INF/db/derby.log (Permission denied)
2011-04-10 09:44:11.630 GMT : Apache Derby Network Server - 10.5.3.0 - (802917) started and ready to accept connections on port 1527
cat: /var/lib/tomcat6/webapps/sysaid/WEB-INF/logs/checklic.log: No such file or directory
FATAL: 
sophie@sophie-laptop:~/Downloads/sysaid-server-linux$ 


It certainly appears that SysAid is not connecting to the MySql server, and is using the native "Derby" database instead.  However, it allows me to login and navigate.  As far as I can tell it's running; but how "well" it's running I'm not quite sure.

Can anyone tell me what the error messages above mean and what I need to do about them, if anything?


Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-13
Hi,

I finally heard back from SysAid's technical support, and they we're clueless...  They did however confirm my suspicion, that I was not able to connect to the MySQL database during the installation.  The 'tech' that handled my support-request recommended that I use 'root' as the database-usename, instead of the actual database-username that I created when I created the MySQL database for SysAid, so that the install script would inherit root priveleges.  Obviously, his understanding of MySQL was flawed, as was his advice.  This did, however, motivate me to run the install script with 'superuser' priveleges.

Here's the command I entered:

sophie@sophie-laptop:~/Downloads/sysaid-server-linux$ ***sudo ./init-sysaid.sh***

This, indeed, did-the-trick.  SysAid's documentation, meaning the *INSTALL.txt* file, does 'not' even suggest this.

I was then able to connect to the MySQL database and complete the installation, without receiving any error messages.  The script even prompted me to create an admin usename and password, which it didn't do previously.  

The script did however 'kill' my ***'Tomcat6'  ***installation. It refused to run after several restarts and a reboot; so I reinstalled the entire Tomcat6 stack, from the repositories, and was back 'running' again.  I was then able to login to SysAid at:

***[http://localhost:8080/sysaid/](http://localhost:8080/sysaid/)***

and the ap functioned correctly.

BTW, inintially, I was very worried that installing a Tomcat6 server on top of an Apache server, would kill my Apache installation.  Fortunately, it did not.  In fact, it appears that, the two don't interact at all.  Also, in fact, they have different *'webroots.'*  The Tomcat6 webroot, if you install from the repositories, like I did, will be:

***/var/lib/tomcat6/webapps/***

And the Apache webroot is located at:

***/var/www/***


Also, another article, I located in this forum, recommends 'not' to use Tomcat6 from the repositories, and instead recommends building from source.  I found this 'not' to be necessary.  Before downloading the source-code, I checked the version in the repositories, and it was the latest one; so I just went ahead and installed it. It's working fine.  I suspect that at the time that post was written, there were indeed problems with the version in the repositories.  This, now, appears to no longer be the case.  And by checking the repositories, I mean checing the version in ***"Synaptic Package Manager."***  If these are not the same, someone please correct me.



Hannibal):P

P.S., I've attached a screenshot of the successful SysAid installation, so you can see what it's supposed to look like, after you login.

---

