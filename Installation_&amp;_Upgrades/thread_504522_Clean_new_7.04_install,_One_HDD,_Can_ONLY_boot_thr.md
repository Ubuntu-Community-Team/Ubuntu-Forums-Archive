---
title: "Clean new 7.04 install, One HDD, Can ONLY boot through LiveCD's 'boot to first disk'"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by phrygius on 2007-07-19
Hello,

I just installed onto a newly built computer with one HDD (a 250GB SATA, if that helps).  I cannot boot directly to the drive; it either just sits there, or displays something like: "No bootable device, please insert boot disk and press any key."

I can boot to the HDD, however, if I put in the LiveCD and select the "boot from first hard drive" option at the bottom.  Once that has booted, I can put the LiveCD away and go about my business.

I have checked to see that GRUB is installed (it is), and through package management, reinstalled GRUB.  I have also checked my BIOS settings, and everything *seems* to be fine.  Boot order is: 1.  CD,  2.  HDD.  It knows the drive is there and labels it correctly.

The only thing I can think of is: I partitioned like this
[LIST]
[*]"/"  sd1   0GB - 30GB
[*]"/home"  sd2  30GB - 249GB
[*]swap  sd3 249GB - 250GB
[/LIST]

And, I assumed that the MBR is automatically accounted for when partitioning.  Is that a bad assumption and I have left no room for GRUB?  Or might this be some GRUB option?

Thanks,
phrygius

---

### Post by Midahed on 2007-07-19
If this is a brand new machine, have you checked that your motherboard BIOS is trying to boot off the SATA drive.  If the mobo supports PATA and SATA, it may default to booting from an IDE channel.

There may be absolutely nothing wrong with your Ubuntu installation.  The mobo is just going to the wrong drive.  You're effectively circumventing the problem by booting from the CD.

Just an idea....

Mike

---

### Post by mozkill on 2007-07-19
yeah, you need to set your bios to boot from sata .   also, if you have 2 different sata controllers (which some motherboards have) , plug your boot drive into the right one.

or, maybe try installing ubuntu with only 1 of the hard drives connected.

---

