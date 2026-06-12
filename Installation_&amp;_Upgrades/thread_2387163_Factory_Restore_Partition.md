---
title: "Factory Restore Partition"
date: 2018-03-15
forum: Installation &amp; Upgrades
---

### Post by mattzab on 2018-03-15
Hello, I searched and couldn't find related question.

I'm thinking about buying a System76 machine with Ubuntu on it. I like to tinker and experiment, and generally push things at times. Rather than breaking my system and reinstalling from a USB, how can I set up a small partition that would allow me to "factory reset" the machine?

I'm thinking maybe a 5 gig boot partition that has the ISO on it, and GRUB can either boot to my OS, or when I break things, select the other boot option to fire up the live ISO.

I'm not sure if that would work, and would like more suggestions on what or how to do this.
Thanks!

---

### Post by ubfan1 on 2018-03-15
The ISOs you want to test may sit on your normal system.  What you'd need is a 10G FAT filesystem to store some casper-rw files (of 2G - 4G apiece).  That will allow you to set up grub boot items with persistence, which is useful for setting up things like wireless and video.  You can have multiple casper-rw files, and use the PERSISTENCE_PATH to select which one to use for an ISO boot.  There are lots of suggestions here and in askubuntu.com  for setting these things up (ISO boot off hard disk).

---

### Post by ajgreeny on 2018-03-15
You may find the info on the post at [https://ubuntuforums.org/showthread.php?t=1838959&p=11218670&viewfull=1#post11218670](https://ubuntuforums.org/showthread.php?t=1838959&p=11218670&viewfull=1#post11218670) useful, though I admit this is not something I have ever used.

---

### Post by yancek on 2018-03-15
Do two installs, one on a minimal partition maybe 10GB and don't use it except if your primary system crashes.

THere is software which you can use to create a bootable iso of your modified system with software changes, etc., within certain size limits that you can either put on a usb, DVD or separate partition on the computer and then use it Live or to reinstall.  Two examples are Systemback and Pinguy Builder.  Not sure if they work on newer Ubuntus, but did on 16.04.

---

