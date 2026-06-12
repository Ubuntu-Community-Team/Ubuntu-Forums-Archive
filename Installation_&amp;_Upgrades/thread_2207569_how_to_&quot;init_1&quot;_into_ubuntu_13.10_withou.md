---
title: "how to &quot;init 1&quot; into ubuntu 13.10 without grub installed"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by giambolo on 2014-02-24
I have to "init 1" into Ubuntu 13.10. I have no grub installed and don't know which key combinations let me interrupt the loading process, so that I can Init 1.

I have already tried esc , shift left, shift right, both shift.

Does anyone know? 

Thanks in advance

Elio

---

### Post by Mark Phelps on 2014-02-24
You can not launch Ubuntu without a Linux boot loader.  You will need to install GRUB.

---

### Post by giambolo on 2014-02-24
Thanks Phelps for your answer, but. I should add that Ubuntu 13.10, is starting in a Fusion VMware session. As soon as I start the VMware session, just after the BIOS, I cannot hook into grub, or whatever launcher it has associated. As stated before, I've already tried some key combinations without success.
How do you intercept the launcher to say "init 1" ?
Thanks again, Elio

---

### Post by giambolo on 2014-02-24
Got rid of the problem this way.
At boot, after BIOS, keep pressing shift, repeteadly.
At the GRUB  menu, press 'e' on the line of the usual boot. There find the linux line and change the "root=/dev/WHATEVER ro" to "root=/dev/WHATEVER rw". Let only "init=/bin/bash"  follows the previous part.
Press F10 to boot.

---

### Post by Mark Phelps on 2014-02-24
Glad to see you got it sorted.

---

