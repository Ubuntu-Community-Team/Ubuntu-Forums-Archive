---
title: "GRUB does not appear on kubuntu reinstall"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by t.achim on 2007-01-28
Hi,
I just recently reinstalled kubuntu, and the installation (seemingly) worked perfectly. However, when I try to boot, GRUB does not appear, and Windows boots.

My partition table (close enough):
/dev/hda1 ext3 /home
/dev/hda2 ext3 /
/dev/hda3 linux-swap swap

/dev/hdb1 windoze
/dev/hdb2 dell utility crap

I checked; when it installed grub it said it was installing to (hd0). If it did, the whole thing should work as I previously had GRUB installed to (hd0) and it worked.

Any suggestions?
Thanks, t.achim

---

### Post by shane2peru on 2007-01-28
I would go through the installation process one more time (it really couldn't hurt to try this since you haven't booted into Ubuntu, you haven't configured anything yet).  It really seems as though grub didn't install.  Especially if it boots straight to windows and doesn't even pause.  The other thing is that Windows is on hdb, and you may somehow be set to boot from that hdd.  That may be something to look at too in your bios.  

Shane

---

