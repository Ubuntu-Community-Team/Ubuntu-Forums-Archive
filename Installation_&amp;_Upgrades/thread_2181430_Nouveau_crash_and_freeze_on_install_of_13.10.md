---
title: "Nouveau crash and freeze on install of 13.10"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by xaegis on 2013-10-17
I upgraded from 13.04 to 13.10 and my ubuntu froze at the Aburgine Ubuntu screen. 
I did a fresh install and now it freezes at the same spot except I get an error about Nouveau.
Ubuntu 13.10
Lenovo Y510P

How should I proceed?

Thanks

---

### Post by VMC on 2013-10-17
Unfortunately you'll have to install nvidia drivers. I too found both Ubuntu 13.10 and Gnome 13.10 to freeze using nouveau. Strange but Kubuntu 13.10 doesn't freeze.

---

### Post by xaegis on 2013-10-17
Yeah,but HOW do I install the drivers? I cant get to a terminal because of the video crash. I suspect that Kubuntu doesnt freeze bacause it is using kwin and is QT based.

---

### Post by VMC on 2013-10-17
Use '***nomodeset***'. When you boot up, and grub menu appears, 'e' at the Ubuntu entry that you want to boot. Then using the arrow keys go to the line that starts with '***linux***', then go to end of that line, push the spacebar then type '***nomodeset***' without quotes. Then push '**F10**'.

---

### Post by xaegis on 2013-10-17
Yep. That is how I installed in the first place. But on boot up I get a screen full of errors and no chance to get to a terminal to enter more commands. (Shift doesn't seem to work)

---

### Post by VMC on 2013-10-18
Use the [RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode"). Then before installing any driver find out what errors your getting. Look at the log files in '/var/log' for research.

---

