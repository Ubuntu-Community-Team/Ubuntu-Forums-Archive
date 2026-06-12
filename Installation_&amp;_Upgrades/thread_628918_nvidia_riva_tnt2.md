---
title: "nvidia riva tnt2"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Jim Lady on 2007-12-01
I installed Ubuntu 7.10 with a NVidia Riva TNT2 Model 64 video card.  I've followed all the instructions about installing the restricted driver.  But when Ubuntu starts up, It gets to a point where it flashes and goes blank as if setting the screen resolution.  Then it flashes back to the command line, then goes blank again.  It does this about three times before I get the message saying it's using low resolution mode and asks me if I want to continue.  I continue, and the screen is in low resolution.  I got to set the driver, and it shows that I'm using some "vesa" driver.  The only other option it gives me is an ever lower resolution.  I try to set it again with the same result.  I have an Iiyama Vision Master 450 monitor.

This is really frustrating :mad:. I've spent way too much time trying to figure this out.   I've installed other versions of Linux and this has never been an issue.  This is the first I've heard of have having to use a "restricted" driver.  Windows has no problem with my hardware.  

Any help would be very much appreciated.

---

### Post by monktbd on 2007-12-02
my guess is that the driver you use (is in the repositories) is too new for your card.
see [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) which driver supports the riva tnt2 chipset.

i don't know which driver is the legacy driver in the repositories since there are two listed on the nvidia site, so even installing the legacy driver from the repositories might not work and you will need to install the 1.0-71xx driver from the nvidia site directly.

also a good read about that problem could be [this](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29#head-1549d676e3de65ec1342cf2c8e25df0d9745b5a7)

---

### Post by Amamba on 2007-12-05
I am having same exact problem. Tried various fixes to no avail.

If I blow away my xorg.conf & restart, I get the hi-res mode but no gls.

If I setup Nvidia restricted driver, it's low-res only.

It worked flawlessly in 6.04, when I first tried Ubuntu. Looks like something got broken along the way.

If anybody was able to fix this please let us know !

---

### Post by Amamba on 2007-12-05
Well, after several attempts (at 2-3 hrs each) I finally gave up and removed Ubuntu from my machine. I guess I'll check back in a year. Happy Holidays to all !

---

### Post by finneyabraham on 2007-12-18
I had the same experience that Jim Lady had. I am not yet ready to throw in the towel with Linux.
Since my system is not critical for me, I am thinking of re-installing Ubuntu server to correct the problem.:(

---

