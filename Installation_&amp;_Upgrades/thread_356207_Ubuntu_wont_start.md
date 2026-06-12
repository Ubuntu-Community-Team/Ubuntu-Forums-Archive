---
title: "Ubuntu wont start"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by evkefalas on 2007-02-08
Hi, I am new Ubuntu user, and chose it because i want to get involved with linux but i am unexperienced,
So with the help of a friend i installed version 6.10 on a partition on my laptop, i have another NTFS partition with XP, another DAta partition FAT32 and recently made 2 more partition 1 GB swap and 5 GB for Ubuntu, 
Now i tried and installed it many times
last times i also did all the upgrades
but when i restart it i login and then the only thing i can see is the ubuntu wallpaper, so taskbars, i can move the cursor but nothing else is active
if i reboot and login with recovery mode it works fine
if i reboot and login with generic mode
again the same problem
Can anyone Help?
Many Thanks

---

### Post by banditti on 2007-02-08
could be a video issue.  What laptop are you using?  Did you install special drivers or keep the standard?

---

### Post by evkefalas on 2007-02-09
Hi, 
I am using a HP Pavilion 2.8 GHz 512 RAM, 60 GB hard disk
with ATI radeon 9600 graphics card!

Do u think i could log in recovery add the ubuntu ATI suggested drivers
and try again?
Thanks

---

### Post by evkefalas on 2007-02-09
i used the standar drivers so far

---

### Post by banditti on 2007-02-10
what model of Pavilion?  This is a pretty good roadmap for issues people have found with linux on laptops.

[http://www.linux-on-laptops.com/hp.html](http://www.linux-on-laptops.com/hp.html)

I am sure yours, on one very similar is in there.

---

### Post by evkefalas on 2007-02-12
Thanx a lot for the information, 
I went through the list but didnt find anything similar :(

I tried to format everything and install ubuntu again fresh
i figured out that when u first install it after intallation finishes
i remove cd and boot normaly for the first time in generic mode
now if try to restartt again then i canot login normally ever after through generic mode
(always loading normally session, entering username, pass and then start up screen and 
the only thing visible is ubuntu background, no taskbars , cursor moves, no right click)
Note this happens always after different format and installation attempts

The only think that you can do is to reboot, login with recovery mode , everything works fine there, and then ctrl Alt Backspace, Exit . So i get to the session login screen and then if i enter again the Username etc it  logs in normally (generic inviroment)
So basically i can only log in generic if i first login recovery, logout and then login normally again

This cant bee right, something stupid is going on
I mean why  the first time after installation i can login normally and then after that i cant?

Many thanks for trying to help

---

### Post by tagra123 on 2007-02-12
check your syslog.

from the recovery mode you can use cat ot tail to display the file but I prefer nano (text editor) to look at the whole file.

nano /var/log/syslog

I'll bet there is a message about bonobo.  

Is the system clock working correctly?

---

