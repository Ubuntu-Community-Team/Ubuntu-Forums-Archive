---
title: "[Ubuntu Software Centre] Eclipse/Netbeans Repository problem"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Asymptotic on 2010-07-18
Using the Ubuntu Software Centre I tried to install Eclipse and got a fail message telling to check my connection, its fine...

I then ran 

sudo apt-get install  eclipse-platform --fix-missing

after saying stuff that seems normal it then says:

Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main libservlet2.5-java 6.0.24-2ubuntu1.1
  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.24-2ubuntu1.1_all.deb)  404  Not Found

I guess either I need a port open that isn't (unlikely) OR the file its looking for is obsolete and no longer there..

Anyone with some insight?

---

### Post by Asymptotic on 2010-07-18
Fixed.

After poking around I ran this command:

sudo apt-get clean && sudo apt-get update && sudo apt-get install eclipse-platform

---

