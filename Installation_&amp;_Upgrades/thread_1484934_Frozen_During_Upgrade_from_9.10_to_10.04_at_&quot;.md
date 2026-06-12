---
title: "Frozen During Upgrade from 9.10 to 10.04 at &quot;Configuring mysql-server-5.1&quot;"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by CheapoDepot on 2010-05-16
I tried upgrading from Ubuntu 9.10 to Ubuntu 10.04 LTS last night. 

Checked my computer this morning and it's stuck at "Installing the upgrades" "Configuring mysql-server-5.1" with "About 3 minutes remaining".

The cleaning up stage and restarting the computer have not happened yet.

The terminal reads...
> Setting up mysql-server-5.1 (5.1.41-3ubuntu12) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.mysql ...
Installing new version of config file /etc/logrotate.d/mysql-server ...

I really don't know what to do here. Is there a way to fix this? What happens if I restart my computer at this stage? Will it revert back to 9.10 or will I be screwed and be in no mans land with part 9.10 and part 10.04?

Any advice is very appreciated.

---

### Post by 1999 on 2010-05-16
yeah, this happened to me when i upgraded
as i remember, you should stop your mysql service

just open terminal and write there "sudo /etc/init.d/mysql stop" and upgrading will continue

---

### Post by CheapoDepot on 2010-05-16
You are the man!

That got it rolling again. Thanks a lot!

---

