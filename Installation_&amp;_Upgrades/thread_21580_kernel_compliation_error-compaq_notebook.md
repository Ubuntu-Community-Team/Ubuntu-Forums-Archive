---
title: "kernel compliation error-compaq notebook"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by andyk on 2005-03-22
i'm running stock hoary-preview on a comapq 2108us notebook.  i have had no problems at all.  but dinking around in syanaptic i found gtkpod.  hoary had no problems with the pcmcia firewire card, but wouldn't detect the ipod.  some lookin into the problem told me that ipod should come up as dev/sbp.  i found that i would have to go into kernel config and turn on sbp-2 support.  i'm runninga clean kernel, never touched it.  heres how i did it and the error during recompile:

download 2.6.10-4 source, headers,  build essentials etc.

d/l, unpack, then cd /usr/local/src/linux-source

make oldconfig (to try and keep old settings.  heard this is a good idea)

make menuconfg (optioned sbp-2 support)

save and exit

make-kpkg clean

make-kpkg kernel_image

after about an eternity of compiling it returned this error in the USB section:

ISD200_get iquiry data
  undefined reference to ISD200  

got [stamp] error1 leaving directory.

anybody got ideas ?

andy

---

