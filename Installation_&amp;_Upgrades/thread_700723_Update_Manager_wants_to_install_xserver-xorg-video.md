---
title: "Update Manager wants to install xserver-xorg-video-intel despite I have a Nvidia!"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2008-02-18
Why is this? This is when using a GeForce 4 Ti 4200 128 MB. I don't want to corrupt X by updating. 

This is with a Dell Dimension 4600i. 

This is despite I disabled the onboard video in the BIOS setup.

---

### Post by miriad on 2008-02-18
Ubuntu installs all the xorg driver packages by default for everyone. This is done for hardware support (and the ability to switch video cards down the line without having to install a new driver from the internet while on command line only)

This update is just for the intel driver that you are not using, so it wont effect your current install.

---

