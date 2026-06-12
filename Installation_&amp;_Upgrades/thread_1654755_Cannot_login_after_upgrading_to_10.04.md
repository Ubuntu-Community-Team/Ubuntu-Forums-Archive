---
title: "Cannot login after upgrading to 10.04"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by cjjoy1980 on 2010-12-28
Hi,
  I upgraded the my ubuntu to version 10.04, the upgrade was succesful, but I am not able to login to the system. I get the login prompt, when I issue the password and press enter, I see a small window which says :

 "A program is still running":
"Power Manager not responding" with three buttons, "Lock Screen", "Cancel", "Logout anyway".

After a few minutes, it takes me back to original login screen.  

I tried few things looking at this post :
[http://ubuntuforums.org/showthread.php?t=1355880](http://ubuntuforums.org/showthread.php?t=1355880)

Tried to reinstall gnome-power-manager, checked the free space on my system, /tmp has all permissions.  Nothing helped.  

Other important thing i noticed is, I am able to login using different user, the login is slow but the login is successful. Also I am able to su to my username once logged.  Please suggest if any thing else needs to be tried. 

THanks
Joy

---

### Post by Joe Ker1086 on 2010-12-28
Have you tried booting into recovery mode and repairing broken packages?

---

### Post by cjjoy1980 on 2010-12-28
HI Joe,
  How do I know which package is broken?  I do not see any errors in /var/log/messages or dmesg when I login from xterm (control + ALT + F1).  
I tried reinstalling ubuntu desktop and also gnome-power-manager

---

### Post by Joe Ker1086 on 2010-12-28
it should find them for you if there are any missing. Just boot into recovery mode and repair broken or missing packages is an option. Give it a try, it has fixed some problems for me a couple times.

---

