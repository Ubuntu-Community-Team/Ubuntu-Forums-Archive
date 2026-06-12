---
title: "BIOS not seeing drive"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by heavylifting on 2012-08-07
Ok so I have installed Ubuntu about 3 times now. I have an ASUS G75VW. Whenever I go into the BIOS to override the boot sequence my hard drive is not showing up as a bootable drive. The BIOS does see the drive its just not listed as something to boot off of.

I booted Ubuntu off of my USB stick again to check out the partition and it has it as an EXT4 partition 200GB. The other 300GB are just a data partition. Also, when I went to Edit Partition in Disk Utility it stated it was a LINUX BASIC PARTITION. I was curious if I needed to change it to a BIOS BOOT PARTITION?

---

### Post by drmrgd on 2012-08-07
Something doesn't seem quite right with that configuration.  200GB is pretty large for a /boot partition, and I'm thinking you may have not created one or didn't correctly assign the where Ubuntu should boot when you set it up.  Also is this a dual boot system, or are you running Ubuntu alone?  

It may be helpful to diagnose if you run Bootinfo Script from the live USB drive, and post the output here with Code tag to make it easier to read please.  That way we can see the layout of the drives and where you put the /boot partition.  You can find the latest version of Bootinfo Script with instructions on how to run here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

