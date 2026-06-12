---
title: "No sound in MacBook Pro 5,3 after Linux-Restricted-Modules departure"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emrys on 2009-10-03
After the departure of LRM yesterday(?) I've lost the sound. Before, I got it working by using the last alsa-driver using the following script (not mine, sorry I don't remember the origin):

#!/bin/bash
sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-2.6.31-11-generic linux-image-2.6.31-11-generic linux-restricted-modules-2.6.31-11-generic
wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install

Anyone else? Any ideas on how to do it now?

---

