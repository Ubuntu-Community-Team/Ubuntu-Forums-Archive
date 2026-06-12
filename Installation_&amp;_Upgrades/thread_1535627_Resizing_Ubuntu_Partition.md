---
title: "Resizing Ubuntu Partition"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by artium on 2010-07-21
Hi,
 
I had Windows 7 installed on a 250 gb partition and decided to install the latest Ubuntu in dual boot. I had 250 bg unallocated space for this but I made a mistake and chose default settings during the installation (instead of making a partition out ofthis space and installing Ubuntu in it). The result is that Ubuntu took few gigs from Windows patition by creating two (one is for swap) logical partitions (I am not shure that this is the right term).
 
During my first session the disk space on the partition was over and now I can not even login to the system (some gnome error).
 
Can you sugest me what to do? I want to add the 250gb of free space to the Ubuntu partition. How can I do this? I tried with windows disk manager and with acronis partition expert 2003 but both were not willing to allow me resize.
 
 
 
Thank you.

---

### Post by artium on 2010-07-21
I had some progress. I was able to run gparted from live cd. A screen capture is attached.

What can be done to add the free space to sda5?

---

### Post by vikas.sood on 2010-07-21
> **artium said:**
> I had some progress. I was able to run gparted from live cd. A screen capture is attached.

What can be done to add the free space to sda5?

Is your windows still bootable?
I think you should remove your /dev/sda4 /dev/sda5 swap 
Once u get all the unallocated space use it to format
1. a partition to mount your / primary
2. a partition to mount /home. i prefer a separate mount point for /home personally. you dont have to do it necessarily.
3. swap

and carry on with a fresh install. Whats to do with the gnome i didnt understand that?

---

### Post by jroa on 2010-07-21
> **artium said:**
> I had some progress. I was able to run gparted from live cd. A screen capture is attached.

What can be done to add the free space to sda5?

I have only used Gparted on a few occasions, but I think you first need to get the unallocated space moved to sda4, then you can use it to resize sda5.

---

### Post by vikas.sood on 2010-07-21
> **jroa said:**
> I have only used Gparted on a few occasions, but I think you first need to get the unallocated space moved to sda4, then you can use it to resize sda5.

I dont think you can move unallocated 237GB space to your /dev/sda4. Once you will remove existing partitions you will get all of it as unallocated space. 

Or may be removing /dev/sda5, the unallocated 1 MB and linux-swap might help. Than probably you can join partitions if gparted lets you do that.

And why would you bother to move if you have already corrupted the partitions and is not getting booted??

---

### Post by Mark Phelps on 2010-07-21
Presuming you WANT to retain Win7 and continue to use it ... STOP using GParted immediately.

You will first need to shrink your Win7 OS partition to make room to expand your Extnded partition and the partitions inside of it.  Do NOT use GParted to do that.  Doing so runs the risk of corrupting Win7 and rendering it unbootable.

Instead, do the following before you do anything else: boot into Win7 and use the Backup function to create and burn a Win 7 Repair CD.  You will need this if you mess up the Win7 Boot Loader during your partitioning attempts.

Second, use the Win7 Disk Management disk management utility to shrink the Win7 OS partition to make room for expansion.

Third, after shrinkage, boot back into Win7 a couple of times to confirm it can reboot properly.  If it can't, boot from the Win7 Repair CD and run startup repair three times.  Then, boot into Win7 again to confirm it can boot properly.

Only now ... boot using a GParted LiveCD and use it to expand the Extended partition to the left to fill the unallocated free space.  Then, use it to expand and move the Ubuntu partition to the left as well.

But, and this is IMPORTANT, be patient!!  GParted is very s..l..o..w.  It will do the partitioning activities twice -- once for a test, and a second time for real.  Interrupting it or cancelling it while it is working is a surefire way to corrupt your Linux filesystem partitions.

---

### Post by kaelspencer on 2010-07-21
In order to grow sda5, you'll need to expand your extended partion sda4. Since the live CD uses the swap partition, you first need to tell it not to. You can tell it is using it by the keys next to the partition. Right click on the swap space in GParted and choose the option that tells the OS not to use it.

Next, add the unallocated space to sda4. Right click on sda4, choose Resize/Move.

Growing sda5 might be a little trickier. You've just added all of the free space after the swap partition. The way I see it, you have two options:
1) Delete the swap space, resize sda5, add a new swap space.
2) Move sda5 and swap to the end of the drive, then resize sda5 the other direction ("up" on gparted).

If you go with 1, you may have to edit your fstab so it knows what the new swap UUID is.

Before you mess with partitions, back your stuff up!

---

