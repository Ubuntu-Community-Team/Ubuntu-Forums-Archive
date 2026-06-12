---
title: "install /, /home, /usr on separate drives? advice needed!"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-07-09
Hii Yaal!

I want to do a fresh install of U.Studio 8.04.1 (alternate).  I read that if you keep separate /home and /usr, you can keep those 3rd party apps/programs and desktop settings.  I have a separate /boot already  since I had another linux O.S. on my IDE drive.  I was given a 10 Gig scsi drive which I will test, and I have a working 40 Gig scsi already (that runs at constant 160 mb/s?), with a Windows XP partition that I still need!  I can liberate only 11 Gigs on that original SCSI drive.  For the sake of rendering video from one drive to another (advisable), and SCSIs running a little faster than IDEs (depends on the SCSI), I want to install Hardy on those SCSI drives and keep /boot,/swap, my Gutsy backup and my data on the IDE, (it's a 500 Gig drive).  Note: I only used up 5.2 Gigs with Gutsy U.Studio, and it was loaded with apps.  

What is the best layout for my desired partitions (/, /home and /usr)?  Will keeping swap on the IDE drive just ruin any speed advantage ( I have 1 Gig RAM- and 2 Gigs swap on the IDE)?  Does adding a new smaller swap on a SCSI help or perhaps lowering swappyness value?  (Boot speed is less important to me, as I have ECC memory; it's always slower). Can those 2 free ~ 10 Gig drives/partns. be enough for anything?

It was simpler to install with Windows on a separate physical drive so far... any more bugs with Hardy and windows dual boot? or other software issues I should be wary of with Hardy and this set-up idea?  After mistries and my DVD drive being a little buggy, my alternate install of Gutsy had succeeded, and Grub allowed me to boot into all my OS's real nice. Ubuntu Studio worked fine exept for no compiz or 3d.  Since Heron is a 3 year version, I don't know if having separate partitions is as important, but I'd like to try.  Any ideas and suggestions would be greatly appreciated.    

My computer is a hp workstation x400 from 2001 with 2 xeon 2.4GHz processors, nVIDIA Quadro4 Pro 900 (Ubuntu defaults to a generic NV Gforce driver), maudio audiophile 2496, no wireless, just DSL, USB 2.0 and an older DVD multi drive that I can actually boot with!  The workstation is meant for multiple SCSIs, but can be particular, so I also don't want to add hardware for too little benefit. 

Anyone wants to share any related stuff, I'd also love to hear!
Toodoloo!

:guitar:                                                :popcorn:

---

### Post by upchucky on 2008-07-09
looks like you need a bigger drive to make administration a-lot easier.

you only need about 10 gig for ubuntu, and a big space for the home partition.
do not need a separate space for usr.

I am running 2 gig ram and one 100 gig hard drive, plus a 150gig usb hard drive with no swap space I have not had any issues from runnig without the swap space but this is probably cause of the 2 gigs of ram.

---

### Post by streamsanddragonflies on 2008-07-11
Yep, of course would be easier to keep everything on my 500 Gig IDE drive, but once again if I want to try rendering video and both Ubuntu and the data rendered are on the same drive it isn't recommended...

It looks like 11 Gigs for / (SCSI a) and 9.8 Gigs for /home (SCSI b) might just work, but does it matter if /boot and /swap are on the other drive? ...from what I read, if my bios is set to boot from the IDE drive first and grub is reinstalled there then I should be ok....

I just want a confirmation: if /usr /proc /temp /bin e.c.t... all install together under / in this scenario, does /home need more than ~10 Gigs?  And what will happen to my 3rd party apps. if they are not in a separate partition in future upgrades?

Anyways, upchuky it's interesting to hear how things can work well with no swap but sufficient memory...

---

### Post by SkonesMickLoud on 2008-07-11
/home can be as large, or as small as you want it to be.  There's no recommended size, but ~10 GiB would be sufficient.

As far as apps and settings:  Not doing a separate /home can be dicey when it comes to upgrades.  If you do a separate /home, most, but not all, of your settings will be retained, and it will be much easier to do a fresh install versus an upgrade.

---

