---
title: "Error: 'grub_puts_'"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by kennystoy on 2010-04-30
I have an error message from upgrading from  Ubuntu 9.10 to 10.4.  
It says error: the symbol 'grub_puts_' not found
Grub rescue >
I just recently went from xp to ubuntu , 2 weeks ago.
I know very little about ubuntu , so I really need help , but in laymans  terms.

---

### Post by Chriis on 2010-04-30
oki, same error in here, can`t help, but i`m waiting with you for some :)

---

### Post by kennystoy on 2010-04-30
Hmm, well maybe if I put more info it might help.
Gateway 3.0 mghz 200gig drive with another 500gig with no os on it.
thanks for reply, don't feel alone now.
Kenny

---

### Post by Chriis on 2010-04-30
unfortulately, i`ve upgraded, so i do not have a live-cd to reinstall grub,.. i`m stock :(

---

### Post by k508 on 2010-04-30
I had the EXACT same problem yesterday but I fixed it by reinstalling the GRUB via means of the 9.10 liveCD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
```

**SIMPLEST - Copy GRUB 2 Files from the LiveCD**

This is a quick and simple method of restoring a broken  system's GRUB 2 files. The terminal is used for entering commands and  the user must know the device name/partition of the installed system  (sda1, sdb5, etc). The problem partition is located and mounted from the  LiveCD. The files are then copied from the LiveCD libraries to the  proper locations and MBR. It requires the least steps and fewer command  line entries than the following methods. 

[LIST=1]
[*]Boot to  the LiveCD Desktop (Ubuntu 9.10 or later).
[*]Open  a terminal by selecting *Applications, Accessories, Terminal* from  the menu bar.
[*]Determine the partition  with the Ubuntu installation. The *fdisk* option "-l" is a  lowercase "L".
[LIST=1]
[*][FONT=Courier New]sudo  fdisk -l[/FONT]If the user isn't sure of the partition, look for one of  the appropriate size or formatting. Running sudo  blkid may provide more information to help locate the proper partition,  especially if the partitions are labeled. The device/drive is designated  by *sdX*, with *X* being the device designation. *sda*  is the first device, *sdb* is the second, etc. For most users the  MBR will be installed to *sda*, the first drive on their system.  The partition is designated by the *Y*. The first partition is 1,  the second is 2. Note the devices and partitions are counted  differently.
[/LIST]
 
[*]Mount the partition  containing the Ubuntu installation. [FONT=Courier New]sudo mount  /dev/sd''xY'' /mnt[/FONT]Example: *sudo mount  /dev/sd**a1*** Note: If the user has a separate /boot partition,  this must be mounted to */mnt/boot*
[*]Run  the grub-install command as described below. This will reinstall the  GRUB 2 files on the mounted partition to the proper location and to the  MBR of the designated device. 
[FONT=Courier New]sudo  grub-install --root-directory=/mnt/ /dev/sdX[/FONT]Example:  *sudo grub-install --root-directory=/mnt/ /dev/sd**a***
[*]Reboot
[*]Refresh the GRUB 2 menu  with sudo update-grub
[*]If the  user wishes to explore why the system failed, refer to *[Post-Restoration  Commands]("https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands")* section below.
[/LIST]

```This was copied from somewhere on the Ubuntu site, normally I'd give you a link but I had this saved in my Google Docs, so you're lucky =P

---

### Post by kennystoy on 2010-04-30
I've got the 9.10 dvd that Ifirst installed Ubuntu with.
Could I use this to boot with?

---

### Post by kennystoy on 2010-04-30
Thanks so much , will try it ... and post results.
Kenny

---

### Post by k508 on 2010-04-30
> **kennystoy said:**
> I've got the 9.10 dvd that Ifirst installed Ubuntu with.
Could I use this to boot with?
Yes, just boot the 9.10 CD and select the 'Try before installing' option at the top. Then just follow the instructions I posted a minute ago.

It might look like a lot of work, but a lot of those instructions are explanations there's only really like 2-3 steps in it.

Edit: I added the link to the original page where I found that information. Hope it helps you.

---

### Post by kennystoy on 2010-04-30
trying it now ,got install-device not specified message will work on it..
thanks so much again.

---

### Post by kennystoy on 2010-04-30
up and running but will not update grub

---

### Post by caonima on 2010-04-30
Had the same problem. The cause for me was the grub was reinstalled to a different hd. For example, the grub was installed in MBR of /dev/sda before upgrade, and it was in MBR of /dev/sdb after upgrade. Just try to boot from a different hd and see if the error is gone.

---

### Post by kennystoy on 2010-04-30
Chriis did it help you any?
At least I have a working but wounded computer.
Hope you can get yours running.

---

### Post by Chriis on 2010-05-01
it was the first time i " upgraded" ,..i've managed to get the .iso file and did a fresh install,..now it's up and running

---

### Post by kennystoy on 2010-05-02
Boot loader was on other hdd , working now that yall for the help ,will keep plugging alone .
ex-xp user

---

### Post by BJohann on 2010-05-04
Maybe i am so unfotunate to be running my OS on 2 SSD Raid 0 disks..

How do I mont a Raid 0 partition? Is this **** possible to fix without a total reinstallation of everything?

This is a picture of ~fdisk -l and blkid:

sudo fdisk -l

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             857        3895    24410767+  fd  Linux raid autodetect
/dev/sda2   *           1         856     6875788+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f175

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             854        3892    24410767+  fd  Linux raid autodetect
/dev/sdb2               1         853     6851691   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029765

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       97281   781409601   83  Linux
/dev/sdc2           97282      121601   195350400    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2613aad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30394   244139773+  83  Linux

Disk /dev/sde: 4100 MB, 4100980736 bytes
16 heads, 63 sectors/track, 7946 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00015cec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        7947     4004832+   b  W95 FAT32


ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="bf50ee90-d76b-4299-909e-557ab338bf68" TYPE="ext3" 
/dev/sda1: UUID="58106625-a3ff-1770-2677-4b1244eafe08" TYPE="linux_raid_member" 
/dev/sda2: UUID="38f8dece-38fa-4175-9a8a-5732827490c8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="58106625-a3ff-1770-2677-4b1244eafe08" TYPE="linux_raid_member" 
/dev/sdb2: UUID="39c9089b-9ebd-4be7-9fb1-29e7c59435df" TYPE="swap" 
/dev/sdc1: LABEL="Div800" UUID="bf80cdc4-11c9-455d-8ed3-8d91c4a2ec5e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: LABEL="Privat200" UUID="edaf6fed-1aaa-4e3a-8499-0c524f346248" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="Gamle250" UUID="83f93034-6e82-4e6f-b97d-a30e05ac2701" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde1: LABEL="CRUZER BJ" UUID="F25C-889F" TYPE="vfat" 
ubuntu@ubuntu:~$ 



-I am about to hate Linux more than Microsoft-

---

### Post by LucianoP on 2010-05-05
I had exactly the same problem, upgraded without an ISO, got the same error, and the followed the tip from k508
It worked fine
= )

---

