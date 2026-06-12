---
title: "Can't install Ubuntu 10.10 desktop from USB drive"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by Landy on 2011-04-20
Hi 

I've made a startup disk with a 2GB USB stick, following the instructions from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download). Then I tried to use this USB disk to install Ubuntu in a new computer. 
The computer can boot from the USB drive successfully, but after I click "Install Ubuntu", it reports that my computer doesn't meet the requirement of "has at least 2.6 GB available drive", but actually my computer has 2*500 GB hard disk which can been recognized in BIOS and displayed in the BOOT option list.

How can I fix this issue? 
btw: if I don't choose "Install Ubuntu" but "Try Ubuntu", the system will hang forever.

I've tried to make the startup disk again, strictly followed the instructions from above link, but no lucky.:(

---

### Post by wilee-nilee on 2011-04-20
You should first make sure you have free space for Ubuntu an unallocated space to build the partitions, and the OS within. 

You may have a graphics driver needed, if this is the case you can do a low graphics boot to the desktop then, build the partitions with gparted, or if you want it on one hd by itself set up the grub loader correctly. 

Low graphic boot; power on immediately hold down shift key, at choice menu hit f6 tick nomodeset then boot to see if you get to a desktop.

Do not choose the side by side option with the install, use the custom install, and at that screen make sure the grub bootloader is going to the mbr of the hd you're installing Ubuntu in.

---

### Post by Landy on 2011-04-21
Thanks wilee, I tried your solution and I can enter the live mode, but Ubuntu can't recognize my hard disk yet. In Disk Utility, it shows USB, SD, CF card, but doesn't show the hard disks. fdisk -l also only return the USB disk. I tried to start "Install Ubuntu 10.10" from the desktop, it failed as expected - not meet the criteria: "At least 2.6 GB available disk space".

Strangely, I installed ubuntu 10.10 from an installation CD before. Now the CD Reader is broken, so I want to install ubuntu with a USB disk.

Is there any other way to try? Thanks.

by the way, I also read this link -http://superuser.com/questions/149701/ubuntu-9-10-installer-doesnt-recognize-the-hard-drive, but the 'apt-get -y remove dmraid' trick doesn't works in my case.

Thanks.

---

