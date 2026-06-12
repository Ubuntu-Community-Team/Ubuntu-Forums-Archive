---
title: "Dual Boot, No Grub Menu"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by jusmurph on 2007-05-15
I have given up on my last boot effort and decided to give it a fresh start.

First I installed windows xp (sp2 disk) on hard drive 2 partition 1 (formatting using the windows installer)
That worked so then I installed 7.04 AMD64 on hard drive 2 partition 2 with a swap on partition 3 (these too were carved from the spare space with the linux partitioner)

There is a total of 4 hard drives on the machine.

Problem
When I boot up the machine… it launches straight into windows xp. How do I go about fixing this setting up the menu to let me decided which I want to boot?

Thanks

---

### Post by logos34 on 2007-05-15
SOunds like grub was installed on a different disk than your winxp/feisty drive (drive 2).  Change the BIOS to boot from drive 1, or whatever disk was set first in hard disk boot priority at time of install. Can you get the grub menu that way?

edit: the ubuntu installer (live cd) will put grub on the first detected hard disk ('hd0'), even though your install is on another disk (in this case 'hd1' or the second drive)

---

### Post by mikewhatever on 2007-05-15
You can look for grub using you Ubuntu installation CD. Boot from the CD, open the terminal and type> sudo grub
then type > find /boot/grub/stage1

You can probably boot Ubuntu using super grub CD [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
then we'll need the output of the following commands
> cat /boot/grub/device.map
> sudo fdisk
> cat /boot/grub/menu.lst 

---

### Post by jusmurph on 2007-05-16
I believe my disk 1 is deing... and I am going to send it back... should i just move disk 2 to disk 1 and re install linux... 

will this fix it?

will windows fall to this?

I am happy to re install as i only have installed the two OS'

---

### Post by mikewhatever on 2007-05-16
In your first post, it says both Ubuntu and Windows are on disk 2, so how is disk 1 relevant, and why would you need to reinstall.

---

### Post by jusmurph on 2007-05-16
Logos34 made mention of disk 1.

(sorry I am a noob, atleast for the time being)


Disk 2 definitely has Windows and Ubuntu on it. I will be able to post the commands tonight, 4 hours from now.:)

---

### Post by confused57 on 2007-05-16
Boot up the live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

Once you determine which is your root partition, you could mount it from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda2 /media/ubuntu
```
substitute your root partition for hda2, then you can get the output of:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
gksudo gedit /media/ubuntu/boot/grub/device.map
```

menu.lst is short for menu.list

Added:  Mike's suggestion of Super Grub Disk is an excellent idea...

---

### Post by jusmurph on 2007-05-16
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3824    30716248+   7  HPFS/NTFS
/dev/sda4   *       10200       24321   113434965    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825        7471    29294527+  83  Linux
/dev/sdb3            7472        7714     1951897+  82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 4110 MB, 4110416896 bytes
33 heads, 63 sectors/track, 3861 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        3862     4014063    6  FAT16
```

Entering the two gksudo commands from there... just launch anoter blank window?

---

### Post by confused57 on 2007-05-16
Did you mount your Ubuntu root partition before entering the 2 gksudo commands?:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb2 /media/ubuntu
```

---

### Post by jusmurph on 2007-05-17
I'm going to assume i made an error. 

However i went into my bios and changed the boot order of hard drives to hard drive 1 and grub launched just fine. I can boot either os though atm i have the two following issues:

Which is great except there is a chance that i will be removing this hard drive from my system (It's dieing).
So that means i lose grub, so how do i move it?

Also windows is giving me a BSoD... so I may in time need to reinstall that which will probably take a poop all over grub right?

---

### Post by mikewhatever on 2007-05-17
> **jusmurph said:**
> I'm going to assume i made an error. 

However i went into my bios and changed the boot order of hard drives to hard drive 1 and grub launched just fine. I can boot either os though atm i have the two following issues:

Which is great except there is a chance that i will be removing this hard drive from my system (It's dieing).
So that means i lose grub, so how do i move it?

Also windows is giving me a BSoD... so I may in time need to reinstall that which will probably take a poop all over grub right?

Here is the page to reinstall grub using a live cd [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
you should also need to reinstall grub after reinstalling Windows. It seems to be a good idea to remove the 'dying' hdd before reinstalling grub.

---

### Post by jusmurph on 2007-05-20
Got it,

Thank you kindly for your help!:popcorn:

---

