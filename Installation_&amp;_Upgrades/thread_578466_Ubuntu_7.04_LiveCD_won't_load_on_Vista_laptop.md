---
title: "Ubuntu 7.04 LiveCD won't load on Vista laptop"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by DeadToad on 2007-10-17
I have a HP Pavilion dv9000z laptop.  AMD 64 Athlon X2 1.73GHz Dual-Core TK-53 CPU. 2GB DDR2. Windows Vista Home Premium (HP) 32bit.
The CPU is a 64bit processor, I assume, while my OS is 32bit.

I cannot get Ubuntu Feistu Fawn v7.04 32bit or AMD64bit to run from the Live CD.
The 32bit runs from my WinXP laptop fine.

MUST the CPU and the OS both be 64bit for the AMD64 Live CD to boot?

I have tried "Alt-F1" and Ctrl-Alt-F1" at boot, but cannot get to a terminal window to type:
sudo dpkg-reconfigure xserver-xorg

I just get a black screen, without a blinking "_".  Nothing.  Nada.  Zilch.
Have tried loading into "Safe graphics mode", zilch.  Caputz.

Does anyone have any suggestions?
Thanks for your help.

---

### Post by logos34 on 2007-10-17
> **DeadToad said:**
> MUST the CPU and the OS both be 64bit for the AMD64 Live CD to boot?

No, that's not the issue.  Something else is preventing the livecd from booting.  

Rather than troubleshooting it to find the right kernel parameters/boot options it might be faster to download and try the text-mode Alternate CD.  Either 64- or 32-bit,

---

### Post by rje_nc on 2007-10-17
I have a Lenovo T60p that also will not boot from the LiveCD due to the ATI 5250GL graphics card installed.  I was able to install the basic system using the text mode installer and then manually install the ATI graphics support with an "apt-get install" command.

What graphics card do you have in your laptop?

---

### Post by Druke on 2007-10-17
on the boot options add 'noapic' and 'noalpic' works like a charm on my dv9000 ^_^. good luck also ndiswrapper works great on it ubuntuforum search for 'dell broadcom' (I know its hp but dell wifi card) anyways works like a charm.

---

### Post by DeadToad on 2007-10-17
Here's some system info:

Processor: 1.70 gigahertz AMD Athlon 64 X2 Dual Core TK-53
64 kilobyte primary memory cache
512 kilobyte secondary memory cache 

Main Circuit Board b: Board: Quanta 30B9 65.28

Bus Clock: 200 megahertz

BIOS: Hewlett-Packard F.37 05/31/2007

Drives: 120.03 Gigabytes Usable Hard Drive Capacity
79.29 Gigabytes Hard Drive Free Space
Optiarc DVD RW AD-7530A ATA Device [CD-ROM drive]
[Hard drive] -- drive 1: TOSHIBA MK1237GSX SCSI Disk Device (120.03 GB) -- drive 0

Memory Modules c,d: 958 Megabytes Installed Memory
Slot 'DIMM 1' has 512 MB (serial number 6FE019FB)
Slot 'DIMM 2' has 512 MB (serial number 6FE019E8)

Local Drive Volumes:
c: (NTFS on drive 0) 	111.26 GB 	77.42 GB free
d: (NTFS on drive 0) 	8.78 GB 	1.86 GB free

Network Drives: None detected

Controllers: ATA Channel 0 [Controller]
ATA Channel 1 [Controller]
NVIDIA nForce Serial ATA Controller
Ricoh Memory Stick Controller
Ricoh MMC Host Controller
Ricoh xD-Picture Card Controller
Standard Dual Channel PCI IDE Controller

Display: NVIDIA GeForce Go 6150 [Display adapter]
Generic PnP Monitor (17.2"vis)

Bus Adapters: Microsoft iSCSI Initiator
Standard Enhanced PCI to USB Host Controller
Standard OpenHCD USB Host Controller

Multimedia: Conexant High Definition Audio

Communications: HDAUDIO Soft Data Fax Modem with SmartCP
6TO4 Adapter
Bluetooth Device (Personal Area Network)
	Dhcp Server: 	none responded
	Physical Address:
Bluetooth Device (RFCOMM Protocol TDI)
Broadcom 802.11a/b/g WLAN
NVIDIA nForce Networking Controller
	Dhcp Server: 	none responded
	Physical Address:
Teredo Tunneling Pseudo-Interface

Other Devices: RICOH OHCI Compliant IEEE 1394 Host Controller
Microsoft AC Adapter
Microsoft ACPI-Compliant Control Method Battery
HP Bluetooth Module
Microsoft Bluetooth Enumerator
HID-compliant device
HP Quick Launch Buttons
HP Pavilion Webcam
HID Keyboard Device
Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Synaptics PS/2 Port TouchPad [Mouse]
SDA Standard Compliant SD Host Controller
USB Composite Device (2x)
USB Mass Storage Device
USB Printing Support
USB Root Hub (2x)
Generic volume shadow copy
Networking Dns Server

I'll try your suggestions.
Thanks again for your help.
DeadToad

---

### Post by DeadToad on 2007-10-17
Drake,
Adding "noapic" worked for me.
"noalpic" and "ndiswrapper" did not.
Thanks.

---

### Post by Druke on 2007-10-17
well no 'noapic' and 'noalpic' are the arguments used at the same time, if you got it right thats great. Ndiswrapper is a wifi driver once Ubuntu is installed.

---

