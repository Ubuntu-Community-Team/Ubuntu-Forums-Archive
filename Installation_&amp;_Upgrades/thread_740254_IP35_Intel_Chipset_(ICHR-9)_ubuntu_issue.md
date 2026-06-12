---
title: "IP35 Intel Chipset (ICHR-9) ubuntu issue"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by Maintech on 2008-03-30
I have posted this before but it was moved to "other OS" because I mentioned that no Debian based OS would run on this computer. Ubuntu IS Debian based. And I am addressing Ubuntu, not Debian.

I have an Abit IP35 motherboard, 4 gig of Buffalo DDR-2 667MHz ram, Nvidia 8800 GTS, 4 Maxtor SATA drives, Lite-On DVD burner, and a floppy drive. The motherboard has 6 SATA ports. I have an Intel Q6600 Quad Core processor. I generally try to install a 64 bit OS but with Ubuntu it doesn't matter if it is 64 or 32 bit. I get the same results. I get the same with every Debian based OS I have tried on this motherboard so I have to believe that any OS built on Debian (This IS Ubuntu) will have this issue. Other linux OS built from Red Hat base (RPM types like Mandriva, SuSE, PCLinuxOS) will install and run ok. Just not Ubuntu and Ubuntu is my preferred linux OS. This is an issue that has been reported in this forum since the IP35 Intel chipset was released. This is what I have happen when I am trying to boot the live CD.

I get to the part where I choose the boot or installl method (and I have tried them all and tried IRQ=nopoll, and noapic among many others and none works) and the system starts to check and configure the system. I usually watch the loading process. When loading SuSE or Mandriva I reach the part where it identifies the Hard drive controller as ICHR-9 and they will load the 4-port driver first then load the 2 -port driver and go on and boot. In Ubuntu it will try to load the 2-port driver, will not be able to do so then will try all kinds of other drivers but never the 4-port. When it tries and fails on ALL the drivers it will loop back to the 2-port and start again and go through the entire list again. Over and over in a loop. Every version I have tried (of Ubuntu including Hardy) does this. Why has Ubuntu not fixed this issue since it is working in other linux distros? In one of the forum posts this is mentioned and someone posted that this is a kernel issue. I have no idea myself but it seems that if SuSE and Mandriva can make the chipset work correctly that Ubuntu should be able to also. I am posting this from SuSE 10.3 now. The thing is, I don't want SuSE 10.3. I want Ubuntu to work.

---

### Post by Pumalite on 2008-03-30
I have Ubuntu Hardy Heron Beta 64 bit installed on a system similar to yours. Only Intel x38 which is similar to P35. If you can afford an unstable system in development; take it for a spin.

---

### Post by Maintech on 2008-03-30
> I have Ubuntu Hardy Heron Beta 64 bit installed on a system similar to yours. Only Intel x38 which is similar to P35. If you can afford an unstable system in development; take it for a spin.

I have already tried and it does exactly what I posted. It tries to load the 2-port SATA driver and goes into an endless loop.

---

### Post by king vash on 2008-03-31
> **fjf said:**
> I remember there was a problem with the ata controler in this board (Jmicron or something ).  That's why I got a SATA DVD and SATA HDD.  And yes, the SATA HDD only works in AHCI mode, whatever that is :)

this worked for me

---

### Post by QuantumAvatar on 2008-04-18
Dont know if i fully understood your problem but the SATA 1-4 are overloaded and ubuntu doesnt like that. If you only use SATA ports 5,6 everything should work fine. I had a problem like this i believe.

---

