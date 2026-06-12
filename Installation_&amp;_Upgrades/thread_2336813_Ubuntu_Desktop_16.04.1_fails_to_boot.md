---
title: "Ubuntu Desktop 16.04.1 fails to boot"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-09-11
Installed Ubuntu from Live Cd.  On first attempt to boot it displays just a few lines and stops.  Messages that do appear include the following bold text:

[B][FAILED] Failed to start load/save random seed
See Systemctl status systemd-random-seed service[/B]

What should I do now?

---

### Post by ajgreeny on 2016-09-11
> **aajax said:**
> Installed Ubuntu from Live Cd.  On first attempt to boot it displays just a few lines and stops.  Messages that do appear include the following bold text:

[B][FAILED] Failed to start load/save random seed
See Systemctl status systemd-random-seed service[/B]

What should I do now?
You should tell us a lot more about your computer; make, CPU, amount of RAM, graphic card, etc etc,

Did you run the live system first to check that it worked, or did you go straight to the "Install" option?
Did you check the md5sum of the .iso file that you used to make the live system? [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by aajax on 2016-09-11
The Live CD runs fine and I used it to partition the drives as well as doing some research on various aspects of the preparation.  In that, I did a fair amount of testing with the Live CD.

Also, I don't think it is a GRUB problem because I get the same result even when I try to boot it by other means such as Super GRUB2 Disk and System Rescue CD.  These other systems have no problem finding this instance of Linux and appear to find the proper kernal etc.

Is it possible that someone knows something about the role of random seeds with regard to booting.

---

