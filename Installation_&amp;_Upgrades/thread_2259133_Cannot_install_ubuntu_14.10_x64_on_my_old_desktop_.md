---
title: "Cannot install ubuntu 14.10 x64 on my old desktop PC"
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by Roey_Peretz on 2015-01-02
Hi,

When I try to install it from a USB device it passes the selection screen and crashes at the installation from the LiveOS (RAM).
When I try to install it from a CD it doesn't even gets to the selection screen.

I try to install it side by side with windows 7 x64.
Attached are the complete hardware specifications and screener from a crash boot from CD.

THNX
Roey

---

### Post by mikewhatever on 2015-01-02
Why the spec.zip? Can't you just post the specs in the original?

---

### Post by Bucky Ball on 2015-01-02
Welcome. You have created free space to install it to? If you need to shrink the Win partition, do that with the Win tool in Win 7, NOT with Gparted in the Live boot of Ubuntu.

---

### Post by Roey_Peretz on 2015-01-02
Alright, Here is the summary:

--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Computer Type                                     ACPI x64-based PC
      Operating System                                  Microsoft Windows 7 Ultimate
      OS Service Pack                                   Service Pack 1
      Internet Explorer                                 9.11.9600.17207
      DirectX                                           DirectX 11.0
      Computer Name                                     DVIR-PC
      User Name                                         Dvir
      Logon Domain                                      Dvir-PC
      Date / Time                                       2002-01-09 / 13:46

    Motherboard:
      CPU Type                                          DualCore AMD Athlon 64 X2, 2200 MHz (11 x 200) 4200+
      Motherboard Name                                  Asus A8N-VM CSM  (2 PCI, 1 PCI-E x1, 1 PCI-E x16, 4 DDR DIMM, Audio, Video, Gigabit LAN, IEEE-1394)
      Motherboard Chipset                               nVIDIA GeForce 6150, AMD Hammer
      System Memory                                     3008 MB  (PC3200 DDR SDRAM)
      DIMM1: Corsair XMS CMX512-3200C2                  512 MB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)  (2.0-2-2-6 @ 133 MHz)
      DIMM2: Corsair XMS CMX512-3200C2                  512 MB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)  (2.0-2-2-6 @ 133 MHz)
      DIMM3: Kingston K                                 1 GB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)
      DIMM4: Kingston K                                 1 GB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)
      BIOS Type                                         AMI (10/05/05)
      Communication Port                                Communications Port (COM1)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     RADEON X800 GT (Microsoft Corporation - WDDM)  (256 MB)
      Video Adapter                                     RADEON X800 GT (Microsoft Corporation - WDDM)  (256 MB)
      3D Accelerator                                    ATI Radeon X800 GT PCI-E (R423)
      Monitor                                           Samsung SyncMaster 2243BW/2243BWX/MagicSyncMaster CX2243BW/CX2243BWX (Digital)  [22" LCD]  (HVLQ203757)

    Multimedia:
      Audio Adapter                                     Analog Devices AD1986A @ nVIDIA nForce 430 (MCP51) - High Definition Audio Controller

    Storage:
      IDE Controller                                    Standard Dual Channel PCI IDE Controller
      Storage Controller                                NVIDIA nForce Serial ATA Controller
      Storage Controller                                NVIDIA nForce Serial ATA Controller
      Storage Controller                                Virtual CloneDrive
      Floppy Drive                                      Floppy disk drive
      Disk Drive                                        SanDisk U3 Cruzer Micro USB Device  (979 MB, USB)
      Disk Drive                                        WDC WD16 00JS-00MHB0 SCSI Disk Device  (160 GB, 7200 RPM, SATA-II)
      Optical Drive                                     ELBY CLONEDRIVE SCSI CdRom Device  (Virtual CD-ROM)
      Optical Drive                                     HL-DT-ST DVDRAM GH24NS95 SCSI CdRom Device  (DVD+R9:8x, DVD-R9:8x, DVD+RW:24x/8x, DVD-RW:24x/6x, DVD-RAM:5x, DVD-ROM:16x, CD:48x/24x/48x DVD+RW/DVD-RW/DVD-RAM)
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         31023 MB (10832 MB free)
      D: (NTFS)                                         118.2 GB (88.2 GB free)
      Total Size                                        148.5 GB (98.7 GB free)

    Input:
      Keyboard                                          HID Keyboard Device
      Mouse                                             HID-compliant mouse

    Network:
      Primary IP Address                                127.0.0.1
      Primary MAC Address                               00-19-5B-73-B8-B4
      Network Adapter                                   D-Link AirPremier DWL-G550 Wireless PCI Adapter

    Peripherals:
      FireWire Controller                               VIA VT6307 Fire IIM IEEE1394 Host Controller (PHY: VIA VT6307)
      USB1 Controller                                   nVIDIA nForce 430 (MCP51) - OHCI USB 1.1 Controller
      USB2 Controller                                   nVIDIA nForce 430 (MCP51) - EHCI USB 2.0 Controller
      USB Device                                        USB Composite Device
      USB Device                                        USB Input Device
      USB Device                                        USB Input Device
      USB Device                                        USB Input Device
      USB Device                                        USB Mass Storage Device

    DMI:
      DMI BIOS Vendor                                   American Megatrends Inc.
      DMI BIOS Version                                  0403
      DMI System Manufacturer                           System manufacturer
      DMI System Product                                System Product Name
      DMI System Version                                System Version
      DMI System Serial Number                          System Serial Number
      DMI System UUID                                   00020003-00040005-00060007-00080009
      DMI Motherboard Manufacturer                      ASUSTeK Computer INC.
      DMI Motherboard Product                           A8N-VM CSM
      DMI Motherboard Version                           Rev 1.xx
      DMI Motherboard Serial Number                     MB-1234567890
      DMI Chassis Manufacturer                          Chassis Manufacture
      DMI Chassis Version                               Chassis Version
      DMI Chassis Serial Number                         Chassis Serial Number
      DMI Chassis Asset Tag                             Asset-1234567890
      DMI Chassis Type                                  Desktop Case
      DMI Total / Free Memory Sockets                   4 / 0 

THNX

---

### Post by mörgæs on 2015-01-02
You didn't answer the question in post 3.
When you have the space available I recommend X/Lubuntu in stead of Ubuntu for this hardware.

---

### Post by Roey_Peretz on 2015-01-02
> **mörgæs said:**
> You didn't answer the question in post 3.
When you have the space available I recommend X/Lubuntu in stead of Ubuntu for this hardware.
Hi,

I didn't saw it.
I'll try creating a 10GB partition for Ubuntu.
Why X/Lubuntu? What is it?

TNX M8

---

### Post by Dennis N on 2015-01-02
10 GB is hardly enough for an install, and leaves little room for additions. With 98 GB free, 25 GB would be more satisfactory. Your decision, of course.
Xubuntu and Lubuntu are distros based on Ubuntu which use two other desktop environments which are different from Unity.

---

### Post by Bucky Ball on 2015-01-02
Xubuntu and Lubuntu are both lighter and less resource hungry than the regular Ubuntu. Better for lower spec or older hardware. ;)

---

