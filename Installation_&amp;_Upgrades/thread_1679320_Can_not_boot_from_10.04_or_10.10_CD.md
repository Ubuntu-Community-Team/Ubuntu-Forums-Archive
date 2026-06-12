---
title: "Can not boot from 10.04 or 10.10 CD"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Quazimoto on 2011-01-31
SOLVED: I found that the issue is with the FireGL workstation card. By removing it and using the built-in ATI video I was able to finish the boot process, install, etc. Once this is done I activated the ATI proprietary driver. After this is done you can shut down, install the FireGL workstation card and make settings in the system settings using ATI CCC. I note that the changes may not appear until you restart.

Original Post Below:

Hi

I can not start running ubuntu 10.04 or 10.10, 32 or 64 bit version try-it and install cds. I can do the install from ubuntu studio, but this is not helpful since I can not get to that area of the HDD from windows 7 to change anything... at least I have not seen a obvious way from windows explorer, or whatever they call it now... 

I am using 4 core AMD phenom (black edition, 3.4mhz), MA785GM gigabyte MB, dual  monitors w/ATI firegl v7700 card, 6 gig 800mhz ddr2 ram. 

Windows xp, and 7 work, so box is good. I am thinking it is the ATI fireGL workstation video card, yet it is not a newer or next gen one. I figure it is about the open gl that the card uses? Any ideas or steps I can take to deal with this issue?? Thanks.

PS just tested, found similar issue with fedora. At the ATI site I see posix shared memory has to be enabled and that the kernel source package is not needed if the kernel header package is installed. Again, any pointers or steps I can take to resolve this is appreciated!

NOTE: I installed ex2explore so I can get into the file system of the installed Ubuntu studio distro. I now need to know what to change or where to add the ATI driver for this card, etc. Thank you for any pointers...

---

### Post by Quazimoto on 2011-02-01
I think that this distro will boot this set-up: PC Linux E17 

it would be a done deal if had been 64 bit. But now that I found a distro that will boot my machine, perhaps someone may know why and if so, what can I do to install and boot Ubuntu Studio?

---

