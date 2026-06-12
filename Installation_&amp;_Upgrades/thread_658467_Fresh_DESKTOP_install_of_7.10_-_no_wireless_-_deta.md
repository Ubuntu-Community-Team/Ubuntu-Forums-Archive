---
title: "Fresh DESKTOP install of 7.10 - no wireless - detailed info provided"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by jw2k_fr on 2008-01-04
Hi

I have just installed 7.10 on a spare desktop I have sitting around.  All seems good except for that fact that it doesn't want to set up the wireless.  I have tried updating the bios to the latest version and then reset to defaults.  After that, I enabled SMART and disabled onboard audio, think that's all.  System is not overclocked

Basic hardware specs as follows:

> Motherboard - MSI 6547 v2 - SIS 645 Ultra chipset with latest bios.
Processor - P4 1.8Ghz
Memory - 1Gb Corsair PC3200C2 (single dimm nicked from my games machine to troubleshoot)
Audio - SB Live 1024   - in PCI slot 6 (furthest from AGP)
Wireless - Netgear WG311 v2   - in PCI slot 2
Display - Leadtek GF4 Ti4200
Storage - Maxtor 40Gb HD,    LiteOn LTD163D DVD,    LG  GCE-8320B CD-RW


The wireless card is picked up during boot as follows:

> [   40.452093] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   40.452099] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   40.452187] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 18
[   40.452208] acx: found ACX111-based wireless network card at 0000:00:06.0, irq:18, phymem1:0xDFFFA000, phymem2:0xDFFA0000, mem1:0xf891c000, mem1_size:8192, mem2:0xf8a00000, mem2_size:131072
[   40.453218] acx: loading firmware for acx1111 chipset with radio ID 16
[   41.001741] input: PC Speaker as /class/input/input2
[   41.592339] acx: FATAL: firmware upload: data parts at offset 4 don't match (0xEA000633 vs. 0xFFFFFFFF)! I/O timing issues or defective memory, with DWL-xx0+? ACX_IO_WIDTH=16 may help. Please report
[   41.592347] acx: firmware upload attempt #1 FAILED, retrying...
[   41.670664] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   41.711729] parport_pc 00:0a: reported by Plug and Play ACPI
[   41.711842] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   42.618656] acx: FATAL: firmware upload: data parts at offset 4 don't match (0xEA000633 vs. 0xFFFFFFFF)! I/O timing issues or defective memory, with DWL-xx0+? ACX_IO_WIDTH=16 may help. Please report
[   42.618665] acx: firmware upload attempt #2 FAILED, retrying...
[   43.641153] acx: FATAL: firmware upload: data parts at offset 4 don't match (0xEA000633 vs. 0xFFFFFFFF)! I/O timing issues or defective memory, with DWL-xx0+? ACX_IO_WIDTH=16 may help. Please report
[   43.641159] acx: firmware upload attempt #3 FAILED, retrying...
[   44.663633] acx: FATAL: firmware upload: data parts at offset 4 don't match (0xEA000633 vs. 0xFFFFFFFF)! I/O timing issues or defective memory, with DWL-xx0+? ACX_IO_WIDTH=16 may help. Please report
[   44.663638] acx: firmware upload attempt #4 FAILED, retrying...
[   45.686111] acx: FATAL: firmware upload: data parts at offset 4 don't match (0xEA000633 vs. 0xFFFFFFFF)! I/O timing issues or defective memory, with DWL-xx0+? ACX_IO_WIDTH=16 may help. Please report
[   45.686116] acx: firmware upload attempt #5 FAILED, retrying...
[   46.684713] acx: reset_dev() FAILED
[   46.684740] ACPI: PCI interrupt for device 0000:00:06.0 disabled
[   46.684769] acx_pci: probe of 0000:00:06.0 failed with error -5
[   46.684902] usbcore: registered new interface driver acx_usb
[   46.685175] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 18


iwconfig returns:

> lo        no wireless extensions.

Other errors which I came across in the boot log was as follows:

> [    24.577913] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found

[    27.585654] fuse init (API version 7.8)
[    27.593713] Failure registering capabilities with primary security module


Very grateful for any and all assistance in getting this nailed
Thx

James

---

### Post by oldsoundguy on 2008-01-04
my wireless installed without a hitch, but you do have to use system> administration> network.

IF that fails: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by jw2k_fr on 2008-01-04
Thanks for the reply - glad YOU aren't having problems ;)

system->administration->network   only lists a modem connection, which is disabled

I checked that page - the card is listed as being supported and it is listed as working out of the box, which was what led me to post the detailed info.  Comment on the page listing supported Netgear PCI adapters is:

> Worked out of the box with Breezy. WEP now works 100%!

Thanks for trying!

Any other ideas?

Thanks
James

---

### Post by jw2k_fr on 2008-01-04
So it appears to be a hardware conflict kinda problem.

I removed the soundcard and dropped the wireless card down into the sixth PCI slot and now it detects it in ubuntu.  However, I am having problems getting it to connect to any network.  I have two in the house, one of which uses WPA (which I don't see as a security option), the other is open but uses MAC filtering.  There is a third locally which is unencrypted (am able to connect with my laptop no problem) and I can't get this desktop to connect to any of them

I also just had the network settings window lock up.  Could my drivers need updating?  I'm a windows sysadmin but have no idea how to do the same thing here.

Having now rebooted, the machine refuses to boot.   ARRGHH!!  I'm really fighting the temptation to say that linux isn't ready for the mainstream... but it's always different when your particular system has a problem

The machine now gets partway through a list of bootup items on a text screen.
Last half dozen successful lines:

* Starting system message bus dbus                                                      [OK]
* Starting network connection manager NetworkManager                     [OK]
* Starting network events dispatcher NetworkManagerDispatcher        [OK]
* Starting System Tools Backends system-tools-backends                     [OK]
* Starting Hardware abstraction layer hald                                            [OK]
* Starting Common Unix Printing System: cupsd

Elapsed waiting time currently five plus minutes.  Caps lock still works and if I hit ctrl-alt-del it should start to reboot like it did last time I tried it, but will most likely hang without shutting down cleanly, again, like last time.

Any help VERY gratefully accepted
Thx

James

---

### Post by jw2k_fr on 2008-01-10
I have now gone and bought a new wireless card of the same model and tried to re-install from the desktop version and it hangs at the point where it is trying to set up APT and is scanning the mirror.

The machine is still responding as I can access the menus on the toolbar, but the install process stays the same way for at least twenty minutes

Am I SOL?  Or does anyone have any suggestions?  Am I going to have to select a different distro to try and get this machine working?

---

