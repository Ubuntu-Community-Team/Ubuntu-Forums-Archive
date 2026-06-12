---
title: "System fan running constantly"
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by raccoonstrait on 2018-11-16
G'day Everyone,

After a upgrade to 18.10 I had a couple of issues [https://ubuntuforums.org/showthread.php?t=2404090&p=13809940#post13809940](https://ubuntuforums.org/showthread.php?t=2404090&p=13809940#post13809940) and upon advice tried booting with the older kernel which resolved both the issues. The dark screen was fixed by re-installing the Nvidea drivers, but the system fan is still running constantly, even when there is no load. So I have waited until a new kernel came out, which happend a couple of days ago. The system fan is still running constantly, even when the system has no load.

```

[FONT=monospace][COLOR=#5454FF]**System:    Host:**[/COLOR][COLOR=#000000] happy [/COLOR][COLOR=#5454FF]**Kernel:**[/COLOR][COLOR=#000000] 4.18.0-11-generic x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#000000] Xfce 4.13.2  [/COLOR]
           [COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 18.10 (Cosmic Cuttlefish)  [/COLOR]
[COLOR=#5454FF]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#5454FF]**System:**[/COLOR][COLOR=#000000] System76 [/COLOR][COLOR=#5454FF]**product:**[/COLOR][COLOR=#000000] Bonobo WS [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] bonw10 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] N/A  [/COLOR]
           [COLOR=#5454FF]**Mobo:**[/COLOR][COLOR=#000000] System76 [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Bonobo WS [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] bonw10 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**UEFI:**[/COLOR][COLOR=#000000] American Megatrends [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.05.02RS76  [/COLOR]
           [COLOR=#5454FF]**date:**[/COLOR][COLOR=#000000] 11/25/2015  [/COLOR]
[COLOR=#5454FF]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT0 [/COLOR][COLOR=#5454FF]**charge:**[/COLOR][COLOR=#000000] 11.9 Wh [/COLOR][COLOR=#5454FF]**condition:**[/COLOR][COLOR=#000000] 76.6/89.1 Wh (86%)  [/COLOR]
[COLOR=#5454FF]**CPU:       Topology:**[/COLOR][COLOR=#000000] Quad Core [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Intel Core i7-6700K [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] MT MCP [/COLOR][COLOR=#5454FF]**L2 cache:**[/COLOR][COLOR=#000000] 8192 KiB  [/COLOR]
           [COLOR=#5454FF]**Speed:**[/COLOR][COLOR=#000000] 3900 MHz [/COLOR][COLOR=#5454FF]**min/max:**[/COLOR][COLOR=#000000] 800/4200 MHz [/COLOR][COLOR=#5454FF]**Core speeds (MHz):**[/COLOR][COLOR=#5454FF]**1:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**2:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**3:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**4:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**5:**[/COLOR][COLOR=#000000] 3900  [/COLOR]
           [COLOR=#5454FF]**6:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**7:**[/COLOR][COLOR=#000000] 3900 [/COLOR][COLOR=#5454FF]**8:**[/COLOR][COLOR=#000000] 3900  [/COLOR]
[COLOR=#5454FF]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] NVIDIA GM204M [GeForce GTX 970M] [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 390.87  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA GM204M [GeForce GTX 970M] [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 390.87  [/COLOR]
           [COLOR=#5454FF]**Display:**[/COLOR][COLOR=#5454FF]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.1 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#5454FF]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~75Hz  [/COLOR]
           [COLOR=#5454FF]**OpenGL:**[/COLOR][COLOR=#5454FF]**renderer:**[/COLOR][COLOR=#000000] GeForce GTX 970M/PCIe/SSE2 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 4.6.0 NVIDIA 390.87  [/COLOR]
[COLOR=#5454FF]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel 100 Series/C230 Series Family HD Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA GM204 High Definition Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454FF]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] k4.18.0-11-generic  [/COLOR]
[COLOR=#5454FF]**Network:   Device-1:**[/COLOR][COLOR=#000000] Qualcomm Atheros Killer E2400 Gigabit Ethernet [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] alx  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] enp3s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 100 Mbps [/COLOR][COLOR=#5454FF]**duplex:**[/COLOR][COLOR=#000000] full [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] 80:fa:5b:2c:1b:a5  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Qualcomm Atheros Killer E2400 Gigabit Ethernet [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] alx  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] enp4s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 100 Mbps [/COLOR][COLOR=#5454FF]**duplex:**[/COLOR][COLOR=#000000] full [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] 80:fa:5b:2c:1b:a4  [/COLOR]
           [COLOR=#5454FF]**Device-3:**[/COLOR][COLOR=#000000] Intel Wireless 8260 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] iwlwifi  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] wlp5s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] a4:34:d9:65:02:34  [/COLOR]
[COLOR=#5454FF]**Drives:    Local Storage:**[/COLOR][COLOR=#5454FF]**total:**[/COLOR][COLOR=#000000] 1.13 TiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 231.81 GiB (20.1%)  [/COLOR]
           [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Samsung [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] SSD 850 EVO M.2 120GB [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 111.79 GiB  [/COLOR]
           [COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#000000] /dev/sdb [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Samsung [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] SSD 850 EVO M.2 120GB [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 111.79 GiB  [/COLOR]
           [COLOR=#5454FF]**ID-3:**[/COLOR][COLOR=#000000] /dev/sdc [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] HGST (Hitachi) [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] HTS721010A9E630 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 931.51 GiB  [/COLOR]
[COLOR=#5454FF]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 93.71 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 40.64 GiB (43.4%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
           [COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 15.96 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] swap [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda3  [/COLOR]
[COLOR=#5454FF]**Sensors:   System Temperatures:**[/COLOR][COLOR=#5454FF]**cpu:**[/COLOR][COLOR=#000000] 81.0 C [/COLOR][COLOR=#5454FF]**mobo:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**gpu:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#5454FF]**temp:**[/COLOR][COLOR=#000000] 54 C  [/COLOR]
           [COLOR=#5454FF]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A  [/COLOR]
[COLOR=#5454FF]**Info:      Processes:**[/COLOR][COLOR=#000000] 305 [/COLOR][COLOR=#5454FF]**Uptime:**[/COLOR][COLOR=#000000] 36m [/COLOR][COLOR=#5454FF]**Memory:**[/COLOR][COLOR=#000000] 15.62 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 4.13 GiB (26.4%) [/COLOR][COLOR=#5454FF]**Shell:**[/COLOR][COLOR=#000000] bash [/COLOR][COLOR=#5454FF]**inxi:**[/COLOR][COLOR=#000000] 3.0.24 [/COLOR]
[/FONT]
```[FONT=monospace]

Any thoughts?

Raccoon Strait[/FONT]

---

