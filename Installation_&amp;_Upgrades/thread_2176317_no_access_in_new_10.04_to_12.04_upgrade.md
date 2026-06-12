---
title: "no access in new 10.04 to 12.04 upgrade"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by whvw on 2013-09-23
I really think it's done for but I'll try asking here. I just did an upgrade, (10.04 to 12.04) and can only log on as a (useless) guest. I do not know if my user account is even still there, since I'm not allowed to see the files. It let me change the user password, but then wouldn't ask me for it.
I cannot access root. I cannot access recovery. No sudo commands of any sort will work, all I get is <<sudo: unable to change to sudoers gid: Operation not permitted>>. None of the fixes for that found here or in other places work. 
Assuming that this install is lost, is it possible to lift my user files from this HD and <<splice>> them into a cloned 10.04 disk? This is bad.

---

### Post by mörgæs on 2013-09-24
> **whvw said:**
> 
Assuming that this install is lost, is it possible to lift my user files from this HD and <<splice>> them into a cloned 10.04 disk? 

In a live boot you can copy your user files from the failed upgrade and paste them into a fresh install of 12.04 or 13.04.

In the other thread of yours a backup was recommended, wasn't it...?

---

### Post by whvw on 2013-09-24
WEll, I discoverd that I could create a new user, and get some access with that. I even managed to restore my original user and root. BUT: Seamonkey  is gone, Open Office won't open and my desktop is a mess. Is there any way to customise the desktop as in older versions?

---

### Post by mikewhatever on 2013-09-25
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1966370") for customizing, though I am not sure how it's going to help with the problems.

---

