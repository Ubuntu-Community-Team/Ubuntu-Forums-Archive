---
title: "2TB Disk, Dual Boot - Ubuntu corrupts partition table"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by nerohj on 2011-08-28
Hello All,

 I've got a 2TB Western Digital "Caviar Green" disk and I'm trying to get a Windows 7 & Ubuntu 11.04 dual-boot going.

After installing Windows 7 first (100mb recovery partition + 300GB Windows partition, the remaining ~1.7TB un-allocated), I reboot and try to install Ubuntu.

The I choose the second option (to select a partition scheme) but Ubuntu detects the entire disk as un-allocated space. So, I click cancel(or quit?) and it brings me to the ubuntu desktop, where I run the disk-utility.

The disk utility shows the first two partitions (100mb + 300GB NTFS) as well as the remaining space. So I manually try to create a third partition for Ubunutu to install to (a 300GB partition). 

When I try to do this, I get an error "disk in use" or something along those lines. Then, when I reboot, the boot loader detects no OS on the hard drive. Ubuntu effectively corrupting the partition table and forcing me to re-install windows and try again (I did this twice just to confirm that it was the disk utility that was corrupting the partiton table and not the installer).


I also tried using Wubi, which fails during boot saying something along the lines of "no root device specified"... and no way to fix it.


So is there any way I can get Ubuntu installed on this system? A dedicated partition would be preferable, but I can live with a Wubi install as well.

Thanks in advance for any help!
Cheers
Nick

---

### Post by ottosykora on 2011-08-28
hmm, not sure what will the ubuntu installer do of this, but are you trying to set up normal partitions, now so called mbr-partition style some people start call it legacy? 

If so, this will probably nor work on this size of drive. It should have the GPT partition system and have an additional partition for the EFI software which is kind of bios extension as I understand it.

---

### Post by nerohj on 2011-08-28
> **ottosykora said:**
> hmm, not sure what will the ubuntu installer do of this, but are you trying to set up normal partitions, now so called mbr-partition style some people start call it legacy? 

If so, this will probably nor work on this size of drive. It should have the GPT partition system and have an additional partition for the EFI software which is kind of bios extension as I understand it.

Thanks for your reply. I guess I am using whatever the standard method is for windows 7, so that would be the "legacy" partitioning.

This is my first large hard drive, do you have some more info on how I can set up the disk correctly so that it will work with Windows and Ubunutu? Will I need to re-install Windows (again) ?

---

### Post by dino99 on 2011-08-28
i never use the installer & let it decide for me, i prefer to partition myself, its less scary.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by nerohj on 2011-08-28
> **dino99 said:**
> i never use the installer & let it decide for me, i prefer to partition myself, its less scary.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Hi, yeah I also prefer to partition myself. I'm just not familiar with the new way I (apparently) must go about it with 2TB drives. The old partition table doesn't seem to cut it anymore.

---

### Post by dino99 on 2011-08-28
> **nerohj said:**
> Hi, yeah I also prefer to partition myself. I'm just not familiar with the new way I (apparently) must go about it with 2TB drives. The old partition table doesn't seem to cut it anymore.

hm, is there a fake raid installed ? if so you need to remove it before formatting. Boot on a livecd and run:

sudo dmraid -rE

---

### Post by srs5694 on 2011-08-28
You do *not* need to use the GUID Partition Table (GPT) system on 2 TB disks; the older Master Boot Record (MBR) partitioning system works on disks up to 2 TiB (about 2.2 TB) in size, assuming the common 512-byte sector size. The Ubuntu installer swiches from MBR to GPT as the default system on fresh installations when the disk size climbs to something between 1 TB and 2 TB, but I don't know the exact cutoff value. If you feed it a larger MBR-partitioned disk, it will work with it just fine.

The symptoms you describe are consistent with a partition table that's been damaged in some subtle way. A number of problems can cause this, such as a partition that extends beyond the end of the disk, overlapping partitions, a mis-sized extended partition, or some types of leftover RAID data. For a better diagnosis, please run the following command from a live CD:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to improve legibility. This output will reveal most of the problems that can create this type of symptom, which will enable us to recommend a specific fix. If you're anxious to get an immediate fix, you can read my [FixParts Web page,](http://www.rodsbooks.com/fixparts/) since FixParts can fix many (but not all) of these problems.

---

### Post by YesWeCan on 2011-08-28
Reinstall Windiws then post the output of
sudo parted - l

and bootinfoscript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ottosykora on 2011-08-28
@srs5694

well how does w7 behave when it meets 2t drive and possible UEFI bios ? Will it not attempt by itself to produce some GUID partitionig just by seeing it is possible?

Or how does one tell w7 not to produce GUID and stay with 'legacy' mbr only set up?

I have so far not met it, the only computer I have access to and which could use UEFI, has it switched off and runs w7 in traditional mode, so I am not bothering to change it.

I mean he installed w7 first and has now more then 1T left, this could well lead to some confusion and the switching to GUID as you described. ??

---

### Post by kelvin spratt on 2011-08-28
Ist thing did you set up a partion table and format the whole drive or just bung w7 on a unformatted drive format the whole drive then put a 300gb for win7 partition then do a extended partition other wise you can only create 2 more partition on the whole Hd you can then make as many partitions as you want format to ext4 or what ever. then install ubuntu

---

### Post by nerohj on 2011-08-29
Hi all,

 So I've booted off a USB drive and run the following command:

```
fdisk -lu
```

Here is the full output:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd12149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   716802047   358297600    7  HPFS/NTFS
/dev/sda3       716802048  1433602047   358400000    7  HPFS/NTFS
/dev/sda4      1433602048  3907026943  1236712448    f  W95 Ext'd (LBA)
/dev/sda5      1433604096  3907026943  1236711424    7  HPFS/NTFS

Disk /dev/sdb: 4127 MB, 4127195136 bytes
127 heads, 62 sectors/track, 1023 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(409512, 23, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(464486, 117, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(415547, 62, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(663637, 52, 13)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?           0           0           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(-268367274, 94, 16)
Partition 3 does not end on cylinder boundary.
/dev/sdb4        50200576   974536369   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(6375, 61, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(123766, 46, 34)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```



It looks like the Windows 7 "system recovery partition" is not setup correctly (windows recommends doing this during it's install, when I specified I wanted 350gb for windows, it added the initial 100mb partition automatically).

I will give my partition table a backup (I really don't want to have to install Windows again) and then give srs5694's FixParts tool a try and see if that can help.

---

### Post by nerohj on 2011-08-29
Hi all,

 When I tried to backup my partition table with this command:

```

sfdisk -d /dev/sdc > parts.txt

```

I received the following message:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```

So I guess the windows install actually did use the new GPT method instead of the "legacy" method. 

Hmm.. so where does that place me? The Ubuntu installer still does not recognize any partitions on my hard drive. And when I use something like "Disk Utility", although it does recognize the existing partitions... [100mb]-[350gb]-[350gb]-[1.2tb] ... Adding a partition ruins the entire partition table.

---

### Post by nerohj on 2011-08-29
> **YesWeCan said:**
> Reinstall Windiws then post the output of
sudo parted - l

and bootinfoscript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


Hi YesWeCan,

  Booting from a USB drive. I ran the parted command as you suggested, here's the output from answering both yes and no to the question it asks:

```

ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? n                                                                 

Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 4127MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4127MB  4127MB  fat32



ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 4127MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4127MB  4127MB  fat32

```

---

### Post by YesWeCan on 2011-08-29
So the problem is that the disk has a GPT format on it and you really want an MBR format.

Is sda the disk you are trying to install Windows and Ubuntu on? If so, just do this to wipe all formats off it (this will erase the disk):
sudo dd if=/dev/zero bs=512 count=2 of=/dev/sda

And then boot a live Ubuntu CD and use Disk Utility to format the drive with an MBR.
Then you can reinstall Windows and Ubuntu. :)

You only need GPT for disks bigger than 2TiB. It is much simpler, at the present time, to use MBR format.

**[edit] If you do not want to install Windows again**, just do this:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda

That will get rid of the GPT header and leave the normal MBR that fdisk is showing. It should be ok after that.

---

### Post by nerohj on 2011-08-29
> **YesWeCan said:**
> So the problem is that the disk has a GPT format on it and you really want an MBR format.

Is sda the disk you are trying to install Windows and Ubuntu on?


Yes.

> **YesWeCan said:**
> If so, just do this to wipe all formats off it (this will erase the disk):
sudo dd if=/dev/zero bs=512 count=2 of=/dev/sda

And then boot a live Ubuntu CD and use Disk Utility to format the drive with an MBR.
Then you can reinstall Windows and Ubuntu. :)

You only need GPT for disks bigger than 2TiB. It is much simpler, at the present time, to use MBR format.

**[edit] If you do not want to install Windows again**, just do this:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda

That will get rid of the GPT header and leave the normal MBR that fdisk is showing. It should be ok after that.


So, the second option - I can do this if I don't want to loose my existing Windows install right? (it's preferable as I've already got everything set up and installed on it, which took most of the weekend).

---

### Post by YesWeCan on 2011-08-29
> **nerohj said:**
> So, the second option - I can do this if I don't want to loose my existing Windows install right? (it's preferable as I've already got everything set up and installed on it, which took most of the weekend).
Yes. This just erases the GPT header sector which is the second sector on the disk. There are no entries in the GPT table so Windows is only using the MBR partition table in the first sector. Use this exact command, tho:

sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda

---

### Post by YesWeCan on 2011-08-29
> **nerohj said:**
> I've got a 2TB Western Digital "Caviar Green" disk and I'm trying to get a Windows 7 & Ubuntu 11.04 dual-boot going.

After installing Windows 7 first (100mb recovery partition + 300GB Windows partition, the remaining ~1.7TB un-allocated), I reboot and try to install Ubuntu.
Your disk must have had a GPT format on it before you installed Windows. It seems Windows will ignore the GPT header in sector 1 if your mobo is in BIOS boot mode. In this case, Windows just uses the MBR partition table in sector 0 and is all happy.

> The I choose the second option (to select a partition scheme) but Ubuntu detects the entire disk as un-allocated space. So, I click cancel(or quit?) and it brings me to the ubuntu desktop, where I run the disk-utility.The Ubuntu installer sees both a populated MBR partition table and a GPT header and empty GPT partition table. Apparently, it chooses to ignore this contradiction and just reports the disk is empty as per the GPT table.

> The disk utility shows the first two partitions (100mb + 300GB NTFS) as well as the remaining space. So I manually try to create a third partition for Ubunutu to install to (a 300GB partition).
When I try to do this, I get an error "disk in use" or something along those lines.Disk Utility reports the partitions from the MBR table but apparently notices the GPT header when you try to create a new partition and reports an obscure error.

> Then, when I reboot, the boot loader detects no OS on the hard drive. Ubuntu effectively corrupting the partition table and forcing me to re-install windows and try again (I did this twice just to confirm that it was the disk utility that was corrupting the partiton table and not the installer).This bit I do not understand. Are you saying Disk Utility produced the "disk in use" error but went and deleted the MBR table so Windows could not boot? I'll have to test this in VirtualBox. That would be really naughty.

---

### Post by YesWeCan on 2011-08-29
OMG you are absolutely right! :(
Disk Utility wipes the MBR partition table!!!! That is outrageous.

I made a 2TB GPT formatted disk with an empty GUID partition table.
I installed Windows 7 to it. Sure enough it made no complaint and set up a new MBR boot code and partition table and left the GPT header sector in place.
Booting from live 11.04, Disk Utility showed the Windows partitions.
11.04 Installer showed an empty disk.

I then used Windows to shrink its C: partition leaving about 1TB of unallocated space.
Then booted live 11.04 , Disk Utility showed the empty space and I tried to make a 300GB ext4 partition in it. Got the same error you reported but no partition was made. However, when I checked the MBR partition table it had been replaced by a "protective" table that is the default for GPT.

---

### Post by YesWeCan on 2011-08-29
After I deleted the GPT header in sector 1 everything worked fine. Disk Utility was able to make a 300GB partition without error. The Installer showed all the MBR partitions.

sfdisk and fdisk still warn of a GPT detection - this is because there is a backup copy of the GPT header in the last sector of the disk. IMO this can be safely ignored. If you want to delete the backup just do the same thing but choose the last sector number (from fdisk -lu total sector count -1)
sudo dd if=/dev/zero bs=512 count=1 seek=3907029167 of=/dev/sda

---

### Post by recluce on 2011-08-29
Don't forget that the Caviar Green 2TB drives need to be aligned (4k sectors internally). You want to start at the second "chunk" of 4kB, since the first is partly in use by the MBR and some other stuff.

If you don't align, you will take a MASSIVE performance hit.

---

### Post by srs5694 on 2011-08-29
> **ottosykora said:**
> @srs5694

well how does w7 behave when it meets 2t drive and possible UEFI bios ? Will it not attempt by itself to produce some GUID partitionig just by seeing it is possible?

Or how does one tell w7 not to produce GUID and stay with 'legacy' mbr only set up?

Under Windows 7, the firmware type and partition table type are tightly bound: If you use a BIOS-based computer, the partition table *must* be MBR; and if you use a UEFI-based computer, the partition table *must* be GPT. Note, however, that most (perhaps all) modern UEFI-based x86-64 computers have UEFIs with BIOS compatibility modes. In those modes, the BIOS rules apply.

Linux is much more flexible; you can use GPT on a BIOS-based computer or (I've heard, but never tried) MBR on a UEFI-based computer.

The upshot of this is that you should follow the Windows rules when creating partitions on a dual-boot computer.

> **neroh]jubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd12149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   716802047   358297600    7  HPFS/NTFS
/dev/sda3       716802048  1433602047   358400000    7  HPFS/NTFS
/dev/sda4      1433602048  3907026943  1236712448    f  W95 Ext'd (LBA)
/dev/sda5      1433604096  3907026943  1236711424    7  HPFS/NTFS[/quote]

The warning about GPT indicates that fdisk has detected GPT data structures on the disk, but the rest of the output indicates a normal MBR disk. From a strictly technical perspective, this makes the disk an MBR disk said:**
> FixParts[/url] utility. When run on your disk, it should report finding GPT data and offer to remove it. If you authorize this, the data will be removed immediately. You should then type "q" at the main menu. Other Linux partitioning tools, including the Ubuntu installer, should then see the MBR partitions that were presumably created by the Windows installer.

[quote=nerohj]When I tried to backup my partition table with this command:

 	Code:
 	sfdisk -d /dev/sdc > parts.txt 
I received the following message:

 	Code:
 	WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.  Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently. 
So I guess the windows install actually did use the new GPT method instead of the "legacy" method. 

Not necessarily. This is probably just the same type of warning that fdisk produces. If you examine the parts.txt file, you'll probably see the same partitions that fdisk reported, just in a different form.

[quote=YesWeCan]Is sda the disk you are trying to install Windows and Ubuntu on? If so,  just do this to wipe all formats off it (this will erase the disk):
sudo dd if=/dev/zero bs=512 count=2 of=/dev/sda[/quote]

[quote=YesWeCan]sfdisk and fdisk still warn of a GPT detection - this is because there  is a backup copy of the GPT header in the last sector of the disk. IMO  this can be safely ignored. If you want to delete the backup just do the  same thing but choose the last sector number (from fdisk -lu total  sector count -1)
sudo dd if=/dev/zero bs=512 count=1 seek=3907029167 of=/dev/sda[/quote]

The backup GPT data can *not* be "safely ignored." We've been through this before, and advising people to ignore it is reckless. There are situations in which such leftover GPT data can cause partition tables to be erased in favor of the the GPT data.

A command like the dd command in the second quote will work, but you've got to be very careful to get it right. An incorrect value or omitted option can end up doing a lot of damage or can leave the intended task undone. Doing damage might not be a concern to nerohj, who seems to want to do a fresh install on a blank disk, but as a general rule it's a serious risk; and of course leaving it undone is an issue.

---

### Post by YesWeCan on 2011-08-29
> **srs5694 said:**
> The backup GPT data can *not* be "safely ignored." We've been through this before, and advising people to ignore it is reckless. There are situations in which such leftover GPT data can cause partition tables to be erased in favor of the the GPT data.
You are wrong. You have shown no evidence of a remotely plausible scenario for this fear you have.
Kindly do not accuse me of being reckless. That is inappropriate.

---

### Post by YesWeCan on 2011-08-29
@srs5694
May I also alert you to my posts in this thread that show Windows 7 installs without any complaint to a disk with no GPT header and a "protective MBR". In another thread, you used this as an argument to support your strident criticisms of my advice. You were wrong to do so.

---

### Post by srs5694 on 2011-08-29
> **YesWeCan said:**
> You are wrong. You have shown no evidence of a remotely plausible scenario for this fear you have.
Kindly do not accuse me of being reckless. That is inappropriate.

[http://ubuntuforums.org/showpost.php?p=11171908&postcount=11](http://ubuntuforums.org/showpost.php?p=11171908&postcount=11)

You didn't reply to the above-referenced post, nor to my reference that that post in [this thread](http://ubuntuforums.org/showthread.php?p=11171944) in which you made a claim that I was being unrealistic and alarmist.

There *are* scenarios in which damaging GPT data in the way you advocate can cause problems in the future. I freely admit that these scenarios are unlikely on an individual basis; however, given a large enough sample, unlikely scenarios *will* be played out *with 100% certainty*. There *are* ways to eliminate this risk, and some of them (such as using parted, GParted, or FixParts, depending on one's needs, to completely wipe the GPT data) are easier and safer to implement than using even a single dd command. Thus, advocating the sort of damage you are suggesting *is reckless*, and pointing out that fact *is appropriate*. If you want me to stop accusing you of recklessness, please stop advocating reckless procedures.

[quote=YesWeCan]May I also alert you to my posts in this thread that show Windows 7  installs without any complaint to a disk with no GPT header and a  "protective MBR". In another thread, you used this as an argument to  support your strident criticisms of my advice. You were wrong to do so.[/quote]

I'm not sure to which other thread you're referring, so I can't respond. If you actually want a response, perhaps you should point it out in that thread, unless you think it's relevant to this one.

---

### Post by nerohj on 2011-08-30
> **recluce said:**
> Don't forget that the Caviar Green 2TB drives need to be aligned (4k sectors internally). You want to start at the second "chunk" of 4kB, since the first is partly in use by the MBR and some other stuff.

If you don't align, you will take a MASSIVE performance hit.

Hi Recluce, I had no idea about this. Thanks for the tip. Can you give me a little info on how I can detect if this is currently the case? I assume there's no way to fix it without having to re-install everything?

---

### Post by srs5694 on 2011-08-30
> **nerohj said:**
> Hi Recluce, I had no idea about this. Thanks for the tip. Can you give me a little info on how I can detect if this is currently the case? I assume there's no way to fix it without having to re-install everything?

You can detect partition alignment using any partitioning tool that gives partition start points in sector values. Most tools can do this, although many make you dig a bit for it. The simplest solution for MBR disks is generally to use fdisk with its -u option, as in:

```

sudo fdisk -lu

```

The result looks something like this:

```

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x786609d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976762879   488380416    b  W95 FAT32
/dev/sdb2       976762880  1953523711   488380416    5  Extended
/dev/sdb5       976764928  1953523711   488379392   83  Linux

```

This shows partition start sectors under the "Start" column. In this case, all the partitions' start values are divisible by 8 (that is, 4KiB), so this example disk is properly aligned. (Don't worry about the extended partition, if you've got one; its alignment doesn't matter.)

Most modern partitioning tools align partitions to multiples of 1 MiB (2048 sectors) by default, which works fine for this purpose. Older tools align on "cylinder" boundaries, which are usually not correct for modern Advanced Format disks.

If you find that your disk is mis-aligned, fixing it could be tricky. Doing a tiny resize operation with GParted could do the trick, but that will take some time, and it will necessarily move the start of the partition, which is a bit risky. Thus, backing up before proceeding is advisable.

---

### Post by recluce on 2011-08-30
Good advise by srs5694.

Below is the (very simple) layout of my WD20EARS (plain storage drive). 

```

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059be2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   83  Linux

```

Note that the drive reports 512b sectors, but works with 4kb sectors internally. WD calls this "advanced format".

The important part is that you stay on 4096 Byte boundaries for the start of each partition (*), this avoids read and write operations on "split" sectors. Let's say you want to write 8k to sector X. If your drive is properly aligned, this will write 4k to physical sector X and 4k to X+1. If you are misaligned by one logical 512b sector (due to the MBR), your drive will read sector X, append 3.5K, write X, then write X+1 (4k) and write the last 512b to X+2. So instead of writing 2 sectors, 1 sector had to be read and 3 to be written. 

(*) If you use an extended partition, alignment is important for the logical partitions inside the extended partition - not so much for the extended partition itself.

Usually, if somebody bemoans the poor performance of this drive, they didn't align it. For reference, with alignment, I have sustained eSATA read/write speads of about 60 MByte/s.

Aligning after the fact: difficult. Maybe what srs5694 said works. Or, if you have a small GRUB or boot partition at the beginning, just make sure that the partitions after that one are aligned. You won't do many write or random access operations on a GRUB or boot partition, so that won't hurt much. 

While you work on your drive, google for "Load Cycles" or "Load Cycle Count" and "wdidle". Basically, the idle timeout for this drive is an insanely short 8 seconds (to allow WD to brag with the low energy consumption) - causing load cycles to accumulate in a very short time, even putting the drive over design limits in less than a year in the "right" kind of usage scenario. Use wdidle to set the timeout to something more sane (like 30 seconds) or to disable it. This will cause a slightly higher energy consumption, but improve the reliability of the drive tremendously.

---

