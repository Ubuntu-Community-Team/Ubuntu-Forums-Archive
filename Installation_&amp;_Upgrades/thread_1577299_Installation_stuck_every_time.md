---
title: "Installation stuck every time"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by merajchhaya on 2010-09-18
Hello

I've decided to delete Windows XP from one of my machines and install Ubuntu instead.

At the first couple of times, the installation got stuck, sometimes at 20% copying files, other times at 50%, and once even at 77%.

Then, when I tried installing again, I got "errno 5", which I searched about, and figured I should burn Ubuntu onto a new CD, which I did. No luck, continue to get the installation stuck at different percentages.

I then just installed Windows 7, and tried installing Ubuntu from there, by running "wubi". It extracted all files successfully, and restarted.

The boot screen was stuck, it automatically booted into Windows. As I did not know previously how to reboot cleanly, I just set the default operating system option in Windows, as "Ubuntu".

I restarted, and the Ubuntu installation began. For my disappointment, I got stuck again, this time at 48%.

My computer has an old 40GB IDE HDD, and I've burned the Ubuntu 10.04 ISO onto a DVD. This same DVD was used to successfully install Ubuntu on another machine.

What could be the problem?

---

### Post by davidmohammed on 2010-09-18
can you describe the specification of your PC?

hardware, processor, ram, graphics card,PCI devices plugged in, USB devices plugged in.  Basically as much information as you can to help us to help you.

---

### Post by merajchhaya on 2010-09-19
Hello David

I've ran a command to get all my computer's info.

Hope it's not too much :)

```
 id:	
ubuntu
description: 	Desktop Computer
product: 	M963G
vendor: 	ECS
version: 	1.0
serial: 	00000000
width: 	32 bits
capabilities: 	smbios-2.3 dmi-2.3 smp-1.1 smp
configuration:	
boot	=	normal
chassis	=	desktop
cpus	=	1
uuid	=	00020003-0004-0005-0006-000700080009
id:	
core
description: 	Motherboard
product: 	M963G
vendor: 	ECS
physical id: 	
0
version: 	1.0
serial: 	00000000
id:	
firmware
description: 	BIOS
vendor: 	American Megatrends Inc.
physical id: 	
0
version: 	080009 (07/29/2004)
size: 	64KiB
capacity: 	192KiB
capabilities: 	isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
id:	
cpu
description: 	CPU
product: 	Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	15.2.9
slot: 	socket 478
size: 	3GHz
capacity: 	3GHz
width: 	32 bits
clock: 	800MHz
capabilities: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
configuration:	
id	=	0
id:	
cache:0
description: 	L1 cache
physical id: 	
5
slot: 	L1-Cache
size: 	8KiB
capacity: 	8KiB
capabilities: 	pipeline-burst internal varies data
id:	
cache:1
description: 	L2 cache
physical id: 	
6
slot: 	L2-Cache
size: 	512KiB
capacity: 	512KiB
capabilities: 	pipeline-burst internal varies unified
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
0.1
width: 	32 bits
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
0.2
width: 	32 bits
capabilities: 	logical
id:	
memory
description: 	System Memory
physical id: 	
28
slot: 	System board or motherboard
size: 	1507MiB
id:	
bank:0
description: 	[empty]
product: 	PartNum0
vendor: 	Manufacturer0
physical id: 	
0
serial: 	SerNum0
slot: 	DIMM0
id:	
bank:1
description: 	[empty]
product: 	PartNum1
vendor: 	Manufacturer1
physical id: 	
1
serial: 	SerNum1
slot: 	DIMM1
id:	
bank:2
description: 	[empty]
product: 	PartNum2
vendor: 	Manufacturer2
physical id: 	
2
serial: 	SerNum2
slot: 	DIMM2
id:	
pci
description: 	Host bridge
product: 	661FX/M661FX/M661MX Host
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	11
width: 	32 bits
clock: 	33MHz
configuration:	
driver	=	agpgart-sis
latency	=	32
resources:	
irq	:	0
memory	:	e0000000-e3ffffff
id:	
pci
description: 	PCI bridge
product: 	SiS AGP Port (virtual PCI-to-PCI bridge)
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pci bus_master
resources:	
memory	:	dbe00000-dfefffff
memory	:	bbd00000-dbcfffff(prefetchable)
id:	
display
description: 	VGA compatible controller
product: 	NV44A [GeForce 6200]
vendor: 	nVidia Corporation
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	a1
width: 	32 bits
clock: 	66MHz
capabilities: 	pm agp agp-3.0 bus_master cap_list rom
configuration:	
driver	=	nouveau
latency	=	64
maxlatency	=	1
mingnt	=	5
resources:	
irq	:	16
memory	:	de000000-deffffff
memory	:	c0000000-cfffffff(prefetchable)
memory	:	dd000000-ddffffff
memory	:	dfee0000-dfefffff(prefetchable)
id:	
isa
description: 	ISA bridge
product: 	SiS964 [MuTIOL Media IO]
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	36
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master
configuration:	
latency	=	0
id:	
ide
description: 	IDE interface
product: 	5513 [IDE]
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
2.5
bus info: 	
pci@0000:00:02.5
logical name: 	
scsi0
logical name: 	
scsi1
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	ide pm bus_master cap_list emulated
configuration:	
driver	=	pata_sis
latency	=	128
resources:	
irq	:	0
ioport	:	1f0(size=8)
ioport	:	3f6
ioport	:	170(size=8)
ioport	:	376
ioport	:	ffa0(size=16)
id:	
cdrom
description: 	DVD-RAM writer
product: 	CDDVDW SH-S222A
vendor: 	TSSTcorp
physical id: 	
0
bus info: 	
scsi@0:0.0.0
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
logical name: 	
/cdrom
version: 	SB02
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
mount.fstype	=	iso9660
mount.options	=	ro,noatime
state	=	mounted
status	=	ready
id:	
medium
physical id: 	
0
logical name: 	
/dev/cdrom
logical name: 	
/cdrom
configuration:	
mount.fstype	=	iso9660
mount.options	=	ro,noatime
state	=	mounted
id:	
disk
description: 	ATA Disk
product: 	ST340016A
vendor: 	Seagate
physical id: 	
1
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/sda
version: 	3.19
serial: 	3HS9PF1G
size: 	37GiB (40GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	000eafda
id:	
volume:0
description: 	Windows NTFS volume
physical id: 	
1
bus info: 	
scsi@1:0.0.0,1
logical name: 	
/dev/sda1
version: 	3.1
serial: 	a441-af94
size: 	98MiB
capacity: 	100MiB
capabilities: 	primary bootable ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-09-19 04:29:31
filesystem	=	ntfs
label	=	System Reserved
state	=	clean
id:	
volume:1
description: 	Windows NTFS volume
physical id: 	
2
bus info: 	
scsi@1:0.0.0,2
logical name: 	
/dev/sda2
version: 	3.1
serial: 	a66ff371-fae1-544d-90b4-96fa95e447ae
size: 	34GiB
capacity: 	34GiB
capabilities: 	primary ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-09-19 04:29:45
filesystem	=	ntfs
state	=	clean
id:	
volume:2
description: 	Extended partition
physical id: 	
3
bus info: 	
scsi@1:0.0.0,3
logical name: 	
/dev/sda3
size: 	1610MiB
capacity: 	1610MiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume
description: 	Linux swap / Solaris partition
physical id: 	
5
logical name: 	
/dev/sda5
capacity: 	1610MiB
capabilities: 	nofs
id:	
multimedia:0
description: 	Multimedia audio controller
product: 	AC'97 Sound Controller
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
2.7
bus info: 	
pci@0000:00:02.7
version: 	a0
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	Intel ICH
latency	=	64
maxlatency	=	11
mingnt	=	52
resources:	
irq	:	18
ioport	:	e800(size=256)
ioport	:	ec00(size=128)
id:	
usb:0
description: 	USB Controller
product: 	USB 1.1 Controller
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
3
bus info: 	
pci@0000:00:03.0
version: 	0f
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
maxlatency	=	80
resources:	
irq	:	20
memory	:	dffdc000-dffdcfff
id:	
usb:1
description: 	USB Controller
product: 	USB 1.1 Controller
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
3.1
bus info: 	
pci@0000:00:03.1
version: 	0f
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
maxlatency	=	80
resources:	
irq	:	21
memory	:	dffdd000-dffddfff
id:	
usb:2
description: 	USB Controller
product: 	USB 1.1 Controller
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
3.2
bus info: 	
pci@0000:00:03.2
version: 	0f
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
maxlatency	=	80
resources:	
irq	:	22
memory	:	dffde000-dffdefff
id:	
usb:3
description: 	USB Controller
product: 	USB 2.0 Controller
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
3.3
bus info: 	
pci@0000:00:03.3
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	64
maxlatency	=	80
resources:	
irq	:	23
memory	:	dffdf000-dffdffff
id:	
network
description: 	Ethernet interface
product: 	SiS900 PCI Fast Ethernet
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
4
bus info: 	
pci@0000:00:04.0
logical name: 	
eth0
version: 	90
serial: 	00:11:5b:33:4a:e4
size: 	100MB/s
capacity: 	100MB/s
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	sis900
driverversion	=	v1.08.10 Apr. 2 2006
duplex	=	full
ip	=	192.168.0.103
latency	=	64
link	=	yes
maxlatency	=	11
mingnt	=	52
multicast	=	yes
port	=	MII
speed	=	100MB/s
resources:	
irq	:	19
ioport	:	e400(size=256)
memory	:	dffdb000-dffdbfff
memory	:	dffa0000-dffbffff(prefetchable)
id:	
multimedia:1
description: 	Multimedia controller
product: 	SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
vendor: 	Philips Semiconductors
physical id: 	
9
bus info: 	
pci@0000:00:09.0
version: 	d1
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	saa7134
latency	=	64
maxlatency	=	38
mingnt	=	15
resources:	
irq	:	17
memory	:	dffff800-dfffffff
id:	
multimedia:2
description: 	Multimedia audio controller
product: 	CM8738
vendor: 	C-Media Electronics Inc
physical id: 	
b
bus info: 	
pci@0000:00:0b.0
version: 	10
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	C-Media PCI
latency	=	64
maxlatency	=	24
mingnt	=	2
resources:	
irq	:	18
ioport	:	e000(size=256)
id:	
scsi:0
physical id: 	
1
bus info: 	
usb@1:1
logical name: 	
scsi2
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description: 	SCSI Disk
physical id: 	
0.0.0
bus info: 	
scsi@2:0.0.0
logical name: 	
/dev/sdb
size: 	465GiB (500GB)
capabilities: 	partitioned partitioned:dos
configuration:	
signature	=	000a3f49
id:	
volume:0
description: 	Windows NTFS volume
physical id: 	
1
bus info: 	
scsi@2:0.0.0,1
logical name: 	
/dev/sdb1
version: 	3.1
serial: 	648afb77-c66e-7545-bc8a-2b976258d3d0
size: 	233GiB
capacity: 	233GiB
capabilities: 	primary ntfs initialized
configuration:	
clustersize	=	4096
created	=	2010-09-18 14:17:11
filesystem	=	ntfs
label	=	500gb
modified_by_chkdsk	=	true
mounted_on_nt4	=	true
resize_log_file	=	true
state	=	dirty
upgrade_on_mount	=	true
id:	
volume:1
description: 	Extended partition
physical id: 	
2
bus info: 	
scsi@2:0.0.0,2
logical name: 	
/dev/sdb2
size: 	232GiB
capacity: 	232GiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume:0
description: 	Linux filesystem partition
physical id: 	
5
logical name: 	
/dev/sdb5
capacity: 	228GiB
id:	
logicalvolume:1
description: 	Linux swap / Solaris partition
physical id: 	
6
logical name: 	
/dev/sdb6
capacity: 	4414MiB
capabilities: 	nofs
id:	
scsi:1
physical id: 	
2
bus info: 	
usb@1:3
logical name: 	
scsi3
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description: 	SCSI Disk
physical id: 	
0.0.0
bus info: 	
scsi@3:0.0.0
logical name: 	
/dev/sdc
size: 	3856MiB (4043MB)
capabilities: 	partitioned partitioned:dos
configuration:	
signature	=	00073639
id:	
volume
description: 	Windows FAT volume
vendor: 	mkdosfs
physical id: 	
1
bus info: 	
scsi@3:0.0.0,1
logical name: 	
/dev/sdc1
version: 	FAT32
serial: 	da94-227c
size: 	3852MiB
capacity: 	3852MiB
capabilities: 	primary bootable fat initialized
configuration:	
FATs	=	2
filesystem	=	fat

```

On another note, for now, how do I boot into Windows?

I've tried all the keystrokes in the Wubi guide, but my keyboard continues frozen during that screen.

Thank you

---

### Post by davidmohammed on 2010-09-19
ok,
  can I suggest you unplug all of your USB devices during the install.  Also I would suggest you pull out all of your PCI cards.

Just have a basic setup - motherboard with your HDD, DVD drive and your graphics card.

Reason - I think one of your devices is causing the install to stall.

---

