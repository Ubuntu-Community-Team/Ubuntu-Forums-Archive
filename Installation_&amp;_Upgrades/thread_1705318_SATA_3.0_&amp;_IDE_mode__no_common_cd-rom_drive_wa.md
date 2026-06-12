---
title: "SATA 3.0 &amp; IDE mode : no common cd-rom drive was detected"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by etnba on 2011-03-12
Hi all,
I want to install Ubuntu 10.10 via a DVD-ROM but I faild. I got the message "no common cd-rom drive was detected." I have tried to install ubuntu 11.4 and failed too.
 
Hardware Setting:
DVD-ROM was attached to SATA 3.0 port.
SATA controller was set to IDE mode.
PCH is CougarPoint.
 
I use the same hardware setting to install Red Hat 6.0 and it works fine.
I tried following boot option but in vain: noapic, acpi=off, nodmraid, all_generic_ide.
It is ok to boot via a live usb but ubuntu 10.10 still can't find DVD-ROM.
I have to use the hardware setting I descripted to install Ubuntu 10.10.
Any ideas?
 
By the way, I found a post it descript a similart problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093)
 
 
Thank you.
 
dmesg:
```

[ 1.892198] ata1: SATA max UDMA/133 cmd 0x3098 ctl 0x30ac bmdma 0x3070 irq 19
[ 3.309652] ata1.01: failed to resume link (SControl 0)
[ 3.469636] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3.469777] ata1.01: SATA link down (SStatus 4 SControl 0)
[ 3.469899] ata1.01: link offline, clearing class 3 to NONE
[ 3.489703] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL02, max UDMA/100
[ 3.529740] ata1.00: configured for UDMA/100
[ 8.526759] ata1.00: qc timeout (cmd 0xa0)
[ 8.526872] ata1.00: TEST_UNIT_READY failed (err_mask=0x4)
[ 9.945970] ata1.01: failed to resume link (SControl 0)
[ 10.105952] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 10.106074] ata1.01: SATA link down (SStatus 4 SControl 0)
[ 10.106188] ata1.01: link offline, clearing class 3 to NONE
[ 10.165978] ata1.00: configured for UDMA/100
[ 15.163063] ata1.00: qc timeout (cmd 0xa0)
[ 15.163171] ata1.00: TEST_UNIT_READY failed (err_mask=0x4)
[ 15.163277] ata1.00: limiting SATA link speed to 1.5 Gbps
[ 15.163382] ata1.00: limiting speed to UDMA/100:PIO3
[ 16.582272] ata1.01: failed to resume link (SControl 0)
[ 16.742249] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 16.742371] ata1.01: SATA link down (SStatus 4 SControl 0)
[ 16.742486] ata1.01: link offline, clearing class 3 to NONE
[ 16.802290] ata1.00: configured for UDMA/100
[ 21.799369] ata1.00: qc timeout (cmd 0xa0)
[ 21.799478] ata1.00: TEST_UNIT_READY failed (err_mask=0x4)
[ 21.799583] ata1.00: disabled
[ 21.799693] ata1.00: hard resetting link
[ 22.149176] ata1.01: hard resetting link
[ 23.218581] ata1.01: failed to resume link (SControl 0)
[ 23.378554] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 23.378676] ata1.01: SATA link down (SStatus 4 SControl 0)
[ 23.378790] ata1.01: link offline, clearing class 3 to NONE
[ 23.378793] ata1: EH complete

```
 
lspci:
```

00:1f.2 IDE interface: Intel Corporation Cougar Point 4 port SATA IDE Controller (rev 04) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Intel Corporation Cougar Point 4 port SATA IDE Controller
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0
Interrupt: pin B routed to IRQ 19
Region 0: I/O ports at 3098 [size=8]
Region 1: I/O ports at 30ac [size=4]
Region 2: I/O ports at 3090 [size=8]
Region 3: I/O ports at 30a8 [size=4]
Region 4: I/O ports at 3070 [size=16]
Region 5: I/O ports at 3060 [size=16]
Capabilities: [70] Power Management version 3
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [b0] PCI Advanced Features
AFCap: TP+ FLR+
AFCtrl: FLR-
AFStatus: TP-
Kernel driver in use: ata_piix

```

---

### Post by Hedgehog1 on 2011-03-12
etnba,

To the best of my knowledge, _at this moment in time_ you cannot boot off of USB 3.0 ports or SATA 3.0 ports.  Both require a new hardware layer that is not in Ubuntu just yet.

Once booted, you can read & write to USB 3.0 devices.  I don't know about the SATA 3.0 (both my internal hard drives are SATA 3.0, but plugged into SATA 2.0 ports).

Can you plug your DVD drive into a SATA 2.0 port?  That will get you rolling for now.

***The Hedge***

:KS

---

### Post by etnba on 2011-03-12
Hi Hedge,
I have tried it and it works well. It also works fine to set BIOS to ACHI mode and plug DVD drive into SATA 3.0 port. But I must install Ubuntu 10.10 via DVD drive with IDE mode so I need to solve this problem or get the prove from Ubuntu that Ubuntu 10.10 have this bug.:(
 
Thank you for your reply.

---

### Post by Hedgehog1 on 2011-03-12
etnba,

I don't know if you want this data or not, but I have been tracking a few other SATA CD/DVD issues with 10.10:

[http://ubuntuforums.org/showthread.php?t=1701554]("http://ubuntuforums.org/showthread.php?t=1701554")

These are not SATA 3.0 Specific, just differences between IDE & SATA for CD/DVD/BluRay.

***The Hedge***

:KS

---

### Post by etnba on 2011-03-12
Hi Hedge,
 
when I type 
```
ls /dev/s*
```
 
there is no sr0 in '/dev' directory
 
there is a sg0 in '/dev' directory
 
I follw your steps and change sr0 to sg0.
 
After rebooting, I type
```
ls -al /media/cdrom0
```
 
there is no file in the '/media/cdrom0' directory
 
sg0 is not a block device.
 
Thanks

---

### Post by etnba on 2011-03-14
Hi all,
 
Can someboy help me file this bug?
 
When I typed anything on
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)
 
I always got the error message 'A summary is required.'
 
I am new to Ubuntu. I don't know this bug belongs to which package so that I can't file this bug with Apport.
 
I really really need someboy to help me. Please..
 
I appreciate your help.

---

