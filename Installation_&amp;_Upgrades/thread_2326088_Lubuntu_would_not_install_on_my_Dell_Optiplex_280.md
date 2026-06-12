---
title: "Lubuntu would not install on my Dell Optiplex 280"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by andrew301 on 2016-05-28
Today I attempted for several hours and several install "cycles" to install Lubuntu on my Dell Optiplex 280 (2GB RAM, 500GB hard disk).
(I used "Universal USB Installer" to create an installation USB.)
I only got a "blue pre-natal screen" (as distinct from the Microsnot "Blue Screen of Death"), in that I could never get a login prompt.
There was a clue there was trouble when the "Try Lubunto without installing" option did not work either.

After giving up installing Lubuntu, I installed Fedora, which works without difficulty.

---

### Post by sudodus on 2016-05-28
Welcome to the Ubuntu Forums :-)

Have you got an ***Intel graphics chip***? There is a known issue with Lubuntu 16.04 LTS and some old Intel graphics chips, that can be fixed by installing the package

**xserver-xorg-video-intel**

You can get it directly if you install Lubuntu from a tarball with the [One Button Installer](https://help.ubuntu.com/community/OBI). I think the 32-bit version would be best for a Dell Optiplex 280.

-o-

If you have ***Radeon graphics*** there might be a problem with a driver for that chip/card. It might work better with Lubuntu 14.04.1 LTS than with 16.04 LTS. There are proprietary drivers for AMD/ATI/Radeon and 14.04.1 LTS (with the Trusty series of linux kernels 3.13).

---

