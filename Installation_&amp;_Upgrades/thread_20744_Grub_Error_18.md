---
title: "Grub Error 18"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by TimJenkin on 2005-03-18
I installed Ubuntu on my PC and when it came around to boot for the first time it gave Grub error 18. I guessed this was because I had no network card in the computer. I installed a network card and connected it to the internet, and then the second time around it installed perfectly. I used the computer for a couple of days and everything worked fine. A few days later I wanted to use it again but had lost the passwords. To overcome the problem I decided to reload Ubuntu but again it came up with Grub error 18 on the first reboot. Now I can't go any further.

It seems this is a fairly common problem and I have read up about it in the forums. Mostly people fix it by fiddling about with BIOS settings. I have tried just about everything in the BIOS but it makes no difference. The HD can't be too large for the BIOS because it used to work with Win 2000 and it worked with Ubuntu on my first successful load.

The computer is a bog standard PC and the HD is 40Gb. Processor is Celeron. There are no other drives apart from the CD and floppy. There is no Windows partition and the installion I performed is the absolute default on the disk.

Any clues....?

---

### Post by benblout on 2005-03-24
[QUOTE=TimJenkin]I installed Ubuntu on my PC and when it came around to boot for the first time it gave Grub error 18. 

<snip>

Any clues....?[/QUOTE]

Have you seen this page:

[http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes)

It got me through a Hoary install I am just finishing.  I had to set the disk type
to "USER" and disable the LBA mode BEFORE starting my install.  And when I 
did so, the default boot order of my hard drives changed.  Just a few things
to look for.

My two cents would be to jump directly to Hoary at this point - it is in very good 
shape, and may save you more upgrade time than any hassles you run into.

-Ben

---

