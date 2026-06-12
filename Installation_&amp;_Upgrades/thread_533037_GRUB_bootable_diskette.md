---
title: "GRUB bootable diskette"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by vmsda on 2007-08-23
I have decided, for educational purposes, to give a go at David Horton's Pocket Linux Guide. For a start, we have to create a bootable diskette featuring GRUB and a kernel.I downloaded GRUB 0.95 and then followed the instructions from an xterm window:

cd /usr/src/grub-0.95
export CC="gcc -march=i686"
./configure --host=i686-pc-linux-gnu --without-curses
make

The last step, "make", fails with a return code of 2. Maybe I have to tweak the Makefile created by "configure", but if so, I have no idea where.

Thank you in advance for your help.

---

### Post by ddrichardson on 2007-08-24
Could you provide a link to the text you're following and the complete output of make (error code 2 doesn;t help - any fail produces it).

---

