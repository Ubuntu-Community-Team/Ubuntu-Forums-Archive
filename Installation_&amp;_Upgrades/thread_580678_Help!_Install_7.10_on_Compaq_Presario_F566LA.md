---
title: "Help! Install 7.10 on Compaq Presario F566LA"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by pitbullcarfc on 2007-10-19
Since version 7.04 i'd tried to install ubuntu but it ends the same way, ubuntu's loading screen and then blank screen where is supoused to be the logon screen. I was hopping 7.10 have no problem, but the same happens.

Anyone can help me?

I also tried thing from other forums (like adding vga=... option to the boot line, works for the live cd on 7.04, but not on grub line or 7.10 live cd)

Compaq specs. from everest ultimate edition 4.20.1170 (trial)

Computer:
	Computer Type  	Based ACPI x86 (Mobile)
	Operating System  	Microsoft Windows Vista Home Basic
 
Motherboard:
	CPU Type  	Mobile AMD Turion 64 MK-38, 2200 MHz (11 x 200)
	Motherboard Name  	Hewlett-Packard Presario F500 (GM639LA#ABM)
	Motherboard Chipset  	nVIDIA GeForce Go 6100, AMD Hammer
	BIOS Type  	Phoenix (05/25/07)
 
Display:
	Video Adapter  	NVIDIA GeForce Go 6100 (64 MB)
	3D Accelerator  	nVIDIA GeForce Go 6100
	Monitor  	Monitor PnP generic [NoDB]
 
Multimedia:
	Audio Adapter  	Conexant Cx20549 @ nVIDIA nForce 430 (MCP51) - High Definition Audio Controller
 
Storage:
	IDE Controller  	Double channel standar controller PCI IDE
	IDE Controller  	NVIDIA nForce Serial ATA Controller
	Storage Controller  	Iniciador iSCSI de Microsoft
	Disk Drive  	Hitachi HTS541612J9S SCSI Disk Device (111 GB)
	Optical Drive  	Optiarc DVD RW AD-7530A ATA Device (DVD+R9:4x, DVD-R9:4x, DVD+RW:8x/8x, DVD-RW:8x/6x, DVD-RAM:5x, DVD-ROM:8x, CD:24x/24x/24x DVD+RW/DVD-RW/DVD-RAM)
 
Input:
	Keyboard  	Dispositivo de teclado HID
	Keyboard  	Teclado estándar de 101/102 teclas o Microsoft Natural PS/2
	Mouse  	Synaptics PS/2 Port TouchPad
 
Network:
	Network Adapter  	NVIDIA nForce Networking Controller
	Network Adapter  	WLAN Broadcom 802.11b/g
	Modem  	HDAUDIO Soft Data Fax Modem with SmartCP
 
Peripherals:
	USB1 Controller  	nVIDIA nForce 430 (MCP51) - OHCI USB 1.1 Controller
	USB2 Controller  	nVIDIA nForce 430 (MCP51) - EHCI USB 2.0 Controller
	Battery  	Adaptador de CA de Microsoft
	Battery  	Batería con método de control compatible con ACPI de Microsoft
 
DMI:
	DMI BIOS Vendor  	Hewlett-Packard
	DMI BIOS Version  	F.17
	DMI System Manufacturer  	Hewlett-Packard
	DMI System Product  	Presario F500 (GM639LA#ABM)
	DMI System Version  	Rev 1
	DMI Motherboard Manufacturer  	Quanta
	DMI Motherboard Product  	30D3
	DMI Motherboard Version  	65.37
	DMI Chassis Manufacturer  	Quanta
	DMI Chassis Version  	N/A
	DMI Chassis Type  	Notebook

---

### Post by Lord Landis on 2007-10-19
> Motherboard:
CPU Type Mobile AMD Turion 64 MK-38, 2200 MHz (11 x 200)

Are you installing the generic/386 version, or the 64-bit version?  With that CPU, I'd think the 64-bit version would work better.

Can you get into a recovery console through GRUB?  If so, try re-configuring X and see if that fixes your problem.  Code:

```
sudo dpkg-reconfigure xserver-xorg
```

I recommend trying a fail-safe graphics configuration at first, like 640x480 (maybe 800x600) w/ 8-bit color just to see if you can get it up and running.  If so, from there you can tweak the settings to get your display looking good again.

I had a similar issue on my laptop this morning (Dell Inspiron 4100), and thought it crapped out after the loading splash, but when I used the touchpad a little, the login screen showed up right away.

There shouldn't be any hardware in that list that's causing a major problem.

---

### Post by mamaolo on 2007-10-19
I am going to install 7.10 version just today, when finished the downloading.
I used 7.04 several months in my Presario F566LA without any problem, just adding "acpi=force vga=774" to the second line of the grub booting option. First time I edit it during booting the grub line, but after that just edit "menu.lst" file in the /boot/grub directory, and after that anything works fine.
Tomorrow I will tell you my experience with 7.10, but i am thinking to use the same idea.
Yours.
MPA

---

### Post by oddchild on 2007-10-21
i got the same problem... i  got it to load... but the broadcom wireless, although availible in the restricted drivers... doesnt work. it just says "fatal" error, when starting up... 

i tried using ndiswireless for it too, doesnt make a difference. 

nvidia works fine with 7.10 though :)

---

