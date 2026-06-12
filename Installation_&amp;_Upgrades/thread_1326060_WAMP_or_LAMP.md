---
title: "WAMP or LAMP"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by little_john on 2009-11-14
Dear all,
In my office, server is running on Windows 2000 server, most of client running on Ubuntu 8.10, other on XP. Right now, my boss want to develop a web server, include apache, php and mysql. Is server must be changed to Linux or must build a new server ? I am just a beginner, what is the right choice ? if server changed as a web server, how about file sharing, is it still work right before ? 
Thanks

---

### Post by davetv on 2009-11-14
Apache, Mysql, php all run fine on Windows 2000 server. Apache on Windows however, is not guaranteed to be secure.

I would suggest going with LAMP, file sharing will work via samba but you may need to learn how to correctly configure it.

---

### Post by Sophont on 2009-11-14
Apache will work on both - but LAMP is practically the standard for web servers - and won't cost you the licence for win2008 - win2000 is being phased out and not really supported anymore.

If the server is just for web server then install Debian or Ubuntu server - you can select LAMP stack during installation. With a bit of googling you can also find many pre-configured LAMP ISOs out there.

If the server is also used for file sharing etc... then have a look at ebox:
[http://www.ebox-platform.com/]("http://www.ebox-platform.com/")

---

### Post by markjensen on 2009-11-14
> **davetv said:**
> Apache, Mysql, php all run fine on Windows 2000 server. Apache on Windows however, is not guaranteed to be secure.
Oh? 

Might I ask what platform *is* guaranteed to be secure?  I am guessing "none".

There are valid reasons to pick Linux over Windows in a server situation, but please don't throw "guaranteed security" out there as one of those reasons.

---

