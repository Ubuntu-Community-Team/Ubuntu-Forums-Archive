---
title: "[SOLVED] Live CD building"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by Keith Hedger on 2007-07-17
Hi guys need some help!
I'm trying to build a custom live cd for PPC I've been folowing this guide:
[http://www.atworkonline.it/~bibe/ubu...tom-livecd.htm](http://www.atworkonline.it/~bibe/ubu...tom-livecd.htm)
but i'm stuck on the last bit, how to create the iso the instructions are:
sudo mkisofs \
-o ubuntu-new.iso \
-b isolinux/isolinux.bin \
-c isolinux/boot.cat \
-no-emul-boot \
-boot-load-size 4 \
-boot-info-table \
-r \
-V "Custom Ubuntu Live CD" \
-cache-inodes \
-J \
-l \
ubuntu-livecd
but this apears to be for a pc based cd, options -b and -c dont seem to apply to a PPC system.
So basicly I need to know how to construct the iso from the folder "ubuntu-livecd" and make it bootable
Any ideas or how-tos?

---

### Post by Keith Hedger on 2007-07-17
[http://ubuntuforums.org/showthread.php?t=502118](http://ubuntuforums.org/showthread.php?t=502118)

---

