---
title: "How Do I Move Installation To A Smaller HDD?"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2011-12-14
I've got a large HDD which appears to be unreliable. How can I transfer my existing Ubuntu installation to my old, smaller HDD? (My used data does not exceed the old HDD.)

---

### Post by darkod on 2011-12-14
FS Archiver makes a backup copy of your partition using just the existing data and it can restore it to a smaller partition as long as the data can fit.

But it depends if you have a third disk to use as temporary medium for the backup file. I have never tried using this without creating the backup file.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by user2037 on 2011-12-20
Actually running Gparted on the smaller HDD then using Rsync with -a and -P worked quite well. It even allowed resuming so I could stop if I noticed unnecessary data being copied.

Although, I did have to boot a live CD, ch-root to the new installation, and run Grub-install.

---

