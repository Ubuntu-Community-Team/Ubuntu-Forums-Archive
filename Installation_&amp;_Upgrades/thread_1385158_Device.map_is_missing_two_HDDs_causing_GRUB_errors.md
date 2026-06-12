---
title: "Device.map is missing two HDDs causing GRUB errors"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by pierrem-m on 2010-01-19
I'm running 9.10 (upgraded from 9.04 so I'm running GRUB not GRUB2 as I understand it) and I have a degree of flakiness in my PC that's beginning to worry me.

Twice now I've rebooted as requested after an update and have got a GRUB error.

Via booting the 9.10 live CD I've managed to fix this on each occasion but it has been far more by good luck than good judgement. Each time I tried some things on various forums on various sites and somehow got 9.10 to boot.

If my understanding is correct my problems are caused by GRUB not being able to locate the Linux partition.

I've done a bit of delving and found my device.map is as follows -

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf
(hd6)	/dev/sdg

all of which are internal SATA HDDs

Unfortunately my PC also has /dev/sdh (internal SATA), the DVD Burner and, most importantly, /dev/sdi which is an internal IDE HDD and is the HDD the Linux partition is located on.

I've hunted around a number of sites and the most I seem to be able to find is that I should add the two missing HDDs to device.map but nowhere have I found how to do this nor how to find out whether /dev/sdh is (hd7) and /dev/sdi is (hd8) or the other way around.

Any assistance would be greatly appreciated and if any further information is needed just tell me what it is and how to get it and I'll happliy oblige.

I'd really like to fix this problem as I'm extremely concerned that I might lose my main HDD and not be able to get it back.

Regards and thanks in anticipation

Pierre

---

### Post by oldfred on 2010-01-19
I have not seen anyone with this many drives, I have 3. I find the order in my system is the hardware order plugged into the SATA ports.
Ubuntu will show you its listing with:
sudo fdisk -l  (el not 1 or I)

You can manually edit the device.map or rename it and let grub create a new one on a 
sudo update-grub

You do need to have grub installed in the MBR of the drive with Ubuntu. It currently has a minor bug that causes it to search drives before loading if one a different drive. It saved me about 20 sec on grub boot to menu by moving grub from sda to sdc where Uubntu was and adjusting BIOS to boot from sdc. 

cd /boot/grub
sudo mv device.map device.map.bu
sudo update-grub2
reinstall from working ubuntu to sda or drive with ubuntu sdb, sdc etc
to make sure you have the latest grub2:
sudo apt-get install --reinstall grub-pc
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda

---

