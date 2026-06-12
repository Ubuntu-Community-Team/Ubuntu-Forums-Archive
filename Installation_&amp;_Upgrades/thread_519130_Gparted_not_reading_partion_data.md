---
title: "Gparted not reading partion data"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by dellcom200 on 2007-08-06
I am trying to install 7.04 with the live cd, however when i get to the part where it asks me to set up my partitions (which i select manually) it does not show any of the partitions for 'sda' .   there should be 7 of them.  And if i do  ' fdisk -l ' all of them are shown so the partition table cant be messed up.   This happens with the 6.10 (edgy) live CD as well.  Which is weird because is did work before.

any ideas?

---

### Post by Pumalite on 2007-08-06
Try with Gparted, the stand alone, bootable CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
It's newer, with more features, more flexible and does the work many times where the one in Live CD fails.

---

### Post by dellcom200 on 2007-08-06
ok.  but the thing is i dont need to partition the drive.  it is already partitioned correctly.  I just need to be able to select the partition /sda6 as '/' and such.   So the correct partitions exist and are even formated correctly, but i cant select them during the install

---

### Post by Pumalite on 2007-08-06
'but i cant select them during the install'
This is why you need it. Right click on partition and you get a menu to set mount points.

---

### Post by dellcom200 on 2007-08-06
I downloaded and burned the iso  and everything worked (no mouse but o well).   The drive shows up the same as it did before, as 465.76Gib of unallocated space.  no partitions mentioned.

however the second drive (sdb) shows the one partition it does have (NFTS)  but this worked in the ubuntu live cd as well

---

### Post by Pumalite on 2007-08-06
You click in that unallocated space and decide what to do with it: new partitions?, resizing?, etc

---

### Post by dellcom200 on 2007-08-06
there is not supposed to b unallocated space there.  there should be 7 partitions.  all of which work (im using the comp now).   sda6 currently has edgy, sda5 is swap, sda3 has windows XP and sda1 is the boot partition but gparted just shows sda with all its space unallocated  that is the problem

i just wanted to do a fresh install of feisty on sda6.  However i can not tell the installer what partition to use because they are not displayed.   however like i said everything shows up fine in fdisk.

---

### Post by Pumalite on 2007-08-06
Post fdisk -l

---

### Post by dellcom200 on 2007-08-06
```
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       60800   467893125    f  W95 Ext'd (LBA)
/dev/sda3            5101       30596   204796588+   7  HPFS/NTFS
/dev/sda5            2551        2805     2048224+  82  Linux swap / Solaris
/dev/sda6            2806        5100    18434556   83  Linux
/dev/sda7           30597       60800   242613598+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979      250574+   6  FAT16

```

sdc  is  my usb thumbdrive

---

### Post by Pumalite on 2007-08-06
What did you use to do the partitioning?

---

### Post by dellcom200 on 2007-08-06
if i remember correctly i used the windows XP partitioning tools. and then right after installing XP i booted the edgy live cd (and it read the partitions fine)  i formated sda6 at ext3 and sda5 as ex2 for swap.  i had even used the live cd after that and it displayed the partition fine with gparted.   i only realized it wasnt working when i decided to try out feisty on the desktop  (didnt want to do the upgrade).  I thought it was sumthing with that livecd but when i tried my edgy cd  the same problem occured.  i just cant figure out why fdisk reads the drive perfectly and gparted does not.

thank you for your help thus far  it is appreciated

---

### Post by Pumalite on 2007-08-06
Well, I'm stumped. What can I tell you. First time I heard of it. Hope somebody with fresher (better) ideas comes in.

---

### Post by merlinus on 2007-08-06
If you look at the results of sudo fdisk -l, you can see that the partition numbering is not in the correct order of the blocks.

This may be the problem.

-merlin

---

### Post by Pumalite on 2007-08-06
Thanks Merlin. There you have it.

---

### Post by dellcom200 on 2007-08-06
is there any way to repair this? or get around it  or do i need to re-partition the drive to correct that discrepancy.

---

### Post by Pumalite on 2007-08-06
I'm beat here. I hope Merlin can help you.

---

### Post by merlinus on 2007-08-06
You might try this:

[http://www.vicman.net/lib/fix/partitiontable](http://www.vicman.net/lib/fix/partitiontable)

or

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

---

### Post by dellcom200 on 2007-08-06
> **merlinus said:**
> You might try this:

[http://www.vicman.net/lib/fix/partitiontable](http://www.vicman.net/lib/fix/partitiontable)

or

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

i dont think im going to try and fudge around with the partition tables right now.  Everything works stably so ill leave till i redo my operating systems.  just have to back everything up on the the other drive.   thank you for your help

---

### Post by amitst on 2007-11-05
I am facing the same issue on my laptop.

Here is the fdisk -l output

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xaec3aec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30480    15361888+   7  HPFS/NTFS
/dev/sda2           30481      155061    62788824    f  W95 Ext'd (LBA)
/dev/sda3           94080      134713    20479504+  83  Linux
/dev/sda5           30481       91425    30716248+   7  HPFS/NTFS
/dev/sda6           91434       94080     1333363+  82  Linux swap / Solaris
/dev/sda7          134714      155061    10255360+  83  Linux
```

And the gparted is showing the entire disk as unallocated,

While installing Ubuntu Edgy, I reduced the size of extended partition by 30GB and installed Ubuntu+swap. I later repartitioned the sda3 and used 10GB partition (sda7) to install PCLinuxOS. Now I wanted to create 10GB partition (by reducing sda2) for sharing home directory across linux distros but can't seem to do it.

---

### Post by amitst on 2007-11-05
Here is the df -k output as well

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             20157208  14289524   5048504  74% /
varrun                  513760       236    513524   1% /var/run
varlock                 513760         0    513760   0% /var/lock
udev                    513760       160    513600   1% /dev
devshm                  513760         0    513760   0% /dev/shm
lrm                     513760     33788    479972   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             15361888  10804236   4557652  71% /media/windowsc
/dev/sda5             30716248   7316708  23399540  24% /media/windowse
/dev/sda7             10094128   2339696   7241664  25% /media/disk

```

So it seems that sda3-7 partitions are created under /dev/sda2. And due to some reason (after installing PCLinuxOS) they are no longer shown in gparted.

I got the same error while trying to install other distros like Fedora, Sabayon etc. (and while trying Ubuntu Edgy liveCD)

---

### Post by amitst on 2007-11-05
I think I found out what the issue is...

The DiskDrake utility (that comes with PCLinuxOS) here is the culprit(?). Or at least Gparted and DiskDrake are not inter-operable.

To resolve the issue, I booted into PCLinuxOS and ran diskdrake. And lo behold, there was my original partition structure. I also was able to shrink my NTFS partition for Linux.

If the original author has also used DiskDrake sometime, then the solution would be to use PCLinuxOS liveCD or the Linux rescue disk that contains DiskDrake.

---

### Post by amitst on 2007-11-06
Even after shrinking the NTFS partition the unallocated space was not available. :(

I referred to the below thread [http://ubuntuforums.org/showthread.php?t=592787&highlight=gparted+unallocated](http://ubuntuforums.org/showthread.php?t=592787&highlight=gparted+unallocated)

And the only option (to include other distros) seems removing all but windows primary partition (through DiskDrake) and then create the required partition structure through GParted,

---

### Post by bulldog on 2007-11-06
Correct me if I'm wrong here,but in my opinion you can't resize an extended partition without messing things up.
You can only resize partition within the extended partition as far as I know.
But than again,what do I know:)

---

### Post by louieb on 2007-11-06
**amitst** has it right. bet you tried a distro that used the **Disk Drake** partitioner.  Your Extended partition sda2  has primary partition sda3 smack in the middle of it.  Extended partitions are suppose to occupy **contiguous space** on the drive and contain only logical partitions. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

Yours is **split into two **separate chunks. Thats why GParted or any of the parted family of partitioner's will have a problem with the partition layout. They think its messed up.       

There may be other way to fix it but amitst sugestion of:
> And the only option (to include other distros) seems removing all but windows primary partition (through DiskDrake) and then create the required partition structure through GParted,  is a way that will work.

---

