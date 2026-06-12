---
title: "[Newbie] Cannot boot after upgrade..."
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by mpetrovic on 2007-10-06
Hello everyone!

With a lot of effort I have managed yesterday to install Ubuntu 7.04 on my laptop (Acer 7720G, a model with 2 SATA HDD's). I was really proud of myself as I am really not experienced in *nix systems, but there wasn't a day passed and problems have occured...

Right now, after I have upgraded the system, my boot loader is showing several choices:

```
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)

```

so, booting ver. 2.6.20-15-generic is still OK. But booting 2.6.20-16-generic leads to a freezing booting screen, the one that shows the Ubuntu logo with a kind of percentage control. It starts moving up to 15-20 percent, then everything stops. Keyboard is unresponsive (ctrl+alt+del or ctrl+alt+Fx are not working).

Now, while I initially installed Ubuntu, I did some modifications:
- enabled SATA support (learned how [here]("http://ubuntuforums.org/showthread.php?t=421588"))
- enabled graphic adapter recognition and support ([here]("http://ubuntuforums.org/showthread.php?t=497284"))
- and enabled sound system

When I try to boot the recovery mode option, it stops here:

```
Begin: Running /scripts/init-bottom...
Done.
* Reading files needed to boot... [OK]
* Setting preliminary keymap... [OK]
* Preparing restricted drivers... [OK]
* Starting basic networking... [OK]
* Loading hardware drivers...
[   21.064000] Linux agpart interface v0.12 (c) Dave Jones
[   21.144000] agpart: Detected an Intel 965GM Chipset
[   21.160000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
```

And then it just stops...

So is there anything I can do to make the updated version work?

My hardware info is:
```
Operating System
Version
Kernel	Linux 2.6.20-15-generic (i686)
Compiled	#2 SMP Sun Apr 15 07:36:31 UTC 2007
C Library	GNU C Library version 2.5 (stable)
Distribution	Ubuntu 7.04
Current Session
Computer Name	Acer7720
User Name	petra
Home Directory	/home/petra
Desktop Environment	GNOME 2.18 (session name: Default)
Misc
Uptime	11 minutes
Load Average	0.23, 0.40, 0.29
Kernel Modules
Loaded Modules
michael_mic	Michael MIC
arc4	ARC4 Cipher Algorithm
ecb	ECB block cipher algorithm
blkcipher	Generic block chaining cipher type
ieee80211_crypt_tkip	Host AP crypt: TKIP
binfmt_misc	
nfs	
nfsd	
exportfs	
lockd	NFS file locking service version 0.5.
sunrpc	
ppdev	
acpi_cpufreq	ACPI Processor P-States Driver
cpufreq_userspace	CPUfreq policy governor 'userspace'
cpufreq_conservative	'cpufreq_conservative' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors optimised for use in a battery environment
cpufreq_stats	'cpufreq_stats' - A driver to export cpufreq statsthrough sysfs filesystem
cpufreq_powersave	CPUfreq policy governor 'powersave'
cpufreq_ondemand	'cpufreq_ondemand' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
freq_table	CPUfreq frequency table helpers
sony_acpi	ACPI Sony Notebook Control Driver v0.2
tc1100_wmi	ACPI WMI Driver
pcc_acpi	ACPI HotKey driver for Panasonic Let's Note laptops
dev_acpi	Device file access to ACPI namespace
video	ACPI Video Driver
ac	ACPI AC Adapter Driver
button	ACPI Button Driver
container	ACPI container driver
asus_acpi	Asus Laptop ACPI Extras Driver
backlight	Backlight Lowlevel Control Abstraction
dock	ACPI Dock Station Driver
sbs	Smart Battery System ACPI interface driver
i2c_ec	ACPI EC SMBus driver
battery	ACPI Battery Driver
ipv6	IPv6 protocol stack for Linux
nls_utf8	
ntfs	NTFS 1.2/3.x driver - Copyright (c) 2001-2007 Anton Altaparmakov
sbp2	IEEE-1394 SBP-2 protocol driver
parport_pc	PC-style parallel port driver
lp	
parport	
fuse	Filesystem in Userspace
nvidia	
snd_hda_intel	Intel HDA driver
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
snd_page_alloc	Memory allocator for ALSA system.
snd_hwdep	Hardware dependent layer
snd_seq_oss	OSS-compatible sequencer module
ipw3945	Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
snd_seq_midi_event	MIDI byte <-> sequencer event coder
af_packet	
agpgart	AGP GART driver
ieee80211	802.11 data/management/control stack
ieee80211_crypt	HostAP crypto
snd_seq	Advanced Linux Sound Architecture sequencer.
uvcvideo	USB Video Class driver
i2c_core	I2C-Bus main module
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
sdhci	Secure Digital Host Controller Interface driver
xpad	driver for Xbox controllers
mmc_core	
videodev	Device registrar for Video4Linux drivers v2
v4l1_compat	v4l(1) compatibility layer for v4l2 drivers.
v4l2_common	misc helper functions for v4l2 device drivers
serio_raw	Raw serio driver
psmouse	PS/2 mouse driver
shpchp	Standard Hot Plug PCI Controller Driver
pci_hotplug	PCI Hot Plug PCI Core
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
evdev	Input driver event char devices
tsdev	Input driver to touchscreen converter
ext3	Second Extended Filesystem with journaling extensions
jbd	
mbcache	Meta block cache (for extended attributes)
sg	SCSI generic (sg) driver
sd_mod	SCSI disk (sd) driver
usbhid	USB HID core driver
hid	
ide_cd	ATAPI CD-ROM Driver
cdrom	
ata_generic	low-level driver for generic ATA
ahci	AHCI SATA low-level driver
libata	Library module for ATA devices
scsi_mod	SCSI core
ohci1394	Driver for PCI OHCI IEEE-1394 controllers
ieee1394	
generic	PCI driver module for generic PCI IDE
tg3	Broadcom Tigon3 ethernet driver
uhci_hcd	USB Universal Host Controller Interface driver
ehci_hcd	10 Dec 2004 USB 2.0 'Enhanced' Host Controller (EHCI) Driver
usbcore	
thermal	ACPI Thermal Zone Driver
processor	ACPI Processor Driver
fan	ACPI Fan Driver
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
vesafb	
capability	Standard Linux Capabilities Security Module
commoncap	Standard Linux Common Capabilities Security Module
piix	PCI driver module for Intel PIIX IDE
Filesystems
Mounted File Systems
/dev/sdb5	70.6 GiB total, 57.9 GiB free
proc	0.0 B total, 0.0 B free
/sys	0.0 B total, 0.0 B free
varrun	1012.9 MiB total, 1012.7 MiB free
varlock	1012.9 MiB total, 1012.9 MiB free
procbususb	1012.9 MiB total, 1012.8 MiB free
udev	1012.9 MiB total, 1012.8 MiB free
devshm	1012.9 MiB total, 1012.9 MiB free
devpts	0.0 B total, 0.0 B free
lrm	1012.9 MiB total, 979.9 MiB free
/dev/sda1	9.8 GiB total, 622.0 MiB free
/dev/sda2	69.8 GiB total, 39.6 GiB free
/dev/sda3	69.5 GiB total, 64.2 GiB free
/dev/sdb1	74.6 GiB total, 73.8 GiB free
nfsd	0.0 B total, 0.0 B free
rpc_pipefs	0.0 B total, 0.0 B free
binfmt_misc	0.0 B total, 0.0 B free
Display
Display
Resolution	1440x900 pixels
Vendor	The X.Org Foundation
Version	7.2.0
Monitors
Monitor 0	1440x900 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DPMS	
Extended-Visual-Information	
GLX	
MIT-SCREEN-SAVER	
MIT-SHM	
MIT-SUNDRY-NONSTANDARD	
NV-CONTROL	
NV-GLX	
RANDR	
RENDER	
SECURITY	
SHAPE	
SYNC	
TOG-CUP	
X-Resource	
XAccessControlExtension	
XC-APPGROUP	
XC-MISC	
XFIXES	
XFree86-Bigfont	
XFree86-DGA	
XFree86-Misc	
XFree86-VidModeExtension	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	NVIDIA Corporation
Renderer	GeForce 8400M GS/PCI/SSE2
Version	2.1.1 NVIDIA 100.14.19
Direct Rendering	Yes
Network Interfaces
Network Interfaces
lo	Sent 0.01MiB, received 0.01MiB (127.0.0.1)
eth0	Sent 0.00MiB, received 0.00MiB
eth1	Sent 0.54MiB, received 4.55MiB (192.168.1.114)
Devices
Processor
Processors
Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz	800.00MHz
Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz	800.00MHz
Memory
Memory
Total Memory	2074516 kB
Free Memory	1230332 kB
Buffers	62644 kB
Cached	405692 kB
Cached Swap	0 kB
Active	517896 kB
Inactive	272332 kB
High Memory	1178000 kB
Free High Memory	433804 kB
Low Memory	896516 kB
Free Low Memory	796528 kB
Virtual Memory	2891660 kB
Free Virtual Memory	2891660 kB
Dirty	524 kB
Writeback	0 kB
AnonPages	321852 kB
Mapped	88508 kB
Slab	28096 kB
SReclaimable	12976 kB
SUnreclaim	15120 kB
PageTables	2752 kB
NFS_Unstable	0 kB
Bounce	0 kB
CommitLimit	3928916 kB
Committed_AS	1054820 kB
VmallocTotal	114680 kB
VmallocUsed	46460 kB
VmallocChunk	63476 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation Mobile Memory Controller Hub
PCI bridge	Intel Corporation Mobile PCI Express Root Port
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
Audio device	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801 Mobile PCI Bridge
ISA bridge	Intel Corporation Mobile LPC Interface Controller
IDE interface	Intel Corporation Mobile IDE Controller
SATA controller	Intel Corporation Mobile SATA AHCI Controller
SMBus	Intel Corporation 82801H
VGA compatible controller	nVidia Corporation Unknown device 0427
Ethernet controller	Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express
Network controller	Intel Corporation PRO/Wireless 3945ABG Network Connection
FireWire (IEEE 1394)	Ricoh Co Ltd Unknown device 0832
USB Devices
UHCI Host Controller
UHCI Host Controller
USB Gaming Mouse	
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
EHCI Host Controller
Acer CrystalEye webcam	
EHCI Host Controller
Printers
Printers (CUPS)
PhotoSmart-C5100	
Battery
Battery: BAT0
State	charged (load: 0 mA)
Capacity	4000 mAh / 4000 mAh (100.00%)
Battery Technology	rechargeable (Lion)
Model Number	GC86508SAT0
Serial Number	
Sensors
ACPI Thermal Zone
TZ01	45Â°C
Hard Disk Temperature
WDC WD1600BEVS-22RST0 (/dev/sda)	38Â°C
Input Devices
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Logitech USB Gaming Mouse	
ImPS/2 Generic Wheel Mouse	
Power Button (FF)	
Power Button (CM)	
Lid Switch	
Sleep Button (CM)	
Storage
IDE Disks
PIONEER DVD-RW DVR-K17RS	
SCSI Disks
ATA WDC WD1600BEVS-2	
ATA WDC WD1600BEVS-2
```

After the system halts, and I do hard reset, the x server cannot work in older version, so I have to reinstall the NVidia drivers.

If you need any further information, please also explain how should I get it :) 

Thanks in advance!

---

### Post by mpetrovic on 2007-10-07
Anyone? Please???

---

### Post by mpetrovic on 2007-10-08
So, now the problem excalated... Every time I shutdown computer, during the next boot I have a problem with xorg and video settings, and each time I need to install NVidia drivers again...

So, please, could anyone help me with this? Thanks in advance...

---

