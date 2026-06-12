---
title: "upgrade problem"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by kieron100 on 2006-11-16
when I try and upgrade to 6.10 from 6.06 using > update-manage -c in the terminal I get the following error > Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
 any idea what is causing this and how to fix it? 

thanks :)

---

### Post by earobinson on 2006-11-16
I assume your running as root aka sudo or gksudo?, try a wget [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) see what that gives you

---

### Post by magiceraser06 on 2006-11-16
@thinktank:~$ wget [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2)
--16:13:47--  [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2)
           => `Packages.bz2'
Resolving security.ubuntu.com... 82.211.81.138
Connecting to security.ubuntu.com|82.211.81.138|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:13:48 ERROR 404: Not Found.



I just recently switched to Linux after XP crashed my harddrive and deleted ALL of my files.  Luckily I had backups.  Found Ubuntu quite accidently, since I was trying to install OSx86.  

LINUX ROCKS!!  I am so happy with Dapper.... but i hear good things about Edgy.  

Any help would be awesome!!

---

### Post by earobinson on 2006-11-16
check out the wiki [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by magiceraser06 on 2006-11-16
Well, I finally did it.  Using Edgy right now and I must say there are definite improvements.

I found a work around that may of use to some people who, like me, kept running to the ERROR CODE (2) with bzip. while trying to install Edgy.

I did this:

sudo gedit /etc/apt/sources.list

changed everything instance of DAPPER to EDGY.

Then opened up SYNATPIC and did RELOAD.

THen, I did MARK ALL UPGRADES.

Then APPLY

That method worked for me instead of using "update-manager -c" method.  Also, I found that you would have to do sudo apt-get update quite a few times before the UNVIVERSE and MULTIVERSE i386 binary packages would download completely and without errors.

just keep trying all of you out there.   

hope that helps.

-Eraser-

---

### Post by magiceraser06 on 2006-11-16
Oh, that and my /HOME/.drmc permissions got reset, but that is an easy fix.

Also, didn't have a splash screen, but when I opened System >>> Administration >>> UPDATE MANAGER

checked for updates, it said i needed to do a DISTRIBUTION UPDATE, so I did that, only about 20.0megs it needed to finish the previous updraded i guess. only a few programs.

now im good. :-D

---

### Post by earobinson on 2006-11-16
good to hear, now do us a favor and edit the original post, click advanced, and mark the thread as resolved :)

---

### Post by magiceraser06 on 2006-11-19
umm, how do i do that?

---

