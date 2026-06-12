---
title: "64bit vs 32bit"
date: 2016-12-22
forum: Installation &amp; Upgrades
---

### Post by hyburn on 2016-12-22
I believe I have installed the 64bit copy of 16.04, but its rather slow... not like I remember. please review the output of my lshw and tell me if I should switch to the 32bit architecture

```
description: Desktop Computer
    product: Z97-HD3P (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To be filled by O.E.M. uuid=FC02AA03-1404-9505-0F06-3E0700080009
  *-core
       description: Motherboard
       product: Z97-HD3P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F2
          date: 09/17/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
          vendor: Intel Corp.
          physical id: 3d
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
          slot: SOCKET 0
          size: 3902MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 3e
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 3f
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 40
             slot: CPU Internal L3
             size: 8MiB
             capacity: 8MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 42
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: DDR3 1600
             vendor: Fujitsu
             physical id: 1
             serial: 0000C48C
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: DDR3 1600
             vendor: Fujitsu
             physical id: 3
             serial: 0000C8EB
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM206 [GeForce GTX 960]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:34 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:33 memory:f7914000-f7917fff
        *-usb:0
             description: USB controller
             product: 9 Series Chipset Family USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:27 memory:f7900000-f790ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-57-generic xhci-hcd
                physical id: 0
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-57-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=14 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@3:3
                   version: 22.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   physical id: 4
                   bus info: usb@3:4
                   version: 4.06
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:2
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: ATHER
                   physical id: b
                   bus info: usb@3:b
                   version: 1.06
                   serial: 12345
                   capabilities: usb-2.00
                   configuration: driver=carl9170 maxpower=500mA speed=480Mbit/s
        *-communication
             description: Communication controller
             product: 9 Series Chipset Family ME Interface #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:31 memory:f791c000-f791c00f
        *-usb:1
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f791b000-f791b3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-57-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia:1
             description: Audio device
             product: 9 Series Chipset Family HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:f7910000-f7913fff
        *-pci:1
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) memory:f7800000-f78fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 11
                serial: fc:aa:14:95:0f:3e
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:29 ioport:d000(size=256) memory:f7800000-f7800fff memory:f2100000-f2103fff
        *-pci:3
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 41
                width: 64 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: iomemory:222001f10-222001f0f
        *-usb:2
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f791a000-f791a3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-57-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: 9 Series Chipset Family Z97 LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 9 Series Chipset Family SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7919000-f79197ff
        *-serial UNCLAIMED
             description: SMBus
             product: 9 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7918000-f79180ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160023AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 3.00
             serial: 4MT1D6XH
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e65b9798
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 3ae213f8-a2c3-4777-8785-da6f5bd46272
                size: 133GiB
                capacity: 133GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-12-19 22:14:02 filesystem=ext4 lastmountpoint=/ modified=2016-12-22 05:07:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-12-21 14:19:22 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 15GiB
                capacity: 15GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 15GiB
                   capabilities: nofs
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:11
       logical name: wlx002127c367ac
       serial: 00:21:27:c3:67:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=carl9170 driverversion=4.4.0-57-generic firmware=1.9.6 ip=192.168.0.4 link=yes multicast=yes wireless=IEEE 802.11bgn
```

not sure if this helps but here is my lscpu
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Model name:            Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
Stepping:              3
CPU MHz:               895.640
CPU max MHz:           4000.0000
CPU min MHz:           800.0000
BogoMIPS:              7200.03
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
```

---

### Post by oldfred on 2016-12-22
It is a 64 bit system. 
Just about all Intel/AMD systems in last 10 years have been 64 bit except some smaller tablet systems. Some small 64 bit systems used 32 bit UEFI to try to prevent other systems from installing, but later Linux added 32 bit UEFI support.

Did you install in UEFI boot mode on gpt partitioned drive?  
You could have the 35 year old BIOS/MBR configuration, but it still should not be noticeably slow.

Some other Gigabyte motherboards need boot parameters. Do not know if your model needed any or not.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5) 

What video card or are you using the internal Intel video?

---

### Post by hyburn on 2016-12-22
as per the UEFI boot mode... I think so. How would I check this?

*****************
my */sys/firmware* file has acpi, dmi, and memmap
I do have a file in */etc/grub.d* named:
```

30_uefi-firmware

```


*****************
as for the viedo card I have a *Geforce GTX960*

---

### Post by oldfred on 2016-12-22
Did you try re-booting and see if either or several of the suggested boot parameters help?

Have you installed nVidia drivers?
You should just be able to install from System Settings, Software & updates, & drivers tab.
If you installed a nVidia driver before, you must totally purge/delete it before installing another. Otherwise you get conflicts as new driver does not uninstall old driver.

---

### Post by hyburn on 2016-12-22
yes I switched it to the proprietary driver for Nvidia

---

### Post by oldfred on 2016-12-22
So what is slow?

---

### Post by hyburn on 2016-12-23
1.)  When I boot, it stalls at the purple screen for a while

2.) When I launch mozilla it stalls and waits a few seconds before I see the window

---

### Post by oldfred on 2016-12-23
Still sounds like video issue?
Did you install more than one nVidia driver? And not totally purge old one?

Do either of these show long times on any boot process.
       systemd-analyze blame 

 systemd-analyze

---

### Post by hyburn on 2016-12-23
systemd-analyze blame:
```
37.491s dev-sda1.device
          8.812s apparmor.service
          5.666s console-setup.service
          4.993s grub-common.service
          4.785s networking.service
          4.629s apport.service
          4.613s irqbalance.service
          4.192s speech-dispatcher.service
          4.192s ondemand.service
          3.237s binfmt-support.service
          2.979s plymouth-start.service
          2.758s NetworkManager.service
          2.728s ModemManager.service
          2.596s accounts-daemon.service
          2.457s systemd-udevd.service
          2.381s lightdm.service
          2.323s thermald.service
          2.296s dns-clean.service
          1.825s gpu-manager.service
          1.809s systemd-tmpfiles-setup-dev.service
          1.762s keyboard-setup.service
          1.704s iio-sensor-proxy.service
          1.320s systemd-modules-load.service
```

systemd-analyze:
```

Startup finished in 2.915s (kernel) + 45.067s (userspace) = 47.982s

```

---

### Post by hyburn on 2016-12-23
I turned off the bluetooth at boot through BUM and have been able to shave the sda boot to 36.758s.

As I am not that familiar with what is critical for boot

by running systemd-analyze critical-chain I see that my graphical target is taking 44.888s to boot. how can we reduce this?

---

### Post by oldfred on 2016-12-23
Back to video issues.
Have you just to experiment moved connector to monitor to internal video to only use Intel video?

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA 

 dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia

---

