---
title: "hal.dll woes and more..."
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by misterpotter on 2006-08-06
so, I did i ubuntu install today and i got the general hal.dll error.  I figured that this could be easily remedied, but, alas windows recovery console refuses to run, claiming that i have no hard drive installed.

the cd refuses to even let me install windows over again as it cannot find a hard drive. (I know i can format and install, but i would prefer not to sacrifice my data)

so i decided to edit the boot.ini file manually.

The only problem with this is that I cannot get the drive to mount.  ntfsmount says that the partition is dirty - whatever that means, and I am unable to force it to mount.  moreover, i am unable to get the partition to mount at all.. though it does seem to mount itself to /tmp/disks-conf-sda3 for some reason, though I am unsure why.  perhaps someone has a better answer... regardles.. i am unable to write to the drive which makes updating boot.ini impossible. (Though i can still read the drive and its contents look fine.

I've installed ubuntu onto a sata drive which was previously (and still is - depending on how you look at it) installed with windows xp home.

if anyone has any ideas or help, i would greatly appreciate it...  i've spent the last 8 hours trying to fix this to no avail.

---

### Post by kebes on 2006-08-06
There are DOS boot disks that have NTFS support. You could download one of these and boot from floppy so that you can at least read the NTFS partition and make the small change you need to. You can probably also make a disk like this by booting from your Windows CD and then doing "format a:" or whatever. A Windows boot floppy should have the basic commands you need.

If none of these boot floppies can see the NTFS drive, then I guess you'll have to try something more exotic.


If you're at the point of formating the drive, you can at least try to make images of your current partitions, which you can restore quickly after the format and re-partitioning. Programs like Ghost will let you make images (version 7.0 supports NTFS). There is a linux program called partimage that makes images:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

You can install it to a Linux running from a LiveCD. The "System Rescue CD" is a Linux LiveCD that has partimage (and other useful rescue tools) built in:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Note that partimage has "experimental" support for NTFS... but it's worth a try if you're going to format the drive anyway.


If you're not willing to format the drive, then you'll need to get that NTFS support working somehow. If you read this thread:
[http://www.ubuntuforums.org/showthread.php?t=202904&highlight=hal.dll](http://www.ubuntuforums.org/showthread.php?t=202904&highlight=hal.dll)
The poster indicates that he was able to write to NTFS using a combination of FUSE and ntfsprogs. That might be worth trying.

---

### Post by kebes on 2006-08-06
These instructions:
[http://www.short-media.com/review.php?r=313](http://www.short-media.com/review.php?r=313)

explain how to resolve "hal.dll" type errors... Not sure if it's applicable to your current predicament.

---

