---
title: "Dual boot with a floppy"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by Raf Rzedowski on 2006-09-04
Salutations!

I'm using Windows XP now. I have two NTFS partitions on my hard disc. On one of them, I plan to install Linux while keeping Windows on the other. However, I do not want to mess with the existing MBR. I want Linux to start with a floppy boot disc. For Windows it must be business as usual. Can somebody advise me on the simplest procedure I should follow?

Thank  you!

Raf

---

### Post by john_spiral on 2006-09-04
backup everything on ntfs drives
boot from ubuntu CD
run installer
choose destination partiton
install grub to /dev/fd0

me thinks

John

---

### Post by confused57 on 2006-09-04
> **john_spiral said:**
> backup everything on ntfs drives
boot from ubuntu CD
run installer
choose destination partiton
install grub to /dev/fd0

me thinks

John

You can do this with the Dapper alternate cd, but the desktop live cd automatically installs grub to the mbr.

---

