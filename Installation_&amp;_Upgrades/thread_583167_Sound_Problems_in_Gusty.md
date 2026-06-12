---
title: "Sound Problems in Gusty"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Rapidsnow on 2007-10-20
After searching I couldn't find my problem. 

I have an HP Pavillion dv6258se laptop. When installing Feisty originally, sound worked fine. Today I upgraded to Gusty and no sound is there. I tried a few things from other threads about sound like installing esd and various plugins. My sound always appears muted and if I click on it, it say: "No Volume Control GStreamer plugins and/or devices found." 

So I took this to mean that I should install GStreamer from Synaptic, but alas sound is still not working. Is there anyone who knows how to fix this problem? It isn't just that the headphones aren't working (I have seen that problem before) the actual speakers aren't working either. I will include my lspci at the end, and if you need any more information that I overlooked, I will be happy to give it.


```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

---

### Post by OnSite511 on 2007-10-20
I've got the same problem with the same hardware,(00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)). I've noticed that 3 things, that when I do ```
alsamixer
```
I get
```
alsamixer: function snd_ctl_open failed for default: No such device
```
and that in Sound Preferences >Devices my Default Mixer Tracks is an empty dropdown 

and when I click Test for any of the other options, I get
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

I wonder if a fresh install would solve our problems, and if so what piece of the fresh install would fix it?

As part of my troubleshooting, I'm going to try to compile the ALSA driver myself, but it wants the kernel source, 
```
checking for kernel linux/version.h... no
The file /usr/src/linux-headers-2.6.22-14/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```
should I point to vermagic.h instead of version.h ?
which package from synaptic should I install?
the description for linux-source-2.6.22 says 'If you are simply trying to build third-party modules for your kernel, you do not want this package. Install the appropriate linux-headers package instead.' <-- which would that be?

---

### Post by OnSite511 on 2007-10-20
Update - just do a clean install.It fixed everything. Gutsy is so much faster than Fiesty. Way to go Ubuntu developers.

---

### Post by xhilyn on 2007-10-22
Hi all. I have the same no sound card problem and have already reinstalled but I still have the same problem. Any other thoughts?
xhi

---

### Post by Grann0n on 2007-10-23
Hi all,

Do the same with a clean install on an A8N-VM CSM with a clean install.

Everything was working under Festy and it seems to be the onliest problem

---

