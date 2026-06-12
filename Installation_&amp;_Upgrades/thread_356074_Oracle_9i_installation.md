---
title: "Oracle 9i installation"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by nikgaapu on 2007-02-08
Hi all,
 if anyone could help me in installing oracle 9i on ubuntu i would really appreciate it.

thanks

---

### Post by Man_Jide on 2007-02-13
*Hello the following procedure was taken from the general information on how to install "Edgy"*
 How to install Oracle Database XE

    * Read #How to add extra repositories
    * Read [http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html) 

    * Add the following repository to your /etc/apt/sources.list: 

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

    * Install the software using apt-get 

sudo apt-get update
sudo apt-get install oracle-xe

    * Add your login to the 'dba' group (where your login name is username) 
[I]
Best regards,

Man_Jide[/I]

sudo usermod -G dba -a username

---

### Post by Man_Jide on 2007-02-13
Hello,  the first posting was wrong. "Best regards and my name should come last.

 How to install Oracle Database XE

    
    * Read #How to add extra repositories
    * Read [http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html) 

    * Add the following repository to your /etc/apt/sources.list: 

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

    * Install the software using apt-get 

sudo apt-get update
sudo apt-get install oracle-xe

    * Add your login to the 'dba' group (where your login name is username) 

sudo usermod -G dba -a username

Best regards,

Man_Jide

---

