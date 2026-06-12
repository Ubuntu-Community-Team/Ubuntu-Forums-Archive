---
title: "GUI not working with Edubuntu 14.04.1 in computer with VIA Technologies hardware"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by lpc on 2014-08-20
Hello,

I installed Edubuntu 14.04.1 from a USB stick in a computer with Intel Pentium Dual 2.0Ghz, 1GB RAM and a 74.4 Gb disk. The installation went fine but after login I either get a black screen or a flickering screen. It works fine in command-line interface. I suspect a problem with the drivers. I have pasted below the hardware info.  Any ideas how could I get Edubuntu to work with this computer? Thanks!

```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  *-network
       descripción: Ethernet interface
       producto: VT6102 [Rhine-II]
       fabricante: VIA Technologies, Inc.
       id físico: 12
       información del bus: pci@0000:00:12.0
       nombre lógico: eth8
       versión: 78
       serie: 00:e0:4d:8c:be:91
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       recursos: irq:23 ioport:d800(size=256) memoria:f6001000-f60010ff
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342206  10 bnep,rfcomm
binfmt_misc            13140  1 
snd_via82xx            28455  0 
snd_mpu401_uart        13865  1 snd_via82xx
snd_ac97_codec        105709  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
gameport               15189  1 snd_via82xx
snd_pcm                85501  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         14230  2 snd_via82xx,snd_pcm
snd_seq_midi           13132  0 
kvm_amd                50537  0 
snd_seq_midi_event     14475  1 snd_seq_midi
kvm                   388083  1 kvm_amd
snd_rawmidi            25135  2 snd_mpu401_uart,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13230  0 
k8temp                 12842  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  9 snd_via82xx,snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_mpu401_uart,snd_seq_device,snd_seq_midi
parport_pc             31981  1 
ppdev                  17391  0 
soundcore              12600  1 snd
mac_hid                13037  0 
i2c_viapro             13096  0 
lp                     13299  0 
shpchp                 32128  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
usb_storage            48417  0 
floppy                 55416  0 
via_rhine              27653  0 
psmouse                91329  0 
pata_via               13407  2 
sata_via               13535  0 
mii                    13654  1 via_rhine
```

---

### Post by kansasnoob on 2014-08-21
So your graphics chip is:

> 01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

I maintain over 20 boxes with a slightly different but similar graphics chip:

> VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)

They just won't handle the Unity DE in Trusty but they will ***barely*** run Flashback w/Metacity in Trusty:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

Performance is even poor with Lubuntu and Xubuntu Trusty :(

I get much better performance out of those old boxes using Ubuntu (or Edubuntu) Precise w/ the Classic (no effects) DE:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Of course they must be installed using the archived 12.04.1 images which provide the original Precise series kernel and Xstack (supported until April 2017) to avoid HWE:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

