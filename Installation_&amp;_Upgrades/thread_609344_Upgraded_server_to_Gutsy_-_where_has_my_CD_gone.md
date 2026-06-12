---
title: "Upgraded server to Gutsy - where has my CD gone?"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by andyni on 2007-11-10
just had a load of fun trying to get 7.10 to install from CD, but it won't mount the drive and installation fails. trying to get a small, light, 7.10 install, so after breaking the computer with the 7.10 CD, I decided to start with a 7.04 server install and upgrade it. now it's lost the CD drive.

/cdrom contains nothing.

mount /dev/hdb /cdrom fails with error "special device /dev/hdb does not exist"

found a post suggesting an edit to /etc/fstab, substituting "/dev/scd0" for "/dev/hdb ", and "auto" for "iso9660". this didn't work either.

how do I mount my CD in Gutsy?
how do I get it to mount if I put a disk in? I know this is probably easier in desktop edition, but I'm trying to work my way up from server towards a GUI to keep things light.

---

### Post by ofb on 2007-11-11
Actually, you may not be doing anything wrong. There's a handful of IDE related problems with 7.10. After spending last weekend going though threads and bug reports I decided the best thing to do is just wait for patches to come through rather than mess further with my settings.

For an example of my own fruitless thrashing around,
[http://ubuntuforums.org/showthread.php?t=599878](http://ubuntuforums.org/showthread.php?t=599878)

Towards the bottom there's a fix that might bring back your missing CD, but as you can see by reading it just shufted me into another problem, so I'm not recommending this sort of thing. Also you'd have to remember to remove it once patches do filter down.

---

