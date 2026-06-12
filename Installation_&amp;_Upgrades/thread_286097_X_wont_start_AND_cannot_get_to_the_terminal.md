---
title: "X wont start AND cannot get to the terminal"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by JackMitchell on 2006-10-27
Hi Everyone,

I think this new ubuntu hates me. I tried the livecd which wouldnt start X. Then i tried the alternate cd and manged to get everything installed however when I try and run the normal ubuntu it crashes on the startup screen, I get lots of weird luminous green lines and offset pixels (this happened on the livecd aswell) tried going into recovery ubuntu and it stopped working on this command:

[17179596.796000] sda: assuming drive cache: write though
[17179596.804000] sda: assuming drive cache: write though

My graphics card is an X800GTO

---

### Post by Beaucephus on 2006-10-27
Did you verify your ISO image with something like MD5sums?  I suspect the disk hates you.

---

### Post by frogotronic on 2006-10-27
> **JackMitchell said:**
> Hi Everyone,

I think this new ubuntu hates me. I tried the livecd which wouldnt start X. Then i tried the alternate cd and manged to get everything installed however when I try and run the normal ubuntu it crashes on the startup screen, I get lots of weird luminous green lines and offset pixels (this happened on the livecd aswell) tried going into recovery ubuntu and it stopped working on this command:

[17179596.796000] sda: assuming drive cache: write though
[17179596.804000] sda: assuming drive cache: write though

My graphics card is an X800GTO

I had this problem with Breezy Badger...the X server is not configured properly.  It didn't install properly.  I reinstalled and it solved ze problem...BUT I would check the CD to make sure it's good before going through all of that.

- CH :KS

---

### Post by Roobert on 2006-10-27
My problem is similar...I upgraded from Dapper to Edgy, xserver got broken along the way and can't detect my video card....so now I have a blank screen, *even when I reboot using the ISO cd!* How can I do a fresh install is I can't see any of the menus?

~ Roobert.

---

### Post by JackMitchell on 2006-10-27
well the same thing happened with the release candidate, final version and the alternative final version so i doubt that i need to md5 it.

---

### Post by pharmd24 on 2006-10-27
Same problem here - x850xt pci-e

Will try again tonight!

---

### Post by pharmd24 on 2006-10-28
Well.....
My iso file passed the md5 checksum but the disk was bad.  I burned another disk, but no joy same nonstartup with funky green lines.  

I booted in to recovery mode got to the command line and edited the xorg.conf file to use the vesa driver. JOY!  Installed the flgrx driver and added a patch at the end to turn off some modues and POOF!  Working install with decent drivers.

Only issue now is onboard sound with ATI Radeon Xpress 200 RS482 Chipset.  If I can get sound I'm going to be very very pleased!

---

