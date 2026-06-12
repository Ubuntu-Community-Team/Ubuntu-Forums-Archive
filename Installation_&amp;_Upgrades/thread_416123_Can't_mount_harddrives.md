---
title: "Can't mount harddrives?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by darundal on 2007-04-20
I just installed feisty (was running dapper before, but did a CLEAN INSTALL over it) and honestly just love feisty. However, I am having two problems. The first problem (and the major one) is that I can't mount the two other hard drives to the mount point I want them at (or at all, for that matter), save for temporarily with the use of the disk-mounter gnome panel applet. I tried to check the UUID of the two drives, however, it wouldn't open the file, so I couldn't even get to the UUIDs, so I couldn't attempt to manually mount them. Second, the disk-mounter gnome panel applet just disappeared from the gnome panel it was on. I have no idea how to fix these two problems. Anyone have any ideas?

---

### Post by darundal on 2007-04-21
Grr...new problem to boot; the trash can applet doesn't display the status of the trash and I can't empty the trash through right click, however, if I click on it and am in nautilus I can empty the trash no problem. Anyone know whats causing any of these problems?

---

### Post by Patrick K on 2007-04-21
You might find the UUID in Device Manager, now called Hardware Information. Select the volume you're interested in go to the advanced page. The UUID is at the bottom. Also in /dev/.udev/db there are more files concerning the file system. Locate the file with the last four characters that match the volumes you're looking for. If they have a UUID number it is in these files, too. 

However, I have some partitions that are not mounting properly and there are no UUID listed anywhere.


EDIT: I just found out how to get the UUID for all the devices on your system. In a term type "blkid" This give the UUID for all partitions.

---

### Post by darundal on 2007-04-21
Thanks! That gets me the UUIDs that I needed, and I can work it from there, now I just have the issue of the gnome panel applets. Anyone know what could be causing the errors I am having there?

---

