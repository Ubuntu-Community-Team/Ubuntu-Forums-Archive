---
title: "Windows 7 OEM dual boot problem"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by mcm307 on 2010-02-19
Hello, 

I have ubuntu 9.10 installed and working on a  Pangolin Performance system 76 laptop with a 120 gb hard drive. The ubuntu install has 65 GB free at the end of hard drive (done using Fdisk). It is STATA II hard drive. I got a dual boot to work on a upgrade for an HP desktop for my mom so I know the basics. 

Using the windows 7 OEM home premium I go the first steps i.e. time ect. Then it shows partitions (as 4 seperat objects 1 primary and 3 logical). The 2nd and 3rd are swap and more ubuntu space. The free space also comes up as logical and is the 4th partition. I try to install and says can not use this partition on the hard drive.I press the format and in changes to extention but still gives the same error(error log is not viewable in the install):o. All a can do is press a formate button in the install no menu. I formated as NTFS in gparted and it still would not work. I saw posts about bios and XP but they were old. 

Any help would be great.

---

### Post by presence1960 on 2010-02-19
Boot into ubuntu & run in terminal ```
sudo fdisk -l
```that is a lowercase L in -l. Post the output back here.

---

### Post by Mark Phelps on 2010-02-19
> **mcm307 said:**
> ... The free space also comes up as logical and is the 4th partition...
You can't install Win7 to a Logical partition.  It must be a primary partition.  Also, since Win7 uses Transactional NTFS filesystem format, you would do better removing the NTFS partition you created and installing to the free space -- letting Win7 do its own formatting.

Also, you do know this will wipe out the GRUB in the MBR and you will have to then replace it, right?

---

### Post by mcm307 on 2010-02-20
> **Mark Phelps said:**
> You can't install Win7 to a Logical partition.  It must be a primary partition.  Also, since Win7 uses Transactional NTFS filesystem format, you would do better removing the NTFS partition you created and installing to the free space -- letting Win7 do its own formatting.

Also, you do know this will wipe out the GRUB in the MBR and you will have to then replace it, right?


Thanks,

Does this mean I should move windows 7 to the front of the hard disk (making a blank spot) so it will be primary? Or should I wipe out ubuntu and start form scratch? 

And yes I know I will have to re-due grub.

I ran fdisk -l (sda7 was formated to NTFS using windows as it was blank before I ran the install)

/dev/sda1   *           1        4377    35158221   83  Linux
/dev/sda2            4378       24321   160200180    5  Extended
/dev/sda5            4378        4693     2538207   82  Linux swap / Solaris
/dev/sda6            4694       16035    91104583+  83  Linux
/dev/sda7           16036       24321    66555904    7  HPFS/NTFS

---

### Post by mcm307 on 2010-02-21
Fixed - just put windows 7 on the front of the Hard drive. :D

---

### Post by Mark Phelps on 2010-02-21
> **mcm307 said:**
> Fixed - just put windows 7 on the front of the Hard drive. :D

Glad to be of help.

---

