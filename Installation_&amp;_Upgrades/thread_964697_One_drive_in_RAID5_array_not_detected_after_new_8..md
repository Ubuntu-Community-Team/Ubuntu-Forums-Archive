---
title: "One drive in RAID5 array not detected after new 8.10 install!"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by zorblart on 2008-10-31
Uh oh,

Hello all...

I took the opportunity to replace my failing 8.04 drive with a fresh 500GB drive and install 8.10 on it this evening.

On my old install, i had a 4 drive RAID5 (4x1TB) array. For some insane reason now, only three of the drives are being picked up by the OS.

I can confirm that the usual sata controller scan during POST picks up all four drives.

I have not tried to do an mdadm --assemble --scan, out of sheer fear.

Can anyone help shed any light on this? So scared ;\
:(
Cheers,

---

### Post by zorblart on 2008-10-31
An update to the above after further troubleshooting.

The weird thing is that the drive doesn't show up in an fdisk -l, or if i grep through dmesg...
its as though ubuntu isn't seeing the drive at all..

Have plugged in the disk containing my old install (8.04), and it detects and assembles the array fine. All this without a modified mdadm.conf (uses persistent superblock i believe – when checking with mdadm --detail)

So i'm thinking perhaps its a problem with the new kernel and its Promise SATA300 TX4 driver... But hell – things are getting into murky territory.

---

### Post by zorblart on 2008-10-31
Further update:

Attempted to assemble the array with the ridiculous idea that the disk was playing hide-and-seek, and succeeded only in assembling it in a degraded state (i.e. it booted the 'missing' disk out of the array). 

To resolve this, I had to boot off my 8.04 drive and re-add the disk - waiting ~8 hours for a resync. Bleh.

At a bit of a loss. Going to reinstall 8.10 without the controller card plugged in, and will attach it after i have done all updates etc.

Side note: in current 8.10 install, the 3/4 disks show up first in an fdisk -l - i.e. before the drives attached to the mainboard.

Is this the correct forum for the posting of this sort of issue? Mods: if you could move the thread if necessary. 

Cheers

---

