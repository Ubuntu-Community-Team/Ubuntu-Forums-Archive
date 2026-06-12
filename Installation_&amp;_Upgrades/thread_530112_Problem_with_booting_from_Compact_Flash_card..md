---
title: "Problem with booting from Compact Flash card."
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by derjoerg on 2007-08-20
Hi,

I just got a Soekris net5501 ([www.soekris.com]("http://www.soekris.com/net5501.htm")). This is an embetted system with AMD Geode LX chip. It will be booted over a compact flash card which is actually configured as "Primary Slave" (hdb). The system has no graphic on board and is, at first, only  configurable over a serial console.

The pxe-installation of ubuntu feisty server works well, no problem. I used the entiry compact flash for the system (hdb1) and a swap-file (hdb5).

When I restart the system after the installation, grub is displayed and I can select the desired Kernel to install.
After some output of the loading I get an "Alert", that /dev/hdb1 (boot-partition) does not exist and "BusyBox" is started with the following prompt: (initramfs)

After two unsuccessful tries, I installed the new debian-stable-release and everything worked :confused:

Can someone help me get ubuntu works on this system?


Here is the output of the serial console:
```

[   30.957118] SMP motherboard not detected.
[   31.005147] Local APIC not detected. Using dummy APIC emulation.
[   31.077221] Brought up 1 CPUs
[   31.113666] Booting paravirtualized kernel on bare hardware
[   31.180503] Time: 11:33:04  Date: 07/21/107
[   31.230623] NET: Registered protocol family 16
[   31.284068] EISA bus registered
[   31.323331] PCI: PCI BIOS revision 2.01 entry at 0xfac61, last bus=0
[   31.399372] PCI: Using configuration type 1
[   31.449482] Setting up standard PCI resources
[   31.508616] ACPI: Interpreter disabled.
[   31.554491] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.622295] pnp: PnP ACPI: disabled
[   31.664062] PnPBIOS: Scanning system for PnP BIOS support...
[   31.732309] PnPBIOS: PnP BIOS support was not detected.
[   31.795000] PCI: Probing PCI hardware
[   31.854845] NET: Registered protocol family 8
[   31.907021] NET: Registered protocol family 20
[   31.961575] NET: Registered protocol family 2
[   32.053697] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   32.138326] TCP established hash table entries: 65536 (order: 7, 524288 bytes
)
[   32.226714] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
[   32.306714] TCP: Hash tables configured (established 65536 bind 32768)
[   32.384831] TCP reno registered
[   32.433969] checking if image is initramfs... it is
[   36.004627] Freeing initrd memory: 6625k freed
[   36.059231] audit: initializing netlink socket (disabled)
[   36.123864] audit(1187695951.960:1): initialized
[   36.179582] VFS: Disk quotas dquot_6.5.1
[   36.226610] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   36.305001] io scheduler noop registered
[   36.352121] io scheduler anticipatory registered
[   36.407534] io scheduler deadline registered
[   36.458901] io scheduler cfq registered (default)
[   36.516380] isapnp: Scanning for PnP cards...
[   36.924258] isapnp: No Plug & Play device found
[   37.113020] Real Time Clock Driver v1.12ac
[   37.162384] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[   37.255316] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.327839] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.401781] mice: PS/2 mouse device common for all mice
[   37.466884] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   37.558115] input: Macintosh mouse button emulation as /class/input/input0
[   37.640603] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   37.716645] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[   37.813293] PNP: No PS/2 controller found. Probing ports directly.
[   38.141008] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.200937] EISA: Probing bus 0 at eisa.0
[   38.249019] EISA: Detected 0 cards.
[   38.291130] TCP cubic registered
[   38.329827] NET: Registered protocol family 1
[   38.382066] Using IPI No-Shortcut mode
[   38.427054]   Magic number: 3:784:580
[   38.470881] Time: tsc clocksource has been installed.
[   38.532061] Freeing unused kernel memory: 328k freed
Loading, please wait...
Begin: Loading essential drivers[   39.535336] Capability LSM initialized
... ...
Done.
Begin: Running /scripts/init-premount ...
[   39.807167] thermal: Unknown symbol acpi_processor_set_thermal_limit
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
[   41.867222] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   41.956178] eth0: VIA Rhine III (Management Adapter) at 0x1e100, 00:00:24:c8:
de:a8, IRQ 11.
[   42.057559] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1
Link 41e1.
[   42.158798] eth1: VIA Rhine III (Management Adapter) at 0x1e200, 00:00:24:c8:
de:a9, IRQ 5.
[   42.259245] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1
Link 0000.
[   42.478563] eth2: VIA Rhine III (Management Adapter) at 0x1e300, 00:00:24:c8:
de:aa, IRQ 9.
[   42.578938] eth2: MII PHY found at address 1, status 0x7849 advertising 05e1
Link 0000.
[   42.683330] eth3: VIA Rhine III (Management Adapter) at 0x1e400, 00:00:24:c8:
de:ab, IRQ 12.
[   42.784784] eth3: MII PHY found at address 1, status 0x7849 advertising 05e1
Link 0000.
[   43.139169] usbcore: registered new interface driver usbfs
[   43.204891] usbcore: registered new interface driver hub
[   43.268521] usbcore: registered new device driver usb
[   43.333379] ohci_hcd 0000:00:14.4: OHCI Host Controller
[   43.396240] ohci_hcd 0000:00:14.4: new USB bus registered, assigned bus numbe
r 1
[   43.484808] ohci_hcd 0000:00:14.4: irq 7, io mem 0xa0020000
[   43.705954] usb usb1: configuration #1 chosen from 1 choice
[   43.772755] hub 1-0:1.0: USB hub found
[   43.820610] hub 1-0:1.0: 4 ports detected
[   43.955800] SCSI subsystem initialized
[   44.032567] ehci_hcd 0000:00:14.5: EHCI Host Controller
[   44.095238] ehci_hcd 0000:00:14.5: new USB bus registered, assigned bus numbe
r 2
[   44.207883] ehci_hcd 0000:00:14.5: irq 7, io mem 0xa0021000
[   44.274588] ehci_hcd 0000:00:14.5: USB 0.0 started, EHCI 1.00, driver 10 Dec
2004
[   44.364540] usb usb2: configuration #1 chosen from 1 choice
[   44.431363] hub 2-0:1.0: USB hub found
[   44.476278] hub 2-0:1.0: 4 ports detected
[   44.645828] AMD5536: IDE controller at PCI slot 0000:00:14.2
[   44.713743] AMD5536: chipset revision 1
[   44.759663] AMD5536: not 100% native mode: will probe irqs later
[   44.831709] AMD5536: 0000:00:14.2 (rev 01) UDMA100 controller
[   44.900578] AMD5536: neither IDE port enabled (BIOS)
Done.
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/dbh1 does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Kind Regards and many thanks in advance

Joerg Schoppet

---

### Post by kerry_s on 2007-08-20
Why? debian is much better for that setup. ubuntu would be slow.
 nice board, what was the cost? What setup are you running with debian?


i was thinking f getting this, to build a mini system> 
[http://www.damnsmalllinux.org/store/Mini_ITX_Systems/Mini_ITX_BareBones_Computer](http://www.damnsmalllinux.org/store/Mini_ITX_Systems/Mini_ITX_BareBones_Computer)

i use debian base+jwm for my setup. 450mhz 256ram

---

### Post by derjoerg on 2007-08-20
Hi,

> Why? debian is much better for that setup. ubuntu would be slow.
Very simply: Because I know Ubuntu (have installed it actually on three servers and a laptop.
Why would ubuntu be slow?

> nice board, what was the cost?
A distributor in germany wants 350 Euro.

> What setup are you running with debian?
Actually, I've installed only the "standard-system", but I want to extend it to act as a wireless access-point, router, backup-server and (if possible) VDR.


So, no plan, why ubuntu doesn't want to boot?

Joerg

---

### Post by derjoerg on 2007-08-26
Actually I get it to work, find my descriptions in the ubuntu-wiki
[https://wiki.ubuntu.com/Soekris](https://wiki.ubuntu.com/Soekris)

Regards

Joerg Schoppet

---

