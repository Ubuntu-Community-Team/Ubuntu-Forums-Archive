---
title: "ubuntu 18.04.1 LTS hangs at ubuntu boot screen  dell-Vostro 200"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by izquierdista on 2018-11-09
I upgraded to Ubuntu 18.04.1 LTS from a previous ubuntu version on Dell-Vostro 200 desktop and now when I boot up the computer the screen doesn't get past the ubuntu boot screen prior to the login page and freezes. My workaround is to boot using safemode and Im able to login and use the computer including printer and scanner. 

What can I do to fix this situation? 

I would greatly appreciate any help

---

### Post by QIII on 2018-11-09
Hello!

Can you provide your hardware specifications?

Did you have a proprietary graphics driver installed when you updated?  That is one of the surest ways to encounter a significant emotional event when upgrading.  Many of us recommend a good backup followed by a fresh installation to avoid situations like this.

---

### Post by izquierdista on 2018-11-09
here are my hardware specs:


```
id:	
dell-vostro-200
description: 	Desktop Computer
product: 	Vostro 200
vendor: 	Dell Inc.
version: 	OEM
serial: 	21QQXF1
width: 	64 bits
capabilities: 	smbios-2.5 dmi-2.5 smp vsyscall32
configuration:	
boot	=	normal
chassis	=	desktop
uuid	=	44454C4C-3100-1051-8051-B2C04F584631
id:	
core
description: 	Motherboard
product: 	0CU409
vendor: 	Dell Inc.
physical id: 	
0
serial: 	..CN7360482H00OC.
id:	
firmware
description: 	BIOS
vendor: 	Dell Inc.
physical id: 	
0
version: 	1.0.11
date: 	01/31/2008
size: 	128KiB
capacity: 	1984KiB
capabilities: 	isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
id:	
cpu
description: 	CPU
product: 	Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
slot: 	Socket 775
size: 	2230MHz
capacity: 	4GHz
width: 	64 bits
clock: 	333MHz
capabilities: 	x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti tpr_shadow vnmi flexpriority dtherm cpufreq
configuration:	
cores	=	2
enabledcores	=	2
threads	=	2
id:	
cache:0
description: 	L1 cache
physical id: 	
a
slot: 	Internal Cache
size: 	32KiB
capacity: 	32KiB
capabilities: 	synchronous internal write-back
configuration:	
level	=	1
id:	
cache:1
description: 	L2 cache
physical id: 	
b
slot: 	External Cache
size: 	4MiB
capacity: 	4MiB
capabilities: 	synchronous external write-back
configuration:	
level	=	2
id:	
memory
description: 	System Memory
physical id: 	
24
slot: 	System board or motherboard
size: 	4GiB
id:	
bank:0
description: 	DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product: 	6400EL Series
vendor: 	7F7F7F7F7F020000
physical id: 	
0
serial: 	00000000
slot: 	DIMM1
size: 	2GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
bank:1
description: 	DIMM [empty]
product: 	M3 78T6553CZ3-CE6
vendor: 	Samsung
physical id: 	
1
serial: 	030D9818
slot: 	DIMM2
id:	
bank:2
description: 	DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product: 	6400EL Series
vendor: 	7F7F7F7F7F020000
physical id: 	
2
serial: 	00000000
slot: 	DIMM3
size: 	2GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
bank:3
description: 	DIMM [empty]
product: 	M3 78T6553EZ3-CE6
vendor: 	Samsung
physical id: 	
3
serial: 	050372D6
slot: 	DIMM4
id:	
pci
description: 	Host bridge
product: 	82G33/G31/P35/P31 Express DRAM Controller
vendor: 	Intel Corporation
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	02
width: 	32 bits
clock: 	33MHz
id:	
pci:0
description: 	PCI bridge
product: 	82G33/G31/P35/P31 Express PCI Express Root Port
vendor: 	Intel Corporation
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm msi pciexpress normal_decode bus_master cap_list
configuration:	
driver	=	pcieport
resources:	
irq	:	16
ioport	:	c000(size=4096)
memory	:	fde00000-fdefffff
ioport	:	fda00000(size=1048576)
id:	
display
description: 	VGA compatible controller
product: 	82G33/G31 Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	msi pm vga_controller bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fdf00000-fdf7ffff
ioport	:	ff00(size=8)
memory	:	d0000000-dfffffff
memory	:	fdb00000-fdbfffff
memory	:	c0000-dffff
id:	
network
description: 	Ethernet interface
product: 	82562V-2 10/100 Network Connection
vendor: 	Intel Corporation
physical id: 	
19
bus info: 	
pci@0000:00:19.0
logical name: 	
enp0s25
version: 	02
serial: 	00:1d:09:8e:f5:78
size: 	100Mbit/s
capacity: 	100Mbit/s
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	e1000e
driverversion	=	3.2.6-k
duplex	=	full
firmware	=	1.1-2
ip	=	192.168.1.5
latency	=	0
link	=	yes
multicast	=	yes
port	=	twisted pair
speed	=	100Mbit/s
resources:	
irq	:	24
memory	:	fdfc0000-fdfdffff
memory	:	fdfff000-fdffffff
ioport	:	fe00(size=32)
id:	
usb:0
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #4
vendor: 	Intel Corporation
physical id: 	
1a
bus info: 	
pci@0000:00:1a.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	16
ioport	:	fd00(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@3
logical name: 	
usb3
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb:1
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #5
vendor: 	Intel Corporation
physical id: 	
1a.1
bus info: 	
pci@0000:00:1a.1
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	21
ioport	:	fc00(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@4
logical name: 	
usb4
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb
description: 	Mouse
product: 	USB Optical Mouse
vendor: 	PixArt
physical id: 	
2
bus info: 	
usb@4:2
version: 	1.00
capabilities: 	usb-2.00
configuration:	
driver	=	usbhid
maxpower	=	100mA
speed	=	2Mbit/s
id:	
usb:2
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #6
vendor: 	Intel Corporation
physical id: 	
1a.2
bus info: 	
pci@0000:00:1a.2
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	19
ioport	:	fb00(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@5
logical name: 	
usb5
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb
description: 	Keyboard
product: 	HP Elite USB Keyboard
vendor: 	Chicony
physical id: 	
1
bus info: 	
usb@5:1
version: 	1.21
capabilities: 	usb-1.10
configuration:	
driver	=	usbhid
maxpower	=	100mA
speed	=	2Mbit/s
id:	
usb:3
description: 	USB controller
product: 	82801I (ICH9 Family) USB2 EHCI Controller #2
vendor: 	Intel Corporation
physical id: 	
1a.7
bus info: 	
pci@0000:00:1a.7
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci-pci
latency	=	0
resources:	
irq	:	18
memory	:	fdffe000-fdffe3ff
id:	
usbhost
product: 	EHCI Host Controller
vendor: 	Linux 4.15.0-38-generic ehci_hcd
physical id: 	
1
bus info: 	
usb@1
logical name: 	
usb1
version: 	4.15
capabilities: 	usb-2.00
configuration:	
driver	=	hub
slots	=	6
speed	=	480Mbit/s
id:	
usb
description: 	Printer
product: 	MFC-L2700DW
vendor: 	Brother
physical id: 	
6
bus info: 	
usb@1:6
version: 	1.00
serial: 	U63887D7N945868
capabilities: 	usb-2.00 bidirectional
configuration:	
driver	=	usblp
maxpower	=	2mA
speed	=	480Mbit/s
id:	
multimedia
description: 	Audio device
product: 	82801I (ICH9 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	02
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	snd_hda_intel
latency	=	0
resources:	
irq	:	25
memory	:	fdff4000-fdff7fff
id:	
usb:4
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #1
vendor: 	Intel Corporation
physical id: 	
1d
bus info: 	
pci@0000:00:1d.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	23
ioport	:	fa00(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@6
logical name: 	
usb6
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb:5
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #2
vendor: 	Intel Corporation
physical id: 	
1d.1
bus info: 	
pci@0000:00:1d.1
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	19
ioport	:	f900(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@7
logical name: 	
usb7
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb:6
description: 	USB controller
product: 	82801I (ICH9 Family) USB UHCI Controller #3
vendor: 	Intel Corporation
physical id: 	
1d.2
bus info: 	
pci@0000:00:1d.2
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	18
ioport	:	f800(size=32)
id:	
usbhost
product: 	UHCI Host Controller
vendor: 	Linux 4.15.0-38-generic uhci_hcd
physical id: 	
1
bus info: 	
usb@8
logical name: 	
usb8
version: 	4.15
capabilities: 	usb-1.10
configuration:	
driver	=	hub
slots	=	2
speed	=	12Mbit/s
id:	
usb:7
description: 	USB controller
product: 	82801I (ICH9 Family) USB2 EHCI Controller #1
vendor: 	Intel Corporation
physical id: 	
1d.7
bus info: 	
pci@0000:00:1d.7
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci-pci
latency	=	0
resources:	
irq	:	23
memory	:	fdffd000-fdffd3ff
id:	
usbhost
product: 	EHCI Host Controller
vendor: 	Linux 4.15.0-38-generic ehci_hcd
physical id: 	
1
bus info: 	
usb@2
logical name: 	
usb2
version: 	4.15
capabilities: 	usb-2.00
configuration:	
driver	=	hub
slots	=	6
speed	=	480Mbit/s
id:	
pci:1
description: 	PCI bridge
product: 	82801 PCI Bridge
vendor: 	Intel Corporation
physical id: 	
1e
bus info: 	
pci@0000:00:1e.0
version: 	92
width: 	32 bits
clock: 	33MHz
capabilities: 	pci subtractive_decode bus_master cap_list
resources:	
ioport	:	d000(size=4096)
memory	:	fdd00000-fddfffff
ioport	:	fdc00000(size=1048576)
id:	
isa
description: 	ISA bridge
product: 	82801IR (ICH9R) LPC Interface Controller
vendor: 	Intel Corporation
physical id: 	
1f
bus info: 	
pci@0000:00:1f.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master cap_list
configuration:	
driver	=	lpc_ich
latency	=	0
resources:	
irq	:	0
id:	
ide:0
description: 	IDE interface
product: 	82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
vendor: 	Intel Corporation
physical id: 	
1f.2
bus info: 	
pci@0000:00:1f.2
version: 	02
width: 	32 bits
clock: 	66MHz
capabilities: 	ide pm bus_master cap_list
configuration:	
driver	=	ata_piix
latency	=	0
resources:	
irq	:	19
ioport	:	f700(size=8)
ioport	:	f600(size=4)
ioport	:	f500(size=8)
ioport	:	f400(size=4)
ioport	:	f300(size=16)
ioport	:	f200(size=16)
id:	
serial
description: 	SMBus
product: 	82801I (ICH9 Family) SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	02
width: 	64 bits
clock: 	33MHz
configuration:	
driver	=	i801_smbus
latency	=	0
resources:	
irq	:	18
memory	:	fdffc000-fdffc0ff
ioport	:	500(size=32)
id:	
ide:1
description: 	IDE interface
product: 	82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
vendor: 	Intel Corporation
physical id: 	
1f.5
bus info: 	
pci@0000:00:1f.5
version: 	02
width: 	32 bits
clock: 	66MHz
capabilities: 	ide pm bus_master cap_list
configuration:	
driver	=	ata_piix
latency	=	0
resources:	
irq	:	19
ioport	:	f000(size=8)
ioport	:	ef00(size=4)
ioport	:	ee00(size=8)
ioport	:	ed00(size=4)
ioport	:	ec00(size=16)
ioport	:	eb00(size=16)
id:	
scsi:0
physical id: 	
1
logical name: 	
scsi0
capabilities: 	emulated
id:	
disk
description: 	ATA Disk
product: 	ST3640623AS
vendor: 	Seagate
physical id: 	
0.0.0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	SD43
serial: 	9VK0JB95
size: 	596GiB (640GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
logicalsectorsize	=	512
sectorsize	=	512
signature	=	6d0505de
id:	
volume:0
description: 	EXT4 volume
vendor: 	Linux
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
logical name: 	
/
version: 	1.0
serial: 	3aa91de7-ba5f-473f-9fe3-1b843a460939
size: 	592GiB
capacity: 	592GiB
capabilities: 	primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration:	
created	=	2017-05-01 17:24:00
filesystem	=	ext4
lastmountpoint	=	/
modified	=	2018-11-09 16:53:09
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,data=ordered
mounted	=	2018-11-09 16:45:06
state	=	mounted
id:	
volume:1
description: 	Extended partition
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
size: 	3316MiB
capacity: 	3316MiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume
description: 	Linux swap volume
physical id: 	
5
logical name: 	
/dev/sda5
version: 	1
serial: 	fcfc71ed-a52f-4366-97b1-2373487cec78
size: 	3316MiB
capacity: 	3316MiB
capabilities: 	nofs swap initialized
configuration:	
filesystem	=	swap
pagesize	=	4096
id:	
scsi:1
physical id: 	
2
logical name: 	
scsi1
capabilities: 	emulated
id:	
cdrom
description: 	DVD-RAM writer
product: 	DVDRAM GH24NS95
vendor: 	HL-DT-ST
physical id: 	
0.0.0
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/sr0
version: 	RN00
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
```

---

### Post by ajgreeny on 2018-11-10
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text.
Unfortunately, it looks as if you have already edited the plain text copied from terminal before posting here so all proper formatting has now been lost

See my signature below for a **How-to**

---

### Post by izquierdista on 2018-11-14
```
 
dell@dell-Vostro-200:~$ sudo lshw
[sudo] password for dell: 
dell-vostro-200             
    description: Desktop Computer
    product: Vostro 200
    vendor: Dell Inc.
    version: OEM
    serial: 21QQXF1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop uuid=44454C4C-3100-1051-8051-B2C04F584631
  *-core
       description: Motherboard
       product: 0CU409
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN7360482H00OC.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.0.11
          date: 01/31/2008
          size: 128KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          slot: Socket 775
          size: 2003MHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti tpr_shadow vnmi flexpriority dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous external write-back
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 6400EL Series
             vendor: 7F7F7F7F7F020000
             physical id: 0
             serial: 00000000
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: M3 78T6553CZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: 030D9818
             slot: DIMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 6400EL Series
             vendor: 7F7F7F7F7F020000
             physical id: 2
             serial: 00000000
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             product: M3 78T6553EZ3-CE6
             vendor: Samsung
             physical id: 3
             serial: 050372D6
             slot: DIMM4
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fde00000-fdefffff ioport:fda00000(size=1048576)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff memory:fdb00000-fdbfffff memory:c0000-dffff
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 02
             serial: 00:1d:09:8e:f5:78
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=1.1-2 ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:24 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fd00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: HP Elite USB Keyboard
                   vendor: Chicony
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.21
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fdffe000-fdffe3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-38-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: Printer
                   product: MFC-L2700DW
                   vendor: Brother
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.00
                   serial: U63887D7N945868
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:25 memory:fdff4000-fdff7fff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fa00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f900(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-38-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fdffd000-fdffd3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-38-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=8) ioport:f400(size=4) ioport:f300(size=16) ioport:f200(size=16)
        *-serial
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:18 memory:fdffc000-fdffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f000(size=8) ioport:ef00(size=4) ioport:ee00(size=8) ioport:ed00(size=4) ioport:ec00(size=16) ioport:eb00(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3640623AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SD43
             serial: 9VK0JB95
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=6d0505de
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 3aa91de7-ba5f-473f-9fe3-1b843a460939
                size: 592GiB
                capacity: 592GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-05-01 17:24:00 filesystem=ext4 lastmountpoint=/ modified=2018-11-13 07:52:17 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-11-13 07:52:23 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3316MiB
                capacity: 3316MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sda5
                   version: 1
                   serial: fcfc71ed-a52f-4366-97b1-2373487cec78
                   size: 3316MiB
                   capacity: 3316MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NS95
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: RN00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
dell@dell-Vostro-200:~$ 

```


here it is again with the code tags

---

