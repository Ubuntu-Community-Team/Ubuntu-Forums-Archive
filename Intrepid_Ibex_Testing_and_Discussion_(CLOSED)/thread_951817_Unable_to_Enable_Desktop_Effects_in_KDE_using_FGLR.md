---
title: "Unable to Enable Desktop Effects in KDE using FGLRX"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fatejudger on 2008-10-18
Desktop effects in KDE using kwin work out of the box using the open source ati drivers. However, once fglrx is enabled, selecting "enable desktop effects" under system systems produces no result. Do the fglrx drivers have to be configured in a certain way to allow compositing, or is it something else?

---

### Post by JPorter on 2008-10-18
Which ATI card are you using?  Did you install FGLRX using the restricted drivers panel, or manually using the download from ATI?  The latest (Catalyst 8.10) is already in the Ubuntu repos and is enabled easily in the Hardware Drivers dialog.

Have you tried running the following, to make sure it's not a configuration issue?
[INDENT][FONT="Courier New"]sudo aticonfig --initial -f[/FONT][/INDENT]

---

### Post by inportb on 2008-10-18
The Canonical version of fglrx works with Xorg 7.4. The "official" AMD version does not. Which are you using?
(btw, you can still use XRender to get some compositing, but that doesn't solve the real problem.)

---

