---
title: "can't reinstall --&gt; USB boots to Grub Rescue Prompt"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by TMGeorge on 2013-01-27
Hi,

The 1st time I could install Ubuntu Desktop 12.04.1 from USB Stick with no problem. Later I upgraded the packages and ran into a problem which I couldn't fix (Stopping System V runlevel compatibility). Because of this I couldn't log on to UI either. So I thought I install again. I switched to terminal mode and used fdisk to delete all the partitions. If I now boot again the grub rescue mode prompt comes up and I don't know why.

If I remove the hard disk the USB Stick boots normally. But with the hard disc installe Grub Rescue comes up.

I played around with boot order in setup but with no success. I am even not sure if grub rescue comes from usb stick or from the hard disc. I have no idea where it would come from the later.

BTW I used "Linux Live USB Creator". I even created a new partition with exFat under Windows7. But no change.


in Grub Rescue:

"ls" results in (hd0) (hd0,msdos1) (hd1) (hd1,msdos1)

a ls (hd0,msdos1) or ls (hd1,msdos1) shows "unknown filesystem"

It doesn't make sense to me and I have no idea about what to do next.


any ideas?



update: luckily I decided to try the build in SD card reader. The SD was listed as harddisk and I put it on 1st place. I currently install from the SD. So it seems for some reason the machine ignored the boot order (Removeable, CDROM, HardDisk) and booted from the harddisk. Looks like grub is still somewhere in the MBR.

---

