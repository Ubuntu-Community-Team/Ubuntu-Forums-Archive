---
title: "Ubuntu on a Dell"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by hamped on 2007-02-14
Hi all! 
I'm trying to start a Ubuntu live CD on my dell machine, but it will not start... I have tryed to write boot: live aic7xxx.aic7xxx=no_probe in the boot options. The specs for my Dell is:




Processor
Model : Intel(R) Pentium(R) 4 CPU 3.00GHz
Speed : 2.99GHz
Performance Rating : PR3741 (estimated)
Cores per Processor : 1 Unit(s)
Threads per Core : 2 Unit(s)
Internal Data Cache : 16kB Synchronous, Write-Thru, 8-way set, 64 byte line size, 2 lines per sector
L2 On-board Cache : 1MB ECC Synchronous, ATC, 8-way set, 64 byte line size, 2 lines per sector

Mainboard
Bus(es) : X-Bus PCI PCIe IMB USB i2c/SMBus
MP Support : 1 Processor(s)
MP APIC : Yes
System BIOS : Dell Inc. A03
System : Dell Inc. OptiPlex GX280
Mainboard : Dell Inc. 0G5611
Total Memory : 511MB DDR2-SDRAM

Chipset 1
Model : Dell Computer Corp 82915G/GV/GL/P/PL/GL Grantsdale Host Bridge/DRAM Controller
Front Side Bus Speed : 4x 200MHz (800MHz data rate)
Total Memory : 512MB DDR2-SDRAM
Memory Bus Speed : 4x 133MHz (532MHz data rate)

Video System
Monitor/Panel : Dell 1905FP (Digital)
Adapter : RADEON X300/X550 Series
Adapter : RADEON X300/X550 Series Secondary

Physical Storage Devices
Removable Drive : Diskettedrev
Hard Disk : ST380013AS (75GB)
CD-ROM/DVD : SAMSUNG CDRW/DVD SM-352F (CD 48X Rd, 32X Wr) (DVD 6X Rd)

Logical Storage Devices
Hard Disk (C:) : 74GB (18GB, 24% Free Space) (NTFS)
3.5" 1.44MB (A:) : N/A

Peripherals
Serial/Parallel Port(s) : 1 COM / 1 LPT
USB Controller/Hub : Intel(R) 82801FB/FBM USB Universal Host Controller - 2658
USB Controller/Hub : Intel(R) 82801FB/FBM USB Universal Host Controller - 2659
USB Controller/Hub : Intel(R) 82801FB/FBM USB Universal Host Controller - 265A
USB Controller/Hub : Intel(R) 82801FB/FBM USB Universal Host Controller - 265B
USB Controller/Hub : Intel(R) 82801FB/FBM USB2 Enhanced Host Controller - 265C
USB Controller/Hub : USB-rodhub
USB Controller/Hub : USB-rodhub
USB Controller/Hub : USB-rodhub
USB Controller/Hub : USB-rodhub
USB Controller/Hub : USB-rodhub
USB Controller/Hub : Standard USB-hub
USB Controller/Hub : USB-sammensat enhed
USB Controller/Hub : USB-sammensat enhed
USB Controller/Hub : USB-sammensat enhed
USB Controller/Hub : USB-sammensat enhed
Keyboard : HID-tastaturenhed
Mouse : HID-kompatibel mus
Mouse : HID-kompatibel mus
Human Interface : HID-kompatibel enhed
Human Interface : HID-kompatibel brugerkontrolenhed
Human Interface : USB-brugerstyret inputenhed (HID)
Human Interface : USB-brugerstyret inputenhed (HID)
Human Interface : USB-brugerstyret inputenhed (HID)
Human Interface : USB-brugerstyret inputenhed (HID)

MultiMedia Device(s)
Device : SoundMAX Integrated Digital Audio

Printers and Faxes
Model : Microsoft Office Document Image Writer
Model : Amyuni PDF Converter

Power Management
AC Line Status : On-Line

Operating System(s)
Windows System : Microsoft Windows XP/2002 Professional 5.01.2600 (Service Pack 2)

Network Services
Adapter : Belkin 11Mbps Wireless Desktop Network Card
_________________________________________________


What to do now? Will Ubuntu work with my Dell?

---

### Post by aysiu on 2007-02-14
When you say it will not boot, what exactly happens? Do you get an error? Is it just a black screen? Are you able to type anything?

By the way, which version of the live CD are you using?

P.S. I removed your other duplicate thread. One issue, one thread. Makes it less confusing for everyone trying to help you.

---

### Post by hamped on 2007-02-14
Thx aysiu for deleting that thread. Saw too late the installation section :)

downloaded ubuntu-6.10-desktop-i386 just three days ago. As i turn on the computer and press run or install ubuntu it just says loading in the upper left corner.  Comp not repsonding to anything until i press alt+ctrl+del.

---

### Post by aysiu on 2007-02-14
It could possibly be a bum CD--corrupted during download or burn.

Did you do a checksum and burn the ISO at a slow  speed?

More details here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by hamped on 2007-02-14
Checksum was fine. Trying another burn at low speed.

---

### Post by hamped on 2007-02-14
Another burn was a failure. It just says "loading" in the upper left corner?

---

### Post by hamped on 2007-02-14
Should i use ubuntu-6.10-alternate-i386.iso instead?

---

### Post by bollix47 on 2007-02-14
I had a similar problem with a Dell and found that I had to go into the bios and up the video memory from 1 to 8.

It looks like your setting is at 1 as you are reporting 511 megs of ram.

Hope it works for you.

---

### Post by hamped on 2007-02-14
Thx for the advise but it didn't work :(

---

### Post by revmc on 2007-02-14
I am relative newcomer.  I use a Dell Precision M60 (basically a glorified Latitude D400) and have had no problems with loading 6.10.

I am unclear how you access the iso disk.  On mine when the Dell Logo comes on I press F12 to lo access the DVD/CD rom where the 6.10 disk is and press enter.  The program automatically comes on and ask if I want to run it.  

I have had bad iso burns on certain cds.  Usually, as was stated above, the program disk is the problem.

Revmc

---

### Post by hamped on 2007-02-14
I press f12 during boot and get to the part where it says start or install ubuntu. But i don't get any further.

---

### Post by Brattbakkk on 2008-03-12
> **hamped said:**
> I press f12 during boot and get to the part where it says start or install ubuntu. But i don't get any further.

I get the same on a Dell Latitude D400 where it goes thru the loading proceedure all the way to an orange background screen where I even get the music, although it stutters, then nothing but the CD continually running as if it still loading but nothing.

I can load the same CD onto a Dell Dimension no problem.

Can anyone help?


I am using 7.10

---

