---
title: "Is it possible to install an up-to-date version of Ubuntu from an old disc?"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by torqueing on 2015-01-12
I have several old Ubuntu discs (and one 15.05). Is it possible to use them to boot up from them, update the OS and just change the software sources to 14.10 so it installs a current version instead of an old one?

I ask this because it seems like my disc burner is knackered

---

### Post by grahammechanical on 2015-01-12
Read through this thread. I am not explaining it twice within a day or two.

[http://ubuntuforums.org/showthread.php?t=2260306](http://ubuntuforums.org/showthread.php?t=2260306)

Regards.

---

### Post by mörgæs on 2015-01-12
Does your computer support booting from USB?

---

### Post by MAFoElffen on 2015-01-12
Yes, *many* ways, including how grahammechanical explained... 

With one note-- You cannot go backwards. (ie 15.04 to 14.10)

If any of them have grub2 above v1.99~rc1... you can also download an Installation ISO image directly to disk, and boot that ISO file directly from an edited Grub menu. That way you could boot from the 15.04 disk as hd1 (/dev/sdb)... and install to hd0 (/dev/sda).

---

