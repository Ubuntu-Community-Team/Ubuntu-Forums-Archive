---
title: "Full disk encryption broken after re-installing 14.04"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Garry_Smyda on 2014-05-05
Hmm, got myself into a bit of a problem here.


Upon upgrading to Trusty Tahr, I encountered a now-forgotten problem.  I'll ask for help on that one later.


Came to the conclusion that what I needed to do was re-install Ubuntu using the live cd.  Wrong move. During the re-install, my previously installed os was not detected, presumably because it was using pre-boot encryption.  So I booted the live cd, unlocked the drive, and completed the re-install.


Now I am never asked for my fde password upon booting, and I get the error "gave up waiting for root device," and the BusyBox built in initramfs shell loads.


A google search says that I can just unlock the device using cryptsetup, but cryptsetup is not found.  Also tried boot-repair running from the live cd, which didn't work either.


Help, please! :)  I would rather not remove the full disk encryption, if possible.

---

### Post by Garry_Smyda on 2014-05-06
Any ideas?

---

