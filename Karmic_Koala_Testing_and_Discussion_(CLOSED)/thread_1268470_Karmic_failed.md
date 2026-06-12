---
title: "Karmic failed"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by G2P on 2009-09-17
Hello! 
I was using Ubuntu Jaunty. Everything was well, till i decided to upgrade to Karmic. I have done that with "update manager -d". In grub, it's added new kernels 2.6.31-10 and 2.6.28-15. When i choose 2.6.31-10 it's starts booting and then black screen. When i choose 2.6.28-15, it's booting till system terminal, after typing "startx" it's starting to load xorg and then returns to system terminal with the error "(EE) intel(0): Failed to set tiling on front buffer: rejected by kernel". Is there any way to downgrade back to Jaunty or do something with Karmic? :(

P.S. I'm using HP Compaq nx7400 laptop.

---

### Post by QIII on 2009-09-17
Karmic is an Alpha, not even a Beta, and is not recommended for production machines.

Alas.

I hope you backed up your important files.

I have been recommending over and over that people wait, and when it does come out to do a fresh install.  A lot has changed -- particularly the fact that Karmic uses GRUB2 as a clean install and doing an update leaves you in a "legacy" mode with GRUB and menu.lst.  Getting GRUB2 installed and everything else in order is really just a matter of a few commands in the terminal, but why hassle with it?

If you backed up, I'd recommend reinstalling Jaunty and keeping your britches on for about 5 weeks.

---

### Post by running_rabbit07 on 2009-09-17
At bootup can you choose the restore kernel for Karmic? If so, do it. If not, find your Jaunty or any other LiveCD and see if you can boot the LiveCD and back up needed files to an external device. If the restore kernel does not work, then you will have to reinstall Jaunty.

---

### Post by G2P on 2009-09-17
Thanks for your replies! Seems that the reinstall is the only way :(
So, i'm doing it right now!

---

### Post by dizzie on 2009-09-17
I got the "cannot connect to dbus error" more fun than a failing grub (which works for me btw) But oh well :-))

---

