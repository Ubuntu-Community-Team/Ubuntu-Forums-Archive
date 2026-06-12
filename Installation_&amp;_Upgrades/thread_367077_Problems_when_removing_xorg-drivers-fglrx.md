---
title: "Problems when removing xorg-drivers-fglrx"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by NightFox500 on 2007-02-21
Hey,

When i try:
sudo apt-get remove xorg-driver-fglrx then i get this as error message:

dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


What does this exactly mean and how can i solve this?

Sincerely,

NightFox

---

### Post by angryfirelord on 2007-02-21
Have you switched to the vesa driver before uninstalling? If not, then do a **sudo dpkg-reconfigure xserver-xorg** and switch from fglrx to vesa.

---

### Post by NightFox500 on 2007-02-22
Hey,

Ok, and what if i did that before installing?

Do i have to reinstall my complete pc?

Sincerely,

NightFox

---

