---
title: "Intel L440GX+ / Adaptec AIC7896/97 installation problem"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by hipnerd on 2007-07-24
I am currently attempting to refurbish an old Intel L440GX+ -based dual P-III server. It is currently running an outdated version of Debian. I wanted to Install Ubuntu Server on it.

When I installed Debian, I had to jump through some hoops, because as I recall, the Adaptec SCSI chip onthe motherboard wasnot supported. I think I had to either hack the ISO, or maybe make some sort of boot floppy.

Well five years of driver developments did not help this situation. Ubuntu will not install. It just freezes shortly after loading the kernel. I suspect it is the same issue. The passing of time has made good information about this board even harder to find.

I think it has an Adaptec AIC7896/97 chipset that is causing the trouble. Does anyone have any advice on how to get past this install issue?

---

### Post by hipnerd on 2007-07-30
No advice from anyone?

I'd hate to junk a perfectly good piece of hardware simply because of a driver issue that only affects installation.

I can think of a few potential ways around this, but I lack the knowledge to implement or to confirm they are possible.

1. Can I install Ubuntu from the command prompt after loading Debian, which is currently on the drive?

2. Can I type in some fancy command during install that loads the driver from a floppy of something?

3. Can I boot from a floppy and do a net install of some sort?

Anyone have any advice here? Or should I look for another machine?

---

### Post by indeed on 2008-04-25
Almost a year later, but maybe you're still interested ...

I wrestled with one of these about three years ago. The problem turned out to be that the installer wasn't loading the dac960 module for the acceleraid controller. It had to be done manually - the details escape me now but it sounds like you know what you're doing.

It's been a nice home-office server ever since.

---

### Post by okdok on 2008-04-28
I am hoping that someone can shed light on the details above. I have an ADAPTEC 2100 S SCSI. I have the same scenario. Installed years ago with CENTOS and all was fine. I am trying to install Hardy and cant get past the Kernel Panic. I get Errno=-16 for a while and it flakes.

In particular, I am looking for something to work at the install point.

---

### Post by indeed on 2008-05-23
Did you get this sorted?

It was a first boot rather than an install problem for me - dapper install detected the RAID and loaded the correct driver to install onto it, but then it didn't load that driver on first boot. I had to use the cd again to get in and put "dac90" in "/etc/modules." As far as I know the problem disappeared at some point between dapper and gutsy 'cause I've not got that line in modules any more.

If you know what module drives your hardware you could try appending it to the kernel options at boot.

Good luck.

---

### Post by okdok on 2008-05-23
Thanks for the inquiry, but no. I was not able to load Hardy or Fiesty. I have moved to another machine until a resolution can be found.

---

