---
title: "No Sound Ubuntu 11.04 on Intel N10/ICH7 with  codec ALC662"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by NSCarneiroBR on 2011-10-19
[FONT=Arial][SIZE=3]Somebody could help me to solve this problem?[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]
[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]Please, examine these informations: 

- The hardware was working very nice under WinXP SP3. In this environment the sound is OK.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]- After that I had found the fault with Ubuntu Linux 11.04, I tested Ubuntu 11.10 with the new kernel 3.0.0 on the same hardware without success. NO SOUND, MUTE.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]- After to test with Ubuntu 11.10, I installed the Fedora 15 and repeated the tests. Again, NO SOUND, MUTE.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]- So, I installed the Ubuntu 11.04 again and updated it[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]- Then I executed alsamixer command and setup all controls to change the &#8220;zero&#8221; values to others values except those controls locked (only 2), following I executed &#8220;alsactl store&#8221; command.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]- After these startup procedures I got these reports:  [/SIZE][/FONT]
 

 [FONT=Verdana][SIZE=3]--------------------------
Output of  lspci -v
--------------------------[/SIZE][/FONT]


 [FONT=Verdana][SIZE=2]00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
Subsystem: Device 1b0a:0006
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) (prog-if 00 [VGA controller])
Subsystem: Device 1b0a:0006
Flags: bus master, fast devsel, latency 0, IRQ 43
Memory at fea00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at c800 [size=8]
Memory at d0000000 (32-bit, prefetchable) [size=256M]
Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
Subsystem: Device 1b0a:0001
Flags: bus master, fast devsel, latency 0, IRQ 44
Memory at feaf8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 3f700000-3f8fffff
Prefetchable memory behind bridge: 000000003f900000-000000003fafffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: feb00000-febfffff
Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at c880 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at cc00 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at d000 [size=32]
Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at d080 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at feaffc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Device 1b0a:0005
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at ffa0 [size=16]
Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Device 1b0a:0005
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
I/O ports at dc00 [size=8]
I/O ports at d880 [size=4]
I/O ports at d800 [size=8]
I/O ports at d480 [size=4]
I/O ports at d400 [size=16]
Capabilities: <access denied>
Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
Subsystem: Device 1b0a:0005
Flags: medium devsel, IRQ 5
I/O ports at 0400 [size=32]
Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
Subsystem: Device 1b0a:0003
Flags: bus master, fast devsel, latency 0, IRQ 42
I/O ports at e800 [SIZE=256]
[/SIZE][/FONT]Memory at febff000 (64-bit, non-prefetchable) [size=4K]
Memory at fdff0000 (64-bit, prefetchable) [size=64K]
Expansion ROM at febc0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

[FONT=Verdana][SIZE=3]-----------------------
Output of lsmod
-----------------------[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Module Size Used by
nls_iso8859_1 12617 1 
nls_cp437 12751 1 
vfat 17335 1 
fat 55505 1 vfat
binfmt_misc 13213 1 
snd_hda_codec_realtek 255820 1 
snd_hda_intel 24140 2 
snd_hda_codec 90901 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80244 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 13132 0 
snd_rawmidi 25269 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28659 2 snd_pcm,snd_seq
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 55295 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915 450944 3 
drm_kms_helper 40745 1 i915
ppdev 12849 0 
soundcore 12600 1 snd
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
parport_pc 32111 1 
drm 180037 4 i915,drm_kms_helper
i2c_algo_bit 13184 1 i915
psmouse 73312 0 
video 18951 1 i915
serio_raw 12990 0 
lp 13349 0 
parport 36746 3 ppdev,parport_pc,lp
usbhid 41704 0 
hid 77084 1 usbhid
usb_storage 43946 1 
uas 17676 0 
r8169 42534 0 
[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]----------------------------[/SIZE][/FONT]
 [FONT=Verdana][SIZE=3]Output of alsa-info 
----------------------------[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]!!Soundcards recognised by ALSA
!!-----------------------------

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfeaf8000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
Subsystem: 1b0a:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=auto position_fix=0


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : -1
id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC662 rev1
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0662
Subsystem Id: 0x1b0a0001
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
rates [0x160]: 44100 48000 96000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
Control: name="PCM Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Device: name="ALC662 rev1 Analog", type="Audio", device=0
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x31 0x31]
Converter: stream=5, channel=0
PCM:
rates [0x160]: 44100 48000 96000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x40 0x40]
Converter: stream=0, channel=0
PCM:
rates [0x160]: 44100 48000 96000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x1d: Stereo Amp-Out
Control: name="Headphone Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x31 0x31]
Converter: stream=5, channel=0
PCM:
rates [0x160]: 44100 48000 96000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
Device: name="ALC662 rev1 Digital", type="SPDIF", device=1
Converter: stream=5, channel=0
Digital: Enabled
Digital category: 0x0
PCM:
rates [0x160]: 44100 48000 96000
bits [0x1e]: 16 20 24 32
formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
Control: name="Capture Switch", index=1, device=0
Control: name="Capture Volume", index=1, device=0
Amp-In caps: ofs=0x09, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x89 0x89]
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x160]: 44100 48000 96000
bits [0x6]: 16 20
formats [0x1]: PCM
Connection: 1
0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
Control: name="Capture Switch", index=0, device=0
Control: name="Capture Volume", index=0, device=0
Device: name="ALC662 rev1 Analog", type="Audio", device=0
Amp-In caps: ofs=0x09, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x11 0x11]
Converter: stream=1, channel=0
SDI-Select: 0
PCM:
rates [0x160]: 44100 48000 96000
bits [0x6]: 16 20
formats [0x1]: PCM
Connection: 1
0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="Rear Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Rear Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Front Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=1, ofs=0
Control: name="Front Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=1, ofs=0
Control: name="Line Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=2, ofs=0
Control: name="Line Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=2, ofs=0
Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x80 0x80] [0x97 0x97] [0x98 0x98] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 9
0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="PCM Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x00 0x00]
Connection: 2
0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x00 0x00]
Connection: 2
0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="Headphone Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x00 0x00]
Connection: 2
0x04 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Pincap 0x0001003c: IN OUT HP EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x01014010: [Jack] Line Out at Ext Rear
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0x0
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0c
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Pincap 0x00010034: IN OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0d
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Pincap 0x00000034: IN OUT Detect
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
Control: name="Rear Mic Boost Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00001734: IN OUT Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x01a19840: [Jack] Mic at Ext Rear
Conn = 1/8, Color = Pink
DefAssociation = 0x4, Sequence = 0x0
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Connection: 1
0x0e
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
Control: name="Front Mic Boost Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x02 0x02]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x0000173c: IN OUT HP Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x02a19c50: [Jack] Mic at Ext Front
Conn = 1/8, Color = Pink
DefAssociation = 0x5, Sequence = 0x0
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Connection: 2
0x0c* 0x0e
Node 0x1a [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00000034: IN OUT Detect
Pin Default 0x0181304f: [Jack] Line In at Ext Rear
Conn = 1/8, Color = Blue
DefAssociation = 0x4, Sequence = 0xf
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Connection: 1
0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Pincap 0x0000173c: IN OUT HP Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x02214c20: [Jack] HP Out at Ext Front
Conn = 1/8, Color = Green
DefAssociation = 0x2, Sequence = 0x0
Pin-ctls: 0xc0: OUT HP VREF_HIZ
Unsolicited: tag=00, enabled=0
Connection: 2
0x0c 0x0e*
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
Pincap 0x00000020: IN
Pin Default 0x593301f0: [N/A] CD at Int ATAPI
Conn = ATAPI, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
Pincap 0x00000020: IN
Pin Default 0x4004c601: [N/A] Line Out at Ext N/A
Conn = RCA, Color = UNKNOWN
DefAssociation = 0x0, Sequence = 0x1
Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
Pincap 0x00000010: OUT
Pin Default 0x014b1130: [Jack] SPDIF Out at Ext Rear
Conn = Comb, Color = Black
DefAssociation = 0x3, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Connection: 1
0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Processing caps: benign=0, ncoeff=12
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="Input Source", index=0, device=0
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 10
0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="Input Source", index=1, device=0
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 10
0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x26 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 6 Oct 16 12:28 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 5 Oct 16 12:28 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 4 Oct 16 12:28 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 3 Oct 16 12:28 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 2 Oct 16 12:28 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 1 Oct 16 12:28 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Oct 16 12:28 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Oct 16 12:28 .
drwxr-xr-x 3 root root 200 Oct 16 12:28 ..
lrwxrwxrwx 1 root root 12 Oct 16 12:28 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfeaf8000 irq 44'
Mixer name : 'Realtek ALC662 rev1'
Components : 'HDA:10ec0662,1b0a0001,00100101'
Controls : 25
Simple ctrls : 14
Simple mixer control 'Master',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
Playback channels: Mono
Limits: Playback 0 - 64
Mono: Playback 51 [80%] [-13.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 64
Mono:
Front Left: Playback 62 [97%] [-2.00dB] [on]
Front Right: Playback 62 [97%] [-2.00dB] [on]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 64
Mono:
Front Left: Playback 62 [97%] [-2.00dB] [on]
Front Right: Playback 62 [97%] [-2.00dB] [on]
Simple mixer control 'Front Mic',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 23 [74%] [0.00dB] [off]
Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Front Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 2 [67%] [20.00dB]
Front Right: 2 [67%] [20.00dB]
Simple mixer control 'Line',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 24 [77%] [1.50dB] [off]
Front Right: Playback 24 [77%] [1.50dB] [off]
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 31
Front Left: Capture 17 [55%] [12.00dB] [on]
Front Right: Capture 17 [55%] [12.00dB] [on]
Simple mixer control 'Capture',1
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 31
Front Left: Capture 9 [29%] [0.00dB] [off]
Front Right: Capture 9 [29%] [0.00dB] [off]
Simple mixer control 'Input Source',0
Capabilities: cenum
Items: 'Rear Mic' 'Front Mic' 'Line'
Item0: 'Front Mic'
Simple mixer control 'Input Source',1
Capabilities: cenum
Items: 'Rear Mic' 'Front Mic' 'Line'
Item0: 'Rear Mic'
Simple mixer control 'Rear Mic',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 0 [0%] [0.00dB]
Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
control.1 {
iface MIXER
name 'PCM Playback Volume'
value.0 62
value.1 62
comment {
access 'read write'
type INTEGER
count 2
range '0 - 64'
dbmin -6400
dbmax 0
dbvalue.0 -200
dbvalue.1 -200
}
}
control.2 {
iface MIXER
name 'PCM Playback Switch'
value.0 true
value.1 true
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.3 {
iface MIXER
name 'Headphone Playback Volume'
value.0 62
value.1 62
comment {
access 'read write'
type INTEGER
count 2
range '0 - 64'
dbmin -6400
dbmax 0
dbvalue.0 -200
dbvalue.1 -200
}
}
control.4 {
iface MIXER
name 'Headphone Playback Switch'
value.0 true
value.1 true
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.5 {
iface MIXER
name 'Rear Mic Playback Volume'
value.0 0
value.1 0
comment {
access 'read write'
type INTEGER
count 2
range '0 - 31'
dbmin -3450
dbmax 1200
dbvalue.0 -3450
dbvalue.1 -3450
}
}
control.6 {
iface MIXER
name 'Rear Mic Playback Switch'
value.0 false
value.1 false
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.7 {
iface MIXER
name 'Front Mic Playback Volume'
value.0 23
value.1 23
comment {
access 'read write'
type INTEGER
count 2
range '0 - 31'
dbmin -3450
dbmax 1200
dbvalue.0 0
dbvalue.1 0
}
}
control.8 {
iface MIXER
name 'Front Mic Playback Switch'
value.0 false
value.1 false
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.9 {
iface MIXER
name 'Line Playback Volume'
value.0 24
value.1 24
comment {
access 'read write'
type INTEGER
count 2
range '0 - 31'
dbmin -3450
dbmax 1200
dbvalue.0 150
dbvalue.1 150
}
}
control.10 {
iface MIXER
name 'Line Playback Switch'
value.0 false
value.1 false
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.11 {
iface MIXER
name 'Rear Mic Boost Volume'
value.0 0
value.1 0
comment {
access 'read write'
type INTEGER
count 2
range '0 - 3'
dbmin 0
dbmax 3000
dbvalue.0 0
dbvalue.1 0
}
}
control.12 {
iface MIXER
name 'Front Mic Boost Volume'
value.0 2
value.1 2
comment {
access 'read write'
type INTEGER
count 2
range '0 - 3'
dbmin 0
dbmax 3000
dbvalue.0 2000
dbvalue.1 2000
}
}
control.13 {
iface MIXER
name 'Capture Switch'
value.0 true
value.1 true
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.14 {
iface MIXER
name 'Capture Switch'
index 1
value.0 false
value.1 false
comment {
access 'read write'
type BOOLEAN
count 2
}
}
control.15 {
iface MIXER
name 'Capture Volume'
value.0 17
value.1 17
comment {
access 'read write'
type INTEGER
count 2
range '0 - 31'
dbmin -1350
dbmax 3300
dbvalue.0 1200
dbvalue.1 1200
}
}
control.16 {
iface MIXER
name 'Capture Volume'
index 1
value.0 9
value.1 9
comment {
access 'read write'
type INTEGER
count 2
range '0 - 31'
dbmin -1350
dbmax 3300
dbvalue.0 0
dbvalue.1 0
}
}
control.17 {
iface MIXER
name 'Input Source'
value 'Front Mic'
comment {
access 'read write'
type ENUMERATED
count 1
item.0 'Rear Mic'
item.1 'Front Mic'
item.2 Line
}
}
control.18 {
iface MIXER
name 'Input Source'
index 1
value 'Rear Mic'
comment {
access 'read write'
type ENUMERATED
count 1
item.0 'Rear Mic'
item.1 'Front Mic'
item.2 Line
}
}
control.19 {
iface MIXER
name 'IEC958 Playback Con Mask'
value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
comment {
access read
type IEC958
count 1
}
}
control.20 {
iface MIXER
name 'IEC958 Playback Pro Mask'
value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
comment {
access read
type IEC958
count 1
}
}
control.21 {
iface MIXER
name 'IEC958 Playback Default'
value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
comment {
access 'read write'
type IEC958
count 1
}
}
control.22 {
iface MIXER
name 'IEC958 Playback Switch'
value true
comment {
access 'read write'
type BOOLEAN
count 1
}
}
control.23 {
iface MIXER
name 'IEC958 Default PCM Playback Switch'
value true
comment {
access 'read write'
type BOOLEAN
count 1
}
}
control.24 {
iface MIXER
name 'Master Playback Volume'
value 51
comment {
access 'read write'
type INTEGER
count 1
range '0 - 64'
dbmin -6400
dbmax 0
dbvalue.0 -1300
}
}
control.25 {
iface MIXER
name 'Master Playback Switch'
value true
comment {
access 'read write'
type BOOLEAN
count 1
}
}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
binfmt_misc
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
usbhid
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ppdev
snd_seq
usb_storage
snd_timer
hid
uas
i915
snd_seq_device
snd
psmouse
drm_kms_helper
serio_raw
drm
soundcore
snd_page_alloc
parport_pc
i2c_algo_bit
video
lp
parport
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x01014010
0x15 0x411111f0
0x16 0x411111f0
0x18 0x01a19840
0x19 0x02a19c50
0x1a 0x0181304f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4004c601
0x1e 0x014b1130

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[ 7.642539] generic-usb 0003:04F3:0210.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1.2/input0
[ 7.643050] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7.643105] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 7.643128] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 7.676151] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/input/input3
[ 7.676262] generic-usb 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.1-1.3/input0
[ 7.695366] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[ 7.702976] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.1/input/input5

--------------------------------------------------------------------------------[/SIZE][/FONT]


 [FONT=Verdana][SIZE=3]This is the present situation.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=3]
[/SIZE][/FONT]
 [FONT=Verdana][SIZE=3]I am waiting for helping.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=3]
[/SIZE][/FONT]
 [FONT=Verdana][SIZE=3]Somebody would like to help me and others common users?[/SIZE][/FONT]


[FONT=Verdana][SIZE=3]Sorry my poor english.
[/SIZE][/FONT]

---

