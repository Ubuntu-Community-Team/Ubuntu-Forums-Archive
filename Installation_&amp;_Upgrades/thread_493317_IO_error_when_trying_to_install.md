---
title: "I/O error when trying to install"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by shadowduke on 2007-07-05
i keep getting this cryptic I/O error when trying to install on my laptap, it gives me a string of numbers and an I/O error on device fd0, what does it mean and how can i fix it.

---

### Post by Pumalite on 2007-07-05
I'm sure you don't have a floppy in your laptop, but, anyway make sure that your CD is first in your BIOS boot list. Check your iso. Do Md5sum. Check CD for corruption before install. Burn at 1x if necessary.

---

### Post by shadowduke on 2007-07-06
> **Pumalite said:**
> I'm sure you don't have a floppy in your laptop, but, anyway make sure that your CD is first in your BIOS boot list. Check your iso. Do Md5sum. Check CD for corruption before install. Burn at 1x if necessary.

Did all that, still getting these errors:
[205.504000] Buffer I/O error on device fd0, logical block 0
[243.608000] Buffer I/O error on device fd0, logical block 0

---

### Post by Pumalite on 2007-07-06
/dev/fd0 is the device driver for a floppy. Has nothing to do in a laptop. Check your hardware for compatibility. See if you need to upgrade your BIOS.

---

### Post by shadowduke on 2007-07-07
I just upgraded my bios, its a dell cpi a 366Mhz laptop

---

### Post by Pumalite on 2007-07-07
How much memory do you have? If 256MB or less>'Alternate Xubuntu CD'.

---

### Post by alexisbatman on 2007-07-07
> **Pumalite said:**
> I'm sure you don't have a floppy in your laptop, but, anyway make sure that your CD is first in your BIOS boot list. Check your iso. Do Md5sum. Check CD for corruption before install. Burn at 1x if necessary.

I've change the bios and now get a different message about hdc:drive not ready for command

one error message replaced by another! any ideas?

---

### Post by Pumalite on 2007-07-07
Does a 'Live CD' boot in your box? If so; do: sudo fdisk -l (lower case L) How much memory do you have?

---

