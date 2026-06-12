---
title: "Installation Problems (I think SATA)"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by TexasTaz on 2008-05-17
Hey Guys,

    I dled the x64 bit Ubuntu 8.04 Tried to install it and it went to the initramfs prompt, I think it's not seeing my hard drive because of the SATA controller, Controller info is as follows:

Identification
Vendor: &#8206;nVidia Corporation

Description: &#8206;MCP65 SATA Controller

Media class: &#8206;IDE interface

Connection
Bus: &#8206;PCI

PCI domain: &#8206;0

Bus PCI #: &#8206;0

PCI device #: &#8206;10

PCI function #: &#8206;0

Vendor ID: &#8206;0x10de

Device ID: &#8206;0x045d

Sub vendor ID: &#8206;0x147b

Sub device ID: &#8206;0x1c39

Misc
Module: &#8206;ahci

Can some one please help if you are in the US I will call you if you have the time, Thanks,

Michael

---

### Post by EXCiD3 on 2008-05-17
It should detect your drives fine . What other hardware do you have and did it display any errors?

You may try using these boot parameters as they have fixed this issue for a few users. Here's how: Just hit F6 at the first menu on the Ubuntu disc and add 
```
all_generic_ide floppy=off irqpoll
```to the boot options.

---

### Post by tofuconfetti on 2008-05-17
The problem actually is that it doesn't seem to see the SATA drives with certain controllers.  It's got to be more complicated than that because the irqpoll parameter alone solved it for me.  Additionally I could ALSO solve the problem by disabling USB legacy support in the BIOS.  I'm still not sure why that works, but when I'm using a USB keyboard, I can disable legacy support and everything works fine without passing any parameters.

I have two computers that require this, an MSI AMD 64 system, and an Intel motherboard with a quadcore processor.  So it happens on several models of motherboards.

---

### Post by TexasTaz on 2008-05-18
Thanks guys I will give that a shot and see if it works, Appreciate the help very much I love ubuntu and was very upset by not being able to install it.

Thanks Again,
Michael

---

