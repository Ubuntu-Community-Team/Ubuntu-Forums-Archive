---
title: "Why are there two lib32 directories?"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by deparvius on 2011-06-17
There are two directories for lib32 files, /usr/lib32 and /lib32. 
Important programs seem to point to /lib32, but more recent files were found in /usr/lib32.    

Why are there two?   I discovered this issue when upgrading Kubuntu to 11.04 from 10.04, with 10.10 interim update.     

A note to software upgrade developers:  upgrading to 10.10 using software management in KDE failed due to openoffice issues, and final stages/restart were nor performed.  I uninstalled openoffice, then clicked &quot;update to 10.10) again, however the upgrade to 11.04 was performed instead, without restart or interim software update, resulting in errors and a broken apt-get (see below).     

linux-headers, and linux-image were broken in the update to 11.04.  
Manually restarted afterwards.  
Boot worked, but X-windows wouldn't load.  
Many other programs wouldn't work, apt-get included, yielding the error similar two (from memory):  version GLIBCXX_3.4.14 not found libstdc++.so.6 not found  

The fix for this was noticing that in /lib32 libstdc++.so.6 was a symbolic link to libstdc++.so.5, but there was a more recent libstdc++.so.6.0.14 (luckily!) in /usr/lib32.  Issues were fixed by copying this file over and pointing the symbolic link to it instead. I was then able to use apt-get to upgrade linux-headers and linux-image simply by calling it, which in turn fixed X-windows/KDE and the rest of the system not starting up.  

My concern is this:  
Why are there two lib32 directories?  
Having two saved me here, but will software updates update to the right directory?  Are both in use?  Will my manual fix cause potential problems down the road?  

This may have been caused by some manual tinkering I did in the past to get a recent version of a program to work in 10.04, but I don't remember if I touched these files or not.  Regardless, it is worth pointing out in case others have this issue on update and don't know how to fix it.

---

