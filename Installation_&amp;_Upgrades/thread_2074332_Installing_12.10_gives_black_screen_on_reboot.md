---
title: "Installing 12.10 gives black screen on reboot"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Geezanansa on 2012-10-21
Once ubuntu finished installing;  after removing DVD and pressing enter when requested system never managed to shutdown properly in order to start POST just get a black screen with no input so no tty or cli or alt + sysrq +reisub so power button on case had to be used.  
Got to log in screen once powered up again.

imo this is a xorg bug which is well reported all ready but cannot get a fix for this particular hardware configuration in order to confirm this or not.

Once logged in to default desktop session if power button at top right of screen is used to select restart or shut down the machine goes to black screen>power button on case has to be used to restart system.

Have spent time searching and have tried some work arounds like reinstalling linux headers and trying different drivers.  

Here is some machine info
```
ubuntu-user@Ubuntu-Ei-314:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: ati-agp

00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fb000000-fcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fdffe000 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at 80000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fdffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fdffb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: 66MHz, medium devsel
    I/O ports at 0500 [size=16]
    Memory at fdffa000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fde00000-fdefffff

00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 80)
    Subsystem: Foxconn International, Inc. Realtek ALC 653
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at fdff9000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_atiixp
    Kernel modules: snd-atiixp

01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device 3214
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at de000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ef00 [size=128]
    [virtual] Expansion ROM at d8000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 3214
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Foxconn International, Inc. Device 0c81
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at de00 [size=256]
    Memory at fddff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp



```

On rebooting there is some times text giving a  boot status/progress broadcast message agpart is reporting unsupported ATI chipset.

Yet the system still boots but because of all the other known bugs thought it would be ok to ask for some advice with regard to what i am trying to achieve which is to install and configure ubuntu/hardware for running games launched through steam (windows client). Thanks in advance for any constructive advice.

---

### Post by Geezanansa on 2012-10-22
It is amazing that this machine booted anything, even more so using gallium drivers before trying nvidia.  Chipset can work on older flavours but not 12.10.  The bios version being used dates to 2006.  The supplier of this machine no longer provides support nor does the motherboard manufacturer although a bios version is available from 2007 and is not for exact board(rc4107ma rs2h and not rc4107ma rs2h d3).  
 
Been window shopping and found good reports for [FONT=Arial][SIZE=2]Gigabyte GA-A75-UD4H FM1 Motherboard[/SIZE][/FONT]  which I am sure would let Ubuntu 12.10 do its thing - at a great number of knots... and that would move me forward several generations.
**[SIZE=1][/SIZE] **

---

