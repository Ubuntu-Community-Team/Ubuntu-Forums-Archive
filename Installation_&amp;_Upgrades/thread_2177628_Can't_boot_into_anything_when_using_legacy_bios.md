---
title: "Can't boot into anything when using legacy bios"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by julien3 on 2013-09-29
Just installed ubuntu 13.04 on my windows 8 laptop.. Had to disable secure boot and EUFI and use legacy bios for my pc to boot into the live cd. If i remove the live cd i get  this screen:[IMG]https://lh5.googleusercontent.com/-iL8G5LBvePE/Ukhx0Z1n0yI/AAAAAAAAACM/bAdBwKvq4rc/s640/IMG_20130929_141958.jpg[/IMG]

It won't even boot into windows 8 again unless i enable EUFI again. Still no grub however.

---

### Post by julien3 on 2013-09-29
Icing on the cake.. Now i can't use the acer power button or search/settings on windows 8..

---

### Post by oldfred on 2013-09-29
That screen is showing PXE boot which is booting a network device. That may be what you have first in boot order?

What laptop? Most have ways to get into UEFI/BIOS but some have strange key combinations. Check vendor manual.
You did turn off secure boot and fast boot in Windows? 

Some other Acer:
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

See also links to install instructions with screen shots from link in my signature.

---

