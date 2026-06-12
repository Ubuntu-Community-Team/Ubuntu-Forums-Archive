---
title: "Upgraded from 13.10 to 14.04 - dual boot windows 7 - Unable to boot - Boot repair"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by posushant on 2014-04-27
System Dual Boot - Windows 7 and Ubuntu 
I upgraded from 13 to 14.04 and have dual boot windows 7 that was working fine. Since upgrading the version 14.04 is not booting shows three options Press I to ignore S to skip mounting and M manual recovery
Tried two solutions
1. Boot-repair - Although showed it is successful the system was in the same state not booting 
Here is what i got [http://paste.ubuntu.com/7347032/](http://paste.ubuntu.com/7347032/)

2. Also tried changing ro to rw in grub file- by choosing manually repair. Performed following
[COLOR=#000000]vim /boot/grub/grub.cfg
[FONT=Verdana]
Looked for line similar to this (search for the [/FONT]**highlighted part):**[/COLOR]
[B]Code:
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=[bunch-of-numbers] loop=/ubuntu/disks/root.disk **ro rootflags=sync**  quiet splash
[/B][B]Tried Changing the ro to rw (as in - instead of mounting as read-only, mount for read-write)
[/B]
But the vim does not allow me to write .. i changed permissions etc. it did not help 

also looked for .viminfo! duplicate - it is not there 
----------------------------------------------

---

