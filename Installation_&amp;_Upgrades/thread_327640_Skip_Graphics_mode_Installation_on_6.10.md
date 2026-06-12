---
title: "Skip Graphics mode Installation on 6.10"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by endymon on 2006-12-29
Hi,
I would like to install the 32bits version of Ubuntu 6.10 .

Unfortunately it ALWAYS tries to start the installer in graphics mode which fails (as I have a 8800 GTX video card). Even safe mode graphics mode does not work and bombs out with error.

Is there a way to force the installer in text mode ?
(I tried to DEBIAN_FRONTEND=text but somehow that still started in GUI mode).

I know what the issue is and can solve it by updaing xorg.conf (videocard = vesa) once the system is installed and get the proper drivers.

Whenever I use the alternate CD install it installs the 64 bits version and not 32 bits.

My initial impression is that it seems pretty shortsigthed to not have a text mode install or a fail safe graphics with the Vesa driver. But then again, I'm a complete Linux Noob :)

Thanks for any help !!

Endymon

---

### Post by meng on 2006-12-29
You need to download the Alternate CD install for 32-bit version, the Alternate CD 64bit is separate.

---

### Post by endymon on 2006-12-29
it's downloading now... thanks a lot :)

Somehow I had in my head that it was all on one CD. I realized now that the link opened different files to choose from.

Thanks a lot !!!!

---

