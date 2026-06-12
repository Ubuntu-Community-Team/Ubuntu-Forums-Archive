---
title: "fixmbr/fixboot NOT working"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-06
I had a bad Ubuntu install, and my MBR got completely messed up.  I've tried using fixboot AND fixmbr, and neither works.  No matter what, fixmbr ALWAYS reports that my boot sector is non-standard or corrupt, even immediately after using fixmbr.  I can get into Windows using the grub super disk, is there anything I can do while running Windows to fix this?  My boot.ini file is still on the hard disk, and it *still* says what it did before any of this happened.  I deleted all Ubuntu/Linux stuff from my drives, so all that's there is Windows.  So, what should I do?

---

### Post by OneL on 2006-06-06
I've been there!  Try downloading Super Grub Disk at:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Go through the various menus until you get to boot Windows.  It will do that.  I've gotten somethings that look like error messages as the disk is booting, but it still worked.

It saved me twice.  The first time my MBR was restored but Windows would still not boot.  The solution to that was to delete the separate /boot partition I had made.

The second time, once I was back in Windows, I was able to use a disk image and restore the MBR using that.

Good luck.

---

### Post by catlett on 2006-06-06
Try the recovery console again but this time enter  ```
fdisk /mbr
```This is supposed to fix the mbr as well. It's worth a shot,  I can't tell you the outcome. Fixmbr worked every time for me so I don't know if this will work or not but it's the only thing I can think of. Good luck.

---

### Post by adrian15 on 2006-06-07
[QUOTE=catlett]Try the recovery console again but this time enter  ```
fdisk /mbr
```This is supposed to fix the mbr as well. It's worth a shot,  I can't tell you the outcome. Fixmbr worked every time for me so I don't know if this will work or not but it's the only thing I can think of. Good luck.[/QUOTE]

If this still does not work... Try with this command from a live cd:

dd if=/dev/zero of=/dev/hda count=446 bs=1

(Change hda to sda if your hard disk is scsi or if the live cd detects it as it)

This puts zeroes to your mbr boot code and I think that it boots the first OS that it finds on the hard disk OR NOT... but DO NOT WORRY.

If the command works ok... I think the fixmbr and fixboot and fixalike commands will not report that the mbr is not ok and they will work.

adrian15

---

### Post by adrian15 on 2006-09-18
> **Cable said:**
> I had a bad Ubuntu install, and my MBR got completely messed up.  I've tried using fixboot AND fixmbr, and neither works.  No matter what, fixmbr ALWAYS reports that my boot sector is non-standard or corrupt, even immediately after using fixmbr.  I can get into Windows using the grub super disk, is there anything I can do while running Windows to fix this?  My boot.ini file is still on the hard disk, and it *still* says what it did before any of this happened.  I deleted all Ubuntu/Linux stuff from my drives, so all that's there is Windows.  So, what should I do?

Download [last SGD version]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=94") and...
Boot From SGD cdrom.
Choose
Windows...
Fix Windows Boot.

And suposedly you're doing the same thing as a FIXMBR. Please tell me if it has worked for you.

adrian15

---

### Post by scrapile on 2007-01-13
just dealt with this same nightmare for several hours... problem actually is that fixmbr and
fixboot apparently don't set the windows partion as active.

use a 98 boot disk and then fdisk to set your orig windows partition as the active one.  Ubuntu sets it's own small partion as active and when you delete the 3 Ubuntu partitions there is no active partition.

---

