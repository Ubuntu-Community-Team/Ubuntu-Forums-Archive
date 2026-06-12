---
title: "Toshiba A215 Laptop - Failure to Boot 12.04 LTS"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by ramblinche81 on 2012-11-17
I would appreciate any help overcoming the Ubuntu BSOD during new ISO  install start up on a Toshiba A215 s7413 w/ATI Radeon 1200 graphics on  board.

ISO DVD is good as evidence by load and start on home  built ASUS/AMD 32bit desktop already running with Karmic (which was a  smooth install over two years ago except for sound which was easily  solved)

On laptop, I can get an intro GRUB menu with  Try/Install/Test and F6 related options etc but I can't seem to load a  full kernel of anything.

nomodeset and other F6 options no help.

Before  experiencing below, I even tried disabling auto graphics in BIOS and  setting to LCD+AnalogRGB without success. PhoenixBIOS has few options  features and Toshiba support shows almost no successful Ubuntu  troubleshooting.

The freeze take place during the PnPBIOS check  sequence of boot load, starting lines (line # varies if nomodeset  selected or omitted) preceding and shown below with NOMODESET selected  from F6 boot options

0.024942 vgaarb: device added: PCI :0000 :01:05.0, decodes=io+mem, owns=io+mem,locks=none

0.026292 Expanded Resource reserved due to conflict with PCI Bus #00
0.026506 NetLabel:initializing
no obvious NetLabel line errors then

0.026824 Switching to clocksource pit  (not shown with nomodeset off)
0.037308 AppArmor filesystem enabled
0.037383  pnp: PnP ACPI: disabled      (this is odd to me, the ACPI=off not x  selected from F6 options, only nomodeset is x selected...maybe BIOS set  disabled, not a lot of options in this bios )
0.037423 PnPBIOS:scanning system for PnP BIOS Support
0.037509 PnPBIOS:found PnP BIOS installation structure at 0xc00f83d0
0.3037551 PnPBIOS: PnP BIOS version 1.0, entry 0xf0000 :0x9afd, dseg 0x400
FREEZE BSOD


Most of the solutions appear based on a working kernel, and I don't seem to get there.

Do I have a BIOS conflict that will never by overcome ?

---

### Post by dino99 on 2012-11-17
posts are numerous if you google around "ubuntu a215" but nothing recent.

Found old howto, like:
[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

you said having tested the boot options, but it really seems related to acpi: so try noacpi, nolapic, noapic (one by one or together) or maybe irq=noacpi or irqpoll

---

### Post by ramblinche81 on 2012-11-17
> **dino99 said:**
> posts are numerous if you google around "ubuntu a215" but nothing recent.

Found old howto, like:
[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

you said having tested the boot options, but it really seems related to acpi: so try noacpi, nolapic, noapic (one by one or together) or maybe irq=noacpi or irqpoll

Thanks for pointing me towards that, it might be more useful after I get a working kernel.  The link above has no reference to BSOD and is tied to 8.04 Heron. It does tell you how to improve graphic performance once a working kernel is in place.

I do not have a working kernel. I cannot sudo xxxxxx.

The screen freezes during the PnPBios load.

I have tried the various combinations of nomodeset and ACPI=off and noAPIC noLAPIC...from all 4 on to individuals. SOmething like 24 permutations.

---

### Post by ramblinche81 on 2012-11-17
> **dino99 said:**
> posts are numerous if you google around "ubuntu a215" but nothing recent.

Found old howto, like:
[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

you said having tested the boot options, but it really seems related to acpi: so try noacpi, nolapic, noapic (one by one or together) or maybe irq=noacpi or irqpoll

dino, while your first two suggestions didn't break me through the barrier, it gave me the idea to try pnpbios=off which appears to be the solution

Thank you for sharing what you know !!!:):):)

While booting 12.04 LTS ISO for the Try Ubuntu option, my system would  freeze during the PnPBIOS load sequence as evidence by the command lines  displayed when it freezes. All the permutations of noacpi, noapic,  nolapic, nomodeset had no effect.

dino99 suggested [INDENT]irq=noacpi
or
irqpoll
[/INDENT]which neither helped, but that is ok because I got brave and tried
[INDENT]PnPBIOS=off
[/INDENT]what did I have to lose ?  

System booted with all functions appearing normal so far.
Wireless is active....I have not tried the ethernet port.
Hard drive is accessible, including WinVista folders and files.
Screen resolution looks tight, no waves, wiggles etc
Have not tried USB ports yet

I have NO idea how setting PNPBIOS=OFF made a difference other than it gave control of IRQ to Linux ?

Talk about a blind squirrel finding an acorn.

Now if I can get acpi running I will feel better overall about all systems being stable.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Follow up some thirty minutes later to finalize F6 options needed for start up
F6 Options - nomodeset
edit boot load line by adding pnpbios=off (at end of line before the   - - )
edit boot load line delete quiet splash (this let me see the progress or not of boot load

Another happy Linux/ubuntu very unsophisticated user up and running

Now I'll go check sound and streaming video ???

---

