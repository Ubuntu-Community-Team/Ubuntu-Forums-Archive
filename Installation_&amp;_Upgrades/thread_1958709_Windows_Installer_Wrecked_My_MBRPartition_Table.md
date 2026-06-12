---
title: "Windows Installer Wrecked My MBR/Partition Table"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by linuxftw11 on 2012-04-14
Here are the steps I took to get where I am now:


    I wanted to install a fresh version of Windows 7 as I use it for gaming.
    I had made an image of the win7 partition with dd, and saved it to another partition (in case there were files I needed after I'd deleted the partition).
    I booted into win7 install from a usb flash drive.
    I wanted to delete the first two primary partitions as (for some bizarre reason) windows decided to waste one of four primary partitions with a 100mb part at the start of the disk, the other one was a 30gb part for windows.
    I deleted them from windows setup.
    Windows setup sat there for more than 5 minutes (no idea what the hell it was doing). So I got annoyed and thought "I will just boot into linux again and use gparted".
    So I reset the PC...
    I got the dreaded 'grub rescue' menu.
    I have a laptop with Fedora installed so I booted into that and stuck grub2 + puppy linux onto a USB.




Before this nightmare started I had two primary partitions that windows allocated its self when I installed it, an extended partition with around 5/6 partitions in it for linux distros, some unallocated space, and the last primary partition was an 800gb ntfs partition I use for all my games/vids/music etc.

So here is a list of problems I need to solve:

    I have 700gb of data on the ntfs partition that is accessible from mounting sda3 in linux, the files are readable (the ones I've tested at least). I only have a 1TB HD available at the moment.
    When I load the drive up in gparted it does not show any partitions, it says "unallocated".



fdisk -l

```

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              14        5549    41840640    7  HPFS/NTFS
/dev/sda2            5549       13870    62912191    5  Extended
/dev/sda3           13870      129202   871905601    7  HPFS/NTFS
/dev/sda5            5549        6243     5245222+  83  Linux
/dev/sda6            6243        8987    20747916   83  Linux
/dev/sda7            8988        9271     2141184   83  Linux
/dev/sda8            6243        8987    20747916   83  Linux
/dev/sda9            8988        9271     2141184   83  Linux
/dev/sda10           6243        8987    20747916   83  Linux
/dev/sda11           8988        9271     2141184   83  Linux
/dev/sda12           6243        8987    20747916   83  Linux
/dev/sda13           8988        9271     2141184   83  Linux
/dev/sda14           6243        8987    20747916   83  Linux
/dev/sda15           8988        9271     2141184   83  Linux
/dev/sda16           6243        8987    20747916   83  Linux
/dev/sda17           8988        9271     2141184   83  Linux
/dev/sda18           6243        8987    20747916   83  Linux
/dev/sda19           8988        9271     2141184   83  Linux
/dev/sda20           6243        8987    20747916   83  Linux
/dev/sda21           8988        9271     2141184   83  Linux
/dev/sda22           6243        8987    20747916   83  Linux
/dev/sda23           8988        9271     2141184   83  Linux
/dev/sda24           6243        8987    20747916   83  Linux
/dev/sda25           8988        9271     2141184   83  Linux
/dev/sda26           6243        8987    20747916   83  Linux
/dev/sda27           8988        9271     2141184   83  Linux
/dev/sda28           6243        8987    20747916   83  Linux
/dev/sda29           8988        9271     2141184   83  Linux
/dev/sda30           6243        8987    20747916   83  Linux
/dev/sda31           8988        9271     2141184   83  Linux
/dev/sda32           6243        8987    20747916   83  Linux
/dev/sda33           8988        9271     2141184   83  Linux
/dev/sda34           6243        8987    20747916   83  Linux
/dev/sda35           8988        9271     2141184   83  Linux
/dev/sda36           6243        8987    20747916   83  Linux
/dev/sda37           8988        9271     2141184   83  Linux
/dev/sda38           6243        8987    20747916   83  Linux
/dev/sda39           8988        9271     2141184   83  Linux
/dev/sda40           6243        8987    20747916   83  Linux
/dev/sda41           8988        9271     2141184   83  Linux
/dev/sda42           6243        8987    20747916   83  Linux
/dev/sda43           8988        9271     2141184   83  Linux
/dev/sda44           6243        8987    20747916   83  Linux
/dev/sda45           8988        9271     2141184   83  Linux
/dev/sda46           6243        8987    20747916   83  Linux
/dev/sda47           8988        9271     2141184   83  Linux
/dev/sda48           6243        8987    20747916   83  Linux
/dev/sda49           8988        9271     2141184   83  Linux
/dev/sda50           6243        8987    20747916   83  Linux
/dev/sda51           8988        9271     2141184   83  Linux
/dev/sda52           6243        8987    20747916   83  Linux
/dev/sda53           8988        9271     2141184   83  Linux
/dev/sda54           6243        8987    20747916   83  Linux
/dev/sda55           8988        9271     2141184   83  Linux
/dev/sda56           6243        8987    20747916   83  Linux
/dev/sda57           8988        9271     2141184   83  Linux
/dev/sda58           6243        8987    20747916   83  Linux
/dev/sda59           8988        9271     2141184   83  Linux
/dev/sda60           6243        8987    20747916   83  Linux

Partition table entries are not in disk order

```As you can see from the above, the Windows setup tool has really screwed me over!

I have assignments I need to complete tomorrow and would like to get my computer back online and be able to boot from a HD (into anything, preferably Lubuntu).

As I don't understand what windows setup has done to the drive I can't fix it, and don't want to either until I understand the problem. I don't want to risk losing my data on the ntfs partition.

If I had a spare HD lying around I know I could just copy the files over (or image the whole disk) and make a new partition table with fdisk, but I don't have one at the moment.

Does anyone understand what had happened here? Any help would be appreciated.

---

### Post by darkod on 2012-04-15
I don't know exactly what happened during the partitioning. If I understand correctly, you tried to delete the partitions win7 wanted to create during the same installation process. I guess that confused the hell out of it.

You can try testdisk from live mode, it should be able to bring back your old partition table:[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

And for the future, if you don't want win7 to create the 100MB partition, make a ntfs partition for it in advance, BEFORE you start the installer. If you already have existing partition and only tell it to format it and use it, it will not create the 100MB boot partition.

If you use the win7 installer to create the win7 partition, then it will chop off 100MB from it and create two primary partitions. So don't use the win7 installer for partitioning, have it prepared in advance.

---

### Post by linuxftw11 on 2012-04-15
Thank you!  That software helped somewhat.  Here is what fdisk gives me now... 
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              13        5222    41840640    7  HPFS/NTFS
/dev/sda3            5223        5875     5245220   83  Linux
/dev/sda4            5876      121602   929577127+   f  W95 Ext'd (LBA)
/dev/sda5            5876        8458    20747264   83  Linux
/dev/sda6            8459        8726     2141184   83  Linux
/dev/sda7            8726        9237     4103160   82  Linux swap / Solaris
/dev/sda8           12543       13032     3926868+   c  W95 FAT32 (LBA)
/dev/sda9           13055      121602   871905596+   7  HPFS/NTFS

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```I know about the 100mb partition windows creates, I installed win7 years ago and it's lay dormant for some time now :), I've only just got round to re-installing it.

You can get around the 100mb in Windows setup also, you just need to create the partitions with the windows setup partition editor before telling it to use that partition as the boot medium. Can't remember EXACTLY how it's done, but I've done it before with VB installations and it's worked fine.

Anyway, testdisk seems to have fixed the MBR, but when I load the disk in gparted it still tells me the disk has 990(ish) of unallocated space.

When I run fdisk on sda I get this...

```

The number of cylinders for this disk is set to 121601.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```Any ideas where I can go from here?

Not sure what a 'cylinder' is to be honest.

---

### Post by oldfred on 2012-04-15
Are you running an old version of fdisk?

Up until the last year or two many partition tools still referred to cylinders, but drives have not used them since hard drives went over 8GB. BIOS converted to using LBA or large block allocation. Back then we had to set cylinders, heads & sectors in BIOS to get it to read hard drive.

Is BIOS set to use legacy IDE or the older cylinders mode? 
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

Or is this an older system with a new large hard drive.

---

### Post by darkod on 2012-04-15
That warning message is strange. First of all, it says there is nothing wrong in having 121601 cylinders, and I think that number is really correct.

To double check, I run fdisk to show details of one 500GB disk I have, and the cylinders number is 60801 which is exactly half of your number, as you would expect because your disk is double the size.

Does that partition table recovered by testdisk look OK with you?

Did you try booting the computer as it is now? You might need to repair the bootloader regardless which one you were using.

Otherwise, the cylinders referred are the imaginary cylinders on the HDD plate, the concentric circles. A 1TB disk should have 121601 cylinder so that sounds right.

---

### Post by linuxftw11 on 2012-04-18
I'm not sure what version of fdisk I'm running, I'm running it from puppy linux (lupu528.iso).

I think this machine is around 5 years old, it's a SATA connection however so I don't think that's the problem.

Yes the partition table looks exactly the same as it did before, I can  mount and access all of the data in the partitions, I can even run  virtualbox from puppy and boot into a win7 image I had lying around on  the ntfs partition.

I just want to install Lubuntu! <img  src="http://ubuntuforums.org/images/smilies/icon_sad.gif" border="0"  alt="" title="Sad" smilieid="11" class="inlineimg" />

I shall try reinstalling grub2 from an ubuntu iso and post the results here.  Thanks for the help everyone!

Also I'll run fdisk from the Ubuntu iso as I assume that will be a newer version.



Another quick question...

Shall I install Lubuntu/Kubuntu 11.10 now, or is it best to wait a few weeks/days for version 12.04?

---

### Post by linuxftw11 on 2012-04-18
Not sure what happened there.

Is it because I have noscript enabled? Forgot to allow Ubuntu :D

---

### Post by linuxftw11 on 2012-04-18
Duplicate post.

Couldn't find the 'delete button'.

Disaster, I can't even post in a forum without messing something up! :lolflag:

---

### Post by linuxftw11 on 2012-04-18
Some updates...

I could not boot into Ubuntu iso at first. It said there was a problem with /dev/sda8 so I ran this command for a few seconds in puppy...

```
dd if=/dev/zero of=/dev/sda8
```That solved the problem, I can now chainload into ubuntu-11.10-64bit iso from grub2 (from a flash drive).

Test disk now gives the following...

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 4 E extended LBA          5875   0  1 121601 254 63 1859154255
No partition is bootable
 5 L Linux                 5875   1  1  8457 234 19   41494528 [_Fedora-16-x86_6]
   X extended              8458 175  1  8725  65 44    4282469
 6 L Linux                 8458 176 39  8725  65 44    4282368 [fedora-install]
   X extended              8725  97  1  9236  52 16    8206396
 7 L Linux Swap            8725  98 14  9236  52 16    8206320
   X extended             12542 114  1 13031  83 21    7853853
Invalid FAT boot sector
 8 L FAT32 LBA            12542 115 54 13031  83 21    7853737
 8 L FAT32 LBA            12542 115 54 13031  83 21    7853737
   X extended             13053 254  1 121601  57 47 1743811256
 9 L HPFS - NTFS          13054   0  1 121601  57 47 1743811193 [ntfs]

```Invalid FAT boot sector? That could be what's causing the problem.

A few days ago I decided to install direct from my HD instead of a USB flash as it's a lot faster, I just used dd to copy a FAT partition boot sector from a win7 usb install I had (I made the boot sector with MS bootsect.exe a few months ago) to one of the extended partitions. Obviously a silly move, I was just experimenting to see if it would work.

I would rather now remove all partitions, including the extended ones and just leave the ntfs partition.

Can I use dd to zero out these paritions and then use testdisk to recover the ntfs partition afterwards?

I tried using 'parted' to modify the disk I got this...

```
Error: Can't have a partition outside the disk!
```Also I have deleted the first three paritions in fdisk, but linux still finds the extended partitions.

I think it may be time to buy a new HD so I don't lose all of my data :D

I'm planning on buying  a new one anyway so I can set up a RAID 0 for faster data transfers. Could I use a 2TB HD with the 1TB, but split the 2TB into two partition so the first partition is RAID 0 but 2nd isn't? (if that makes sense).

---

### Post by darkod on 2012-04-18
If you only need to read the NTFS partition, try fixparts to solve your partition outside the disk error.

Try not to work on partitions with fdisk, it's a good tool for quick show of partitions, but don't manage them with it.

Use cfdisk (if the partition table is msdos), or parted.

As for the raid0 question, depending what you use. If you use fakeraid, it works on disk level so you can't use half of the disk for raid0 and the other half for something else. Linux software raid works on partition level, so yes, you can do that.

But if you want to dual boot, you are stuck with fakeraid because windows can't understand the linux software raid.

---

### Post by linuxftw11 on 2012-04-18
I've just tried cfdisk, it told me that partition 4 is bad because it ends after the end-of-disk. Then it terminated.

I think I'll just switch to linux for good and run windows applications in a VB where they belong, I need to stop wasting my time playing computer games anyway :D

I was thinking of buying a PCI raid card, but I doubt they work on a partition level? I think linux software raid is the way forward.

Excited now... might buy a new 2TB HD and hope it gets delivered tomorrow.

I'll do some research on fixparts and see if I can get it fixed today.

Thanks again :D

---

### Post by linuxftw11 on 2012-04-18
Sounds brilliant, I can even backup the partition table to a text file with sfdisk.

Hopefully I can get this sorted out today.

---

### Post by linuxftw11 on 2012-04-18
IT'S FIXED! :guitar:

Thanks!

I've been compressing and deleting files all morning so I've got around 400GB of data in the ntfs partition.

Now I can create a new 400gb ext4 partition at the end of the disk, copy my files to it, and be free of the windows curse!

FREEDOM!

I think I'll invest in a bluray burner and some blank disks, always good to keep backups offsite.

---

### Post by oldfred on 2012-04-18
Windows partitions have to have a partition boot sector - PBR that matches the partition they are in or the partition table. So you cannot copy one to another. Also FAT, NTFS with XP & NTFS with Vista/7 have different data in the PBR. I had used chkdsk on my XP install from a Windows 7 USB and it worked better at chkdsk but wrote a Windows 7 PBR. I could see the difference in testdisk's compare backup with current and one had bootmgr and the other had ntldr.

If you really want speed, consider a SSD. I recently got one and it is a real luxury. Boot is quick, programs load fast. Somehow I do not type any faster or even more correctly though. And Internet downloads do not change. But I never saw an install go so fast as a grub2 boot of the ISO from my rotating hard drive to install to my SSD.

---

### Post by linuxftw11 on 2012-04-18
Yeah I can get a 60GB SSD for less than the price of a 2TB disk.

Probably a better investment as most of my files can be re-downloaded anyway. And I'm only using 40% of the 1TB disk.

How about two of them in a raid 0 config? I like the sound of that! :) Especially with linux as it doesn't take up a ridiculous amount of space for the OS.

---

### Post by darkod on 2012-04-18
Note that is raid0 you have no redundancy. If one disk goes, everything is gone. :)

---

### Post by linuxftw11 on 2012-04-19
> **darkod said:**
> Note that is raid0 you have no redundancy. If one disk goes, everything is gone. :)

Shall have to set up some nice backup scripts.

I've just installed Lubuntu to my HD, it's using 200mb of 3GB ram with firefox open. Awesome!

It's good to be back, I've tried a few different distros but I always return to Ubuntu.


```

Linux Mint < --------------Ubuntu---------------> Fedora

```Mint was too user-friendly, I noticed it had loads of ports open for samba servers etc by default, no thanks.

With Fedora I had to recompile the kernel everytime there was an update because I was using the non-OS edition because of USB2 support.

Ubuntu seems to be a nice middle ground.

Has anyone got any idea why tab-completion isn't working with 'apt-get install' in Lubuntu? In Ubuntu I can type say 'apt-get install p7' and then tab twice and it will list the packages.

Is this a bug or do I need to install an extra package?

---

