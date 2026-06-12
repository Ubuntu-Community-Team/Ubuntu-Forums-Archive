---
title: "Installation issues due to bad sectors"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by trd.bullitt on 2010-12-21
I'm attempting to install ubuntu desktop 10.10 onto my laptop and having a few issues. Ive created a usb startup disk and it boots fine from the usb. When i try to install ubuntu it crashes when it tries to partition the drives. It comes up with the error "the ext4 file partition creation failed....."or something along those lines. I tried to run GParted to look at the partitions and that crashes as it opens and it does what I assume are the scans to work out what partitions are what.
 
I've heard this is due to bad sectors in my hdd. Is this right? If so will I need a new hdd for my laptop. Will any old 2.5'' SATA hdd fit in the old space or does it need to be a specific type?
 
BTW I have an ASUS m51v laptop (320gb hdd, 2.53 ghz dual core proccessor if that helps)

---

### Post by trd.bullitt on 2010-12-22
bump

---

### Post by efflandt on 2010-12-23
A laptop like that should have a SATA drive, so any SATA drive should work.  There are drives with different speeds, 4200 rpm, 5400 rpm, and 7200 rpm.  Or the ultimate (at a price) would be SSD (solid state drive).

I used my laptop to install Ubuntu to an SSD and it was 4 times faster than the laptop's 4200 rpm drive (limited by SATA I).  When I put the SSD in my SATA II desktop it was twice as fast as on SATA I or my SATA II 7200 rpm hard drive.

---

