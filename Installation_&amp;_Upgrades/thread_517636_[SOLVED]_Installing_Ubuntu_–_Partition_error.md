---
title: "[SOLVED] Installing Ubuntu – Partition error"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by sfgeorge on 2007-08-04
Howdy,

I'm looking for some advice on what I'm doing wrong in my install of Ubuntu.  I'm doing something wrong in my partition setup.

I'm installing 7.04 64-bit Server edition on an AMD 64 machine.

After specifying my configuration for a manual partition setup, I receive this error

> [CENTER][COLOR="Red"][!!] Partition Disks[/COLOR][/CENTER]

SYSTEM~2_RESTO~1RP138CHANGE~1.1 is 1k, but it has 4 clusters (16k).

ERROR!!!

[CENTER]Ignore
Cancel[/CENTER]

My primary hd has 4 partitions already set up - Windoze, Knoppix, Gentoo, and a swap.  I'm trying to wipe Gentoo and mount Ubuntu's root in its place.  Here's what the Ubuntu partitioner shows for the primary drive before I reconfigure:

```
IDE1 master (hda)  -  160.0 GB ST3160023A
   #1 primary  115.3 GB   K ntfs       /media/hda1  (Windoze)
   #2 primary   21.0 GB B K reiserfs   /media/hda2  (Knoppix)
   #3 primary   21.0 GB   K reiserfs   /media/hda3  (Gentoo)
   #4 primary    2.7 GB   F swap       swap
```

Here are the settings that I specified for hda3 (Gentoo), which may have caused my error:

```
Partition settings:
Use as:                  ReiserFS journaling file system
Format the partition:    yes, format it
Mount point:             /
Mount options:           default
Label:                   none
Bootable flag:           off

Done setting up this partition
```

Any pointers on what I may be doing wrong would be appreciated.  Here are my system's specs, in case they may be helpful here:

AMD Athlon 3000+ 64
1 GB RAM
Primary HD: Barracuda 7200.7 ST3160023A 160 GB

Thank you very much,

Stephen

---

### Post by itismike on 2007-08-05
Hi sfgeorge,

Your error statement stood out to me because of the use of the broken words separated by a tilde (..RESTO~ for example) looked like a Windows path.  I Googled some portions of the error ("RP138 CHANGE") and found that that string is a path to the Windows System Restore directory(C:\System Volume Information\_restore{...}\RP138\change.log ).  

Sounds like the file is unhealthy.  Try running chkdsk from Windows to repair it, or if you don't have a need for the system restore files, delete them. ;-)

-Mike

---

### Post by sfgeorge on 2007-08-05
Thanks Mike, I think you may be onto something.

I was ignoring the fact that that it looked suspiciously like something to do with Windows System Restore, because I wasn't attempting to modify the Windows partition.  But I think that running a full chkdsk indeed is the best step forward.

I couldn't find a visible (i.e. healthy) RP138 folder in C:\System Volume Information\, but I found a reference to it in the fifo.log.  I'm going to run that chkdsk and see what the Windoze event viewer shows as results.

Thanks,

Stephen

---

### Post by sfgeorge on 2007-08-06
Mike, you were exactly right.  Thanks for your help!

After running chkdsk, I also noticed that my drive had Windows write-caching enabled (whoops).  No guess how that error got on there now. :)

Thanks again,

Stephen

---

