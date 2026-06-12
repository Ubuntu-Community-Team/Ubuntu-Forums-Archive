---
title: "Recover data from a .img file"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by itz_nsn on 2011-02-07
I was dual booting Ubuntu 10.10 with windows 7 on a Toshiba Satellite L305D laptop - recently ubuntu asked for an automatic update and after i did that, my grub was corrupted and i could not boot - i tried to use the live cd and repair but my partition table was messed up - my friend took a full disk image of my disk and now i have a 230GB ".img" file. I want to recover data from this file - i have been following blogs an reading articles - but very few articles on how to get data out of the .img file 

i have the img file in a 1TB external drive 

What i have tried till now 
1. foremost - sudo foremost -w -i /img-file -o /recovery/foremost 
tried to get an audit of the files that i can recover - foremost ran for a while and the output was empty 

2. fsck.ext4 -y filename.img 
e2fsck 1.41.12 
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open naveenorig.img

The superblock could not be read or does not describe a correct ext2 file system.  If the device is valid and it really contains an ext2 file system (and not swap or ufs or something else), then the super block is corrupt, and you might try running e2fsck with an alternate superblock:     e2fsck -b 8193 <device>

I tried the alternate superblock and it gives me the same message

3. Sleuthkit mmls 
Command : mmls filename.img
Result was "Cannot determine partition type (GPT or DOS at 0)"

Next i tried "mmls -t dos filename.img"
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
00:  Meta    0000000000   0000000000   0000000001   Primary Table (#0)
01:  -----   0000000000   0000000000   0000000001   Unallocated
02:  00:00   0000000001   4294967295   4294967295   GPT Safety Partition (0xEE)

I did not know what to do further - one tutorial said to multiply the offset by 512 and mount that partition, but i am not able to do that 

4. Currently i am trying a file craver called Scalpel 
scalpel filename.img -o /output-dir 

I think it will run for the whole night 

Is there any way to get the data out of the image file of my hard disk? If scalpel fails what should i do? 
I have searched for softwares that can extract data from .img files but could not find any - i have started looking at professional softwares - can you suggest one? 

Please help 

Thank you for your time

---

### Post by itz_nsn on 2011-02-10
any suggestions?

---

### Post by srs5694 on 2011-02-10
A lot depends on the format of that backup file. The fact that it has an extension of ".img" doesn't really mean much; it could be just about anything. If it's a raw disk image (say, created by "dd if=/dev/sda of=filename.img", then you should be able to access it in various ways -- say, by using mount with appropriate options to mount the filesystems it contains. If the file was created with a tool that only backs up used sectors, though, you'll need to use that tool (or something compatible with it) to access the data. I recommend you ask your friend who made the backup for help.

I'm not familiar with the mmls utility, but the output you posted suggests that the disk uses the GUID Partition Table (GPT) partitioning system rather than the more common Master Boot Record (MBR) system. There's nothing wrong with this per se, but it is unusual, particularly on a system that boots Windows -- Windows requires MBR to boot when a computer uses a BIOS, which most still do. (Windows boots from GPT disks on computers that use an EFI.) If your computer uses (U)EFI, that's important information. If you were experimenting with GPT for some reason (say, to install OS X on a PC), that's also important information.

You should *not* attempt to use fsck or similar tools on the backup file unless you understand how to use those tools to access the actual partitions contained within the file, which you clearly don't understand. At best, nothing will happen. At worst, you'll damage your backup.

It's probably better to try to recover the data on the original disk than using the backup. The reason is that data recovery tools are generally written with the assumption that they'll be operating on a disk rather than a file. Some important options may not work correctly (or at all) when applied to a file. Use your backup file as a way to recover if you make your original worse. There's also the issue of the format of the data file; if it's anything but a raw sector-for-sector copy, the standard data recovery tools won't work properly with it.

I recommend you boot a live CD (such as the Ubuntu installer in "try before installing" mode, or whatever it's called) on the computer, download the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) run it, and post the RESULTS.txt file it produces (either as a link or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings). This will give us more information on the state of your disk.

---

