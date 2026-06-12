---
title: "soundcard not working after gutsy upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by hinge on 2007-10-21
Hi there,

I upgraded to gutsy 2 days ago - everything went smooth during the upgrade, it seemed.

Yesterday I found out that I have no sound...did some checking...

```
martin@glass:~$ aplay -l
aplay: device_list:204: no soundcards found...
```

```
martin@glass:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

```
martin@glass:~$ sudo lshw -class sound
  *-multimedia UNCLAIMED
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

```

OK - so my conclusion is that my hardware is OK but the alsa driver is not loaded.

Before I did the gutsy upgrade I had no problems with my sound - I never even checked which alsa driver I used - it just worked.
I went to the alsa project page and found that I should be using the snd-intel-hda driver. So I tried to modprobe it and found out that it does not exist on my system among the 152 snd drivers.
Did some googling and searches in the forums and found that people are actually compiling all the alsa stuff in order to get this working - is this really correct ??
I had this working on feisty - were I using another driver ?
Why would this not work on gutsy ??

Does anybody have the same chipset / soundcard working under gutsy / feisty ? which driver are you using ?

---

### Post by Gimli on 2007-10-21
I am having the same problem, my soundcard is intel ICH7 chipset. Mine was working fine on fiesty as well.

Will this be fixed soon or do we have to compile as mentioned above?

---

### Post by Gimli on 2007-10-21
I found this post by OPM8 which solved my sound problem. Boot into the generic kernel and all is well.

[http://ubuntuforums.org/showthread.php?t=582408](http://ubuntuforums.org/showthread.php?t=582408)

---

### Post by hinge on 2007-10-21
Yep, works fine !!

---

