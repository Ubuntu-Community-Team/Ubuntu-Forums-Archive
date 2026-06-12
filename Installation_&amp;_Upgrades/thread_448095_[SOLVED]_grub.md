---
title: "[SOLVED] grub"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by ripit on 2007-05-18
Hi,
when I try to boot my laptop hangs in grub, it say:

GRUB Loading stage1.5


GRUB Loading, please wait...


and then it just stays there.
Help please.

---

### Post by apunc1 on 2007-05-18
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/15531](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/15531)
[http://ubuntuforums.org/showthread.php?t=23519](http://ubuntuforums.org/showthread.php?t=23519)

---

### Post by ripit on 2007-05-19
I solved it.

When booted the livecd and started qtparted I saw a strange partition in the beegining of the disk 1mb big. I thought that this was making all the trouble so I downloaded the qtparted livecd( probably not needed could probably just as well used qtpartd from ubuntu live). After booting with this I made my first drive bigger by using the 1mb in front of it. I was a little worried because it was on that partition I had Vista but after it was finished and rebooted grub was there and worked just fine. Now it was problems with vista but it was solved by it self when I chosed repair from vista install cd. Now everything works fine.

Hopes this helps someone.

---

