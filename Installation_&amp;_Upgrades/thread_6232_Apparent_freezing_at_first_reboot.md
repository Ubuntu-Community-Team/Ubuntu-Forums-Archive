---
title: "Apparent freezing at first reboot"
date: 2004-11-26
forum: Installation &amp; Upgrades
---

### Post by jmarc on 2004-11-26
Hi all,

I've tried to install Ubuntu on my 3 years old computer.  The hard disk was a new
one and the previous disk was removed, so no interaction with anything already
installed was possible.  The computer is able to run the live CD without problem.

The first part of installation went well, but at reboot, after the messages from the
BIOS (and possibly a small message from GRUB, it went too quickly to be sure)
the screen was cleared.  The light of the disk continued to flash during about 1 or
2 minutes.  Trying various keys (ESC, Alt-Fx, Space Bar, Return,...) didn't have
an effect.  Rebooting and trying to press the keys more quickly (in hope that before
the freeze I could access something or get messages) didn't have an effect.

Rebooting with the live CD, I could get access to the partition where I've installed
Ubuntu and nothing seemed strange.

I don't know what to try next.

Yours,

-- 
Jean-Marc

---

### Post by arctic on 2004-11-26
please post some info on the hardware you are using. :)

---

### Post by jmarc on 2004-11-26
Processor is an AMD 1.7+
   Memory is 512Mb
   DD is a new maxtor (IDE, 160Gb)
   MotherBoard is something from Asus.  I don't remember the number.  DDR memory.
   DVD reader, I don't remember brand.
   CD-Writer is older (was from the previous computer)

I'll post more info from home where I can get the info.

It ran without problem with Debian 3.0 using 2.4 kernel (using the old but never tried a 2.6 
kernel).

It ran without problem from the Live CD.

Yours,

-- 
Jean-Marc

---

### Post by jmarc on 2004-11-26
The motherboard is an asus A7V266-E.

The problem is GRUB related.  

I could somewhat solve it by booting on the other HD (which has Debian 3.0 installed)
and adding a LILO entry from Ubuntu. So my current set up is

hda has lilo installed with entries for
           - grub on hda1
           - ubuntu with root=/dev/hda1
           - debian with root=/dev/hdb1

Booting on grub hang as described above with no message and no hint that
something is strange.
Booting ubuntu works (I'm posting this from Ubuntu)
Running grub-install /dev/hda1 doesn't give any error message, but booting
from grub doesn't work afterward
Booting debian works.

There is still something to be solved for GRUB.

Another problem,
/etc/apt/source.list
contains only
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

I'm not sure that's right.

Yours,

-- 
Jean-Marc

---

### Post by wallijonn on 2004-11-26
Seeing as this is an ASUS mobo, and seeing as ASUS mobos use Promise controllers, is this an IDE (PATA) or a SATA drive? If it is an IDE, are you turning off SATA in the BIOS? If it is SATA, are you turning off Legacy PATA in the BIOS? Which SATA connector are you using? How did you get the LiveCD to install? Or did you use the non-LiveCD to install?

---

### Post by jmarc on 2004-11-26
My motherboard BIOS doesn't have anything about SATA in its settings.

The Live CD didn't install, I just could run Ubuntu from it.

I've tried to use --force-lba with grub-install but that doesn't seem to have
an effect on my problem.

Another information, when trying to boot with GRUB I'm now pretty sure that
I see a message from GRUB (perhaps GRUB phase 2 but it goes out very
quickly).  Trying ESC and other keys at that time doesn't have an effect.

Yours,

-- 
Jean-Marc

---

### Post by jmarc on 2004-11-27
I've tried to install the GRUB version coming from Debian 3.0 instead of the one
from Ubuntu and that works.

Yours,

-- 
Jean-Marc

---

