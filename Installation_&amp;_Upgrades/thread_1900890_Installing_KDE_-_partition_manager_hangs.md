---
title: "Installing KDE - partition manager hangs"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2011-12-27
Hi,


I'm trying to dual boot a pc with win 7 by installing kubuntu side by side with it,

The CD passes the checksum test, 

At first I had
 ERROR(5): Opening '/dev/sda1' as NTFS failed: Input/output error
 NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
 The usage of the /f parameter is very IMPORTANT! No modification was
 and will be made to NTFS by this software until it gets repaired.

So I did it,

Then I didn't see the usual options for partitioning while intalling, So I tried KDE partition manager from the CD, I got many errors of the type

ntfs_mst_post_read_fixup: magic: 0x00000000  size: 1024  usa_ofs: 0  usa_count: 65535: Invalid argument
Record 23 has no FILE magic (0x0) 

And KDE partition manager stopped at 25 percent and is still hanging there, What should I do?

---

### Post by Mariane on 2011-12-27
It was just a question of patience... The process returned with success after 2 hours and a half...

If this happens to you open a console and type
top

This will show you if the program is running or not

---

