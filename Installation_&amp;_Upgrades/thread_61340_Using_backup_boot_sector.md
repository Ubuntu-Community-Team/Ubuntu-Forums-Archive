---
title: "Using backup boot sector"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by ddubuntu on 2005-08-31
Hi,

I have a problem, I can't boot xp, I use grub and I have the following error:

Error 13: Invalid or unsupported executable format

However, I can mount this xp partition using the option errors=recovery in fstab, and I can read it.
Here are some lines of dmesg:

NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Recovery of primary boot sector failed: Read-only mount
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Using backup boot sector

The system seems to use a backup boot sector. I would like to know where this file is located and how I can restore it to fix the problem so I can boot xp.

Thanks a lot.

David.

---

### Post by nad on 2005-08-31
[http://support.microsoft.com/?kbid=153973](http://support.microsoft.com/?kbid=153973)

---

### Post by ddubuntu on 2005-08-31
Finally, I have fixed the problem:

- start xp installation cd
- select repair (R)
- in console mode, type fixboot c: (not fixmbr), answer yes to reinstall the boot sector
- the problem was solved, without having to reinstall xp or grub (but I don't guarantee anything for your system, backup your data).

PS: I run xp to use my conexant modem which doesn't work with linux, but that's another problem.

---

