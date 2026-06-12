---
title: "Can't boot 12.04 nor 14.04 on Asus with celeron dual core and chipset Sis 671"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by robertco on 2015-01-29
Hello friends!
I'm trying to install one of the two versions in subject on an Asus notebook model 

this is the output of lspci

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 64
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [d0] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [f4] Power Management version 2
    Capabilities: [70] Subsystem: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
    Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 128
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fff0 [size=16]
    Capabilities: [58] Power Management version 2
    Kernel driver in use: pata_sis

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at fddff000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fddfe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at fddfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 1815
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fddfcc00 (32-bit, non-prefetchable) [size=128]
    I/O ports at cc00 [size=128]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: sis190
    Kernel modules: sis190

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 1847
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at c800 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b800 [size=16]
    I/O ports at b400 [size=128]
    Capabilities: [58] Power Management version 2
    Kernel driver in use: sata_sis
    Kernel modules: sata_sis

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fdf00000-fdffffff
    Capabilities: [b0] Subsystem: Silicon Integrated Systems [SiS] Device 0004
    Capabilities: [c0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [d0] Express Root Port (Slot+), MSI 00
    Capabilities: [f4] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=06, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe000000-febfffff
    Prefetchable memory behind bridge: 00000000fa000000-00000000fcffffff
    Capabilities: [b0] Subsystem: Silicon Integrated Systems [SiS] Device 0004
    Capabilities: [c0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [d0] Express Root Port (Slot+), MSI 00
    Capabilities: [f4] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 1883
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fddf4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
    Subsystem: ASUSTeK Computer Inc. Device 1b32
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at d800 [size=256]
    Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at fdec0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
    Subsystem: ATI Technologies Inc RV710/730
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdeec000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Device 1a3b:1067
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

While booting, either in a live session, 

with ACPI=OFF it hangs right after one line that says "app armor"

with NOLAPIC it hangs with what you see in [this screeshot]("https://drive.google.com/file/d/0B4_vsda_GXyeejBjTU1aS1I1cjA/view?pli=1")

The pretty strange is that with Ubuntu 10.04 netbook live cd it boots pretty fine (the lspci has been run from this live netbook version cd)

Thank you for hinting

Cor

---

### Post by fantab on 2015-01-29
Have you done a [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") on the downloaded ubuntu.iso image to check its integrity? Also test the Ubuntu DVD/USB on another machine to rule out any 'burn' issues.
The error from the screenshot points to a bad burn (since 10.04 boots 'pretty fine'). Try again after you've re-burned the .iso image to a DVD/USB.

Is there another OS in the picture? Are you dual-booting?

---

### Post by mörgæs on 2015-01-29
Here's some more information about SIS graphics processors:
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by robertco on 2015-01-29
Hello, thank you for replying

I have the same issue with
14.04, 12.04 and crunchbang (crunchbang ISO is tested and working on an old netbook Acer, I've installed it past week) latest version
Looks not an ISO integrity issue, though I'll also check the checksum.

About dual boot, there is no one.
I've the original hdd of the notebook that as I did many times now, I've installed ubuntu 14.04 x32 on another intel core duo pc.
Also fitting this hdd prepared on another machine won't boot, while fitting this hdd on three different PCs, they boot fine.


I forgot, I've tried also lubuntu 14.04, same issue.
This notebook, was running windows XP until January the 26 2015 without issues.

---

### Post by mörgæs on 2015-01-29
Are you able to install Lubuntu using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by robertco on 2015-01-29
Going to try that out (because of your suggestion :-) ) and I'll update the post

Things changed a little with lubuntu 14.04 minimal ISO.
Boot hanged as previous attempts, so I've booted again with option nolapic
With this parameter, now installation is in progress, though we'll see after that's finished if it will be able to boot into the new system.
Last but not least, at this stage it is in text mode and no drivers looks are loaded (so far)

---

### Post by robertco on 2015-01-29
Installed fine
Changed/edited grub and added "nolapic"
Doesn't finishes the boot, blank screen.
Though hdd blinks for some seconds loading first part of boot.

Also checked MD5 checksum for the ubuntu 14.04.1 ISO and matches.
I'm running it from USB pendrive made with latest UUI (universla usb installer)
but it goes "
*&#8220;(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error.*
 *Can not mount /dev/loop0 (cdrom/casperfilesystem.squashfs) on //filesystem.squashfs.&#8221;"*

---

### Post by mörgæs on 2015-01-31
I am not sure I understand what works and what does not. 
Did you manage to install the command-line only system?

---

