---
title: "Kubuntu 7.10 - Live CD works, Installed not"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by g0kb3rk on 2007-10-24
Actually there is nothing wrong with Kubuntu while working as a Live CD (and it is working perfect) but when I install it on my computer, this is where the problem starts, after the Grub nothing happens. Really nothing happens, it is just a black screen. I tried to install 3 times but every time same thing happened. I can't understand why it is working without a single as a Live CD but something happens when I install it.

---

### Post by Pumalite on 2007-10-24
Memory?. Graphics?.

---

### Post by g0kb3rk on 2007-10-24
Intel Centrino 1.8 GHz, with 512 MBs of Ram, Ati Radeon Mobility 9600, 8 GBs for Kubuntu and 300 MBs for swap. The main thing I can't get it is Kubuntu works on Live CD and installs without a problem but something happens after it. (I can't see a splash screen after installing the OS and restarting from the Live CD)

---

### Post by jaygo on 2007-10-26
hit CTRL + ALT + F1 and see if it shows you any errors. Also, you can try booting from one of the recovery modes in GRUB.

---

### Post by Pumalite on 2007-10-26
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

