---
title: "Need swap and bootloader advice"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by Awes0meSauce on 2011-07-11
I had just a couple of questions before I take the plunge and install Ubuntu 11.04 64 bit. I have a multi-drive system. Three hard drives to be exact. When I install Ubuntu I will be dual booting. I have Windows 7 on sda. I will be installing Ubuntu on sdb. If I remember correctly, when it asks me where I want to install the bootloader it gives me the option to install it on ATA(drive model) sda. But when I hit the drop down arrow, there is another option ATA (drive model) sda1 (Windows 7 loader). Do I install the boot loader over the Windows 7 loader? Or do I just put it on the drive in general? My second question is how big should I make the swap? I have 4GB of ram. I've read that you should have twice the amount of ram and I have also read that 2GB is plenty. Not sure which it is. Any help would be much appreciated. Thanks for your time.

---

### Post by oldos2er on 2011-07-11
If you don't plan on using hibernation, a 1GB swap file would probably be more than enough, unless you're going to be running some very RAM-intensive programs. I've never touched swap with either 2GB RAM or 4.

The advice to make swap twice actual RAM is not really valid for modern systems.

---

### Post by linuxman94 on 2011-07-11
For the bootloader, select the drive and not the partition. So don't use sda1, use sda.

Edit: 300th post! :D

---

### Post by Awes0meSauce on 2011-07-11
> **oldos2er said:**
> If you don't plan on using hibernation, a 1GB swap file would probably be more than enough, unless you're going to be running some very RAM-intensive programs. I've never touched swap with either 2GB RAM or 4.
 
The advice to make swap twice actual RAM is not really valid for modern systems.
I don't think I have ever used hibernation so I'll go with 1GB like you recommend.
> **linuxman94 said:**
> For the bootloader, select the drive and not the partition. So don't use sda1, use sda.
 
Edit: 300th post! :D
Thanks for clearing that up! I looked everywhere but could never find an answer.

---

### Post by Quackers on 2011-07-11
If you have 3 hard drives in your system you should get other options for the boot loader - like /dev/sdb and /dev/sdc.
If you want grub on the hard drive that you install Ubuntu on you should select that option for grub installation then select that drive as the first bootable hard drive in your bios. That way the Windows boot loader will remain untouched on /dev/sda.
Or at least that is another option that some would recommend for you.

---

