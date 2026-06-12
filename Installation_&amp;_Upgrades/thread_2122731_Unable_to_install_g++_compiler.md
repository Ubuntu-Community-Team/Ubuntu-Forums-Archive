---
title: "Unable to install g++ compiler"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by its_bigB on 2013-03-06
Hi all,

I just run **sudo apt-get install g++** on terminal with the permission. But it's not working and kind of a messages listed (sorry i'm new to this and I don't know the exact terchnical term) and end up with something like this,

> 
gvfs-fuse is already the newest version.
xorg-docs-core is already the newest version.
libgnome-bluetooth8 is already the newest version.
xserver-xorg-video-nouveau-lts-quantal is already the newest version.
gir1.2-appindicator3-0.1 is already the newest version.
gstreamer0.10-alsa is already the newest version.
python-gconf is already the newest version.
gstreamer0.10-tools is already the newest version.
libgphoto2-port0 is already the newest version.
libglib2.0-0 is already the newest version.
gir1.2-peas-1.0 is already the newest version.
python-configglue is already the newest version.
gnome-session-bin is already the newest version.
libgomp1 is already the newest version.
usb-creator-gtk is already the newest version.
libgnome-desktop-3-2 is already the newest version.
software-properties-gtk is already the newest version.
libcupsimage2 is already the newest version.
growisofs is already the newest version.
gnome-power-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
its_bigb@its_bigb-VirtualBox:~$


Can anybody please comment on this.

---

### Post by schragge on 2013-03-06
Seems like *g++* is already installed.  What does *dpkg -s g++* show?

---

### Post by its_bigB on 2013-03-06
I found the issue, after spining my head around. Event I set the proxy from my browser, it's not reflect to the terminal somehow, I couldn't find the reason actually. However, I set the proxy from settings and after that it works.

Earlier it didn't work. I couldn't compile and source file.

---

