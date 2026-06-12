---
title: "Can't figure out what kind of tv tuner I have"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by froman2686 on 2007-09-08
Okay. I just converted to Ubuntu, permanently, after the latest patch for Vista caused a wonderful "Network services failed to start" side effect. Took me a solid day or so to install (and reinstall, twice, after I screwed up my nvidia drivers and Beryl, which works beautifully now) and now, whilst exploring my new found powers, I've become interested in my TV tuner card.

This card, ATI in brand, was installed a loong time ago. It worked well with XP, but once I switched over to Vista, it became another piece of hardware that microsoft decided wasn't good enough. Vista didn't even detect it, I eventually forgot about it, so it goes. 

Now with my renewed interest, I've discovered that Ubuntu has no idea what card it is. It identifies as an ATI card, but beyond that, nothing. I personally can't remember for the life of me. Is there any way I can identify this piece of hardware through software? 

Thanks.

---

### Post by llamakc on 2007-09-08
Yes. Open a Terminal and type:

sudo lspci -v

and cut/paste the output here.

---

### Post by froman2686 on 2007-09-08
Here's the whole thing, I bolded what I think is the card.

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e2000000-e4ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Intel Corporation Unknown device 0000
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e5325900 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at e5300000 (32-bit, non-prefetchable) [size=128K]
        Memory at e5324000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 40c0 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 40a0 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 4080 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at e5325400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 2504
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at e5320000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: e5400000-e54fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e5200000-e52fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: e5500000-e55fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: e5600000-e56fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4
        Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: e5700000-e57fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 4060 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 4040 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 4020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at e5325000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: e5000000-e51fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e1ffffff
        Capabilities: [50] Subsystem: Intel Corporation Unknown device 514d

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 4138 [size=8]
        I/O ports at 414c [size=4]
        I/O ports at 4130 [size=8]
        I/O ports at 4148 [size=4]
        I/O ports at 4110 [size=16]
        I/O ports at 4100 [size=16]
        Capabilities: [70] Power Management version 3

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: medium devsel, IRQ 10
        Memory at e5325800 (32-bit, non-prefetchable) [size=256]
        I/O ports at 4000 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 4128 [size=8]
        I/O ports at 4144 [size=4]
        I/O ports at 4120 [size=8]
        I/O ports at 4140 [size=4]
        I/O ports at 40f0 [size=16]
        I/O ports at 40e0 [size=16]
        Capabilities: [70] Power Management version 3

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0400 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2280
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e2000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 3000 [size=128]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. Unknown device 6101
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at 2018 [size=8]
        I/O ports at 2024 [size=4]
        I/O ports at 2010 [size=8]
        I/O ports at 2020 [size=4]
        I/O ports at 2000 [size=16]
        Memory at e5200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

[B]07:01.0 Multimedia controller: ATI Technologies Inc Unknown device 4d52
        Subsystem: ATI Technologies Inc Unknown device a346
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at e5000000 (32-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [50] Power Management version 2[/B]

07:02.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-538TX 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 1000 [size=256]
        Memory at e5104800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e5104000 (32-bit, non-prefetchable) [size=2K]
        Memory at e5100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

---

### Post by llamakc on 2007-09-08
That's probably it.

Mine shows up like:

```

01:07.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0b)
        Subsystem: Lumanate, Inc. Unknown device 001a
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fe9fc000 (32-bit, non-prefetchable) [size=8K]
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [40] Power Management version 2

```

Unfortunately for me, mine is junk and works on Windows only (from the research I've done).

Have you modprobed the "bttv" module yet?

In the Terminal, type: sudo modprobe bttv 

and then check to see if it loaded correctly with "lsmod".

---

### Post by froman2686 on 2007-09-08
Module                  Size  Used by
bttv                  173684  0 
video_buf              26116  1 bttv
ir_common              31236  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
videodev               28160  1 bttv
v4l2_common            25216  2 bttv,videodev
v4l1_compat            15236  1 videodev
isofs                  36284  1 
udf                    85252  0 
vmnet                  32932  13 
vmmon                 185676  0 
nls_iso8859_1           5120  0 
nls_cp437               6784  1 
vfat                   14208  0 
fat                    53916  1 vfat
usb_storage            72256  0 
libusual               17936  1 usb_storage
snd_rtctimer            4384  0 
nls_utf8                3072  3 
ntfs                  107764  3 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  2 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
button                  8720  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
video                  16388  0 
battery                10756  0 
ipv6                  268960  16 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_hda_intel          21912  5 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
nvidia               7252756  44 
snd_seq_oss            32896  0 
i2c_core               22656  5 bttv,i2c_algo_bit,tveeprom,i2c_ec,nvidia
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
xpad                    9988  0 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
serio_raw               7940  0 
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
af_packet              23816  6 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd                    54020  18 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              26140  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 nvidia,intel_agp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
usbhid                 26592  0 
hid                    27392  1 usbhid
sg                     36252  0 
sd_mod                 23428  8 
generic                 5124  0 [permanent]
pata_marvell            7936  2 
ata_piix               15492  4 
ata_generic             9092  0 
libata                125720  3 pata_marvell,ata_piix,ata_generic
scsi_mod              142348  6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata
8139too                27648  0 
mii                     6528  1 8139too
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  7 usb_storage,libusual,xpad,usbhid,ehci_hcd,uhci_hcd
e1000                 126016  0 
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

appears in a number of places, I'm assuming this means it loaded correctly?

---

### Post by llamakc on 2007-09-08
Yeah, so do you have an input attached to the card at the back of the computer, like cable coax (or whatever you're using)? Start up a tv program and see if it works.

---

### Post by froman2686 on 2007-09-08
got everything attached, I was gonna set up MythTV but it won't advance since it doesn't probe the card...is there another program i could try, or perhaps a way to get MythTV to work even though the card isn't completely setup?

---

### Post by llamakc on 2007-09-08
That I don't know. I'd search Google and the forums for the type of card you have and it's compatibility with MythTV. That's precisely what I wanted to set up but had no luck with.

---

### Post by scxtt on 2007-09-08
i'd start simple, w/ something like tvtime - just to be sure you can get the basics going ... i have an older ATI tvtuner, worked fine w/ tvtime.

---

### Post by froman2686 on 2007-09-08
TvTime reports that /dev/video0 does not exist...I guess this means linux has no idea what to do with my capture card?

---

### Post by llamakc on 2007-09-08
Are you following any particular howto for this? I remember having to use mknod to create the /dev/video0.

---

### Post by scxtt on 2007-09-08
mine worked out of the box, back w/ dapper/edgy - it's a TV Wonder VE - what model do you have?

---

### Post by froman2686 on 2007-09-08
> **scxtt said:**
> mine worked out of the box, back w/ dapper/edgy - it's a TV Wonder VE - what model do you have?

No idea what the model is, that's what sparked this post!

> Are you following any particular howto for this? I remember having to use mknod to create the /dev/video0.

No, I was originally just trying to figure out what kind of card it was via software. Now I'm just basically doing what you tell me to :popcorn:

---

### Post by scxtt on 2007-09-08
> **froman2686 said:**
> No idea what the model is, that's what sparked this post!have you physically looked on the card, i doubt ATI is trying to hide the model name from you ...

---

### Post by froman2686 on 2007-09-08
Looks like a Theater 550 PRO.

ATI doesn't have official linux drivers, off to google i go!

---

