---
title: "Freeze during install @ ide-cd module.."
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by BMasiak on 2006-03-08
Ok, so this has been mentioned a problem with this old thread, that i tried to bring back to life, but probably due to a fact it covers the old version got ignored.. ( [http://ubuntuforums.org/showthread.php?t=7734](http://ubuntuforums.org/showthread.php?t=7734) )
So here is the problem.. I have the compaq presario 1230 laptop, tried to install both 5.04 & 5.10 and both freeze at the same point, when it's Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'...
[img]http://bmasiak.com/pics/computer/ide_problem01.jpg[/img]

Alt-F4 shows the ide-cd cmd 0x25 timed out along with hdc: lost interrupt:
[img]http://bmasiak.com/pics/computer/ide_problem02.jpg[/img]

Alt-F3 stops at insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko:
[img]http://bmasiak.com/pics/computer/ide_problem03.jpg[/img]

Any ideas would appreciated...
btw, i've tried ide-off, acpi-off with the same result...

---

### Post by BMasiak on 2006-03-08
After further searching, i've found this to be a common problem on here, with mixed results... so if mods/admins don't oppose, I'll keep posting here bits and pieces from other threads, and their applicability with my particular laptop.

In reference to: [http://ubuntuforums.org/showpost.php?p=415290&postcount=12](http://ubuntuforums.org/showpost.php?p=415290&postcount=12)

It finally went thru past the ide-cd detection, however, it now freezes upon Scanning /cdrom/pool/main/l...
[img]http://bmasiak.com/pics/computer/ide_problem04.jpg[/img]

---

### Post by wrtrdood on 2006-03-08
I had the same problem on an Acer TravelMate and a Compaq 1230 but was not able to resolve it.  As I understand it, the problem is that the default interrupt for CDROM is 15 and more than likely yours (like mine) is at 14.  Have a look at

 [http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html](http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html)

 for some possible troubleshooting steps.  I tried several without success.  Oddly, Debian Sarge installs just fine.

---

### Post by zerocool1014a on 2006-03-08
I had the exact same issue but im typing this from breezy right now try:

linux acpi=off no acpi

it worked for me!

---

### Post by BMasiak on 2006-03-08
[QUOTE=zerocool1014a]I had the exact same issue but im typing this from breezy right now try:

linux acpi=off no acpi

it worked for me![/QUOTE]
I've tried that before, with no result.. thanks though.

[QUOTE=wrtrdood]
I had the same problem on an Acer TravelMate and a Compaq 1230 but was not able to resolve it. As I understand it, the problem is that the default interrupt for CDROM is 15 and more than likely yours (like mine) is at 14. Have a look at

[http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html](http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html)

for some possible troubleshooting steps. I tried several without success. Oddly, Debian Sarge installs just fine.[/QUOTE]

Intersting link, hasn't work for me yet, but i'm trying different things based on that fact. Thanks

---

