---
title: "6 partitions on 1 hard disk (ubuntu, puppy and ntfs)"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by vampire666eng on 2007-11-25
Would it be possible to have on one hard disk:

1) an NTFS partition (just data, not operating system)

2) an uBuntu installation with
- two ext3 partition
- one swap partition

3) a puppy linux installation with
- one ext2 partition
- one swap partition

So I would have 6 partition on a hard disk. As I have understood the maximum partitions one can have on a hard disk is 4, but I can somehow get around this limitation with the extended partition that can hold other partitions.

How would you suggest me to do this?

Partition 1: ntfs (only data)
Partition 2: extented ---> with the 3 uBuntu partition inside (two ext3 and one swap)
Partition 3: ext2 ---> Puppy
Partition 4: swap --->Puppy

or 

Partition 1: extended ---> with the ntfs (only data) and the 2 Puppy partition (etx2 and swap) inside.
Partition 2: ext3 ---> uBuntu
Partition 3: ext3 ---> uBuntu
Partition 4: swap ---> uBuntu

Or what else? Then how should I put the singular partition (active, primary or logical)?

Thanks a bunch.:)

---

### Post by Pumalite on 2007-11-25
Up to 4 primary partitions. But you need one to make one extended and in that extended, as many logicals as you want.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://partedmagic.com/](http://partedmagic.com/)
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by vampire666eng on 2007-11-25
Cool. Thanks. That explains a lot.

Just one thing...does the extended partition still have the 4 partition limitation or I can store more then 4 partition in it?

I mean on a hard disk I can have 4 primary partition, one of these I make it extended. In this extended partition I could have how many I want? Even more then 4 (so the 4 partition limit doesn't effect the extended partition)? If this is correct, what is the purpose of not having an extended partition as a default? Wouldn't it be better if the hard disk is immediately partitioned as one extended partition, so I won't have problems from the start (having the need of more then 4 partitions)?

EDIT: If operating system can be booted in extended partitions...I really can't see the need of non-extended partitions. :)

---

### Post by Pumalite on 2007-11-25
Ubuntu works great in logicals and you can have as many as you want. Space is the only limit. That's the convenience of logicals.

---

### Post by vampire666eng on 2007-11-25
Thanks again.;-)

Just found this (even if it doesn't mention linux it helps understand partitions "logic"):
[http://www.theeldergeek.com/hard_drives_01.htm](http://www.theeldergeek.com/hard_drives_01.htm)

---

### Post by Pumalite on 2007-11-25
Pretty good link.

---

### Post by markusf21 on 2007-11-25
you only need 1 swap partition

---

### Post by vampire666eng on 2007-11-25
> **markusf21 said:**
> you only need 1 swap partition

I can use the same swap partition for the two linux operating systems (Puppy and uBuntu)? I don't need to use one for each systems? Even if one linux is in the extended partition and the other in a primary partition?

That would be nice (less space used). If this is the case, do I have to specify something when I install the second linux operating system or I just don't create the swap and everything is taken care of (the secon linux knows where to look).

Thanks.

---

### Post by markusf21 on 2007-11-25
It should mount it by itself

---

### Post by vampire666eng on 2007-11-25
Ok. Thanks a lot for telling me this.

I won't install another swap for my second linux installation. ;)

---

### Post by sandysandy on 2007-11-25
hi guys
hope i am not barging in.

i have 3 linux flavors installed- open SUSE 10.3, Edubuntu 7.10 and Mandriva. (in addition to Win XP)
all of them were installed in default option so i have 3 swap partitions.
Can i delete 2 swap partitions or are the different distros linked to their individual swap partitions in some way.

the output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] is as follows:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155   133114589    40957717+   f  W95 Ext'd (LBA)
/dev/sda3       133114590   179301464    23093437+   7  HPFS/NTFS
/dev/sda4       179301465   312576704    66637620   83  Linux
/dev/sda5        51199218    86188724    17494753+   7  HPFS/NTFS
/dev/sda6        93578751    96663104     1542177   82  Linux swap / Solaris
/dev/sda7        96663168   116005364     9671098+  83  Linux
/dev/sda8   *   116005428   132279209     8136891   83  Linux
/dev/sda9       132279273   133114589      417658+  82  Linux swap / Solaris
/dev/sda10       86188788    90140714     1975963+  83  Linux
/dev/sda11       90140778    90943964      401593+  82  Linux swap / Solaris
/dev/sda12       90944028    93578624     1317298+  83  Linux

Partition table entries are not in disk order


regards.

---

### Post by louieb on 2007-11-25
> **sandysandy said:**
> ... i have 3 linux flavors installed...so i have 3 swap partitions.
Can i delete 2 swap partitions or are the different distros linked to their individual swap partitions in some way.
They mount whatever swap partition(s) in /etc/fstab.   
You can change the /etc/fstab file in all three to use the same swap partition.

---

### Post by sandysandy on 2007-11-25
> **louieb said:**
> They mount whatever swap partition(s) in /etc/fstab.   
You can change the /etc/fstab file in all three to use the same swap partition.

how do i change the /etc/fstab file.

regards

---

### Post by david_kt on 2007-12-07
> **sandysandy said:**
> how do i change the /etc/fstab file.

regards

From ubuntu, open terminal (Applications>Accesories>Terminal)
In terminal type:
```
gksudo gedit /etc/fstab
```

enter and type your password as requested. It will open gedit and edit the swap as mentioned before. After that, you could recover the unused swap using gparted.

DK

---

