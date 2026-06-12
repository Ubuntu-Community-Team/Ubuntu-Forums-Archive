---
title: "Wubi gets error: No disk in the drive"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-10-11
Well so much for that!

At the Ubuntu.ork front page, it promises:
> This Windows installer (Wubi) will help you to run Ubuntu within your current system.

What exactly is meant my this?  Does this mean it is an easier way to install the dual boot with Windows? (I am using Windows-7 on a new PC.)  Or does it mean it will install Ubuntu under Windows?  I assumed it meant the latter.

In any case, I downloaded it - a mere 1024K, scanned it and ran it.  I get a stubborn error box with the message:
> There is no disk in the drive. Please insert a disk into drive
\Device\Harddisk3\DR3

[Cancel]   [Try Again]   [Continue]

And that box will not go away - no matter what I press, including the [X] button in the upper corner, the box reappears.  I had to go into Process Explorer to kill pyrun.exe and its parent, pyl5E39.tmp.exe before the [Cancel] button would close it for good.

Clearly, that's not the way to go.  I could not find doc on this so I don't know what it really wants as a prerequisite to running wubi.

Clues? Pointers to the right doc, please?

Thank y'all.

---

### Post by bcbc on 2010-10-12
There is a known bug that you get this popup - normally it's because you have a usb card or something plugged in that confuses python (that wubi is written in), or so I've heard. Every time it scans the system's drives (which is apparently often) you get the popups. You can hit cancel each time (it's not an infinite loop as it appears) or just unplug the cards etc.

Wubi installs Ubuntu on a virtual disk that is actually a file under the windows ntfs file system. (Or fat32 is also possible). You install and uninstall from windows, but Ubuntu runs natively as a dual boot using the virtual disk. It's good for trying out Ubuntu but generally recommended to install Ubuntu to its own partition for more reliability.

---

