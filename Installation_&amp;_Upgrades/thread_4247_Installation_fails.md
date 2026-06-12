---
title: "Installation fails"
date: 2004-11-13
forum: Installation &amp; Upgrades
---

### Post by tini on 2004-11-13
hello

i encounter each time the same error while installing ubuntu 4.1:

when installing the base-system, the installation always fails either installing debootstrap or initrd.
i'm  rather a newbie and don't know what i can do about it.

has anyone encountered the same problems with this hardware:

ASUS A7N8X Deluxe
AMX Atholn XP 2800+
Seagate ATA-133 60GB

thx

tini

---

### Post by tini on 2004-11-13
now something strange:

i plugged my 60 GB Harddisk into an older PC of mine (ASUS A7V133, AMD 1 GHz).
and all worked perfectly. the entire installation went abolutely smoothely.

now whats the problem between ubuntu and the ASUS A7N8X Deluxe?

thx in advance

---

### Post by d0gbert on 2004-11-13
I also had issues during installation.  If you press [F1] when the Ubuntu boot screen appears, a short help menu will appear that lists a few boot variables if you are having problems.  It allowed me to solve my problem and may also help you.

d0gbert

---

### Post by tini on 2004-11-14
yeah, i know the possibility of boot-params.
but i have really no clue what to use.
i sea an option for seagate drives, but have no idea about the IRQs and other stuff to provide with this param.
which boot params did you use?

---

### Post by d0gbert on 2004-11-15
My problem was that the CD-ROM would spin up for a few seconds and then stop.  So the system would hang at whatever point I was at in the installation.  Typing the following at the boot prompt seemed to fix this issue:

linux noapic nolapic

hope it works for you!

d0gbert

---

### Post by d0gbert on 2004-11-15
...BTW, I also have a seagate drive.

---

