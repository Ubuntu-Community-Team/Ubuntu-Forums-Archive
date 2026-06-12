---
title: "Ubuntu install not seeing partitions"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by JMC2543 on 2011-03-30
I am trying to duel boot win 7 and ubuntu 10.10. I have been dealing with this all day and cant figure out what's is going on. I create the partitions in windows and then reboot using a CD but when I go to select a oartition ubuntu do sent see any partitions its a totally blank drive. I have even wiped the drive totally and tried fresh install of windows and then creating partitions', even booted into the live CD area and it still dosent see any partitions just a blank drive. What am I doing wrong, or what is going wrong to cause this?


Running windows 7 x64 trying to install 10.10 x64

---

### Post by Sean Moran on 2011-03-30
I take it you've created one or more NTFS partitions on your hard disk drive.  If you boot from the Live-Cd and open System->Administration->GParted, you should see the state of your hard disk partitions.  Make sure there are 8+ GB of unallocated space, so that you can create the Linux partitons for root (/) and SWAP.

---

### Post by JMC2543 on 2011-03-30
I have tried creating the partitions through the live CD as well. I can leave the free space unallocated or create a new drive out of it in windows, ubuntu sees no partitions what so ever. The live CD and the installer sees a blank drive, it does not see windows at all, or any partitions.

---

### Post by Sean Moran on 2011-03-30
> **JMC2543 said:**
> I have tried creating the partitions through the live CD as well. I can leave the free space unallocated or create a new drive out of it in windows, ubuntu sees no partitions what so ever. The live CD and the installer sees a blank drive, it does not see windows at all, or any partitions.

I'm quite surprised that you're unable to see the NTFS partition/s from the Live-CDs GParted utility.  Is it possible to run up the Live-CD again and open a terminal, and type: **df** ?  That should provide a listing of the partitions on the hard disk/s, and perhaps give some clues as to why GParted doesn't show the partitions that Windows does.

I'll try to stay online for the next hour or so until we can sort this out.

---

### Post by JMC2543 on 2011-03-30
Sure I will take a look and get back to you.

---

### Post by Rubi1200 on 2011-03-30
Also from the LiveCD, post the output of this command:

```
sudo fdisk -lu
```

(lowercase L not 1)

---

### Post by JMC2543 on 2011-03-30
Ok this is really odd. I typed in df and got



ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   2028236     53236   1975000   3% /
none                   1988020       308   1987712   1% /dev
/dev/sr0                711674    711674         0 100% /cdrom
/dev/loop0              672384    672384         0 100% /rofs
none                   2028236       100   2028136   1% /dev/shm
tmpfs                  2028236        12   2028224   1% /tmp
none                   2028236        96   2028140   1% /var/run
none                   2028236         4   2028232   1% /var/lock
ubuntu@ubuntu:~$ 

and then I typed in the second command and got 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82aa84b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       55285   443968512    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           55285       55807     4195328    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           55807      121602   528493568    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           55285       55807     4194304    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a59606a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

I even went into GPart and sure enough one empty drive, but in disk utility it sees the partitions. But I didnt check it but its usually the trend that the installer will not see the partitions eather.

---

### Post by Sean Moran on 2011-03-30
> **JMC2543 said:**
> Ok this is really odd. I typed in df and got



ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   2028236     53236   1975000   3% /
none                   1988020       308   1987712   1% /dev
/dev/sr0                711674    711674         0 100% /cdrom
/dev/loop0              672384    672384         0 100% /rofs
none                   2028236       100   2028136   1% /dev/shm
tmpfs                  2028236        12   2028224   1% /tmp
none                   2028236        96   2028140   1% /var/run
none                   2028236         4   2028232   1% /var/lock
ubuntu@ubuntu:~$ 

and then I typed in the second command and got 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82aa84b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       55285   443968512    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           55285       55807     4195328    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           55807      121602   528493568    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           55285       55807     4194304    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a59606a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

I even went into GPart and sure enough one empty drive, but in disk utility it sees the partitions. But I didnt check it but its usually the trend that the installer will not see the partitions eather.


Is it possible to delete the extra NTFS partitions apart from the first two, (where I assume you've got Windows installed across a small boot partition and a main partition on /dev/sda2), or is there data or recovery data on those that Windows requires?  The objective being to simplify things down to the two partition for WIndows, and the rest unallocated space, and then we can use GParted to resize the Windows partitions slightly to match the cylinder boundaries, and fixup that mess with the little extended partition with only one logical, and set things right.

---

### Post by JMC2543 on 2011-03-30
The way i had the partitons set up were 

sda1 windows boot (windows install created it when I partitioned in windows installer)

sda2 root

sda3 not sure I didnt create that one

sda4 windows 7

sda5 swap

as far as using GPart, like I said it sees the entire drive as empty. GPart does not see any partitions says all of it is unallocated. I can try again and start with the windows partitions and the rest unallocated if need be.

---

### Post by JMC2543 on 2011-03-30
im tying to take screen shots but cant figure out where they are located after capture.

---

### Post by Rubi1200 on 2011-03-30
You appear to have a GPT partition table which is probably why GParted cannot see it.

There are ways to deal with this, but I suggest you wait for the experts on this one.

I will send a message to one of them to take a look and offer advice.

Please be patient.

It would also be useful if you could post the results of the boot info script. There is a link at the bottom of my post with instructions.

When you post back, please highlight all the text and then click on # in the toolbar to wrap with code tags (makes for easier reading).

---

### Post by JMC2543 on 2011-03-30
Oh joy I get the pain in the butt issue. Thanks for your help guys. I will get that info posted here shortly.

---

### Post by Sean Moran on 2011-03-30
> **JMC2543 said:**
> The way i had the partitons set up were 

sda1 windows boot (windows install created it when I partitioned in windows installer)

sda2 root

sda3 not sure I didnt create that one

sda4 windows 7

sda5 swap

as far as using GPart, like I said it sees the entire drive as empty. GPart does not see any partitions says all of it is unallocated. I can try again and start with the windows partitions and the rest unallocated if need be.
It looks as though your /dev/sda3 is setup as an extended partition, with /dev/sda5 another small NTFS partiton within that.  It might be easier if it was possible to delete /dev/sda5, /dev/sda4, and /dev/sda3 to make some space available to redo that part from the Live-CD.  I'm worried that you might have something important for Windows on /dev/sda4 though.  If not, then probably best to wipe those two primaries and the single logical partition, and recreate the required Linux partitions in GParted.

---

### Post by JMC2543 on 2011-03-30
> **Sean Moran said:**
> It looks as though your /dev/sda3 is setup as an extended partition, with /dev/sda5 another small NTFS partiton within that.  It might be easier if it was possible to delete /dev/sda5, /dev/sda4, and /dev/sda3 to make some space available to redo that part from the Live-CD.  I'm worried that you might have something important for Windows on /dev/sda4 though.  If not, then probably best to wipe those two primaries and the single logical partition, and recreate the required Linux partitions in GParted.
  Lol yea sda4 is important that is windows itself. I have a 1TB drive somewhat split equity.

---

### Post by JMC2543 on 2011-03-30
Reposting updated info below

---

### Post by Sean Moran on 2011-03-30
> **JMC2543 said:**
> Lol yea sda4 is important that is windows itself. I have a 1TB drive somewhat split equity.
In that case, best to delete the root partition /dev/sda2, so you can use that one as a nice little ext4 partition, and then use what's left for your extended on /dev/sda3, into which you can fit a small SWAP partition, but Windows doesn't like to have to create Linux partitons as far as I know.
.

---

### Post by JMC2543 on 2011-03-30
> **Sean Moran said:**
> In that case, best to delete the root partition /dev/sda2, so you can use that one as a nice little ext4 partition, and then use what's left for your extended on /dev/sda3, into which you can fit a small SWAP partition, but Windows doesn't like to have to create Linux partitons as far as I know.
.

I went ahaid and went back to windows and deleted all but the root partition and then the two windows partitions. After I boot back up I will repost my boot script and if a thing has changed.

---

### Post by JMC2543 on 2011-03-30
Here is my current setup of all partitions. I went ahaid and ran a new df, sudo fdisk, and the boot script.
df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   2028236     54984   1973252   3% /
none                   1988020       304   1987716   1% /dev
/dev/sr0                711674    711674         0 100% /cdrom
/dev/loop0              672384    672384         0 100% /rofs
none                   2028236       112   2028124   1% /dev/shm
tmpfs                  2028236        48   2028188   1% /tmp
none                   2028236        88   2028148   1% /var/run
none                   2028236         4   2028232   1% /var/lock

```sudo fdisk -lu:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d42792f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   629358591   314575872    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       629358592  1953519615   662080512    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a59606a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048   488394751   244196352    7  HPFS/NTFS

``````
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => HP/Gateway is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   629,358,591   629,151,744   7 HPFS/NTFS
/dev/sda3         629,358,592 1,953,519,615 1,324,161,024   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3618CB5F18CB1CAD                       ntfs       System Reserved               
/dev/sda2        7CC4DC23C4DBDE08                       ntfs                                     
/dev/sda3        1B24D50E2A0BA7E4                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdf1        0C6CCCD56CCCBAAA                       ntfs       Backup                        
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by Rubi1200 on 2011-03-30
Did you read my previous post about GPT and waiting?

---

### Post by JMC2543 on 2011-03-30
> **Rubi1200 said:**
> Did you read my previous post about GPT and waiting?

Yep sure did. I got that script up for you and ill be watching for a update from someone else. i appreciate your help.

---

### Post by JMC2543 on 2011-03-30
Can i expect a shout back tonight or probally during regular business hours?

---

### Post by Rubi1200 on 2011-03-30
> **JMC2543 said:**
> Can i expect a shout back tonight or probally during regular business hours?
Not sure what time zone you are in, but the person I sent a message to, srs5694, is in the States so...

---

### Post by JMC2543 on 2011-03-30
> **Rubi1200 said:**
> Not sure what time zone you are in, but the person I sent a message to, srs5694, is in the States so...

That will work perfect as I am in the states as well. Its like 4am here atm so. Thanks so much for your help.

---

### Post by srs5694 on 2011-03-30
It appears that your disk used to use the GUID Partition Table (GPT) partitioning system (most commonly used by Mac OS X), but that's been incompletely overwritten by the older Master Boot Record (MBR) scheme. Technically, this is legal, and your disk should be treated as an MBR disk; however, some tools, such as GParted, tend to get confused when they see a valid MBR setup and leftover GPT data. Such tools either say that the disk is completely blank or they show the old GPT data.

You can wipe the old GPT data in a number of ways. The easiest is to use my [FixParts](http://www.rodsbooks.com/fixparts/) utility. You can download the latest version [here.](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/) You can use the Windows version or download the .deb file for whatever variety of Ubuntu you're using (i386 or amd64). When you launch the program, it should detect the stray GPT data and offer to delete it. Answer "Y", then type "q" at the main menu to exit from the program. The problem should be fixed.

---

### Post by JMC2543 on 2011-03-30
You sir are a saint. I dont understand why the live cd was giving me the wrong type of table as I am obviously running windows and I know I downloaded the correct cd in the downloads section. Regardless, I thank you again your help has been greatly appreciated.

---

### Post by Rubi1200 on 2011-03-30
> **JMC2543 said:**
> You sir are a saint. I dont understand why the live cd was giving me the wrong type of table as I am obviously running windows and I know I downloaded the correct cd in the downloads section. Regardless, I thank you again your help has been greatly appreciated.
I told you it was worth the wait; srs5694 really knows his stuff!

Glad you got things worked out.

Enjoy!

---

### Post by srs5694 on 2011-03-30
> **JMC2543 said:**
> You sir are a saint. I dont understand why the live cd was giving me the wrong type of table as I am obviously running windows and I know I downloaded the correct cd in the downloads section. Regardless, I thank you again your help has been greatly appreciated.

It's not a question of what OS(es) you're running; it's a question of the quirks of MBR vs. GPT (specifically, the fact that GPT covers more sectors than MBR, so that if you put an MBR table on a [formerly] GPT disk there's GPT data left over) and how well various partitioning utilities cope with this sort of situation. Unfortunately, most Linux partitioning tools are based on libparted, which does a poor job at handling most types of errors and unexpected inputs -- including this one.

Incidentally, recent versions of Windows can use GPT, too -- but not as a boot disk on a BIOS-based computer. Windows installs to and handles GPT fine on EFI-based systems, and Windows Vista and 7 can both handle GPT fine as a data disk even on BIOS-based computers. Linux can use GPT as both a data and a boot disk on either BIOS-based or EFI-based computers.

---

