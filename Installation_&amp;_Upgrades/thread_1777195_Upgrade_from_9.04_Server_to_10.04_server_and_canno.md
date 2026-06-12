---
title: "Upgrade from 9.04 Server to 10.04 server and cannot boot"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by AndiTails on 2011-06-07
Hello all,

I'm hoping someone can help me.
I've just upgraded by dedicated server with OVH from 9.04 to 10.04 and it now refuses to boot with the error 
"kernel panic unable to mount rootfs on unknown block 2,0"

With OVH you must use their custom kernel, but this has been installed and seems to boot thus far, but fails at above.
OVH also recommend adding a dev line to fstab, which I've done: [http://travaux.ovh.net/?do=details&id=4154](http://travaux.ovh.net/?do=details&id=4154)

I'm now at a loss as what to do, as it seems the kernel can't see the hard drives, yet when I boot up in rescue mode, I can mount all the drives fine.

Any help gratefully received!

Files of interest below.

lilo.conf
```
boot=/dev/sda
prompt
timeout=50
default=linux_updated

# Enable large memory mode.
large-memory

image=/boot/bzImage-2.6.38.2-xxxx-grs-ipv6-64
        label="linux_updated"
        root=/dev/sda1
        read-only
```

fstab
```
# <sys.fichiers><pt de montage><type> <options>  <dump> <pass>
/dev/sda1       /       ext4    errors=remount-ro       0       1
/dev/sda2       /home   ext4    defaults        1       2
/dev/sda3       swap    swap    defaults        0       0
/dev/sdb1       /backup ext4    defaults        1       2
proc            /proc   proc    defaults                0       0
sysfs           /sys    sysfs   defaults                0       0
dev             /dev    devtmpfs        rw      0       0
```

lspci -v
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: fast devsel
        Capabilities: [40] #00 [0000]

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: [40] Subsystem: Super Micro Computer Inc Device 0605
        Capabilities: [60] Message Signalled Interrupts: Mask+ 64bit- Queue=0/1 Enable+
        Capabilities: [90] Express Root Port (Slot+), MSI 00
        Capabilities: [e0] Power Management version 3
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [150] Access Controls <?>
        Capabilities: [160] Vendor Specific Information <?>
        Kernel driver in use: pcieport

00:05.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 3 (rev 11) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Subsystem: Super Micro Computer Inc Device 0605
        Capabilities: [60] Message Signalled Interrupts: Mask+ 64bit- Queue=0/1 Enable+
        Capabilities: [90] Express Root Port (Slot+), MSI 00
        Capabilities: [e0] Power Management version 3
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [150] Access Controls <?>
        Kernel driver in use: pcieport

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel
        Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Vendor Specific Information <?>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
        Subsystem: Device 00d9:0005
        Flags: fast devsel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c0000000-c01fffff
        Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Super Micro Computer Inc Device 0605
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fae00000-faefffff
        Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Super Micro Computer Inc Device 0605
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: faf00000-faffffff
        Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Super Micro Computer Inc Device 0605
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fadfc000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCIe advanced features <?>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: fb000000-fbffffff
        Prefetchable memory behind bridge: 00000000f9000000-00000000f9ffffff
        Capabilities: [50] Subsystem: Super Micro Computer Inc Device 0605

00:1f.0 ISA bridge: Intel Corporation 3400 Series Chipset LPC Interface Controller (rev 05)
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=16]
        I/O ports at c080 [size=16]
        Capabilities: [70] Power Management version 3
        Capabilities: [b0] PCIe advanced features <?>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: medium devsel, IRQ 3
        Memory at fadff800 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0400 [size=32]

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05) (prog-if 85 [Master SecO PriO])
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at bc00 [size=8]
        I/O ports at b880 [size=4]
        I/O ports at b800 [size=8]
        I/O ports at b480 [size=4]
        I/O ports at b400 [size=16]
        I/O ports at b080 [size=16]
        Capabilities: [70] Power Management version 3
        Capabilities: [b0] PCIe advanced features <?>
        Kernel driver in use: ata_piix

04:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at faee0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at dc00 [size=32]
        Memory at faedc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [a0] MSI-X: Enable+ Mask- TabSize=5
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number fa-78-de-ff-ff-48-30-00
        Kernel driver in use: e1000e

05:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fafe0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at ec00 [size=32]
        Memory at fafdc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [a0] MSI-X: Enable+ Mask- TabSize=5
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number fb-78-de-ff-ff-48-30-00
        Kernel driver in use: e1000e

06:03.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200eW WPCM450 (rev 0a) (prog-if 00 [VGA controller])
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, medium devsel, latency 64, IRQ 15
        Memory at f9000000 (32-bit, prefetchable) [size=16M]
        Memory at fbffc000 (32-bit, non-prefetchable) [size=16K]
        Memory at fb000000 (32-bit, non-prefetchable) [size=8M]
        Capabilities: [dc] Power Management version 1
```

---

### Post by mörgæs on 2011-06-08
This looks a bit strange to me.

The list mentions 2.6.38, which is the kernel used in Ubuntu 11.04. Have you upgraded all the way to 11.04?

---

### Post by psusi on 2011-06-08
You can not upgrade from 9.04 directly to 10.04.  You can only upgrade 9.04 to 9.10.  Did you do that, and THEN upgrade to 10.04?

You also are missing an initramfs for your kernel, and why are you using lilo?

---

