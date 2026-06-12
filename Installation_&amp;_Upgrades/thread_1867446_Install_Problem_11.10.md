---
title: "Install Problem 11.10"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by Alderonn on 2011-10-22
I have tried 5-6 times to get this to install. I have a WD 500GB HD, with winXP on 135GB of it. I would like to install Ubuntu on the 330+GB that remain. I need a 64 bit OS for the new upgrades i have coming in the mail. (8GB Ram)

Ok, so I have tried to install both with USB and CD. It always says that i don't have enough disk space. its not finding the hard drive.

i partitioned the 330+ GB in NTFS, then in FAT32, then in EXT3. with no luck. I also tried it with no partition whatsoever. 

How can i get this fixed?

i would really prefer to install on the whole disk but i can't even get it to install at all at the moment.

And yes it does let me use the try it. i can get on firefox and use the apps. just can't get past the second page of the install.. Please help

---

### Post by Quackers on 2011-10-23
Are you using raid? 
Are you using SATA3 ports?

From the live desktop please post the output of ```
sudo fdisk -lu
``` if there is any :-)

---

### Post by Alderonn on 2011-10-23
Disk /dev/sda: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     7837695     3918832    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


That is what it shows.  (in this case using the USB )

I am not using raid.
I am using Sata3
I can switch to Sata2 if that will help.

---

### Post by Quackers on 2011-10-23
It's not picking up your hard drive at all. There was a problem with the Marvell sata controller and sata3 ports, which I don't know whether it's fixed or not.
Try the sata2 ports and see if the drive is then recognised.

---

### Post by westie457 on 2011-10-23
> **Alderonn said:**
> Disk /dev/sda: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     7837695     3918832    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


That is what it shows.  (in this case using the USB )

I am not using raid.
I am using Sata3
I can switch to Sata2 if that will help.

Hi switching to SATA2 will help as Ubuntu in general has issues with SATA3 drives in SATA3 ports. Using a SATA3 drive is okay.

@ Quackers Well spotted.

---

### Post by Alderonn on 2011-10-23
You guys are AWESOME. i pulled the side off my case and plugged into the SATA2 port number 1 and it installed perfectly first try.   

I do have a Marvel SATA controller on this Asrock 770 Extreme 3 Mobo.

Count this one as solved.

---

### Post by Quackers on 2011-10-23
Excellent! Glad to hear that :-)
Please mark the thread as solved using the Thread Tools tab near the top of this page.

---

