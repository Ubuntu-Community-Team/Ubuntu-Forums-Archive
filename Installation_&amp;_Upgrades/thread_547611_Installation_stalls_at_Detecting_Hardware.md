---
title: "Installation stalls at Detecting Hardware"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by lizanddogs on 2007-09-10
Hi,

I am trying to install Ubuntu 7.04 Server (alternate CD) on my HP Pavilion 540n.

I was able to get the install to start using:
debian-installer/framebuffer=false
turning off the usb detection - I forget the debian-installer option - but I pulled it from the documentation and it worked.

I've added 1gb RAM in slot 1 leaving the older 256mb RAM in slot 2
The DVD/CD-ROM drive is an HP DVD 1040i
Two IDE drives are installed internally - the original 40gb drive and a 60gb drive
I have a 500gb USB external drive which I switched off for this install -- attached to a Ultra 7 Firewire/USB card

The keyboard and mouse are both older PS/2

I checked the .iso with the MD5 utility

The install hangs up at 0% at Detecting Hardware.   The motherboard specs follow.

Help would be appreciated.

Thanks

Motherboard description   	

    * Manufacturer's name - ASUS P4S333-M
    * HP/Compaq name - Missouri

Motherboard supplier 	ASUS
System BIOS supplier 	Asus Award
Form factor 	UATX
Processor brand 	Intel
Processor socket type 	MPGA478
Processor family 	Pentium® 4 (Willamette, Northwood)
Processor front side bus frequency 	400 MHz
Chipset name 	SiS650
Chipset "North Bridge" 	SiS650
	Revision/Stepping 	A1
Chipset "South Bridge" 	SiS961
	Revision/Stepping 	A2
Super I/O 	ITE
	Revision/Stepping 	IT8707
Flash BIOS device 	2MB Flash EEPROM
Memory type 	DDR
Memory speed 	PC2100 / PC1600
Memory sockets 	2 DIMM
Maximum memory 	2GB
Graphics supplier 	Graphic Card
Graphics configuration 	Up/Down
Onboard graphics memory 	N/A
Graphics connector (AGP) 	AGP 4X
TV-out device 	No
TV-out configuration 	AGP TV Out Card
Audio 	AC97 Down
AC’97 CODEC device 	ADI1885
Audio jacks (legend below) 	M, LI, LO, SO, M/G
	M 	Microphone
	LI 	Line In
	LO 	Line out
	SO 	Speaker
	M/G 	Midi/Game
Ethernet 10/100 LAN supplier 	SiS 961+PHY ICS 1893
Ethernet configuration 	Integrated Down
IDE UDMA modes 	Supports UDMA 100/66/33 - requires a 40 pin/80 conductor cable for UDMA 66 and 100 disk drives
Expansion slots (AGP/PCI/Exten) 	1 AGP, 3 PCI
USB ports 	6
USB front/back options 	2F + 2 B +2 on connector
Serial, parallel, floppy, PS2 Kbd and mouse 	2S, 1P, !F, PS2 K+M

---

### Post by Pumalite on 2007-09-10
What does your BIOS say about your memory?. Maybe those 256 Ram are in the middle.

---

### Post by lizanddogs on 2007-09-10
The bios says 1028mb of memory.   I had Windows XP Pro up and running fine on the system.  I just want to dump MS Windows and make this my home Linux server installation.

I have two laptops - one MacBook Pro and one Toshiba running Windows XP media edition.   I work at home a lot and usually use (although I'm no expert by any means) Linux Fedora Core 4 at work.   I'd like to be able to run the same programs and simple scripts at home.

I have not tried the noacpi options yet.  I'm going to try that next.

Thanks

---

### Post by Pumalite on 2007-09-10
If BIOS says 1028MB it's not recognizing the 256 stick and it might be bothering Ubuntu. Why don't you remove it and see. ( 1 GB=1024)

---

### Post by lizanddogs on 2007-09-10
Well I was wrong about that.   I'm operating in two different rooms and simply forgot the correct number between them - old age.

The system is seeing 1280mb of memory which is the correct amount.

It hangs up for a while at detecting hardware to find CD-ROM drives,  eventually (because I walked out to go do something else) it gives me a list of hardware modules it will load based on what it detects....  now it is there that it hangs up at 6% of whatever the first module is it tries to install.

I tried the noacpi option and it never got to the menu beyond the first screen.

What to try next ?

Thanks.

---

### Post by Pumalite on 2007-09-10
Go to BIOS>IDE Configuration>Set it to 'Enhanced Support for PATA+SATA' and let's see. I still have other things up my sleeve.

---

### Post by lizanddogs on 2007-09-10
My BIOS doesn't have that option.   My computer is about 4-5 years old - this is before SATA.

---

### Post by Pumalite on 2007-09-10
Next step is to set CD-DVD drive in your computer as 2nd Master and 'Auto' in BIOS

---

