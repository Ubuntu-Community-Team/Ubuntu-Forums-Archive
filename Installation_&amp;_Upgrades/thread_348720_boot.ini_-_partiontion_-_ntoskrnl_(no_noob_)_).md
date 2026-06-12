---
title: "boot.ini - partiontion - ntoskrnl (no noob :) )"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by xor.be on 2007-01-29
Hey all

I'm having a situation with my partitions.

I had win xp, and i needed to install 2k3 and ubuntu for school work. (i already have ubuntu for some time as primary OS on another laptop)

I manually partitioned my drive,and installed w2k3 just fine.

During the first partitioning i left some space for ubuntu,and installed it on there (after partitioning again for swap)

As you might have guessed, xp boots fine,and i receive the ntoskrln error while trying to boot 2k3.
Before i did any research,i tried manually copying the ntoskrln from the disc,after that i tried the expand command, no luck

Now,i know the problem lies with the boot.ini file,but i don't see what the problem is.

My 2k3 is located on hd6 (i confirmed this with multiple commands)
After updating the boot.ini file with the right partition, the windows boot menu has added a (Windows Default) option, wich results in some message about hardware misconfiguration, and the original w3k option still shows the ntoskrnl problem.

Now i am quite stuck, since i'm not sure what to change in the boot.ini file

This is the boot.ini content = 

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(6)\WINDOWS="Windows Server 2003, Enterprise" /fastdetect 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect




This is my partition info = 

> Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4116    22820332+   f  W95 Ext'd (LBA)
/dev/hda3            4117        4864     6008310   83  Linux
/dev/hda5            1276        3187    15358108+   7  HPFS/NTFS
/dev/hda6            3188        4079     7164958+   7  HPFS/NTFS
/dev/hda7            4080        4116      297171   82  Linux swap / Solaris


Now,the only thing i can think of,is that there is some issue due that my hda6 seems to be a "subpartition" of hda2 ( it was shown like that in the ubuntu partition menu).

Can anybody please advise me as how to proceed,since any online research stops after people figure out to update the boot.ini :)

Thx a mil ! :)

---

### Post by xor.be on 2007-01-29
Hey all

I'm having a situation with my partitions.

I had win xp, and i needed to install 2k3 and ubuntu for school work. (i already have ubuntu for some time as primary OS on another laptop)

I manually partitioned my drive,and installed w2k3 just fine.

During the first partitioning i left some space for ubuntu,and installed it on there (after partitioning again for swap)

As you might have guessed, xp boots fine,and i receive the ntoskrln error while trying to boot 2k3.
Before i did any research,i tried manually copying the ntoskrln from the disc,after that i tried the expand command, no luck

Now,i know the problem lies with the boot.ini file,but i don't see what the problem is.

My 2k3 is located on hd6 (i confirmed this with multiple commands)
After updating the boot.ini file with the right partition, the windows boot menu has added a (Windows Default) option, wich results in some message about hardware misconfiguration, and the original w3k option still shows the ntoskrnl problem.

Now i am quite stuck, since i'm not sure what to change in the boot.ini file

This is the boot.ini content =

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(6)\WINDOWS="Windo ws Server 2003, Enterprise" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect

This is my partition info =


> Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1275 10241406 7 HPFS/NTFS
/dev/hda2 1276 4116 22820332+ f W95 Ext'd (LBA)
/dev/hda3 4117 4864 6008310 83 Linux
/dev/hda5 1276 3187 15358108+ 7 HPFS/NTFS
/dev/hda6 3188 4079 7164958+ 7 HPFS/NTFS
/dev/hda7 4080 4116 297171 82 Linux swap / Solaris
Now,the only thing i can think of,is that there is some issue due that my hda6 seems to be a "subpartition" of hda2 ( it was shown like that in the ubuntu partition menu).

Can anybody please advise me as how to proceed,since any online research stops after people figure out to update the boot.ini

Thx a mil !

---

### Post by xor.be on 2007-01-29
update  = ok, i removed the 3 from the default (since it was the linux partition anyway).

i know its noobish,but i still tried to associate every partition with the w2k3, although i know its partition 6.

now i still get the ntoskrnl error, even after expanding it.
the xp (wich is also in the win loader, which i can call up just fine trough grub) works very well

i just don't understand,the boot ini file is pointing to the right partition :(

also,like i mentionned,in the ubuntu partitioner, my hda6 shows as a "subpartition" of hda2.

could this have smth to do with it.

help please :(

---

### Post by xor.be on 2007-01-29
update  = ok, i removed the 3 from the default (since it was the linux partition anyway).

i know its noobish,but i still tried to associate every partition with the w2k3, although i know its partition 6.

now i still get the ntoskrnl error, even after expanding it.
the xp (wich is also in the win loader, which i can call up just fine trough grub) works very well

i just don't understand,the boot ini file is pointing to the right partition :(

also,like i mentionned,in the ubuntu partitioner, my hda6 shows as a "subpartition" of hda2.

could this have smth to do with it.

help please :(

---

### Post by louieb on 2007-01-29
You have described how you machine is set up and that you have a problem. But for the life of me I can't tel what the problem is. Is it that can't boot Ubuntu? w2k?
Are you using ntldr or grub for your boot manager?

---

### Post by xor.be on 2007-01-29
Thx for answering louieb.

As i mentionned =
> 
As you might have guessed, xp boots fine,and i receive the ntoskrln error while trying to boot 2k3.

So , ubuntu,and xp start up fine,but not win 2003.

the grub loader gives me the choice between booting ubuntu ,and has a pointer to the windows boot manager (i guess ntldr) wich offers xp and 2003.

The boot loader ini file is =

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(6)\WINDOWS="Windo ws Server 2003, Enterprise" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect

The problem is that the windows 2003 server option is pointing to the right partition (6), but i still get can't boot.
( i actually tried changing it to every partition i have,no luck)

The only thing i  think could cause the problem is that hda6 showed up under hda2 in the ubuntu partitioning menu.

( i already tried reinstalling win2003 when this happens yesterday,but that deleted the grub loader,and upon installing that one again, the win2K3 problem appears again).

so,as you might see,i'm quite stuck :(

---

### Post by louieb on 2007-01-29
You mentioned that w2k 
> Now,the only thing i can think of,is that there is some issue due that my hda6 seems to be a "subpartition" of hda2 ( it was shown like that in the Ubuntu partition menu).According to the fdisk output you posted you are correct.  
Let me define  some terms first. 
Logical partition: what you called a subpartition most of the stuff you read will refer to this as a logical partition. Your hda6 is this type of partition.
Extended partition: This type of partition serves as a container for logical partitions. Your hda2 is an extended  partition. You can have one and only one extended  partition and it counts against the limit of four primary partitions.  
Primary partition:   Primary partition information is stored in the master boot record [(MBR)]("http://www.cpqlinux.com/mbr.html"). Because the size of the MBR is fixed so is the number of primary partitions a drive can have. Four is the number of primary partitions a given drive can have. 

The reason I want you to know something about partitions is I have read that some Microsoft operating systems don't work if they have been installed in a logical partition.  
Don't ask me why cause I don't know. 

So my wild as guess of the day: I think you can get all three to boot  if you swap the install partitions  of Ubuntu and w2k. 
That is let the w2k3 installer format  hda3 NTFS and install w2k in hda3.
Then  let the Ubuntu installer format hda6 ext3 and Install Ubuntu there. Any Linux system will happily run from a logical partition.

---

