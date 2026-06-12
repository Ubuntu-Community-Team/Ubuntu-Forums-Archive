---
title: "Breezy and Hoary Dual Boot -- how to?"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by jimcooncat on 2005-10-05
I'd like to install Breezy on a new partition set without touching my Hoary install, as I have plenty of room. Anything I should watch out for? Grub issues? Can I share the swap partition?

---

### Post by SilentCacophony on 2005-10-05
Hi. Assuming you already have a free partition to install Breezy to, should be no problem. Ubuntu will generally recognise an existing swap partition automatically and assign it as swap, as well.

As for grub, there is one thing to watch out for. If you choose to do the usual *install to mbr* as you probably did on your previous install, then the grub stage 1 will thereafter point to the menu.lst on the new Ubuntu istallation, and it's from there that you'll want to make future changes, if necessary. Also, if you were to later format that partition, you'd orphan grub's mbr loader and have to do a rescue grub-install operation (I learned that the hard way ;) )

---

