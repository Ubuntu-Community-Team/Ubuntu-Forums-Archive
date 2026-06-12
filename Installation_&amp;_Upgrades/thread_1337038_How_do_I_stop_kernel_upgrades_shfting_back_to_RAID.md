---
title: "How do I stop kernel upgrades shfting back to RAID array for boot?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Carr0t on 2009-11-25
A while ago I set up my work box to be an Ubuntu install (9.04). It has 2 hard drives, and I didn't want to have to reinstall it and set it up as I liked in the case of hard disk failure, so I set up software RAID 1 (mirrored).

Some time later I came to do big file copies across the network and found that after pulling about 500meg or so file copies and the like would grind to a crawl and the system would become unusable until the copy had completed (even the mouse pointer was very jerky and lagging by a good few seconds). This seemed to be as a result of the software RAID, so I got rid of it. Nuked out one disc, nuked the RAID info of the other, changed /boot/grub/menu.lst to have root on /dev/sda1 instead of /dev/md0, updated fstab etc etc. File copies were suddenly a lot happier.

All seems fine, except that whenever the Update Manager/apt has need to update menu.lst with a new kernel, it resets the root= part of each kernel line present in the file back to /dev/md0, as well as putting in a new kernel with root as /dev/md0. I can't find any other references to md0 left on the system, so i'm not sure why it's still convinced this is where root is for upgrades. Can someone tell me what I need to change so that I don't have to remember to go and edit menu.lst before the reboot every time I do a kernel update?

I've now done an upgrade to 9.10 by the way, still the same install.

---

### Post by oldfred on 2009-11-25
See the post by presence1960

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

