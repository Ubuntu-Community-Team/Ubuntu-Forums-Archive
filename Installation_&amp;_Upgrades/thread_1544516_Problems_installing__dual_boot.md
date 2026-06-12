---
title: "Problems installing : dual boot"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by donniesito on 2010-08-02
Ok. I've never seen this problem before, and other "instructions" haven't worked, so I'm bringing this problem to you all :)

I've been dual-booting Windows & Ubuntu for years now. Last Christmas I got a new laptop & was triple-booting XP, Win7 and Ubuntu. 

A few days ago I decided I no longer needed to be able to boot into XP, so I decided to erase the whole disc and install Ubuntu and Win7 fresh.

I booted up my GParted disc, erased the disk & created three partitions: One for Win7 (NTFS), one for Ubuntu (ext3), and one for swap. (I've done it this way countless times with no problems.)

I then installed Windows7, but it gave me errors saying it was the wrong partition type. I deleted the ntfs partition within Win install & recreated the partition; it still said it was the wrong partition type, and the only way I could make it work was to delete ALL partitions on the disk and create a single partition on the drive to install Windows. Once in Win, I used Partition Magic to resize and create the linux partition & the swap-partition.  (I installed Win WITHOUT it using the 100MB extra partition.)

Windows 7 installed fine after that & it's up and running (I'm using it now). SO - I booted up my Ubuntu disc & started the installation process. When it started the disk partitioning part of the install, it says "no operating system on the disk" and doesn't even see the separate partitions I had created.

I've never had this happen before; Ubuntu has always detected Windows, and always detected the partitions I created.

Any ideas guys?  I'm at a total loss, 'cause I've never had these problems before.

---

### Post by donniesito on 2010-08-02
I hate to do this, but -bump-

---

### Post by oldfred on 2010-08-02
Even though you just installed windows run chkdsk on the NTFS partition. Was this drive ever in RAID as that leaves metadata on a drive that interfers with an install. What BIOS setting do you have set on you hard drives, ide compatiblity ususally is the best.

Run this just to see partition list:

```
sudo fdisk -lu
```

---

### Post by 23dornot23d on 2010-08-02
Sounds like the partition table is messed up ..... 
I had a similar experience with two overlapping partitions ..... how it happened is a mystery
but there were reports that the resize of ext4 partitions messed up using a old version of gparted

The question is now how do you know if the disk layout is correct .....

I often fall back to Testdisk ....... to check the disk out ...... 

Thats the best I can think of at the moment ..... and you cannot show me a gparted screenshot

as it will just show one partition with nothing in it .......... 

See what Testdisk tells you ...... it just runs a check to start with ........ quit out of it after

I just like to see whats going on before making any major decisions with disk layouts  .......

---

### Post by donniesito on 2010-08-02
Here's the results of TestDisk. After I post this, I'm going to boot the Ubuntu Live disc and run fdisk and post the results.  I ran chkdsk (at the Win command prompt) and no errors were reported.


```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 22933 254 63  368434647
 2 E extended LBA         22934   0  1 30400 254 63  119957355
 5 L Linux                22934   1  1 29578 254 63  106751862
   X extended             29579   0  1 30400 254 63   13205430
 6 L Linux Swap           29579   1  1 30400 254 63   13205367
```

---

### Post by oldfred on 2010-08-02
I do not see anything in the test disk data. Did it report anything that seemed out of place?

---

### Post by donniesito on 2010-08-02
Here are the results of fdisk -lu

I'm not sure if this is normal or not, but I don't understand why I'm showing 4 partitions. When I run Partition Wizard in Windows, I still show only the original three I created, yet this fdisk result clearly shows four and gparted just shows the whole disk as unallocated space.  I'm entirely confused. -- And what happened to /sda3 and /sda4 ?

Also, to answer a previous question: No, this drive has never been in a RAID.

```
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't 
support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x61943c43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   368434709   184217323+   7  HPFS/NTFS
/dev/sda2       368434710   488392064    59978677+   f  W95 Ext'd (LBA)
/dev/sda5       368434773   475186634    53375931   83  Linux
/dev/sda6       475186698   488392064     6602683+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2010-08-03
Some computers with only one drive came with the BIOS set to RAID so raid metadata was written.

You can have 4 primary partitions sda1 thru sda4. You can convert any primary to an extended that then holds sda5 on up.

 GPT (GUID Partition Table) detected on '/dev/sda

GPT is not currently the standard but will be required for drives over 2TB and is used by Apple. I converted one of my smaller drives to GPT with gparted and installed without any issue but windows is on a different drive. I did manually partition in advance & created a small bios_grub partition. Then used manual install.

Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.
[http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html](http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html)
GRUB 2 boot.img will go into the protective MBR (using the first 446 bytes of the MBR). Use legacy boot in BIOS ?if EFI boot jumps directly to boot partiion.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by donniesito on 2010-08-03
> Some computers with only one drive came with the BIOS set to RAID so raid metadata was written.

As this is a notebook computer with one HD, and as the BIOS doesn't even have a RAID option, I do not believe this is the case.

I have had multi-boot set up on this machine previously. Until this happened I was triple booting between XP, Win7 and Ubuntu with absolutely no problems. After deciding I no longer needed XP, I decided to erase the drive and do fresh installs of Win7 and Ubuntu. This is when this all began.

I'd like to find a way to fix this that wouldn't involve having to erase and reinstall Windows and all my apps again.

> GPT is not currently the standard but will be required for drives over 2TB and is used by Apple. 

Ok. How do I change the GPT partition table? That may well be the problem, as I had experimented with a "hackintosh" build at one point, and now that you've mentioned it, I remember having to set the partition table to "GUID" when I was messing with that.  Hmmmmm

---

### Post by donniesito on 2010-08-03
Aaah. After looking into it, I've answered my own question. Unfortunately in order to change the partition table back to MBR, I'll have to reformat the disk :(  I think I knew that, but refused to believe it as I don't relish the thought of reinstalling everything ... again ...

While GParted didn't give me the option to specify a partition scheme (that I saw anyway), I booted the LiveCD again and used the "Disk Management" tool. That will allow me to change the scheme back to MBR, but only with reformatting.  Oh well, looks like I'll be reinstalling windows and all my apps tomorrow.

Thanks so much for your help, it's really appreciated!  Once I've redone the system, I'll post an update and if all is well, I'll mark this as solved.

Thanks again!!

---

### Post by oldfred on 2010-08-03
Gparted will let you create gpt partition type. On the create screen is an advanced button that lets you choose partition type.

I installed gpt on my 160GB drive and then installed Ubuntu without problems (I thought) Ubuntu worked just fine. Later when I tried booting a msdos partition from the gpt grub it would not boot. You have to add the part msdos line to grub to make it work. Grub also requires the bios boot partition. (bios_grub)

You may have created the hybrid version that has several MBR partitions at the beginning and is known to have issues.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by donniesito on 2010-08-03
Yeah - Once you mentioned GPT being an apple thing, I remembered about setting the partition type to guid and when I got home today I repartitioned to MBR type and reinstalled ubuntu and Win7.

Thanks again :-)

---

