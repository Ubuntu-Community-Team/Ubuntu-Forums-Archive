---
title: "Ubuntu doesnt recognise existing partitions"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by gpushkar on 2010-02-06
I am trying to install ubuntu 9.10 on an system which already has XP installed. I had used Ubuntu earlier but when I installed XP ( in an attempt to dual boot) I seem to have lost the Ubuntu Installation. 

But the problem is GParted or the Ubuntu installer dont recognize the existing partitions but instead see it as an empty unallocated drive. I have a 120GB hard disk. 

Below is the extract after fdisk: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa8a60b
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa8a60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4403    35359169+   7  HPFS/NTFS
/dev/sda2            4403        5810    11302025    7  HPFS/NTFS
/dev/sda3            5811        6896     8723263+   7  HPFS/NTFS
/dev/sda4            6897       14594    61834185    f  W95 Ext'd (LBA)
/dev/sda5            6897        6951      441748   82  Linux swap / Solaris
/dev/sda6            6952        9502    20480000    7  HPFS/NTFS
/dev/sda7            9502       13890    35249152    7  HPFS/NTFS
/dev/sda8           13891       14593     5646847    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

   

Also this is how the disk Utility in Ubuntu sees my system: ( See attachment) 
[IMG]file:///D:/Screenshot.png[/IMG]

---

### Post by lemming465 on 2010-02-07
I'm not sure what the deal with the absurd amount of supposedly free disk space is, but if you look at the left-hand pane of the palimpsest display you'll see basically the same disk layout as fdisk is showing.  I don't know if this system has more than one hard drive in it; if so, the scenario where fdisk sees disks but the ubuntu 9.10 ubuquity live CD installer doesn't is typical of systems which currently or historically had some kind of firmware/BIOS/fake RAID setup.  A quick test is to open a terminal window from the live CD an run:```
sudo apt-get remove dmraid
```.  Then try the installer; it may be happier about the disks.  Note that if windows is actually depending on the firmware RAID across multiple disks, you will destroy everything if you try install Linux without using dmraid.  If there is only one hard drive, you will probably be OK.

Losing access to a Linux install temporarily after doing anything major (install, service pack, ...) with a dual-boot windows system is typical; Microsoft thinks it owns the MBR (first disk sector master boot record) and overwrites it freely.  You can use a bootable Linux CD to re-run your preferred boot loader install to correct this after the fact.

---

### Post by gpushkar on 2010-02-08
I tried 
sudo apt-get remove dmraid

Still it shows the same thing. Installer says no operating systems found and shows the entire hard disk ( I have only one hard disk) as empty!

---

### Post by gpushkar on 2010-02-08
This is what i get after doing fdisk: 
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fa8a60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    70718401    35359169+   7  HPFS/NTFS
/dev/sda2        70719488    93323537    11302025    7  HPFS/NTFS
/dev/sda3        93337713   110784239     8723263+   7  HPFS/NTFS
/dev/sda4       110784240   234452609    61834185    f  W95 Ext'd (LBA)
/dev/sda5       110784303   111667798      441748   82  Linux swap / Solaris
/dev/sda6       111681536   152641535    20480000    7  HPFS/NTFS
/dev/sda7       152643584   223141887    35249152    7  HPFS/NTFS
/dev/sda8       223142850   234436543     5646847    7  HPFS/NTFS


```


Any help hugely appreciated!!

---

### Post by darkod on 2010-02-08
You already have the maximum of 4 partitions on the hdd. You see sda1 to sda4. Logical are marked from sda5 upwards.
The installer detects this and doesn't offer you much options except erasing the whole hdd and manual option (in which you would still have to delete some partition which I don't recommend during the installer).
Even if it did recognize you have XP you're still stuck because you can't create 5th partition.
You need to sit down and reconsider the layout of your hdd. After you have made a decision about the new partitions layout, use the live desktop first and Gparted which is on it. That is a very good partition manager. Delete the partition you selected and ubuntu will be able to be installed. Also you need to consider how much space you want for ubuntu.

---

### Post by gpushkar on 2010-02-08
OK. But the problem is in GParted , I dont see any partitions. Just a huge unallocated space. For example take a look at the attached screenshot. How do I proceed without affecting my data in the first partition - sda1 ?

---

### Post by darkod on 2010-02-08
You're right, something is weird. Can you boot XP, does it work fine?

---

### Post by gpushkar on 2010-02-08
Yes. I can boot into XP. No issues there!

---

### Post by darkod on 2010-02-08
> **gpushkar said:**
> Yes. I can boot into XP. No issues there!

I don't know. I'm not experienced enough to advise you what to do next, I don't want you to lose your data maybe. I hope someone else will jump in.

---

### Post by gpushkar on 2010-02-08
:) thanks anyways mate! Seriously hope some one jumps in to help!

---

### Post by lemming465 on 2010-02-08
Could we also get the output of (live CD OK):```
sudo cfdisk -Pt /dev/sda
sudo sfdisk -V /dev/sda
```
The *fdisk -lu* output looks fairly sane by itself, but there is something weird going on to confuse gparted.  

Echoing darkod's comment, you have occupied pretty much the whole disk with NTFS partitions.  If you are willing to sacrifice one of them, move all the data off, change the partition type to 0x83 ("t" command in fdisk), pick "manual" partitioning in the installer, and format it as type ext3 or ext4, usage root (directory "/").  The minimum useful size for running standard Ubuntu installs is about 5GB; more if you want to play with extra applications or source code.

---

### Post by gpushkar on 2010-02-09
```

ubuntu@ubuntu:~$ sudo cfdisk -Pt /dev/sda
FATAL ERROR: Bad primary partition 1: Partition ends after end-of-disk
ubuntu@ubuntu:~$ sudo sfdisk -V /dev/sda
Warning: partition 2 extends past end of disk
ubuntu@ubuntu:~$ 

```

I managed to create primary partition using fdisk. Here is the output of that 
```

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa8a60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4403    35359169+   7  HPFS/NTFS
/dev/sda2            6897       14594    61834185    f  W95 Ext'd (LBA)
/dev/sda5            6897        9502    20929609    7  HPFS/NTFS
/dev/sda6            9502       13890    35249152    7  HPFS/NTFS

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (4403-14593, default 4403): 
Using default value 4403
Last cylinder, +cylinders or +size{K,M,G} (4403-6896, default 6896): 
Using default value 6896

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa8a60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4403    35359169+   7  HPFS/NTFS
/dev/sda2            6897       14594    61834185    f  W95 Ext'd (LBA)
/dev/sda3            4403        6896    20032919   83  Linux
/dev/sda5            6897        9502    20929609    7  HPFS/NTFS
/dev/sda6            9502       13890    35249152    7  HPFS/NTFS

Partition table entries are not in disk order

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.


```

Even after doing this, GParted or Ubuntu installer dont recognise existing partitions.

I have data sda5 sda6. If I remove sda2 in fdisk, i can see that sda5 & 6 no longer appear.

---

### Post by darkod on 2010-02-09
Another option is to go to the hdd manufacturer website and they should have some tools to diagnose the hdd and repair it if necessary.
It seems that ubuntu is far more sensitive to bad sectors than windows is. While windows might run even on a bad disk (until it completely crashes), ubuntu seems unwilling to run on it, from what I've seen around as comments.
Run the manufacturer tool to make sure it doesn't report anything. It's always wise to have a backup before operations like that.

---

### Post by anubis2497 on 2010-02-09
try installing xp first then ubuntu.

---

### Post by gpushkar on 2010-02-09
yes. I think there may be some bad sectors which are causing this problem. I m presently running the diagnostic program from the HDD manufacturer ( Seagate).   

@anubis: I already have installed XP on sda1

---

### Post by gpushkar on 2010-02-09
New update. My HDD is screwed. 

```

ubuntu@ubuntu:~$ sudo ./st -G /dev/sg0
Starting generic long (full sequential verify) test (234441647 blocks) on drive /dev/sg0 (^C will abort test)
    VERIFY  failed on block 2352128   Sense data = 11/00/00
TEST FAILED at block 3 on drive /dev/sg0


```

:frown:

---

### Post by anubis2497 on 2010-03-11
hey u might need a new hard disk because my brother recently had a similer issue and had to end up geting a new hard disk for his laptop i recomend doing that after backing up your dada if possible.

---

### Post by gpushkar on 2010-03-11
hmm... I think i ll ve to buy a new HDD. Problem is its a Laptop, so HDD s are damn expensive!

---

