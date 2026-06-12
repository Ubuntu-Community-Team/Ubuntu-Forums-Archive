---
title: "Problem installing karmic beta on fake raid"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrissk_2 on 2009-10-05
I tried to install karmic beta on my pc at work and the installed failed during grub-install.

I tried os-prober from command line and i got this message

> 
ERROR: isw device for volume "STATION7800" broken on /dev/sda in RAID set "isw_djjdcfhihf_STATION7800"
ERROR: isw: wrong # of devices in RAID set "isw_djjdcfhihf_STATION7800" [1/2] on /dev/sda
At this point i am completely stuck since i can not find "STATION7800" anywhere on the machine configuration. If this is actually raid i don't know how to overcome this issue and complete the installation. 

The pc is an HP Compaq dx2300 Microtower using an MSI motherboard and
Intel 946PL/GZ, Intel 82801GB (ICH7/R) chipset.

I never had any problem with previous releases. 

Can someone help pls ??

---

### Post by chrissk_2 on 2009-10-23
Hello again ...

I tried to install the latest karmic rc and when i started the installer, the partition editor showed no errors. I checked the installer log on /var/log/installer and i could not find any errors there either.

When i tried gparted i could see the partitions normally :
  2 windows XP partitions (NTFS) 
  1 ext4 partition with karmic beta installed there (unusable since i could not get grub to work)
  1 swap partition

Also os-prober still returns the same error from my previous post.

Any help ??  Please advice since i can not find any way to even begin the installation

Thanks

---

### Post by chrissk_2 on 2009-10-23
> **chrissk_2 said:**
> I tried to install the latest karmic rc and when i started the installer, the partition editor showed no errors.


Sorry i mean 'the partition editor showed no partitions'...

---

