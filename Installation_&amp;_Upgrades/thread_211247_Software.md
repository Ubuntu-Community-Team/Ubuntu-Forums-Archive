---
title: "Software"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by AbGilley89 on 2006-07-08
I finally got ubuntu installed after I got the alternative cd and it installed with a eorror saying gnome-applets or something like that failed and I was wondering is their any commands I can use in the terminal to like make sure I have all the software.

---

### Post by Max Luebbe on 2006-07-08
What software are you afraid you're missing?

Can you post the error message?

---

### Post by aysiu on 2006-07-08
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by AbGilley89 on 2006-07-08
I don't know what software I might be missing I tried installing with the regular cd about literally 15 times with it always freezing around the 45-49% range so I downloaded the alternative cd and it got about 54% through sat their for min or two and that error came up I don't really remember what all it said but it was like gnome-applets or something like that could not be installed so I chose continue and it was finished installing within a few min and I booted into the dektop and I wasn't sure if since it had that error it skiped a few packages that would have been installed. 

aysiu I did what you posted and got this,
alan@linux:~$ sudo aptiude update
Password:
sudo: aptiude: command not found
alan@linux:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
alan@linux:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
alan@linux:~$

---

### Post by aysiu on 2006-07-08
Bad news. You're good--everything you need to have installed is already installed.

---

### Post by AbGilley89 on 2006-07-08
Dude I saw bad I was like crap i'm screwed but good thing I read further! Automatix is finishing up right now. Thanks for the fast replies!!!

---

