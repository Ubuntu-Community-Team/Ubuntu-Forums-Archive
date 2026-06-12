---
title: "LibreOffice highlighting not working correctly"
date: 2017-09-11
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2017-09-11
I recently installed Xubuntu 16.04 and when I use LibreOffice Calc the active cell is not highlighted, and in Write, when I highlight more than 1 line I get an outline instead of the usual highlighted text.
Everything works just fine, but it is inconvienient not to have the highlighting working as I like it.

some useful information (perhaps):

here are the last few lines from 
apt-get upgrade ```
apt-get upgrade
update-initramfs: Generating /boot/initrd.img-4.10.0-33-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.10.0-32-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
Setting up snapd-login-service (1.13-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...

```

About LibreOffice:
> Version: 5.1.6.2
Build ID: 1:5.1.6~rc2-0ubuntu1~xenial2
CPU Threads: 4; OS Version: Linux 4.10; UI Render: default; 
Locale: en-US (en_US.UTF-8); Calc: group

I have the latest version of libreoffice-gtk3

outupt from lspci -v
```
 lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Dell 4 Series Chipset DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fe500000-fe5fffff
    Capabilities: [88] Subsystem: Dell 4 Series Chipset PCI Express Root Port
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell 4 Series Chipset Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at fe800000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ecb0 [size=8]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Dell 4 Series Chipset Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0
    Memory at fe700000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 2

00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
    Subsystem: Dell 4 Series Chipset HECI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at feda6000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell 4 Series Chipset PT IDER Controller
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    I/O ports at fe80 [size=8]
    I/O ports at fe90 [size=4]
    I/O ports at fea0 [size=8]
    I/O ports at feb0 [size=4]
    I/O ports at fef0 [size=16]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: ata_generic
    Kernel modules: pata_acpi

00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03) (prog-if 02 [16550])
    Subsystem: Dell 4 Series Chipset Serial KT Controller
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    I/O ports at ecb8 [size=8]
    Memory at fe6d8000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
    Subsystem: Dell 82567LM-3 Gigabit Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at fe6e0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fe6d9000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ece0 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at fc00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB2 EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fe6da000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
    Subsystem: Dell 82801JD/DO (ICH10 Family) HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at fe6dc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fe400000-fe4fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 82801JD/DO (ICH10 Family) PCI Express Port 1
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fe300000-fe3fffff
    Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell 82801JD/DO (ICH10 Family) PCI Express Port 2
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell 82801JD/DO (ICH10 Family) USB2 EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Memory behind bridge: fe200000-fe2fffff
    Capabilities: [50] Subsystem: Dell 82801 PCI Bridge

00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
    Subsystem: Dell 82801JDO (ICH10DO) LPC Interface Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=16]
    I/O ports at ecc0 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
    Subsystem: Dell 82801JD/DO (ICH10 Family) SMBus Controller
    Flags: medium devsel, IRQ 9
    Memory at fe6db000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0940 [size=32]
    Kernel modules: i2c_i801

00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at fe40 [size=8]
    I/O ports at fe50 [size=4]
    I/O ports at fe60 [size=8]
    I/O ports at fe70 [size=4]
    I/O ports at fed0 [size=16]
    I/O ports at ecd0 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

04:00.0 Network controller: Ralink corp. RT3062 Wireless 802.11n 2T/2R
    Subsystem: Ralink corp. RT3062 Wireless 802.11n 2T/2R
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe2f0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci
```

---

### Post by BenginM on 2017-09-12
Hiya , Download kabylake DMC - Ver 1.01 [from ]("https://01.org/linuxgraphics/downloads/firmware")

in a terminal , $ cd Downloads 

$ wget [https://01.org/sites/default/files/downloads/intelr-graphics-linux/kbldmcver101.tar.bz2](https://01.org/sites/default/files/downloads/intelr-graphics-linux/kbldmcver101.tar.bz2)
$ tar xvjf kbldmcver101.tar.bz2
$ sudo cp -t /lib/firmware/i915/ kbl_dmc_ver1_01/kbl_dmc_ver1_01.bin
$ sudo update-initramfs -u -k all

save your works , and reboot .. open LibreOffice see highlight and test , does the glitch still remains!

---

### Post by BenginM on 2017-09-13
Also, is OpenGL enabled or disabled ?

---

### Post by reut2 on 2017-09-14
> **BenginM said:**
> Also, is OpenGL enabled or disabled ?

```
reuven@reuven:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 2.1 Mesa 12.0.6
reuven@reuven:~$ 



```

---

