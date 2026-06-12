---
title: "Ubuntu install can't find my hard drive?"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by prestoN_ on 2008-09-30
I am dual booting Window's XP SP3 & Ubuntu 8.04

Okay well I am new to Ubuntu (I am using 8.04) I ran the live CD decided i liked it and tried to install it. It was all going smoothly till it got to step 4 "Hard drive partitioning" It can't find my hard drive but when i put my flash drive in it does my CD is good i did a disk check 100% ok. So I am really confused now I am dual booting i have only one hard drive i have 70GB of free space too. I tried to partition it with the partition app but still no dice everything works find just can't find my dad gum hard drive! 

if you need spec's ask please thank you for your time! :)

---

### Post by prestoN_ on 2008-10-01
Bump. Someone please help?

---

### Post by prestoN_ on 2008-10-01
bump

---

### Post by forger on 2008-10-01
Do the following commands in livecd in Applications > Accessories > Terminal:
```
sudo update-pciids
sudo update-usbids

```

Then do:
```

ls -l /dev/disk/by-id/
lspci -nnv

```
Reply with the full output here

It might also be good to head to launchpad and report a bug: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

Example subject line: hardy install livecd - cannot detect hard drive *brand and model here*
(Better leave the package as "I don't know")
In the "Further information" field you type in the release you're trying (hardy heron 8.04.1 ?) and the steps you took to discover this bug, also include the output of the commands given above :)

---

### Post by prestoN_ on 2008-10-01
Ahh thank you I will when i get home tommarow at 12:00 in the morning.

I just installed hardy on my grampa's PC. It went fine he has a very old computer.

I am installing hardy on my computer (Well trying to) I have been fourm searching for awhile but no one else has this problem I don't know why I get the bad luck.

---

### Post by prestoN_ on 2008-10-02
ubuntu@ubuntu:~$ sudo update-pciids
--12:40:11--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 216.34.181.96
Connecting to pciids.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 137,665 (134K) [application/x-bzip2]

100%[====================================>] 137,665      192.99K/s             

12:40:15 (192.06 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [137665/137665]

Done.
ubuntu@ubuntu:~$ sudo update-usbids
--12:40:40--  [http://linux-usb.sourceforge.net/usb.ids](http://linux-usb.sourceforge.net/usb.ids)
           => `/var/lib/misc/usb.ids.new'
Resolving linux-usb.sourceforge.net... 216.34.181.96
Connecting to linux-usb.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,258 (349K) [text/plain]

100%[====================================>] 357,258      166.01K/s             

12:40:46 (165.46 KB/s) - `/var/lib/misc/usb.ids.new' saved [357258/357258]

Done.
ubuntu@ubuntu:~$ ls -1/dev/disk/by-id/
ls: invalid option -- /
Try `ls --help' for more information.
ubuntu@ubuntu:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2008-10-02 12:30 usb-Kingston_DataTraveler_2.0_5B830D000536-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-10-02 12:30 usb-Kingston_DataTraveler_2.0_5B830D000536-0:0-part1 -> ../../sda1
ubuntu@ubuntu:~$ lspci -nnv
00:00.0 Host bridge [0600]: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge [1002:5952]
	Subsystem: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge [1002:5952]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: <access denied>

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:81ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 221
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 7000 [size=16]
	Memory at fbcffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbcfe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fbcfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fbcfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbcfa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20 [EHCI])
	Subsystem: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbcff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:4385]
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
	Subsystem: ATI Technologies Inc SB600 IDE [1002:438c]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fbcf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV670PRO [Radeon HD 3850] [1002:9505] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device [1002:2542]
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbdf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fbdc0000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Audio device [0403]: ATI Technologies Inc Radeon HD 3870 Audio device [1002:aa18]
	Subsystem: ATI Technologies Inc Radeon HD 3870 Audio device [1002:aa18]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbdec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2360] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8202]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
	Subsystem: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044]
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at fbfff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>

03:04.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
	Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus) [1043:811a]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at e800 [size=256]
	Expansion ROM at fbf00000 [disabled] [size=128K]
	Capabilities: <access denied>

ubuntu@ubuntu:~$

---

### Post by prestoN_ on 2008-10-02
Up.

---

### Post by dabl on 2008-10-02
If it's a SATA drive, try setting the SATA "mode" in BIOS to AHCI.

---

### Post by prestoN_ on 2008-10-02
> **dabl said:**
> If it's a SATA drive, try setting the SATA "mode" in BIOS to AHCI.

Tried it still didn't work :{

---

### Post by dabl on 2008-10-02
Hmmmm.  Is it a SATA drive?  Is there also a PATA/IDE hard drive in that computer?

Usually fiddling with the "mode" choices in BIOS is what it takes to get a hard drive to show up in Linux.  Linux gets it cues about the onboard hardware from BIOS.  So if there is a "Legacy IDE" or other mode available, try it.

---

### Post by prestoN_ on 2008-10-02
> **dabl said:**
> Hmmmm.  Is it a SATA drive?  Is there also a PATA/IDE hard drive in that computer?

Usually fiddling with the "mode" choices in BIOS is what it takes to get a hard drive to show up in Linux.  Linux gets it cues about the onboard hardware from BIOS.  So if there is a "Legacy IDE" or other mode available, try it.

There is a legacy drive option, i'll go try it and, it is a SATA drive. It's my only hard drive.

---

### Post by prestoN_ on 2008-10-02
> **dabl said:**
> Hmmmm.  Is it a SATA drive?  Is there also a PATA/IDE hard drive in that computer?

Usually fiddling with the "mode" choices in BIOS is what it takes to get a hard drive to show up in Linux.  Linux gets it cues about the onboard hardware from BIOS.  So if there is a "Legacy IDE" or other mode available, try it.

Just tried the Legacy IDE mode but no dice :/

---

### Post by forger on 2008-10-03
> 00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
Subsystem: ASUSTeK Computer Inc. Unknown device [1043:81ef]
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 221
I/O ports at b000 [size=8]
I/O ports at a000 [size=4]
I/O ports at 9000 [size=8]
I/O ports at 8000 [size=4]
I/O ports at 7000 [size=16]
Memory at fbcffc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
[...]
02:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2360] (rev 02) (prog-if 01 [AHCI 1.0])
Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8202]
Flags: bus master, fast devsel, latency 0, IRQ 17
I/O ports at dc00 [size=8]
I/O ports at d880 [size=4]
I/O ports at d800 [size=8]
I/O ports at d480 [size=4]
I/O ports at d400 [size=16]
Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>

Looks like your sata controllers aren't detected, I had a similar problem back in gutsy, and reported it as a bug in time, then they fixed it :)

Be sure to include in your bug report the output of this command
```
sudo lspci -nnv
```
(with sudo)

---

### Post by prestoN_ on 2008-10-06
Thank's where do I post this at?

---

