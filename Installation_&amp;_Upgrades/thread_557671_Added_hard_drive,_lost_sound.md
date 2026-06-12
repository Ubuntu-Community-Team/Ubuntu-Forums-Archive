---
title: "Added hard drive, lost sound?"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Exakun on 2007-09-22
I added a new hard drive today and suddenly lost ability to "see" my Audigy 2 ZS Platinum in both Ubuntu 7.04 and Windows XP. My Audigy is not on the same power cable as the hard drive, so the hard drive shouldn't have affected it. I tried unplugging the hard drive just to make sure and I still have no sound or device detection. I can't reinstall the driver in windows because the device is not detected; I don't know how to try to force it to detect it in linux.

Any help would be really appreciated :(

---

### Post by Pumalite on 2007-09-22
Post:

lshw

---

### Post by Exakun on 2007-09-22
> **Pumalite said:**
> Post:

lshw
what does this mean, exactly?

---

### Post by Pumalite on 2007-09-22
Applications>Accessories>Terminal

---

### Post by Exakun on 2007-09-23
I did the lshw command and it says nothing in that huge list about my audigy :(

Any ideas?

---

### Post by Pumalite on 2007-09-23
Post the output.

---

### Post by shaniac on 2007-09-23
Hey, I too just added a hard drive and lost my sound AND one of my CPU cores.  Obviously, some kind of configuration data is being stored off of the main filesystem.  But where?  Assume everything shows up fine in *lhsw*.

---

### Post by Pumalite on 2007-09-23
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

