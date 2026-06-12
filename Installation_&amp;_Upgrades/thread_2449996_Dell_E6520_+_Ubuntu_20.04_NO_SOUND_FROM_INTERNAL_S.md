---
title: "Dell E6520 + Ubuntu 20.04 NO SOUND FROM INTERNAL SPEAKER, IDT HD Audio CODEC"
date: 2020-09-05
forum: Installation &amp; Upgrades
---

### Post by sameerhk on 2020-09-05
Hi I am very new to Linux/Ubuntu, had been using WIn7 & 10 earlier. But trying 1st time and everything install okay with Ubunto 20.04 expect the internal sound isn't working.

Below is my configuration-
Dell Latitude E6520
2.40 gigahertz Intel Core i7-2760QM
64-bit ready, Multi-core (4 total), Hyper-threaded (8 total)
RAM 8G DDR3
NVIDIA NVS 4200M [Display adapter]
Bus Adapters - Intel(R) 6 Series/C200 Series Chipset Family USB Enhanced Host Controller - 1C26, Intel(R) 6 Series/C200 Series Chipset Family USB Enhanced Host Controller - 1C2D
Audio - IDT High Definition Audio CODEC
WIFI - Intel(R) Centrino(R) Ultimate-N 6300 AGN

I have read few help online and below is the command outputs;

1. lspci
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0b:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
0b:00.1 SD Host controller: O2 Micro, Inc. OZ600RJ0/OZ900RJ0/OZ600RJS SD/MMC Card Reader Controller (rev 05)
0b:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)

2. lspci | grep -i audio
spci | grep -i audio
00:1b.0 [COLOR=#CC0000]**Audio**[/COLOR] device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition [COLOR=#CC0000]**Audio**[/COLOR] Controller (rev 04)
01:00.1 [COLOR=#CC0000]**Audio**[/COLOR] device: NVIDIA Corporation GF119 HDMI [COLOR=#CC0000]**Audio**[/COLOR] Controller (rev ff)


3. sudo lshw -C multimedia

$ sudo lshw -C multimedia
*-multimedia 
description: Audio device
product: GF119 HDMI Audio Controller
vendor: NVIDIA Corporation
physical id: 0.1
bus info: pci@0000:01:00.1
version: a1
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: driver=snd_hda_intel latency=0
resources: irq:17 memory:e5080000-e5083fff
*-usb
description: Video
product: Laptop_Integrated_Webcam_FHD
vendor: CN0CJ3P272487226A3TDA01
physical id: 5
bus info: usb@1:1.5
version: 3.10
capabilities: usb-2.00
configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
*-multimedia
description: Audio device
product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 04
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=snd_hda_intel latency=0
resources: irq:38 memory:e6e60000-e6e63fff


4. sudo alsa force-reload

$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-idt snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg snd-seq-midi snd-seq-midi-event snd-hda-codec snd-hda-core snd-rawmidi snd-seq snd-hwdep snd-pcm snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-idt snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-idt snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg snd-seq-midi snd-seq-midi-event snd-hda-codec snd-hda-core snd-rawmidi snd-seq snd-hwdep snd-pcm snd-seq-device snd-timer.

These are my findings kindly help me to enable the internal speakers.

Thanks in advance to each and everyone.

---

### Post by CelticWarrior on 2020-09-05
Welcome.

Is your sound output correctly selected?

---

