---
title: "First install of 10.04 a failure"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by dummkauf on 2010-09-18
Ok, I used to run Mythbuntu when version 9 was out with no problems.  I downloaded the cd, it autodected my hardware and worked great right from the start.  However, I then purchased a hauppauge 1250 to record digital channel(supposedly works with mythbuntu), but I couldn't get it working.  So I installed windows and mediaPortal to give that a go, since my 1250 came with Windows drivers.  Anyway, that didn't work, so I"m back to Mythbuntu and figured I'd install 10.04, however now neither or my tuner cards work at all, I can't even get the analog channels.  The analog should still work as I plugged the wire into my TV(old TV, no digital tuner built in) and I could tune in channels 1-99 just fine.  So I'm still getting analog signals from Comcast, but yet my analog card(Hauppauge 150) just won't work.

Right now my goal is to just get the Hauppauge 150 working for my analog channels and I'll deal with the DVB issues later.

I am also running on an AMD x64 processor with the x64 version of mythbuntu installed.

Here is my lspci info
```

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
05:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)

```

lshw -C Multimedia
```

  *-multimedia            
       description: Audio device
       product: MCP65 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:20 memory:fe024000-fe027fff
  *-multimedia:0
       description: Multimedia video controller
       product: iTVC16 (CX23416) MPEG-2 Encoder
       vendor: Internext Compression Inc
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ivtv latency=128 maxlatency=8 mingnt=128
       resources: irq:17 memory:ec000000-efffffff(prefetchable)
  *-multimedia:1
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1724 latency=64
       resources: irq:16 ioport:cc00(size=32) ioport:c800(size=128)
  *-multimedia
       description: Multimedia video controller
       product: Hauppauge Inc. HDPVR-1250 model 1196
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:16 memory:fd800000-fd9fffff

```

dmesg | grep ivtv
```

[   19.423185] ivtv: Start initialization, version 1.4.1
[   19.590138] ivtv0: Initializing card 0
[   19.590143] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   19.592370] ivtv 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   19.700484] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   20.083197] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   20.146552] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   20.216971] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   20.221140] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.242479] IRQ 17/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.243036] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   20.243141] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   20.243241] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   20.243346] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   20.243449] ivtv0: Registered device radio0 for encoder radio
[   20.243451] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   20.243494] ivtv: End initialization
[   20.860047] ivtv 0000:01:07.0: firmware: requesting v4l-cx2341x-enc.fw
[   20.896899] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   21.090173] ivtv0: Encoder revision: 0x02060039

```

Looking for some advice on what to start checking/troubleshooting as I am now lost.  It looks like the devices are all detected and loading, but I can't get them to work. 

Any advice would be greatly appreaciated!

Thank you!

---

