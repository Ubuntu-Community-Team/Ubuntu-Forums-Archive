---
title: "Can't install with alternate or Live CD"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by wackyiniraqi on 2008-07-08
I've tried the Live CD 8.04.1 i386 and everything loads just fine all hardware found and installed without any problems even my wireless card.  I tried to install and it stops at metacity common 63%.  I tried the alternate CD and it hangs at libgl1-mesa-dri, or at gnome-keyring.  I've tried to install about 10 times total.  I've run killdisk before many of those installs.....help me please before I lose my mind and shoot my pc in the face and throw it though my window.

---

### Post by Bubba64 on 2008-07-08
What is your computer setup. And how have you been installing with the desktop CD, and the alternative.

---

### Post by bigken on 2008-07-08
have you tried using a different type of media to burn your iso

---

### Post by wackyiniraqi on 2008-07-08
with the live cd i just did the install icon that's placed on the desktop.

the alternate cd i plugged into my network and just did the normal install...and followed the prompts

i don't understand what the options are under F6....
there's 
expert mode
acpi=off
noapic
nolapic
edd=on
free software only.


downloading the 7GB DVD now to try

I've tried several different disks...they all checkout ok with the check CD for defects option.

as far as hardware goes I don't know what's in this box other than it's a KIA kt400 board....this machine given to me by a relative since they don't need anymore...has 1gb of RAM so ok there.

---

### Post by THEDARKNESSHASCOME on 2008-07-08
I have a dual Booting system it has windows vista and ubuntu hardy haron on it both working perfectly and no lag at all. My problem is i downloaded ubuntu studio the dvd version and burned the iso to a dvd but when i try to install it goes to a manual setup which i have no problem with just it gives me a bunch of errors about missing files ive done this several times and it always does the same thing ive even tried open suse and all i got out of that was a  swipped computer. It only occures when i get the dvd downloads I've used back track 2 and 3 beta ubuntu feasty fawn gutsy gibbson and now hardy haron but i dont get what is wrong and i don't believe there is a live disk version of ubuntu studio. If so i have probably already downloaded it. Any one got any ideas also I've tried this with a fresh install and it still doesn't work

---

### Post by THEDARKNESSHASCOME on 2008-07-08
> **wackyiniraqi said:**
> with the live cd i just did the install icon that's placed on the desktop.

the alternate cd i plugged into my network and just did the normal install...and followed the prompts

i don't understand what the options are under F6....
there's 
expert mode
acpi=off
noapic
nolapic
edd=on
free software only.


downloading the 7GB DVD now to try

I've tried several different disks...they all checkout ok with the check CD for defects option.

as far as hardware goes I don't know what's in this box other than it's a KIA kt400 board....this machine given to me by a relative since they don't need anymore...has 1gb of RAM so ok there.

do you have windows on the computer you are trying to install to?

---

### Post by THEDARKNESSHASCOME on 2008-07-08
btw if you do get dxdiag in the run box get specs to be sure and check if your comp meets the minimum requirements for installation also check to see its not just your disk drive. its always a good idea to check everything try cleaning the lens to your disk drive if its a laptop that part will be easy. btw post your specs

---

### Post by wackyiniraqi on 2008-07-08
there is no OS installed on this machine.

---

### Post by wackyiniraqi on 2008-07-08
anyone know of a bootable dxdiag type program i could use to get the info on this machine?

---

### Post by THEDARKNESSHASCOME on 2008-07-08
goto the bios it will tell all system info when you turn on the computer it will tell you what to press at boot screen in order to get there like mine shows an acer logo at the bottom of it it says to press f2 it is different for most computers. when you get there flip through till you find your specs.

---

### Post by wackyiniraqi on 2008-07-09
well here's the export I got from hardinfo...took a long time to get Live CD to load...did another killdisk changed CMOS to safest configuration...

here's what's in this machine as per hardinfo

Computer
Summary
Computer
Processor	AMD Athlon(tm) XP 2400+
Memory	515MB (296MB used)
Operating System	Ubuntu 8.04.1
User Name	ubuntu (Live session user)
Date/Time	Wed 09 Jul 2008 07:45:10 AM UTC
Display
Resolution	1280x1024 pixels
OpenGL Renderer	Mesa GLX Indirect
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	VIA8233 - VIA 8235
Input Devices
Macintosh mouse button emulation	
Microsoft Comfort Curve Keyboard 2000	
Microsoft Comfort Curve Keyboard 2000	
PC Speaker	
Power Button (FF)	
Power Button (CM)	
Sleep Button (CM)	
Microsoft Microsoft Optical Mouse with Tilt Wheel	
Printers (CUPS)
PDF	
IDE Disks
SCSI Disks
ATA SAMSUNG SP8004H	
ATA WDC WD1200BB-00C	
Model: DVD-ROM Rev: 1.18 DVD-ROM	
LITE-ON LTR-52246S	
Operating System
Version
Kernel	Linux 2.6.24-19-generic (i686)
Compiled	#1 SMP Wed Jun 18 14:43:41 UTC 2008
C Library	GNU C Library version 2.7 (stable)
Distribution	Ubuntu 8.04.1
Current Session
Computer Name	ubuntu
User Name	ubuntu (Live session user)
Home Directory	/home/ubuntu
Desktop Environment	GNOME 2.22 (session name: Default)
Misc
Uptime	1 hour, 10 minutes
Load Average	0.68, 0.53, 0.41
Kernel Modules
Loaded Modules
wlan_ccmp	802.11 wireless support: AES-CCM cipher
af_packet	
ipv6	IPv6 protocol stack for Linux
rfcomm	Bluetooth RFCOMM ver 1.8
l2cap	Bluetooth L2CAP ver 2.9
bluetooth	Bluetooth Core ver 2.11
ppdev	
lp	
cpufreq_userspace	CPUfreq policy governor 'userspace'
cpufreq_stats	'cpufreq_stats' - A driver to export cpufreq stats through sysfs filesystem
cpufreq_powersave	CPUfreq policy governor 'powersave'
cpufreq_ondemand	'cpufreq_ondemand' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
freq_table	CPUfreq frequency table helpers
cpufreq_conservative	'cpufreq_conservative' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors optimised for use in a battery environment
video	ACPI Video Driver
output	Display Output Switcher Lowlevel Control Abstraction
sbs	Smart Battery System ACPI interface driver
sbshc	ACPI SMBus HC driver
container	ACPI container driver
dock	ACPI Dock Station Driver
ac	ACPI AC Adapter Driver
iptable_filter	iptables filter table
ip_tables	IPv4 packet filter
x_tables	[ip,ip6,arp]_tables backend module
i2c_viapro	vt82c596 SMBus driver
wlan_scan_sta	802.11 wireless support: default station scanner
ath_rate_sample	SampleRate bit-rate selection algorithm for Atheros devices
snd_via82xx	VIA VT82xx audio
gameport	Generic gameport layer
snd_ac97_codec	Universal interface for Audio Codec '97
ac97_bus	
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
snd_page_alloc	Memory allocator for ALSA system.
snd_mpu401_uart	Routines for control of MPU-401 in UART mode
snd_seq_dummy	ALSA sequencer MIDI-through client
snd_seq_oss	OSS-compatible sequencer module
joydev	Joystick device interfaces
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
i2c_core	I2C-Bus main module
snd	Advanced Linux Sound Architecture driver for soundcards.
hisax	ISDN4Linux: Driver for passive ISDN cards
via_ircc	VIA IrDA Device Driver
psmouse	PS/2 mouse driver
ath_pci	Support for Atheros 802.11 wireless LAN cards.
via_agp	
isdn	ISDN4Linux: link layer
irda	The Linux IrDA Protocol Stack
shpchp	Standard Hot Plug PCI Controller Driver
parport_pc	PC-style parallel port driver
serio_raw	Raw serio driver
button	ACPI Button Driver
agpgart	AGP GART driver
slhc	
evdev	Input driver event char devices
crc_ccitt	CRC-CCITT calculations
pci_hotplug	PCI Hot Plug PCI Core
parport	
wlan	802.11 wireless LAN protocol support
ath_hal	Atheros Hardware Access Layer (HAL)
soundcore	Core sound module
pcspkr	PC Speaker beeper driver
battery	ACPI Battery Driver
squashfs	squashfs 3.3, a compressed read-only filesystem
loop	
unionfs	Unionfs 1.4 ([http://unionfs.filesystems.org/](http://unionfs.filesystems.org/))
nls_cp437	
isofs	
ext3	Second Extended Filesystem with journaling extensions
jbd	
mbcache	Meta block cache (for extended attributes)
usbhid	USB HID core driver
hid	
sg	SCSI generic (sg) driver
sr_mod	SCSI cdrom (sr) driver
cdrom	
sd_mod	SCSI disk (sd) driver
pata_via	low-level driver for VIA PATA
pata_acpi	SCSI low-level driver for ATA in ACPI mode
floppy	
ata_generic	low-level driver for generic ATA
libata	Library module for ATA devices
ehci_hcd	10 Dec 2004 USB 2.0 'Enhanced' Host Controller (EHCI) Driver
uhci_hcd	USB Universal Host Controller Interface driver
scsi_mod	SCSI core
ohci1394	Driver for PCI OHCI IEEE-1394 controllers
usbcore	
pdc202xx_old	PCI driver module for older Promise IDE
ide_core	
ieee1394	
thermal	ACPI Thermal Zone Driver
processor	ACPI Processor Driver
fan	ACPI Fan Driver
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
fuse	Filesystem in Userspace
Boots
Boots
Wed Jul 9 00:36 - 07:45 (07:08)	Kernel 2.6.24-19-generi
Filesystems
Mounted File Systems
proc	0.0 B total, 0.0 B free
sysfs	0.0 B total, 0.0 B free
tmpfs	251.7 MiB total, 235.6 MiB free
tmpfs	251.7 MiB total, 235.6 MiB free
varrun	251.7 MiB total, 251.6 MiB free
varlock	251.7 MiB total, 251.7 MiB free
udev	251.7 MiB total, 251.7 MiB free
devshm	251.7 MiB total, 251.7 MiB free
devpts	0.0 B total, 0.0 B free
tmpfs	251.7 MiB total, 251.7 MiB free
gvfs-fuse-daemon	251.7 MiB total, 164.2 MiB free
/dev/sdb1	109.5 GiB total, 102.1 GiB free
Shared Directories
SAMBA
NFS
Display
Display
Resolution	1280x1024 pixels
Vendor	The X.Org Foundation
Version	1.4.0.90
Monitors
Monitor 0	1280x1024 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
Extended-Visual-Information	
GLX	
MIT-SCREEN-SAVER	
MIT-SHM	
MIT-SUNDRY-NONSTANDARD	
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
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
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	Mesa project
Renderer	Mesa GLX Indirect
Version	1.4 (2.1 Mesa 7.0.3-rc2)
Direct Rendering	No
Network Interfaces
Network Interfaces
lo	Sent 0.47MiB, received 0.47MiB (127.0.0.1)
wifi0	Sent 0.83MiB, received 20.80MiB
ath0	Sent 0.57MiB, received 9.58MiB (192.168.1.103)
Users
Human Users
System Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
dhcp	
syslog	
klog	
hplip	HPLIP system user
avahi-autoipd	Avahi autoip daemon
gdm	Gnome Display Manager
pulse	PulseAudio daemon
messagebus	
avahi	Avahi mDNS daemon
polkituser	PolicyKit
haldaemon	Hardware abstraction layer
ubuntu	Live session user
Devices
Processor
Processor
Name	AMD Athlon(tm) XP 2400+
Family, model, stepping	6, 8, 1 (AMD Athlon XP/MP (Thoroughbred))
Vendor	AuthenticAMD
Configuration
Cache Size	256kb
Frequency	1994.51MHz
BogoMIPS	3992.65
Byte Order	Little Endian
Features
FDIV Bug	no
HLT Bug	no
F00F Bug	no
Coma Bug	no
Has FPU	yes
Capabilities
fpu	Floating Point Unit
vme	Virtual 86 Mode Extension
de	Debug Extensions - I/O breakpoints
pse	Page Size Extensions (4MB pages)
tsc	Time Stamp Counter and RDTSC instruction
msr	Model Specific Registers
pae	Physical Address Extensions
mce	Machine Check Architeture
cx8	CMPXCHG8 instruction
apic	Advanced Programmable Interrupt Controller
sep	Fast System Call (SYSENTER/SYSEXIT)
mtrr	Memory Type Range Registers
pge	Page Global Enable
mca	Machine Check Architecture
cmov	Conditional Move instruction
pat	Page Attribute Table
pse36	36bit Page Size Extensions
mmx	MMX technology
fxsr	FXSAVE and FXRSTOR instructions
sse	SSE instructions
syscall	SYSCALL and SYSEXIT instructions
mmxext	Extended MMX Technology
3dnowext	Extended 3DNow! Technology
3dnow	3DNow! Technology
up	
ts	
Memory
Memory
Total Memory	515580 kB
Free Memory	32456 kB
Buffers	30728 kB
Cached	187596 kB
Cached Swap	5892 kB
Active	315308 kB
Inactive	132196 kB
High Memory	0 kB
Free High Memory	0 kB
Low Memory	515580 kB
Free Low Memory	32456 kB
Virtual Memory	1510068 kB
Free Virtual Memory	1431208 kB
Dirty	0 kB
Writeback	0 kB
AnonPages	224324 kB
Mapped	57260 kB
Slab	21324 kB
SReclaimable	13208 kB
SUnreclaim	8116 kB
PageTables	2232 kB
NFS_Unstable	0 kB
Bounce	0 kB
CommitLimit	1767856 kB
Committed_AS	669180 kB
VmallocTotal	507896 kB
VmallocUsed	7384 kB
VmallocChunk	500036 kB
PCI Devices
PCI Devices
Host bridge	VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
PCI bridge	VIA Technologies, Inc. VT8235 PCI Bridge
Communication controller	Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
Ethernet controller	Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor
FireWire (IEEE 1394)	VIA Technologies, Inc. IEEE 1394 Host Controller
RAID bus controller	Promise Technology, Inc. PDC20265
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. USB 2.0
ISA bridge	VIA Technologies, Inc. VT8235 ISA Bridge
IDE interface	VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
Multimedia audio controller	VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller
VGA compatible controller	nVidia Corporation NV44A [GeForce 6200]
USB Devices
Printers
Printers (CUPS)
PDF	
Battery
No batteries
No batteries found on this system	
Sensors
ACPI Thermal Zone
THRM	40°C
Input Devices
Input Devices
Macintosh mouse button emulation	
Microsoft Comfort Curve Keyboard 2000	
Microsoft Comfort Curve Keyboard 2000	
PC Speaker	
Power Button (FF)	
Power Button (CM)	
Sleep Button (CM)	
Microsoft Microsoft Optical Mouse with Tilt Wheel	
Storage
IDE Disks
SCSI Disks
ATA SAMSUNG SP8004H	
ATA WDC WD1200BB-00C	
Model: DVD-ROM Rev: 1.18 DVD-ROM	
LITE-ON LTR-52246S	
Benchmarks
CPU ZLib
CPU ZLib
This Machine	0.000
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561
CPU Fibonacci
CPU Fibonacci
This Machine	4.741
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682
CPU MD5
CPU MD5
This Machine	47.611
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998
CPU SHA1
CPU SHA1
This Machine	50.701
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776
CPU Blowfish
CPU Blowfish
This Machine	21.053
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713
FPU Raytracing
FPU Raytracing
This Machine	26.585
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647

---

### Post by wackyiniraqi on 2008-07-09
that's a bit much I know but working with LiveCD and what little I can install and run.....

---

### Post by THEDARKNESSHASCOME on 2008-07-09
kk you have an older computer but it should be fine im assuming you have the standard bios set up for it to run off a disk and everything. Now just try this one more time and post exactly what happens. Boot in a standard hardy haron disk (live cd)now a little bit off notice make sure you are burning the disk at the correct speed. cuz i burned one at 64 times and the disk was set for 32 and part of the data was corrupt so it screwed the install. Instead of loading into Ubuntu select the installation feature on the main menu instead of logging in that install never worked when i tried installing while running the os i believe this is your problem. I installed fine when i tryed because ive had Ubuntu since feasty fawn so i installed immediately. 

basic directions---

make sure disk was burned at correct speed.
load the disk but do the install not the live experience then install. 
the install im refering to is the secound option when you are at the disks menu before you goto the live use of the os.
the live experience install doesnt work

---

### Post by wackyiniraqi on 2008-07-09
kk intalling now...hopefully it was some advanced setting in the cmos that was causing my problems.....burned disk with Brasero on laptop...should be good.

---

### Post by THEDARKNESSHASCOME on 2008-07-09
which install did you use btw some times the install gets stuck and stops working  its happened to me once and to my friend 3 times so the disk might be fine if it messes up and use the install that is autimatic but you are not in live distro mode on the ubuntu hardy live cd

---

### Post by wackyiniraqi on 2008-07-09
holy sweet jesus.....WOOT.....must have been something in the CMOS....Ubuntu now loaded....thank you so much for your help.....hmmm wonder if it will be able to handle compiz-fusion ?  Probably not lol

---

### Post by THEDARKNESSHASCOME on 2008-07-09
yes to the basic stuff but not so much for the intense graphical items. my friend had an 8600 nvidia 4gb ddr2 ram and amd dual core 2.0ghz processor and it lagged on the high end effects but it was perfect for the cube effects and shadows

---

### Post by wackyiniraqi on 2008-07-09
cool yea I've got a tyan s2460 MP that Tyan tech support is currently working on..dual athlons are fun...

---

### Post by THEDARKNESSHASCOME on 2008-07-09
you never officially thanked me on the post.....jk

---

### Post by wackyiniraqi on 2008-07-10
lol how do i do that?

---

### Post by grundygreen on 2008-07-10
> **wackyiniraqi said:**
> anyone know of a bootable dxdiag type program i could use to get the info on this machine?

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

A good general toolbox disk.

---

