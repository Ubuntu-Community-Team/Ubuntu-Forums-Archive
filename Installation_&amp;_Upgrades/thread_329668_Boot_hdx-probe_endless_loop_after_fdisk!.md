---
title: "Boot hdx-probe endless loop after fdisk!"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-01-02
I have a *very* weird problem developed a couple hours ago, with Ubuntu 6.10.

During the boot process, when the drives are being probed, the kernel gets in an endless loop reading the 4 PATA IDE drives mounted on the Promise Fasttrak TX2000 FakeRAID controller.

The RAID device is configured as a 2x2 1+0 (Mirror + Stripe) and contains two NTFS partitions with Windows 2003 Server on them, and is the boot device for the system. The logical volume is 120GB on 4 x 60GB drives.

Ubuntu had been starting from the Desktop Live CD without too many problems until after I used ntfsresize and fdisk to shrink the 2nd NTFS partition to create space for Linux. I added 2 primary partitions (root and swap) to the partition table.

Since then it endlessly loops these errors, for all the RAID controller's drives (hde-hdh):
```
PDC202XX: Primary channel reset.
ide2: reset: success
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hde: task_in_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: unknown
end_request: I/O error, dev hde, sector 238276076
printk: 8 messages suppressed.
Buffer I/O error on device hde2, logical block 47279294
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hde: task_in_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: unknown
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
```

Previously it would report these errors for a few seconds during boot then 'recover' and continue booting.

Once booted I could then install dmraid and mount the volumes successfully.

Now I have to add the boot-time options "hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe" so Ubuntu can boot.

I thought it was a problem with the partition table written by fdisk but Windows has successfully booted from the partitions and CHKDSK reports everything is okay with the file systems.

Is there a way to probe for the hdx devices after the system has booted, from the shell?

I'm figuring if I can get the hde-hdh devices detected I can then investigate and fix the problem.

---

### Post by IntuitiveNipple on 2007-01-08
This is a bug of sorts with the IDE probe logic for partitions, which is exposed by software RAID 0 stripes across multiple disks.

My article on it is [Kernel Bug during IDE / hd probing](http://www.ubuntuforums.org/showthread.php?t=329995)

---

### Post by IntuitiveNipple on 2007-01-25
I've updated the bug report on this issue at [Disk Read Errors during boot-time probe of physical softRAID drives](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77734)

---

