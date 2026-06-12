---
title: "HP Pavilion  15"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Piddell on 2013-04-03
Just bought a new i5 pavilion machine and having problems installing (runs ok in Live mode, apart from wifi, but we're not there yet..)

so I installed Ubuntu, but on re-boot it comes back with windows, followed the boot-repair instructions, failed 2nd time with the number
5674397

HP Pavilion Sleekbook 15-b052
Ubuntu 12.04 just downloaded


Any thoughts?

Phill

---

### Post by oldfred on 2013-04-03
Link is not always the same, is this yours?
[http://paste.ubuntu.com/5674397/](http://paste.ubuntu.com/5674397/)

Locked-ESP detected.
Several others with HPs have not had that issue, but others have. Not sure how it is occurring.
There are several work arounds. Often just best to fully backup efi partition, erase it & recreate it.

grub-efi fails to install with Input/output error - locked efi[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829"]
https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829[/URL]

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6 
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by Piddell on 2013-04-04
Yes I think that was my link
I just installed Ubuntu on its own, erased windows 8 from the PC.  Seemed the logical solution and is working fine :-)
Thanks
Phill

---

### Post by oldfred on 2013-04-04
Glad you have it working. Are you in UEFI mode or BIOS/CSM mode?

---

