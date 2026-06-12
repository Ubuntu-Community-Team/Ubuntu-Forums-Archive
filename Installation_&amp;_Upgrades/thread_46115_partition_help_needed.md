---
title: "partition help needed"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by not_yet on 2005-07-03
hello,

I have installed Ubuntu for a friend and ran across this problem

after the install I cannot see the original "D" drive?

original setup

xp pro / c drive / d drive

partition magic shows the following

primary ntfs

extended 

logical ntfs

I used the partition magic to resize the logical to make some free space

then I installed Ubuntu in the free space

Ubuntu works fine

when windows starts, I only see the c drive, can't see the old d drive?

---

### Post by mingus on 2005-07-03
in Ubuntu in a terminal do:

$sudo fdisk -l

and post back the result

when you say W$ doesn't see D:\, what *does* Disk Manager see?

---

### Post by not_yet on 2005-07-03
sudo fdisk -l


Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2570    20643493+   7  HPFS/NTFS
/dev/hda2            2571        6866    34507620    f  W95 Ext'd (LBA)
/dev/hda3            6867        9964    24884685   83  Linux
/dev/hda5            2571        6730    33415168+   7  HPFS/NTFS
/dev/hda6            6731        6866     1092388+  82  Linux swap / Solaris

> when you say W$ doesn't see D:\, what *does* Disk Manager see?

when you say  Disk Manager, do you mean the file explorer?

when I look there I see the C drive and the CD rom drive

thanks

---

### Post by Degnaw on 2005-07-03
Is the D:\ drive in the extended "section" of your drive? as in, was it grouped in with the linux partitions?
If thats the case, move it back outside the extended partition (im not sure about it, but i think extending it with the lin partitions it hides it)

---

### Post by mingus on 2005-07-03
[QUOTE=not_yet]
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2570    20643493+   7  HPFS/NTFS
/dev/hda2            2571        6866    34507620    f  W95 Ext'd (LBA)
/dev/hda3            6867        9964    24884685   83  Linux
/dev/hda5            2571        6730    33415168+   7  HPFS/NTFS
/dev/hda6            6731        6866     1092388+  82  Linux swap / Solaris

when you say  Disk Manager, do you mean the file explorer?[/QUOTE]

Disk Manager is XP's built-in tool for managing partitions, it is at My Computer/Manage/Disk Management.  From the report above, you see "D:" (this is just how W$ arbitrarily names partitions) as hda5.  Apparently you had created an extended partition (hda2) inside which you had created a second logical NTFS partition (hda5).  Did you shrink the logical, and then shrink the extended leaving room for the swap?  Ubuntu is on the second primary (hda3), following the extended.  After you made the change with PM, did you verify that D was still there from inside Windows?

Check a couple of things:
First, with Disk Manager, what does it report for that partition?  Healthy?  It should show it as NTFS. 

Second, what does PM report?

Third, in Ubuntu, get into a terminal and do:
$sudo mkdir /mnt/xp2
$sudo mount /dev/hda5 /mnt/xp2
Then go to Places/Computer.  You will see a Hard Drive icon for each mounted partition.  The one that says "filesystem" is Ubuntu.  Is there another one for the partition you just mounted?  Can you click on it and see the NTFS files?

---

### Post by not_yet on 2005-07-03
firstly, thanks for the help  :) 

> Third, in Ubuntu, get into a terminal and do:
$sudo mkdir /mnt/xp2
$sudo mount /dev/hda5 /mnt/xp2
Then go to Places/Computer. You will see a Hard Drive icon for each mounted partition. The one that says "filesystem" is Ubuntu. Is there another one for the partition you just mounted? Can you click on it and see the NTFS files?

only shows "filesystem", no other partitions


> Check a couple of things:
First, with Disk Manager, what does it report for that partition? Healthy? It should show it as NTFS. 

c                           ntfs                         healthy         primary           20g

extended                                             healthy         primary            33g

storage                 ntfs                        healthy         logical              32g

swap                      unknown                healthy         logical             1,066g

ext2                       unknown                healthy          primary           24g

**Note: storage was the name of the original D drive

also the graphic shows the extended and the swap as being connected

> 
Second, what does PM report?

about the same as above

from Ubuntu Gparted reports as follows

/dev/hda1        ntfs             !(symbol)               20g

/dev/hda2        ext               lock(symbol)          33g

/dev/hda5        ntfs              !                            32g

/dev/hda6        swap            lock                       1,067g

/dev/hda3        ext3             lock                        24g

**Note: the gparted graphic shows the extended partition as including

hda5 ntfs and hda6 swap

the numbers don't seem to add up :???:

---

### Post by mingus on 2005-07-04
Suggest you try a few more checks . . . 

Get into Ubuntu again in a terminal and do:
$sudo mkdir /mnt/xp2
$sudo mount /dev/hda5 /mnt/xp2
$cd /mnt/xp2
$ls
Do you see the D: files?

Now back in Windows get into Disk Manager once again.  For this partition . . .
* In the Filesystem column, does DM show the partition as "NTFS"?
* Right-click on the partition; is "Format" shown as an option or is it shaded out?
* Does DM show a drive letter?  Right-click, does DM offer the option to change the drive letter/paths?  Can you change the drive letter there to D: or another letter?
* Right-click then left-click; does DM report space used and capacity?  Look about right?  Note the summary numbers.

Now open Window Defragmenter (Start/Program/Accessories/System Tools/); does the partition show there?  If so, click on it and click on Analyze and then View Report.  Do the used and capacity numbers agree with Disk Manager?

And finally in Windows, open a Command Prompt window (Run/cmd) and type d: to switch to that partition; what if any error msg do you get?  If you are switched to D:, type dir - do you see the files?

Reason for doing above:  Isolate nature of problem.  Can be in the partition table, the filesystem, the file lable, the disk, or a particular program.  

*the numbers don't seem to add up :???*

If you are referring to the numbering sequence, it's the order of partition creation, not the placement on the disk . . . the partition boundaries all look OK.

---

### Post by not_yet on 2005-07-04
>  	Suggest you try a few more checks . . .

Get into Ubuntu again in a terminal and do:
$sudo mkdir /mnt/xp2
$sudo mount /dev/hda5 /mnt/xp2
$cd /mnt/xp2
$ls
Do you see the D: files?

yes I see the blue directories
> 
* In the Filesystem column, does DM show the partition as "NTFS"?    yes

> 
 Right-click on the partition; is "Format" shown as an option or is it shaded out?    yes format is shown


> * Does DM show a drive letter? Right-click, does DM offer the option to change the drive letter/paths? Can you change the drive letter there to D: or another letter?


no drive letter, shows "storage" ( the original partition name for D)

yes option is there to change the drive letter



> * Right-click then left-click; does DM report space used and capacity? Look about right? Note the summary numbers.

Now open Window Defragmenter (Start/Program/Accessories/System Tools/); does the partition show there? If so, click on it and click on Analyze and then View Report. Do the used and capacity numbers agree with Disk Manager?

yes they are the same


> And finally in Windows, open a Command Prompt window (Run/cmd) and type d: to switch to that partition; what if any error msg do you get? If you are switched to D:, type dir - do you see the files?

no says "can't find path

Question: could the problem be that the extended partition contains the old "storage" partition and the linux swap partition?

---

### Post by not_yet on 2005-07-04
hi mingus,

went back and changed the drive letter to D in DM / as per your suggestion

surprise, surprise, all good now :)  :) 

I can see the whole D drive again

thank you very much for your assistance

/me slides mingus a tall cool beer :)  :)  ( only if your of age of course  ;-) )

cheers

---

### Post by mingus on 2005-07-05
[I]went back and changed the drive letter to D in DM / as per your suggestion

surprise, surprise, all good now :)  :) 

I can see the whole D drive again[/I]

Great.  Somehow you lost the drive letter assignment.  Very strange.  I suggest you run PM's DriveMapper utility to make sure that all the Registry partition pointers are correct.

*/me slides mingus a tall cool beer :)  :)  ( only if your of age of course  ;-) )*

Thanks . . . I've been of age for longer than I can remember.

---

### Post by DHLawrence on 2005-07-05
How can you find out which partition contains the swap partition if it isn't labelled as such in sudo fdisk? I'm trying to find out which one it is for editing a boot script.

---

### Post by mingus on 2005-07-05
[QUOTE=DHLawrence]How can you find out which partition contains the swap partition if it isn't labelled as such in sudo fdisk? I'm trying to find out which one it is for editing a boot script.[/QUOTE]

$sudo fdisk -l

will show you all the partitions, you should see one labeled "Linux swap" - if you don't, it isn't there.

---

### Post by bpilgrim1979 on 2005-07-22
what does the flag "lba" mean in gparted?

---

### Post by mingus on 2005-07-22
[QUOTE=bpilgrim1979]what does the flag "lba" mean in gparted?[/QUOTE]

logical block addressing

---

### Post by bpilgrim1979 on 2005-07-23
[QUOTE=mingus]logical block addressing[/QUOTE]

Thanks, do you know if this is necessary for Windows.  If so, how do I set it?

See [my other post on ubuntuforums](http://ubuntuforums.org/showpost.php?p=267125&postcount=3).

---

### Post by mingus on 2005-07-23
[QUOTE=bpilgrim1979]Thanks, do you know if this is necessary for Windows.  If so, how do I set it?

See [my other post on ubuntuforums](http://ubuntuforums.org/showpost.php?p=267125&postcount=3).[/QUOTE]

LBA is a technology that was invented to get around the disk size limitation in earlier systems.  My memory is sketchy on the details, I think it was initially introduced at 32-bit and then a later 48-bit called Extended LBA.  It needs to be supported by both the BIOS and the OS.  With LBA disk geometries are calculated differently and so it also overcomes the 1024 cylinder limitation on x86 machines.  LBA is turned on in the BIOS setup for a drive.  I don't know why lba would be written in to the label for a particular partition.  In your BIOS, make sure the full capacity of the drive is being reported; if it's not, you may have problems with partitioning.

Your other thread indicates XP cannot act on partitions you created for it with GParted.  Don't know why.  But there is a general safety rule of thumb:  If you can, try to use an OS partitioner native to the OS that will reside on a partition, do not mix partitioners on the same partition, and do not use a W$ partitioner and a Linux partitioner on the same partition.  Has to do with how geometries are calculated, boundary addresses, how the partition table is written to, and how data elements in the table are used.  Gets extra dicey when W$ and other OS partitions are interleaved inside an extended.  Hands-down the best tool for multi-OS disks is PartitionMagic.  If you don't have that, then delete that first partition you created with GParted with that tool, leave the space unallocated, and then try Disk Manager to create and format it.  One time I got around overlapping table records by leaving a small amount of unallocated space between the partitions to compensate for the different boundary address calculations.

---

### Post by bpilgrim1979 on 2005-07-24
Okay, thanks for your detailed response.

The original ide drive came with an IBM Thinkpad.  About a year ago, IBM starting putting the "recovery cd" in a hidden part of the hdd.  Those lba flags are on the original partitions shipped from IBM.

---

### Post by eeried on 2005-07-25
> About a year ago, IBM starting putting the "recovery cd" in a hidden part of the hdd

Ah the bother - I know ! Now that hda2 partition is at the end of the HDD, and I installed Ubuntu between hda1 (C windows) which I resized with qtparted and hda2 which I left well alone.

Now LBA: funnily enough Ubuntu statred t identify my external zip drive as LBA.

Later as USB0, later as Zip-100, and finally as Iomega... I move the drive betwwen my desktop and that laptop -- only way I can shift documents in the absence of a LAN.

---

