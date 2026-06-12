---
title: "[SOLVED] Envy get errno 39"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by bindkeeper on 2008-03-16
Hi 
when I tried to install drivers for my GeForce 8400 GS with Envy and I got
 [Errno 39] directory not empty in the Envy terminal

Any Ideas?

---

### Post by Pumalite on 2008-03-16
Did you try to install drivers with Envy before and it didn't work?

---

### Post by bindkeeper on 2008-03-16
before envy I tried the " NVIDIA-Linux-x86-169.12-pkg1.run" 
but I cannot understand how to exit X. So  I went to Envy

---

### Post by bindkeeper on 2008-03-16
I'm using Ubuntu 7.04

---

### Post by Pumalite on 2008-03-16
Try the NVIDIA driver again. In a Virtual Terminal:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linux-x86xxxxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx
Make sure you have build-essential first:
sudo apt-get install build-essential

---

