---
title: "Nvidia Driver (96) errors after Upgrade to Lucid"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2010-05-07
I want to use my video card, but after upgrade i got this message:


You do not appear to be using the NVIDIA X driver. Please edit  your X configuration file (just run `nvidia-xconfig`  as root), and restart  the X server.


any help, i've been searching around, and many people got this same problem

any help please, will be apreciaTED, after running from terminal I got this

CODE:
rey@rey-desktop:~$ sudo nvidia-xconfig
[sudo] password for rey: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



Please help!!!!

---

### Post by squaregoldfish on 2010-05-08
I had the same issue, and did the following:

Remove all packages pertaining to nVidia drivers.
Move the X11 configuration file (/etc/X11/xorg.conf) somewhere out of the way.
Restart the machine - this will give you a basic X setup with no nVidia drivers, but it will still work.
In the Gnome Control Center, select Hardware Drivers.
It should recommend the nVidia 96 drivers for you. Install them, and everything should be peachy.

Hope this helps,
Steve.

---

