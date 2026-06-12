---
title: "Sound worked on 8.04, fails on 8.10 (AMD64)"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by pbewig on 2008-11-12
I have a home-built system with Asus motherboard and AMD64 cpu.  Sound worked properly on 8.04.  I upgraded to 8.10 yesterday, and am patched up-to-date, but sound fails -- instead of sound, I just get some very fast clicking noises.  Some details:

lspci -v:
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8242
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

What should I do to get sound working?

Many thanks,

Phil

---

### Post by cdtech on 2008-11-12
Me as well. I'm still working on this issue and will let you know if I have a solution. I'm sure there are a ton of others with this problem as well, maybe we could pull together and find a cure.

I'm working on the pulse issue but still no luck by removing.

---

### Post by pbewig on 2008-11-14
Still need help!  Anybody?

---

### Post by iaskedalice09 on 2008-11-14
This is from the Dell Linux wiki, but it's worth a shot!

[Ubuntu 8.04/Issues/No Sound After Distribution Or Kernel Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

Let me know and hope this helps!

---

### Post by cdtech on 2008-11-14
I don't know what I did, but now I have sound. I just opened up a KDE session then went right back into GDM now I have sound. lol

I'm looking now to see what was woke up......

---

