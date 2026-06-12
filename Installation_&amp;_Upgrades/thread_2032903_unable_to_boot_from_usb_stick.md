---
title: "unable to boot from usb stick"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by ironcoque on 2012-07-24
I'm trying to boot from a usb stick, on a tablet iconia tab w500. It halts immediately after "syslinux" version message. I've tried different iso files, different usb makers, but always got the same problem. Funny thing, if I install ye wuni version, it works perfectly. Other non debian distros also managed to boot (peppermint and fedora).

---

### Post by efflandt on 2012-07-25
Strange, I have no problem booting from USB stick or SD slot in Acer W500P, which should be same as yours, except Win7 Pro instead of Home.  The tough thing originally was trying to figure out how to get into CMOS setup to enable it to show the F12 key (I forget if I changed boot order too). 

But now if I just turn it on, it boots Win7.  If I hold Windows button while turning on, it boots from SD, or if USB stick is inserted (with or w/o SD), it boots from USB.  It can even boot Ubuntu without keyboard attached if you enable touch screen keyboard in Universal Access.

I used **Startup Disk Creator** in Ubuntu to do the ISO on USB.  And using that I recently installed both Lubuntu and Ubuntu (12.04 64-bit) on 32 GB SD with common /home.  The only issue I had was that I had to install pulseaudio and pavucontrol in Lubuntu to get its sound to work.

---

