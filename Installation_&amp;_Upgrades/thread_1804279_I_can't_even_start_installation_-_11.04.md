---
title: "I can't even start installation - 11.04"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by yoahim on 2011-07-14
I've got a problem with Ubuntu 11.04 . I can't install it. Just after boot from CD(i also used install from wubi and unetbootin - same result) installation stops.  I tried with PS/2 keyboard and without [COLOR=Black]mouse[/COLOR] - no effects.

Here's a [COLOR=SeaGreen][COLOR=Black]screen:[/COLOR] [/COLOR][http://imgur.com/JBeAT](http://imgur.com/JBeAT)

---

### Post by Rubi1200 on 2011-07-15
Hi and welcome to the forums :-)

Please post the make and model of the computer as well as the full specifications.

Which operating system do you currently have installed and have you tried older versions of Ubuntu to see if there is still a problem?

---

### Post by yoahim on 2011-07-16
I'm using Windows XP. Here's my config: DFI AD77 Pro, Athlon 2500+ (Barton), Radeon 9800Pro, 768MB RAM. I just tried 10.04 LTS and i got diffrent errors. 

[SCREEN1]("http://i.imgur.com/Qba6C.jpg")
[SCREEN2]("http://i.imgur.com/sqSkf.jpg")

---

### Post by steve11911 on 2011-07-16
I dug your system specs a little and Uncle Google seems to indicate that Ubuntu should install just fine and I ran across an indication that Natty should install just fine on that hardware as well. [ Caveat-sometimes Uncle Google is wrong.]
I would try a new Natty live cd.Download the iso,check the md5 and burn the disk at the lowest speed.Have you tried your existing disk on another computer?

---

### Post by R Smit on 2011-07-17
My problem is comparable: [http://ubuntuforums.org/showthread.php?t=1762786](http://ubuntuforums.org/showthread.php?t=1762786)

Ubuntu 11.04 installation usually fails.
In the last few months I tried several distributions:

Success: 
Mint 11, 
Kubuntu 11.04

Fail: 
Ubuntu 11.04
OpenSuse 11.4 (installation progress bar halts at the very beginning of the installation) 
Fedora 15 (installation halted at 'waiting for hardware to be initialized')

All these (live) distributions work fine on my old laptop.As I did these installations over a period over several months I can not remember exact details about what happened.
What  component in my computer is preventing these installations? How can I determine it?
```

id:	
roland-desktopmint
description: 	Desktop Computer
product: 	ixtreme M5850
vendor: 	Packard Bell
version: 	P01-A1
serial: 	PTU65E209805205C2F9600
width: 	32 bits
capabilities: 	smbios-2.6 dmi-2.6 smp-1.4 smp
configuration:	
administrator_password	=	disabled
boot	=	normal
chassis	=	desktop
cpus	=	4
power-on_password	=	disabled
uuid	=	F80F4102-92D3-2010-1230-111919000000
id:	
core
description: 	Motherboard
product: 	ixtreme M5850
vendor: 	Packard Bell
physical id: 	
0
slot: 	To be filled by O.E.M.
id:	
firmware
description: 	BIOS
vendor: 	American Megatrends Inc.
physical id: 	
0
version: 	P01-A1 (11/13/2010)
size: 	64KiB
capacity: 	960KiB
capabilities: 	pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
id:	
cpu:0
description: 	CPU
product: 	Intel(R) Core(TM) i5-2300 CPU @ 2.80GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	6.10.7
serial: 	0002-06A7-0000-0000-0000-0000
slot: 	CPU 1
size: 	1600MHz
capacity: 	1600MHz
width: 	64 bits
clock: 	100MHz
capabilities: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt xsave avx lahf_lm ida arat pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
configuration:	
id	=	2
id:	
cache:0
description: 	L1 cache
physical id: 	
5
slot: 	L1-Cache
size: 	256KiB
capacity: 	256KiB
capabilities: 	internal write-back unified
id:	
cache:1
description: 	L2 cache
physical id: 	
6
slot: 	L2-Cache
size: 	1MiB
capacity: 	1MiB
capabilities: 	internal varies unified
id:	
cache:2
description: 	L3 cache
physical id: 	
7
slot: 	L3-Cache
size: 	6MiB
capacity: 	6MiB
capabilities: 	internal unified
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
2.1
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
2.2
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:2
description: 	Logical CPU
physical id: 	
2.3
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:3
description: 	Logical CPU
physical id: 	
2.4
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:4
description: 	Logical CPU
physical id: 	
2.5
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:5
description: 	Logical CPU
physical id: 	
2.6
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:6
description: 	Logical CPU
physical id: 	
2.7
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:7
description: 	Logical CPU
physical id: 	
2.8
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:8
description: 	Logical CPU
physical id: 	
2.9
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:9
description: 	Logical CPU
physical id: 	
2.a
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:10
description: 	Logical CPU
physical id: 	
2.b
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:11
description: 	Logical CPU
physical id: 	
2.c
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:12
description: 	Logical CPU
physical id: 	
2.d
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:13
description: 	Logical CPU
physical id: 	
2.e
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:14
description: 	Logical CPU
physical id: 	
2.f
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:15
description: 	Logical CPU
physical id: 	
2.10
width: 	64 bits
capabilities: 	logical
id:	
memory
description: 	System Memory
physical id: 	
2a
slot: 	System board or motherboard
size: 	4GiB
id:	
bank:0
description: 	DIMM Synchronous [empty]
physical id: 	
0
slot: 	DIMM4
width: 	64 bits
id:	
bank:1
description: 	DIMM Synchronous 1333 MHz (0.8 ns)
product: 	GU512303EP0202
vendor: 	Unifosa
physical id: 	
1
serial: 	00000000
slot: 	DIMM2
size: 	2GiB
width: 	64 bits
clock: 	1333MHz (0.8ns)
id:	
bank:2
description: 	DIMM Synchronous [empty]
physical id: 	
2
slot: 	DIMM3
width: 	64 bits
id:	
bank:3
description: 	DIMM Synchronous 1333 MHz (0.8 ns)
product: 	GU512303EP0202
vendor: 	Unifosa
physical id: 	
3
serial: 	00000000
slot: 	DIMM1
size: 	2GiB
width: 	64 bits
clock: 	1333MHz (0.8ns)
id:	
cpu:1
physical id: 	
1
bus info: 	
cpu@1
version: 	6.10.7
serial: 	0002-06A7-0000-0000-0000-0000
size: 	1600MHz
capacity: 	1600MHz
capabilities: 	vmx ht cpufreq
configuration:	
id	=	2
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
2.1
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
2.2
capabilities: 	logical
id:	
logicalcpu:2
description: 	Logical CPU
physical id: 	
2.3
capabilities: 	logical
id:	
logicalcpu:3
description: 	Logical CPU
physical id: 	
2.4
capabilities: 	logical
id:	
logicalcpu:4
description: 	Logical CPU
physical id: 	
2.5
capabilities: 	logical
id:	
logicalcpu:5
description: 	Logical CPU
physical id: 	
2.6
capabilities: 	logical
id:	
logicalcpu:6
description: 	Logical CPU
physical id: 	
2.7
capabilities: 	logical
id:	
logicalcpu:7
description: 	Logical CPU
physical id: 	
2.8
capabilities: 	logical
id:	
logicalcpu:8
description: 	Logical CPU
physical id: 	
2.9
capabilities: 	logical
id:	
logicalcpu:9
description: 	Logical CPU
physical id: 	
2.a
capabilities: 	logical
id:	
logicalcpu:10
description: 	Logical CPU
physical id: 	
2.b
capabilities: 	logical
id:	
logicalcpu:11
description: 	Logical CPU
physical id: 	
2.c
capabilities: 	logical
id:	
logicalcpu:12
description: 	Logical CPU
physical id: 	
2.d
capabilities: 	logical
id:	
logicalcpu:13
description: 	Logical CPU
physical id: 	
2.e
capabilities: 	logical
id:	
logicalcpu:14
description: 	Logical CPU
physical id: 	
2.f
capabilities: 	logical
id:	
logicalcpu:15
description: 	Logical CPU
physical id: 	
2.10
capabilities: 	logical
id:	
cpu:2
physical id: 	
2
bus info: 	
cpu@2
version: 	6.10.7
serial: 	0002-06A7-0000-0000-0000-0000
size: 	1600MHz
capacity: 	1600MHz
capabilities: 	vmx ht cpufreq
configuration:	
id	=	2
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
2.1
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
2.2
capabilities: 	logical
id:	
logicalcpu:2
description: 	Logical CPU
physical id: 	
2.3
capabilities: 	logical
id:	
logicalcpu:3
description: 	Logical CPU
physical id: 	
2.4
capabilities: 	logical
id:	
logicalcpu:4
description: 	Logical CPU
physical id: 	
2.5
capabilities: 	logical
id:	
logicalcpu:5
description: 	Logical CPU
physical id: 	
2.6
capabilities: 	logical
id:	
logicalcpu:6
description: 	Logical CPU
physical id: 	
2.7
capabilities: 	logical
id:	
logicalcpu:7
description: 	Logical CPU
physical id: 	
2.8
capabilities: 	logical
id:	
logicalcpu:8
description: 	Logical CPU
physical id: 	
2.9
capabilities: 	logical
id:	
logicalcpu:9
description: 	Logical CPU
physical id: 	
2.a
capabilities: 	logical
id:	
logicalcpu:10
description: 	Logical CPU
physical id: 	
2.b
capabilities: 	logical
id:	
logicalcpu:11
description: 	Logical CPU
physical id: 	
2.c
capabilities: 	logical
id:	
logicalcpu:12
description: 	Logical CPU
physical id: 	
2.d
capabilities: 	logical
id:	
logicalcpu:13
description: 	Logical CPU
physical id: 	
2.e
capabilities: 	logical
id:	
logicalcpu:14
description: 	Logical CPU
physical id: 	
2.f
capabilities: 	logical
id:	
logicalcpu:15
description: 	Logical CPU
physical id: 	
2.10
capabilities: 	logical
id:	
cpu:3
physical id: 	
3
bus info: 	
cpu@3
version: 	6.10.7
serial: 	0002-06A7-0000-0000-0000-0000
size: 	1600MHz
capacity: 	1600MHz
capabilities: 	vmx ht cpufreq
configuration:	
id	=	2
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
2.1
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
2.2
capabilities: 	logical
id:	
logicalcpu:2
description: 	Logical CPU
physical id: 	
2.3
capabilities: 	logical
id:	
logicalcpu:3
description: 	Logical CPU
physical id: 	
2.4
capabilities: 	logical
id:	
logicalcpu:4
description: 	Logical CPU
physical id: 	
2.5
capabilities: 	logical
id:	
logicalcpu:5
description: 	Logical CPU
physical id: 	
2.6
capabilities: 	logical
id:	
logicalcpu:6
description: 	Logical CPU
physical id: 	
2.7
capabilities: 	logical
id:	
logicalcpu:7
description: 	Logical CPU
physical id: 	
2.8
capabilities: 	logical
id:	
logicalcpu:8
description: 	Logical CPU
physical id: 	
2.9
capabilities: 	logical
id:	
logicalcpu:9
description: 	Logical CPU
physical id: 	
2.a
capabilities: 	logical
id:	
logicalcpu:10
description: 	Logical CPU
physical id: 	
2.b
capabilities: 	logical
id:	
logicalcpu:11
description: 	Logical CPU
physical id: 	
2.c
capabilities: 	logical
id:	
logicalcpu:12
description: 	Logical CPU
physical id: 	
2.d
capabilities: 	logical
id:	
logicalcpu:13
description: 	Logical CPU
physical id: 	
2.e
capabilities: 	logical
id:	
logicalcpu:14
description: 	Logical CPU
physical id: 	
2.f
capabilities: 	logical
id:	
logicalcpu:15
description: 	Logical CPU
physical id: 	
2.10
capabilities: 	logical
id:	
pci
description: 	Host bridge
product: 	Sandy Bridge DRAM Controller
vendor: 	Intel Corporation
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	09
width: 	32 bits
clock: 	33MHz
id:	
pci:0
description: 	PCI bridge
product: 	Sandy Bridge PCI Express Root Port
vendor: 	Intel Corporation
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	09
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm msi pciexpress normal_decode bus_master cap_list
configuration:	
driver	=	pcieport
resources:	
irq	:	40
ioport	:	e000(size=4096)
memory	:	fa000000-fb0fffff
ioport	:	f0000000(size=167772160)
id:	
display
description: 	VGA compatible controller
product: 	nVidia Corporation
vendor: 	nVidia Corporation
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	a1
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress vga_controller bus_master cap_list rom
configuration:	
driver	=	nvidia
latency	=	0
resources:	
irq	:	16
memory	:	fa000000-faffffff
memory	:	f0000000-f7ffffff
memory	:	f8000000-f9ffffff
ioport	:	e000(size=128)
memory	:	fb000000-fb07ffff
id:	
multimedia
description: 	Audio device
product: 	nVidia Corporation
vendor: 	nVidia Corporation
physical id: 	
0.1
bus info: 	
pci@0000:01:00.1
version: 	a1
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
resources:	
irq	:	17
memory	:	fb080000-fb083fff
id:	
communication
description: 	Communication controller
product: 	Cougar Point HECI Controller #1
vendor: 	Intel Corporation
physical id: 	
16
bus info: 	
pci@0000:00:16.0
version: 	04
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fb229000-fb22900f
id:	
network
description: 	Ethernet interface
product: 	82579LM Gigabit Network Connection
vendor: 	Intel Corporation
physical id: 	
19
bus info: 	
pci@0000:00:19.0
logical name: 	
eth0
version: 	04
serial: 	f8:0f:41:02:92:d3
size: 	100MB/s
capacity: 	1GB/s
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	e1000e
driverversion	=	1.0.2-k4
duplex	=	full
firmware	=	0.13-4
ip	=	192.168.1.104
latency	=	0
link	=	yes
multicast	=	yes
port	=	twisted pair
speed	=	100MB/s
resources:	
irq	:	43
memory	:	fb200000-fb21ffff
memory	:	fb228000-fb228fff
ioport	:	f040(size=32)
id:	
usb:0
description: 	USB Controller
product: 	Cougar Point USB Enhanced Host Controller #2
vendor: 	Intel Corporation
physical id: 	
1a
bus info: 	
pci@0000:00:1a.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	16
memory	:	fb227000-fb2273ff
id:	
multimedia
description: 	Audio device
product: 	Cougar Point High Definition Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	04
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
resources:	
irq	:	46
memory	:	fb220000-fb223fff
id:	
pci:1
description: 	PCI bridge
product: 	Cougar Point PCI Express Root Port 1
vendor: 	Intel Corporation
physical id: 	
1c
bus info: 	
pci@0000:00:1c.0
version: 	b4
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pciexpress msi pm normal_decode bus_master cap_list
configuration:	
driver	=	pcieport
resources:	
irq	:	41
id:	
pci:2
description: 	PCI bridge
product: 	Cougar Point PCI Express Root Port 3
vendor: 	Intel Corporation
physical id: 	
1c.2
bus info: 	
pci@0000:00:1c.2
version: 	b4
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pciexpress msi pm normal_decode bus_master cap_list
configuration:	
driver	=	pcieport
resources:	
irq	:	42
ioport	:	d000(size=4096)
memory	:	fb100000-fb1fffff
id:	
storage
description: 	SATA controller
physical id: 	
0
bus info: 	
pci@0000:03:00.0
logical name: 	
scsi6
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	storage msi pm pciexpress ahci_1.0 bus_master cap_list rom emulated
configuration:	
driver	=	ahci
latency	=	0
resources:	
irq	:	45
ioport	:	d050(size=8)
ioport	:	d040(size=4)
ioport	:	d030(size=8)
ioport	:	d020(size=4)
ioport	:	d000(size=32)
memory	:	fb110000-fb1101ff
memory	:	fb100000-fb10ffff
id:	
cdrom
description: 	DVD-RAM writer
product: 	DVDRAM GH60N
vendor: 	HL-DT-ST
physical id: 	
0.0.0
bus info: 	
scsi@6:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	UG00
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
usb:1
description: 	USB Controller
product: 	Cougar Point USB Enhanced Host Controller #1
vendor: 	Intel Corporation
physical id: 	
1d
bus info: 	
pci@0000:00:1d.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	23
memory	:	fb226000-fb2263ff
id:	
isa
description: 	ISA bridge
product: 	Cougar Point LPC Controller
vendor: 	Intel Corporation
physical id: 	
1f
bus info: 	
pci@0000:00:1f.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master cap_list
configuration:	
latency	=	0
id:	
storage
description: 	SATA controller
product: 	Cougar Point 6 port SATA AHCI Controller
vendor: 	Intel Corporation
physical id: 	
1f.2
bus info: 	
pci@0000:00:1f.2
logical name: 	
scsi0
version: 	04
width: 	32 bits
clock: 	66MHz
capabilities: 	storage msi pm ahci_1.0 bus_master cap_list emulated
configuration:	
driver	=	ahci
latency	=	0
resources:	
irq	:	44
ioport	:	f090(size=8)
ioport	:	f080(size=4)
ioport	:	f070(size=8)
ioport	:	f060(size=4)
ioport	:	f020(size=32)
memory	:	fb225000-fb2257ff
id:	
disk
description: 	ATA Disk
product: 	WDC WD10EARS-22Y
vendor: 	Western Digital
physical id: 	
0.0.0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	80.0
serial: 	WD-WCAV5H993600
size: 	931GiB (1TB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	9b5d01e8
id:	
volume:0
description: 	Windows NTFS volume
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
version: 	3.1
serial: 	ecaf-3245
size: 	17GiB
capacity: 	18GiB
capabilities: 	primary ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-12-01 17:20:34
filesystem	=	ntfs
label	=	PQSERVICE
state	=	clean
id:	
volume:1
description: 	Windows NTFS volume
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
version: 	3.1
serial: 	326c-032c
size: 	98MiB
capacity: 	100MiB
capabilities: 	primary bootable ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-12-01 17:40:11
filesystem	=	ntfs
label	=	SYSTEM RESERVED
state	=	clean
id:	
volume:2
description: 	Windows NTFS volume
physical id: 	
3
bus info: 	
scsi@0:0.0.0,3
logical name: 	
/dev/sda3
version: 	3.1
serial: 	a88627f6-2c6f-e74b-9821-272f87637dce
size: 	96GiB
capacity: 	96GiB
capabilities: 	primary ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-12-01 17:40:12
filesystem	=	ntfs
label	=	Packard Bell
modified_by_chkdsk	=	true
mounted_on_nt4	=	true
resize_log_file	=	true
state	=	dirty
upgrade_on_mount	=	true
id:	
volume:3
description: 	Extended partition
physical id: 	
4
bus info: 	
scsi@0:0.0.0,4
logical name: 	
/dev/sda4
size: 	816GiB
capacity: 	816GiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume:0
description: 	HPFS/NTFS partition
physical id: 	
5
logical name: 	
/dev/sda5
capacity: 	223GiB
id:	
logicalvolume:1
description: 	Linux swap / Solaris partition
physical id: 	
6
logical name: 	
/dev/sda6
capacity: 	5722MiB
capabilities: 	nofs
id:	
logicalvolume:2
description: 	Linux filesystem partition
physical id: 	
7
logical name: 	
/dev/sda7
logical name: 	
/
capacity: 	587GiB
configuration:	
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered
state	=	mounted
id:	
serial
description: 	SMBus
product: 	Cougar Point SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	04
width: 	64 bits
clock: 	33MHz
configuration:	
latency	=	0
resources:	
memory	:	fb224000-fb2240ff
ioport	:	f000(size=32)
id:	
scsi:0
physical id: 	
5
bus info: 	
usb@1:1.4
logical name: 	
scsi8
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description: 	SCSI Disk
product: 	2500JB External
vendor: 	WD
physical id: 	
0.0.0
bus info: 	
scsi@8:0.0.0
logical name: 	
/dev/sdb
version: 	0107
size: 	232GiB (250GB)
capabilities: 	partitioned partitioned:dos
configuration:	
signature	=	8f9c798a
id:	
volume
description: 	Windows FAT volume
vendor: 	MSWIN4.1
physical id: 	
1
bus info: 	
scsi@8:0.0.0,1
logical name: 	
/dev/sdb1
logical name: 	
/media/My Book
version: 	FAT32
serial: 	3717-d230
size: 	232GiB
capacity: 	232GiB
capabilities: 	primary fat initialized
configuration:	
FATs	=	2
filesystem	=	fat
label	=	My Book
mount.fstype	=	vfat
mount.options	=	rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
state	=	mounted
id:	
scsi:1
physical id: 	
6
bus info: 	
usb@2:1.2
logical name: 	
scsi9
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk:0
description: 	SCSI Disk
physical id: 	
0.0.0
bus info: 	
scsi@9:0.0.0
logical name: 	
/dev/sdc
id:	
disk:1
description: 	SCSI Disk
physical id: 	
0.0.1
bus info: 	
scsi@9:0.0.1
logical name: 	
/dev/sdd
id:	
disk:2
description: 	SCSI Disk
physical id: 	
0.0.2
bus info: 	
scsi@9:0.0.2
logical name: 	
/dev/sde
id:	
disk:3
description: 	SCSI Disk
physical id: 	
0.0.3
bus info: 	
scsi@9:0.0.3
logical name: 	
/dev/sdf
id:	
disk:4
description: 	SCSI Disk
physical id: 	
0.0.4
bus info: 	
scsi@9:0.0.4
logical name: 	
/dev/sdg

```

---

### Post by steve11911 on 2011-07-17
I found a page indicating a problem with Natty and Sandy Bridge...
[http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1)

---

### Post by R Smit on 2011-07-18
> **steve11911 said:**
> I found a page indicating a problem with Natty and Sandy Bridge...
[http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1)

That would mean that *a lot *of users are experiencing problems, and that with coming distributions of Ubuntu, Fedora and so on, these problems will be resolved?

---

### Post by steve11911 on 2011-07-19
I cannot speak for this purported Sandy Bridge enhancement but offer the page for your consideration.

[http://cuduwudu.com/2011/03/13-lines-that-enhance-the-performance-of-sandy-bridge/](http://cuduwudu.com/2011/03/13-lines-that-enhance-the-performance-of-sandy-bridge/)

Let us know

---

### Post by R Smit on 2011-07-20
> **steve11911 said:**
> I cannot speak for this purported Sandy Bridge enhancement but offer the page for your consideration.

[http://cuduwudu.com/2011/03/13-lines-that-enhance-the-performance-of-sandy-bridge/](http://cuduwudu.com/2011/03/13-lines-that-enhance-the-performance-of-sandy-bridge/)

Let us know

Thank you for the links you sent.
It is becoming to compicated and time consuming for me.
I continu with Mint 10 for the time being.

---

### Post by yoahim on 2011-07-25
Well, I party solve the problem. I used "nomodeset" - I don't now why this didn't work before. Now I've got another problem during installation, just after loading screen becomes black. I had the same problem with Mint 11, but i used compatibility mode+nomode set and it helped, but i can't find this mode in ubuntu.

---

