---
title: "Intrepid CD Install - &quot;can't read boot cd&quot;"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by jfollmann on 2008-11-01
Trying to install Intrepid AMD64 on my desktop PC, from CD. After selecting "try," "install," or "check CD," the CD drive activity light flashes briefly, then stops. Several minutes later I get the "can't read from boot CD" error.

I know this sounds like a bad disc, however I have burned several copies, using two different machines. I have tried burning from three different ISO images to try to eliminate a single corrupted image, one from the Wayne State HTTP, one from MIT Media Lab HTTP, and one from the official torrent.

I have also tried booting from these CDs on two different machines, my laptop and my desktop - both of them failed (and yes, they are both 64-bit), so I'm reasonably sure the problem is not with the desktop's drive. Both machines are able to boot from my old Hardy Heron 64-bit CD just fine.

It appears that the AMD64 ISO in general is simply not bootable, but I don't see how that's possible (surely someone else would have posted about it by now?). What is going on here? Is anyone else having this problem?

It's possible the 32 bit version is ok, I have not tested it for two reasons - first, I don't want to install 32 bit. Second, I'm out of blank CDs (d'oh!).

I tried to use the flash drive installer, but discovered this machine doesn't have the ability to boot from a USB flash drive. Argh!

---

### Post by taurus on 2008-11-01
How fast did you burn the ISO image to a CD?  If you burnt it as a default, max speed, try burning it again but at a slower speed like 4X if you can.

Don't forget to check the integrity of the ISO image with checksum first before you do any burning.

---

### Post by jfollmann on 2008-11-01
> **taurus said:**
> How fast did you burn the ISO image to a CD?  If you burnt it as a default, max speed, try burning it again but at a slower speed like 4X if you can.

Initially, at max speed. But after the first failure, all burns were done at minimum allowed speed (9-something on one machine, 11-something on the other).

> **taurus said:**
> Don't forget to check the integrity of the ISO image with checksum first before you do any burning.

The MD5 matches what's found on [_this_]("http://releases.ubuntu.com/8.10/MD5SUMS") page.

---

