---
title: "Cannot boot at all from ubuntu 8.04 i386 cdrom"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Zorgy on 2008-10-23
I simply cannot get started with ubuntu 8.04 (desktop). When I try to boot from the cd, install, or check cd consistency, it loads the kernel 100%, and then crashes, showing the cpu registers.

The only thing that works is the initial menu, and the memorytest.  

I've also tried ubuntu 8.04 64bits, 8.04 i386 server, 8.10 beta, and debian. More or less the same thing happens. It crashes as soon as it tries to do anything more than showing the inital boot menu from the cd. 

I've tried the same ubuntu 8.04 cd on a dell laptop (d820), and it booted just fine there, so I expect the cds to be okay. 

Windows XP runs fine on the computer. 

Quick specs of the computer:
- zalman hd160xt cabinet with built in touch screen.
- motherboard: msi 945gt speedster
- cpu: Intel t7200 core2 2GHz
- hardrive: samsung hd501LJ
- gfx: onboard (not used) and nvida geforce 7600 gs (in use)
- logitech bluetooth keyboard via bluetooth dongle
- ethernet pci card (in use)
- wireless pci card (not in use) 

I've tried searching for this problem alot, but all boot problems I seem to find is ppl already managed to install ubuntu. Could not find anything related to this in this forum either. 

I see some suggestions to disable acpi, but i struggle to find exactly how to do this. Pressing F6 in the ubuntu boot menu and adding acpi=off to the parameters does definately not help. Is this how it should be done?

So it seems that something about the hardware or bios just doesn't work for any linux. 

I'm pretty much stuck. 
The bios setup should be pretty clean. 

Help!

---

### Post by Zorgy on 2008-10-23
obtw, the message when it crashes before listing cpu registers is:

BUG int 6 cr2 0000000 

In debian is says unknown fault or interrupt.

---

### Post by Zorgy on 2008-10-30
Nobody able to help me out here?

---

### Post by integracd on 2008-10-30
I am having the same issue bump!!  I posted a thread on it as well using the 64bit version.

---

### Post by executorvs on 2008-10-30
did you try adding the command "pci=nomsi" to the boot line under F6?

---

### Post by Zorgy on 2008-10-30
the commandline ends with "--". Should I write this after that?
Didn't seem to help anyhow...

---

