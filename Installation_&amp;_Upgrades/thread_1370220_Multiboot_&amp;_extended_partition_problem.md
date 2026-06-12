---
title: "Multiboot &amp; extended partition problem"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by speedygeo on 2010-01-02
I use different systems on my laptop to test and help purpose.
Now I have this situation:
sda1 WinXP
sda2 Kubuntu karmic
sda3 Fedora
sda4 extended
sda5 home
sda6 swap
sda7 opensuse
sda8 chakra

I installed the kubuntu grub 2 on the MB, but for all the other linuxes I installed their grubs on their partitions.
I can use without problem winxp, kubuntu and fedora. The grub recognize opensuse and arch, but can't access there.
Can anyone help me?

---

### Post by Moozillaaa on 2010-01-02
Run this script, and post the result file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I had multiboot problems for 2 days, and just solved them here:

[http://ubuntuforums.org/showthread.php?t=1369442](http://ubuntuforums.org/showthread.php?t=1369442)

---

