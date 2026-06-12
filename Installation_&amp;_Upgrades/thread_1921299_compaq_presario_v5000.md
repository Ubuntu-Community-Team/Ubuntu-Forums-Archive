---
title: "compaq presario v5000"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by bepperk on 2012-02-06
hi everyone.
I tried everything to install the last version of ubuntu on an old Compaq Presario v5000.
these are the characteristic:
- AMD Turion™ 64 ML-32
- RAM: 512 MB DDR 333 MHz (2 x 256 MB)
- HD: 80 GB a 4200 rpm
- Video: ATI RADEON® XPRESS 200M IGP

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00626021](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00626021)

I tried these version:
11.10 i386 (also with alternate CD)
11.10 AMD (also with alternate CD)
11.04 i386 (only with alternate CD)

the installation always fails

can you help me please?

if you need more information tell me please.

---

### Post by lkraemer on 2012-02-07
I have an old Compaq V5201US and I am running Ubuntu 8.04 LTS on it.
It works fine.  I haven't upgraded it yet to 10.04 LTS.

Does your LiveCD run fine on the Compaq before you start the Install?
Have you verified the MD5SUM or SHA256 of the ISO file?  Did you burn
the ISO as Disk at Once DAO and at a SLOW rate?

Will the LiveCD install on any other computer?

It is likely you will need the Broadcom Firmware for your Wifi Hardware.
Most Compaq's of that vintage used Broadcom.  Search this forum for a
HOWTO: Broadcom for the answer.

lk

---

### Post by mörgæs on 2012-02-07
Xubuntu and Lubuntu are good options.

---

### Post by Mark Phelps on 2012-02-08
Just so you know ... Ubuntu 8.04 is the LAST Ubuntu version to provide support for the restricted ATI video drivers.

If you do succeed in installing a more recent Ubuntu version, you will be limited to using the open-source Radeon drivers -- which will be installed by default.

No point in then asking how to install the Catalyst drivers, because there aren't any that will work with your video card and recent Ubuntu versions.

---

### Post by mörgæs on 2012-02-08
True, but the open source drivers are good for this card (and actually for most ATI's). 

I have a Dell 610 with the same card, and I have not considered installing closed source.

---

