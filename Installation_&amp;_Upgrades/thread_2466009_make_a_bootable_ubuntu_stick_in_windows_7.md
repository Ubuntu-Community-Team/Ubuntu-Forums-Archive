---
title: "make a bootable ubuntu stick in windows 7 ?"
date: 2021-08-17
forum: Installation &amp; Upgrades
---

### Post by josephfg on 2021-08-17
Hi there.  Been away for a while.  Recently I obtained a desktop machine with Windows7.  I have the laptop I used to use with Ubuntu (Focal Fossa).  The laptop now has no bootable drive (gives that message on startup.)  I want to install Focal Fossa or Hirsute Hippo on it (any suggestions?)

I have a blank SanDisk 32GB flash drive, and I have read some tutorials but they seem to miss the point of what I am trying to do.  I am trying to make the 32G stick into a bootable install stick for my laptop.

If it helps, the desktop machine is a Dell XPS with a Core i5 and the laptop is an HP notebook.

Also, I already have the iso image for Focal Fossa stored on my hard drive.  Just need to get it burned to the stick.

---

### Post by GhX6GZMB on 2021-08-17
Burn the .ISO to your USB stick using Rufus on your Win machine. Choose the defaults in Rufus. Done.

---

### Post by oldfred on 2021-08-17
Is HP UEFI or BIOS based system?
Desktop with i5 should be UEFI. But need more details on specs to give better details on install procedure. 
Dell often needs some settings in UEFI changed.

Most Windows 7 installs were BIOS, but Windows 7 could be installed in UEFI mode to gpt partitioned drive, if UEFI secure boot off.
Rufus makes either an UEFI only or a BIOS only bootable flash drive. You need to match system.
Other tools make bootable flash drive that can be booted either UEFI or BIOS, but then in UEFI boot menu must choose the UEFI boot option.Lots of 

info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by josephfg on 2021-08-17
Wow that was spectacularly easy.  Thank you!!!

---

### Post by josephfg on 2021-08-17
ml9104's solution worked like a charm.  Thanks!

---

