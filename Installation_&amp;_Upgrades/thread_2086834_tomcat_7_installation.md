---
title: "tomcat 7 installation"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by 333ameeth on 2012-11-22
Hi,
I recently upgraded to ubuntu 12.04LTS,
and installing tomcat 7 but got following errors 
    
root@me:/# sudo apt-get install tomcat7 tomcat7-docs tomcat7-examples tomcat7-admin -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tomcat7 : Depends: tomcat7-common (>= 7.0.26-1ubuntu1.1) but it is not going to be installed
 tomcat7-admin : Depends: tomcat7-common (>= 7.0.26-1ubuntu1.1) but it is not going to be installed
 tomcat7-docs : Depends: tomcat7-common (>= 7.0.26-1ubuntu1.1) but it is not going to be installed
 tomcat7-examples : Depends: tomcat7-common (>= 7.0.26-1ubuntu1.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

pleas help me to solve this problem,
thank you.

---

### Post by 333ameeth on 2012-11-22
need to remove tomcat6-common before installing tomcat7 due to some conflict.

See [http://askubuntu.com/questions/173981/installing-tomcat-7-on-ubuntu-server-12-04](http://askubuntu.com/questions/173981/installing-tomcat-7-on-ubuntu-server-12-04).

---

