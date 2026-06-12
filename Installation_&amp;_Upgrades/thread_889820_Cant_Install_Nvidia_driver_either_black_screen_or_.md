---
title: "Cant Install Nvidia driver either black screen or no loaded"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by extruct on 2008-08-14
Hello, well I installed a fresh Ubuntu 64bit and tried to install Nvidia driver using the Hardware Drivers and I got black screen after rebooting.
I reinstalled the system, tried again the same so I run xfix through recovery mode. It let me login to the system (screen wasn't black or frozen). I installed build-essential, got Nvidia driver from nvidia.com and followed the instructions in this thread
[http://ubuntuforums.org/showthread.php?t=880787&highlight=nvidia+restricted+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=nvidia+restricted+driver)
But my Nvidia x-server settings says "You do not appear using nvidia x driver. Please edit your x-configuration file (just run `nvidia-xconfig` as root) and restart the x-server." I did, the same problem.
I don't want to back to windows :( But seems like getting Nvidia working in Ubuntu is nightmare.
I'm using Ubuntu 8.04.1 Desktop AMD64 version (running on Pentium 4 3.0Ghz 64bit) and Inno3D Nvidia GeForce 6600 AGP 256mb.
I don't know what to do help me please.
[SIZE="1"]( gone reinstalling the system, again :( )[/SIZE]

---

### Post by extruct on 2008-08-14
Ok I followed this tutorial
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)
During driver installation I got warning:
"Unable to perform runtime configuration check for library "libGL.so.1" ('/usr/lib32/libGL.so.173.14.12'); assuming successful installation."

And after starting x/rebooting I got black screen. I used recovery mode and xfix and was able to login into the system. Trying execute system tools->nvidia x server settings gave the message about running nvidia-xconfig and I did. This gave me another message
"Data incomplete in file /etc/X11/xorg.conf Device section "Configured video device" must have a driver line".
After restarting x/rebooting the same lovely black screen appeared and system became frozen, and again I run xfix and here I am.
Don't Know what to do.
Help me please, I don't want windows :(:(

Thanks a lot!

A fresh update:
Trying to use envyng the same black screen.
This night is going to be looong...

---

### Post by extruct on 2008-08-14
Tried everything I found in this forum. Don't know what to do help me please :(

I've got Inno3D Nvidia Geforce 6600 AGP 256mb Video card
LG Flatron L1760TR LCD Monitor
If it helps somehow..

---

