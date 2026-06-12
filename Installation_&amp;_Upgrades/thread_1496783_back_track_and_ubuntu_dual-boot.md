---
title: "back track and ubuntu dual-boot"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by coolman98 on 2010-05-29
How would I install backtrack without ruining my ubuntu installation.
I would like to make my family's computer more secure but I still want
my ubuntu!

---

### Post by coolman98 on 2010-05-29
Come on...

---

### Post by davidmohammed on 2010-05-29
patience is a virtue...

suggest backup your PC and then give the backtrack installation a try...

---

### Post by coolman98 on 2010-05-29
thanks.

---

### Post by oldfred on 2010-05-29
If you want Ubuntu's grub to be in charge, when you install backtrack either install no boot loader or if you want to chainload install its grub to the partition you install backtrack into. Just do not install to the MBR or sda or hd0 or whatever it calls it.

---

