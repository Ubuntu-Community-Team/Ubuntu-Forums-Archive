---
title: "New info re blank screen at x64 7.1 install"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by UTGort on 2008-02-02
Like several others the install process is not working for me. I have tried the normal and alt installs. Both appear to hang at the beginning of the boot process. With the alt install it hangs at the message:

Kernal alive
Kernal direct mapping tables up to 180000000 @ 8000-f000


After waiting long enough to get bored I hit control+c. Then I get the message:
/build/buildd/cdebconf-0.117buildl/src/debconf.c:135 (main): Cannot initialize debconf template database

Anyone have any insites? My system is:

Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 CPUs), ~2.2GHz
 Memory: 5120MB RAM
 Video: NVIDIA GeForce 7300 GS
   Display Memory: 512.0 MB
    Current Mode: 1024 x 768 (32 bit) (75Hz)
 Description: Realtek HD Audio output
     Drive: C: (NTFS Win Xp x64)
     Free Space: 138.3 GB
     Total Space: 202.7 GB
      2 empty partitions 30 gb and 15 gb
      Drive: D:
      Model: HL-DT-ST DVD-ROM GDR8164B
      Drive: E:
      Model: SONY DVD RW AW-Q170A

---

### Post by UTGort on 2008-02-02
Found some more info. Decided to try the Command Line System install. This lets you see what is happening. Everything went OK up to the line:
Floppy drive(s): fd0 is 1.44m




That is where the system is hanging. I assume ( I know lol) that the next step is to check the hard drives.
I am using a 230G SATA drive WDC WD2500JS-60MHB5

---

### Post by UTGort on 2008-02-03
I found it. After playing with the  system for a while I thought it might be helped by command line options. The gparted live cd required that I run Forcevideo to start. So I was looking for equivalent commandline options. Reading the documentation led me to the Installation/32bitonAMD64 page. (Note that I have the 64 bit version.) That page gave me the command line options:
irqpoll pci=noacpi noapic nolapic acpi=off

Well it worked. Entering that allowed me to install using the graphical interface. Maybe it should be made standard for all amd installs.

---

