---
title: "Ubuntu installer and gparted(on live disc) do not see hard drive partition table"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by instantepiphany on 2011-10-04
Hi all,

I am by no means a linux newbie, I have been using various distros for several years. I have just built a new computer with rendering in mind,(6-core cpu etc) and I cannot for the life of me install ubuntu 11.04 on it.

I have already installed win7, and I cannot lose the data on it and do not have a backup drive handy.

When I boot into the ubuntu live cd and start the installer, it gets to the partitioning stage and says something like "No operating system detected" and gives me the option to wipe the disk and install ubuntu or to manually create partitions. I tried going the manual option, but it didn't show any of my win7 partitions(100mb system partition, 1.8tb C: drive).
I found something on the web about win7 not partitioning properly, and sometimes the end partition was allocated one more sector than was on the drive. Sure enough, fdisk showed that the last partition ended on a sector that didn't exist.

e.g this is a flash drives output

```
Disk /dev/sde: 2038 MB, 2038431744 bytes
251 heads, 62 sectors/track, 255 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          64     3981311     1990624    c  W95 FAT32 (LBA)
```
You can see that sde1 ends on 3981311, and there are 3981312 total sectors.
I cannot remember the number for my harddrive, but the partition ended on one more than the number of total sectors, eg 4581235 total sectors, and the partition ended on 4581236.

Could someone help me solve this without reinstalling win7 or losing data?

Thanks

---

### Post by WasMeHere on 2011-10-04
> **zzcranjo said:**
> Hi all,

I am by no means a linux newbie, ... I have already installed win7, and I cannot lose the data on it and do not have a backup drive handy.
...
Could someone help me solve this without reinstalling win7 or losing data?

Thanks
I would start this task backing up the disk using Clonezilla to make an image of the disk onto an external disk. I think it is risky to tamper with the win7 partition, so wait until you get such a drive.

Then I would try various tools to 'prune' the ntfs file system. I suggest that you start with the *chkdsk* utility (or some clone of it) of win7, winvista or winxp and see if the partition can be repaired (or should we say standardized?). Use the built-in help to find a 'strong' option for chkdsk! I guess that win7 also needs defragmentation, so that would be the next step before edting the partitions.

---

### Post by instantepiphany on 2011-10-04
Yeah I will try chkdsk and report the results, but I don't think I need to defrag, I just finished building the computer 2 days ago, so not much fragmentation as of yet :D I started using the hd in an external enclosure about 1 month ago, but when I put it in my new build a couple days ago, win7 refused to install on it, so I had to format.

---

### Post by dino99 on 2011-10-04
i cant trust the installer and gparted break ntfs on resizing, so be aware. Better to use partedmagic

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by instantepiphany on 2011-10-04
i don't think you have read my posts properly Dino, I cannot touch the hard drive from Linux as it will erase windows seven. Also the post you made in the thread you linked to is wrong, swap size should be at least two gigs, bu if you want to hibernate you need your swap to be bigger than your total ram, in my case, eight gigs.

---

### Post by dino99 on 2011-10-04
maybe you dont too ;)

there is no relation about the installed ram and the swap size, it only depends on the needs (suspend/hibernation, or heavy special app needs)

---

### Post by instantepiphany on 2011-10-04
Nope, hibernation stores the rams contents in the swap disk, as when ram is unpowered it is wiped. Ram is volatile, that is why it cannot retain its contents without power. So when you wake a computer from hibernation, the contents of the swap disk are transferred to the ram. If the swap size is smaller than the ram then corruption could occur, so both win7 and linux only let you hibernate if your swap is bigger than your ram. Please stop hijacking my thread, pm me if you want to argue further.
Please people can we stay on topic?

---

### Post by coffeecat on 2011-10-04
> **zzcranjo said:**
> 
e.g this is a flash drives output

```
Disk /dev/sde: 2038 MB, 2038431744 bytes
251 heads, 62 sectors/track, 255 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          64     3981311     1990624    c  W95 FAT32 (LBA)
```
You can see that sde1 ends on 3981311, and there are 3981312 total sectors.
I cannot remember the number for my harddrive, [COLOR="Red"]but the partition ended on one more than the number of total sectors, eg 4581235 total sectors, and the partition ended on 4581236.[/COLOR]

The bit in red is the reason Gparted is not showing any partitions and the installer is having difficulty making sense of your hard drive. But why did you not post the fdisk output for your hard drive? :? 

Post the full output of 'sudo fdisk -lu' to be sure. If an end partition sector is beyond the last physical sector of the drive, this is an inconsistency in the partition table, but is easily fixed.

---

### Post by instantepiphany on 2011-10-04
Because the pc was (still is) running chkdsk. >  If an end partition sector is beyond the last physical sector of the drive, this is an inconsistency in the parition table, but is easily fixed. 
It is. Thats why i said it, you even highlighted it in red :P
So how do I fix it?

---

### Post by coffeecat on 2011-10-04
> **zzcranjo said:**
> 
It is. Thats why i said it, you even highlighted it in red :P

Yes, but I like to see the whole of fdisk's output before offering suggestions. Or is it a secret? :wink:

> **zzcranjo said:**
> So how do I fix it?

The easy way:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

The Sourceforge site is a bit of a labyrinth. Make sure you download fixparts and not gdisk. It has been known - you do not want to run gdisk in this situation! 

The "fun" way:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

**EDIT**: whichever you choose, backup anything valuable - you are messing with the partition table. Having said which, I've used both methods without problem.

---

### Post by Mark Phelps on 2011-10-04
> **zzcranjo said:**
> ... I have already installed win7, and I cannot lose the data on it and do not have a backup drive handy.

All the more reason to not use ANY Linux utility on this drive!

What you could try, and even THIS comes with some risk, is booting into Win7 and using the Disk Management utility to shrink the Win7 OS partition just a little.  That will cause the partition table to be rebuilt and may solve your current partition problem.

---

### Post by instantepiphany on 2011-10-04
Coffecat, I tried fixparts, and I made sure not to use gdisk. I started cmd.exe in administrator mode, and changed directory to where I put fixparts. It wouldn't run properly. Here is the output.
```
FixParts 0.8.0
Type device filename, or press <Enter> to exit: 0

Loading MBR data from 0
Problem opening 0 for reading!

Unable to read MBR data from '0'! Exiting!
```
I tried pressing 1 instead of 0, then 2, 3 etc all the way to 10. 0 Should have worked as I only have one drive in my system. I will note, it is a sata drive.

---

### Post by coffeecat on 2011-10-04
It looks as though you used the Windows version of fixparts which I am not familiar with - am I right? It might be easier to use the Linux version from the Ubuntu live CD. But don't do that yet, if at all....

On second thoughts, we really do need to see the output of fdisk. There may be other partition table irregularities which you missed and which might affect how you go about dealing with this problem. Also let's get the output of sfdisk so that you have a proper backup of the partition table data as it is now. You need to use Ubuntu for this - presumably you'll need to use a live CD/USB. Post the output of:

```
sudo fdisk -lu
sudo sfdisk -d /dev/sda > Desktop/parts.txt 
```

The second command will produce the file parts.txt on the desktop - replace /dev/sda with whatever the affected hard drive is designated. Save this on a separate medium as well as posting it so that you have a secure backup.

**EDIT**: Another thought. Mark Phelps makes a valid point. If this was just a partition table irregularity then it wouldn't matter which OS you chose to repair it. However it might affect a NTFS filesystem as well, but you haven't given us enough information to go on, and if a NTFS filesystem then I agree with Mark Phelps and using Windows to resize it might be part of the answer. Another reason to post the full output of fdisk and sfdisk. Please! :)

---

### Post by instantepiphany on 2011-10-04
Yeah I'll do both of those when I can. Thanks, I'll post back with the output of fdisk then.

---

### Post by instantepiphany on 2011-10-16
Fixparts didn't work for me.
```

C:\Users\*******\Downloads\fixparts-windows-0.8.0>fixparts 0
FixParts 0.8.0

Loading MBR data from 0
Problem opening 0 for reading!

Unable to read MBR data from '0'! Exiting!


C:\Users\*******\Downloads\fixparts-windows-0.8.0>fixparts C:
FixParts 0.8.0

Loading MBR data from C:
Problem opening \\.\physicaldriveC for reading!

Unable to read MBR data from 'C:'! Exiting!


C:\Users\*******\Downloads\fixparts-windows-0.8.0>fixparts C
FixParts 0.8.0

Loading MBR data from C
Problem opening C for reading!

Unable to read MBR data from 'C'! Exiting!


C:\Users\*******\Downloads\fixparts-windows-0.8.0>fixparts C:\
FixParts 0.8.0

Loading MBR data from C:\
Problem opening \\.\physicaldriveC for reading!

Unable to read MBR data from 'C:\'! Exiting!


C:\Users\*******\Downloads\fixparts-windows-0.8.0>fixparts sda
FixParts 0.8.0

Loading MBR data from sda
Problem opening sda for reading!

Unable to read MBR data from 'sda'! Exiting!

```

Sorry for the late reply, been busy.

EDIT:
I noticed the readme included was for gdisk, not fixparts. I searched online and within 1 minute found that I needed to do
```

C:\Users\******\Downloads\fixparts-windows-0.8.0>fixparts \\.\physicaldrive0
FixParts 0.8.0

Loading MBR data from \\.\physicaldrive0

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):

```
instead. Do I do it?

---

