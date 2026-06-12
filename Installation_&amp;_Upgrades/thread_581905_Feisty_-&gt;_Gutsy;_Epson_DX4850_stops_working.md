---
title: "Feisty -&gt; Gutsy; Epson DX4850 stops working"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by amelyst on 2007-10-19
After upgrading from feisty to gutsy (kubuntu flavour by the way), I am no longer able to print anything on my espon dx4850. 
It worked flawless with feisty. 
I am using cups with the gutenprint drivers. The print jobs just get queued and nver make it to the printer.
Using the cups web interface I see the follwoing error with my printer:
```
"Unable to open parallel port device file: Permission denied"
```

The funny thing is, that this is an usb printer. The error message isn't even specifying the atual device name.

I did some digging and notice now some changes in the detection of the printer:

The uri is different in the two versions:
feisty: usb://EPSON/Stylus DX4800
gutsy: epson://dev/usb/lp0

After enabling the debug info I found the follwoing lines in my cups error log:

```
I [19/Oct/2007:22:23:50 +0200] [Job 394] Started filter /usr/lib/cups/filter/pstops (PID 7846)
I [19/Oct/2007:22:23:50 +0200] [Job 394] Started filter /usr/lib/cups/filter/pstoraster (PID 7847)
I [19/Oct/2007:22:23:50 +0200] [Job 394] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 7849)
I [19/Oct/2007:22:23:50 +0200] [Job 394] Started backend /usr/lib/cups/backend/epson (PID 7850)
D [19/Oct/2007:22:23:50 +0200] Discarding unused job-state event...
D [19/Oct/2007:22:23:50 +0200] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
E [19/Oct/2007:22:23:50 +0200] PID 7850 (/usr/lib/cups/backend/epson) stopped with status 1!
E [19/Oct/2007:22:23:50 +0200] [Job 394] Unable to open parallel port device file: Permission denied
```

So it seems there is a problem with the backend process, which exits with an error is no longer able to deliver the data to the printer itself.

Anyone here with some ideas, or maybe just a confirmation of the my problem ?

Any help is highly appreciated.

---

### Post by miestrâ on 2007-10-21
I have exactly the same problem - except with an Epson Stylus C41UX printer.

---

### Post by amelyst on 2007-10-21
I have opened a bug report at launchpad. See here [https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/154833](https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/154833) for further details.

As it seems, there may be a problem with the epson backend in the cups-driver-gutenprint package. I will do some more investigations and will also post here if any solution come up.

---

### Post by miestrâ on 2007-10-21
Here's my own "printingbuginfo" output. I do note that there are some differences from the one posted in the bug report above: for example, the fields for "UsbPrinterDevices:" and "UsbPrinterIEEE1284Id:" are blank, which is possibly not a good sign. I should also point out that the Stylus C41-UX is a singlefunction device (printer).

Apart from that, as I say, the symptoms I'm suffering are the same as those above - print job gets queued to the printer, hangs there for a while, and then comes back with a message saying "Unable to open parallel printer port" or similar (when it's a USB printer).

---

### Post by amelyst on 2007-10-22
It looks like your device file is not found.

What owner/group and permissions does your device ( /dev/usb/lp0) have ?

---

### Post by miestrâ on 2007-10-22
lrwxrwxrwx 1 root root 3 2007-10-22 11:14 /dev/usb/lp0 -> lp0

---

### Post by amelyst on 2007-10-22
This does not look right. As far as I know the device /dev/usb/lp0 should not be a link as it is in your case. Furthermore it points to itself, leaving you with no evidence where the real device should be.

When you disconnect your printer and look at the /dev/usb directory, is there still an entry visible ? If so, try to remove this entry, turn on the printer and look at the /dev/usb directory again.

If not, turn on the printer and see if you really have a link in place.

There should be a link /dev/usblp0 pointing to /dev/usb/lp0.

---

### Post by miestrâ on 2007-10-22
/dev/usb/lp0 disappears when I switch the printer off and reappears when I switch it on. No sign of any /dev/usblp0.

---

### Post by amelyst on 2007-10-22
Is this the output in your /dev directory using ls -al /dev/usb* after turning on your printer ?

Could you post the output of the command dmesg just after you connected and turned on your printer. We just have to be sure the printer is detected at all, and this should turn up in the dmesg output.

---

### Post by miestrâ on 2007-10-22
Sebastienne:~$ ls -al /dev/usb*

crw-rw---- 1 root root 189,   0 2007-10-23 00:14 /dev/usb1
crw-rw---- 1 root root 189, 128 2007-10-23 00:14 /dev/usb2
crw-rw---- 1 root root 189, 256 2007-10-23 00:14 /dev/usb3
crw-rw---- 1 root root 189, 384 2007-10-23 00:14 /dev/usb4
crw-rw---- 1 root root 254,   0 2007-10-23 00:14 /dev/usbdev1.1_ep00
crw-rw---- 1 root root 254,   1 2007-10-23 00:14 /dev/usbdev1.1_ep81
crw-rw---- 1 root root 254,   8 2007-10-22 22:11 /dev/usbdev1.4_ep00
crw-rw---- 1 root root 254,   9 2007-10-22 22:11 /dev/usbdev1.4_ep01
crw-rw---- 1 root root 254,  10 2007-10-22 22:11 /dev/usbdev1.4_ep82
crw-rw---- 1 root root 254,   2 2007-10-23 00:14 /dev/usbdev2.1_ep00
crw-rw---- 1 root root 254,   3 2007-10-23 00:14 /dev/usbdev2.1_ep81
crw-rw---- 1 root root 254,   4 2007-10-23 00:14 /dev/usbdev3.1_ep00
crw-rw---- 1 root root 254,   5 2007-10-23 00:14 /dev/usbdev3.1_ep81
crw-rw---- 1 root root 254,   6 2007-10-23 00:14 /dev/usbdev4.1_ep00
crw-rw---- 1 root root 254,   7 2007-10-23 00:14 /dev/usbdev4.1_ep81
crw-rw---- 1 root root 254,  11 2007-10-22 16:10 /dev/usbdev4.3_ep00
crw-rw---- 1 root root 254,  12 2007-10-22 16:10 /dev/usbdev4.3_ep01
crw-rw---- 1 root root 254,  13 2007-10-22 16:10 /dev/usbdev4.3_ep82
crw-rw---- 1 root root 254,  14 2007-10-22 16:10 /dev/usbdev4.3_ep83

/dev/usb:
total 0
drwxr-xr-x  2 root root    60 2007-10-22 22:11 .
drwxr-xr-x 14 root root 14400 2007-10-22 22:11 ..
lrwxrwxrwx  1 root root     3 2007-10-22 22:11 lp0 -> lp0

Sebastienne:~$ dmesg

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002dff0000 (usable)
[    0.000000]  BIOS-e820: 000000002dff0000 - 000000002dff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002dff8000 - 000000002e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 735MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 188400) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   188400
[    0.000000]   HighMem    188400 ->   188400
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   188400
[    0.000000] On node 0 totalpages: 188400
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1439 pages used for memmap
[    0.000000]   Normal zone: 182865 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA1F0 checksum 0
[    0.000000] ACPI: RSDP 000FA1F0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 2DFF0000, 002C (r1 AMIINT VIA_P6         10 MSFT       97)
[    0.000000] ACPI: FACP 2DFF0030, 0081 (r1 AMIINT VIA_P6         11 MSFT       97)
[    0.000000] ACPI: DSDT 2DFF0120, 3045 (r1    VIA   P4M266     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 2DFF8000, 0040
[    0.000000] ACPI: APIC 2DFF00C0, 005C (r1 AMIINT VIA_P6          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2e000000:d0c00000)
[    0.000000] Built 1 zonelists.  Total pages: 186929
[    0.000000] Kernel command line: root=UUID=b8b10658-6c5d-459f-aaa9-a4f8f7bcd1dd ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1996.831 MHz processor.
[   15.547504] Console: colour VGA+ 80x25
[   15.549517] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.552331] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.586036] Memory: 735244k/753600k available (2015k kernel code, 17772k reserved, 916k data, 364k init, 0k highmem)
[   15.586052] virtual kernel memory layout:
[   15.586054]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.586055]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.586057]     vmalloc : 0xee800000 - 0xff7fe000   ( 271 MB)
[   15.586058]     lowmem  : 0xc0000000 - 0xedff0000   ( 735 MB)
[   15.586061]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.586063]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   15.586064]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   15.586068] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.586138] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.666052] Calibrating delay using timer specific routine.. 3999.72 BogoMIPS (lpj=7999454)
[   15.666110] Security Framework v1.0.0 initialized
[   15.666128] SELinux:  Disabled at boot.
[   15.666154] Mount-cache hash table entries: 512
[   15.666516] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   15.666548] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   15.666552] CPU: L2 cache: 128K
[   15.666556] CPU: Hyper-Threading is disabled
[   15.666561] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   15.666585] Compat vDSO mapped to ffffe000.
[   15.666628] Checking 'hlt' instruction... OK.
[   15.682356] SMP alternatives: switching to UP code
[   15.683293] Freeing SMP alternatives: 11k freed
[   15.684133] Early unpacking initramfs... done
[   16.180931] ACPI: Core revision 20070126
[   16.181075] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.183870] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
[   16.183943] Total of 1 processors activated (3999.72 BogoMIPS).
[   16.184717] ENABLING IO-APIC IRQs
[   16.185097] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.329168] Brought up 1 CPUs
[   16.329625] Booting paravirtualized kernel on bare hardware
[   16.329830] Time: 11:14:14  Date: 09/22/107
[   16.329929] NET: Registered protocol family 16
[   16.330376] EISA bus registered
[   16.330428] ACPI: bus type pci registered
[   16.333297] PCI: PCI BIOS revision 2.10 entry at 0xfdae1, last bus=1
[   16.333301] PCI: Using configuration type 1
[   16.333303] Setting up standard PCI resources
[   16.342798] ACPI: EC: Look up EC in DSDT
[   16.348197] ACPI: Interpreter enabled
[   16.348211] ACPI: (supports S0 S1 S4 S5)
[   16.348249] ACPI: Using IOAPIC for interrupt routing
[   16.366340] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.366359] PCI: Probing PCI hardware (bus 00)
[   16.367291] PCI quirk: region 0800-087f claimed by vt8235 PM
[   16.367299] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   16.367884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.390340] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   16.390531] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   16.390706] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   16.390880] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   16.391266] ACPI: Power Resource [URP1] (off)
[   16.391374] ACPI: Power Resource [URP2] (off)
[   16.391462] ACPI: Power Resource [FDDP] (off)
[   16.391542] ACPI: Power Resource [LPTP] (off)
[   16.391605] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.391655] pnp: PnP ACPI init
[   16.391698] ACPI: bus type pnp registered
[   16.399836] pnp: PnP ACPI: found 12 devices
[   16.399851] ACPI: ACPI bus type pnp unregistered
[   16.399860] PnPBIOS: Disabled by ACPI PNP
[   16.400113] PCI: Using ACPI for IRQ routing
[   16.400122] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.403499] NET: Registered protocol family 8
[   16.403504] NET: Registered protocol family 20
[   16.403903] pnp: 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[   16.403912] pnp: 00:05: iomem range 0xfee00000-0xfee00fff could not be reserved
[   16.404870] Time: tsc clocksource has been installed.
[   16.435690] PCI: Bridge: 0000:00:01.0
[   16.435701]   IO window: disabled.
[   16.435711]   MEM window: dfd00000-dfefffff
[   16.435717]   PREFETCH window: cfc00000-dfbfffff
[   16.435749] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.435794] NET: Registered protocol family 2
[   16.472912] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.473533] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.479269] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.481383] TCP: Hash tables configured (established 131072 bind 65536)
[   16.481407] TCP reno registered
[   16.493159] checking if image is initramfs... it is
[   16.936057] Switched to high resolution mode on CPU 0
[   17.410618] Freeing initrd memory: 7211k freed
[   17.412448] audit: initializing netlink socket (disabled)
[   17.412492] audit(1193051654.716:1): initialized
[   17.423716] VFS: Disk quotas dquot_6.5.1
[   17.424072] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.424610] io scheduler noop registered
[   17.424619] io scheduler anticipatory registered
[   17.424622] io scheduler deadline registered
[   17.424713] io scheduler cfq registered (default)
[   17.424746] PCI: VIA PCI bridge detected. Disabling DAC.
[   17.424839] Boot video device is 0000:01:00.0
[   17.425631] isapnp: Scanning for PnP cards...
[   17.779520] isapnp: No Plug & Play device found
[   18.037044] Real Time Clock Driver v1.12ac
[   18.037551] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.037750] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.041709] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.046355] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.047028] input: Macintosh mouse button emulation as /class/input/input0
[   18.047499] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.048143] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.048161] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.049219] mice: PS/2 mouse device common for all mice
[   18.049898] EISA: Probing bus 0 at eisa.0
[   18.049952] EISA: Detected 0 cards.
[   18.050330] TCP cubic registered
[   18.050405] NET: Registered protocol family 1
[   18.050492] Using IPI No-Shortcut mode
[   18.051051]   Magic number: 11:12:227
[   18.051204]   hash matches device ttyre
[   18.051462]   hash matches device PNP0200:00
[   18.052818] Freeing unused kernel memory: 364k freed
[   18.082952] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.692991] AppArmor: AppArmor initialized<5>audit(1193051656.716:2):  type=1505 info="AppArmor initialized" pid=1168
[   19.717884] fuse init (API version 7.8)
[   19.735115] Failure registering capabilities with primary security module.
[   19.776039] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.922800] usbcore: registered new interface driver usbfs
[   21.922901] usbcore: registered new interface driver hub
[   21.923037] usbcore: registered new device driver usb
[   21.925213] USB Universal Host Controller Interface driver v3.0
[   21.925440] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 16
[   21.925464] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   21.925944] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   21.926008] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000d800
[   21.926364] usb usb1: configuration #1 chosen from 1 choice
[   21.926455] hub 1-0:1.0: USB hub found
[   21.926492] hub 1-0:1.0: 2 ports detected
[   22.022750] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.022764] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.028116] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 16
[   22.028143] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   22.028221] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   22.028267] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000dc00
[   22.028584] usb usb2: configuration #1 chosen from 1 choice
[   22.028666] hub 2-0:1.0: USB hub found
[   22.028698] hub 2-0:1.0: 2 ports detected
[   22.123559] Floppy drive(s): fd0 is 1.44M
[   22.131900] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 16
[   22.131929] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   22.132022] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   22.132072] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000e000
[   22.132359] usb usb3: configuration #1 chosen from 1 choice
[   22.132444] hub 3-0:1.0: USB hub found
[   22.132475] hub 3-0:1.0: 2 ports detected
[   22.204747] FDC 0 is a post-1991 82077
[   22.238246] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 16
[   22.238291] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   22.238436] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   22.238540] ehci_hcd 0000:00:10.3: irq 16, io mem 0xdfffff00
[   22.238554] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.238859] usb usb4: configuration #1 chosen from 1 choice
[   22.238975] hub 4-0:1.0: USB hub found
[   22.239005] hub 4-0:1.0: 6 ports detected
[   22.241712] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   22.340370] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   22.340413] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   22.340416] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   22.340438] VP_IDE: chipset revision 6
[   22.340442] VP_IDE: not 100% native mode: will probe irqs later
[   22.340461] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   22.340477]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   22.340508]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   22.340524] Probing IDE interface ide0...
[   22.754572] hda: ST380011A, ATA DISK drive
[   23.426022] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.430603] Probing IDE interface ide1...
[   23.525195] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   23.706026] usb 1-2: configuration #1 chosen from 1 choice
[   24.292033] hdc: ASUS DRW-1608P3S, ATAPI CD/DVD-ROM drive
[   25.074739] hdd: WPI CDRW-4424, ATAPI CD/DVD-ROM drive
[   25.132674] ide1 at 0x170-0x177,0x376 on irq 15
[   25.152691] SCSI subsystem initialized
[   25.164267] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 17
[   25.169522] eth0: VIA Rhine II at 0x1d400, 00:0b:6a:0d:f8:5e, IRQ 17.
[   25.170252] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   25.174843] libata version 2.21 loaded.
[   25.216852] hda: max request size: 512KiB
[   25.235988] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   25.238315] hda: cache flushes supported
[   25.238502]  hda: hda1 hda2 hda3 < hda5 > hda4
[   25.282387] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(33)
[   25.282406] Uniform CD-ROM driver Revision: 3.20
[   25.312457] hdd: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   25.848965] Attempting manual resume
[   25.848975] swsusp: Resume From Partition 3:5
[   25.848978] PM: Checking swsusp image.
[   25.867138] PM: Resume from disk failed.
[   25.913733] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.913746] EXT3-fs: write access will be enabled during recovery.
[   29.963542] kjournald starting.  Commit interval 5 seconds
[   29.963602] EXT3-fs: recovery complete.
[   29.964132] EXT3-fs: mounted filesystem with ordered data mode.
[   37.183614] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.848837] NET: Registered protocol family 17
[   40.931268] Linux agpgart interface v0.102 (c) Dave Jones
[   40.939791] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.944193] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.019542] agpgart: Detected VIA P4M266x/P4N266 chipset
[   41.025689] agpgart: AGP aperture is 64M @ 0xe0000000
[   41.281937] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xec00, speed 1011kHz
[   42.190262] irda_init()
[   42.190319] NET: Registered protocol family 23
[   42.626618] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   42.626690] usbcore: registered new interface driver usblp
[   42.626699] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   43.012389] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 18
[   43.243858] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   43.384443] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   43.388929] parport_pc 00:03: reported by Plug and Play ACPI
[   43.389055] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   43.392418] input: PC Speaker as /class/input/input3
[   45.128362] lp0: using parport0 (interrupt-driven).
[   45.264974] Adding 859436k swap on /dev/hda5.  Priority:-1 extents:1 across:859436k
[   45.809797] EXT3 FS on hda4, internal journal
[   65.579312] kjournald starting.  Commit interval 5 seconds
[   65.579572] EXT3 FS on hda2, internal journal
[   65.579587] EXT3-fs: mounted filesystem with ordered data mode.
[   67.088712] No dock devices found.
[   67.374450] input: Power Button (FF) as /class/input/input4
[   67.387414] ACPI: Power Button (FF) [PWRF]
[   67.429078] input: Power Button (CM) as /class/input/input5
[   67.429788] ACPI: Power Button (CM) [PWRB]
[   71.423719] ppdev: user-space parallel port driver
[   72.041261] audit(1193004908.826:3):  type=1502 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4818 profile="/usr/sbin/cupsd"
[   72.193424] apm: BIOS not found.
[   74.284702] [drm] Initialized drm 1.1.0 20060810
[   74.334131] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   74.342067] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   74.343580] mtrr: base(0xd2000000) is not aligned on a size(0x5000000) boundary
[   74.345997] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   74.346689] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   74.347349] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   74.547583] Failure registering capabilities with primary security module.
[   74.875760] Bluetooth: Core ver 2.11
[   74.876012] NET: Registered protocol family 31
[   74.876019] Bluetooth: HCI device and connection manager initialized
[   74.876026] Bluetooth: HCI socket layer initialized
[   74.948530] Bluetooth: L2CAP ver 2.8
[   74.948541] Bluetooth: L2CAP socket layer initialized
[   74.999089] Bluetooth: RFCOMM socket layer initialized
[   74.999281] Bluetooth: RFCOMM TTY layer initialized
[   74.999288] Bluetooth: RFCOMM ver 1.8
[17756.440456] usb 4-6: new high speed USB device using ehci_hcd and address 3
[17756.576818] usb 4-6: configuration #1 chosen from 1 choice
[17756.927406] usbcore: registered new interface driver libusual
[17757.163857] Initializing USB Mass Storage driver...
[17757.166401] scsi0 : SCSI emulation for USB Mass Storage devices
[17757.172681] usb-storage: device found at 3
[17757.172698] usb-storage: waiting for device to settle before scanning
[17757.172831] usbcore: registered new interface driver usb-storage
[17757.172838] USB Mass Storage support registered.
[17762.163248] usb-storage: device scan complete
[17762.167161] scsi 0:0:0:0: Direct-Access     UDISK    PDU01_512 69A2.0 0.00 PQ: 0 ANSI: 2
[17762.273676] sd 0:0:0:0: [sda] 1007616 512-byte hardware sectors (516 MB)
[17762.275163] sd 0:0:0:0: [sda] Write Protect is off
[17762.275180] sd 0:0:0:0: [sda] Mode Sense: 00 00 00 00
[17762.275185] sd 0:0:0:0: [sda] Assuming drive cache: write through
[17762.278952] sd 0:0:0:0: [sda] 1007616 512-byte hardware sectors (516 MB)
[17762.282944] sd 0:0:0:0: [sda] Write Protect is off
[17762.282964] sd 0:0:0:0: [sda] Mode Sense: 00 00 00 00
[17762.282968] sd 0:0:0:0: [sda] Assuming drive cache: write through
[17762.282984]  sda:
[17762.479267] sd 0:0:0:0: [sda] Attached SCSI removable disk
[17762.578182] sd 0:0:0:0: Attached scsi generic sg0 type 0
[38080.356059] usb 1-2: USB disconnect, address 2
[38080.363668] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[38547.847460] usb 1-2: new full speed USB device using uhci_hcd and address 3
[38548.029355] usb 1-2: configuration #1 chosen from 1 choice
[38548.039381] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[38706.435789] ppdev0: registered pardevice
[38706.504263] ppdev0: unregistered pardevice
[38709.216579] ppdev0: registered pardevice
[38709.262129] ppdev0: unregistered pardevice
[38709.504141] audit(1193043609.531:4):  type=1502 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=22515 profile="/usr/sbin/cupsd"
[38709.638273] audit(1193043610.031:5):  type=1502 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=22520 profile="/usr/sbin/cupsd"
[38709.639630] audit(1193043610.031:6):  type=1502 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=22520 profile="/usr/sbin/cupsd"
[38710.922728] audit(1193043611.031:7):  type=1502 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=22525 profile="/usr/sbin/cupsd"
[38710.924136] audit(1193043611.031:8):  type=1502 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=22525 profile="/usr/sbin/cupsd"
[39406.260462] usb 1-2: USB disconnect, address 3
[39406.261033] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[39408.496734] usb 1-2: new full speed USB device using uhci_hcd and address 4
[39408.675149] usb 1-2: configuration #1 chosen from 1 choice
[39408.684803] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005

---

### Post by amelyst on 2007-10-22
This looks completely different from the behaviour on my machine. I have no idea why you have this ominous link in the /dev/usb directory instead of a real device node.

The base problem in your case is seemingly the lack of a device node, thus preventing any print jobs getting transferred to the printer. The printer is correctly recognized, as can be seen from the dmesg output. The system responsible for creating the correct device nodes is udev. Seems like something is really messed up here.

Having no real knowlegde about the inner workings of the udev system and its interdependencies, I regret to say that I can't be of any serious help to you any further from here on, sorry for that.

regards
martin

---

