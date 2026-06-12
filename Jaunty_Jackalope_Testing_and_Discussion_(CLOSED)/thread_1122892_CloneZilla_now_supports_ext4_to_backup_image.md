---
title: "CloneZilla now supports ext4 to backup image"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Trespasser on 2009-04-11
Use the Experimental (Ubuntu based) version. Be sure to read the Changelog to understand how to do it.

[http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)

For those that have never used CloneZilla before you can use a USB pen drive or a second hard drive to back up your image. Does not work backing up to a CD or DVD (at least not easily). I always use a pen drive for my laptop or a second hard drive or pen drive for my Desktop.

I've tried it and it does work to backup ext4.

Here's the Changelog for this version...

Clonezilla live 20090411-jaunty

  * Based on Ubuntu Jaunty (beta) repository on Apr/11/2009. Kernel 2.6.28-11 is used.
  * Beginner/Expert modes were added. If beginner mode, the default choices in advanced parameters will be used automatically.
  * Ext4 is supported by partclone now. Therefore if you want to save ext4 system, remember to enter expert mode and use option -q2 so that partclone will save your ext4 partition.
  * Patched live-initramfs 1.157 is used.
  * When multi CPU/core is available, -z1p (pigz) will be used when saving in Clonezilla live.

Hope this helps someone.

Later...

---

### Post by FuturePilot on 2009-04-11
Awesome. Thanks for the heads up. I was wondering when one of the imaging programs would get Ext4 support.

---

