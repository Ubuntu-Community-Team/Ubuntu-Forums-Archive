---
title: "SD Card Reader"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-09-30
All of the Ubuntu distros i have used, none of them have one simple feature.

They dont enable me to use the SD Card reader built into my tablet.  Is this something that will probably be absent in 9.10 too?

---

### Post by gchand7 on 2009-09-30
Gnome Format is what I use its great.

---

### Post by rubenverweij on 2009-09-30
Although my German is not that good, I believe I workaround is provided here:
[http://linuxwiki.de/LinuxHardware/NoteBooks/HP/2710p#Ricoh_Co_Ltd_R5C822_SD.2BAC8-SDIO.2BAC8-MMC.2BAC8-MS.2BAC8-MSPro_Host_Adapter](http://linuxwiki.de/LinuxHardware/NoteBooks/HP/2710p#Ricoh_Co_Ltd_R5C822_SD.2BAC8-SDIO.2BAC8-MMC.2BAC8-MS.2BAC8-MSPro_Host_Adapter)
Let me know whether it works!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-30
Is this the same problem 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258446)

---

### Post by archiesteel on 2009-09-30
> **zoomy942 said:**
> They dont enable me to use the SD Card reader built into my tablet.  Is this something that will probably be absent in 9.10 too?

What is the result of [FONT="Courier New"]lspci -vvnn[/FONT]?

---

### Post by rburkartjo on 2009-09-30
zoomy i just bought a  digital 6 slot hi speed 51 in 1 card reader/writer and plug it into a usb port. about 25 bucks works great

---

### Post by zoomy942 on 2009-09-30
> **archiesteel said:**
> What is the result of [FONT="Courier New"]lspci -vvnn[/FONT]?


here you go sir

```
zimmerman@Karmic-Tablet:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at e0400000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 2000 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at e0500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:03.0 Communication controller [0780]: Intel Corporation Mobile PM965/GM965 MEI Controller [8086:2a04] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e0600000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:03.2 IDE interface [0101]: Intel Corporation Mobile PM965/GM965 PT IDER Controller [8086:2a06] (rev 0c) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 18
	Region 0: I/O ports at 2008 [size=8]
	Region 1: I/O ports at 2010 [size=4]
	Region 2: I/O ports at 2018 [size=8]
	Region 3: I/O ports at 2020 [size=4]
	Region 4: I/O ports at 2030 [size=16]
	Capabilities: <access denied>

00:03.3 Serial controller [0700]: Intel Corporation Mobile PM965/GM965 KT Controller [8086:2a07] (rev 0c) (prog-if 02)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 2040 [size=8]
	Region 1: Memory at e0601000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 26
	Region 0: Memory at e0620000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at e0640000 (32-bit, non-prefetchable) [size=4K]
	Region 2: I/O ports at 2060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 4: I/O ports at 20a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at e0641000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e0644000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	Memory behind bridge: e0000000-e00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at 20c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 22
	Region 4: I/O ports at 20e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 2100 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at e0648000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: e0100000-e03fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 2120 [size=16]
	Kernel driver in use: ata_piix

02:09.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at e0100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:09.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
	Subsystem: Hewlett-Packard Company Device [103c:30c8]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at e0101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: ricoh_mmc

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Device [8086:1000]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at e0000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

zimmerman@Karmic-Tablet:~$ 


```

---

### Post by Longinus00 on 2009-10-01
Actually, could you post what you get from this?
```
$ lsmod
```

---

### Post by zoomy942 on 2009-10-01
here you go buddy

```
zimmerman@Karmic-Tablet:~$ lsmod
Module                  Size  Used by
vboxnetadp             95148  0 
vboxnetflt            102316  0 
vboxdrv              1710444  1 vboxnetflt
berry_charge            5188  0 
nls_iso8859_1           5280  0 
nls_cp437               6976  0 
vfat                   13184  0 
fat                    59832  1 vfat
usb_storage            65952  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_analog    79680  1 
fbcon                  41248  71 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
arc4                    2144  2 
ecb                     3296  2 
snd_hda_intel          31624  3 
snd_hda_codec          79776  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
iwlagn                123328  0 
iwlcore               132320  1 iwlagn
mac80211              210136  2 iwlagn,iwlcore
ip_tables              21200  1 iptable_filter
sdhci_pci               8928  0 
joydev                 13088  0 
hp_wmi                  6896  0 
snd                    77096  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_infineon           10044  0 
soundcore               9088  1 snd
tpm                    18464  1 tpm_infineon
tpm_bios                7680  1 tpm
ricoh_mmc               4480  0 
x_tables               25832  1 ip_tables
sdhci                  20484  1 sdhci_pci
hp_accel               12480  0 
lis3lv02d               9312  1 hp_accel
input_polldev           4720  1 lis3lv02d
led_class               5256  3 iwlcore,sdhci,hp_accel
cfg80211              109144  3 iwlagn,iwlcore,mac80211
heci                   64676  0 
psmouse                57124  0 
i915                  244616  3 
serio_raw               6596  0 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
lp                     11908  0 
parport                40528  2 ppdev,lp
video                  23484  1 i915
output                  3680  1 video
intel_agp              31792  1 
e1000e                138704  0 
zimmerman@Karmic-Tablet:~$ 


```

---

### Post by Longinus00 on 2009-10-01
Insert the card again and run
```
$ dmesg | tail
```

---

### Post by zoomy942 on 2009-10-01
you got it buddy

```
zimmerman@Karmic-Tablet:~$ dmesg | tail
[   74.840089] wlan0: no IPv6 routers present
[  247.916058] CE: hpet increasing min_delta_ns to 15000 nsec
[  275.584030] CE: hpet increasing min_delta_ns to 22500 nsec
[  521.301645] wlan0: disassociating by local choice (reason=3)
[  533.066111] wlan0: authenticate with AP 00:90:4c:7e:00:6e
[  533.068237] wlan0: authenticated
[  533.068245] wlan0: associate with AP 00:90:4c:7e:00:6e
[  533.071226] wlan0: RX AssocResp from 00:90:4c:7e:00:6e (capab=0x401 status=0 aid=1)
[  533.071235] wlan0: associated
[  692.625664] Monitor-Mwait will be used to enter C-2 state
zimmerman@Karmic-Tablet:~$ 


```

---

### Post by Longinus00 on 2009-10-01
Try loading mmc_core and mmc_block I suppose.
```

$ sudo modprobe mmc_core
$ sudo modprobe mmc_block
```

Remove and reinsert after you do the above and post the contents of that dmesg command if it looks any different.

---

### Post by knarf on 2009-10-01
I'd say look through dmesg for relevant messages related to the Ricoh controller and the related drivers, eg.
```
dmesg|egrep -i 'ricoh|sdhci|mmc'|less
```
or
```
dmesg|egrep -A2 -i 'ricoh|sdhci|mmc'|less
```
(the latter shows two lines of context after each occurrence of the search term)

Post the results of one of these commands

---

### Post by zoomy942 on 2009-10-01
> **Longinus00 said:**
> Try loading mmc_core and mmc_block I suppose.
```

$ sudo modprobe mmc_core
$ sudo modprobe mmc_block
```

Remove and reinsert after you do the above and post the contents of that dmesg command if it looks any different.

tada!

```
zimmerman@Karmic-Tablet:~$ sudo modprobe mmc_core
[sudo] password for zimmerman: 
FATAL: Module mmc_core not found.
zimmerman@Karmic-Tablet:~$ sudo modprobe mmc_block
zimmerman@Karmic-Tablet:~$ sudo modprobe mmc_core
FATAL: Module mmc_core not found.
zimmerman@Karmic-Tablet:~$ .

```

---

### Post by zoomy942 on 2009-10-01
> **knarf said:**
> I'd say look through dmesg for relevant messages related to the Ricoh controller and the related drivers, eg.
```
dmesg|egrep -i 'ricoh|sdhci|mmc'|less
```
or
```
dmesg|egrep -A2 -i 'ricoh|sdhci|mmc'|less
```
(the latter shows two lines of context after each occurrence of the search term)

Post the results of one of these commands

here you go my friend

```


















[    0.172453] PCI: Not using MMCONFIG.
[    0.266177] PCI: Using MMCONFIG at f8000000 - fbffffff
[    7.669392] ricoh-mmc: Ricoh MMC Controller disabling driver
[    7.669397] ricoh-mmc: Copyright(c) Philip Langdale
[    7.676884] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.1 [1180:0843] (rev 12)
[    7.676907] ricoh-mmc: Main Ricoh function not found. Cannot disable controller.
[    7.794196] sdhci: Secure Digital Host Controller Interface driver
[    7.794200] sdhci: Copyright(c) Pierre Ossman
[    7.898852] sdhci-pci 0000:02:09.0: SDHCI controller found [1180:0822] (rev 22)
[    7.898881] sdhci-pci 0000:02:09.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    7.901004] Registered led device: mmc0::
[    7.902208] mmc0: SDHCI controller on PCI [0000:02:09.0] using PIO
[11297.858812] sdhci-pci 0000:02:09.0: PME# disabled
[11297.858822] sdhci-pci 0000:02:09.0: PCI INT B disabled
[11298.818682] sdhci-pci 0000:02:09.0: restoring config space at offset 0xf (was 0x200, writing 0x205)
[11298.818712] sdhci-pci 0000:02:09.0: restoring config space at offset 0x4 (was 0x0, writing 0xe0100000)
[11298.818720] sdhci-pci 0000:02:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[11298.818730] sdhci-pci 0000:02:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[11299.293808] sdhci-pci 0000:02:09.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
(END) 
























```

---

### Post by archiesteel on 2009-10-01
Mmmh...Is it possible that the SD card is recognized by simply not auto-mounted?

When you insert a card, does a new device appear in /dev (Presumably something like /dev/mmcblk0p1 or similar)?

---

### Post by zoomy942 on 2009-10-01
> **archiesteel said:**
> Mmmh...Is it possible that the SD card is recognized by simply not auto-mounted?

When you insert a card, does a new device appear in /dev (Presumably something like /dev/mmcblk0p1 or similar)?

i see that folder, but should i be looking for a new file or a new folder?  What am i looking for to see of anything new popped up?

---

### Post by archiesteel on 2009-10-01
> **zoomy942 said:**
> i see that folder, but should i be looking for a new file or a new folder?  What am i looking for to see of anything new popped up?

You should be looking for a new file; the /dev folder lists "devices" that are handled by the Linux system. Inserting a card should normally create a new device, which will appear as a new file in that folder.

I can't tell you the exact name of the file; chances are it'll start with "mmc", but it could also be seen as a disk (i.e. /dev/sdb, /dev/sdc, etc.).

---

### Post by zoomy942 on 2009-10-01
> **archiesteel said:**
> You should be looking for a new file; the /dev folder lists "devices" that are handled by the Linux system. Inserting a card should normally create a new device, which will appear as a new file in that folder.

I can't tell you the exact name of the file; chances are it'll start with "mmc", but it could also be seen as a disk (i.e. /dev/sdb, /dev/sdc, etc.).

understood.  upon testing this, i had 178 files in that folder before i inserted the card.  after i insterted it, it stayed at 178.  :(

---

### Post by archiesteel on 2009-10-02
> **zoomy942 said:**
> understood.  upon testing this, i had 178 files in that folder before i inserted the card.  after i insterted it, it stayed at 178.  :(

Mmmh...wish I could help you, but I'm stumped.

Question: did you try installing Karmic Koala yet (or even just running the LiveCD)? Perhaps the new kernel will offer support for this particular card reader...

---

