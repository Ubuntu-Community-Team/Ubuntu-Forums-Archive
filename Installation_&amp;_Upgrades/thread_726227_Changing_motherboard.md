---
title: "Changing motherboard"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Scorpuk on 2008-03-16
I plan to upgrade the motherboard of my server due to the dire capability of the X3100 onboard graphics.


My current system is as follows:

M/B - Gigabyte GA-G33-DS3R
CPU - Q6600
Mem - 4Gb
HDD - 12 x Seagate 500Gb
HDD Controller - Adaptec 9650SE-12ML

HDD's are set up as follows:

Volume 0 	100.00 GB
Volume 1 	2.00 TB
Volume 2 	2.00 TB
Volume 3 	926.17 GB

Volume 0 is OS (Ubuntu 7.10 64bit)
Volume 1 & 2 & 3 is Raid 5 with LVM mounted in /media/raid5


I plan on changing to Asustek S775 GeForce 680i ATX GLAN  with Gigabyte GeForce 8600GT 256MB DDR2 PCIE DX10 HDCP 570/1400  


Ensuring the drives are connected up in the same order will I have any problems switching motherboards?

---

### Post by scragar on 2008-03-16
I swapped out for a whole new computer and nothing stopped working, so I shouldn't image any problems.

---

### Post by Scorpuk on 2008-03-16
My main concern is that I'm using the hardware raid controller.

---

### Post by Herman on 2008-03-16
I don't know anything about RAID.

But since you'll have a different video card, you may find that the video driver that your Ubuntu is set up for now will not work the first time you boot up.
You might boot to a command prompt in a black screen.
If that happens, don't worry. Just run sudo ddcprobe to get Ubuntu to tell you what video card and monitor you have now.
```
sudo ddcprobe
```Then you can run sudo dpkg-reconfigure xserver-xorg to set up Ubuntu with the right drivers for your hardware.
```
sudo dpkg-reconfigure xserver-xorg
```It might take about five or ten minutes the first time you reboot with the new hardware and after that things will be back to normal, (or actually, better than before, because you'll be set up with the new video driver.

Here's a web page with more info about that, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html") 

Regards, Herman :)

---

