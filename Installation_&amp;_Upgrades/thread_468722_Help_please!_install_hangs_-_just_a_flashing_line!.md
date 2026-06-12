---
title: "Help please! install hangs - just a flashing line!"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by geforce on 2007-06-09
just tried to install ubuntu , dvd boots fine and i select install , it then says loading linux kernal and then goes to a screen with just a white flashing line in the top left corner and stays like that???

help please!


im trying to instsall on an Asus/ergo laptop
512mb ram
Centrino pentium m 1.6ghz

---

### Post by geforce on 2007-06-09
anyone?

---

### Post by geforce on 2007-06-19
Help please!!!!

---

### Post by Redman7 on 2007-06-19
I have the same problem, the machine i am installing to is an ASUS M2400N 
(Pentium M 1600mhz, 256mb RAM)

I have tried loading both 6.10 & 7.04 installation CD, same result after selecting "Start or Install Xubuntu" or "Check CD for Defects",  black screen with blinking cursor at the top left of the monitor.
(at least "memory check" is working)

Would appreciate help extended.

---

### Post by wpshooter on 2007-06-19
Have you tried starting using safe graphics mode parameter ?

P.S. - Are you burning your CDs at 4X or less ?

---

### Post by Pumalite on 2007-06-19
> **wpshooter said:**
> Have you tried starting using safe graphics mode parameter ?

P.S. - Are you burning your CDs at 4X or less ?

Or maybe download a new TORRENT iso and burn at 1x. The one with 256MB RAM, I would try an 'Alternate' CD, Xubuntu.

---

### Post by PressPot on 2007-11-12
I'm having the same problem in my asus m2400n. After kernel loading the cd-rom drive stops spinning and a cursor flashes on the screen top. 

Asus M2400n
CPU: 1.3ghz
Ram: 512mb

I burn my iso at 4x, my cd-rom burner doesn't support less.

Does anyone know the solution for this problem?

---

### Post by Pumalite on 2007-11-12
Try the Alternate CD.

---

### Post by PressPot on 2007-11-13
Did anoyne try this?

---

### Post by Pumalite on 2007-11-13
Everyone tries that when the Live CD doesn't boot, or has hardware problems.

---

### Post by Gordone on 2008-01-02
Turning ACPI off also seems to help, especially with older hardware.

To do this, at the initial boot screen, highlight the normal installation option and press F6.
This will allow you to edit the execution flags of the installation. After the -- add "acpi=off" (without the inverted commas).

Hopefully this helps:)

---

### Post by Knight007 on 2008-04-28
I think this is the issue which most closely resembled mine.  I'm installing on an old Pentium 3 and have tried re-burning at low speed as well as with ACPI=off with no luck.  

The exact issue is that following the "loading linix kernel" progress bar, the system hangs with a flashing cursor and no further progress or error message.

I am about to try with the alternate install CD which I'm currently downloading - wish me luck!

---

### Post by eyv on 2008-07-05
Having the same problem. Alternate CD did not work (neither did Server or LiveCD). ACPI fail-safe did not work. I've also confirmed that Debian Lenny has the same problem. Suspect something to do with newer kernels.
It seems to happen after the kernel gets uncompressed, and control should jump to the kernel. This does not happen, so the system does nothing. Note that mine still responds to CTRL-ALT-DEL.
My system is an old HP NetServer LC3 with a PIII-500 and 256MB of non-ECC non-HP (not original) RAM, although the RAM is not the problem (tried with old HP RAM).
Windows XP Pro install just fine. The irony!

---

