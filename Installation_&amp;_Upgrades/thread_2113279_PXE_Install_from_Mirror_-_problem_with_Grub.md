---
title: "PXE Install from Mirror - problem with Grub"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by fs2307 on 2013-02-07
I am attempting to do unattended installation of ubuntu from  pxe server. 
I created my own mirror with apt-mirror. Everything seems to be working fine until it gets to "grub-pc"  configuration that require confirmation that I want to continue without  installing boot manager. I cannot find a way to suppress that menu or preseed choice in any way. If yes option selected installation finishes as expected and machine is bootable (Actually Grub is installed after you select yes proceed without installing it).  This supposed to be used for automatic deployment so having question pop up needs to be avoided.
Any help would be appreciated.

I attached screenshot of the dialog in question.

Any advise on possible change to grub package, preseed option or modification to kickstart file are appreciated.

---

