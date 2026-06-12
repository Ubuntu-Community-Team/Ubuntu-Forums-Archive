---
title: "Installation Error Message at 83%"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by new2linux9 on 2005-12-05
Please note, this was origionally posted under "Dual booting.  Can't quite find the right answer".  However as I didn't receive a specific reply re. this error, I have re-posted.
 
I have now set up my dual boot system:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2432 19535008+ 7 HPFS/NTFS
/dev/hda2 2433 5958 28322595 83 Linux
/dev/hda3 5959 6043 682762+ 5 Extended
/dev/hda4 6044 7296 10064722+ 83 Linux
/dev/hda5 5959 6043 682731 82 Linux swap / Solaris

However although everything now looks okay during install at 83% I got the following error message:

[B][4295351.0640000] NTFS - fs error (device hda1):ntfs_ucstonls():Unicode name contains characters that cannot be converted to charcter set cp437.
[/B]
The install carried on and I am now using my computer with no apparent
problems.

Can anyone tell me what this means and what I should do about it?

Thank you

---

