---
title: "Boot Ubuntu 14.10 on a Intel NUC D54250WYKH2 Barebone several Issues"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by daniel241 on 2015-01-20
Hey Guys, 

i a pretty new to Ubuntu - i do have several Issues.

 **First my Hardware:**

WD Green 2TB WD20NPVX - 2,5'' / SATA III / I.Power / 8MB 
 Kingston 8GB SO-DIMM DDR3L 1600MHz CL11 - ValueRam
Intel NUC D54250WYKH2 Barebone - Intel Core i5-4250U 

The System itself runs perfect - i have no Problem accessing the Intel Bios etc.

[B]What i want to do:

[/B]I want to run a Ubuntu System on the Flash USB Drive.
So i bought a Kingston DataTraveler G4 32GB - USB 3.0 Stick - I downloaded the latest Ubuntu Dekstop 64 bit Iso - then i use "Universal Installer" to create a Bootversion on my USB Stick.

So far so good - no Problems here. It works fine on my Windows 7 Professionel Dekstop PC (i restart and boot from the USB)[B]

Then:

[/B]I configue my Bios on the NUC: I set UEFI and Boot from my USB first - Ubuntu Comes to live and i can choose whether i want to run it from the USB OR if i want to install it - but both Options dont work .. after a short loading Screen from Ubuntu this Message appears: "Unable to find a medium containing a live file System".


Any suggestions ? (Process DOES work with an USB 2.0 Flash Drive though - but as my NUC supports USB 3.0 and i bought a quite Expensive USB 3.0 Flash Drive i want it to run with a 3.0 stick).


I hope  somebody can help :)

---

### Post by oldfred on 2015-01-20
I had saved some NUC links as question was regularly coming up. Not sure if still current.

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

---

### Post by daniel241 on 2015-01-21
Thanks ! I have a look here ..

---

