---
title: "Incorrect Partitioning"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Arminius_ on 2007-11-26
I recently gave windows the bird and installed Ubuntu 7.10. The only problem with this is that my All-In-One Lexmark won't work with Ubuntu. So, I'm forced to reinstall XP. The problem is that for some reason I have 5 partitions. I don't remember setting it up this way. Could I have some how installed Ubuntu twice?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3e3d3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6644    53367898+  83  Linux
/dev/sda2           19082       19457     3020220    5  Extended
/dev/sda3   *        6645       19081    99900202+  83  Linux
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris
/dev/sda6           19082       19269     1510047   82  Linux swap / Solaris

In Gparted sda1 is at mountpoint /media/disk-1 and sda3 is at /. 

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2007-11-27
What's done is done. You do have two ext3 partitions and tree swap ones. Delete the redundant, install Windows, and use super grub disk to restore grub.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by wolfen69 on 2007-11-27
i also had xp hanging around just for my Lexmark.if you really want to kick windows to the curb, buy an HP all-in-one, like the kind at Wal-Mart or other discount store. i paid only $69 for one. it was well worth it to give windows the boot.

---

### Post by Arminius_ on 2007-11-27
mikewhatever or anyone- Could any of those be a jump drive or cd that was in my drive? I can't check it right now, thats the only reason I ask.

Wolfen69- I would like to but need to watch the spending right now. Plus this Lexmark is pretty nice. I may in the future though. Thanks for the suggestion.

---

### Post by mikewhatever on 2007-11-28
> **Arminius_ said:**
> mikewhatever or anyone- Could any of those be a jump drive or cd that was in my drive? I can't check it right now, thats the only reason I ask.

No, they are all partitions of the sda hard disk.

---

### Post by Arminius_ on 2007-11-28
Yeah I checked that out. I got the partitioning done last night. The most recent version of Gparted Livecd wouldn't work, so I had to use 3.4-9. Everything looks good, so I guess I will reinstall XP tonight. Thanks for the input.


:guitar:

---

