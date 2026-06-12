---
title: "Can't restore GRUB2; can't mount Ubuntu partition."
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-04-29
I get the error - 'You must specify the filesystem type'.

I used the syntax on the GRUB2 page:
**mount /dev/sdb3 /mnt **
but it returns the above error.

Is there additional parameters to the code???

---

### Post by Moozillaaa on 2011-04-29
fsck /dev/sdb3:

group descriptors look bad ...
bad magic number in super-block ...
 ...
device or resource busy ...

Can I repair / restore bad disk sectors???

---

