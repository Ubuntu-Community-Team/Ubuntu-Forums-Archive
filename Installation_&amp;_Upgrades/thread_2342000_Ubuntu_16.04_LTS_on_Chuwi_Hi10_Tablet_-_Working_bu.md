---
title: "Ubuntu 16.04 LTS on Chuwi Hi10 Tablet - Working but need help"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by skanger on 2016-11-02
I tried to get used to W10 but could not and worse yet, it was corrupting files on my USB flash drives constantly. W10 apparently has serious issues with USB storage since its now well documented. Just the never-ending notifications that a good drive needed formatting or had a problem were enough to make me re-format.

I installed 16.04 directly over W10 and it functions, but its not usable yet. Some of the problems are:

1) None of the tablet functions are working (touch screen, auto-rotate)
2) No wi-fi
3) It is operating, but slowly
4) Graphics are at full resolution sometimes, other times not.

I updated but that made no difference. Under 3rd party drivers in the software manager I disable the Intel microcode driver which seemed to help a bit.

For me this was not an easy decision since the tablet maker offers no support or warranty if W10 is altered, but I'm glad its gone. I want to be free of W for good. No version of Ubuntu has ever corrupted any drive of mine, internal or external. 

Any help, suggestions or recommendations are greatly appreciated!

---

### Post by skanger on 2016-11-14
Since getting this tablet to be fully functional under Ubuntu 16.04  requires proper drivers, I would greatly appreciate help running commands to determine what chip sets the tablet uses for its different subsystems. I know only a little about those commands (dmesg, ls, etc.) but not how to properly use them to get the information the knowledgeable people here need.

 I also know that there is a lot of interest in installing Ubuntu onto these low priced tablets, so any progress with getting this tablet functional would definitely increase interest in the Ubuntu OS.

---

### Post by mörgæs on 2016-11-14
Try these:

[https://ubuntuforums.org/showthread.php?t=2321854&page=3&p=13485819&viewfull=1#post13485819](https://ubuntuforums.org/showthread.php?t=2321854&page=3&p=13485819&viewfull=1#post13485819)

I suggest 16.10 and not 16.04 for new hardware.

---

### Post by skanger on 2016-11-15
Thank you for your reply and suggestions. Below are the results of the three commands in the order they were listed in the old post you referenced.

I already downloaded 16.10 and will try that later. It looks like it has a more recent kernel so maybe that will make a difference.


```
--------------------- sudo lshw -numeric -sanitize results
computer                  
    description: Desktop Computer
    product: Default string (MRD)
    vendor: Default string
    version: Default string
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=desktop family=CherryTrail CR sku=MRD uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Cherry Trail CR
       vendor: Hampoo
       physical id: 0
       version: Default string
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P02A_C106.60D
          date: 03/03/2016
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 1066 MHz (0.9 ns)
             product: 00000000
             vendor: Hynix Semiconductor
             physical id: 0
             serial: [REMOVED]
             slot: A1_DIMM0
             size: 4GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM [empty]
             product: 00000000
             vendor: Hynix Semiconductor
             physical id: 1
             serial: [REMOVED]
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 32
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 33
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz
          vendor: Intel Corp.
          physical id: 34
          bus info: cpu@0
          version: Intel(R) Atom(TM) x5-Z8300 CPU @ 1.44GHz
          slot: SOCKET 0
          size: 479MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 80MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Intel Corporation [8086:2280]
          vendor: Intel Corporation [8086]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 22
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation [8086:22B0]
             vendor: Intel Corporation [8086]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d0ffffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: Intel Corporation [8086:22B8]
             vendor: Intel Corporation [8086]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:d1000000-d13fffff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation [8086:22DC]
             vendor: Intel Corporation [8086]
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:310 memory:d183b000-d183bfff
        *-usb
             description: USB controller
             product: Intel Corporation [8086:22B5]
             vendor: Intel Corporation [8086]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:115 memory:d1800000-d180ffff
           *-usbhost:0
                product: xHCI Host Controller [1D6B:3]
                vendor: Linux 4.4.0-45-generic xhci-hcd [1D6B]
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb
                   description: USB hub
                   product: USB3.0 Hub [BDA:401]
                   vendor: Realtek [BDA]
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.11
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
                 *-usb
                      description: Generic USB device
                      product: USB 10/100/1000 LAN [BDA:8153]
                      vendor: Realtek [BDA]
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 30.00
                      serial: [REMOVED]
                      capabilities: usb-3.00
                      configuration: driver=r8152 maxpower=144mA speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller [1D6B:2]
                vendor: Linux 4.4.0-45-generic xhci-hcd [1D6B]
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB3.0 Hub [BDA:5401]
                   vendor: Realtek [BDA]
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.11
                   capabilities: usb-2.10
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Keykoard [1A2C:21]
                      vendor: USB [1A2C]
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
                 *-usb:1
                      description: Mouse
                      product: Usb Mouse [1C4F:34]
                      vendor: SIGMACHIP [1C4F]
                      physical id: 3
                      bus info: usb@1:2.3
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-generic:1
             description: Encryption controller
             product: Intel Corporation [8086:2298]
             vendor: Intel Corporation [8086]
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:311 memory:d1700000-d17fffff memory:d1600000-d16fffff
        *-isa
             description: ISA bridge
             product: Intel Corporation [8086:229C]
             vendor: Intel Corporation [8086]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enx00e04c680097
       serial: [REMOVED]
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.08.2 duplex=half link=no multicast=yes port=MII speed=10Mbit/s



00:00.0 Host bridge [0600]: Intel Corporation Device [8086:2280] (rev 22)
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel driver in use: iosf_mbi_pci

00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:22b0] (rev 22) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: i915

00:03.0 Multimedia controller [0480]: Intel Corporation Device [8086:22b8] (rev 22)
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at d1000000 (32-bit, non-prefetchable) [disabled] [size=4M]
    Capabilities: <access denied>

00:0b.0 Signal processing controller [1180]: Intel Corporation Device [8086:22dc] (rev 22)
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 310
    Region 0: Memory at d183b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device

00:14.0 USB controller [0c03]: Intel Corporation Device [8086:22b5] (rev 22) (prog-if 30 [XHCI])
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 115
    Region 0: Memory at d1800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:1a.0 Encryption controller [1080]: Intel Corporation Device [8086:2298] (rev 22)
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 311
    Region 0: Memory at d1700000 (32-bit, non-prefetchable) [size=1M]
    Region 1: Memory at d1600000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: mei_txe
    Kernel modules: mei_txe

00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:229c] (rev 22)
    Subsystem: Intel Corporation Device [8086:7270]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


```

```
---------------- lspci -vvnn results



Bus 002 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8153 
  bcdDevice           30.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           57
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               36mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               8
        bMaxBurst               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           98
    bNumInterfaces          2
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               36mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      6 Ethernet Networking
      bInterfaceProtocol      0 
      iInterface              5 
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC Ethernet:
        iMacAddress                      3 (??)
        bmEthernetStatistics    0x00000000
        wMaxSegmentSize               1514
        wNumberMCFilters            0x0000
        bNumberPowerFilters              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               8
        bMaxBurst               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              4 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               0

Bus 002 Device 002: ID 0bda:0401 Realtek Semiconductor Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0401 
  bcdDevice            1.11
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes           19
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               8
        bMaxBurst               0

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0

Bus 001 Device 004: ID 1c4f:0034 SiGma Micro 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1c4f SiGma Micro
  idProduct          0x0034 
  bcdDevice            1.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

Bus 001 Device 003: ID 1a2c:0021 China Resource Semico Co., Ltd Keyboard
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1a2c China Resource Semico Co., Ltd
  idProduct          0x0021 Keyboard
  bcdDevice            1.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
```


```
------------------ lsusb -v results


Bus 001 Device 002: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x5401 RTL 8153 USB 3.0 hub with gigabit ethernet
  bcdDevice            1.11
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
```

---

### Post by skanger on 2016-11-15
it doesn't look like 16.10 will install on this tablet. it can only boot from usb so i made a usb drive with unetbootin and it repeatedly froze. checksums were checked. iso is good..

didn't try nomodeset.

---

### Post by skanger on 2016-11-15
got it to start with nomodeset, but strangely double-clicking on the install icon does nothing. clicking on the shut-down icon also does nothing.

---

### Post by skanger on 2016-12-06
i'm back to windows 10 because i need to use this tablet, but i did upgrade to kernel 4.9-rc8 and can report that the tablet is a little less sluggish but still not usable. none of the desired hardware is active (wifi, touch screen, audio, etc.). linus told me to give this a try so i did. come on linus, you can do better than that!

---

### Post by skanger on 2016-12-07
forgot to mention....

while trying to boot my windows repair disk, ubuntu came back running  faster at 800x600 resolution. the speed was much closer to usable but the low resolution and lack of functions made it insufficient. i think everything these tablets need is in place already (aside from some drivers and firmware for full functioning). maybe a few more kernels ahead and all will be ready.

---

### Post by demokrit011 on 2017-04-15
Hi skanger,
just an idea but if you want to give it a try again there is some guidance how to setup linux Mint (which has common codebase & repos with ubuntu) on the chuwi Hi10 here [https://techtablets.com/forum/topic/linux-mint-on-a-chuwi-hi10-tablet/](https://techtablets.com/forum/topic/linux-mint-on-a-chuwi-hi10-tablet/)
with wifi/bluetooth drivers and anything. If you try again (perhabs with 17.04 ;-P) please leave a comment if/how it worked!

---

