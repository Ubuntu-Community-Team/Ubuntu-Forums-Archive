---
title: "Triple Booting Win 7 and Ubuntu"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by xrecar727 on 2009-11-25
I have been banging my head on this install for a while now and haven't been able to get things going.  I am trying to triple boot between 2 separate Win7 installs and Ubuntu 9.10, all of these being 64bit. For the current install (I think I have tried this 4 different ways by now) I began with installing Windows 7 twice, basically setting up a dual boot scenario. I then installed Ubuntu 9.10 and used the advanced setting to tell it to install the bootloader on the same partition as Ubuntu. The problem is I cannot seem to get it to boot into Ubuntu. I have been using EasyBCD (Version 2.0) in Win7 to install the linux boot entry and choosing Grub2. After doing this, when I choose the Ubuntu option it loads me into a Grub prompt and that's as far as I have been able to get. I have a feeling my raid setup is the cause of the issue, but I don't know how to resolve it (or if it is even possible to resolve). Any help would be greatly appreciated! Here are the details of my configuration:

3 x 160 Gb SATA Drives configured in RAID 0 using the on board raid (Gigabyte MA790X-UD4P)

Partition 1 - Windows 7 System Partition
Partition 2 - Windows 7 OS 1
Partition 3 - Windows 7 OS 2
Partition 4 - Ubuntu Partition

At this point I have not created a swap partition because I thought maybe somehow having Ubuntu on an Extended partition was causing a problem. I had thought by installing Ubuntu last (on the first try), it would install the Grub bootloader and everything could boot from that, but it didnt. From what I have been able to find online I can only guess that the RAID configuration may be the cause for that.

Any ideas on how to go about solving this? If more info is needed, let me know and I will do whats needed. Also, keep in mind I am relatively new to linux so some instruction may be warranted :)

Thanks,
+Rob

---

### Post by jacobs444 on 2009-11-25
I think you need grub installed to the MBR, not on ubuntu's partition.

---

### Post by xrecar727 on 2009-11-25
I think so too, in fact my first attempt (after the initial installation) was to attempt that. The problem I am having is getting it to do so. I found this link: [http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708"), but when I issue the mount command, I get an error:

mount: special device /dev/sda4 does not exist

I think this is due to the raid configuration but I am not sure. fdisk shows the drive as sda4 but I have suspicions that I need to be using something else instead. For example in gparted, the partition is labeled /dev/mapper/pdc_dbagiefd4. When I substitute that in place of /dev/sd4 it actually takes the mount command, but then when I issue:

sudo grub-install --root-directory=/media/mapper/pdc_dbagiefd4 /dev/mapper/pdc_dbagiefd4

I get the following error:

grub-probe: error: no mapping exists for 'pdc_dbagiefd4'
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly.

At that point I decided to go another route and try to use EasyBCD instead,


+Rob

---

### Post by jacobs444 on 2009-11-25
i think raid disks are referred to as: md instead of sd.

---

### Post by jacobs444 on 2009-11-25
should be md0 or something like that, not too much raid here.

---

