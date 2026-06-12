---
title: "RAID 1 Setup"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by catlover2 on 2011-09-10
Hello, currently I have Windows XP, Windows 7, and Ubuntu 11.04 installed in that order on a 1TB harddrive.
/dev/sdc is the harddrive that I want to add to the[COLOR=Red] RAID 1[/COLOR] array, can I do so without destroying all my current partitions?
```
reed@Reeds-custom-computer:~$ sudo fdisk -l
[sudo] password for reed: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       32768    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2               5       60802   488352768   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes                                                                       
Sector size (logical/physical): 512 bytes / 512 bytes                                                                  
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                      
Disk identifier: 0x000d1511                                                                                            
                                                                                                                       
   Device Boot      Start         End      Blocks   Id  System                                                         
/dev/sdb1               1       19214   154328065    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *       19214       37439   146394112    7  HPFS/NTFS [COLOR=Red](XP)[/COLOR]
Partition 2 does not end on cylinder boundary.
/dev/sdb3           76154      121602   365060096    7  HPFS/NTFS [COLOR=Red](files)[/COLOR]
/dev/sdb4           56951       76154   154245120    7  HPFS/NTFS[COLOR=Red] (Win7)[/COLOR]
/dev/sdb5               1        1038     8334336   82  Linux swap / Solaris
/dev/sdb6            1038        5118    32768000   83  Linux[COLOR=Red] (root)[/COLOR]
/dev/sdb7            5118       19214   113223680   83  Linux [COLOR=Red](/home)[/COLOR]

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63decbe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               5      121602   976726016   83  Linux
/dev/sdc2               1           5       34816    b  W95 FAT32
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x454c7e6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           5       32768    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sdd2               5       60802   488352768   83  Linux
reed@Reeds-custom-computer:~$
```Thanks, catlover2

---

### Post by YesWeCan on 2011-09-10
Hi. Would you explain a little more about what you want to do? The thread title is RAID 1 but you say you want to add to a RAID 0. Is it that sda and sdd are a 500GB RAID1 and you want to convert your 1TB drive to a 2TB RAID0?
Please clarify. :)

---

### Post by catlover2 on 2011-09-10
Ouch, sorry, I have no RAID arrays currently, I want to set up /dev/sda and /dev/sdc in RAID 1.

Is it possible to preserve the data on /dev/sda/ while converting it to RAID 1?

I know how to set it up in the BIOS, but have no idea what to do software-wise.

---

### Post by YesWeCan on 2011-09-10
Sure, no problem.
sda is 500GB and has a linux partition and a FAT32 partition
sdc is 1000GB and also has a linux partition and a FAT32 partition

Which of these partitions do you want to keep? Which do you want in RAID1?

---

### Post by catlover2 on 2011-09-11
I want to preserve the data on _/dev/sdb _and put it in RAID 1 with _/dev/sdc_ (I don't care about the data on /dev/sdc)

I think I have my partitions straight now. :redface:

---

### Post by YesWeCan on 2011-09-11
> **catlover2 said:**
> I think I have my partitions straight now. :redface:

Good. :) The issue is that Windows and linux normally use different RAID systems. So you have two choices:
1) Make only your linux partitions RAID1 using linux raid, leaving your Windows partitions non raid.
2) Incorporate both disks into a fake raid1 (if your motherboard supports it) and reinstall both Windows and Ubuntu.

Ubuntu works best on linux raid, called mdraid or mdadm. It is less complicated to have Windows raid and Ubuntu raid completely separate.
For example, you could make a fake raid1 using your two 500GB drives for Windows and make a linux raid1 using the two 1TB drives.

With fake raid the whole drive has to be used. With linux raid only individual partitions are needed, which is much more flexible. So it is easy to leave Windows as is on sdb and mirror the Ubuntu sdb partitions to sdc.

---

### Post by catlover2 on 2011-09-11
OK, 

1. Is this fake raid you are talking about hardware raid, or something else?
2. How do I setup Linux RAID, if all I was mirroring was my Linux partitions?

I like the idea of the two 500GB drives for windows, but one is IDE, and the other SATA.

---

### Post by YesWeCan on 2011-09-11
> **catlover2 said:**
> OK, 

1. Is this fake raid you are talking about hardware raid, or something else?
Hardware RAID is when you use a dedicated PCI card that does everything and looks like a single drive to any OS. Very expensive.

Fake RAID is Window's software RAID with some mobo assistance. This is called dmraid in linux. This is what I assume you would use if you made a RAID 1 for Windows.

Linux RAID is software RAID that is partition or drive based and needs no mobo assistance. It is called mdraid or mdadm. This is recommended for linux systems.

> 2. How do I setup Linux RAID, if all I was mirroring was my Linux partitions?
Here is a procedure for doing it that would need a small change in step 5 so you keep your Windows partitions: [http://ubuntuforums.org/showthread.php?p=11185647&highlight=migrate#post11185647](http://ubuntuforums.org/showthread.php?p=11185647&highlight=migrate#post11185647)

You would create a degraded RAID on a partition on sdc and then copy your files to it. This becomes you main system and then you mirror it back to sdb.
Let me know if you would like to do this.

> I like the idea of the two 500GB drives for windows, but one is IDE, and the other SATA.
Yes you probably need two SATA drives to use the mobo RAID. Linux RAID would work so you could use these for Ubuntu. Obviously an EIDE drive will impact performance.

---

### Post by catlover2 on 2011-09-11
> **YesWeCan said:**
> Hardware RAID is when you use a dedicated PCI card that does everything and looks like a single drive to any OS. Very expensive.
so the built-in RAID on my motherboard will NOT do this?


> **YesWeCan said:**
> 
You would create a degraded RAID on a partition on sdc and then copy your files to it. This becomes you main system and then you mirror it back to sdb.
Let me know if you would like to do this.


Well, I suppose i would like to do this.

---

### Post by YesWeCan on 2011-09-11
> **catlover2 said:**
> so the built-in RAID on my motherboard will NOT do this? I doubt it - what is your mobo? This is a hardware controller: [http://www.adaptec.com/en-us/support/raid/sas_raid/sas-6405/](http://www.adaptec.com/en-us/support/raid/sas_raid/sas-6405/)
Many people confuse mobo RAID or "Host RAID" with true hardware RAID, including me...in the past.

[quote]Well, I suppose i would like to do this.
Have a go. Whenever you mess with partitions there is a chance of damaging something, so please back up any vital files off sdb, including Windows files, before you start. :)

[COLOR="Red"]The biggest risk is getting the drive names wrong.[/COLOR] So each time you boot make sure you know which drive is which and use the right names. They may change between booting off HD and booting off CD. I'll assume here that your original disk is sdb and the spare one is sdc.

**In step 5, do this instead:**
[COLOR="Navy"]Copy your sdb partition table to sdc
sudo sh -c "sfdisk -d /dev/sdb | sfdisk /dev/sdc"

Use GParted to change sdc partitions: delete sdb5, sdb6 and sdb7 and replace them with one large logical partition. **Do not change the size of the extended partition**. **DO NOT change sdc2 sdc3 or sdc4 yet** (because at step 26 the partition table will be copied back to sdb and these Windows partitions need to be preserved).

The new single, logical partition sdc5 will be your RAID partition and this is what you should use in step 10 in place of sdb1.[/COLOR]

---

### Post by catlover2 on 2011-09-11
OK, I'll report back when I finish, or fail :)

---

### Post by catlover2 on 2011-09-11
Oh boy,
```
reed@Reeds-custom-computer:~$ sudo sh -c "sfdisk -d /dev/sdb | /dev/sda"
[sudo] password for reed: 
sh: /dev/sda: Permission denied
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
reed@Reeds-custom-computer:~$
```??

same drives, but I unplugged the 500gb hds just to be safe, and the letters changed.

---

### Post by YesWeCan on 2011-09-11
Oh sorry. I made a mistake when I was typing that.
Should be:
```
sudo sh -c "sfdisk -d /dev/sdb | sfdisk /dev/sda"
```


Sensible move to unplug the 500GB. Keep an eye out for those letters changing.

---

### Post by catlover2 on 2011-09-11
And what does this mean?
```
root@ubuntu:~# mdadm -vC /dev/md0 --level=1 -n2 /dev/sda1 missing
mdadm: partition table exists on /dev/sda1 but will be lost or
       meaningless after creating array
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 0K
Continue creating array? 
Continue creating array? (y/n) y
mdadm: Defaulting to version 1.2 metadata
mdadm: ADD_NEW_DISK for /dev/sda1 failed: Invalid argument
root@ubuntu:~#
```

---

### Post by YesWeCan on 2011-09-12
> The new single, logical partition sdc5 will be your RAID partition and this is what you should use in step 10 in place of sdb1.

What you are trying to do is to make an array out of the single, logical partition that you made. This will probably be called sda5. The extended partition, sda1, is not a real partition but a "container" for logical partitions so you cannot use this.

Please stop at step 24 and post the output of sudo sfdisk -luS so I can check the new partition table is ok, before you copy it to sdb. :)

---

### Post by catlover2 on 2011-09-12
I'm not sure what the difference between these two commands are.

```
reed@Reeds-custom-computer:~$ sudo sfdisk -luM
[sudo] password for reed: 

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1         1+ 150712  150712- 154328065    5  Extended
                end: (c,h,s) expected (1023,254,63) found (1023,53,40)
/dev/sda2   * 150713  293675  142963  146394112    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,53,41)
                end: (c,h,s) expected (1023,254,63) found (1023,110,48)
/dev/sda3     597365  953868  356504  365060096    7  HPFS/NTFS
/dev/sda4     446735  597364  150630  154245120    7  HPFS/NTFS
/dev/sda5         2   8140   8139    8334336   82  Linux swap / Solaris
                end: (c,h,s) expected (1023,254,63) found (1023,212,7)
/dev/sda6      8142  40141  32000   32768000   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,244,40)
/dev/sda7     40143  150712  110570  113223680   83  Linux

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                               
   Device Boot Start   End    MiB    #blocks   Id  System                                                                                                                                                                                                                      
/dev/sdb1         1+ 150712  150712- 154328065    5  Extended                                                                                                                                                                                                                  
/dev/sdb2   * 150713  293675  142963  146394112    7  HPFS/NTFS                                                                                                                                                                                                                
/dev/sdb3     597365  953868  356504  365060096    7  HPFS/NTFS                                                                                                                                                                                                                
/dev/sdb4     446735  597364  150630  154245120    7  HPFS/NTFS                                                                                                                                                                                                                
/dev/sdb5         2   8140   8139    8334336   82  Linux swap / Solaris                                                                                                                                                                                                        
/dev/sdb6      8142  40141  32000   32768000   83  Linux                                                                                                                                                                                                                       
/dev/sdb7     40143  150712  110570  113223680   83  Linux                                                                                                                                                                                                                     
                                                                                                                                                                                                                                                                               
Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track                                                                                                                                                                                                                    
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                               
   Device Boot Start   End    MiB    #blocks   Id  System                                                                                                                                                                                                                      
/dev/sdc1         1     32     32      32768    b  W95 FAT32                                                                                                                                                                                                                   
/dev/sdc2        33  476939  476907  488352768   83  Linux                                                                                                                                                                                                                     
/dev/sdc3         0      -      0          0    0  Empty                                                                                                                                                                                                                       
/dev/sdc4         0      -      0          0    0  Empty 
```
```
reed@Reeds-custom-computer:~$ sudo sfdisk -luS
                                                                                                                                                                                                                                                                               
Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track                                                                                                                                                                                                                   
Warning: extended partition does not start at a cylinder boundary.                                                                                                                                                                                                             
DOS and Linux will interpret the contents differently.                                                                                                                                                                                                                         
Units = sectors of 512 bytes, counting from 0                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                               
   Device Boot    Start       End   #sectors  Id  System                                                                                                                                                                                                                       
/dev/sda1          4094 308660223  308656130   5  Extended                                                                                                                                                                                                                     
                end: (c,h,s) expected (1023,254,63) found (1023,53,40)                                                                                                                                                                                                         
/dev/sda2   * 308660224 601448447  292788224   7  HPFS/NTFS                                                                                                                                                                                                                    
                start: (c,h,s) expected (1023,254,63) found (1023,53,41)                                                                                                                                                                                                       
                end: (c,h,s) expected (1023,254,63) found (1023,110,48)                                                                                                                                                                                                        
/dev/sda3     1223403520 1953523711  730120192   7  HPFS/NTFS                                                                                                                                                                                                                  
/dev/sda4     914913280 1223403519  308490240   7  HPFS/NTFS
/dev/sda5          4096  16672767   16668672  82  Linux swap / Solaris
                end: (c,h,s) expected (1023,254,63) found (1023,212,7)
/dev/sda6      16674816  82210815   65536000  83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,244,40)
/dev/sda7      82212864 308660223  226447360  83  Linux

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          4094 308660223  308656130   5  Extended
/dev/sdb2   * 308660224 601448447  292788224   7  HPFS/NTFS
/dev/sdb3     1223403520 1953523711  730120192   7  HPFS/NTFS
/dev/sdb4     914913280 1223403519  308490240   7  HPFS/NTFS
/dev/sdb5          4096  16672767   16668672  82  Linux swap / Solaris
/dev/sdb6      16674816  82210815   65536000  83  Linux
/dev/sdb7      82212864 308660223  226447360  83  Linux

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1          2048     67583      65536   b  W95 FAT32
/dev/sdc2         67584 976773119  976705536  83  Linux
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty
reed@Reeds-custom-computer:~$**
```**

---

### Post by YesWeCan on 2011-09-12
sfdisk -luM displays in MB and -luS displays in sectors.

How far have you got through the procedure? What happened about sda5,6 & 7; you decided to keep all 3? I expected you to have replaced them with a single partition.

---

### Post by catlover2 on 2011-09-13
ok, I got to step 26 and 27, this is the output:
```
root@Reeds-custom-computer:~# hdparm -z /dev/sdb

/dev/sdb:
 re-reading partition table
 BLKRRPART failed: Device or resource busy
root@Reeds-custom-computer:~# mdadm /dev/md0 --add /dev/sdb1
mdadm: /dev/sdb1 not large enough to join array
root@Reeds-custom-computer:~#
```

by the way, everything looks fine from the degraded array.

---

### Post by YesWeCan on 2011-09-13
Did you read my post #15? You cannot use sdb1 because it is an extended partition. You also didn't combine your logical partitions into one for the array to use.

Please post the outputs of:
[COLOR=DarkSlateBlue]cat /proc/mdstat
sudo sfdisk -luS
sudo blkid

[COLOR=Black]and we'll see what needs adjusting.[/COLOR] :)
[/COLOR]

---

### Post by catlover2 on 2011-09-14
```
reed@Reeds-custom-computer:~$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0]
      292968181 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>
reed@Reeds-custom-computer:~$
```
```
reed@Reeds-custom-computer:~$ sudo sfdisk -luS
[sudo] password for reed: 

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63 585938744  585938682  fd  Linux raid autodetect
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1            63 585938744  585938682  fd  Linux raid autodetect
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/md0: 73242045 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md0: unrecognized partition table type
No partitions found

Disk /dev/dm-0: 561 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/dm-0: unrecognized partition table type
No partitions found

Disk /dev/dm-1: 4568 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/dm-1: unrecognized partition table type
No partitions found

Disk /dev/dm-2: 15273 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/dm-2: unrecognized partition table type
No partitions found

Disk /dev/dm-3: 15665 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/dm-3p1   ?   6579571 1924427647 1917848077  70  DiskSecure Multi-Boot
        start: (c,h,s) expected (409,142,41) found (365,99,47)
        end: (c,h,s) expected (1023,254,63) found (371,114,37)
/dev/dm-3p2   ? 1953251627 3771827541 1818575915  43  Unknown
        start: (c,h,s) expected (1023,254,63) found (288,115,51)
        end: (c,h,s) expected (1023,254,63) found (364,116,50)
/dev/dm-3p3   ? 225735265 225735274         10  72  Unknown
        start: (c,h,s) expected (1023,254,63) found (288,116,47)
        end: (c,h,s) expected (1023,254,63) found (372,101,51)
/dev/dm-3p4     2642411520 2642463409      51890   0  Empty
        start: (c,h,s) expected (1023,254,63) found (0,0,0)
        end: (c,h,s) expected (1023,254,63) found (0,0,0)
reed@Reeds-custom-computer:~$ 

```
```
reed@Reeds-custom-computer:~$ sudo blkid
/dev/sdb1: UUID="310b223e-40af-dc47-8b66-30751fd94e55" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/md0: UUID="GvN9TM-JG19-iJLT-1Guu-cXUn-Kyu8-K49diK" TYPE="LVM2_member" 
/dev/mapper/system-swap: UUID="d20a5842-e89e-4a2b-a12c-c5a0eeae9932" TYPE="swap" 
/dev/mapper/system-root: UUID="4c97ceae-c52d-4810-bf36-fb91a646215b" TYPE="ext4" 
/dev/mapper/system-home: UUID="12ef7262-f48e-4b1d-aea5-7e6f1e238dce" TYPE="ext4" 
/dev/mapper/system-vbox: UUID="4B823F4C0FB7017C" TYPE="ntfs" 
reed@Reeds-custom-computer:~$ 

```

---

### Post by YesWeCan on 2011-09-14
Well you seem to have gone off on your own here. What you appear to have now is 2 300GB RAID partitions and no Windows partitions.

The array is missing sda1 not sdb1. That's why your add command failed. Try
sudo mdadm --add /dev/sda1

Did you say that Ubuntu is running fine on the degraded RAID?


You'll need to reinstall Windows to the unallocated 700GB on one of the disks, if that's what you want.

---

### Post by catlover2 on 2011-09-14
```
reed@Reeds-custom-computer:~$ sudo mdadm --add /dev/sda1
mdadm: /dev/sda1 does not appear to be an md device
reed@Reeds-custom-computer:~$ 

```I didn't do anything to my knowledge that deleted my windows partitions, but I don't mind reinstalling.

Yes, Ubuntu is fine on the degraded RAID.

---

### Post by YesWeCan on 2011-09-14
> **catlover2 said:**
> ```
reed@Reeds-custom-computer:~$ sudo mdadm --add /dev/sda1
mdadm: /dev/sda1 does not appear to be an md device
reed@Reeds-custom-computer:~$ 

```I didn't do anything to my knowledge that deleted my windows partitions, but I don't mind reinstalling.

Yes, Ubuntu is fine on the degraded RAID.
Gawd what am I like?
[COLOR="DarkSlateBlue"]sudo mdadm /dev/md0 --add /dev/sda1[/COLOR]

That ought'a do it. Looks like you've set the LVM up right, etc. :)

---

### Post by catlover2 on 2011-09-14
OK, mdam: added /dev/sdc1. cool. (yes the letters changed again lol.)

In disk utility it says State: Degraded. Action: Recovering

I guess I'm done?

---

### Post by YesWeCan on 2011-09-14
Pretty close, I think. You'll need Grub installed in both disks so you can boot off either if you need to, so don't forget step 29 and choose /dev/sdb and /dev/sdc (or whatever the devices are called now!).

I'd be interested in seeing more details of your LVM volumes. If you have time would you mind posting the outputs of:
[COLOR="DarkSlateBlue"]sudo pvs
sudo vgs
sudo lvs[/COLOR]

---

### Post by catlover2 on 2011-09-14
```
reed@Reeds-custom-computer:~$ sudo pvs
[sudo] password for reed: 
  PV         VG     Fmt  Attr PSize   PFree
  /dev/md0   system lvm2 a-   279.39g 3.09g
reed@Reeds-custom-computer:~$ sudo vgs
  VG     #PV #LV #SN Attr   VSize   VFree
  system   1   4   0 wz--n- 279.39g 3.09g
reed@Reeds-custom-computer:~$ sudo lvs
  LV   VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  home system -wi-ao 117.00g                                      
  root system -wi-ao  35.00g                                      
  swap system -wi-ao   4.30g                                      
  vbox system -wi-ao 120.00g                                      
reed@Reeds-custom-computer:~$
```This might be better in a different thread, but how can I setup the 1.5TB drives that I will get tomorrow in a RAID 1 that both Windows and Linux can access?

Thank you for all your help!!

---

### Post by YesWeCan on 2011-09-14
That looks good. :) You now have a 300GB RAID-1/LVM partition on a pair of 1TB drives. The thing is like a layer cake:

file systems
LVM logical volumes
LVM volume group
mdraid device
disk partition

So if you ever want to enlarge it you have to enlarge each layer starting from the bottom and working up. Post back if you want to do this.


To have a RAID that both Windows and Ubuntu can access will require you to use Windows RAID (or Fake RAID). You have to configure the BIOS to make the two 1.5TB drives RAID-1 members, then install Windows with the appropriate drivers. Fake RAID makes a whole disk a RAID device. You then have to install Ubuntu to it, probably using the alternate install ISO. I don't know much about this but these are the things you'll need to Google for.
See also: [http://ubuntuforums.org/showthread.php?t=1574765&highlight=raid](http://ubuntuforums.org/showthread.php?t=1574765&highlight=raid)

Good luck.

---

