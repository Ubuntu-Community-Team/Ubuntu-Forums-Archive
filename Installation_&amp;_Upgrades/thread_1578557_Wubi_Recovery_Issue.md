---
title: "Wubi Recovery Issue"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by IlyZor on 2010-09-20
Ok, so I backed up all my Wubi-files + the boot.ini etc. I reinstalled my Windows OS, then put my Wubi-files on a new partition D: . Put the wubildr.mdr file + wubildr in the C: dir. Changed the boot.ini to C:\wubildr.mdr = "Ubuntu" . But when I select Ubuntu in the boot manager I get an error message (Couldn't load Windows, ntoskrnl corrupt - or something).

What do I do wrong? Can't I just install a new Wubi using the installer and then replace the disk-file by the old one?

---

### Post by bcbc on 2010-09-20
You can reinstall the same version of wubi and replace just the .disk files. 

However if you changed the partition that wubi was installed on you'll also have to do a manual edit of the grub entry the first time.

E.g. if they were on /dev/sda2 and they're now on /dev/sda3
then press 'e' on first entry,
change instances of (hd0,2) to (hd0,3) and /dev/sda2 to /dev/sda3 and then CTRL+X to boot.
Run "sudo update-grub" after booting to fix.

---

### Post by IlyZor on 2010-09-21
Thanks. That works.

---

