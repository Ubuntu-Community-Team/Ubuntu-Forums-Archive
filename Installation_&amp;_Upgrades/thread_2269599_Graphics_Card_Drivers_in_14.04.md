---
title: "Graphics Card Drivers in 14.04"
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by olligobber on 2015-03-16
My new computer has an Asus Radeon R9 290 DC2 4GD5 in it, and didn't seem to be having great performance, so I installed some drivers that I got off the AMD website, with no improvement. I have no idea which drivers to use now, and after trying to install fglrx from terminal got the following error message:

```
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Depends: xorg-video-abi-11 but it is not installable or
                  xorg-video-abi-12 but it is not installable or
                  xorg-video-abi-13 but it is not installable or
                  xorg-video-abi-14 but it is not installable or
                  xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.
```

What have I done wrong?

---

### Post by QIII on 2015-03-16
You didn't do anything wrong.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

For the moment, 12.04.4 pr 14.04.1 will work.  That or 14.10.

The bad thing about this is that I had just just blogged about how well the R9 290X worked with Ubuntu.  The new hardware enablement stack made me have to eat crow.  I'm not happy.

---

### Post by olligobber on 2015-03-17
So how do I install graphics drivers please?

---

### Post by olligobber on 2015-03-17
> **QIII said:**
> You didn't do anything wrong.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

For the moment, 12.04.4 pr 14.04.1 will work.  That or 14.10.

The bad thing about this is that I had just just blogged about how well the R9 290X worked with Ubuntu.  The new hardware enablement stack made me have to eat crow.  I'm not happy.

So how do I install graphics drivers please?

Edit: After a reboot everything works fine... I think I did enough apt-get purge fglrx* commands

Edit2: Ok, so apt-get purge fglrx* got rid of the graphics drivers I had installed, next I updated to Ubuntu 14.10 (without proper graphics drivers). After several reboots I got a command line interface and did apt-get install fglrx-updates, rebooted, and I had drivers.

---

