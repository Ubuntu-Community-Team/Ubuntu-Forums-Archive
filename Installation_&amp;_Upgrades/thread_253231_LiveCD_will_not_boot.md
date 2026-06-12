---
title: "LiveCD will not boot"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Az7 on 2006-09-08
My Hardware:
-- AMD Athlon 64 X2 4200+ Windsor 2.2GHz Socket AM2 Dual Core Processor Model ADA4200CUBOX
-- PNY VCG7600GXPB Geforce 7600GT 256MB GDDR3 PCI Express x16 Video Card - Retail
-- CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
-- ASUS M2N32-SLI Deluxe Wireless Edition Socket AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
-- Western Digital 250GB SATA drive

desktop-kubuntu-6.06.1 livecd
"Start or Install Kubuntu" stalls at: 
[32.940729] fb0:  VGA16 VGA frame buffer device
"Start Kubuntu in safe graphics mode" stalls at:
[32.760424] fb0:  VGA16 VGA frame buffer device
"Start or Install Kubuntu" after hitting F6 and adding in "noacpi acpi=off" stalls at:
[105.136152] hda_codec:  Unknown model for AD1988, try auto-probe from BIOS. and again at [299.204224] parport0:  PC-style at 0x378 [PCSPP,TRISTATE,EPP]

Oddly enough i've tried a regular desktop-ubuntu-6.06 livecd.  It seems to get further with the "noacpi acpi=off" boot parameters.  It starts X but hangs at a blank, brown screen.  If anyone has any ideas on what to try that would be great.  Thanks.

---

### Post by go.lem on 2006-10-02
Hi!

just trie _only_ "noapic" bootparameter!
with "acpi=off" i got problems!

best regards go.lem

---

