---
title: "installation freezes at random points"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by d4rkf0rm on 2011-03-11
so ive never had an issue with a ubuntu installation before.
on this box everything fails... ubuntu 10.10/10.04, fedora 14 (x86 and x64), windows 7 x64, knoppix, centos 5.5, everything.

here are the specs:

MSI 890FXA-GD65
AMD Phenom II X2 555
Mushkin Silverline 996770 (2x 4GB)     (passed memorytest with 0 errors after 3 hours)
Nvidia GeForce GTS450
Hitachi 2x 500GB @7200rpm
Corsair HX 650W


in order to get any OS to make it past a grub i have to disable USB in the BIOS

ive failed with all 8GB of memory installed and only one stick of 4GB.

ive also tried this on an ASUS M4A79XTD EVO motherboard and a Diamond ATI Radeon 5770

ive tried acpi=off noapic nomodeset etc etc etc

The only thing i havnt tried is dropping down to a 2GB stick of memory and using a different power supply

---

### Post by Hedgehog1 on 2011-03-11
d4rkf0rm,

You have tried most combinations <Yikes!>.  This means less ground to cover now.

I think we need to get a look at your disk partition layout.  The disk is the one constant.

Please boot off the LiveCD/LiveUSB, select 'TRY' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by mörgæs on 2011-03-12
It might be worth a try to upgrade the BIOS.

---

### Post by d4rkf0rm on 2011-03-13
so ive upgraded my BIOS to the most recent version.

The install worked with a lower capacity stick of ram (1x Crorsair Dominator GT 2GB module)

and it boots fine with that one module of ram, but if i put the 2x 4GB modules back in it fails to boot and hangs at a black screen with blinking cursor...

but heres where that doesnt make sense: that ram im using passed 3 hours of memtest86+


the next thing im going to try is not using RAID and only installing on one disk and probably go pick up some new ram :(

---

### Post by d4rkf0rm on 2011-03-13
oh something interesting i just stumbled upon... if i launch memtest from grub i get:
too small: Lower memory and some random memory pointers.... so for some reason grub doesnt like the amount of ram in my system

---

### Post by d4rkf0rm on 2011-03-14
ok ive narrowed it down to the ram.... it seems as though GRUB does not like the fact that the smallest module attached to the board is 4GB and im thinking that its the issue of 32 bit memory addressing.

is there a GRUB release that is designed to handle this much ram on a single module??

---

