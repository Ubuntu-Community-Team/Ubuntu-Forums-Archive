---
title: "AMD HD 5450 Graphics in 12.10:  No 3D Support with Radeon driver"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by edantes on 2012-11-30
I am trying to install an XFX Radeon HD 5450 graphics card in my Ubuntu 12.10 desktop. I was disappointed that Xorg's radeon driver does not support Unity 3D for this card.

Is that really the case?  Using this same driver Unity 3D works fine with the motherboard built-in graphics a (radeon X1200).

This is the output for /usr/lib/nux/unity_support_test -p
> 
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  2.1 Mesa 9.0

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no



This is the output fot lspci -v:
> 
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450/6350] (prog-if 00 [VGA controller])
	Subsystem: XFX Pane Group Inc. Device 303e
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdfc0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon


---

