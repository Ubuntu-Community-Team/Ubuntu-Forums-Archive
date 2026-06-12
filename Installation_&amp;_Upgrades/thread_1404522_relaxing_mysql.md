---
title: "relaxing mysql"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2010-02-11
dear ubuntu wizards:

I am running 9.10, with mysql version 14.14, distrib 5.1.37.

I need to do two things.  first, I want to open up mysql to remote access.  second, I want to move /var/log/mysql to /home/mysql/log via a symbolic link.  (the latter sits on another partition that has a whole lot more space available than the former.)

let's start with the second.  I move it, and restart mysql.  /var/log/messages tells me:

> 
Feb 11 14:23:00 w kernel: [14263.498160] type=1503 audit(1265916180.435:202): operation="open" pid=5590 parent=5589 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Feb 11 14:23:00 w kernel: [14263.513144] type=1503 audit(1265916180.455:203): operation="open" pid=5599 parent=5598 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"


and mysql now no longer starts.  so, I am wondering whether this could be apparmor.  I added the new directories into /etc/apparmor.d/usr/sbin/mysqld , and tried again.  still no dice.  so, this was not it.  does anyone know what I need?

and, is there some further chanting required to open it up to remote tcp/ip connections?

advice appreciated.

/iaw

---

### Post by iaw4 on 2010-02-12
bump

---

