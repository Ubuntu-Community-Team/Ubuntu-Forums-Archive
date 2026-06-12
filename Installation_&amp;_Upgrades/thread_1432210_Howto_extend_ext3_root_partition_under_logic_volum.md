---
title: "Howto extend ext3 root partition under logic volume"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by lucret on 2010-03-17
Hi folks,

fdisk -l gives:

# fdisk -l

Platte /dev/sda: 100.0 GByte, 100030242816 Byte
255 Köpfe, 63 Sektoren/Spuren, 12161 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x6a2b0efb

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            5147        9973    38772877+   f  W95 Erw. (LBA)
/dev/sda3            9974       10738     6144862+  83  Linux
/dev/sda4            1021        5146    33142095    c  W95 FAT32 (LBA)
/dev/sda5            5147        6451    10482381   83  Linux
/dev/sda6            6452        9062    20972826    b  W95 FAT32
/dev/sda7            9063        9323     2096451   82  Linux Swap / Solaris
/dev/sda8            9324        9973     5221093+  83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge


My ubuntu root partition is sda8. 

sda2 is a logic partition with members sda5,6,7,8

sda1 is windows xp.

sda3 ist empty.

As you may imagine 5gb is to small as root partition in the long run. I want to enlarge sda8. 

What I tried so far:
As it is a logic volume, gparted did not work for me.
lvm did not recognise the logic volume:

lvm> lvdisplay 
  No volume groups found

I can't remeber with what tool I created the logic volume...

Thanks in advance for any suggestions!

---

### Post by srs5694 on 2010-03-17
I think you're confusing logical partitions with logical volume management (LVM) -- understandable given their names.

Logical partitions are ordinary partitions in the Master Boot Record (MBR) scheme that reside inside an extended partition. Logical partitions have numbers of 5 and above. They're ordinary partitions -- they're contiguous areas of the disk that are defined by the start sector and length, just like other ("primary") partitions.

LVM is a method of managing filesystems such that they can be handled more like files. You needn't be concerned with the location on the disk of a logical volume; you give it a name and let the LVM system figure out where to put it. This greatly simplifies things if you frequently add, delete, or modify filesystems (say, for trying new Linux distributions or because you add new disk space and want to expand a filesystem's size), but it adds a layer of complexity to filesystem management.

Based on your fdisk output, you seem to have logical partitions but no LVM configuration. You shouldn't use LVM tools to try to manage things, at least not with your configuration as it exists now. You do have enough space on /dev/sda3 to turn it into an LVM physical volume and move your Linux system onto it. You could then convert /dev/sda8 into a second LVM physical volume and expand your current system; however, this will take a lot of effort and you'll need to learn a lot about LVM, and perhaps other tools (such as tar), to do so. I wrote a piece on LVM for Linux Magazine a couple of years ago; you can read it [here](http://www.linux-mag.com/id/2453) if you're interested. (Read parts one and three; part two is about RAID and is irrelevant.)

One thing I notice about your current configuration, though, is that /dev/sda3 immediately follows /dev/sda8 in terms of disk space. Thus, it will probably be simpler for you to delete /dev/sda3 and extend /dev/sda8 into the space formerly occupied by /dev/sda3. You can do this with GParted, but you'll need to boot from an emergency disc to do this. Your Ubuntu installer might do, or you can try [PartedMagic](http://partedmagic.com) or [System Rescue Cd](http://www.sysresccd.org). Once in the rescue disc's system, you'll need to:


[list=1]
[*]Ensure that your current swap space isn't being used (type "swapoff /dev/sda7" in a shell prompt)
[*]Launch GParted
[*]Delete /dev/sda3
[*]Extend the logical partition /dev/sda2 to fill the cleared space
[*]Extend /dev/sda8 to fill the extra space that's now part of the extended partition
[*]Reboot
[/list]


In theory this should go smoothly, but of course practice often puts the lie to theory when it comes to computers!

Best of luck, whatever you do.

---

### Post by lucret on 2010-03-18
Thanks a lot for all the ideas and the correction of my mistunderstanding!

I took the -in my sense- most simple approach.

I just had not come across the idea myself of resizing the logical partition hda2 and afterwards resizing the partition hda8. But it worked great!

Now every thing is fine.

Thanks again :)

---

