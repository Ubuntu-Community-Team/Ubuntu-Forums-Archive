---
title: "Maxtor SATA Harddrive"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by AmericanAqualung on 2007-02-08
Hey,

I've been using Ubuntu the past several months - very happy with it.  However, our physics department at school just got a Dell Dimension 4700 given to us for our Theoretical/Computational Physics research group.  The computer has a 3.0 GHz P4 with 1 gig of Ram and an 80 gig Maxtor SATA drive.
When I tried installing Dapper (6.06.1), it was unable to detect the harddrive.  Now I'm trying Edgy (6.10) (both with the alternate install CD), and at least get a screen that prompts me to input the type of driver necessary for the drive.  Does anybody have some hints for what to use for this set up?  I googled quite a bit and haven't been able to figure out which driver is necessary (or if it isn't available on the cd, what to download to patch in).

Thanks,
Andy

---

### Post by Ritchstorm on 2007-02-08
Hello! I have two 160gb maxtor sata hard disks and they work fine. Maybe the hard disk is set to RAID. If so you will need some other stuff and other drivers. I am no longer using RAID but I used to but I never tried it on Ubuntu. It was a little awqward gettng to work on Windows as well. Maybe turn RAID off in the bios? (if no other operating systems are installed) but if windows is also installed, if you turn it ff, you probably wont be able to run windows anymore. Try asking for RAID help if you wish to use it.

---

### Post by AmericanAqualung on 2007-02-09
Thanks for your response.  Although the bios contained no explicit RAID setting, I switched the mode from "compatible" to "normal" and it worked no sweat with Dapper.  Rather interesting because compatible is supposed to mean that the drive will work for any OS and is intended to make it work for those with difficulty detecting SATA drives.  Even though Ubuntu works on SATA, I figured compatible would mean it was work whether or not the OS liked SATAs.  Oh well.  Hope this experience helps others out there having a similar problem.

---

