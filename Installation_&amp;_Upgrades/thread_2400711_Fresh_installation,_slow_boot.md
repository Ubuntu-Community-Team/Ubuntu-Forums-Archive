---
title: "Fresh installation, slow boot"
date: 2018-09-09
forum: Installation &amp; Upgrades
---

### Post by spearhead2 on 2018-09-09
I've upgraded old Laptop to use Lubuntu 18.04 instead Windows 7. The system works fine, however I'm finding the boot speed surprisingly slow compared to previous OS and my different machine alike. I'd like to change this, if possible.

```

$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @51.441s
&#9492;&#9472;multi-user.target @51.441s
  &#9492;&#9472;kerneloops.service @51.428s +12ms
    &#9492;&#9472;network-online.target @51.427s
      &#9492;&#9472;NetworkManager-wait-online.service @31.464s +19.963s
        &#9492;&#9472;NetworkManager.service @27.802s +3.659s
          &#9492;&#9472;dbus.service @27.790s
            &#9492;&#9472;basic.target @27.716s
              &#9492;&#9472;sockets.target @27.716s
                &#9492;&#9472;dbus.socket @27.716s
                  &#9492;&#9472;sysinit.target @27.629s
                    &#9492;&#9472;systemd-timesyncd.service @27.364s +264ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @17.476s +9.778s
                        &#9492;&#9472;systemd-journal-flush.service @2.976s +14.499s
                          &#9492;&#9472;systemd-remount-fs.service @2.306s +668ms
                            &#9492;&#9472;systemd-journald.socket @2.278s
                              &#9492;&#9472;system.slice @2.277s
                                &#9492;&#9472;-.slice @2.273s
```

```
$ lshw
WARNING: you should run this program as super-user.
mariusz-k73sd               
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3848MiB
     *-cpu
          product: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 907MHz
          capacity: 2300MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm arat pln pts flush_l1d cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:dc000000-dd0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF119M [GeForce 610M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:33 memory:dc000000-dcffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:d000(size=128) memory:dd000000-dd07ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:dd400000-dd7fffff memory:b0000000-bfffffff ioport:e000(size=64) memory:c0000-dffff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:df60b000-df60b00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:df608000-df6083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:df600000-df603fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:c000(size=4096) memory:dec00000-df5fffff ioport:d3700000(size=10485760)
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:b000(size=4096) memory:de200000-debfffff ioport:d2c00000(size=10485760)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: 00:08:ca:84:bd:7f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.15.0-33-generic firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:de200000-de27ffff memory:de280000-de28ffff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:a000(size=4096) memory:dd800000-de1fffff ioport:d2100000(size=10485760)
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: c0
                serial: c8:60:00:33:6b:e0
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                resources: irq:31 memory:dd800000-dd83ffff ioport:a000(size=128)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:df607000-df6073ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:e0b0(size=8) ioport:e0a0(size=4) ioport:e090(size=8) ioport:e080(size=4) ioport:e060(size=32) memory:df606000-df6067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df605000-df6050ff ioport:e040(size=32)
     *-scsi
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8B0AW
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


```

```

$ dmesg | grep -i error
[    1.821105] RAS: Correctable Errors collector initialized.
[    7.195866] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   24.364082] usb 1-1.1: device descriptor read/64, error -110
[   35.200038] usb 1-1.1: device not accepting address 5, error -32



```

---

