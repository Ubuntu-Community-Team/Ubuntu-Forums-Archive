---
title: "Installation Problem"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by bfr on 2007-01-02
When I select "Start or Install Ubuntu", I get:

hda:  ide_intr:  huh?  expected NULL handler on exit
Buffer I/O error on device hda, logical block 357566

I'm using an AMD Semperon CPU, a CD/DVD drive (where I have a CD-R that contains Ubuntu) and one Serial-ATA hard drive (plus the rest of the components, but I'm not sure of their details).

One thing to note though, is that the CD/DVD drive makes an odd sound, as if the CD-R disc inside it is bumping around its edges abnormally.

---

### Post by dorcssa on 2007-01-04
Maybe you burned the iso file wrong, did you md5 checksummed it? And with which speed did you burn it?

---

### Post by Pobega on 2007-01-04
Buffer I/O error usually means that the disc wasn't burned correctly. Reburn on a new disc and try to burn it at 4x speed, faster speed can sometimes mess up the installer.

---

