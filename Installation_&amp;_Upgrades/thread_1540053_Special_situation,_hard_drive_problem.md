---
title: "Special situation, hard drive problem"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by acolyte_to_jippity on 2010-07-27
Ok, so i have 9.40 (or 04, not sure) Jaunty Jackalope.  I installed it to my portable hard drive, and can boot off of it (as long as i idle in the bios a bit first to let the protable warm up)
 
Unfortunately, i'm only useing approx. 80 GB out of the 500 GB portable for the linux install, yet my windows vista (installed on laptop's internal HD) efuses to recognise the portable as formatted.
 
when i installed linux, i set the partitions as such:
/ : 20 GB ext3
/home : 40 GB ext3
:blank: :6 GB swap
 
and the rest i labled DoNotUse (while formatting it to fat32)
 
 
also, i cannot use GRUB (off of the portable) to boot to windows...but that's minor.  the fact that i've lost about 400GB of storage ability however, is a problem

---

### Post by -kg- on 2010-07-27
Hi again;

When you say you labeled it "DoNotUse," how do you mean?  Do you mean label, or did you use flags and mark it as "Hidden"?  If it's there and it's marked as "Hidden" (so the installer wouldn't be able to use or detect it) then you must un-hide it before Windows will detect it.

The rest is on the other thread.

What would be helpful is if you could post the output of:

```
sudo fdisk -l
```

...here on the thread.

---

### Post by dabl on 2010-07-27
Windows only looks at the first partition of a USB-connected storage device. So there's no easy fix for your present situation.

There are ways to install Linux on a second (or higher) partition of a USB storage device, and have it bootable (with Grub), while using the first partition for general storage.  For example: [http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

Based on that, it is theoretically possible that you could use Gparted to (a) shrink the partition on your portable drive, (b) make a new (smaller) partition in the freed up area and format it ext4, (c) use "dd" to copy over your existing Linux system, (d) reformat the first partition to NTFS or FAT32, and (e) fix the Grub entries to point to the Linux OS on the second partition.

Personally I'd just repartition and reinstall on the second partition.

---

### Post by acolyte_to_jippity on 2010-07-27
> **-kg- said:**
> Hi again;
 
When you say you labeled it "DoNotUse," how do you mean? Do you mean label, or did you use flags and mark it as "Hidden"? If it's there and it's marked as "Hidden" (so the installer wouldn't be able to use or detect it) then you must un-hide it before Windows will detect it.
 
The rest is on the other thread.
 
What would be helpful is if you could post the output of:
 
```
sudo fdisk -l
```
 
...here on the thread.
 
well, in the installer i marked the filesystem type fat32, and the other option to doNotUse. Ialso told the installer not to format that partition.
 
i'll run the fdisk when i get on after work. i just open up a terminal (command prompt) and type that in right?
 
> **dabl said:**
> Windows only looks at the first partition of a USB-connected storage device. So there's no easy fix for your present situation.
 
There are ways to install Linux on a second (or higher) partition of a USB storage device, and have it bootable (with Grub), while using the first partition for general storage. For example: [http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)
 
so basically, i just have to reformat and reinstall leaving the storage section as the first partition...and it should work?  will the BIOS lo0ok past the first partition when booting from the portable?

---

### Post by dabl on 2010-07-27
Not the BIOS -- it only needs to see the connected drive.  It is Grub that looks for the right partition & kernel to boot.

But, the *buntu Live CD uses Ubiquity for the installer -- Ubiquity might not see the partition.  You might need to use an Alternate Install CD.

Also, I saw you used 6G for swap.  I agree with making a swap partition -- comes in handy for "hibernate" or Suspend to Disk. But unless you have an unusual amount of memory being used at the moment you wish to hibernate, it's doubtful that you need more than 2G or 3G for swap.

---

### Post by acolyte_to_jippity on 2010-07-27
> **dabl said:**
> Not the BIOS -- it only needs to see the connected drive. It is Grub that looks for the right partition & kernel to boot.
 
But, the *buntu Live CD uses Ubiquity for the installer -- Ubiquity might not see the partition. You might need to use an Alternate Install CD.
 
Also, I saw you used 6G for swap. I agree with making a swap partition -- comes in handy for "hibernate" or Suspend to Disk. But unless you have an unusual amount of memory being used at the moment you wish to hibernate, it's doubtful that you need more than 2G or 3G for swap.
 
i have 4 GB RAM, and the book i'm working w/ says to have at least that much swap, preferably double...
 
plus i'm working w/ a 500GB drive lol.
 
i can spare the room

---

### Post by -kg- on 2010-07-28
I'm preparing to do a little experiment here.  I'm doing something I've been intending to do anyway.  I've had that huge FAT32 partition that I wanted to convert over to NTFS anyway, so I created the partition and am transferring all my files over to it.  I have around 1 1/2 hours left at this point.

Once I have done this, I'm going to delete the FA32 partition (first partition on the drive) and make an experimental installation of Ubuntu as the first partitions on the drive.  I find it hard to believe that:

> Windows only looks at the first partition of a USB-connected storage device.

If that were the case, then I would only have one partition available to Windows on my external.  I have two, and both are accessible.  The only thing I do not have is a non-Windows partition as the first partition.  I'm going to find out if that's the problem.

@dabi:  The link you provided was for a flash drive.  That might be true for a flash drive, but I wonder about a USB hard drive and whether it would be a different matter.

In any case, I'll find out.  If that's true, all I have to do is delete the Ubuntu partitions and I'll have my NTFS partitions available again.  All it can do is not work.

> i'll run the fdisk when i get on after work. i just open up a terminal (command prompt) and type that in right?

Right.  That should give you results similar to what I posted in the other thread.

---

### Post by dabl on 2010-07-28
@kg, regarding the ability of Windows to find available storage partitions, I have only tested USB flash drives.  It is possible that USB-connected hard drives work differently --- you can let us know.  :p

---

### Post by -kg- on 2010-07-28
OK, I have now "done the dirty deed." :p

I deleted my original 465GB FAT32 partition (first partition on the drive) and installed Lucid as first partition, with a swap partition taking the second spot.  Of course, I installed the GRUB bootloader in the MBR of the external drive.

I then booted into Vista, upon which a chkdsk on the NTFS partition on the external was performed.  Knowing what I know, I rebooted into Vista twice, then checked.  The NTFS partition was completely accessible with no problems.

I then rebooted into the Lucid installation on the external.  I have a boot selection menu during posting from which I can select which drive I want to boot to (main hard drive, secondary hard drive, optical drive, etc.).  This worked perfectly.  After entering my security password for the wireless, I had Internet access (and 270-somewhat updates, which I ignored...don't need *another* installation of Lucid!).

So everything was accessible, I booted successfully into the installation on the external drive, and I have a big smile on my face.  There are a couple of other considerations that I have come up with, though.

Of course, my TB drive was already partitioned in the first place.  I am in the habit (especially with something as large as my 1 TB external hard drive) of, when I don't anticipate absolutely needing a Primary partition for something (such as an installation of Windows, which pretty much requires a Primary partition), I will delete all partitions on the hard drive and create an Extended Partition that encompasses all the free space on the drive.

This means that every formatted partition on the drive is a Logical partition.  The thing about Linux is, it will install into and run from a Logical partition.  Windows will access logical partitions...it just won't run from one (actually, it will, but takes extra effort and procedures).

@ dabl:

> Windows only looks at the first partition of a USB-connected storage device.

...I have only tested USB flash drives.

This may be correct, except that perhaps it only looks at the first ***Primary partition*** on the USB storage device.  Since an Extended partition is a type of Primary partition, it may look at it, see it is an Extended partition, then go to the Partition Table contained in the root of the Extended partition, from where it's able to find whatever partitions with file types it can recognize.  As small as they are, there would be little reason for an Extended partition on even the largest of Flash drives.

Now another thought:

@ acolyte_to_jippity: It very possibly could be that your FAT32 partition wasn't formatted.  I see where you marked "Do Not Use" in the partitioning process.  That is where you tell the partitioner what file system to format it to.  The only way Ubuntu will "use" that partition is if you mark it with a mount point.

You should have selected "NTFS" or "FAT32" (if available...I wasn't looking for it) and it would have formatted it to your choice.  That you didn't means that you have the partition present, but it is unformatted (if you look at it with a partition editor, it will generally show as "RAW", which means unformatted.  At that point, it is only an entry in the partition table.

Nothing really to worry about there, though.  You can go in with GParted, select the partition, and format it to the desired file format.  It's there...it's just that it hasn't been formatted yet.

"sudo fdisk -l" would have told me that, but I deduced it anyway.  Now, if you're able to boot into it from GRUB on the external drive, you should pretty well know what's going on.

And one aside:

You said you're installing Jaunty...you *do know* that support for Jaunty 9.04 ends at the end of August, right?  I would strongly suggest you go ahead and install Lucid 10.04, or at least Karmic 9.10.  Lucid is an LTS (Long Term Support) distribution whose support cycle ends in April 2013, and Karmic (not LTS) support ends in April 2011.

---

### Post by dabl on 2010-07-29
> **-kg- said:**
> 

  I have a boot selection menu during posting from which I can select which drive I want to boot to (main hard drive, secondary hard drive, optical drive, etc.)

Assuming you mean something more elegant than a trip through the BIOS "boot sequence" settings, that's handy (but not very common ...).


> I am in the habit (especially with something as large as my 1 TB external hard drive) of, when I don't anticipate absolutely needing a Primary partition for something (such as an installation of Windows, which pretty much requires a Primary partition), I will delete all partitions on the hard drive and create an Extended Partition that encompasses all the free space on the drive.

I admit it -- I never thought of that!  Not a bad idea, actually.  :)

> 
@ dabl:


This may be correct, except that perhaps it only looks at the first ***Primary partition*** on the USB storage device.  Since an Extended partition is a type of Primary partition, it may look at it, see it is an Extended partition, then go to the Partition Table contained in the root of the Extended partition, from where it's able to find whatever partitions with file types it can recognize.  As small as they are, there would be little reason for an Extended partition on even the largest of Flash drives.



I'd forgotten most of whatever I used to know about the subject, but Google found this:  [http://www.msfn.org/board/topic/69211-a-multiple-partition-usb-stick-with-multi-boot-os/](http://www.msfn.org/board/topic/69211-a-multiple-partition-usb-stick-with-multi-boot-os/)

It's old, and refers to Win XP, but it appears the key is "removable" drive type, versus "fixed" drive type.  As you say, there are few reasons in the universe to make a USB stick a "fixed" drive.

Thanks for doing the experiment, and for the cool "They're ALL logical partitions" idea.  :)

---

