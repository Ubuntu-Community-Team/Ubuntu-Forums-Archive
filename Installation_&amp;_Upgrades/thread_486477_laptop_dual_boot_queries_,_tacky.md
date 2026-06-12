---
title: "laptop dual boot queries , tacky"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by farbird on 2007-06-28
I have a laptop with preinstalled vista..

i bought another hdd and installed kubuntu..

ie now i have 2 hdd but the laptop only has a single hdd bay..

I am thinking of a way to place the vista partition into the kubuntu hdd..

any guides?

ie without reinstalling everything

---

### Post by wjp.reg on 2007-06-28
I think you are going to have to reinstall something..  unless you have a way of installing the second HD alongside the vista-installed HD.

Here's a thread that may help you.

[http://ubuntuforums.org/showthread.php?t=486574]("http://ubuntuforums.org/showthread.php?t=486574")

good luck!

---

### Post by farbird on 2007-06-28
possible to use gparted to shrink ubuntu hdd disk partition and create a secondary partition?

after which, i ghost the vista hdd partition and place inside the secondary partition of the ubuntu hdd?

---

### Post by wjp.reg on 2007-06-28
> **farbird said:**
> possible to use gparted to shrink ubuntu hdd disk partition and create a secondary partition?

after which, i ghost the vista hdd partition and place inside the secondary partition of the ubuntu hdd?

gparted live cd will work very well to resize, but I can't tell you about ghosting.  You could just resize vista (using gparted) and add linux to it, perhaps a lot easier?

Wolf

---

### Post by Immolatus on 2007-06-28
Windows must be the installed FIRST on the drive, on acount of the MBR.
Ubuntu will then install GRUB to MBR and automatically "chainload" windows.
As  long as there are installed on the same drive.

---

