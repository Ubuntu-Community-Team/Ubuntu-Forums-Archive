---
title: "Partition manager does not identify partitions"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by sf-andrew on 2005-06-29
I am thoroughly confused by the problems I am having trying to install Ubuntu and would appreciate any help. I am particularly puzzled by the partition manager with the Ubuntu installer since it does not appear to identify partitions correctly.

I have a Dell Optiplex GX110 running Win98SE, and I have just replaced the hard drive (using the tools that came with the disk) so that I now have 80GB (Western Digital). I have partitioned the new drive (40 & 40) and I have transferrred my Win98SE setup to the first partition of the new drive. It boots correctly (and a lot faster!). So far so good. My plan is now to install UbuntuLinux (5.04) in the second partition.

I want to be careful so that I don't delete my Win98SE installation. I therefore created a new partition (of around 40GB), using the tools that came with the Western Digital disk. However, when I then started to install Ubuntu (choosing the option to manually assign partitions, I found that it did not report there being any partition present. I wondered whether it was something to do with the way the partitioning had been done, so I therefore aborted the installation and downloaded and burned a CD containing QTParted. Using this I set up some partitions - as shown below, formatting the new ones to be ext3 and with the appropriate names for the Ubuntu installation.

[Incidentally, I also made the new root partition to be active (probably unnecessarily, since I later had to make the Windows partition active again before the computer would boot from it). Also, from reading other postings I realize that the swap directory shouldn't be so large.]

Set up using QTparted:
........Partition.....Type....Status....Size...... Used Space.....Start......End.........Label
01..../dev/hda1...fat32................37.44GB...17.26GB..... .0.03MB...37.44GB...DRV2_VOL1
02..../dev/hda2...ext3...Active.....31.25GB.....1.59GB.....37 .44GB...68.68GB.../
03..../dev/hda3...ext3....................5.84GB...331.31MB.. .68.68GB...74.53GB.../swap

I then started up the Ubuntu installation again. Now I was nervous about where Ubuntu would be installed, so I went into the manual partitioning again. Once again, the partitions reported by the installer seem to bear little resemblance to the partitions that I thought I had created.

Reported by Ubuntu:
IDE master (hda) 80GB WDC WD800...
........#1 primary 8.4GB <lightning>
..............pril/log 35.8GB FREESPACE
........#2 primary 35.8GB ext3
IDE slave (hdb) 20.0 GB IC35...
........#1 primary 20.0GB <lightning> FAT32

I therefore aborted the installation and decided to seek help! What is going on? I am not comfortable getting different stories from QTParted and the Ubuntu installer.

Is there something wrong with the partition manager in this version of Ubuntu (5.04 for intel)? Why does it not correctly identify the partitions that are present on the disk? Is it something to do with the utility that was loaded with the Western Digital drive - a Dynamic Drive Overlay?

---

### Post by mingus on 2005-06-29
*Is there something wrong with the partition manager in this version of Ubuntu (5.04 for intel)? Why does it not correctly identify the partitions that are present on the disk? Is it something to do with the utility that was loaded with the Western Digital drive - a Dynamic Drive Overlay?*

There is nothing wrong with the Ubuntu partitioner.  Nor is it a matter of "correctly" identifying the partitions . . . the problem is with the overlay.

You installed it because of the 64GB limitation in W98, your BIOS, or both?  The way the overlay works is to "overlay" what the BIOS reports the drive capacity to be and passes that to the OS; I think it also writes the partition table in a way that fools the OS.  The WD utility uses its own formatting utility because the FDISK with W98 cannot see more than 64GB and FORMAT reports partition sizes incorrectly - this is because under the hood W98 is still DOS.  The result is W98 disk I/O can see the full capacity, although its utilities still cannot.  Hence the procedure to have WD partition upon install, and then not change it again.

Complicating things is that DOS' brain-dead method of writing the table makes it hostile to partitioning done under another OS.  Partitioners native to Windows like PartitionMagic have code to work around this and reconcile OS incompatibilities.  WD told me that it is dangerous to mix DOS fdisk or even XP's Disk Manager with any other partitioner.

I once got this work on a system with the 8.4GB BIOS limitation, using the same WD drive you have.  I had used the overlay,  installed XP, and then sometime later tried to add a partition with Disk Manager.  The overlay busted and the OS could not be found at boot.  I got the system back by removing the overlay and rebuilding the boot sector in XP's Recovery console.  

Later I wiped the drive, installed W98 and Linux - without the overlay.  I *think* (sorry, my memory is rusty on this) I set the capacity in the BIOS at its limit, and then when installing W98 used only enough for the OS and programs.  Thereafter I used PM - which sees the full capacity because it reads from the drive directly - to create an additional FAT32 partition for W98 and Linux to share, plus the Linux partitions.  When I installed Linux, I did not let it take over the MBR - I think I just used a boot floppy, although setting the Linux partition as the active primary may have work as well.

Hope this helps.

---

### Post by davahmet on 2005-06-29
[QUOTE=mingus]*Is there something wrong with the partition manager in this version of Ubuntu (5.04 for intel)? Why does it not correctly identify the partitions that are present on the disk? Is it something to do with the utility that was loaded with the Western Digital drive - a Dynamic Drive Overlay?*

There is nothing wrong with the Ubuntu partitioner.  Nor is it a matter of "correctly" identifying the partitions . . . the problem is with the overlay.

You installed it because of the 64GB limitation in W98, your BIOS, or both?  The way the overlay works is to "overlay" what the BIOS reports the drive capacity to be and passes that to the OS; I think it also writes the partition table in a way that fools the OS.  The WD utility uses its own formatting utility because the FDISK with W98 cannot see more than 64GB and FORMAT reports partition sizes incorrectly - this is because under the hood W98 is still DOS.  The result is W98 disk I/O can see the full capacity, although its utilities still cannot.  Hence the procedure to have WD partition upon install, and then not change it again.

Complicating things is that DOS' brain-dead method of writing the table makes it hostile to partitioning done under another OS.  Partitioners native to Windows like PartitionMagic have code to work around this and reconcile OS incompatibilities.  WD told me that it is dangerous to mix DOS fdisk or even XP's Disk Manager with any other partitioner.

I once got this work on a system with the 8.4GB BIOS limitation, using the same WD drive you have.  I had used the overlay,  installed XP, and then sometime later tried to add a partition with Disk Manager.  The overlay busted and the OS could not be found at boot.  I got the system back by removing the overlay and rebuilding the boot sector in XP's Recovery console.  

Later I wiped the drive, installed W98 and Linux - without the overlay.  I *think* (sorry, my memory is rusty on this) I set the capacity in the BIOS at its limit, and then when installing W98 used only enough for the OS and programs.  Thereafter I used PM - which sees the full capacity because it reads from the drive directly - to create an additional FAT32 partition for W98 and Linux to share, plus the Linux partitions.  When I installed Linux, I did not let it take over the MBR - I think I just used a boot floppy, although setting the Linux partition as the active primary may have work as well.

Hope this helps.[/QUOTE]
 Mingus is absolutely correct on this.
Wndows based partioners, including many of the ones from HD manufacturers, have some extraordinary work-arounds for known partition problems in Windows.  However, this means the overlay makes things difficult for other OS partitioners.

The way around this is to delete the new partition fith the Linux partitioner.  If you look at the HD manufacturer's partitioning tool as simply a means of setting a Windows/Linux boundary, it begins to make since.  Assume the partition created by the Windows-based partitioner is corrupt and delete it with fdisk or the installer, leaving unpartitioned free space.  Now use the Linux version of fdisk  (which is posixly correct unlike the Windows version) or the Unbuntu installer partitioning tool and create your new partitions.  This should get you up and running smoothly.

---

### Post by sf-andrew on 2005-06-29
**Mingus**, thanks for your comments. I had come to the conclusion that it was something to do with the Overlay, but I needed confirmation and help on what to do next. 

Interestingly, Knoppix LiveCD can see the partitions set up by the WD utility, but cannot see the Ubuntu data that the installation placed there. Ubuntu LiveCD 5.04 won't even boot, while v3.? will, and it can see the installed Ubuntu data, but cannot see the Win98 partition. Grub on a floppy can't see the Ubuntu-generated partitions, presumably because it is confused by the Overlay, and it refused to boot into Win98, presumably for the same reason. All this goes to show that what both you and **davahmet** said is true about lack of a standard approach.
> **mingus]*Is there something wrong with the partition manager in this version of Ubuntu (5.04 for intel)? Why does it not correctly identify the partitions that are present on the disk? Is it something to do with the utility that was loaded with the Western Digital drive - a Dynamic Drive Overlay?*

There is nothing wrong with the Ubuntu partitioner.  Nor is it a matter of "correctly" identifying the partitions . . . the problem is with the overlay.

You installed it because of the 64GB limitation in W98, your BIOS, or both?[/QUOTE]
I didn't actually make the choice... I think the installer did it for me! I will have to check whether the BIOS requires it. 
[QUOTE=mingus]  The way the overlay works is to "overlay" what the BIOS reports the drive capacity to be and passes that to the OS said:**
> 
How do you remove the overlay? Will it still exhibit the partitioning that I originally created? Will I lose my Win98 data? Since I was wanting to give Win98 less than 64GB anyway, I should be OK without it (although I will have to check the BIOS requirements). Am I likely to have data in overlapping partitions? I tried to keep the partitioning away from the Win98 data, but this relies on the overlay not interlacing data. I haven't observed any problems with it working in Win98.

[QUOTE=mingus]  
Later I wiped the drive, installed W98 and Linux - without the overlay.  I *think* (sorry, my memory is rusty on this) I set the capacity in the BIOS at its limit, and then when installing W98 used only enough for the OS and programs.  Thereafter I used PM - which sees the full capacity because it reads from the drive directly - to create an additional FAT32 partition for W98 and Linux to share, plus the Linux partitions.  When I installed Linux, I did not let it take over the MBR - I think I just used a boot floppy, although setting the Linux partition as the active primary may have work as well.

Hope this helps.
Yes, thanks!... although I haven't quite worked out what I am going to do next.

Andrew

---

### Post by sf-andrew on 2005-06-29
[QUOTE=davahmet]Mingus is absolutely correct on this.
Windows-based partioners, including many of the ones from HD manufacturers, have some extraordinary work-arounds for known partition problems in Windows.  However, this means the overlay makes things difficult for other OS partitioners.

The way around this is to delete the new partition with the Linux partitioner.  If you look at the HD manufacturer's partitioning tool as simply a means of setting a Windows/Linux boundary, it begins to make sense.  Assume the partition created by the Windows-based partitioner is corrupt and delete it with fdisk or the installer, leaving unpartitioned free space.  Now use the Linux version of fdisk  (which is posixly correct unlike the Windows version) or the Unbuntu installer partitioning tool and create your new partitions.  This should get you up and running smoothly.[/QUOTE]
Thanks for your help. 

Does this procedure involve losing all of the data that is on the disk (i.e. when you delete the new partition)? Does it also involve getting rid of the overlay first? If not, I can't see how the linux partitioner is going to get rid of the boundary, since it cannot see it.

Thanks,

Andrew

---

### Post by mingus on 2005-06-30
*How do you remove the overlay?*

Been quite a while, but I seem to recall that the WD Lifeguard utility includes a menu command to do this . . . and that it took a while to find it.

*Will it still exhibit the partitioning that I originally created? Will I lose my Win98 data?*

*Am I likely to have data in overlapping partitions?*

The most important thing for you to do now is backup your W98 data.  That partition table is a ticking bomb.  And one reason for this is because, yes, it is conceivable that data could be written across boundaries.  Drive geometries are not physical, they're virtual.  DOS and Linux calculate this differently.  And DOS uses what the BIOS tells it - in your case, the overlay.  But again, this only helps W98 with capacity, it's disk mgmt cannot handle over 64GB.  IMHO the only safe thing to do is backup, remove overlay, reinstall, restore.

*Since I was wanting to give Win98 less than 64GB anyway, I should be OK without it (although I will have to check the BIOS requirements). *

You probably cannot do it this this way.  Your BIOS most likely has the 1024 cylinder limitation.  Worse yet, because the BIOS cannot see the drive's full capacity, it will miscalculate where that cylinder is.  I think you'll need to give the BIOS the drive parameters rather than using "auto", because of this.  WD always suggests 16383/16/63.  This should yield the max capacity the BIOS can see, and therefore make the BIOS calculate 1024 as far onto the disk as it can.  This should give you the room you need to create a small first partition for W98.  BTW, also in the BIOS set the drive to LBA mode.  But do not try to use grub or lilo's "force LBA" feature to get around the 1024; this ordinarily works but will not with this BIOS/drive disconnect.

---

### Post by sf-andrew on 2005-07-01
Mingus,

Thank you for all your help - I am a little swamped at work at present, so I shall have to wait before implementing what you suggest. All my data is currently on the original drive (which was in turn backed up to an external drive), so I don't have to worry about that, yet.

Andrew

PS How do I find out what my BIOS limitations are?

---

### Post by mingus on 2005-07-02
*How do I find out what my BIOS limitations are?*

Setup in BIOS's differ a bit, but in general these is a field for "auto" or "manual" configuration; if auto is used the BIOS should try to retrieve the CHS from the disk and  calculate its capacity.  If it cannot or it retrieves less than you know the HDD is, then that is its limitation.  You can also do this with manual set, by entering CHS of 16383/16/63; if the BIOS is not limited you should see the full capacity.  The BIOS limitations have been 528MB (<8/94), 2.1GB (<2/96), 8.4GB (<1/98), 32GB (<6/99), 64GB, and 137GB.  I don't have the date frames for the last two.  If I'm not mistaken, W95 cannot support >32GB and W98/ME utilities don't see correctly >64GB (scandisk fails >32GB).  If memory serves, XP initially had a 137GB limitation, but that was overcome with 48-bit LBA in SP1.

(That smiley is actually an eight.)

---

