---
title: "[SOLVED] Help! Live CD Hard Disk Wireless Network Not Detected"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by kishorebudha on 2008-06-30
Hi,

On the following system:

Asus P5B-VM SE (Bios Updated to latest version 9063)
Core2 Quad Q6600
Zotac Nvidia 8500GT
4GB Memory

Live CD loads fine, but does not detect Hard Disk or Wireless Card (Marvel 88W8335).

Thanks

---

### Post by kishorebudha on 2008-06-30
> **kishorebudha said:**
> Hi,

On the following system:

Asus P5B-VM SE (Bios Updated to latest version 9063)
Core2 Quad Q6600
Zotac Nvidia 8500GT
4GB Memory

Live CD loads fine, but does not detect Hard Disk or Wireless Card (Marvel 88W8335).

Thanks

[B]Also, The Hard Disk is IDE

[/B]

---

### Post by untermensch on 2008-06-30
What do you mean by it doesn't detect it? Are you trying to partition or just look at stuff?

---

### Post by kishorebudha on 2008-06-30
> **untermensch said:**
> What do you mean by it doesn't detect it? Are you trying to partition or just look at stuff?

I am trying to install Ubuntu. I tried with various versions of Ubuntu 8.04 32bit/64bit, Ubuntu Studio 8.04, no luck.

---

### Post by untermensch on 2008-06-30
It's not showing any drives? or it's not showing free\used space?

---

### Post by kishorebudha on 2008-07-01
> **untermensch said:**
> It's not showing any drives? or it's not showing free\used space?

It does not show any of the drives. None at all. So I am unable to install Ubuntu. The Wireless card does not show up either. When I do a hardware scan, it does report the Marvel 88W8335 Wireless Card, though a wireless network does not show up.

---

### Post by kishorebudha on 2008-07-01
The motherboard uses a JMicron controller. I wonder if that is the cause? This is so frustrating as I have had an absolutely smooth install on my laptop Inspiron 6000.

---

### Post by untermensch on 2008-07-01
You could try the alt. cd. It tends to be better at finding bad hardware. If you want to try that just go to ubuntu.com, and find the page were you would download the iso, and at the bottom of the page is a box you can check to get the alt cd (it'll have a few sentences beside the box telling you this). 

Your wireless card probably needs drivers. so yes it can be detected, but no it wont give you a wireless signal yet.

---

### Post by kumarnarain on 2008-07-01
Pls post your BIOS settings...may be you should try with acpi turned off...

---

### Post by kishorebudha on 2008-07-01
> **kumarnarain said:**
> Pls post your BIOS settings...may be you should try with acpi turned off...

**I tried with ACPI turned off -- no luck. **

My lspci looks like this:

[INDENT]00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/INDENT]

My BIOS is as follows:

**1) MAIN**
SATA 1: [Not Detected]
SATA 2: [Not Detected]
SATA 3: [Not Detected]
SATA 4: [Not Detected]

IDE CONFIG
SATA#1 Configuration [Enabled]
SATA#2 Configuration [Enabled]
Hard Disk write protect [Disabled]
IDE Detect Timeout (Sec) [35]
JMB368 Controller [Enabled]

SYSTEM INFO
Amibios 0903
Build Date 03/03/08

PROCESSOR
Type: Intel (R) Core2 Quad Q6600@2.40GHz
Speed: 2400MHz

SYSTEM MEMORY
Available: 3072 MB

**2) ADVANCED**

Jumper free Configuration [Standard]
USB Configuration
[INDENT]   USB Functions [10 USB Ports]
   Legacy USB Support [Auto]
   USB 2.0 Controller Mode [Hispeed]
   BIOS EHCI Hand off [Enabled][/INDENT]
CPU CONFIGU
[INDENT]   CPU Ratio Setting [Auto]
   C1E Support [Enabled]
   MAX CPUID Value Limit [Disabled]
   Vanderpool Tech [Enabled]
   CPU TM Function [Enabled]
   Execute Disable Bit [Enabled]
   EIST [Enabled][/INDENT]
CHIPSET/Northbridge
   [INDENT]Memory Remap [Disabled]
   DRAM Frequency [800MHz]
   Config DRAM timing by SPD [Enabled]
   Memory Hole [Disabled]
   DRAM in mode select [Disabled]
   Initiate graphic adapter [PEG/PCI]
   Internal Graphics mode select [Enabled 8 MB]
   PEG Port [Auto]
   PEG Force x1 [Disabled][/INDENT]
CHIPSET/Southbridge
   [INDENT]Onboard LAN [Enabled]
   Onboard LAN Boot ROM [Disabled]
   HD Audio Controller [Enabled]
   Front Panel support type [HD Audio][/INDENT]
Onboard Devices Configuration
   [INDENT]Serial Port 1 Address [3FG/IRQ4]
   Parallel Port Address [378]
   Parallel Port Mode [ECP]
   ECP Mode DMA Channel [DMA3]
   Parallel Port IRQ [IRQ7][/INDENT]
PCIPnP
   [INDENT]Plug and play O/S [No]
   PCI Latency timer [64]
   Allocate IRQ to PCI VGA [Yes]
   Palette Snooping [Disabled]
   IRQ-3 assigned to [PCI DEV]
   IRQ-4 assigned to [PCI DEV]
   IRQ-5 assigned to [PCI DEV]
   IRQ-7 assigned to [PCI DEV]
   IRQ-9 assigned to [PCI DEV]
   IRQ-10 assigned to [PCI DEV]
   IRQ-11 assigned to [PCI DEV]
   IRQ-14 assigned to [PCI DEV]
   IRQ-15 assigned to [PCI DEV][/INDENT]

**3) POWER**
Suspend Mode [Auto]
ACPI Version Features [ACPI v1.0]
ACPI APIC Support [Enabled]

---

### Post by upchucky on 2008-07-01
you can fix this without knoppix but if you can, get it to find/fix hard drive issue, the wireless card info may be on the hard drive so that explains that part. knoppix will fix broken windows and Linux install errors from the live cd.

get supergrub to make a supergrub live floppy, cd, dvd, or usb rescue. (all of the types will work)  use it to find/repair drive info for grub.

---

### Post by kishorebudha on 2008-07-01
> **upchucky said:**
> you can fix this without knoppix but if you can, get it to find/fix hard drive issue, the wireless card info may be on the hard drive so that explains that part. knoppix will fix broken windows and Linux install errors from the live cd.

get supergrub to make a supergrub live floppy, cd, dvd, or usb rescue. (all of the types will work)  use it to find/repair drive info for grub.

I haven't even been able to install Ubuntu to begin with... I can boot Windows XP, which has already been installed. :)

---

### Post by upchucky on 2008-07-01
thats why you need Knoppix and supergrub to get the drive info for ubuntu to use to start the install.

I have yet to see a sys that Knoppix cant find info for especially the hard drives.

the intent is to find the drive problem then when that is solved, use that info to manual install and if ubuntu and/or windows wont boot fix that with supergrub.

---

### Post by avtolle on 2008-07-01
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) generally discusses the use of boot options, and how to use them. I'd suggest use of one not listed in the link, all_generic_ide implemented as detailed in the link at boot from the Live CD to see if you can get to installation.

---

### Post by kishorebudha on 2008-07-01
I removed the jumper from the hard disk (western digital 160GB, 10 pin drive) and the disk was detected. Earlier it was set to master. Now to see if plugging in the SATA drive causes any problems with XP!!!! I am expecting SATA cables tomorrow. Will keep this thread updated...

**And THANKS everybody for your support and patience**

---

