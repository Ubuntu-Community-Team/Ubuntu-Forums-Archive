---
title: "Partitioning for Dual Boot"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by AndrewElmore on 2006-11-14
Hello,

I was in the middle of installing 6.06 (I dled it a while ago), and I came to the partitioning part.  I want to share my 250GB HD that already has XPP on it.  I also want to share a FAT32 partition for storing files.

I already have 2 partitions, XPP and a 3GB recovery partition.  I freed up 92GB, used 70 for shared partition, 20 for Ubuntu, and 2 for swap partition.

I must be doing something wrong somewhere.  This is what happens...

After selecting 20GB for Primary Partition and ext3 as the file system type, and 2GB for Primary Partition (I tied selecting extended as well) for Linux-Swap, I try to get the rest for the shared partition, which I select FAT32 and extended as my filesystem.  When I try to do the last step, it says I can NOT have any more than 4 primary partitions.  I'm sure I'm doing something wrong, this is something I just don't want to screw up, or figure out using trial and error.

I have tried looking up the answer on Ubuntu website and [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) , but neither give a full explanation for exactly what to do with creating partitions.  

I know this is a long post, but I hope this is enough info for someone to help me out.

---

### Post by rsambuca on 2006-11-14
You can only have four primary partitions on a hard drive.  If you have two already  used for XP, then you can make two more - not a problem for what you want to do.

If you must use one storage partition for both systems (FAT32), then that can be a separate partition, and all of the rest can be logical partitions.  The "/" root partition and the swap partition can be separate partitions within one logical partition.  You can actually have a bunch of partitions if you want.

By the way, 2GB for a swap sounds a bit like overkill to me.

---

### Post by AndrewElmore on 2006-11-16
Ok, so I think this is right, but I want to make sure before I do.

Here's a screenshot attached.  Please let me know if I have it right (with what I wrote beforehand) or wrong, and what I can do to fix it.

Thanks,
Andrew

---

### Post by rsambuca on 2006-11-17
It's a little hard to make things out from the screenshot (I can't make out the exact numbers clearly), but if what I am seeing is correct, you have (or will have):

1.  130GB ntfs (presumably your XP)
2.  58GB FAT32 for sharing files
3.  32GB extended partition composed of 950MB swap and 32GB ext3 for linux root
4.  4GB FAT32 recovery?

To make this work, I think you have to format the 950MB swap as "linuxswap" rather than ext3.  Other than that, things should work fine.

On a side note, there is a driver readily available for windows XP that allows it to read and write to ext2 and ext3 formatted drives.  If you use this, it would eliminate the need for the FAT32 partition, which you could instead format as ext3 and use it for your ubuntu '/home' directory and still access it from XP.  Quite handy.  The separate /home will allow you to reinstall ubuntu if you ever have to without worrying about your data and settings files.  Apparently ext3 is a better filing system that FAT32.

---

### Post by AndrewElmore on 2006-11-18
Thanks for all your help.  I changed the 950MB to linux-swap.  I decided to go for FAT32 in the end, as I have heard some horror stories about Linux and Windows coming in direct contact with eachother.  It's also kind of nice to seperate all my audio/video files onto a seperate partition (have a bit more structure, and hopefully speed up my XP partition when searching through My Doduments).

Anyway, after I did that, I came to the screen below (which makes me think I should've gone with ext3).  Everything looks fine, except it didn't automaticaaly recognize the 60GB FAT32 partition!  I know what to choose in the right column, but I'm not sure what to call it.  Or do I just leave it?  I think I'd want to reformat it (even though no info whould be on it).  Can I just call it /shared ?

Sorry if these are dumb questions, I really should know more about Linux (I guess that's why I'm trying to install it).

P.S. I hope this digicam pic (wireless wasn't working on Live CD so couldn't take screenshot) is easier to see.

---

### Post by rsambuca on 2006-11-18
Hey, not dumb questions at all.  That's what these forums are for.  I am by no means a linux expert either.  I just happen to have been doing this stuff a lot recently, so it is all fresh in my mind!

The 60GB FAT partition should definitely be mounted now if you want to use it.  It is easier to do now than wait until post-installation, although it can be done later with an edit to your fstab file.  The partition should show up when you click the drop down menu on the right side.  I assume it will be sda3, but you will be able to tell from the size.  

I would probably call it "/media/whatever_you_want_here", and it will be accessible from both XP and ubuntu.

You can change the names of those other partitions as well before you go further to make it easier for you.  eg. /media/windows, etc.

You are free to mount it if you wish, but I would personally just not mount the little 4G recovery partition as you probably don't want to mess around with those files anyways.

I started out very similar to you as far as my partitions go, then I added an old 6GB drive as slave to run ubuntu, then recently I bought a SATA drive strictly for linux.

I now have XP and Vista on my original IDE drive, and the new SATA drive for ubuntu (I have installed both the 32bit and 64bit versions).  

Good luck!

---

### Post by AndrewElmore on 2006-11-18
It worked, now I have a dual boot computer! Thanks.   Now all I have to figure out is getting my wireless usb adaptor to work with Ubuntu, but thats another forum.

You have Vista already?  You must have some handy friends.

---

### Post by rsambuca on 2006-11-18
It is RC2, build 5744.  Wife got it at a conference she was at in Seattle.  It expires at the end of May 2007, at which point it says it will become unusable.

I am using it right now, actually.  Some pretty neat stuff, but I definitely won't be rushing out to buy the final RTM version.  Lots of driver issues right now, and I doubt they will all be fixed by release time.

So for now, I'll play with Vista, but use XP and ubuntu for the bulk of my stuff.  There is a cool little game on Vista called inkball, though!

Good luck with the USB wireless adapter stuff.  I can't help ya there.

---

