---
title: "How can I make XP my default OS in grub?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Trebuchet on 2007-04-25
Until I get a bit more experience with ubuntu 6.10, I'd prefer to have XP load by default when I restart. Is there a simple way (capable of being done by a newb)  to edit the bootloader to switch defaults?

---

### Post by jerrylamos on 2007-04-25
To juggle the default OS, do Applications Accessories Terminal.
Then do sudo gedit /boot/grub/menu.lst    (where the l is a lower case L)
It will want a password.
Browse down thru menu.lst and you'll see sets of lines for each bootable installation, with the key lines starting with "title" and running to the next blank line.
To get XP to be the default, move its lines as an intact set ahead of the Linux lines.
Proofread carefully before save.

If you mess up you get the privilege of re-installing Linux, unless you were thoughtful enough to save a copy of menu.lst as in 
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.save

It's pretty useful to know how to work with menu.lst so you can set default boot options, even some workarounds for problems.

Cheers, Jerry

---

### Post by Trebuchet on 2007-04-25
Thanks. I'll give that a try. If I blow it, at least that'll give me an excuse to install 7.04. :)

---

### Post by speeddemon8803 on 2007-04-25
:lolflag: nice excuse!

---

### Post by sailingboarder on 2007-04-25
if u know what number on the list windows is, then u can just change the default number to the number of xp

the numbering starts with 0, and includes the divider "other operating systems"

---

