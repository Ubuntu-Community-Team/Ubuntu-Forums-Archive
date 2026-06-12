---
title: "Partition Confusion and Dual Boot Set Up"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Kwag on 2007-02-20
Hi, 

I am pumped and excited about Ubuntu Linux and have been playing around with it via Live CD and virtualization using VMWare.  (Virtualization is too slow because I don't have enough memory)  I am about to take the next scary step of installing Ubuntu Edgy Eft alongside Windows XP Service Pack 2 on my Dell Dimension 4700, with 512 RAM, 2.8 processor speed, and a single physical hard disk with 80GB.

I have the Edgy Eft .iso burned on a CD (the Live CD that also lets you install), I have a GRUB Boot Loader Bootable CD, a GAG Boot Loader Bootable CD and a GParted Live CD.  (Hopefully, with all these things I can solve whatever problems arise or at least bet back into Windows if I mess things up).  

Recently, I looked at my partitions and now I am confused.  Since I haven't ever touched my partitions, I expected to see just one primary partition containing all my hard drive space on it for booting windows.  What I saw surprised me.  Can someone please explain what these partitions are for?  (Following is the output from using Partition Magic 8, which I WILL NOT use when installing Ubuntu, but I have also looked at my partitions with GParted and they were similar).

DELLUTILITY(*.)  FAT  47 MB  (7.3 used, 39.7 unused) Primary Partition

Local Disk (C:)    NTFS 72,841.6  MB  Primary Partition   (This is clearly the Windows Partition)

Local Disk(*.)     CP/M, Concurrent DOS, CTOS    3.4 MB, (all of it is used)  Primary Partition

(*) Unallocated  7.8 MB

What is the first and third partition all about?  Concerning the 4th entry, why did my computer ship with unallocated space?

Maybe this will help.  If I look at windows explorer I see "Removable Disk F:", (why it isn't E: I don't know).  However I do not have any USB mass storage device connected.  However, I have my printer connected, via USB, it has a built in card reader  (HP 7660), but I assume, and I hope, this does not have anything to do with my partitions?

Also, when I look at my hard disk partitions from within the Edgy Eft Live CD, they are always labeled as dev/sda instead of dev/hda.   Is this because my hard drive is a SATA drive?  Is that what the "s" stands for?  Is there anything about this that I should be concerned about? 

Thanks so much for helping!

Kwag

---

### Post by dcstar on 2007-02-20
> **Kwag said:**
> 
........
DELLUTILITY(*.)  FAT  47 MB  (7.3 used, 39.7 unused) Primary Partition

Local Disk (C:)    NTFS 72,841.6  MB  Primary Partition   (This is clearly the Windows Partition)

Local Disk(*.)     CP/M, Concurrent DOS, CTOS    3.4 MB, (all of it is used)  Primary Partition

(*) Unallocated  7.8 MB

What is the first and third partition all about?  Concerning the 4th entry, why did my computer ship with unallocated space?
........

The first partition are the Maintenance utilities available to you at boot time - don't touch this one!!!!

The third, don't know but it may be another system utility partition, better leave it as well.

The last bit is a leftover that wasn't used by the image that the manufacturer used to clone your PC - they may have had a 73.456 GB image and the batch of hard drives supplied had 73.464 GB capacity, so there was a little bit left over.

Your best bet is to resize your NTFS partition to give yourself ~20 GB space for a Ubuntu install (more if you can manage it).

And yes, the "s" is for a SATA drive.

---

### Post by rsambuca on 2007-02-20
Are those small partitions MB or GB's? 

I assume that your machine came with XP pre-installed and that you had to make these "recovery disks" right after you purchased your PC, right?  Presumeably you did not receive the XP installation disk with your system.

That tiny little partition is usually for some files to run special hot keys.  Do you have a special media key or something on your keyboard?

The other partition will be your recovery partition since you don't have the installation disk (I am guessing).  You can copy those files to CD's and delete that partition if that is the case.  You can actually view the files from the ubuntu live CD and see what is there.  I can't tell you for sure til you confirm the sizes - MB vs GB sizes.

---

### Post by Kwag on 2007-02-20
I don't have my computer with me, but I believe my figures are right (with respect to GB vs. MB) except for the mistake that dcstar picked up on but did not mention directly.  The unallocated space is 7.8 GB, not 7.8 MB.  

I actually do have my Windows XP CD shipped from Dell, along with all sorts of other Dell CDs for re-installing the software  (lucky me).  I bought the computer through a small business so that might have helped me get these CDs.

I don't think I have any special media keys on my keyboard.

Looks like so far my best bet, is to simply shrink my ntfs partition, and use the savings there combined with the 7.8 GB unallocated space to set up ubuntu.  Doing this I will have enough (and then some) to do the following:

/ ext3 10 GB
/home ext3 10 GB
linux-swap 1 GB

From the live CD, I will set up these partitions and install the GRUB Bootloader to my MBR, and hope for the best.  rsambuca, I am still nervous about removing that third partition.  It is really small, anyway, so it is probably not worth the risk.

---

### Post by rsambuca on 2007-02-20
Yeah, if you don't have to remove it, I wouldn't either.  Just keep in mind that you can only have four primary partitions on one drive, so you will have to make one extended partition containing the 3 partitions you want as logical partitions.  It will still work fine, though.

---

### Post by Kwag on 2007-02-20
I have a lot on my mind and I am tired.  It shouldn't be hard to tell people how much space each partition is taking up.  Don't know how I got the GB and MB mixed up, but I am back at my computer now and I double checked.  Anyway, here are the actual numbers

DELLUTILITY(*.) FAT 47 MB (7.3 MB used) Primary Partition

Local Disk (C :) NTFS 72.8 GB Primary Partition (about half of it is used) (This is clearly the Windows Partition)

Local Disk(*.) CP/M, Concurrent DOS, CTOS 3.4 GB, (all of it is used) Primary Partition

(*) Unallocated 7.8 MB

And I definitely have no media keys on my keyboard, and I have all my install disks (software and OS).  Why do I have my install disks and the 3.4 GB partition, I wonder?

I can still just work by resizing the ntfs partition, and yes I realize that I will need to make the fourth partition as an extended one to break everything out for Ubuntu, since I already have three primary partitions on my disk.

However, I am now somewhat disappointed that 3.4 GB are unavailable to me.  rsambuca, now that I have given you the correct, accurate information, do you have any advice for me about reclaiming this space and can you tell me what it is used for?  Or does anyone else have any idea about that 3.4 GB partition is doing and whether it is safe to delete it?

Thanks, sorry for the earlier confusion.

---

### Post by Kwag on 2007-02-20
A simple Google search provided the answer.   

The CP/M, Concurrent DOS, CTOS 3.4 GB partition is a full image (DELL proprietary format) of the hard disk when the computer shipped.  Apparently it is better than the restore cd, since it holds more data.  

Therefore, I guess I will leave that partition alone for now.  (Down the road maybe I'll free up the space, if needed, and back up the image, and remove the partition).  For now, though, I'll just use my own last available partition slot as an extended partition when I am ready to install Ubuntu (which will happen in the next week or so.

---

