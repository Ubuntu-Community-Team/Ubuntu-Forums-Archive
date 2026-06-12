---
title: "&quot;No boot device available&quot; after installing Ubuntu 16.04"
date: 2017-06-08
forum: Installation &amp; Upgrades
---

### Post by matty.ice on 2017-06-08
Hi, first off I'm new to Linux/Ubuntu and know next to nothing about it, but I have an interest in learning it.  So I recently wiped the hard drive off an old desktop (Dell Dimension 3100 I believe) to install Ubuntu 16.04.  I ran it from a "Live USB" external hd, then ran the install application, and set it to install to my primary 80gb hd.

So after saying it finished installation and asked to restart the machine, I switched the boot order back so it doesn't attempt to pull from the USB drive first, and I get the "No boot device available" error message.  I checked the BIOS to make sure the correct hd is enabled, which it is.

I did a bit of searching and saw some recommendations of changing some of the BIOS settings, like secure boot and UEFI, etc. but my BIOS doesn't have any of those options. I turned off "fast boot" to see if that made a difference and it did not.  I checked the Dell site to see if there is a newer BIOS version available, and it appears I have the latest one for this model (A04).

Also ran the boot-repair tool from the Live USB and then tried again and still getting the "No boot device available" message.  Not sure what else to try at this point.

Any help will be much appreciated!

---

### Post by oldfred on 2017-06-08
Looking at specs for that system it has very little RAM by modern standards. 
Did you try to install Ubuntu which now is really for newer computers with better graphics or one of the lightweight systems. 
And if you have not upgraded RAM it may still be slow.

Is hard drive set for AHCI? Does your system even have an AHCI setting? It may be too old.

 Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie 

 [https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)

---

### Post by matty.ice on 2017-06-09
> **oldfred said:**
> Looking at specs for that system it has very little RAM by modern standards. 
Did you try to install Ubuntu which now is really for newer computers with better graphics or one of the lightweight systems. 
And if you have not upgraded RAM it may still be slow.

Is hard drive set for AHCI? Does your system even have an AHCI setting? It may be too old.

 Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie 

 [https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)
It has 2gb RAM which I know isn't a ton but that is what is recommended on the Ubuntu site.  I'm not super concerned about the speed, just using it to try And get a basic understanding of Linux.

As far as AHCI, I'm not sure but I'm thinking no.  Should it be?

---

### Post by oldfred on 2017-06-09
If you have the AHCI setting change that from IDE or RAID to AHCI.
The IDE setting is for very old drives.

My old laptop was 1.5GB and I was able to run 64 bit Ubuntu, but with 12.04 Unity was so slow as to be unusable. I installed fallback which is the older menu type configuration. I have since retired laptop but recently installed 16.04 and was surprised that Unity seemed usuable, but a bit slow. With lower RAM, just do not try to run a lot of larger apps at one time or it will go to swap and be real slow.

---

