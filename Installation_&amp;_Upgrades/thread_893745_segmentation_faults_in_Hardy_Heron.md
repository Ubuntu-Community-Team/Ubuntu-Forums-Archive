---
title: "segmentation faults in Hardy Heron"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by duffrecords on 2008-08-18
I was using Hardy Heron for a few days with no problem until I discovered I could not compile applications from source without segmentation faults occurring.  I ran seven passes of memtest86+ and found no memory errors.  So I booted the live CD to rule out a corrupted installation (and of course, I used md5sum and checked the CD for defects first).  Even with the live CD I am seeing segmentation faults in dmesg.  I tried reinstalling Hardy and it booted, albeit with segmentation faults.  Now, a day later, the boot process loads BusyBox and I can't start Gnome.  I didn't have this trouble with Feisty Fawn or Gutsy Gibbon.  Can anyone understand what's going wrong in these dmesg logs?

---

### Post by duffrecords on 2008-08-19
Ok, so this problem is definitely unrelated to Hardy Heron.  I went into the BIOS last night and noticed the advanced chipset configuration page was missing half of its options.  At that point the utility froze.

It would appear my shipment of fail has arrived.

---

### Post by duffrecords on 2008-08-21
I should be more careful with my use of the word "definitely."  I fixed my BIOS and tried the Hardy Heron live CD again.  The dmesg output shows errors when trying to mount each partition.  Then I booted my trusty ol' Debian Etch live CD...FLAWLESSLY.

This must be a problem with the new kernel.  Hardy has been an absolute nightmare on this machine.  The live CD (checked with md5sum) periodically froze, and I had to go through the installation process several times before it would complete without locking up.  Then I had to edit /etc/grub/menu.lst since libata now handles both IDE and SATA drives and it doesn't refer to the drives by the same names that GRUB uses (i.e. hd0 and hd1 are switched).  Then applications began crashing randomly, and eventually the system became unbootable with multiple segfaults.  I'm going to try Gutsy and see how that goes.

---

### Post by duffrecords on 2008-08-24
I've narrowed the problem down some more and I'm hoping someone could give me a little help at this point.  There are some issues with my Promise SATA controller, so I removed it for now and reinstalled Hardy.  The installation process did not freeze this time, although dmesg indicates there is trouble with my CD-RW drive on each subsequent boot:
```
[   24.588764] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   24.588773] ata2: failed to recover some devices, retrying in 5 secs
[   29.738669] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   29.738677] ata2: failed to recover some devices, retrying in 5 secs
[   34.888620] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   34.888628] ata2: failed to recover some devices, retrying in 5 secs
[   40.202279] ata2.00: ATAPI:         RW-523252         1.29 20031204, 1.29, max UDMA/33
[   40.373950] ata2.00: configured for UDMA/33
```
Aside from that, I couldn't find any problems.  Then I upgraded to UbuntuStudio using [these]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy") instructions.  At the very end of the upgrade, I saw this:
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-rt
Segmentation fault
Segmentation fault

```
I tried reinstalling linux-rt and linux-image-rt, but the same thing happened again.  I'm about to reboot and I'm pretty sure it's going to dump me into BusyBox again, rendering this machine unusable.  But at least now I know where the segmentation faults started happening.  It appears the same thing happened to [this user]("http://ubuntuforums.org/showthread.php?t=591746") when upgrading the kernel.  What's going on here?

---

### Post by duffrecords on 2008-08-24
Out of frustration, I tried reinstalling linux-image-rt a third time... and a fourth time.  Finally, update-initramfs completed without a segmentation fault and I was able to reboot successfully!  Seems like initramfs-tools is buggy.  Maybe yaird would be a better choice in the future.

---

### Post by duffrecords on 2009-06-14
This is an old post but I thought I should update it.  At some point I ended up adding some new hardware and I noticed the IDE cable for the CD-ROM was so tight it had come slightly unplugged.  This may have been responsible for the segmentation faults.

---

