---
title: "Ubuntu 17.10 upgrade problem"
date: 2018-01-05
forum: Installation &amp; Upgrades
---

### Post by whynot on 2018-01-05
Hi everyone
I have quite old Ubuntu system 4.13.0-21-generic and intel core 2 cpu 6300 1.86GHZ.With this system I could do most of the things.After I upgrade from 17.04 to 17.10 everything went well.But at the login screen there was a screen but it was unrecognizable.You can see screenshut at the bottom.Is it possible to turn that back to normal?
```
$ lspci | grep ' VGA '
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV535 [Radeon X1650 PRO] (rev 9e)

```

```
$ uname -a
Linux whynot-Bus 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:35 UTC 2017 i686 i686 i686 GNU/Linux

```

```
$ lspci -nnk | grep -i vga -A3 | grep 'in use'
	Kernel driver in use: radeon
```

```
$ sudo update-pciids
Downloaded daily snapshot dated 2017-12-20 03:15:01

```

```
$ lspci -nn | grep -E 'VGA|Display'
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV535 [Radeon X1650 PRO] [1002:71c7] (rev 9e)
01:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV535 [Radeon X1650 PRO] (Secondary) [1002:71e7] (rev 9e)

```

```

$ dmesg | egrep 'drm|radeon'
[    2.123310] [drm] radeon kernel modesetting enabled.
[    2.123380] fb: switching to radeondrmfb from VESA VGA
[    2.123815] [drm] initializing kernel modesetting (RV530 0x1002:0x71C7 0x174B:0x0840 0x9E).
[    2.125393] [drm] Generation 2 PCI interface, using max accessible memory
[    2.125398] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[    2.125401] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[    2.125415] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.125416] [drm] RAM width 128bits DDR
[    2.125523] [drm] radeon: 256M of VRAM memory ready
[    2.125525] [drm] radeon: 512M of GTT memory ready.
[    2.125535] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.126239] [drm] Possible lm63 thermal controller at 0x4c
[    2.128399] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[    2.129411] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    2.129437] radeon 0000:01:00.0: WB enabled
[    2.129441] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000000 and cpu addr 0xffc1e000
[    2.129443] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.129444] [drm] Driver supports precise vblank timestamp query.
[    2.129446] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    2.129496] radeon 0000:01:00.0: radeon: using MSI.
[    2.129516] [drm] radeon: irq initialized.
[    2.129524] [drm] Loading R500 Microcode
[    2.129728] [drm] radeon: ring at 0x0000000010001000
[    2.129759] [drm] ring test succeeded in 9 usecs
[    2.139389] [drm] ib test succeeded in 0 usecs
[    2.144318] [drm] Radeon Display Connectors
[    2.144320] [drm] Connector 0:
[    2.144321] [drm]   VGA-1
[    2.144323] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.144324] [drm]   Encoders:
[    2.144325] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.144326] [drm] Connector 1:
[    2.144327] [drm]   SVIDEO-1
[    2.144328] [drm]   Encoders:
[    2.144329] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[    2.144330] [drm] Connector 2:
[    2.144330] [drm]   DVI-I-1
[    2.144331] [drm]   HPD1
[    2.144333] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.144334] [drm]   Encoders:
[    2.144335] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.144335] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[    2.274228] [drm] fb mappable at 0xE00C0000
[    2.274230] [drm] vram apper at 0xE0000000
[    2.274231] [drm] size 7258112
[    2.274231] [drm] fb depth is 24
[    2.274232] [drm]    pitch is 6912
[    2.274314] fbcon: radeondrmfb (fb0) is primary device
[    2.274461] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.280086] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0

```

Thanks and Happy New Year.

---

### Post by whynot on 2018-01-05
Solved
Ok I solved the issue with this command
```

sudo dpkg-reconfigure gdm3

```
afterwards I choose ldm and reboot.
Thats it.

---

### Post by sienile on 2018-04-09
I also have an **AMD Radeon** video chipset (mines an APU, unlike whynot's) running on the **4.13 kernel** and had a similar issue (black screen after login screen) upon upgrading to **17.10**. After seeing this thread, **switching from gdm3 to lightdm solved my issue**. Perhaps there is an issue with the combination of the 4.13 kernel, gdm3, and Radeons?

Relevant system identifiers:
```
$ lspci | grep ' VGA '
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8370D]


$ uname -a
Linux ubuntu 4.13.0-38-lowlatency #43-Ubuntu SMP PREEMPT Wed Mar 14 16:20:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```
Thanks for the help, whynot!

---

