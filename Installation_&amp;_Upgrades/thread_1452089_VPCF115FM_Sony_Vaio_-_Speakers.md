---
title: "VPCF115FM Sony Vaio - Speakers"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by gseaton on 2010-04-11
I trolled a few sites to get a solution to getting my VPCF115FM laptop speakers to work.

Here's the post:

"Just download the new alsa version to "youruser" folder frome here:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)

unzip it (either GUI or in terminal "tar jxvf alsa-driver-1.0.22.1.tar.bz2")

then open the terminal as admin and type those commands one at time:

cd alsa-driver-1.0.22.1
./configure --with-sequencer=yes && make
make install
./snddevices 

Just reboot and You're fine ;-)"
and the link:

[http://code.google.com/p/vaio-f11-linux/issues/detail?id=9](http://code.google.com/p/vaio-f11-linux/issues/detail?id=9)

The speakers aren't the best, but it saves having to burn up one of the USB ports for external speakers.

The original post was for other Sony laptops with the same audio chipset so YMMV. 

Good Ubuntu'ng.

---

### Post by rfbeck on 2010-05-07
Works great. Good looking out!

---

### Post by estres on 2010-05-13
I upgrade my kernel to Linux 2.6.32-22-generic and I did first the alsa thing above but it does not work until I downloaded the linux-backports-modules-alsa-lucid-generic package with the Synaptics Package Manager and this fixed the sound problem.

---

