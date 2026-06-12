---
title: "Kernal panic - not syncing"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by petersfreeman on 2013-01-28
I have a desktop that I can install Ubuntu 10.04, 10.10, 11.04, 11.10 but when I try to install 12.04 or 12.10, I get this message:

"kernal panic - not syncing: fatal exception in interrupt"

I figured that the LiveCD installer was the problem, So I installed 11.10 and then did an upgrade from 11.10 to 12.04 using the update manager.  After rebootoing, my desktop would not get to the Grub menu as it would produce the same error.

Next I tried the Alternate CD.  It installed 12.04 fine but after rebooting, it also would not get to the Grub menu and it would produce the same error.

I thought it might be my BIOS but have not figured a way of upgrading it as the installation requires Windows to be running on my desktop, which I do not have.

I assume that between 11.10 and 12.04, The Ubuntu or Linux software engineers have changed some very low level code and it conflicts with my hardware.

How can I install more recent Ubuntu releases?

Thanks,

Peter Freeman

----------------------------------------------------------------------
I am using a rebranded Acer that is about 2 years old (Gateway DX4850).  Here are the relevent specifications:

```

**Computer**
Processor	8x Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
Memory	8177MB (1633MB used)
Operating System	Ubuntu 11.10

**Display**
Resolution	1920x1080 pixels
OpenGL Renderer	GeForce GT 420/PCI/SSE2
X11 Vendor	The X.Org Foundation

**Operating System**
Version
Kernel	Linux 3.0.0-30-generic (x86_64)
Compiled	#47-Ubuntu SMP Wed Jan 2 23:16:29 UTC 2013
C Library	Unknown
Default C Compiler	GNU C Compiler version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
Distribution	Ubuntu 11.10

**Loaded Modules**
xts	XTS block cipher mode
gf128mul	Functions for multiplying elements of GF(2^128)
snd_hrtimer	ALSA hrtimer backend
bnep	Bluetooth BNEP ver 1.3
rfcomm	Bluetooth RFCOMM ver 1.11
bluetooth	Bluetooth Core ver 2.16
pci_stub	
vboxpci	Oracle VM VirtualBox PCI access Driver
vboxnetadp	Oracle VM VirtualBox Network Adapter Driver
vboxnetflt	Oracle VM VirtualBox Network Filter Driver
vboxdrv	Oracle VM VirtualBox Support Driver
dm_crypt	device-mapper target for transparent encryption / decryption
parport_pc	PC-style parallel port driver
ppdev	
nvidia	
snd_hda_codec_hdmi	HDMI HD-audio codec
snd_hda_codec_realtek	Realtek HD-audio codec
arc4	ARC4 Cipher Algorithm
binfmt_misc	
rt2800pci	Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
rt2800lib	Ralink RT2800 library
snd_hda_intel	Intel HDA driver
crc_ccitt	CRC-CCITT calculations
joydev	Joystick device interfaces
snd_hda_codec	HDA codec core
rt2x00pci	rt2x00 pci library
snd_hwdep	Hardware dependent layer
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
rt2x00lib	rt2x00 library
snd_pcm	Midlevel PCM code for ALSA.
mac80211	IEEE 802.11 subsystem
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
cfg80211	wireless configuration support
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
mei	Intel(R) Management Engine Interface
eeprom_93cx6	EEPROM 93cx6 chip driver
wmi	ACPI-WMI Mapping Driver
psmouse	PS/2 mouse driver
serio_raw	Raw serio driver
lp	
parport	
vesafb	
ses	SCSI Enclosure Services (ses) driver
enclosure	Enclosure Services
usb_storage	USB Mass Storage driver for Linux
usbhid	USB HID core driver
hid	
ahci	AHCI SATA low-level driver
libahci	Common AHCI SATA low-level routines
e1000e	Intel(R) PRO/1000 Network Driver

**OpenGL**
Vendor	NVIDIA Corporation
Renderer	GeForce GT 420/PCI/SSE2
Version	4.1.0 NVIDIA 280.13
Direct Rendering

**Processors**
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	3200.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	3401.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz
Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz	1600.00MHz

**Memory**
Total Memory	8177268 kB
Free Memory	5123536 kB
Buffers	140756 kB
Cached	1454944 kB
Cached Swap	0 kB
Active	1451196 kB
Inactive	1194148 kB
Active(anon)	1050688 kB
Inactive(anon)	2940 kB
Active(file)	400508 kB
Inactive(file)	1191208 kB
Unevictable	32 kB
Mlocked	32 kB
Virtual Memory	8365052 kB
Free Virtual Memory	8365052 kB
Dirty	396 kB
Writeback	0 kB
AnonPages	1049660 kB
Mapped	294996 kB
Shmem	4000 kB
Slab	182512 kB
SReclaimable	117440 kB
SUnreclaim	65072 kB
KernelStack	5488 kB
PageTables	36864 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	12453684 kB
Committed_AS	4260732 kB
VmallocTotal	34359738367 kB
VmallocUsed	359236 kB
VmallocChunk	34359364604 kB
HardwareCorrupted	0 kB
AnonHugePages	0 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	2048 kB
DirectMap4k	202752 kB
DirectMap2M	8169472 kB

**PCI Devices**
Host bridge	Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
PCI bridge	Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
Communication controller	Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
Ethernet controller	Intel Corporation 82579V Gigabit Network Connection (rev 04)
USB Controller	Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
Audio device	Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
PCI bridge	Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
PCI bridge	Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
USB Controller	Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
ISA bridge	Intel Corporation H67 Express Chipset Family LPC Controller (rev 04)
SATA controller	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
SMBus	Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
VGA compatible controller	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
Audio device	nVidia Corporation GF108 High Definition Audio Controller (rev a1)
Network controller	Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

**Battery**
No batteries
No batteries found on this system	

**Storage**
SCSI Disks
ATA WDC WD10EARS-22Y	
ATAPI DVD A DH16ABSH	
WD My Book 1140	
WD SES Device	
WD My Book 1140	
WD SES Device	
Seagate Desktop	
Seagate Desktop	
Generic- Compact Flash	
Generic- SM/xD-Picture	
Generic- SD/MMC	
Generic- MS/MS-Pro/HG	
Generic- SD/MMC/MS/MSPRO	
WDC WD12 00BEVS-60LAT0	
ST310003 33AS	

**BIOS**
Date	02/11/2011
Vendor	American Megatrends Inc. (www.ami.com)
Version	P01-A3

**Board**
Name	Predator G3600
Vendor	Acer (www.acer.com)

**I/O Ports**
0000-0cf7 	PCI Bus 0000:00
0000-001f 	dma1
0020-0021 	pic1
0040-0043 	timer0
0050-0053 	timer1
0060-0060 	keyboard
0064-0064 	keyboard
0070-0071 	rtc0
0080-008f 	dma page reg
00a0-00a1 	pic2
00c0-00df 	dma2
00f0-00ff 	fpu
03c0-03df 	vesafb
0400-0453 	pnp 00:08
0400-0403 	ACPI PM1a_EVT_BLK
0404-0405 	ACPI PM1a_CNT_BLK
0408-040b 	ACPI PM_TMR
0410-0415 	ACPI CPU throttle
0420-042f 	ACPI GPE0_BLK
0450-0450 	ACPI PM2_CNT_BLK
0454-0457 	pnp 00:09
0458-047f 	pnp 00:08
04d0-04d1 	pnp 00:06
0500-057f 	pnp 00:08
0a00-0a1f 	pnp 00:02
0a20-0a2f 	pnp 00:02
0a30-0a3f 	pnp 00:02
0cf8-0cff 	PCI conf1
0d00-ffff 	PCI Bus 0000:00
1180-119f 	pnp 00:08
e000-efff 	PCI Bus 0000:01
e000-e07f 	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
f000-f01f 	Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
f020-f03f 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
f020-f03f 	AHCI SATA low-level driver
f040-f05f 	Intel Corporation 82579V Gigabit Network Connection (rev 04)
f060-f063 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
f060-f063 	AHCI SATA low-level driver
f070-f077 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
f070-f077 	AHCI SATA low-level driver
f080-f083 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
f080-f083 	AHCI SATA low-level driver
f090-f097 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
f090-f097 	AHCI SATA low-level driver

**Memory**
00000000-0000ffff 	reserved
00010000-0009abff 	System RAM
0009ac00-0009ffff 	reserved
000a0000-000bffff 	PCI Bus 0000:00
000c0000-000c7fff 	Video ROM
000c8000-000dffff 	PCI Bus 0000:00
000e0000-000fffff 	reserved
000f0000-000fffff 	System ROM
00100000-bf3e0fff 	System RAM
01000000-0160586b 	Kernel code
0160586c-01cbc27f 	Kernel data
01dbd000-01f0ffff 	Kernel bss
bf3e1000-bf435fff 	ACPI Non-volatile Storage
bf436000-bf4cafff 	reserved
bf4cb000-bf4cbfff 	ACPI Non-volatile Storage
bf4cc000-bf4d0fff 	reserved
bf4d1000-bf4d1fff 	System RAM
bf4d2000-bf4dbfff 	ACPI Non-volatile Storage
bf4dc000-bf52ffff 	reserved
bf530000-bf572fff 	ACPI Non-volatile Storage
bf573000-bf7fffff 	System RAM
bf800000-bfffffff 	RAM buffer
e0000000-efffffff 	PCI MMCONFIG 0000 [bus 00-ff]
e0000000-efffffff 	pnp 00:01
f0000000-ffffffff 	PCI Bus 0000:00
f0000000-f9ffffff 	PCI Bus 0000:01
f0000000-f7ffffff 	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
f8000000-f9ffffff 	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
f9000000-f94fffff 	vesafb
fa000000-fb0fffff 	PCI Bus 0000:01
fa000000-faffffff 	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
fa000000-faffffff 	nvidia
fb000000-fb07ffff 	nVidia Corporation GeForce GT 420 (rev a1) (prog-if 00 [VGA controller])
fb080000-fb083fff 	nVidia Corporation GF108 High Definition Audio Controller (rev a1)
fb080000-fb083fff 	ICH HD audio
fb100000-fb1fffff 	PCI Bus 0000:03
fb100000-fb10ffff 	Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
fb100000-fb10ffff 	Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
fb200000-fb21ffff 	Intel Corporation 82579V Gigabit Network Connection (rev 04)
fb200000-fb21ffff 	Intel(R) PRO/1000 Network Driver
fb220000-fb223fff 	Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
fb220000-fb223fff 	ICH HD audio
fb224000-fb2240ff 	Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
fb225000-fb2257ff 	Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
fb225000-fb2257ff 	AHCI SATA low-level driver
fb226000-fb2263ff 	Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
fb226000-fb2263ff 	ehci_hcd
fb227000-fb2273ff 	Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
fb227000-fb2273ff 	ehci_hcd
fb228000-fb228fff 	Intel Corporation 82579V Gigabit Network Connection (rev 04)
fb228000-fb228fff 	Intel(R) PRO/1000 Network Driver
fb229000-fb22900f 	Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
fb229000-fb22900f 	Intel(R) Management Engine Interface
fec00000-fec003ff 	IOAPIC 0
fed00000-fed003ff 	HPET 0
fed08000-fed08fff 	pnp 00:08
fed10000-fed19fff 	pnp 00:01
fed1c000-fed3ffff 	reserved
fed1c000-fed1ffff 	pnp 00:08
fed20000-fed3ffff 	pnp 00:01
fed90000-fed93fff 	pnp 00:01
fee00000-fee0ffff 	pnp 00:01
fee00000-fee00fff 	Local APIC
ff000000-ffffffff 	reserved
ff000000-ffffffff 	pnp 00:08
100000000-23f7fffff 	System RAM
23f800000-23fffffff 	RAM buffer

**DMA**
4	cascade

```

---

