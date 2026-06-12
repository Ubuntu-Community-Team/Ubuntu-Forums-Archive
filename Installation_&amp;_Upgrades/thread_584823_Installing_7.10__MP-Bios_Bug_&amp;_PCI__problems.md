---
title: "Installing 7.10 : MP-Bios Bug &amp; PCI  problems"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by fuligin on 2007-10-21
HI, 
I just installed 7.10 on my Thinkpad R51e, and seem to have the following errors at startup
MP-Bios Bug 8254 Timer Not connected to IO-ACPI. 
Additionally I get PCI cannot allocate resources ( I assume this is for my  Artheros wifi which also isnt working)

when using the live disk it tells me that it cant find the support directory for manufacturers ACPI Library. 

It takes about 10 -15 minutes for splash screen to appear and login to desktop. 

Additionally I can see wireless networks but i cant connect to them at all once I enter wpa password. ( this worked fine in Fiesty)

Any help would be much apprichtated

---

### Post by Z_Cee on 2007-10-21
I have the exact same problem with *M-Bios Bug: 8254 timer not connected to IO-APIC* on my Toshiba A75 laptop when installing Gutsy.

The last couple version of Ubuntu I had problems with ACPI and now it's APIC I'm having problems with...

---

### Post by fuligin on 2007-10-22
I tried to load with dapper live cd and its still telling me that there is an missing apci directory. 
I found thinkpad-apci page but i have no clue how to install it and if i really need to install it. ?
I wish I could get this solved. right about now I dont care if its gutsy, fiesty or even dapper. Unless I get this apci problem fix i will have a very hard time starting up.  :(.

---

### Post by diskotek on 2007-10-22
i had that error also with edgy and also with feisty... adding "nosplash"  ddint worked me

---

### Post by &#1084;&#1072;&#1083;&#1080;&#1115; on 2008-01-26
> **fuligin said:**
> HI, 
I just installed 7.10 on my Thinkpad R51e, and seem to have the following errors at startup
MP-Bios Bug 8254 Timer Not connected to IO-ACPI. 

I have the same problem on Thinkpad R51e (with Ubunt 7.04)!

> **fuligin said:**
> It takes about 10 -15 minutes for splash screen to appear and login to desktop. 


Maybe this can help you:

[http://ubuntuforums.org/showthread.php?t=475112&highlight=thinkpad+r51e](http://ubuntuforums.org/showthread.php?t=475112&highlight=thinkpad+r51e)

---

