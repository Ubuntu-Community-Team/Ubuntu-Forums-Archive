---
title: "need generic xorg,conf file"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by rfruth on 2006-10-27
Tried to upgrade from Dapper to Edgy, my mini tower has a X300 video card & I have no b/u of  my xorg.conf file, can someone (anyone) give me theirs cause X won't start, help me please I'm dead in the water right now (I have a bootable Dapper CD if need be)

---

### Post by magicfab on 2006-10-27
Look at the contents of the /etx/X11/ directory, you may have backups of the xorg.conf file you previously had.

If not, you can try changing the driver to "vesa" to trouble shoot, then make other changes.

using this command will re-run the configuration util for X:

sudo dpkg-recounfigure xserver-xorg

---

### Post by rfruth on 2006-10-27
Thanks I'm in business again !

---

