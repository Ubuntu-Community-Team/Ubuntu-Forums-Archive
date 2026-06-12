---
title: "Should I Dual-Boot?"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by Deedlebag on 2012-12-20
(Sorry if this isn't the right section)

I am curious as to if I should dual-boot operating systems. As of now, I currently am running Windows 7, but I also want to use Ubuntu. Now I've done this before on a less powerful computer, but I want to ensure I'm able to do this on my newer PC.
Here are my specs:
Processor - AMD FX 8-Core Processor, Black Edition (4 Cores, 8 Logical Processors)
RAM - 8GB
Hard Drive - 250GB

What I'm most worried about is hard drive space, but I want to know what you guys think? Can my computer handle a dual boot? And any other important helpful tips would be nice.

Thanks!

---

### Post by ZombieApocalypse on 2012-12-20
If you're willing to create a shared partition for the two operating systems, then it won't be a problem. You could shrink the Windows7 partition down to 20GB, create a Ubuntu partition of the same size, a swap partition of 16GB (ie twice your installed memory) and use the rest of the drive (around 140GB) as a shared partition (remember to keep this as NTFS), which you would mount as your home drive in Ubuntu.

---

### Post by sudodus on 2012-12-20
The answer is probably yes :-)

Have you tried running a live session yet? (Booted from an install USB/CD/DVD drive). If that works, the computer can run with Ubuntu.

There might be problems with new computers due to complicated bios (or equivalent newer) systems and new Windows installation ways. But there is help available here at the Ubuntu Forums. I have only fairly old computers, but there are people around here, who know about such new systems, and how to make a successful dual boot installation.

I agree that 20 GB is enough for the Ubuntu root partition '/'.

In my humble opinion:
leave much more than 20 GB to Windows
use ext4 or ext3 partitions for / and /home
and use a separate data partition formatted to NTFS

---

### Post by Mark Phelps on 2012-12-20
When you go to shrink down Win7, do NOT use the Ubuntu installer, with the slider, to do the shrinkage.  Win7 is touchy about changes being made to its OS partition from Linux tools, and all too often, will end up with a corrupted filesystem, and not be bootable anymore.

Better approach is to use the Win7 Disk Management utility to shrink down the OS partition.  Then, reboot into Win7 a couple of time to let it do filesystem adjustments.

Also, while you're in Win7, use the Backup feature to create and burn a Win7 Repair CD (if you have a CD drive).  That will be invaluable later, should you need to repair Win7 from the dual boot setup.

---

### Post by ZombieApocalypse on 2012-12-20
> **Mark Phelps said:**
> When you go to shrink down Win7, do NOT use the Ubuntu installer, with the slider, to do the shrinkage.  Win7 is touchy about changes being made to its OS partition from Linux tools, and all too often, will end up with a corrupted filesystem, and not be bootable anymore.

Better approach is to use the Win7 Disk Management utility to shrink down the OS partition.  Then, reboot into Win7 a couple of time to let it do filesystem adjustments.

A very good point! That's how I created my dual-boot system.

> Also, while you're in Win7, use the Backup feature to create and burn a Win7 Repair CD (if you have a CD drive).  That will be invaluable later, should you need to repair Win7 from the dual boot setup.

You only need to do this if you don't have a Windows 7 installation disc.

---

### Post by Pjotr123 on 2012-12-20
> **Mark Phelps said:**
> When you go to shrink down Win7, do NOT use the Ubuntu installer, with the slider, to do the shrinkage.  Win7 is touchy about changes being made to its OS partition from Linux tools, and all too often, will end up with a corrupted filesystem, and not be bootable anymore.

Better approach is to use the Win7 Disk Management utility to shrink down the OS partition.  Then, reboot into Win7 a couple of time to let it do filesystem adjustments.

Also, while you're in Win7, use the Backup feature to create and burn a Win7 Repair CD (if you have a CD drive).  That will be invaluable later, should you need to repair Win7 from the dual boot setup.
Nothing wrong with using Windows 7 to do the shrinking, but very much nothing wrong with Ubiquity (the Ubuntu installer) doing that, too... At least in my experience. This is the first time that I've heard about such problems. And I consider myself to be an experienced Ubuntu user.

Of course you'll find that Windows needs to do a file system check when booted the first time after being shrunk by Ubiquity, but that's normal and no problem at all....

---

### Post by cybrsaylr on 2012-12-20
I've been dual booting with XP, Vista and W7 since 2007 with no problems using the Linux partitioning tools. Done dual boots with a Pentium II up to my present i7 with no issues. Ubuntu ran great on all of them. 

With Windows I always did a defrag first before installing Ubuntu on the back end of the hard drive. If you are pressed for space Ubuntu will run fine on as little as a 10 GB partition but I usually prefer 20 GB or more.

---

### Post by El Tito on 2012-12-20
> **ZombieApocalypse said:**
> If you're willing to create a shared partition for the two operating systems, then it won't be a problem. You could shrink the Windows7 partition down to 20GB, create a Ubuntu partition of the same size, a swap partition of 16GB (ie twice your installed memory) and use the rest of the drive (around 140GB) as a shared partition (remember to keep this as NTFS), which you would mount as your home drive in Ubuntu.

I would give no more than 1GB to swap; with 8GB of RAM you shouldn't have problems. The rule 'twice your RAM' was for older computers in which low memories were an issue. I would give a little more space for the windows partition, as mentioned above.

Good luck!

---

### Post by Pjotr123 on 2012-12-20
> **El Tito said:**
> I would give no more than 1GB to swap; with 8GB of RAM you shouldn't have problems. The rule 'twice your RAM' was for older computers in which low memories were an issue. I would give a little more space for the windows partition, as mentioned above.

Good luck!

The rule of thumb is still: a little bigger than your RAM. 100 MB or so. In this case therefore: 8,1 GB. 

Reason: suspend-to-disk... :)

---

### Post by Deedlebag on 2012-12-20
Thank you all for the help! 
From what I've gathered, I should defrag before installing.

But what I am confused about is if I should or should not use the installer?
Would it be better if I put Ubuntu on a Live-CD?

---

### Post by cybrsaylr on 2012-12-20
Always defrag first. This pushes Windows files towards the front of your HDD freeing up clear space on the back of the drive for Ubuntu. Otherwise there is a chance your Windows OS may be damaged.

A Live-CD serves two functions.
1. It allows you to give Ubuntu a test run on your PC to see how it runs. 
2. Then is serves as the install disc for Ubuntu.

---

### Post by Pjotr123 on 2012-12-20
Prior defrag shouldn't be necessary before letting Ubiquity resize Windows. 

Run this command:
```
man ntfsresize
```

Key quote from the output:
> All  NTFS versions are supported, used by 32-bit and 64-bit Win&#8208;
dows.  **Defragmentation is NOT required prior to  resizing**  because  the program   can  relocate  any  data  if  needed,  without  risking  data
integrity.

However, just to be on the safe side, I always let Windows defrag itself first, too... :p

---

### Post by sudodus on 2012-12-20
> **Deedlebag said:**
> Thank you all for the help! 
From what I've gathered, I should defrag before installing.

But what I am confused about is if I should or should not use the installer?
Would it be better if I put Ubuntu on a Live-CD?

In a computer with at least 1 GB of memory, you can easily boot into a live session (from a live-CD/DVD/USB) and from there start the installer. So this is recommended in your case.

If you want good control of the partitioning, follow the advice to first backup, then defrag, then shrink the Windows partition.

Then boot from the live-CD/DVD/USB drive and start gparted (a GUI program) to create the other partitions from the space made available when you shrunk the Windows partition.

And finally, when you are satisfied with the partitions, start the installer. At the page about partioning, select

***"Something else"***

and use the partitions you have already created.

---

### Post by Herman on 2012-12-20
Windows's own partitioning tool can shrink Windows but it has the limitation of being unable to shrink Windows to less then half it's original size due to 'immovable files'.
If the Windows file system has already been resized smaller at some time in the past and Windows is already half the size it was originally installed in, Windows partitioner might not work at all.
Defragging is normally recommended before reszing with the Windows tool.

While defragging is generally a good thing to do and relatively harmless to the file system, it could be just a waste of time.  Obviously, in order to be able to resize a partition, it is implied that a partition editing tool must have an ability to move files if necessary, think about it. What is there was a partition editing tool invented that could not move files? Would it be useful? No, I  think not. So defragging first is just taking hours to double-do what the file system resizer should be able to do. Most partition editors worth using can move all the necessary files effortlessly in a few minutes.

It would be a much better use of a Windows user's time if they would run a file system check now and again in addition to the occasional defrag. For some reason Windows users tend to be afraid to run CHKDSK and the NT File systems do tend to get horribly corrupted after a while. Often, CHKDSK /R (the 'thorough' disk check), needs to be run several times and can take ages at first, then becomes faster with each run before it clears all the errors and starts to come up clean. 
Your computer repair shop does not want Windows users to know how to run CHKDSK /R.

Gnu/Linux partitioning tools have been perfectly capable of resizing NTFS partitions for years now, I think since about 2005 or 2006, back in the days of Ubuntu Breezy Badger or Dapper Drake.  With free and open source software It's possible to check bug reports and read wikis and web forums to read about  problems people may have experienced.  What we don't know is how many problems users might experience with proprietary tools because the details are not generally publicized.

---

