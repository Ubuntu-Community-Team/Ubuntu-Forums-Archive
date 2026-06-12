---
title: "Nvidia-drivers problem in Ubuntu 14.04.1 64bits after update"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by miguel-carcamo on 2015-01-31
Today I've upgraded(update with kernel) the system and the problem is that it  appears and 640*480 screen with the login and the background, after  logging in, the screen got stuck(No unity, just background and mouse).

  I have an NVIDIA card, GT610 to be precise, and I have CUDA  installed, this is necessary because I'm learning to develop on this. So  I followed the CUDA Ubuntu 14.04 Official Instructions. Which are to  install a deb package, and then do sudo apt-get install cuda. This  installs nvidia-340 and cuda-6.5


  Everything was fine until the upgrade, what can I do to fix this?

  PS1: I've been looking for answers(reinstall ubuntu-desktop, reinstall unity), and no one seems to fix the problem.
  PS2: I have a PC Intel Core i7-3770 .40 GHz, 4 GB RAM, NVIDIA GT610.
  EDIT 1: There was another update today, I tried it, I repeated the uninstall-install and nothing happened

---

### Post by Nutria on 2015-02-01
Look in /var/log/Xorg.0.log for any errors.

---

