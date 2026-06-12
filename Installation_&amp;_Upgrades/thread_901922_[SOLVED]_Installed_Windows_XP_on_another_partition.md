---
title: "[SOLVED] Installed Windows XP on another partition, Ubuntu doesn't boot"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by wiseguyxp on 2008-08-26
I just installed XP on my 2nd partition on my laptop.  Windows overwrote my MBR and I can't boot into Ubuntu anymore.  I used the Super Grub Disk and tried to restore my grub files to the mbr, but it didn't work.  I couldn't even use SGD to boot the Ubuntu partition without restoring the MBR.  I know my filesystem and grub are still intact on the first Ubuntu partition, since I used Ext2IFS to view the Ubuntu partition from Windows XP.  Is there something else I can try so Ubuntu will be bootable and intact?

---

### Post by damis648 on 2008-08-26
You are going to need this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by wiseguyxp on 2008-08-26
Thanks a lot, I'll try it out.  Seems like exactly what I was looking for.

---

### Post by Sef on 2008-08-26
Or check out [Super GRUB Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by wiseguyxp on 2008-08-27
> **wiseguyxp said:**
> I used the Super Grub Disk and tried to restore my grub files to the mbr, but it didn't work.  I couldn't even use SGD to boot the Ubuntu partition without restoring the MBR.
:)

I used what damis648 posted, and it worked perfectly.

---

