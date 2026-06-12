---
title: "USB ports do not work after upgrading from 12.04 to 14.04"
date: 2015-12-03
forum: Installation &amp; Upgrades
---

### Post by Philip Gray on 2015-12-03
Good afternoon

Yesterday afternoon and evening I upgraded my 12.04 64 bit Ubuntu installation to 14.04 via the Update Manager. After the process finally finished and I rebooted I found that my keyboard and mouse no longer worked. Both are USB. My mouse is a wireless USB one. I initially started the upgrade last weekend via the Update manager which went fine until I lost my internet connection at which point Ubuntu advised thereof and that it was going to roll back to 12.04 and keep all the 14.04 files it had downloaded.

Yesterday when I opened up the Update Manager I found that the '14.04' upgrade option was no longer there. I searched the net for a solution and found one which suggested I send off this command:- *sudo update-manager -d* which I did. The Update manager then displated with the upgrade button. At some point during the installation of the new packages I received a prompt asking me if I wanted to keep my settings. As this was the recommended option I selected it. When the process reached the clean up stage a popup was displayed advising me of 486 packages which could be deleted. The 486 packages consisted of 411 obsolete packages and 67 for removal. The 67 consisted of three programs (Abuse, k3copy and Thoggen) and 64 library (lib) files. I selected the delete option to free up disk space.

I am using a desktop computer on which I have Ubuntu 14.04, Linux Mint 17.2, Zorin 9 and Windows 7 installed. All of them are 64 bit. My keyboard and mouse work in Mint, Zorin and Windows so it seems something went wrong during the upgrade. I cannot het past the log in screen because of this. I also do not have a serial mouse and keyboard. My hardware is as follows
Gigabyte GA-B75M-D3H motherboard
i5-3330 CPU
NVidia GeForce GT630 2GB video card
32GB RAM
2x2TB hard drive
1x1TB hard drive
2xDVD Rewriters
4G USB modem

All my Linux installations are on the 1TB hard drive and Windows is on one of the 2TB hard drives. I am using the Grub menu that comes with zorin because I like the blue background colour which is easier on my eyes than the purple colour.

Is there a way I can enable my USB ports? I have a number of 14.04 disks I got from a number of Linux magazines.

Regards
Philip

---

### Post by mörgæs on 2015-12-05
It seems like the 12.04 / 14.04 installation is so messed up that a fresh install of 14.04 is the best option.

---

