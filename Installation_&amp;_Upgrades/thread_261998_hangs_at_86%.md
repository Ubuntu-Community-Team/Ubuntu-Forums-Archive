---
title: "hangs at 86%"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by tehdecoy on 2006-09-21
I am trying to install xubuntu on an old dell PII box.  I tried installing ubuntu first, but it ran so slow that the computer kept freezing up.  I decided to go with xubuntu instead, it runs much fast from the live CD and it actually lets me open the install program.  It goes through that fine until it gets to 86% when it starts setting up the clock.  There it just hangs and stops doing anything at all for hours.  I read a post on this issue before, but the solution was to use breezy instead of dapper.  As best as I can tell, there isn't a version of xubuntu for breezy, and I'm not sure if my pos dell can handle it.  Any help would be nice.  Thanks in advance.

---

### Post by unisol on 2006-09-21
what are your system specs

---

### Post by tehdecoy on 2006-09-21
PII 233mhz
640k RAM (most likely PC100, havent really looked that close at it)
32mb AGP card, not sure of the make or brand, isn't labled and the comp was so full of crap that I couldn't check what it was when win98 loaded.
Also has a 4.5GB primary HD, and a 2.5GB slave.
Had Windows 98 until I cleared it off to put xubuntu.
Oh, and it's an old Dell Dimension XPS D233

---

### Post by wpshooter on 2006-09-21
I have one of these exact old Dells in the computer graveyard room in the back at work.

When I get a chance I will bring my CD from home and see if I can install it on that machine.

Are you using the DESKTOP CD or the ALTERNATE CD for Xubuntu ?

I think what I will try will be the ALTERNATE CD version of Dapper Drake (Gnome).

---

### Post by pansz on 2006-09-21
I've got the same 86% problem, however I solved it in this way:

Use Alternative CD.

Choose Install a server.

When the server finished install and reboot, make sure the /etc/apt/source.list have the repositories (it should have the cdrom as the first), if you want to speed the installation, the http repositories can be commented out now,  let's only leave the cdrom there.
run the command:
sudo install xubuntu-desktop 

will do the trick (At least it works for me), believe me, it will not hangup at 86%.

---

### Post by tehdecoy on 2006-09-21
I'm been trying to install using the desktop cd.  I will try it from the alternative cd and see what happens.

---

