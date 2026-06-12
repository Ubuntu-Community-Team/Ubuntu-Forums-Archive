---
title: "where is the minimal ISO?"
date: 2020-08-27
forum: Installation &amp; Upgrades
---

### Post by mringer on 2020-08-27
In another thread:

[https://ubuntuforums.org/showthread.php?t=2448046](https://ubuntuforums.org/showthread.php?t=2448046)

I was advised that  L-ub 16.04  is out of support & i should upgrade to 20. Also I 
should install the minimal ISO & LXDE. But when I looked for the ISO in

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

there is no ISO for 20, instead there are ISOs for 18, 16 and (!!!) 14 .

Please where should I look? Thank you.

---

### Post by ActionParsnip on 2020-08-27
[http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso)

---

### Post by oldfred on 2020-08-27
The minimal ISO were not UEFI bootable and all systems since Microsoft released Windows 8 in 2012 are UEFI hardware.

Suggestion was to use server ISO and not install anything you do not want. Server without apps is not really much more than minimal.
I had to use server installer to install 20.04 to my 2006 laptop with 1.5GB of RAM. GUI server installer did not work, I had to use the terminal version.
I then installed my lightweight GUI of choice and lighterweight apps. Old laptop was functional, but now spoiled with desktop, larger screen, and SSD.

Just do not choose anything & then manually install apps your want.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by ActionParsnip on 2020-08-27
Note that UEFI can be disabled if Ubuntu is the only OS on the system. It's not mandatory

---

