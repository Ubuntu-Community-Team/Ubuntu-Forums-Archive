---
title: "Xubuntu partial upgrade: gmd not finding exec line for xfce"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by NachoMas on 2009-03-07
Hi all,
after a partial upgrade to test the brand new xfce 4.6 in my xubuntu, gdm does not find the exec line to start xfce and I need to start it manually from an safe-mode xterm. I guess it is a very simple line missing somewhere in any of the X11 /etc/ files, but I cannot find it. Any kind soul to point me on where to look for the reason gdm is not calling startxfce4 by itself?

Tx!
/Nacho

---

### Post by mr_pouit on 2009-03-07
Hi,

Check /usr/share/xsessions/xfce.desktop, which should contain a line such as "Exec=startxfce4" (you should probably reinstall the xfce4-utils package anyway).

---

### Post by NachoMas on 2009-03-08
I checked the line and it was there and then I reinstalled xfc4-utils, but still I get the same behavior... Any other hints?

Tx!
/Nacho

---

