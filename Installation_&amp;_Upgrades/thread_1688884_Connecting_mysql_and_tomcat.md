---
title: "Connecting mysql and tomcat"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by srijith_bhandary on 2011-02-15
Hi I am new to tomcat and mysql. 

I have installed Tomcat and mysql and both are working great!!

But now I have task of connecting mysql and tomcat. 
I dont have any idea on this. However I looked some manuals but did not find any luck. 

Guy, Please give me the step by step procedure on how to connect mysql with tomcat. 

btw I have downloaded  mysql connector and copied the .jar file to $CATALINA_HOME/lib 

What else should I do ? 
Thanks!

---

### Post by srijith_bhandary on 2011-02-16
This is the steps I followed to install tomcat  [http://www.linuxnix.com/2010/12/how-to-install-apache-tomcat-on-linuxredhatubuntu.html](http://www.linuxnix.com/2010/12/how-to-install-apache-tomcat-on-linuxredhatubuntu.html)      and I installed mysql server and client using the commands sudo  apt-get install mysql-server mysql-client   later I downloaded JDBC  Driver for MySQL (Connector/J)  from [http://www.mysql.com/products/connector/](http://www.mysql.com/products/connector/)   and extrated it and pasted the .jar fille in /opt/apache-tomcat-6.0.29/lib ( I  dont have $CATALINA_HOME/common/lib) . My questions are  1) Is the  connection between tomcat and sql established ?  2) do i need to install  mysql-server when I have tomcat server ?

---

### Post by lykeion on 2011-02-16
You can install JDBC driver for MySQL from Ubuntu repositories:
```
sudo apt-get install libmysql-java
```
Then add the jar-file /usr/share/java/mysql.jar to classpath in ~/.bashrc, see: [https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)
And possibly add this to your Tomcat startup script $CATALINA_HOME/bin/startup.sh as well.

---

### Post by srijith_bhandary on 2011-02-17
Hi thanks for the help.
I did what you said and everything finished great! 

I then executed the java script to test ( in the link that you have mentioned) with username as root  and with password 

when I enter 
$javac DBDemo.java 

It gave me this error 

[I]DBDemo.java:4: error while writing DBDemo: DBDemo.class (Permission denied)
public class DBDemo
       ^
1 error[/I]

So I did 
$sudo javac DBDemo.java   and it worked 

but I get the following error when I do  $java DBDemo 
com.mysql.jdbc.Driver
Exception in thread "main" java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at DBDemo.main(DBDemo.java:22)

---

### Post by lykeion on 2011-02-17
The ClassNotFoundException means it the JDBC driver is not in the classpath.

1. Login to mysql as root user (if it's first time just press enter when prompted for password)
```
mysql -u root -p
```
2. Create the database
```
create database emotherearth;
```
3. Change database
```
use emotherearth;
```
4. Create a user and grant privileges to database
```
grant all privileges on emotherearth to paulr@localhost identified by "paulr";
```
5. Logout
```
quit;
```

6. Add JDBC driver to classpath
```
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATH
```

7. Create the java file DBDemo.java (paste the contents from the [JDBCAndMySQL]("https://help.ubuntu.com/community/JDBCAndMySQL") page)

8. Compile it
```
javac DBDemo.java
```

9. Run it (if everything is okay it should display "It works !")
```
java DBDemo
```


You shouldn't need sudo privileges to access javac. It may be something strange you've done when installing JDK.
Could you please post the output of this command:
```
sudo update-java-alternatives -l
```

---

