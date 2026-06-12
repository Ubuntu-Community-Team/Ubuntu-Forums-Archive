---
title: "Trouble with Grub &amp; 2xHDDs (IDE&amp;SATA)"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Evan S on 2007-07-12
Hi everyone, I'm a new user of Ubuntu and am really enjoying it.  

I currently have installed XP on my IDE and Ubuntu 7.04 on my SATA.  I will be only be using XP for a couple of little things, and Ubuntu will be my main OS.

Everything installed OK, and Grub even detected XP and automatically added an option on it's menu.  The problem is that when I select XP from the menu, I either get *error 12: Invalid device requested* or even *error 13: unknown file type *(or something to that effect).

I have spent hours reading threads and trying various fixes from previous experiences, but most of them seem to be working the other way (IDE Ubuntu, XP SATA).   I can get either to boot using the bios each time, but that's not really a practical solution forever.

Here's my setup:  (if there's more info that would help, let me know, and I can post it)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS



Anyone know the menu setup for this?

Thanks in advance...

---

### Post by luvr on 2007-07-12
> **Evan S said:**
> I can get either to boot using the bios each time
What do you do through BIOS then? Does it offer you the option to select which disk drive you want to boot from, and do you select either the S-ATA or the IDE disk?

If that's the case, then it looks to me like Windows XP finds itself on the *second* disk when you attempt to boot it from within your GRUB menu. Windows doesn't support this--it can boot only off the **first** hard disk.

Fortunately, GRUB lets you temporarily remap the disk order, to make Windows XP think it's on the *first* disk anyhow. Just edit your GRUB configuration file (i.e., **/boot/grub/menu.lst**--you will have to *"become root"* in order to do this), and add the following lines to the boot entry for Windows XP (just under the title line):
```
map (hd0) (hd1)
map (hd1) (hd0)
```

---

### Post by Evan S on 2007-07-20
Thank you luvr, that did the trick!

I'm now cruising along with Ubuntu, and I don't even have the need to boot into Windows very often at all!

:smile:

---

