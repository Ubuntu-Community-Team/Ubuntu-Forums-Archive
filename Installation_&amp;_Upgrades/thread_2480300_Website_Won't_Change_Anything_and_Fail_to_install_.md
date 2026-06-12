---
title: "Website Won't Change Anything and Fail to install Apache2"
date: 2022-10-25
forum: Installation &amp; Upgrades
---

### Post by levi88 on 2022-10-25
Can Anyone help me, i can't install apache2, it say 

 mysql.service: Failed with result 'exit-code'.
 Failed to start MySQL Community Server.
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-8.0; however:
  Package mysql-server-8.0 is not configured yet.

and Also, i already upload and deleted many times and it wont change the website

---

### Post by yancek on 2022-10-25
The messages and errors you are reporting are all in regard to mysql.  Did you follow instructions from the mysql web site or some other web site to install it?  What method did you use to install?  

> Package mysql-server-8.0 is not configured yet.  

That seems to be the primary problem, do you not have instructions on how to do that?  There seem to be a number of sites reporting similar problems such as the one below.

[https://unix.stackexchange.com/questions/505764/ubuntu-18-04-lts-problem-with-dependencies-installing-mysql-8-0-server](https://unix.stackexchange.com/questions/505764/ubuntu-18-04-lts-problem-with-dependencies-installing-mysql-8-0-server)

---

