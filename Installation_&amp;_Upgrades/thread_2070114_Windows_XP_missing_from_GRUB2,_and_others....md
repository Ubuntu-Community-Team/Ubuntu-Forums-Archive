---
title: "Windows XP missing from GRUB2, and others..."
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by mUNKYsTUFF on 2012-10-12
Hi all, first I'll post my fdisk:
```
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x036fe920

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf648f648

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   216074249   108037093+   7  HPFS/NTFS/exFAT
/dev/sdb2       216074250   596413124   190169437+   7  HPFS/NTFS/exFAT
/dev/sdb3       596413125   817917344   110752110    7  HPFS/NTFS/exFAT
/dev/sdb4       817917345   976768064    79425360    5  Extended
/dev/sdb5   *   817917408   970213544    76148068+  83  Linux
/dev/sdb6       970213608   976768064     3277228+  82  Linux swap / Solaris

Disk /dev/sdc: 267.4 GB, 267386880000 bytes
255 heads, 63 sectors/track, 32507 cylinders, total 522240000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce132

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   522224954   261112446    b  W95 FAT32

Disk /dev/mapper/cryptswap1: 3355 MB, 3355881984 bytes
255 heads, 63 sectors/track, 407 cylinders, total 6554457 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x959d71b5

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```Legend:
sda1 - Windows XP
sdb1 - broken XP, now empty
sdb5 - Ubuntu
sdc - a USB thumb drive

I just reformatted sda1 for another distro, when I needed to access windows. I rebooted, selected XP in grub, when it told me: "Error: No such device: (very long number)"
I then proceeded to panic, and rebooted into Ubuntu. After some messing around, I thought I had fixed the problem, so I rebooted again. This time the entry was simply not there.
Panicked again, and followed [this tutorial.]("http://linuxaria.com/howto/windows-entry-grub2-men?lang=en")
Terminal told me that it was not expecting a redirection when I ran update-grub, and didn't fix that.
I then thought to just use grub's command line to boot into windows, and that worked fine until windows started to boot. First I got BOOTMGR is missing, fixed that with XP setup disk. Now I have NTDLR is missing. That is where I am up to, and I am expecting more issues.

There are two things I want to get out of this:
1. To get a XP entry in GRUB2
2. And to get an entry for BackTrack (when I install it, (into sdb1))

The XP issues I can handle, it's the grub problems I have no clue about.

Thank you for any assistance, however futile.
Nathan

---

### Post by mUNKYsTUFF on 2012-10-12
Bump...?

---

### Post by darkod on 2012-10-12
You have no grub2 problems, you have XP issues and need to fix that first.

If sdb1 was your first windows installation, when you installed XP on sda1 it combines the boot files and adds them on sdb1 without telling you anything. That's how MS does it.

So by formatting sdb1 you effectively deleted your XP boot files it seems. Otherwise, grub2 is very good at locating other OSs when you run the sudo update-grub command. If it doesn't detect XP, it means the boot files are not there or correct.

I suggest using the XP cd to fix the sda1 boot process. It's better to discinnect sdb temporarily because windows is stupid and might try to mess with it too. Once you have XP booting happily with sda, connect sdb, boot ubuntu once and run the update-grub.

It should locate XP and create the menu entry.

I don't know the Backtrack install process but I suggest you investigate it and see if you can skip installing the bootloader during install. You might need to enter some advanced option or manual install. I would keep grub2 from ubuntu as main on the MBR of sdb. That's why I suggest seeing if you can skip BT bootloader installation.

It case you can't, you will have to restore grub2 from ubuntu back to sdb if you want to keep using it as main bootloader, and if BT overwrites it.

---

### Post by oldfred on 2012-10-12
+1 on Darko's suggestions.

Minor point. You cannot have two boot flags on one drive. So remove boot flag from sdb5. Grub does not use boot flag. Windows only boots, repairs booting or installs to a primary NTFS partition with the boot flag, so boot flag needs to be on a primary NTFS partition.

Because you have multiple drives, keep Windows & its boot loader on one drive and Ubuntu & its boot loader on another. And then set BIOS to boot grub on Ubuntu drive. Darko's suggestions will do that for you.

---

