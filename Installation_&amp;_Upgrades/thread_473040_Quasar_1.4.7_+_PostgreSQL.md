---
title: "Quasar 1.4.7 + PostgreSQL"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by Onompoly on 2007-06-13
I'm running the newest version of fiesty 7.04
I'm following these directions

[http://wiki.ubuntu.org.cn/index.php?title=UbuntuHelp:QuasarAccountingInstallation&variant=zh-tw](http://wiki.ubuntu.org.cn/index.php?title=UbuntuHelp:QuasarAccountingInstallation&variant=zh-tw)

[http://ubuntuforums.org/showthread.php?t=50662](http://ubuntuforums.org/showthread.php?t=50662)



Well i got as far as properly install quasar my problem is when i try to to do the driver config in the quasar admin app... it says my non dba username password is incorrect:(


The last link suggest something about firebird database also running and screwing things up ....im not really quite sure what to do now..

---

### Post by Onompoly on 2007-06-13
anthony@MobileClone:~$ psql -h localhost -U quasar template1
Password for user quasar: 
psql: FATAL:  password authentication failed for user "quasar"
anthony@MobileClone:~$ createuser -E -P quasar
Enter password for new role: 
Enter it again: 
Shall the new role be a superuser? (y/n) y 
createuser: could not connect to database postgres: FATAL:  no pg_hba.conf entry for host "[local]", user "anthony", database "postgres", SSL off



i get this message when i try to set a password for quasar .. i dont know what the password is if any if this user is even created im going insane


I have been going to the forum .. ive got like 8 different tabs open.....guess i shouldnt have completely uninstalled windows

---

### Post by MichaelSM on 2007-10-15
Hi Onompoly.

If you got it fixed, let me know.

I'm at the same point as you were, except I didn't read the instructions properly and answered 'n' to the first question. But I don't think it would have made any difference, since my passwords weren't recognised either.

All the best.

Mike.

---

