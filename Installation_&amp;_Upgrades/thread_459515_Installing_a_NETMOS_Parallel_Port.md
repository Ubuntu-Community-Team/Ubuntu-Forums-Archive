---
title: "Installing a NETMOS Parallel Port"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by distracted on 2007-05-30
Hello....  New to the forum and Ubuntu...  Looking forward to the experience!  Hope someone can help me.

I was given the flollwing instructions fron the parallel port vendor.  I cannot get "insmod parport.o" to work! to load the generic 'parport' code. nor "more /proc/pci".  Am I missing something here???....  

I am running v6.06 and using the Netmos Nm9805CV parallel.

Help!  Eric

*************************************

Installation Guide for PCI Parallel Ports 



This installation guide describes the procedure to install the Nm9705CV, Nm9735CV, Nm9805CV, Nm9715CV, Nm9835CV, Nm9755CV PCI parallel ports in Linux platform.



Linux kernel provide a 'parport' code to support parallel port (/dev/lp0,  /dev/lp1, /dev/lp2). This code provides the ability to share one port between multiple devices. And it is loadable when kernel is running.



The 'parport' code is split into two parts : generic (which deals with port sharing) and architecture-dependent eg. X86, SPARC. (which deals with actually using the port). Thus, please take the following steps to install 'parport' module!



Check the on-board parallel port's hardware resources



Most likely each motherboard has a built-in parallel port. And its hardware resources are settable with BIOS utility.



Enter the command  more  /proc/pci



The response is similar to the following

      

			Bus 0, Device 11, function 0:

			Serial controller : Unknown vendor Unknown device (rev 01).

			Vendor id=9710, Device id=9705

					Device id=9735

					Device id=9805

					Device id=9815

					Device id=9835

					Device id=9855



			Medium devsel. Fast back-to-back capable. IRQ 11

			

			Board with Nm9705CV part

			I/O at 0xc000 [0xc001]	printer port

			       0xc008 [0xc009]	ECP/EPP config registers



			Board with Nm9735CV part

			I/O at 0xc000 [0xc001]	not used

			       0xc008 [0xc009]	not used

			       0xc010 [0xc011]	printer port

			       0xc018 [0xc019]	ECP/EPP config registers

			

			Board with Nm9805CV part

			I/O at 0xc000 [0xc001]	printer port

			I/O at 0xc400 [0xc401]	ECP/EPP config registers

			I/O at 0xc800 [0xc801]	not used

			I/O at 0xd000 [0xd001]	not used

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used



			Board with Nm9715CV part

			I/O at 0xc000 [0xc001]	printer port 1

			I/O at 0xc400 [0xc401]	ECP/EPP config registers 1

			I/O at 0xc800 [0xc801]	printer port 2

			I/O at 0xd000 [0xd001]	ECP/EPP config registers 2

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used



			Board with Nm9835CV part

			I/O at 0xc000 [0xc001]	not used

			I/O at 0xc400 [0xc401]	not used

			I/O at 0xc800 [0xc801]	printer port

			I/O at 0xd000 [0xd001]	ECP/EPP config registers

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used



			Board with Nm9755CV part

			I/O at 0xc000 [0xc001]	printer port 1

			I/O at 0xc400 [0xc401]	ECP/EPP config registers 1

			I/O at 0xc800 [0xc801]	printer port 2

			I/O at 0xd000 [0xd001]	ECP/EPP config registers 2

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used




Install 'parport' module



To load the generic 'parport' code



Type 			insmod parport.o

         

To load the architecture-dependent code to tell 'parport' code



			insmod parport_pc.o  io=0x378,0xc000,0xc800

			irq=7, irq=11, none

			

			or



			insmod parport_pc.o  io=0x378,0xc000,0xc800

			irq=7,11,none	

		

You have three PC-style ports, one at 0x378 with IRQ 7, one at

0xc000 with  IRQ11, one at 0xc800 with no IRQ.





Check the attached printer device [optional]



Once the architecture-dependent part of the paraport code is loaded into the kernel. You could enter the following command 



 			insmod parport_probe.o 



To check any attached devices and log a message similar to



			parport0: Printer, epson




Then 			/dev/lp0, /dev/lp1 and /dev/lp2 are ready for service

---

### Post by distracted on 2007-05-30
Looks Like I have success!  Found the follwing for anyone else loking...

4. Can you provide Linux Source Code for MCS98XX?
   There is no Linux driver/source code for MCS98XX. You have to manually
   configure the ports on Linux. Please use the following steps:
       •   setserial /dev/ttyS2 port 0xecf8 UART 16550A irq 10 Baud_base 115200
       •   setserial /dev/ttyS3 port 0xece8 UART 16550A irq 10 Baud_base 115200
       **•   /sbin/modprobe parport_pc io=0x3f8,0xecd8 irq=4,10**
   Note: Use the appropriate IRQ number as per your system.
   For the complete details, refer to “Read me” file which is available on our website.
   It can be downloaded from the following link:
   [http://www.moschip.com/html/download_drivers.html](http://www.moschip.com/html/download_drivers.html)

---

