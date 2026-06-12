---
title: "tomcat"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by zabi_ulla on 2007-11-16
hello there.can anyone tell me how to install tomcat(jdk) on ubuntu 7.04??

---

### Post by sgordon on 2007-11-18
Well, here's some initial steps to get you going. This should work in Feisty. Please let me know how it goes, I'm trying to make a general guide for more people!

1) First, the usual general system updates!
sudo apt-get update
sudo apt-get install

2) Now install the latest Java 6 from Sun (recommended, other JDK/JRE should work too)
sudo apt-get install sun-java6-jdk
(has dependancies, accept them)

sudo update-java-alternatives -s java-6-sun
(this tells ubuntu to use the new package for common commands like 'java' and 'javac'. You will get some warnings about browser plugins like firefox etc, don't worry)

3) Quick check that the last commands went ok
javac -version
java -version
(both should output the version as being 1.6. Sometimes Java 6 is Java 1.6. Bit confusing!)

4) Ok, actually install Tomcat. We'll get some example webapps as well, just to test what we have
sudo apt-get install tomcat5.5-webapps tomcat5.5
sudo /etc/init.d/tomcat5.5 start

5) Check that tomcat is running
(wait a few seconds after the 'start' above)
netstat -an | grep 8180

Should show port :8180 as LISTENing

6) Give it a try. In your favourite web browser, try:
[http://localhost:8180/tomcat-docs/](http://localhost:8180/tomcat-docs/)

Hope that works for you! Any queries on this or next steps, let me know!

  Si

---

### Post by everk on 2008-01-13
Hi,
 I'am having a confusing problem with the tomcat5.5 installation on my Gutsy-Box (AMD2-64). I have installed Java 1.6.0-03-b05 and Tomcat5.5. After configuring the user/role database file tomcat-users.xml. All seems to work fine. All the applications that came with the installation of tomcat-webapps seem to work fine. 
However, I run into troubles, when I tried to install an Tomcat web application that works fine in a comparable Windows environment. The jasper exception: 
org.apache.jasper.JasperException: Could not initialize class org.apache.jasper.runtime.BodyContentImpl 
suggested the something was wrong with my JAVA_HOME settings. After consulting several forums I tried several solution. My major problem is I don't know where JAVA_HOME is. The suggestion to uncomment the line #JAVA_HOME=/usr/lib/jvm/java-6-sun in /etc/default/tomcat5.5 had, after a restart of tomcat, the effect that none of the web-application ran anymore. The same holds for uncommenting the line containing CATALINA_HOME. Can anyone give my a clue how to continue ?

Thanx

---

### Post by KombOver on 2008-01-23
SGordon - Thank you for concise & accurate instructions.  I followed them precisely and I had Java and Tomcat running in 5 minutes.   You saved me a bunch of time.

---

### Post by ufis on 2008-01-24
So after installing tomcat like this: Where do I deploy my projects to?

---

### Post by nikkkko on 2008-02-20
Installed successfully on ubuntu and kubuntu following sgordon's straightforward guide. Many thanks!

---

### Post by fedo on 2008-04-20
If someone find the same problem that everk maybe this can help.

There are some security issues that ubuntu setup when you are running tomcat as daemon. 
To fix this edit  /etc/tomcat5.5/policy.d/50user.policy 

sudo nano /etc/tomcat5.5/policy.d/50user.policy

and add this to teh file:

grant codeBase "file:/var/lib/tomcat5.5/webapps/mi-aplicacion-web/-" {
     permission java.security.AllPermission;
     permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve";
     permission java.net.SocketPermission "*.noaa.gov:80", "connect";
     permission java.io.FilePermission "/var/lib/tomcat5.5/webapps/mi-aplicacion-web/WEB-INF/logs-", "read,write,delete";
};

---

