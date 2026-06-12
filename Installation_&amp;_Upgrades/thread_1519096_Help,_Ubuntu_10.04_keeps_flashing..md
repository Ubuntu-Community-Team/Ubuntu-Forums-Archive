---
title: "Help, Ubuntu 10.04 keeps flashing."
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by edissono on 2010-06-27
Well hello. I just recently installed Ubuntu 10.04. Every time I boot it up the screen flashes, like going off, then on again. It won't stop doing that. I can see the screen for 1 sec then it goes black, and keeps repeating this. Can anyone help me please?

---

### Post by fr0sty on 2010-06-27
Sorry if I am asking a redundant question... You were able to install ubuntu and now it flashes, or you are trying to install and the screen is flashing? Post the specs of your comp, and we may be able to help if it is hardware issues.

---

### Post by edissono on 2010-06-27
General Spec
Brand	HP
Series	Pavilion
Model	M9400F(FK790AA)
Type	Media Center / HTPC
Processor	AMD Phenom X4 9750(2.4GHz)
Processor Main Features	64 bit Quad-Core Processor
Cache Per Processor	4 x 512KB L2 Cache
Memory	8GB DDR2 800
Hard Drive	750GB SATA 7200RPM
Optical Drive 1	SuperMulti DVD Burner with LightScribe Technology
Graphics	ATI Radeon HD 3650 graphics card with 512MB dedicated graphics memory, DVI, HDMI and VGA capabilities, and support for Microsoft DirectX 10. Up to 2303MB Total Available Graphics Memory as allocated by Windows Vista
Audio	High Definition Audio
Ethernet	Integrated 10/100 Base-T networking interface
Wireless Card	Wireless LAN 802.11 b/g/n
Keyboard	HP multimedia keyboard
Mouse	HP optical mouse
Operating System	Windows Vista Home Premium 64-bit
Motherboard
Chipset	NVIDIA nForce 430
CPU
CPU Type	Phenom X4
Installed Qty	1
CPU Speed	9750(2.4GHz)
L2 Cache Per CPU	4 x 512KB
CPU Socket Type	AM2+
CPU Main Features	64 bit Quad-Core Processor
Graphics
GPU/VPU Type	ATI Radeon HD 3650
Graphics Interface	PCI Express x16
Memory
Memory Capacity	8GB DDR2
Memory Speed	DDR2 800
Form Factor	DIMM 240-pin
Memory Spec	2GB x 4
Memory Slots (Available/Total)	0/4
Maximum Memory Supported	8GB
Hard Drive
HDD Capacity	750GB
HDD Interface	SATA
HDD RPM	7200rpm

I know half of this stuff is useless. Umm I installed it 20 mins ago. When I boot it up, it flashes, blinks, I really don't know how to explain. The screen turns black for a second, then normal for a sec, then black for a second, then normal, and just keeps repeating.

---

### Post by fr0sty on 2010-06-27
Well on an unrelated note, that is a pretty kickass system. Now on a related note. I think your issue may be that your graphics card is an ATI graphics card. I personally haven't worked with an ATI graphics card myself, but it seems that there is a lack of support for those cards. Sorry about not really having a clue to how you fix it.

---

### Post by ronparent on 2010-06-27
Which graphics port are you using. If you can, will switching to another port work? If that doesn't work, try booting with the nomodeset parameter.

If one of the above options work, you can probably activate the proprietary video driver and restore your preferred video hookup and eliminate the nomodeset with no further problems.

---

### Post by RJARRRPCGP on 2010-06-27
I had a similar problem with the nv driver, when using Kubuntu in the past and using the proprietary driver solved the problem, at least with Nvidia. 

I only saw a problem like that with KDE.

---

