---
title: "Installing oracle 11g database in ubuntu 13.10"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by mohitsharma3172 on 2013-12-14
[COLOR=#000000][FONT=Consolas]hello...
i'm new to ubuntu...
i'm using ubuntu 13.10...
i'm trying to install oracle 11g database...
i succeeded doing that by following the tutorial in the link [/FONT][/COLOR][http://meandmyubuntulinux.blogspot.in/2012/05/installing-oracle-11g-r2-express.html](http://meandmyubuntulinux.blogspot.in/2012/05/installing-oracle-11g-r2-express.html)
I succeeded..it worked
but after restart , it says sqlplus command not found
please help.

---

### Post by raja.genupula on 2013-12-15
whats the output of 

> apt-get cache policy sqlplus

---

### Post by mohitsharma3172 on 2013-12-21
it says :
E: Invalid operation cache

---

### Post by icelechi2 on 2014-05-11
Try this:


Create a new file called .oracle in your home directory and in the file write

#!/bin/bash
sudo mkdir /var/lock/subsys
sudo touch /var/lock/subsys/listener

sudo service oracle-xe start

Save it and give it the appropriate privileges 

sudo chmod 755 ~/.oracle
then run it ./.oracle

---

