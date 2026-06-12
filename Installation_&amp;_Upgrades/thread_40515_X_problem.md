---
title: "X problem"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by nortoncillo on 2005-06-09
hi, mi box just cant show me gdm....

what i have..
Pentium III 600Mhz
128Mb Ram
HD 30 Gb
GeForce2 MX400 64Mb

well it cant show me gdm, X, or anything that means video... console work fine

i made a fresh install of ubuntu warthy, that didn't show me anything, then upgraded to hoary and nothing again....

help :???:  :???:

---

### Post by christooss on 2005-06-09
What about fresh install hoary not upgrade from Warty?

---

### Post by mingus on 2005-06-09
Also do a 
$lsmod | more
to make sure that the kernel modules for that video card are getting loaded.  The module names will have "nvidia" or "nforce" in them.

---

### Post by mingus on 2005-06-09
Few other quick thoughts:

Did the upgrade change the X-server?  Hoary uses the xorg version.

$apt-get remove xserver-xfree86
$apt-get install xserver-xorg

Or try having it reconfigure itself . . .

$sudo X -configure

or 

$sudo dpkg-reconfigure <your xserver name>

there is a lot on the forums on this topic . . . try searching

---

### Post by nortoncillo on 2005-06-09
[QUOTE=christooss]What about fresh install hoary not upgrade from Warty?[/QUOTE]
 well i dont have hoary disk, besides the upgrade from warty have been really good before (in other boxes)

anyway im downloading the hoary disk right now

---

### Post by nortoncillo on 2005-06-09
[QUOTE=mingus]Few other quick thoughts:

Did the upgrade change the X-server?  Hoary uses the xorg version.

$apt-get remove xserver-xfree86
$apt-get install xserver-xorg

Or try having it reconfigure itself . . .

$sudo X -configure

or 

$sudo dpkg-reconfigure <your xserver name>

there is a lot on the forums on this topic . . . try searching[/QUOTE]
 about the change from XFree86 to Xorg, it's installing Xorg actually..

let me see if it works now...

---

### Post by mingus on 2005-06-09
[QUOTE=nortoncillo]well i dont have hoary disk, besides the upgrade from warty have been really good before (in other boxes)[/QUOTE]

what's works in other boxes is only relevant if the internal devices and hw configuration are the same . . .

---

