---
title: "problem with installation"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by appleboy on 2007-01-24
Hey,

I just got my new computer today (:D) and decided I was going to go with Ubuntu and see how it is, but i'm having a problem installing.  When I boot up the cd (edgy) and try to run livecd or install I get the following errors

```
Buffer I/O error on device hda, logical block 357564
hda: ide_intr: huh? expected NULL handles on exit
```

Pretty sure it has something to do with my HDD, but I have no idea what to do here.  

Here's my PC specs
Asus M2N-E ATX AM2 Nforce 570 Ultra
Athlon 64bit X2 3800+
EVGA GF7600GT
Mushkin 1gb PC2-5300 DDR2 ram
Seagate Barracuda 320GB SATA2 HDD

Thanks :- )

---

### Post by appleboy on 2007-01-24
bump >_>

---

### Post by wpshooter on 2007-01-24
Does the system already have any other O/S, like M/S windows on it or is it **completely** (?) empty ?

---

### Post by appleboy on 2007-01-24
completely blank

---

### Post by wpshooter on 2007-01-24
Have you tried to boot the machine to a WIN98 boot diskette to make sure that machine will boot to an albeit rudimentary O/S ?

Then have you considered getting the Seagate diagnostic software to run a test of the hard drive integrity.

And after that being done, and it had passed integrity testing, I would then get the **KILLDISK** program and **WIPE** the drive completely clean and then try the installation again.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by appleboy on 2007-01-25
Well the computer didn't come with a floppy drive, so I can't test a windows 98 boot disc.  The only other copy of windows I have is the XP home that's being used by the machine I'm typing on, so I think I'm out of luck trying that.

Nothing else I've tried has worked either, after checking afew posts I saw some similar problems with SATA drive computers.  I tried entering acpi=force irqpoll, pci=nomsi, and something=ide-generic (can't remember off the top of my head).  Tried both the regular and AMD64 bit versions of the edgy cd as well..

anyone out there know what's going on?  the error changes to logical block 353610 on the AMD64 cd.

---

### Post by logos34 on 2007-01-25
Does your BIOS recognize the Seagate drive?  You could try flashing your bios if there any updates...Of course you'll need a floppy drive for that (borrow a usb floppy if you have to)...My board has an update because it wasn't recognizing Sata II drives larger than 300GB...

---

### Post by appleboy on 2007-01-25
yea it's recognized and in the SATA1 slot, everything's been installed properly.

---

### Post by logos34 on 2007-01-25
cancel

---

### Post by logos34 on 2007-01-25
cancel

---

### Post by appleboy on 2007-01-26
I think I'm about to give up and just borrow an XP cd from someone, any last ideas :confused:

---

### Post by logos34 on 2007-01-26
I misinterpreted your last post...thought you meant that everything was working now....

I was going to suggest adding 'irqpoll' to the end of the boot options line, but you already tried that...

The error message mentions hda, which is your dvd/cdrom (your sata hdd is 'sda')...could be a problem with the ide controller...What make and model motherboard do you have?  The reason I ask is there are issues/bugs with some controllers (JMicron on some Asus boards, just to mention one example)...

---

### Post by appleboy on 2007-01-26
It's an ASUS M2N-E ATX AM2 Nforce 570 Ultra

---

### Post by logos34 on 2007-01-26
try flashing the bios (0602 - latest update).

Found this
[http://forum.ncix.com/forums/displaylink.cfm?link=http://blog.tobias-olry.de/asus-m2n-e-vs-kubuntu-edgy/](http://forum.ncix.com/forums/displaylink.cfm?link=http://blog.tobias-olry.de/asus-m2n-e-vs-kubuntu-edgy/)
[http://forum.ncix.com/forums/index.php?mode=showthread&forum=199&threadid=1121566&pagenumber=1&product_id=18885&subpage=1](http://forum.ncix.com/forums/index.php?mode=showthread&forum=199&threadid=1121566&pagenumber=1&product_id=18885&subpage=1)

---

