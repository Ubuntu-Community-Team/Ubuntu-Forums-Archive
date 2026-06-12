---
title: "CD Install Errors: Invalid Boot Diskette?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by abbot on 2006-06-03
I'm having all kinds of problems with this Dapper Install.  I was running Breezy on a 10gb HD in this box previously with no problems.  I have everything I need backed up and am trying to just do a clean wipe & install on a different 40gb HD and ditch the 10gb.  I used the dapper desktop disk to install and it kept freezing half way through the process of removing the language packs and giving kernel errors when I'd restart it afterwards.  I tried on the old 10gb HD (hda) instead and it's doing the same thing.  

I then downloaded & tried to install with the text install Dapper disc on the 40gb HD (hde) and its getting through the install but when I remove the CD & reboot afterward it says "Invalid Boot Diskette: Insert boot diskette into A:" and I don't have any disks in my floppy drive to begin with, or know why its even bringing up a drive A: (isn't that a windows term for a floppy drive?).  My boot order in BIOS is #1 CD ROM #2 IDE HDD and that's it.  I think this 40gb drive had Windows on it before, but I tried both assisted & manual partitioning during my install attempts and completely deleting those partitions.

Please help somebody!  I've been patiently awaiting the final Dapper release before I installed it so everything would be working, but its obviously not for me.

Thanks In Advance.

---

### Post by abbot on 2006-06-03
Another weird thing that i noticed.  I'm trying to use the text based install cd and when I manually edit the partition table my only hard drive looks like this:

```
IDE3 master (hde) - 40.0GB WDC WD400BB-75AUA1
#1  primary  38.5GB  B  F  ext3          /
#5  logical  1.5GB      F  swap          swap
```

But then once the install is done I get the boot diskette in A: error.  When I try to install again and I get back into the partitioner it shows the current partitions as:

```
IDE3 master (hde) - 40.0GB WDC WD400BB-75AUA1
#1  primary  38.5GB  B  K  ext3          /media/hde1
#5  logical  1.5GB      F  swap          swap
```

Is it supposed to change the mount point to /media/hde1 like that?  I would think that it would still show as the root system there.  Is it thinking that this drive is a secondary drive rather than the one its supposed to be booting the OS from?

I know this isn't a problem with my install disks, so I'm at a total loss here.

---

