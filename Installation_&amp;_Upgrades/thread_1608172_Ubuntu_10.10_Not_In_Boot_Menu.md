---
title: "Ubuntu 10.10 Not In Boot Menu?"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by jazznaz on 2010-10-28
I've just installed Ubuntu 10.10 Netbook edition on a brand new Packard Bell Dot S2 netbook, and when the system rebooted after installation the netbook booted straight into Windows 7.

When I rebooted again and paid more attention to the boot process, there was no GRUB menu (like the one I get when booting up my desktop).

The Windows partition has been resized, but I can't seem to get to the new Ubuntu partition.

Any ideas?

---

### Post by Tirean on 2010-10-29
I have the same problem...in a way...
 
I installed Ubuntu 10.10 Desktop edition on an HP (Compaq Presario A900) laptop with a clean install of Windows Vista(Home Premium).
 
The CD installed, but when I boot, Vista starts up immediately, there is no boot menu. I think Grub is on the wrong partition? or maybe I even installed on the wrong drive. 
 
I apparently have two hard drives. one of them is Vista, the other is a recovery hdd. for some reason, the partitioner in the ubuntu installation wanted me to put it on that drive instead of the main one with vista on it. should I have reason to believe taht the ubuntu install has overwritten my recovery files? is there a way I can still choose to boot Ubuntu from that drive? or is there a way of deleting Ubuntu from that drive and putting it on the other one?

UPDATE:

I went into windows, as admin, and ran "compmgr.msc" and went into disk management and deleted the ubuntu partitions. booted ubuntu 10.10 from CD and then used the advanced partitioner. i set up the free space as a ext-3 partition of mount point "/" then another bit as a swap point. the ext-3 partition of mount point "/" is dev/sda2 in my case and thats where i told it to put GRUB. i installed, the CD installed fine... one thing to note here is that when i went to restart after the install, there was a huge repeating error message after the disc was automatically ejected...i turn off the computer and boot....STILL no boot menu, still goes right to vista...

DOUBLE UPDATE:

putting GRUB on /dev/sda and NOT on the same partition(/dev/sda2) as the install solved the problem. i now get a boot menu.

---

