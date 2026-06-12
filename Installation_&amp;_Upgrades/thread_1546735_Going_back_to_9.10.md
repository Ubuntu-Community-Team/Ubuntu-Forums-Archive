---
title: "Going back to 9.10"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by wavery on 2010-08-05
I'm at wits end...10.04 won't connect to a wireless network on my laptop, and that sort of makes it useless.  What is the easiest way to revert back to 9.10?  I have a dual-boot system with XP and I'd rather not have to start from scratch.

---

### Post by presence1960 on 2010-08-05
Unfortunately you are going to have to do what you said you do not want to do...unless you had the foresight to make an image of your 9.10 install prior to installing or upgrading to 10.04. 

For future reference Clonezilla or remastersys work very well.

---

### Post by lechien73 on 2010-08-06
Looking at your other posts, you have an 'orinoco' driver running. Have you tried installing the Lucid backports and working from there? This routine has worked for me when I had problems with the Atheros chipset, and I know that patched orinoco drivers are included with compat-wireless in this package.

Open a terminal window and type:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

Then reboot. If it doesn't work (which is likely), then type:

```
sudo rmmod orinoco
sudo modprobe orinoco
```

It's worth a shot before you go through the hassle of removing 10.04.

---

