---
title: "Installation does not detect my network. Possible IRQ conflicts?"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by godrox on 2007-01-03
I have an old computer someone gave me that was running Windows 98 (866 MHz, 128 MB), which I promptly removed to install Ubuntu. Because of it's low memory, I'm using the text installation from the alternate 6.10 CD, but after trying to detect network devices, it stops and says, "Configure the network - No network interfaces found." I can continue with the installation, but of course there's no network connection after Ubuntu finishes installing either. (The Xubuntu alternate installation gives the same error message.)

I've tried three different PCI network cards (Belkin, D-link, and Network Everywhere) all with the same results. I've tried each card in different PCI slots, as well. Both the NIC and the router light up appropriately, but for some reason the Ubuntu still misses it.

Now, for what it's worth, I don't know much about IRQs, but I noticed during the BIOS boot screen that both the network adapter and the VGA were both set at IRQ 11. I tried different IRQ settings in the BIOS (not really knowing what I was doing), but it made no difference.

Can anyone point me in the right direction for solving this issue?

---

### Post by lloyd_b on 2007-01-03
The questions is: is the machine not detecting the card, or just not loading a driver for it.

Note: I'd avoid the Belkin card - I've seen tons of messages about people having problems with their hardware under Linux.  I'd suggest the D-Link as a test (I never heard of the third brand before, so no telling if there's driver support for it).

Install the D-Link card (no need to reinstall) and boot up the machine.  Once booted, open a terminal window, and run the command "lspci", which will list all detected devices on the PCI bus.  See if the D-Link card appears in the list.

If it shows up, please post that section of the output and we can start sorting things out from there.  Also, please identify whether the card is wired or wireless (it makes a heck of a lot of difference!).

Ideally, PCI devices should have no trouble sharing IRQ's - it's inherent in the PCI specs.  When PCI first came out there were a lot of drivers that still had IRQ issues, but I haven't seen one in many years (The last time I saw in IRQ conflict, it was on a P2-300).

Lloyd B.

---

### Post by godrox on 2007-01-03
Thanks for the reply! I installed Ubuntu with the D-link wired NIC and then ran lspci. It returned the following:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)

```

Now what?

---

### Post by godrox on 2007-01-04
Been searching around here trying to find some leads and came across this when I do dmesg:

```
[17179595.580000] 8139too Fast Ethernet driver 0.9.27
[17179595.580000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179595.580000] PCI: setting IRQ 10 as level-triggered
[17179595.580000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179595.580000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17179595.580000] Trying to free nonexistent resource <0000de00-0000deff>
[17179595.580000] Trying to free nonexistent resource <efffff00-efffffff>
[17179595.580000] 8139too: probe of 0000:00:0a.0 failed with error -16

```

Not really sure what that error means yet, though.

---

### Post by lloyd_b on 2007-01-04
> Been searching around here trying to find some leads and came across this when I do dmesg:

```
[17179595.580000] 8139too Fast Ethernet driver 0.9.27 
[17179595.580000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10 
[17179595.580000] PCI: setting IRQ 10 as level-triggered 
[17179595.580000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10 
[17179595.580000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0 [17179595.580000] Trying to free nonexistent resource <0000de00-0000deff> [17179595.580000] Trying to free nonexistent resource <efffff00-efffffff> 
[17179595.580000] 8139too: probe of 0000:00:0a.0 failed with error -16

```
Not really sure what that error means yet, though.

Ouch.  Error -16 = "EBUSY" - when it tried to allocate an I/O range for the card, it seems to be trying to grab an I/O range that's already in use.

Could you run the following and post the results?
cat /proc/ioports

This will provide a listing of all I/O ports in use on the system, and provide some info as to what is using those ports.

It looks like you DO have a conflict - not IRQ, but in I/O space.  Now for the bad news - I've never heard of this happening before...

I'm not sure where to go from here.  Take a look at the BIOS settings and see if there's any configuration for I/O ports (on the page where you saw the IRQ settings).  There may be something there that will resolve the conflict.

Sorry I can't be more help.  Hopefully somebody else will wander by with some more specific suggestions...

Lloyd B.

---

### Post by godrox on 2007-01-04
cat /proc/ioports returned the following:

```
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : ide1
01f0-01f7 : ide0
02f8-02ff : serial
0376-0376 : ide1
0378-037a : parport0
037b-037f : parport0
03c0-03df : vga+
03f6-03f6 : ide0
03f8-03ff : serial
0778-077a : parport0
0cf8-0cff : PCI conf1
5000-5003 : ACPI PM1a_EVT_BLK
5004-5005 : ACPI PM1a_CNT_BLK
5008-500b : ACPI PM_TMR
5010-5015 : ACPI CPU throttle
5020-5023 : ACPI GPE0_BLK
50e0-50ef : amd756_smbus
b000-cfff : PCI Bus #01
  c800-c8ff : 0000:01:05.0
dc00-dc03 : 0000:00:00.0
  dc00-dc00 : ACPI PM2_CNT_BLK
de00-deff : 0000:00:0a.0
  de00-de03 : motherboard
    de00-de03 : pnp 00:01
f000-f00f : 0000:00:07.1
  f000-f007 : ide0
  f008-f00f : ide1

```

I'll look around in the BIOS. Apparently that's where the problem lies, not with my network adapter, right? I'll check to see if there's an updated BIOS available, too, that maybe I can flash to correct the issue.

---

### Post by godrox on 2007-01-04
The latest BIOS version was already loaded, but I re-flashed it anyway just to make sure. The ioports list remained the same.

I looked around in the BIOS for something about I/O settings, but didn't see anything. Only IRQ and PnP/PCI settings. Nothing I saw looked relevant, but I still tried making some changes with no reportable results.

Thanks for your help and your time! I appreciate it.

---

### Post by lloyd_b on 2007-01-04
Now that's interesting:

```
de00-deff : 0000:00:0a.0
  de00-de03 : motherboard
    de00-de03 : pnp
```

It shows de00-deff allocated to 0a.0, which is the network card, but the driver fails with EBUSY, which means that it can't access that range.  Weird.

I wonder - could this be some sort of timing error, where the driver is attempting to initialize the card too early in the boot process?

Experiment:  Boot the machine up.  At a command prompt:

```
sudo rmmod 8139too
sudo modprobe 8319too
```

This should remove the driver (assuming it's installed), and then re-install it.  Then look at dmesg and see if it shows that same error condition.  If not, then run "sudo /etc/init.d/networking restart" and see if the network comes up.

You mention having two other cards available - plug one of them in (try the Belkin last, please), and repeat the "lspci" scan and check dmesg (note: you do NOT have to re-install Ubuntu for this to work - if the new card is supported, then it should be recognized at boot).  I'm curious if this is the only card that gets this weird error, or if it's common to several cards (the former indicates a card/driver issue, while the latter indicates a chipset/driver issue).

Other than that, I'm out of ideas.

Lloyd B.

---

### Post by godrox on 2007-01-04
Thanks so much for your help, lloyd_b! I just finished installing openSUSE and the network is fine (I'm writing this post from it), so I'm guessing it must be a software issue now that I've verified that the card works. I'll try to install Ubuntu again now and try the steps you provided.

---

### Post by godrox on 2007-01-04
**dmesg with the D-link NIC:**
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000007ff0000 - 0000000007ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000007ff8000 - 0000000008000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 127MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 32752
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 28656 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fabb0
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x07ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000011 MSFT 0x00000097) @ 0x07ff0030
[17179569.184000] ACPI: DSDT (v001 AMD75X IRONGATE 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01109000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[17179569.184000] Detected 858.641 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.008000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.008000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.020000] Memory: 120308k/131008k available (1910k kernel code, 10160k reserved, 1070k data, 308k init, 0k highmem)
[17179573.020000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.100000] Calibrating delay using timer specific routine.. 1719.14 BogoMIPS (lpj=3438287)
[17179573.100000] Security Framework v1.0.0 initialized
[17179573.100000] SELinux:  Disabled at boot.
[17179573.100000] Mount-cache hash table entries: 512
[17179573.100000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179573.100000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179573.100000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.100000] CPU: L2 Cache: 256K (64 bytes/line)
[17179573.100000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179573.100000] Checking 'hlt' instruction... OK.
[17179573.116000] SMP alternatives: switching to UP code
[17179573.116000] Freeing SMP alternatives: 16k freed
[17179573.116000] checking if image is initramfs... it is
[17179574.200000] Freeing initrd memory: 5254k freed
[17179574.200000] ACPI: Core revision 20060707
[17179574.208000] ACPI: Looking for DSDT ... not found!
[17179574.212000] ACPI: setting ELCR to 0200 (from 1c00)
[17179574.212000] CPU0: AMD Athlon(tm) Processor stepping 02
[17179574.212000] SMP motherboard not detected.
[17179574.212000] Local APIC not detected. Using dummy APIC emulation.
[17179574.212000] Brought up 1 CPUs
[17179574.212000] migration_cost=0
[17179574.212000] NET: Registered protocol family 16
[17179574.212000] EISA bus registered
[17179574.212000] ACPI: bus type pci registered
[17179574.228000] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[17179574.228000] PCI: Using configuration type 1
[17179574.228000] Setting up standard PCI resources
[17179574.244000] ACPI: Interpreter enabled
[17179574.244000] ACPI: Using PIC for interrupt routing
[17179574.244000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.244000] PCI: Probing PCI hardware (bus 00)
[17179574.248000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179574.248000] Boot video device is 0000:01:05.0
[17179574.248000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.256000] ACPI: Power Resource [URP1] (off)
[17179574.256000] ACPI: Power Resource [URP2] (off)
[17179574.256000] ACPI: Power Resource [FDDP] (off)
[17179574.256000] ACPI: Power Resource [LPTP] (off)
[17179574.256000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.256000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179574.256000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179574.256000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[17179574.256000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.256000] pnp: PnP ACPI init
[17179574.264000] pnp: PnP ACPI: found 11 devices
[17179574.264000] PnPBIOS: Disabled by ACPI PNP
[17179574.264000] PCI: Using ACPI for IRQ routing
[17179574.264000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.264000] pnp: 00:01: ioport range 0xde00-0xde03 has been reserved
[17179574.264000] PCI: Bridge: 0000:00:01.0
[17179574.264000]   IO window: b000-cfff
[17179574.264000]   MEM window: ede00000-efefffff
[17179574.264000]   PREFETCH window: e5c00000-e5cfffff
[17179574.264000] NET: Registered protocol family 2
[17179574.292000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[17179574.292000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.292000] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[17179574.292000] TCP: Hash tables configured (established 4096 bind 2048)
[17179574.292000] TCP reno registered
[17179574.292000] audit: initializing netlink socket (disabled)
[17179574.292000] audit(1167959769.292:1): initialized
[17179574.292000] VFS: Disk quotas dquot_6.5.1
[17179574.292000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.292000] Initializing Cryptographic API
[17179574.292000] io scheduler noop registered
[17179574.292000] io scheduler anticipatory registered
[17179574.292000] io scheduler deadline registered
[17179574.292000] io scheduler cfq registered (default)
[17179574.292000] isapnp: Scanning for PnP cards...
[17179574.648000] isapnp: No Plug & Play device found
[17179574.696000] Real Time Clock Driver v1.12ac
[17179574.696000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.696000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.696000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.696000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.696000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.696000] mice: PS/2 mouse device common for all mice
[17179574.700000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.700000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.700000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.700000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.700000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.700000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.704000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.704000] EISA: Probing bus 0 at eisa.0
[17179574.704000] Cannot allocate resource for EISA slot 5
[17179574.704000] EISA: Detected 0 cards.
[17179574.704000] TCP bic registered
[17179574.704000] NET: Registered protocol family 1
[17179574.704000] NET: Registered protocol family 8
[17179574.704000] NET: Registered protocol family 20
[17179574.704000] Using IPI No-Shortcut mode
[17179574.704000] ACPI: (supports S0 S1 S4 S5)
[17179574.704000] Freeing unused kernel memory: 308k freed
[17179575.016000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.080000] Capability LSM initialized
[17179576.656000] ACPI: Thermal Zone [THRM] (30 C)
[17179577.924000] AMD7409: IDE controller at PCI slot 0000:00:07.1
[17179577.924000] AMD7409: chipset revision 7
[17179577.924000] AMD7409: not 100% native mode: will probe irqs later
[17179577.924000] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[17179577.924000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.924000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179577.924000] Probing IDE interface ide0...
[17179578.212000] hda: WDC WD200BB-00DEA0, ATA DISK drive
[17179578.548000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.548000] Probing IDE interface ide1...
[17179579.284000] hdc: CRD-8322B, ATAPI CD/DVD-ROM drive
[17179579.956000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.976000] hda: max request size: 128KiB
[17179580.104000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(66)
[17179580.104000] hda: cache flushes not supported
[17179580.104000]  hda: hda1 hda2 < hda5 >
[17179580.156000] hdc: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[17179580.156000] Uniform CD-ROM driver Revision: 3.20
[17179580.492000] usbcore: registered new driver usbfs
[17179580.492000] usbcore: registered new driver hub
[17179580.496000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179580.496000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179580.496000] PCI: setting IRQ 12 as level-triggered
[17179580.496000] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179580.496000] ohci_hcd 0000:00:07.4: OHCI Host Controller
[17179580.496000] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[17179580.496000] ohci_hcd 0000:00:07.4: irq 12, io mem 0xefffe000
[17179580.552000] usb usb1: configuration #1 chosen from 1 choice
[17179580.552000] hub 1-0:1.0: USB hub found
[17179580.552000] hub 1-0:1.0: 4 ports detected
[17179580.936000] Attempting manual resume
[17179580.960000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179581.172000] usb 1-1: configuration #1 chosen from 1 choice
[17179581.192000] usbcore: registered new driver hiddev
[17179581.204000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179581.204000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.4-1
[17179581.204000] usbcore: registered new driver usbhid
[17179581.204000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179581.600000] kjournald starting.  Commit interval 5 seconds
[17179581.600000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.900000] Floppy drive(s): fd0 is 1.44M
[17179597.916000] FDC 0 is a post-1991 82077
[17179597.996000] 8139too Fast Ethernet driver 0.9.27
[17179597.996000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179597.996000] PCI: setting IRQ 10 as level-triggered
[17179597.996000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179597.996000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17179597.996000] Trying to free nonexistent resource <0000de00-0000deff>
[17179597.996000] Trying to free nonexistent resource <efffff00-efffffff>
[17179597.996000] 8139too: probe of 0000:00:0a.0 failed with error -16
[17179598.084000] input: PC Speaker as /class/input/input2
[17179598.100000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.104000] agpgart: Detected AMD Irongate chipset
[17179598.116000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179598.232000] parport: PnPBIOS parport detected.
[17179598.232000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179598.288000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.296000] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[17179598.296000] shpchp: shpc_init: cannot reserve MMIO region
[17179598.296000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.868000] ts: Compaq touchscreen protocol output
[17179599.384000] lp0: using parport0 (interrupt-driven).
[17179599.452000] Adding 369452k swap on /dev/disk/by-uuid/7d8a1020-3104-49e9-bb5e-4512b7c715ce.  Priority:-1 extents:1 across:369452k
[17179599.540000] EXT3 FS on hda1, internal journal
[17179601.940000] ACPI: Power Button (FF) [PWRF]
[17179601.940000] ACPI: Sleep Button (FF) [SLPF]
[17179601.940000] ACPI: Power Button (CM) [PWRB]
[17179602.160000] ibm_acpi: ec object not found
[17179602.216000] pcc_acpi: loading...
[17179602.880000] powernow: No powernow capabilities detected
[17179605.568000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.568000] apm: overridden by ACPI.
[17179612.224000] Bluetooth: Core ver 2.8
[17179612.224000] NET: Registered protocol family 31
[17179612.224000] Bluetooth: HCI device and connection manager initialized
[17179612.224000] Bluetooth: HCI socket layer initialized
[17179612.260000] Bluetooth: L2CAP ver 2.8
[17179612.260000] Bluetooth: L2CAP socket layer initialized
[17179612.284000] Bluetooth: RFCOMM socket layer initialized
[17179612.284000] Bluetooth: RFCOMM TTY layer initialized
[17179612.284000] Bluetooth: RFCOMM ver 1.7
[17180669.180000] NET: Registered protocol family 10
[17180669.180000] lo: Disabled Privacy Extensions
[17180669.180000] IPv6 over IPv4 tunneling driver
[17181313.608000] 8139too Fast Ethernet driver 0.9.27
[17181313.608000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17181313.608000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17181313.608000] Trying to free nonexistent resource <0000de00-0000deff>
[17181313.608000] Trying to free nonexistent resource <efffff00-efffffff>
[17181313.608000] 8139too: probe of 0000:00:0a.0 failed with error -16

```

---

### Post by godrox on 2007-01-04
**lspci with the Network Everywhere NIC**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:05.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)

```

**dmesg with the Network Everywhere NIC**
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000007ff0000 - 0000000007ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000007ff8000 - 0000000008000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 127MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 32752
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 28656 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fabb0
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x07ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000011 MSFT 0x00000097) @ 0x07ff0030
[17179569.184000] ACPI: DSDT (v001 AMD75X IRONGATE 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01109000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[17179569.184000] Detected 858.616 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.748000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.748000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.760000] Memory: 120308k/131008k available (1910k kernel code, 10160k reserved, 1070k data, 308k init, 0k highmem)
[17179572.760000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.840000] Calibrating delay using timer specific routine.. 1719.12 BogoMIPS (lpj=3438247)
[17179572.840000] Security Framework v1.0.0 initialized
[17179572.840000] SELinux:  Disabled at boot.
[17179572.840000] Mount-cache hash table entries: 512
[17179572.840000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.840000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.840000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.840000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.840000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.840000] Checking 'hlt' instruction... OK.
[17179572.856000] SMP alternatives: switching to UP code
[17179572.856000] Freeing SMP alternatives: 16k freed
[17179572.856000] checking if image is initramfs... it is
[17179573.940000] Freeing initrd memory: 5254k freed
[17179573.940000] ACPI: Core revision 20060707
[17179573.948000] ACPI: Looking for DSDT ... not found!
[17179573.952000] ACPI: setting ELCR to 0200 (from 1c00)
[17179573.952000] CPU0: AMD Athlon(tm) Processor stepping 02
[17179573.952000] SMP motherboard not detected.
[17179573.952000] Local APIC not detected. Using dummy APIC emulation.
[17179573.952000] Brought up 1 CPUs
[17179573.952000] migration_cost=0
[17179573.952000] NET: Registered protocol family 16
[17179573.952000] EISA bus registered
[17179573.952000] ACPI: bus type pci registered
[17179573.968000] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[17179573.968000] PCI: Using configuration type 1
[17179573.968000] Setting up standard PCI resources
[17179573.984000] ACPI: Interpreter enabled
[17179573.984000] ACPI: Using PIC for interrupt routing
[17179573.984000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.984000] PCI: Probing PCI hardware (bus 00)
[17179573.988000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179573.988000] Boot video device is 0000:01:05.0
[17179573.988000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.996000] ACPI: Power Resource [URP1] (off)
[17179573.996000] ACPI: Power Resource [URP2] (off)
[17179573.996000] ACPI: Power Resource [FDDP] (off)
[17179573.996000] ACPI: Power Resource [LPTP] (off)
[17179573.996000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.996000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.996000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179573.996000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[17179573.996000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.996000] pnp: PnP ACPI init
[17179574.004000] pnp: PnP ACPI: found 11 devices
[17179574.004000] PnPBIOS: Disabled by ACPI PNP
[17179574.004000] PCI: Using ACPI for IRQ routing
[17179574.004000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.004000] pnp: 00:01: ioport range 0xde00-0xde03 has been reserved
[17179574.004000] PCI: Bridge: 0000:00:01.0
[17179574.004000]   IO window: b000-cfff
[17179574.004000]   MEM window: ede00000-efefffff
[17179574.004000]   PREFETCH window: e5c00000-e5cfffff
[17179574.004000] NET: Registered protocol family 2
[17179574.032000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[17179574.032000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.032000] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[17179574.032000] TCP: Hash tables configured (established 4096 bind 2048)
[17179574.032000] TCP reno registered
[17179574.032000] audit: initializing netlink socket (disabled)
[17179574.032000] audit(1167962570.032:1): initialized
[17179574.032000] VFS: Disk quotas dquot_6.5.1
[17179574.032000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.032000] Initializing Cryptographic API
[17179574.032000] io scheduler noop registered
[17179574.032000] io scheduler anticipatory registered
[17179574.032000] io scheduler deadline registered
[17179574.032000] io scheduler cfq registered (default)
[17179574.032000] isapnp: Scanning for PnP cards...
[17179574.388000] isapnp: No Plug & Play device found
[17179574.436000] Real Time Clock Driver v1.12ac
[17179574.436000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.436000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.436000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.440000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.440000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.440000] mice: PS/2 mouse device common for all mice
[17179574.440000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.440000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.440000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.440000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.440000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.444000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.444000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.444000] EISA: Probing bus 0 at eisa.0
[17179574.444000] Cannot allocate resource for EISA slot 5
[17179574.444000] EISA: Detected 0 cards.
[17179574.444000] TCP bic registered
[17179574.444000] NET: Registered protocol family 1
[17179574.444000] NET: Registered protocol family 8
[17179574.444000] NET: Registered protocol family 20
[17179574.444000] Using IPI No-Shortcut mode
[17179574.444000] ACPI: (supports S0 S1 S4 S5)
[17179574.448000] Freeing unused kernel memory: 308k freed
[17179574.756000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.820000] Capability LSM initialized
[17179576.396000] ACPI: Thermal Zone [THRM] (30 C)
[17179577.700000] AMD7409: IDE controller at PCI slot 0000:00:07.1
[17179577.700000] AMD7409: chipset revision 7
[17179577.700000] AMD7409: not 100% native mode: will probe irqs later
[17179577.700000] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[17179577.700000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.700000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179577.700000] Probing IDE interface ide0...
[17179577.992000] hda: WDC WD200BB-00DEA0, ATA DISK drive
[17179578.328000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.328000] Probing IDE interface ide1...
[17179579.064000] hdc: CRD-8322B, ATAPI CD/DVD-ROM drive
[17179579.736000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.756000] hda: max request size: 128KiB
[17179579.776000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(66)
[17179579.776000] hda: cache flushes not supported
[17179579.776000]  hda: hda1 hda2 < hda5 >
[17179579.860000] hdc: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[17179579.860000] Uniform CD-ROM driver Revision: 3.20
[17179580.268000] usbcore: registered new driver usbfs
[17179580.268000] usbcore: registered new driver hub
[17179580.272000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179580.276000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179580.276000] PCI: setting IRQ 12 as level-triggered
[17179580.276000] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179580.276000] ohci_hcd 0000:00:07.4: OHCI Host Controller
[17179580.276000] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[17179580.276000] ohci_hcd 0000:00:07.4: irq 12, io mem 0xefffe000
[17179580.332000] usb usb1: configuration #1 chosen from 1 choice
[17179580.332000] hub 1-0:1.0: USB hub found
[17179580.332000] hub 1-0:1.0: 4 ports detected
[17179580.740000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179580.908000] Attempting manual resume
[17179580.952000] usb 1-1: configuration #1 chosen from 1 choice
[17179580.972000] usbcore: registered new driver hiddev
[17179580.984000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179580.984000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.4-1
[17179580.984000] usbcore: registered new driver usbhid
[17179580.984000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179581.676000] kjournald starting.  Commit interval 5 seconds
[17179581.676000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.416000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.416000] agpgart: Detected AMD Irongate chipset
[17179597.428000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179597.740000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.752000] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[17179597.752000] shpchp: shpc_init: cannot reserve MMIO region
[17179597.752000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.884000] Linux Tulip driver version 1.1.14 (May 6, 2006)
[17179597.888000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179597.888000] PCI: setting IRQ 10 as level-triggered
[17179597.888000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179597.888000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17179597.912000] input: PC Speaker as /class/input/input2
[17179598.584000] parport: PnPBIOS parport detected.
[17179598.584000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179598.612000] Floppy drive(s): fd0 is 1.44M
[17179598.628000] FDC 0 is a post-1991 82077
[17179599.032000] ts: Compaq touchscreen protocol output
[17179599.564000] lp0: using parport0 (interrupt-driven).
[17179599.636000] Adding 369452k swap on /dev/disk/by-uuid/7d8a1020-3104-49e9-bb5e-4512b7c715ce.  Priority:-1 extents:1 across:369452k
[17179599.720000] EXT3 FS on hda1, internal journal
[17179602.196000] ACPI: Power Button (FF) [PWRF]
[17179602.196000] ACPI: Sleep Button (FF) [SLPF]
[17179602.196000] ACPI: Power Button (CM) [PWRB]
[17179602.428000] ibm_acpi: ec object not found
[17179602.480000] pcc_acpi: loading...
[17179603.144000] powernow: No powernow capabilities detected
[17179605.832000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.832000] apm: overridden by ACPI.
[17179612.624000] Bluetooth: Core ver 2.8
[17179612.624000] NET: Registered protocol family 31
[17179612.624000] Bluetooth: HCI device and connection manager initialized
[17179612.624000] Bluetooth: HCI socket layer initialized
[17179612.656000] Bluetooth: L2CAP ver 2.8
[17179612.656000] Bluetooth: L2CAP socket layer initialized
[17179612.684000] Bluetooth: RFCOMM socket layer initialized
[17179612.684000] Bluetooth: RFCOMM TTY layer initialized
[17179612.684000] Bluetooth: RFCOMM ver 1.7
[17179646.772000] NET: Registered protocol family 10
[17179646.776000] lo: Disabled Privacy Extensions
[17179646.776000] IPv6 over IPv4 tunneling driver

```

**lspci with the Belkin NIC**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)

```

**dmesg with the Belkin NIC**
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000007ff0000 - 0000000007ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000007ff8000 - 0000000008000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 127MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 32752
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 28656 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fabb0
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x07ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000011 MSFT 0x00000097) @ 0x07ff0030
[17179569.184000] ACPI: DSDT (v001 AMD75X IRONGATE 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01109000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[17179569.184000] Detected 858.544 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.880000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.880000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.892000] Memory: 120308k/131008k available (1910k kernel code, 10160k reserved, 1070k data, 308k init, 0k highmem)
[17179572.892000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.972000] Calibrating delay using timer specific routine.. 1719.13 BogoMIPS (lpj=3438277)
[17179572.972000] Security Framework v1.0.0 initialized
[17179572.972000] SELinux:  Disabled at boot.
[17179572.972000] Mount-cache hash table entries: 512
[17179572.972000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.972000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.972000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.972000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.972000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.972000] Checking 'hlt' instruction... OK.
[17179572.988000] SMP alternatives: switching to UP code
[17179572.988000] Freeing SMP alternatives: 16k freed
[17179572.988000] checking if image is initramfs... it is
[17179574.072000] Freeing initrd memory: 5254k freed
[17179574.072000] ACPI: Core revision 20060707
[17179574.080000] ACPI: Looking for DSDT ... not found!
[17179574.084000] ACPI: setting ELCR to 0200 (from 1c00)
[17179574.084000] CPU0: AMD Athlon(tm) Processor stepping 02
[17179574.084000] SMP motherboard not detected.
[17179574.084000] Local APIC not detected. Using dummy APIC emulation.
[17179574.084000] Brought up 1 CPUs
[17179574.084000] migration_cost=0
[17179574.084000] NET: Registered protocol family 16
[17179574.084000] EISA bus registered
[17179574.084000] ACPI: bus type pci registered
[17179574.100000] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[17179574.100000] PCI: Using configuration type 1
[17179574.100000] Setting up standard PCI resources
[17179574.116000] ACPI: Interpreter enabled
[17179574.116000] ACPI: Using PIC for interrupt routing
[17179574.116000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.116000] PCI: Probing PCI hardware (bus 00)
[17179574.120000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179574.120000] Boot video device is 0000:01:05.0
[17179574.120000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.128000] ACPI: Power Resource [URP1] (off)
[17179574.128000] ACPI: Power Resource [URP2] (off)
[17179574.128000] ACPI: Power Resource [FDDP] (off)
[17179574.128000] ACPI: Power Resource [LPTP] (off)
[17179574.128000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.128000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179574.128000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179574.128000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[17179574.128000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.128000] pnp: PnP ACPI init
[17179574.136000] pnp: PnP ACPI: found 11 devices
[17179574.136000] PnPBIOS: Disabled by ACPI PNP
[17179574.136000] PCI: Using ACPI for IRQ routing
[17179574.136000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.136000] pnp: 00:01: ioport range 0xde00-0xde03 has been reserved
[17179574.136000] PCI: Bridge: 0000:00:01.0
[17179574.136000]   IO window: b000-cfff
[17179574.136000]   MEM window: ede00000-efefffff
[17179574.136000]   PREFETCH window: e5c00000-e5cfffff
[17179574.136000] NET: Registered protocol family 2
[17179574.164000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[17179574.164000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.164000] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[17179574.164000] TCP: Hash tables configured (established 4096 bind 2048)
[17179574.164000] TCP reno registered
[17179574.164000] audit: initializing netlink socket (disabled)
[17179574.164000] audit(1167962089.164:1): initialized
[17179574.164000] VFS: Disk quotas dquot_6.5.1
[17179574.164000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.164000] Initializing Cryptographic API
[17179574.164000] io scheduler noop registered
[17179574.164000] io scheduler anticipatory registered
[17179574.164000] io scheduler deadline registered
[17179574.164000] io scheduler cfq registered (default)
[17179574.164000] isapnp: Scanning for PnP cards...
[17179574.520000] isapnp: No Plug & Play device found
[17179574.568000] Real Time Clock Driver v1.12ac
[17179574.568000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.568000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.568000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.572000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.572000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.572000] mice: PS/2 mouse device common for all mice
[17179574.572000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.572000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.572000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.572000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.572000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.576000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.576000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.576000] EISA: Probing bus 0 at eisa.0
[17179574.576000] Cannot allocate resource for EISA slot 5
[17179574.576000] EISA: Detected 0 cards.
[17179574.576000] TCP bic registered
[17179574.576000] NET: Registered protocol family 1
[17179574.576000] NET: Registered protocol family 8
[17179574.576000] NET: Registered protocol family 20
[17179574.576000] Using IPI No-Shortcut mode
[17179574.576000] ACPI: (supports S0 S1 S4 S5)
[17179574.580000] Freeing unused kernel memory: 308k freed
[17179574.888000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.948000] Capability LSM initialized
[17179576.520000] ACPI: Thermal Zone [THRM] (30 C)
[17179577.808000] AMD7409: IDE controller at PCI slot 0000:00:07.1
[17179577.808000] AMD7409: chipset revision 7
[17179577.808000] AMD7409: not 100% native mode: will probe irqs later
[17179577.808000] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[17179577.808000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.808000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179577.808000] Probing IDE interface ide0...
[17179578.100000] hda: WDC WD200BB-00DEA0, ATA DISK drive
[17179578.436000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.436000] Probing IDE interface ide1...
[17179579.172000] hdc: CRD-8322B, ATAPI CD/DVD-ROM drive
[17179579.844000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.864000] hda: max request size: 128KiB
[17179579.884000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(66)
[17179579.884000] hda: cache flushes not supported
[17179579.884000]  hda: hda1 hda2 < hda5 >
[17179579.960000] hdc: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[17179579.960000] Uniform CD-ROM driver Revision: 3.20
[17179580.280000] usbcore: registered new driver usbfs
[17179580.284000] usbcore: registered new driver hub
[17179580.288000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179580.288000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179580.288000] PCI: setting IRQ 12 as level-triggered
[17179580.288000] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179580.288000] ohci_hcd 0000:00:07.4: OHCI Host Controller
[17179580.292000] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[17179580.292000] ohci_hcd 0000:00:07.4: irq 12, io mem 0xefffe000
[17179580.348000] usb usb1: configuration #1 chosen from 1 choice
[17179580.348000] hub 1-0:1.0: USB hub found
[17179580.348000] hub 1-0:1.0: 4 ports detected
[17179580.728000] Attempting manual resume
[17179580.756000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179580.968000] usb 1-1: configuration #1 chosen from 1 choice
[17179580.988000] usbcore: registered new driver hiddev
[17179581.000000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179581.000000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.4-1
[17179581.000000] usbcore: registered new driver usbhid
[17179581.000000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179581.392000] kjournald starting.  Commit interval 5 seconds
[17179581.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.996000] Floppy drive(s): fd0 is 1.44M
[17179597.012000] FDC 0 is a post-1991 82077
[17179597.064000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.068000] agpgart: Detected AMD Irongate chipset
[17179597.080000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179597.504000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.508000] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[17179597.508000] shpchp: shpc_init: cannot reserve MMIO region
[17179597.508000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.160000] parport: PnPBIOS parport detected.
[17179598.160000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179598.216000] input: PC Speaker as /class/input/input2
[17179598.316000] 8139too Fast Ethernet driver 0.9.27
[17179598.316000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179598.316000] PCI: setting IRQ 10 as level-triggered
[17179598.316000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179598.316000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17179598.316000] Trying to free nonexistent resource <0000de00-0000deff>
[17179598.316000] Trying to free nonexistent resource <efffff00-efffffff>
[17179598.316000] 8139too: probe of 0000:00:0a.0 failed with error -16
[17179598.356000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179598.356000] 8139cp: pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179598.356000] 8139cp: Try the "8139too" driver instead.
[17179599.008000] ts: Compaq touchscreen protocol output
[17179599.520000] lp0: using parport0 (interrupt-driven).
[17179599.592000] Adding 369452k swap on /dev/disk/by-uuid/7d8a1020-3104-49e9-bb5e-4512b7c715ce.  Priority:-1 extents:1 across:369452k
[17179599.676000] EXT3 FS on hda1, internal journal
[17179602.136000] ACPI: Power Button (FF) [PWRF]
[17179602.136000] ACPI: Sleep Button (FF) [SLPF]
[17179602.136000] ACPI: Power Button (CM) [PWRB]
[17179602.364000] ibm_acpi: ec object not found
[17179602.424000] pcc_acpi: loading...
[17179603.084000] powernow: No powernow capabilities detected
[17179605.740000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.740000] apm: overridden by ACPI.
[17179612.540000] Bluetooth: Core ver 2.8
[17179612.540000] NET: Registered protocol family 31
[17179612.540000] Bluetooth: HCI device and connection manager initialized
[17179612.540000] Bluetooth: HCI socket layer initialized
[17179612.580000] Bluetooth: L2CAP ver 2.8
[17179612.580000] Bluetooth: L2CAP socket layer initialized
[17179612.604000] Bluetooth: RFCOMM socket layer initialized
[17179612.604000] Bluetooth: RFCOMM TTY layer initialized
[17179612.604000] Bluetooth: RFCOMM ver 1.7
[17179616.776000] NET: Registered protocol family 10
[17179616.776000] lo: Disabled Privacy Extensions
[17179616.776000] IPv6 over IPv4 tunneling driver

```

---

### Post by lloyd_b on 2007-01-05
It looks like the D-Link and the Belkin card both use the same Realtek chip (and driver), while the Network Everywhere card is a good old "Tulip" device.  Yet they all show exactly the same problem - that "error -16".

So there's a problem with the kernel's handling of that particular motherboard.  I did a couple of quick searches, but I couldn't find any references to issues involving that particular chipset (AMD 751 "Irongate").

You mentioned that you got SuSe to run without an issue.  Question: what kernel version is it using ("cat /proc/version" with SuSe running will give you this info).  With Ubuntu, you've got 2.6.17-10, and I'm wondering if the SuSe is an older/newer kernel.  Obviously, there's something different between SuSe and Ubuntu, and given the nature of the problem the issue pretty much has to be somewhere in the kernel.

Lloyd B.

---

### Post by godrox on 2007-01-05
Well, I erased openSUSE when I reinstalled Ubuntu, but a Google search indicates that it's running kernel version 2.6.18.2-34.

So am I pretty much doomed with trying to run Ubuntu on this hardware configuration? Purchasing a newer NIC apparently won't make a difference, will it?

---

### Post by lloyd_b on 2007-01-05
> Well, I erased openSUSE when I reinstalled Ubuntu, but a Google search indicates that it's running kernel version 2.6.18.2-34.

So am I pretty much doomed with trying to run Ubuntu on this hardware configuration? Purchasing a newer NIC apparently won't make a difference, will it?

You are correct in that another NIC won't make any difference - the issue is with how PCI on that machine allocates I/O ranges.  I doubt that ANY PCI ethernet card will work on that machine with the current kernel version.

However, USB *does* appear to  be working on that machine, and it's possible to get a USB ethernet device.

If it were my machine, I would download the kernel sources for a later kernel version, and build a custom kernel.  But then, I'm a professional programmer who has been building custom kernels since version 1.3.  Whether or not you should give that option a try depends on your experience level.

Lloyd B.

---

### Post by godrox on 2007-01-05
Yeah, USB works okay. I'm using a USB mouse and use my USB pen drive to transfer the dmesg output text and such to a computer with Internet access so I can post the text here. However, I got the computer for free and it's not really worth putting any money into buying a USB network adapter. I'm just fixing it up to give away to a charity that needs it. Since I hardly know what a kernel is in the first place, I guess I'll have to introduce them to openSUSE instead of Ubuntu. :(

What if I used an earlier version of Ubuntu, like 6.06 or even 5.10? Do they use kernels that would work?

Thanks for all your help, lloyd_b! I really appreciate your patience with helping me figure this out.

---

### Post by lloyd_b on 2007-01-05
> What if I used an earlier version of Ubuntu, like 6.06 or even 5.10? Do they use kernels that would work?

You can give it a shot.  I really don't know why the 2.6.17-10 kernel has this problem while the 2.6.18 kernel from SuSe doesn't - it is quite possible that an older kernel will work.  You can download Dapper (6.06) and give it a try.

You could also grab the Feisty testing version - it probably has a more recent kernel version.  But be aware that Feisty is NOT a stable version, so there's a real chance of other issues popping up.

Lloyd B.

---

### Post by themule on 2007-01-24
Just my 2 cents:

on one FC4 system, the second eth card stopped working some time ago (gone unnoticed since now). I think it happened after a kernel update (now running 2.6.17-1.2142_FC4).
Motherboard is AMD-751 [Irongate] based, too. Symptoms are the same. Both cards are tulip-based, at load time you get:

Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
PCI: setting IRQ 12 as level-triggered
ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
tulip0:  EEPROM default media type Autosense.
tulip0:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
tulip0:  MII transceiver #1 config 1000 status 782d advertising 01e1.
eth0: Digital DS21143 Tulip rev 65 at d8816800, 00:C0:F0:4D:8A:B1, IRQ 12.
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
PCI: Unable to reserve I/O region #1:80@de00 for device 0000:00:0a.0 :frown: 

But before that i noticed also:
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
pnp: 00:01: ioport range 0xde00-0xde03 has been reserved    :frown: 
PCI: Bridge: 0000:00:01.0
  IO window: c000-cfff
  MEM window: edd00000-eddfffff
  PREFETCH window: e3b00000-e3bfffff

which might explain /proc/ioports output:

[FONT="Courier New"]dc00-dc7f : 0000:00:09.0
[this is the first card bus address]
  dc00-dc7f : tulip
  [i/o region correctly grabbed by the driver]
de00-de7f : 0000:00:0a.0
[this is the second card bus address]
  de00-de03 : motherboard
  [some other driver claimed part of the space already]
    de00-de03 : pnp 00:01[/FONT]

So it's not distro specific, and it's possibily something on the MB that gets recognized by new kernels only, and that happens at early boot stage... i checked BIOS setup but saw nothing apparently related.

---

### Post by prensing on 2007-07-18
Does anyone have a resolution for this? I am trying to install Feisty on an older machine and am hitting exactly this problem. Thanks.

---

### Post by prensing on 2007-07-23
I have solved this (sort of) on my machine. I added "acpi=off" to the boot and the card was seen immediately. Of course, now my power management is disabled, but don't think I care and there may be a way of just shutting off ACPI PNP.

---

