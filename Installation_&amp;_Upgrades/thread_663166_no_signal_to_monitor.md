---
title: "no signal to monitor"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by NTesla on 2008-01-09
Hi,

I've recently installed ubuntu 7.10 on my desktop that also has vista on it (dual boot). Everything worked well until I installed a new video card (geforce 8400gs) on PCI-ex slot. The previous video card was an integrated one. There is no problem with vista, but when I choose Ubuntu at the booter, the monitor goes blank after that.. I hear the hard disk so it actually loads ubuntu, but no display. 

Can it be a driver issue? How should I install it (assuming it is supported). I am very new to Ubuntu.

Thanks for help.

---

### Post by or1on on 2008-01-09
when the screen goes blank try hitting ctrl+alt+f1 and it should bring u to a login screen type your user name and pw then type sudo dpkg-reconfigure xserver-xorg that will allow you to reconfigure your xserver choosing the vesa driver should give you video untill u can install the nvidia driver....ctrl+alt+f7 should bring u back to the gui if its not running after the reconfigure type startx at the f1 login screen

---

### Post by NTesla on 2008-01-09
Thanks a lot. That did work!

---

