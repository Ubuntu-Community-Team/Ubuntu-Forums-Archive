---
title: "Restore Ubuntu after WinXP reinstall"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by jht2k on 2005-08-28
Hi all,

I'm dual booting WinXP and Hoary on this Sony Vaio laptop. Recently, I reinstalled WinXP using the Vaio recovery disk, which clears the contents of drive C:, leaving the drive D: untouched (The 40GB hard disk is evenly spaced into two 20GB partitions - one of which has Ubuntu installed). Unfortunately, this had the effect of erasing GRUB from its home, meaning that the machine now boots directly into XP (even though Ubuntu, which could previously be selected from the GRUB menu, is still present on the second partition).

I've tried various methods of restoring GRUB from the support forums on this site and Google searches elsewhere, but all failed in some way or another. I'm now looking for further guidance on how to restore GRUB so that I can dual boot WinXP and Ubuntu. Here's the output of "fdisk -l" run under Knoppix:

```

knoppix@0[knoppix]$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        4864    19535040    f  W95 Ext'd (LBA)
/dev/hda3            4774        4864      730957+  83  Linux
/dev/hda5            2433        4772    18795987   83  Linux

```

It appears that Ubuntu installed in the Win extended partition /dev/hda2, but I can't seem to reinstall GRUB using grub-install, grub itself, or the Ubuntu installation disk (all using the instructions provided in the various sticky forum posts on this site).

Any suggestions gratefully appreciated.

Cheers,

Jon

---

### Post by Seth on 2005-08-28
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

