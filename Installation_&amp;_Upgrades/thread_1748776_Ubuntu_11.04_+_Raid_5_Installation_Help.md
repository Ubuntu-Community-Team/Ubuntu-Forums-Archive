---
title: "Ubuntu 11.04 + Raid 5 Installation Help"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by skyrider55 on 2011-05-03
Hey everyone,

I've been trying for about 11 hours to install ubuntu 11.04 in a raid 5 configuration, and this is embarrassing because I'm a computer engineer and getting infuriated. 

All I want, is to install linux in a raid 5 configuration on 3 2TB western digital drives using the GUI interface in 11.04.

I'm using the 11.04 additional desktop installation iso.

If someone could post what the Partitions should look like on the 3 drives so that I can get past the error of it being unable to install grub boot manager and critical erroring, I'd be very grateful. Right now, I've essentially tried:

md0_raid5
- 512 MB's unusable
- 4TB Free Space

Drive 0
- boot (1MB)
- swap (8GB)
- raid (2TB)
Drive 1
- swap (8GB)
- raid (2TB)
Drive 2
- swap (8GB)
- raid (2TB)

so this is essentially what it looks like from memory, and grub bootloader can't install and the install process fails.

I'm so lost, and I'm doing 11 hours of work not to install windows onto this HTPC.

---

### Post by klavmanian on 2011-05-10
I tried this same setup yesterday with 4 drives. This was done from the Ubuntu 11.04 alternate installer (64 bit). Each attempt was in a raid 5 and then raid 10 configuration. No luck. During GRUB installation, I got the error; "cannot install grub to /dev/mapper".

Here is a similar situation with Ubuntu 10.10
[http://ubuntuforums.org/showthread.php?t=1710394](http://ubuntuforums.org/showthread.php?t=1710394)

I'll have to try the /boot on a RAID 1 tonight but I thought booting from RAID 5 and LVM was possible with grub2.

Any thoughts / solutions on this topic are greatly appreciated.

---

### Post by Quackers on 2011-05-10
Something that worked with raid0 and 11.04 was booting to the live desktop and then installing kpartx. The install then worked (after choosing the /dev/mapper "drive" for the grub installation - if you don't it will default to /dev/sda).
I don't know if that will help in your circumstances.

---

### Post by klavmanian on 2011-05-10
I thought the alternate installer was required to install the entire system onto a linux software raid/lvm.

Note that the idea here is to install onto a software RAID array, with all partitions on RAID and LVM (including root and boot).

I have gotten RAID 1 to work with the installation method mentioned. However, the idea is to get this to work with RAID 5 (or RAID 10 in my case).

I will give the graphical install a shot, but I don't believe software RAID / LVM is supported. (I haven't done a graphical install for a while so its worth a shot :D)

---

### Post by klavmanian on 2011-05-11
So last night I concluded that there is most likely something wrong with the 11.04 install process dealing with these configurations. I successfully installed Debian Server 6.0.1a in RAID 10 (linux software raid with lvm).

When it asked me to install the grub, it defaulted to /dev/sda

Sorry I couldn't be of further help, but all I needed to work was a .deb based distribution. So Debian Server it is.

---

