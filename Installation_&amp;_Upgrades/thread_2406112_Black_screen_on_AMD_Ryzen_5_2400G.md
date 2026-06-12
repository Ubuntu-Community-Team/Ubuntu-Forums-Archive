---
title: "Black screen on AMD Ryzen 5 2400G"
date: 2018-11-15
forum: Installation &amp; Upgrades
---

### Post by dam034 on 2018-11-15
Dear users,

I created a bootable USB to install ubuntu 18.10 on a pc with these components:
[LIST]
[*]ASRock - B450 GAMING-ITX/AC Mini ITX AM4 Motherboard
[*]AMD - Ryzen 5 2400G 3.6 GHz Quad-Core Processor
[*]Patriot - Viper 4 8 GB (2 x 4 GB) DDR4-3000 Memory
[/LIST]

I created the USB with Rufus 3.3p selecting GPT-UEFI-FAT32 options.

When I select "Try Ubuntu without installing", the screen becomes black with "No signal" shown, as you can see in [this screencast]("http://cdn.dampc.ga/ctv/ub-live.mp4").
When I select "Install ubuntu" I can install ubuntu without problems.

After rebooting, when I try to boot ubuntu, after selecting it in grub, I have black screen with "No signal" shown, but the ethernet and optical audio lights (on motherboard) turn on. So I try continously to reboot, and ubuntu started 3-4 times on 20 attempts.
When I installed it, I selected the checkbox to install additional drivers and the checkbox to download the updates during installation.

When I try to boot ubuntu, these are the 2 types of problems:
[list]
[*][screencast 1]("http://cdn.dampc.ga/ctv/avvio%20ub%202.mp4")
[*][screencast 2]("http://cdn.dampc.ga/ctv/avvio%20ub%203.mkv")
[/list]
And then I power off the computer, because the boot stops.

When ubuntu managed to start (3-4 times), I created two journals with these commands:
```
journalctl -D /var/log/journal/long-name -b > starting-journal.txt
journalctl -b1 > previous-boot-journal.txt
```
So one is for a successful boot, one for failed boot:
[list]
[*][successful]("http://cdn.dampc.ga/ctv/giornale-avvio.txt")
[*][failed]("http://cdn.dampc.ga/ctv/giornale-avvio-precedente.txt")
[/list]
And I executed some commands to get info:
```
root@videotv:~# uname -a
Linux videotv 4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
root@videotv:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:        18.10
Codename:        cosmic
root@videotv:~# lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15d0
    Subsystem: ASRock Incorporation Device 15d0
    Flags: fast devsel

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 15d1
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device 15d1
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Capabilities: [40] Secure device <?>
    Capabilities: [64] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [74] HyperTransport: MSI Mapping Enable+ Fixed+

00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
    Flags: fast devsel

00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=15, subordinate=25, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff
    Memory behind bridge: fe600000-fe8fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 1453
    Capabilities: [c8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [270] #19
    Capabilities: [2a0] Access Control Services
    Capabilities: [370] L1 PM Substates
    Kernel driver in use: pcieport

00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=2e, subordinate=2e, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f0200000-f03fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 1453
    Capabilities: [c8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [270] #19
    Capabilities: [2a0] Access Control Services
    Capabilities: [370] L1 PM Substates
    Kernel driver in use: pcieport

00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
    Flags: fast devsel

00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Bus: primary=00, secondary=38, subordinate=38, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe200000-fe5fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 0000
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [270] #19
    Capabilities: [2a0] Access Control Services
    Kernel driver in use: pcieport

00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15dc (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Bus: primary=00, secondary=39, subordinate=39, sec-latency=0
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Subsystem: Advanced Micro Devices, Inc. [AMD] Device 0000
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [270] #19
    Kernel driver in use: pcieport

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
    Subsystem: ASRock Incorporation FCH SMBus Controller
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
    Subsystem: ASRock Incorporation FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e8
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e9
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ea
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15eb
    Flags: fast devsel
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ec
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ed
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ee
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ef
    Flags: fast devsel

15:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43d5 (rev 01) (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 43d5
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fe8a0000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [300] Latency Tolerance Reporting
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: xhci_hcd

15:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43c8 (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 43c8
    Flags: bus master, fast devsel, latency 0, IRQ 60
    Memory at fe880000 (32-bit, non-prefetchable) [size=128K]
    Expansion ROM at fe800000 [disabled] [size=512K]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: ahci
    Kernel modules: ahci

15:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c6 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Bus: primary=15, secondary=1d, subordinate=25, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff
    Memory behind bridge: fe600000-fe7fffff
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Upstream Port, MSI 00
    Capabilities: [c0] Subsystem: ASRock Incorporation Device 43c6
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: pcieport

1d:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Bus: primary=1d, secondary=1e, subordinate=1e, sec-latency=0
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASRock Incorporation Device 43c7
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

1d:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Bus: primary=1d, secondary=1f, subordinate=1f, sec-latency=0
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASRock Incorporation Device 43c7
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

1d:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Bus: primary=1d, secondary=22, subordinate=22, sec-latency=0
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASRock Incorporation Device 43c7
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

1d:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Bus: primary=1d, secondary=23, subordinate=23, sec-latency=0
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASMedia Technology Inc. Device 3306
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

1d:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Bus: primary=1d, secondary=24, subordinate=24, sec-latency=0
    Memory behind bridge: fe700000-fe7fffff
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASMedia Technology Inc. Device 3306
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

1d:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Bus: primary=1d, secondary=25, subordinate=25, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff
    Memory behind bridge: fe600000-fe6fffff
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASMedia Technology Inc. Device 3306
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] #19
    Capabilities: [400] L1 PM Substates
    Kernel driver in use: pcieport

24:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)
    Subsystem: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak]
    Flags: bus master, fast devsel, latency 0, IRQ 68
    Memory at fe700000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 30-24-32-ff-ff-8e-cd-6c
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [154] L1 PM Substates
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

25:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
    Subsystem: ASRock Incorporation I211 Gigabit Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 39
    Memory at fe600000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at f000 [size=32]
    Memory at fe620000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [70] MSI-X: Enable+ Count=5 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 70-85-c2-ff-ff-a1-b7-22
    Capabilities: [1a0] Transaction Processing Hints
    Kernel driver in use: igb
    Kernel modules: igb

38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c6) (prog-if 00 [VGA controller])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
    Flags: bus master, fast devsel, latency 0, IRQ 72
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at e000 [size=256]
    Memory at fe500000 (32-bit, non-prefetchable) [size=512K]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [c0] MSI-X: Enable- Count=3 Masked-
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [200] #15
    Capabilities: [270] #19
    Capabilities: [2a0] Access Control Services
    Capabilities: [2b0] Address Translation Service (ATS)
    Capabilities: [2c0] Page Request Interface (PRI)
    Capabilities: [2d0] Process Address Space ID (PASID)
    Capabilities: [320] Latency Tolerance Reporting
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

38:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
    Flags: bus master, fast devsel, latency 0, IRQ 70
    Memory at fe588000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

38:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device 15df
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at fe400000 (32-bit, non-prefetchable) [size=1M]
    Memory at fe58c000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [c0] MSI-X: Enable- Count=2 Masked-
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>

38:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e0 (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 7914
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fe300000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [c0] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: xhci_hcd

38:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e1 (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 7914
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at fe200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [c0] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: xhci_hcd

38:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
    Subsystem: ASRock Incorporation Device 2220
    Flags: bus master, fast devsel, latency 0, IRQ 71
    Memory at fe580000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

39:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation FCH SATA Controller [AHCI mode]
    Flags: bus master, fast devsel, latency 0, IRQ 62
    Memory at fe900000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/2 Maskable- 64bit+
    Capabilities: [d0] SATA HBA v1.0
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [270] #19
    Kernel driver in use: ahci
    Kernel modules: ahci
```

How can I fix this boot issue? It seems a graphic driver issue.


Thanks

---

### Post by dinkidonk on 2018-11-16
As the first thing, you should make sure that your BIOS is the latest version available and that the memory is set to run at SPD speed (2133Mhz, disable DOCP or whatever), resetting the BIOS to default values may also be a good idea. When booting the installation media, you must highlight "Start Ubuntu" and hit "e" on the keyboard and change "quiet splash" to "nomodeset quiet splash" in the first line and hit ctrl+x to boot with that option. When your system is installed and booted (you may need the nomodeset option to boot after install), you must make sure that the system is up-to-date by installing all suggested updates. Then you need to upgrade the kernel to at least 4.19. You can do that with the UKUU (Ubuntu Kernel Update Utility) or you can just use the following set of commands:

```
mkdir /tmp/kernelupdate
cd /tmp/kernelupdate
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901_4.19.1-041901.201811041431_all.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-modules-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-image-unsigned-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
sudo dpkg -i *.deb
cd /
rm -r /tmp/kernelupdate
#REBOOT!
```

If you want another kernel than 4.19.1, you can get a [list of available kernels here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). If you still have problems, you may need to update MESA using the PPA's from [Ubuntu-X Team]("https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates"). When the system is working satisfyingly you can (re)set your memory to whatever it can handle.

---

### Post by dam034 on 2018-11-16
I have UEFI instead of BIOS, the motherboard was released this year, so I have an updated UEFI.

I managed to boot ubuntu with nomodeset parameter after 5 attempts, because I could see the ubuntu logo (with five white dots), and a white underscore flashing in the black screen at top left corner.

I executed apt update, upgrade and autoremove commands and the list of commands you sent. The result is the same: ubuntu manages to start once in a while.

If you want, I can send the screencast showing UEFI settings and ubuntu boot attempt.

I didn't understand the update of MESA, can you explain better?

Thanks

---

### Post by dinkidonk on 2018-11-16
Your problem may be issues with the motherboard, the B450 chipset is pretty new so try to search the web for any clues in that regard. Kernel 4.18 in combination with never AGESA (part of the BIOS/UEFI) versions are known to cause boot problems which have mostly been fixed in kernel 4.19. MESA is (part of the) graphics stack in Ubuntu/Linux, if your problem is related to iGPU, updating MESA may fix the issues - the link I posted clearly shows how to do this with two commands. Did you try to set memory @ SPD speed or reset BIOS/UEFI? Have you tried with Ubuntu 18.04 LTS? Have you had success installing other systems on the hardware?

I'm currently writing from a system with a ASUS PRIME A320M-A motherboard + Ryzen 2400G APU + 8GiB of 2133Mhz memory running Kubuntu 18.04.1 LTS and I have next to no issues with it, so... :)

EDIT: Most ppl experiences boot issues when "warm booting", usually cold booting causes no problems.

---

### Post by dam034 on 2018-11-16
I have also installed Windows 10, downloaded from Microsoft website, with the Oct 18 update, and it works fine.
I tried to install ubuntu 16.04, but it had also graphic issues, the screen flashed and broken continously.

Are these the commands to update MESA?
```
add-apt-repository ppa:ubuntu-x-swat/updates
apt-get update
```

The RAM speed is 3000Mhz, I can screencast the UEFI and send here, so you can see if I did something wrong. Do you want to see it?


Thanks

---

### Post by dinkidonk on 2018-11-17
Please try [Ubuntu 18.04.1 LTS](https://www.ubuntu.com/download/desktop/thank-you?country=DK&version=18.04.1&architecture=amd64) and not 18.10 or 16.04. Use the nomodeset boot option for installation, upgrade kernel to at least 4.19 and see how it goes. I would still recommend you to either reset your BIOS/UEFI to default or at least run your memory at SPD speed (2133Mhz) until the system is stable, even though you do not seem to mind this tip.

---

### Post by dam034 on 2018-11-18
So I installed the 18.04 version and and 4.19 kernel from github as you wrote in post #2.

I can't understand where in UEFI I can set the memory speed, so I did two screencast to show my UEFI, and you can tell me where I have to change the settings:
[LIST]
[*][video 1]("http://cdn.dampc.ga/ctv/uefi.mp4") showing all UEFI
[*][video 2]("http://cdn.dampc.ga/ctv/uefi-a.mp4") showing the advanced tab in UEFI
[/LIST]

After the installation, I managed to start ubuntu as you can see in [this video]("http://cdn.dampc.ga/ctv/avvio-buono.mp4").
In the installation, I check the boxes to install updates and additional drivers.

Now it seems that the boot works properly, as long as I add nomodeset on every boot. Is there a way to save nomodeset setting so I don't have to add it on every boot?

I don't want to bring bad luck, but in case it returns to give a black screen, what should I do?

And about the updates, what do I have to do with the kernels?

Thanks

---

### Post by dinkidonk on 2018-11-21
Sorry, I'm out of ideas then. I suspect your problem to be a lack of support for the motherboard / chipset - but I'm not sure. You could try Manjaro and see if that works for you :)

---

