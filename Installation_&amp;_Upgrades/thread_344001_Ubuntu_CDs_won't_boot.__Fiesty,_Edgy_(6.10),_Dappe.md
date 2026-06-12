---
title: "Ubuntu CDs won't boot.  Fiesty, Edgy (6.10), Dapper (6.06), 5.10, 4.10"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by Culture20 on 2007-01-22
I've been doing some searching, but haven't been able to find anything like this yet.  I'm trying to install Edgy (or for that matter, even 6.06 LTS, and even 5.10 and 4.10) as a Guest HVM domain for Xen on a machine with intel's VT cpus.  I've gotten Suse, Gentoo, RHEL, & Fedora to install, but any Ubuntu CD gives me a blank black screen and no error messages, including the alternate & server install CDs.

Is there something special that the Ubuntu CDs do that the others don't?
Is there a way I could possibly boot from another medium (e.g. virtual floppy), then install from the iso/CD?
Is there a special ctrl+alt+F#+wave_a_chicken key sequence to skip past the hangup?

Heck, even Winblows is installing as an HVM (unmodified) guest.

](*,) 

Thanks a bunches

-C20

---

### Post by unisol on 2007-01-22
try booting into safe graphics mode and do a text mode install if that doesnt work you may have to get the alternate install cd.

---

### Post by Culture20 on 2007-03-22
Simple solution posted on this site from Colin Watson:
[http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/](http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/)

"Try holding down the Shift key while booting the CD; this should let you skip gfxboot."



And it worked!  Currently installing Ubuntu in HVMs.  Now I can support Ubuntu easier.  Thanks Colin!

---

