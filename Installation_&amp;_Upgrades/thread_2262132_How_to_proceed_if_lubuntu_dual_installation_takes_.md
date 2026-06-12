---
title: "How to proceed if lubuntu dual installation takes arbitrarily long?"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2015-01-23
In a new Asus laptop (x-200LA-KX034D) with 4gb Ram and 500gb hdd loaded with free DOS I tried to install lubuntu by downloading iso file and creating  a bootable usb drive (used unetbootin) to give dual boot set up. Installation started showing many  options and I selected "install lubuntu". After two or three steps I was shown default hdd partition of 246gb and 239gb respectively for freeDos (Fat32) and lubuntu (ext4) and I kept the default. After this there was message that this partitioning may take long time and I waited for one and half hour but the process did not end. By this time part of lubuntu had been installed and I  shutdown the machine assuming something had gone wrong. This is very unfortunate to terminate installation this way. Now please tell me whether hdd may have been affected adversely and how I should proceed for installation again. Should I uninstall whatever part of lubuntu had been installed? How to do that? Another doubt is: is it normal to have different file system like fat32 and ext4 for two partitions of same hdd? I need to keep the free DOS even though I won't use it seriously.

---

### Post by TheFu on 2015-01-23
Sure, you can mix file system types on the same HDD.
1.5 hrs?  Something is probably broke or about to break.  Definitely check the hardware.
If it is slow and connected to the internet, unplug the network cable and try again.  Installs should take 20 minutes or less. I see 14 minute installs here.
If you don't like any Linux install, just delete the partition it was on.
Also - before doing anything like this, make a know-you-can-restore backup of anything on the HDD. Definitely backup the freedos partition(s).

---

### Post by arroy_0209 on 2015-01-23
Thanks for suggestions. I have checked for disk errors and there in none. Also the same problem is repeated: the live usb is used to install lubuntu and the resize operation to allocate drive spaces of 246 gb and 239gb resp for freedos and Ubuntu is taking so long. Does anybody have any idea how long it may take for volume sizes mentioned? The installation process tells that due to rewriting partitions this process will take long but does not give any idea how long it may be.

Second doubt is I have made the first boot option usb but so far have not been able to make harddrive as second boot option. Due to laptop configuration that can be done later i.e., after this installation is over, I can change first boot option from usb to harddrive but these two cannot  be done  simultaneously. Is my problem of excessive time because of that?

---

### Post by TheFu on 2015-01-23
Did you unplug the ethernet cable?

Why so much storage?  Neither Linux or FreeDOS need it for the OS and applications.

20G is overkill for an Lubuntu install.  Don't forget that a swap partition is needed - especially on low-RAM computers.
You can use the extra storage for data as another partition. Separating /home and /data from / is common and a best practice.

How long to format a partition?  With LVM is it almost instant - under 2 sec regardless of size. If there isn't any RAID involved, it shouldn't be more than a few minutes for SATA disks.  Of course, if there are disk controller, cable issues, then things take longer.

Does a liveCD with Lubuntu run fine?  Not installed, just run from the flash drive?

If you are stuck, perhaps posting the output from a boot-info script or the boot repair info would be helpful. Just the link please.

---

