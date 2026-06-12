---
title: "Fresh 16.04 Install fails - lose video before files copied"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Derspankster on 2016-04-27
Hi all, long time user here - 10+ years!  Tried to do a fresh install of 16.04. Have been running 14.04 without issue. I never upgrade, always do fresh installs and I only run LTS. Anyway, I've tried perhaps 5 times now with different DVD media and two different CD/DVD drives to install 16.04 without success. The install fails before all files are copied. I lose video and the machine just sits.  I am trying to install to a SSD.  Never had a problem before and bot 12.04 and 14.04 have been installed to this SSD. The interesting part is now I cannot reinstall 14.04 either. It fails in like fashion.  I am back running 12.04. It went in without a hitch. All are 64 bit. I flashed my bios after I reinstalled 12.04 since I noticed it was several versions old.  I run the SSD and 2 mechanical storage drives. 

All drives test just fine and my 4 gig of ran pass fine.  If you've made it this far I appreciate your patience at my ramble.  I can't seem to come up with a solution.

---

### Post by bcschmerker on 2016-04-27
**Sounds as though the Ubuntu® 16.04.0-LTS installer suite has a regression somewhere.**  Could ye conCATenate /proc/cpuinfo and /proc/modules, and LsPCI, for a Reply hereto?  It may help the Developers track down the regression that is crashing the install process.  A Script similar to the example below might help accelerate the process of adding the Text files as Codeboxes in the Reply:
```

#!/bin/bash
# CPU Information
cat /proc/cpuinfo > /home/Derspankster/Desktop/ProcCPUInfo.txt
# Loaded Kernel modules
cat /proc/modules > /home/Derspankster/Desktop/ProcModules.txt
# Onboard PCI devices
lspci -vv > /home/Derspankster/Desktop/LsPCIVV.txt

```

---

### Post by Derspankster on 2016-04-28
Thank you for your reply. Here are the results of the scripts that you posted. 

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5999.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5999.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

snd_hda_codec_hdmi 32532 4 - Live 0x0000000000000000
pci_stub 12623 1 - Live 0x0000000000000000
vboxpci 23159 0 - Live 0x0000000000000000 (O)
vboxnetadp 25814 0 - Live 0x0000000000000000 (O)
vboxnetflt 27880 0 - Live 0x0000000000000000 (O)
joydev 17694 0 - Live 0x0000000000000000
coretemp 13642 0 - Live 0x0000000000000000
kvm_intel 137888 0 - Live 0x0000000000000000
kvm 422160 1 kvm_intel, Live 0x0000000000000000
vboxdrv 446707 3 vboxpci,vboxnetadp,vboxnetflt, Live 0x0000000000000000 (O)
gpio_ich 13384 0 - Live 0x0000000000000000
snd_hda_codec_realtek 79901 1 - Live 0x0000000000000000
snd_usb_audio 136507 1 - Live 0x0000000000000000
snd_hda_intel 34063 5 - Live 0x0000000000000000
snd_hda_codec 135141 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel, Live 0x0000000000000000
snd_pcm 97523 4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
uvcvideo 78117 0 - Live 0x0000000000000000
videobuf2_core 33025 1 uvcvideo, Live 0x0000000000000000
videodev 125126 2 uvcvideo,videobuf2_core, Live 0x0000000000000000
videobuf2_vmalloc 12861 1 uvcvideo, Live 0x0000000000000000
videobuf2_memops 13405 1 videobuf2_vmalloc, Live 0x0000000000000000
snd_hwdep 17765 2 snd_usb_audio,snd_hda_codec, Live 0x0000000000000000
snd_usbmidi_lib 29478 1 snd_usb_audio, Live 0x0000000000000000
snd_seq_midi 13325 0 - Live 0x0000000000000000
microcode 23030 0 - Live 0x0000000000000000
serio_raw 13216 0 - Live 0x0000000000000000
snd_rawmidi 30750 2 snd_usbmidi_lib,snd_seq_midi, Live 0x0000000000000000
nvidia 11405325 40 - Live 0x0000000000000000 (PO)
snd_seq_midi_event 14900 1 snd_seq_midi, Live 0x0000000000000000
snd_seq 61931 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
snd_timer 29990 2 snd_pcm,snd_seq, Live 0x0000000000000000
snd_seq_device 14498 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
lpc_ich 17145 0 - Live 0x0000000000000000
snd 83674 24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x0000000000000000
mac_hid 13254 0 - Live 0x0000000000000000
bnep 18240 2 - Live 0x0000000000000000
rfcomm 47562 0 - Live 0x0000000000000000
soundcore 15092 1 snd, Live 0x0000000000000000
snd_page_alloc 18573 2 snd_hda_intel,snd_pcm, Live 0x0000000000000000
bluetooth 212001 10 bnep,rfcomm, Live 0x0000000000000000
parport_pc 32867 1 - Live 0x0000000000000000
shpchp 37278 0 - Live 0x0000000000000000
ppdev 17114 0 - Live 0x0000000000000000
binfmt_misc 17541 1 - Live 0x0000000000000000
lp 17800 0 - Live 0x0000000000000000
parport 46563 3 parport_pc,ppdev,lp, Live 0x0000000000000000
hid_logitech_dj 18768 0 - Live 0x0000000000000000
usbhid 47259 1 hid_logitech_dj, Live 0x0000000000000000
hid 105241 2 hid_logitech_dj,usbhid, Live 0x0000000000000000
r8169 62741 0 - Live 0x0000000000000000
pata_jmicron 12748 0 - Live 0x0000000000000000
ahci 25869 2 - Live 0x0000000000000000
libahci 31434 1 ahci, Live 0x0000000000000000

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5/GA-EG45M-DS2H Motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fb000000-fcffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at fe00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at fd00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5 Motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-UD3R Motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5 Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at fc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5 Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at fb00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5 Motherboard
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at fa00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5 Motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
	Subsystem: Gigabyte Technology Co., Ltd Device 5001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01 [AHCI 1.0])
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5/GA-EG45M-DS2H Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 44
	Region 0: I/O ports at f900 [size=8]
	Region 1: I/O ports at f800 [size=4]
	Region 2: I/O ports at f700 [size=8]
	Region 3: I/O ports at f600 [size=4]
	Region 4: I/O ports at f500 [size=32]
	Region 5: Memory at fdffd000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Gigabyte Technology Co., Ltd GA-EP45-DS5/GA-EG45M-DS2H Motherboard
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 3
	Region 0: Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 1236
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at ee000000 (64-bit, prefetchable) [size=32M]
	Region 5: I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at e0000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_304_updates, nvidia_304, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
	Subsystem: eVga.com. Corp. Device 1236
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: Gigabyte Technology Co., Ltd Device b000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at df00 [size=8]
	Region 1: I/O ports at de00 [size=4]
	Region 2: I/O ports at dd00 [size=8]
	Region 3: I/O ports at dc00 [size=4]
	Region 4: I/O ports at db00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 45
	Region 0: I/O ports at ce00 [size=256]
	Region 2: Memory at fdcff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fdce0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by Derspankster on 2016-04-28
I just discovered that the live CD of 16.04 crashes after a few minutes just like happens during my installation attempts. I lose video and the system crashes. Interesting for sure. I'm wondering if it's graphics system related?

---

### Post by Derspankster on 2016-04-28
Well, I'm kind of talking to myself but I think I may have found the solution. I believe I'm going to have to install with NOMODESET. I think the Nvidia driver is causing my problem. I set NONMODESET at the liveCD boot and ran 16.04 as a liveCD without issue.  Of course my resolution was incorrect but it didn't crash just like my installation attempts.  I will post my results after I give 16.04 another installation attempt. Just in case anyone is reading this thread.  

der

---

### Post by ArchivalAudio on 2016-04-28
So I aM NOT A HUGE SUDO USER TODAY I TRIED TO UPGRADE FROM 15.10 to 16.04 it froze so I shutdown  = BIG mistake.
Now on my mac I am training to use unetbootin to make a bootable usb from the iso it keep freezing and failing at gile 253 or .squashfs from casper I have a Board of directors meeting and retreat this weekend and thought I could update... so far I am totally lost.

---

### Post by Derspankster on 2016-04-30
OK, found the solution.  Installation had to be done with NOMODESET because of changes made by Ubuntu with the boot video driver. My Nvidia video card didn't like it basically. So solution is to wait until the DVD starts and you see the purple screen hit ESC which brings up the menu, press F6 and check NOMODESET and then ESC back to the menu and select Install. When finished you can enable the proper driver and reboot and you should be fine.  If not, you and start your install with the NOMODESET  option and troubleshoot from there. 

Two other things - "ubuntu Software" (old Software Center) won't install 3rd party apps at the moment. Use Gdebi for now.  Finally, Brasero is painfully slow anymore. My max speed burning DVD's is .05X.  Gnome Baker is much faster.

---

