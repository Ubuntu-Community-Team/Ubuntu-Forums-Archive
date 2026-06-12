---
title: "Alternate Install stop at 60% (xserver setup)"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by heri on 2006-06-02
I tried to install Ubuntu 6.06-alternate version, but at 60% during xserver xorg set up the installation stop.

I have installed Breezy and Dapper flight 6 and 7 on this PC, all went fine without any problem.

The monitor is generic, using Intel Corp. 82845G/GL[Brookdale-G]/GE Ch                                           ipset Integrated Graphics Device 

I've checked the CD (md5sum and media check before install) and the CD is O.K.

Running Ubuntu 6.06-desktop in livecd is O.K., but I tried not to install from here as it will install Grub in MBR.

Any suggestion please..

_SOLVED:_
My stupid, it's very easy actually.
I repeated the install, but this time before installation began, I pressed the F4 key and changed the monitor's resolution from VGA to 1024 x768 (as per my monitor's  specs).  Everything is fine now :mrgreen:

All the best !

---

### Post by towsonu2003 on 2006-06-02
[QUOTE=heri]I've checked the CD (md5sum and media check before install) and the CD is O.K.
[/QUOTE]
if md5sum is ok, try burning it to the CD at the slowest possible speed. thatusually works. also check if you told it to format the partition (it should format the / -also called root- partition) where ubuntu is gonna be installed.

---

### Post by heri on 2006-06-02
Downloaded again from different mirror and burned with 4x speed.
Reinstalled,  and the problem remains exactly the same.

---

### Post by SleepyHollow on 2006-06-02
Hallo,

I got exactly the same problem with dapper-alternate-i386. Only the pure server-installation without X works. This happened with a amilo laptop  on which Breezy 5.10 was sucessfully installed without probs.  I deleted it before in order to test dapper final.

This is really annoying. :evil: 

Greetings
SleepyHollow

(using windoze in the meantime)

---

### Post by heri on 2006-06-02
I have solved my problem, please see my original entry.

---

### Post by SleepyHollow on 2006-06-04
It works, thanks. I don't understand the reason why this is necessary. I should be equal if you install in VGA or in a resolution of 1024 . It was not necessary with Breezy to choose such an option.

:confused:

---

