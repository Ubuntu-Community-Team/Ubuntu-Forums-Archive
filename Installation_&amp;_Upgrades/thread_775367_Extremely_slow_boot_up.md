---
title: "Extremely slow boot up"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by stuque on 2008-04-30
I justed upgraded to Hardy Heron, and re-starting takes about 15 minutes each time.

When I finally get to my desktop, windows are extremely slow, and the resolution/screen size is usually wrong. 

I've tried running dpkg-reconfigure -phigh xserver-xorg, but re-starting still takes about 15 minutes. 

Pressing ctrl-alt-backspace takes much less time, but the windows are still extremely slow to appear.

I am not sure what to try next to figure this out ... any ideas?

---

### Post by hermes0710 on 2008-04-30
Have you installed the restricted driver for your graphics card?

(System>Administration>Hardware drivers: check you graphic card in order to have the drivers DOWNLOADED automatically by the manager. You will then be asked to reboot)

---

### Post by park8b156 on 2008-04-30
or try grub edit and remove "ro splash" that worked for me in 7.10 I don't need it with 8.04 though. Search in Google for edit of 1st.menu ubuntu to get the comand if you need it I always for get it.

---

### Post by PmDematagoda on 2008-04-30
Does this happen when you start Ubuntu up afresh? If so, try booting Ubuntu up in Recovery Mode and post the places where it gets stuck(if it does).

---

### Post by stuque on 2008-04-30
Hermes, I do have the proper Nvidia graphics card installed. Graphical effects work just fine when the desktop finally appears.

I've since discovered that by choosing the 2.6.22-14 Linux kernel (instead of 2.6.24-16), booting appears to be normal. 

However, I can't figure out how to use the Nvidia drivers with 2.6.22-14 (I've tried envy and downloading the drivers from the Nvidia website, but both seem to fail for different reasons). So I am stuck with the nv driver for now.

---

### Post by hermes0710 on 2008-04-30
> **stuque said:**
> Hermes, I do have the proper Nvidia graphics card installed. Graphical effects work just fine when the desktop finally appears.

I've since discovered that by choosing the 2.6.22-14 Linux kernel (instead of 2.6.24-16), booting appears to be normal. 

However, I can't figure out how to use the Nvidia drivers with 2.6.22-14 (I've tried envy and downloading the drivers from the Nvidia website, but both seem to fail for different reasons). So I am stuck with the nv driver for now.

If you use the nv driver, 3d effects should not be enabled since 3d acceleration is disabled on this driver, thats why you have slow responses.

Post the problems you face while installing the latest drivers through envyng so we can have a better picture. (Note that if you install a driver in one kernel, you should NOT expect this driver to work on another kernel...at least smoothly)

---

