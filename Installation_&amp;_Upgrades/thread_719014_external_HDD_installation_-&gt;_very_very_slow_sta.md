---
title: "external HDD installation -&gt; very very slow start up"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by jeden_Jedi on 2008-03-08
Hello!

this is the 1st time that I try to install a Linux distribution

currently I have the Ubuntu 7.10 installed on a usb external disk (ED)
boot it on a laptop by usb (2.0), but the start up is very slow.(more than 4 minutes)

[INDENT]Laptop:
Intel Pentium M 1,6
ram 1024+256 at 333

ED:
Toshiba 2,5' 160Gb
the Ubuntu partition is about 10 Gb[/INDENT]


The installation process was not pacific.
I solved the other problems consulting the forums, but now I would like to ask for some help.

Attempts:
[INDENT]1st
installed Ubuntu on a partition at the end of the disk
installation changed the MBR of the laptop disk(LD)
booting-> GRUB gave the error 17

2nd
MBR of the LD was restored with windows cd
got the laptop disk out
installed Ubuntu in the external disk without any partition (160gb)
booting-> got the GRUB error 18

3rd and finally
with the laptop disk out.
left unallocated space in the begin of the ED
used the *Largest Continuos Free Space* option
installation succeeded
boots and works (writing from it right now)

[/INDENT]

Problem:
takes about 4 to 5 minutes to start up, more than the live cd,

Problem Description:
the GRUB starts, it takes about 30 seconds for the selection option (if I press Esc I have 3 options, all related with Ubuntu),
if I don't press Esc, 3 seconds and it starts the default
from now till the appearance of "*Starting Up*" it takes about 4 minutes, during this time the ED is always in Read/Write mode (only in a few milliseconds the light status change)

Questions:
1. Is 4 to 5 minutes too much for an external disk boot?
2. If yes, how can I determine what is happening and put it booting faster?
3. Is it possible to install it with the laptop disk connected then change the both MBR . instead of making the installation without the LD wired?

---

### Post by jeden_Jedi on 2008-03-11
after reading some things in the forum

[http://ubuntuforums.org/showthread.php?t=285920&page=2](http://ubuntuforums.org/showthread.php?t=285920&page=2)
[http://ubuntuforums.org/showthread.php?t=287537](http://ubuntuforums.org/showthread.php?t=287537)
[http://ubuntuforums.org/showthread.php?t=604437](http://ubuntuforums.org/showthread.php?t=604437)

installed bootchart and restarted
so I got to the conclusion that the problem is in the grub
because the rest of the startup goes in normal time

---

### Post by PaulFXH on 2008-03-11
In my system, I have quite a number of linux OSes installed on external usb drives (although Ubuntu itself is on an internal HD).
I use the Grub bootloader (accessible through Ubuntu) to boot all of my OSes on external drives as well as some non-Linux stuff on internal drives (Windows XP, FreeBSD).
In my situation, I have NEVER had a problem with long boot times with Grub. In general, most OSes are ready for use well within 2 minutes of having been selected from the Grub boot menu.
If you want any more info on my setup, just ask.

---

