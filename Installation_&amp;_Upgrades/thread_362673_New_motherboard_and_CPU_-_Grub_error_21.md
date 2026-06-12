---
title: "New motherboard and CPU - Grub error 21"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by samjh on 2007-02-15
I t looks like this is a bit of a problem for quite a few Ubuntu users.

Yes, I've searched thoroughly, no the workarounds posted have not yet worked.  No scenario I've seen matches mine anyway.

Situation:
Just installed a new motherboard and CPU (Asus P5B deluxe, and Intel Core 2 Duo 6300).
Booted up computer: Grub error 21.
Assumed I'll need to reinstall Ubuntu, so did.
Booted up computer: Grub error 21 again.

I have one IDE hard drive connected in a chain with one DVD/CD-RW drive, with the hard drive as master and optical drive as slave.  This is the same configuration I've used for the past 2 years with WIndows and Ubuntu without any errors.

I've seen a bug report that said there is a problem with the linux kernel and Intel's P965 chipset.  Other places have stuff about SATA, but that's irrelevant to my situation since I'm using IDE not SATA (and this is correctly detected by BIOS).  Other places have suggested manual installation of Grub, to no effect.  Configuring Grub to use hd0,0 has also had no effect.

Any further suggestions would be very appreciated -- and hooray to whoever thought up the idea of a live cd, or else I wouldn't be able to post this! :)

---

### Post by logos34 on 2007-02-16
Try using SuperGrub to boot it.  See [this page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17") for more info on your grub error and links to download sgd.

---

