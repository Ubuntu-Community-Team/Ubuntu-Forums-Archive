---
title: "Won't boot 32 bit installation from Hard Drive"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by rob18767 on 2017-01-20
I am reasonably green on the issue of Linux. However we have a 32 bit driver for some custom hardware we developed (PCI express) so we need to run a 32 bit version of Ubuntu/Linux. 

We had no problems when we used the Intel DN2800MT or Mitac PD11TI Mini ITX boards. However we have problems with the Mitac PD10BI Mini ITX board. 

The BIOS on the DN2800MT is
MDCDT10N.86A.0152.2012.0220.1510
UEFI fast boot disabled (legacy) with fast boot disabled.

PB10BI BIOS is
American Megatrends D7360A08
Legacy boot is chosen with fast boot chosen.

PD11TI BIOS is
MTCDT10N.85T.0201.2014.1209.1030
There is no option to select UEFI from BIOS menu.
 
First of all, the boards boot the 32 bit Ubuntu installer in legacy mode and the installer runs. This works on all three boards.

However after installation the PB10BI will not boot to Linux. After BIOS messages the processor seems active (Num Lock and ctrl-alt-del work on keypad), however the screen stays black.

If I swap a HDD flash drive from a board that boots to Ubuntu to the PB10BI it still hangs.

If I swap the HDD flash drive from the PB10TI after running the installer to one of the other two boards then Linux boots.

The main difference between the systems I see is the BIOS and the PB10TI has a faster Intel Celeron CPU as opposed to and Intel Atom on the other boards. 


Any suggestions as to why the PB10TI board does not boot 32 bit Ubuntu in legacy mode? 

Installation works in UEFI mode with 64 bit Ubuntu.

---

### Post by oldfred on 2017-01-20
UEFI fast boot assumes no hardware or system change. That speeds booting as then UEFI does not have to go thru an enumerate all the hardware and write that onto drive for operating system to use.

So when installing you need to have fast boot off.
And often fast boot is so quick that you do not have time to press a key to get into UEFI to change settings.

The 32 bit Ubuntu installer is BIOS only.
So if installing that on a newer UEFI motherboard, make sure Secure Boot is off and Legacy/CSM/BIOS setting is on.

---

