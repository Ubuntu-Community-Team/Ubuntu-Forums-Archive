---
title: "&quot;Disk read error occured&quot; when trying to boot Vista from GRUB after RAID0 install"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by kipling100 on 2008-01-10
Hi, I just finished installing Ubuntu 7.10 on my RAID 0 set that had Vista on it.
First, I used the Vista disk manager to shrink my vista partition.
I then followed this fakeraid tutorial: [http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

Everything seemed to work, and I could boot to Ubuntu fine.
But, when trying to load Vista from GRUB, I get "a disk read error occurred"

Here is the output from fdisk:
> 

Disk /dev/mapper/isw_djdfgeebcg_Volume0: 500.1 GB, 500113342464 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb10db10d

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_djdfgeebcg_Volume0p1   *           1       50993   409600672+   7  HPFS/NTFS
/dev/mapper/isw_djdfgeebcg_Volume0p2           50994       60801    78782760    5  Extended
/dev/mapper/isw_djdfgeebcg_Volume0p5           50994       52210     9775521   83  Linux
/dev/mapper/isw_djdfgeebcg_Volume0p6           52211       52454     1959898+  83  Linux
/dev/mapper/isw_djdfgeebcg_Volume0p7           52455       60801    67047246   83  Linux




Here is the relevant portion of my menu.lst file:

> 
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1



I tried using my Vista DVD to repair, expecting it to overwrite GRUB but to save my Vista partition, but it didn't seem to do anything, as it would just go the GRUB menu again and I would get the same error when choosing to boot Vista.

I also mounted the ntfs partition using ntfs-3g, and I was able to view the Vista partition and everything is still there, including the Boot directory, so I'm pretty sure I didn't do anything to wipe out my Vista partition.  I just can't get it to load in GRUB...

Any help will be greatly appreciated!

Thanks in advance,

Dennis

---

### Post by kipling100 on 2008-01-10
UPDATE:

I think I fixed my problem by using the Vista DVD to boot into the command prompt:

bootrec /rebuildbcd
bootrec /fixboot
bootrec /mbr

Upon restart, it would boot directly to Vista.

Then I restarted with the Ubuntu 7.10 LiveCD, and rebuilt GRUB from the terminal per the same instructions from the tutorial above.

Kept my menu.lst the same as outlined above...and for some reason, I can now boot fine into Vista AND Ubuntu :)

Best,

Dennis

---

