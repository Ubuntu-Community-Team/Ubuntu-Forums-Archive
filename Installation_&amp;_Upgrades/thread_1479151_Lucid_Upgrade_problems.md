---
title: "Lucid Upgrade problems"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by skibum3027 on 2010-05-10
I have two problems I cannot solve following my upgrade to Lucid from Karmic.

1. I have four hard drives (SATA) set up so that two of them are responsible for OSes, and two hold my music and movies. Following the upgrade, anytime I have the extra hard drives plugged in, my system fails to boot, saying that device sda7 has unrecoverable errors. sda7 is my /home partition. Without the extra hard drives it works just fine. The only reason I can think for this to happen is a soft link I made between sdc (Movies I) and /home/USERNAME/Music. I have no idea what to do from here.

2. I have no sound :( Worse yet, I have tried so many different "Comprehensive Sound Solution" guides on the forums that I don't even know where to start on this issue any more. I've worked my way through [this guide]("http://ubuntuforums.org/showthread.php?t=766683&highlight=ac+889a") and _[U]_[/U][this guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=ac+889a") most recently, and seeing as there's still no sound, I can only assume I've made things worse. My sound card is an ALC889A. I need the optical sound since it's all I have spots for on my receiver. I've put the output of a couple different commands below, and I can add whatever else anyone needs to help me.

```
USERNAME@MY-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I shortened this one :)
```
mike@mike-desktop:~$ lspci -v

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: nVidia Corporation Device c55e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at cfff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

Any ideas for either problem?

---

