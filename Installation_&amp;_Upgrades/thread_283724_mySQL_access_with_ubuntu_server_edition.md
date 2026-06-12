---
title: "mySQL access with ubuntu server edition"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Methose on 2006-10-24
I just installed ubuntu server edition on my test machine for an oscommerce site that a partner of mine and I are building. The problem that I have encountered is that when setting up the mySQL database I had to use the sudo command to access mySQL, therefore using the root username rather than the username I created when I first installed the OS. 

I used the command: sudo mysql 
-then created a database (This was required to create a database before the installation of oscommerce.)
-then started the installation and got to the point of it asking for the database information

username: 
password: 
database name:
host name or IP:

I tried the username I created durring installation as well as root, both with the only password that I know of for the machine.
neither of them worked giving the error:
   "Access denied for user '*******@'localhost' 

  Any ideas on how to solve this problem...can I give my username access to mysql and then create the database without sudo? if so how?



:mad:

---

