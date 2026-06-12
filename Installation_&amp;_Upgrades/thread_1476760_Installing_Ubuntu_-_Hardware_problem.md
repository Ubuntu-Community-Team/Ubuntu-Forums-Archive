---
title: "Installing Ubuntu - Hardware problem"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by groonrix on 2010-05-08
Hi everyone.
I've been trying to install Ubuntu a few times for a few months now.
When I boot from the Live CD and try to run the OS in live mode,
it freezes after a few minutes of loading.
I did that with two different releases, and checked the CDs for damages,
both by using the tool in the live CD and trying to run the OS on a different machine.
Apparently there are no damages.
I can only conclude that this is a hardware problem.
Here's a summary of my machine's hardware:

    Computer:
      Computer Type                                     ACPI Multiprocessor PC
      Operating System                                  Microsoft Windows XP Professional
      OS Service Pack                                   Service Pack 3
      DirectX                                           4.09.00.0904 (DirectX 9.0c)

    Motherboard:
      CPU Type                                          Intel Pentium 4, 2800 MHz (14 x 200)
      Motherboard Name                                  Springdale
      Motherboard Chipset                               Intel Morgan Hill i865GV
      System Memory                                     1014 MB  (PC3200 DDR SDRAM)
      DIMM1: DDR400-1G                                  1 GB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)  (2.0-2-2-6 @ 133 MHz)
      BIOS Type                                         Phoenix (03/15/07)
      Communication Port                                (COM1)
      Communication Port                                &#8207;(LPT1)

    Display:
      Video Adapter                                     HIGHTECH EXCALIBUR RADEON 9250 - Secondary  (128 MB)
      Video Adapter                                     HIGHTECH EXCALIBUR RADEON 9250  (128 MB)
      Video Adapter                                     Intel(R) 82865G Graphics Controller  (96 MB)
      3D Accelerator                                    ATI Radeon 9250 (RV280)
      3D Accelerator                                    Intel Extreme Graphics 2
      Monitor                                           Proview 572  [15" LCD]  (FGIJ420007397)

    Multimedia:
      Audio Adapter                                     Realtek ALC655 @ Intel 82801EB ICH5 - AC'97 Audio Controller [A-2/A-3]

    Storage:
      IDE Controller                                    Intel(R) 82801EB Ultra ATA Storage Controllers
      Storage Controller                                SCSI/RAID Host Controller
      Disk Drive                                        WDC WD1600AAJS-07PSA0  (149 GB, IDE)
      Disk Drive                                        WDC WD20 00JB-00GVA0 USB Device  (186 GB, USB)
      Optical Drive                                     _NEC DVD_RW ND-2510A  (DVD+R9:2.4x, DVD+RW:8x/4x, DVD-RW:8x/4x, DVD-ROM:12x, CD:32x/16x/40x DVD+RW/DVD-RW)
      Optical Drive                                     HL-DT-ST DVD-ROM GDR8162B  (16x/48x DVD-ROM)
      Optical Drive                                     NN1925D PTC614T SCSI CdRom Device

    Partitions:
      C: (NTFS)                                         76308 MB (38689 MB free)
      E: (NTFS)                                         76308 MB (1966 MB free)
      H: (NTFS)                                         186.3 GB (55.9 GB free)
      Total Size                                        335.3 GB (95.6 GB free)

    Network:
      Network Adapter                                   Realtek RTL8139/810x Family Fast Ethernet NIC

    DMI:
      DMI BIOS Vendor                                   Phoenix Technologies, LTD
      DMI BIOS Version                                  6.00 PG           
      DMI Motherboard Product                           Springdale 
      DMI Chassis Type                                  Desktop Case
      DMI Total / Free Memory Sockets                   4 / 3

Can you assist?
Thanks for your time.

---

### Post by cci[RR]us on 2010-05-08
Not sure if you're having the same problem as me... did you try booting without the splash screen and look out for any errors?

When booting up the CD, go to the menu, and choose Install. But change the options such that you remove the "quiet splash" options at the end of the line.

---

### Post by AnonCat on 2010-05-08
I have a similar setup and wasn't able to install ubuntu until I took out the graphics card and used the integrated graphics.  If you try this and it works, you'll need to blacklist the integrated graphics even if they're turned off in bios before you put the graphics card back in.  You can do this by adding the following statements to the blacklist.conf file in the directory /etc/modprobe.d :

#blacklist graphics
blacklist agp_gart
blacklist intel_agp

to open the file for editing you can simply paste the following into the terminal:

sudo gedit /etc/modprobe.d/blacklist.conf

---

### Post by groonrix on 2010-05-08
Thank you both.
@cci[RR]us; I suppose you meant that I should change the command:
"file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --"
to:
"file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz --".
When I did,
The last line displayed was "init: tty5 respawning too fast, stopped".
Does that help?

@AnonCat; I have never modified hardware, so I need a more detailed explanation.
Do I have to physically take out my graphics card? Can't I disable it using BIOS or anything the like? I'd really prefer that.
By saying integrated graphics, you mean... some graphical component that is a part of the motherboard?
I am really not sure about your next instructions, but since I'm not sure that disabling the graphics card would even work, I guess that they can wait until later.

---

