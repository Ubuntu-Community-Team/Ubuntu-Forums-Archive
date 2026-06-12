---
title: "Issue booting X Windows (VBESetVBEMode failedEmulator)"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by MSumulong on 2008-04-29
I am trying to install Xubuntu onto my Compaq Armada 7400 Notebook (366 MHz PII / 256 MB RAM / 10 GB HD) and I am having issues booting into the graphical part of the installation. After a while I just get to the standard terminal screen. The screen seems to blink about three or four times and then apparently quits to the terminal.

I think the issue lies in the last part of the log file when it tries to load the libint10.so module. 

> 
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 4096 kB
(II) VESA(0): VESA VBE OEM: S3 Incorporated. M5 BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) VESA(0): VESA VBE OEM Product: VBE 2.0
(II) VESA(0): VESA VBE OEM Product Rev: Rev 1.1
(==) VESA(0): Write-combining range (0x40000000,0x400000)
(II) VESA(0): virtual address = 0xb7562000,
	physical address = 0x40000000, size = 4194304
(II) VESA(0): VBESetVBEMode failedEmulator asked to make a suspect byte access to port 17 (0x0011); terminating.


I've tried to search endlessly for what this particular error means without any luck. I've also tried to add the recommended settings from Compaq's site for Linux distros to the Xorg.conf file w/o any luck either.

I have had success getting DSL 4.2.5 to work on this laptop but I'd rather use Xubuntu.

---

