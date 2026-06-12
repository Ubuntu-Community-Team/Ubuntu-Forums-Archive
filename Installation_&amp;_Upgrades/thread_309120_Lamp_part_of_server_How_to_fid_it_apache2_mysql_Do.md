---
title: "Lamp part of server How to fid it apache2 mysql Dont seemed to be available"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-11-29
Cant seem to find Apache or Mysql whats up

some how I dont think Apache2 or Mysql where loaded in the install
I chose Lamp server option aswell. Some how the lamp part of server didnt get installed any ideas

**apache2ctl status**

bill007@production:~$ apache2ctl status
-bash: apache2ctl: command not found
bill007@production:~$

**ps -A | grep apache**

bill007@production:~$ ps -A | grep apache
bill007@production:~$

**sudo /etc/init.d/apache2 start**

bill007@production:~$ sudo /etc/init.d/apache2 start
sudo: /etc/init.d/apache2: command not found
bill007@production:~$
[B]
 sudo apt-get install apache2[/B]

bill007@production:~$ sudo apt-get install apache2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bill007@production:~$


Cant seem to find the files either

---

