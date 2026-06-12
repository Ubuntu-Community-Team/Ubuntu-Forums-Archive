---
title: "Failed to initialize the NVIDIA graphics device"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by wakin125 on 2011-01-15
hi i am kinda new to linux so i dont know how to fix this problem. I installed an update for my graphics card through the Additional Drivers in ubuntu 10.10 64 bit and when i restarted the computer, after ubuntu loaded it brought me to a black screen with white writing that asked me for username and password and then said that it failed to initialize the NVidia graphics device. is there a way to repair this or rollback the driver with some code? Please help asap. Thanks in advance.

---

### Post by dino99 on 2011-01-15
open a terminal, then run:

sudo rm /etc/X11/xorg.conf

reboot (power off)

if problem is still there, inside synaptic, remove/purge (right click) ALL the installed nvidia packages then reinstall : nvidia-current, nvidia-common, nvidia-settings

reboot again then check driver activation

---

### Post by wakin125 on 2011-01-15
Thanks bro. it worked

---

### Post by wakin125 on 2011-01-15
thanks bro. it worked

---

