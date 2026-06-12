---
title: "What does &quot;/boot on a seperate partition&quot; means?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by earfer on 2009-12-05
Lets get stright to the point~!

What does...

> 
[LIST]
[*]If you have /boot on a separate partition, that need's to be mounted aswell.  For reference, /dev/sda2 will be used.
[/LIST]
$ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these up, pay attention to the output of FDISK*

means?

I mean what does it mean when it said "If you have /boot on a separate partition"? is it a ext? or a swap partition?

Heres what my hardrive looks like...

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             774       16904   129572257+  83  Linux
/dev/sda2   *       16905       16917      102400    7  HPFS/NTFS
/dev/sda3           16917       29652   102294528    7  HPFS/NTFS
/dev/sda4           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris

```

Thanks in Advance~

---

### Post by wesleybailey on 2009-12-05
When you install linux, some distributions give you the option to install different parts of the linux os, on different mount points.

In this example all the linux files reside on the partition /sda1
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.9G  905M  7.6G  11% /

```

You could also split up the linux files like this.
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.9G  905M  7.6G  11% /
/dev/sda2             8.9G  905M  7.6G  11% /boot

```

Hope this explains that quote

---

### Post by presence1960 on 2009-12-05
> **earfer said:**
> Lets get stright to the point~!

What does...



means?

I mean what does it mean when it said "If you have /boot on a separate partition"? is it a ext? or a swap partition?

Heres what my hardrive looks like...

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             774       16904   129572257+  83  Linux
/dev/sda2   *       16905       16917      102400    7  HPFS/NTFS
/dev/sda3           16917       29652   102294528    7  HPFS/NTFS
/dev/sda4           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris

```

Thanks in Advance~
within your sda1 partition is a directory named /boot. Most people install Ubuntu this way which is the default. But for various reasons some create a separate boot partition in which that directory which would have been in / (root) of ubuntu now becomes a separate partition of it's own.

One good reason to utilize this is when Ubuntu will be installed outside the area readable by older BIOS versions(usually 137 GB but less for really older BIOS). This is a limitation of BIOS not Ubuntu. If there is not a BIOS update that will fix this then one must utilize the separate boot partition in order to get ubuntu to boot. 

Example: you have a BIOS with a readable area limit of 137 GB. You have a 250 GB hard disk and your existing partitions take up the first 200 GB. If you install Ubuntu after those your BIOS will not be able to read the files necessary to boot Ubuntu and thus will get a GRUB error. For those not willing to redo their partition table and put Ubuntu on the front of the disk they can shrink a partition and create a boot partition from the freed  space which will fall within the 137 GB area readable by BIOS. This will allow Ubuntu to boot.

---

### Post by earfer on 2009-12-05
Yes thankyou. But may i ask how do you found out which is on boot?

---

### Post by presence1960 on 2009-12-05
> **earfer said:**
> Yes thankyou. But may i ask how do you found out which is on boot?

I don't quite understand this question.

When you install Ubuntu and use the manual option at the Prepare disk space window you create  a boot partition (if you haven't already done so), highlight it and set the Filesystem type, tick the format box and in the drop down box for mount point select /boot. When you set all partitions and are ready to install the files that are in boot directory on a default install will be placed in the separate boot partition. This is how to create an install utilizing a separate /boot partition.

Hope this answer it. if not rephrase the question please.

---

### Post by wesleybailey on 2009-12-05
.

---

### Post by earfer on 2009-12-05
> **presence1960 said:**
> within your sda1 partition is a directory named /boot. Most people install Ubuntu this way which is the default. But for various reasons some create a separate boot partition in which that directory which would have been in / (root) of ubuntu now becomes a separate partition of it's own.

One good reason to utilize this is when Ubuntu will be installed outside the area readable by older BIOS versions(usually 137 GB but less for really older BIOS). This is a limitation of BIOS not Ubuntu. If there is not a BIOS update that will fix this then one must utilize the separate boot partition in order to get ubuntu to boot. 

Example: you have a BIOS with a readable area limit of 137 GB. You have a 250 GB hard disk and your existing partitions take up the first 200 GB. If you install Ubuntu after those your BIOS will not be able to read the files necessary to boot Ubuntu and thus will get a GRUB error. For those not willing to redo their partition table and put Ubuntu on the front of the disk they can shrink a partition and create a boot partition from the freed  space which will fall within the 137 GB area readable by BIOS. This will allow Ubuntu to boot.


Im sorry but can you please simplyfy that? from expert to nub or midy?
Ive lost you~!
[U]
some more random info:

[/U]- in the code sda 2 is system reserved and sda 3 is windows 7.
- sda 2 has a flag = boot

---

### Post by earfer on 2009-12-05
> **presence1960 said:**
> I don't quite understand this question.

When you install Ubuntu and use the manual option at the Prepare disk space window you create  a boot partition (if you haven't already done so), highlight it and set the Filesystem type, tick the format box and in the drop down box for mount point select /boot. When you set all partitions and are ready to install the files that are in boot directory on a default install will be placed in the separate boot partition. This is how to create an install utilizing a separate /boot partition.

Hope this answer it. if not rephrase the question please.

aha sorry thats for wesleybailey at first but dw about it. it was a stupid question.

---

### Post by presence1960 on 2009-12-05
> **earfer said:**
> Im sorry but can you please simplyfy that? from expert to nub or midy?
Ive lost you~!
[U]
some more random info:

[/U]- in the code sda 2 is system reserved and sda 3 is windows 7.
- sda 2 has a flag = boot

That is the simple version, maybe reading on BIOS will help you undestand.

System reserved in Windows 7 is the partition that contains windows 7 boot files. I may be incorrect but I think Windows 7 does that when installing to a clean hard disk. If installing it to an existing partition I don't think it creates a system reserved partition. At least it didn't when I installed Win 7 RC to an existing partition on my rig.

---

### Post by earfer on 2009-12-05
> **presence1960 said:**
> That is the simple version, maybe reading on BIOS will help you undestand.

System reserved in Windows 7 is the partition that contains windows 7 boot files. I may be incorrect but I think Windows 7 does that when installing to a clean hard disk. If installing it to an existing partition I don't think it creates a system reserved partition. At least it didn't when I installed Win 7 RC to an existing partition on my rig.

ok lemme give more info about what i mean...(i guess i wasn't "straight to the point*)

I installed Ubunut 9.10 (Grub 2) on the whole entire disk. 
Then i made another partition that is for win 7.
I installed it i did the guide to reinstall grub 2 but didnt get far.

[html]https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD[/html]

I stopped when it told me to...

> 
[LIST]
[*]If you have /boot on a separate partition, that need's to be mounted aswell.  For reference, /dev/sda2 will be used.
[/LIST]
$ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these up, pay attention to the output of FDISK*

I didnt know what /boot and which sda it was. 

hope i made a little clearer for everyone.

---

### Post by garvinrick4 on 2009-12-05
Is this what you want. Every partition to boot on sda1 called system.
Extended sda3 is Linux and inside of extended partitions is 2 linux partions 
and 2 swap partitions. But all the boots are in the grub2 on
partition sda1.  sda2 is windows 7   sda4 is what linux sees as
a vista boot, it is the D: drive in windows the image of the O.S.
to reinstall window 7 with.
So 1 for boot.  1 for windows. 1 for D: in windows.
1 large extended partition for linux.
2 partitions inside of linux partion and 2 swap partitions in side of extended partition.

4 a grand total of 8 partitions for 3 OS's.
The 2 swap partitions are for virtual memory basically in the 2 linux systems.
All Windows are NTSF format. 

Gparted software will do it all for you when you load Ubuntu software.



Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order
rick@rick-laptop:~$

---

### Post by presence1960 on 2009-12-05
> **earfer said:**
> ok lemme give more info about what i mean...(i guess i wasn't "straight to the point*)

I installed Ubunut 9.10 (Grub 2) on the whoe entire disk. 
Then i made another partition that is for win 7.
I installed it i did the guide to reinstall grub 2 but didnt get far.

[HTML]https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD[/HTML]

I stopped when it told me to...



I didnt know what /boot and which sda it was. 

hope i made a little clearer for everyone.
If you don't have a separate boot partition skip that set of instruction. You want to use sda1 and then install GRUB to /dev/sda.

---

### Post by earfer on 2009-12-05
> **garvinrick4 said:**
> Is this what you want. Every partition to boot on sda1 called system.
Extended sda3 is Linux and inside of extended partitions is 2 linux partions 
and 2 swap partitions. But all the boots are in the grub2 on
partition sda1.  sda2 is windows 7   sda4 is what linux sees as
a vista boot, it is the D: drive in windows the image of the O.S.
to reinstall window 7 with.
So 1 for boot.  1 for windows. 1 for D: in windows.
1 large extended partition for linux.
2 partitions inside of linux partion and 2 swap partitions in side of extended partition.

4 a grand total of 8 partitions for 3 OS's.
The 2 swap partitions are for virtual memory basically in the 2 linux systems.
All Windows are NTSF format. 

Gparted software will do it all for you when you load Ubuntu software.



Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order
rick@rick-laptop:~$

WAHHH!!! DONT GET YOU!!!!:-k

> **presence1960 said:**
> If you don't have a separate boot partition skip that set of instruction.

But how do you check if you DO or do not have a seperate boot partition?

---

### Post by garvinrick4 on 2009-12-05
sudo fdisk -l                     that is a small L not an l


The partition with the * is the boot partition. How is that.

---

### Post by earfer on 2009-12-05
> **garvinrick4 said:**
> sudo fdisk -l                     that is a small L not an l


The partition with the * is the boot partition. How is that.

 So thats the seperate partition? aka (/boot)?

so do i type in the terminal:

```
$ sudo mount /dev/sda2 /mnt/boot
```

like that?

---

### Post by u.b.u.n.t.u on 2009-12-05
> **earfer said:**
> I installed Ubunut 9.10 (Grub 2) on the whole entire disk. 
Then i made another partition that is for win 7.


Better to install Windows 7 on the entire HDD and then install Ubuntu 9.10 on a partition(s).

---

### Post by presence1960 on 2009-12-05
> **earfer said:**
> So thats the seperate partition? aka (/boot)?

so do i type in the terminal:

```
$ sudo mount /dev/sda2 /mnt/boot
```

like that?

NO...

This is fdisk from your original post:

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1             774       16904   129572257+  83  Linux
/dev/sda2   *       16905       16917      102400    7  HPFS/NTFS
/dev/sda3           16917       29652   102294528    7  HPFS/NTFS
/dev/sda4           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris
```

You have 2 Linux partitions- root (sda1) & swap (sda5). You do not have a separate boot partition. You would know anyway if you did have a separate boot partition because you would have specifically had to create one manually during the install of Ubuntu. Just skip those instructions.

The * in fdisk denotes a boot flag not a boot partition. Windows needs a boot flag turned on to be able to boot, Linux does not.
One last time you do not have a boot partition disregard the set of instructions dealing with the extra boot partition.

---

### Post by darkod on 2009-12-05
Just do what presence says. You would know if you have separate /boot because you would need to create that manually during install.
Your /dev/sda2 is the 100MB partition win7 creates, you can see it's ntfs type.

---

### Post by garvinrick4 on 2009-12-05
Where is the D: partition for Windows 7? If that was XP would
look right? Should there not be a System about 100 meg. A Windows
7 and a D: Linux reads the D: in 7 as Vista it cannot tell the difference but that is the image of 7's OS.
Then an extended, a linux and a swap. That would be 6 and their
are 5 in her fdisk.

What am I missing here?

---

### Post by darkod on 2009-12-05
> **garvinrick4 said:**
> Where is the D: partition for Windows 7? If that was XP would
look right? Should there not be a System about 100 meg. A Windows
7 and a D: Linux reads the D: in 7 as Vista it cannot tell the difference but that is the image of 7's OS.
Then an extended, a linux and a swap. That would be 6 and their
are 5 in her fdisk.

What am I missing here?

Don't know.
/dev/sda1   /
/dev/sda2   100MB win7 boot (doesn't show with letter in win7)
/dev/sda3   win7 system C:
/dev/sda5   swap

What are you looking for?

---

### Post by garvinrick4 on 2009-12-05
If it is Windows 7 I was looking for the D: partition that it needs
to put its image in. The recovery is a default. The D: for now Linux sees
as Vista in boot menu. Cannot tell deference for time being. It is not in her
"fdisk -l".     I saw the Vista in my install of 7 so investigated. No big deal.

---

### Post by darkod on 2009-12-05
I think you are mixed up by the fact that most branded machines these days ship with recovery/restore partition with an image of the system as it comes from factory/dealers. But this is not always the case. Plus you are free to delete that recovery partition if you have another way to install your windows OS if you need to.
Personally I consider these partitions useless. Most of them literary wipe the hdd and create the same setup as when it was bought. Which means it would not only destroy a second OS but it will also destroy all your windows data even if you never had linux and use it only for windows. That is no way to restore OS, IMHO. If it shipped with a Windows DVD, that would give you options to really repair your OS. But try telling that to MS and explain how much inconvenience they create for their own customers who paid for their license fair and square.

---

### Post by garvinrick4 on 2009-12-09
Have truple boot with Windows 7, 9.10 and 10.04.  Used the image of windows 7 in grub called Vista and reinstalled Windows 7 as an experiment to see if it just reinstalled on its
own partition or cleaned whole drive. It just saw its NTSF partition and left my Extended
partition alone. Boot partition came out fine. D: partition fine, just overwrote the C: partition with fresh install. THIS WAS MY OWN EXPERIMENT AND DO NOT GUARANTEE ANY
OTHERS. I just wanted see what happened, curiosity.
 Machine a Hp- G71-34 OUS    Had to make my own Disks when opened box. 3 DVD's a one opportunity thing to make disk image. Can make all the repair disks I want. Used
g-parted to configure partitions. Linux see's D: drive as Vista in GRUB2 it is your Windows
7 image on internal Disk. Also has a recovery boot which requires your self made recovery
disk.  
  I do seem to use Linux OS all the time now but with size of drives now a days I see no reason to not leave a partition for OS that came loaded on machine.

---

