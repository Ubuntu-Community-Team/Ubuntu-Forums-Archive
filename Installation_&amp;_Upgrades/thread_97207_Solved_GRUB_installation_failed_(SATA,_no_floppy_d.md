---
title: "Solved: GRUB installation failed (SATA, no floppy drive)"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by enodr on 2005-11-30
Hi,

Just to share a problem I just had installing Ubuntu:

Install process failed when trying to install GRUB (screen was just hanging). The problem was due to the fact that the floppy controller was disabled in the bios (I have no floppy of course). Enabling the floppy controller without any floppy drive solved the issue. I have a SATA drive.

I think that should be listed as a bug. The program failing was apt-install grub.

enodr

---

### Post by bwog on 2005-11-30
Interesting, I will try that tomorow.

Edit: It turned out that my problem was unrelated (solved it also).

---

