---
title: "Kubuntu repeated crash after upgrade to 17.10"
date: 2017-11-10
forum: Installation &amp; Upgrades
---

### Post by jduns on 2017-11-10
Kubuntu 17.04 did not crash. This problem begins with Kubuntu 17.10. Crashes typically occur during PC downtime; I put the problem on [Ubuntu's Italian site]("https://forum.ubuntu-it.org/viewtopic.php?f=30&t=624105") but did not give me any answers.

I add something from /home/.xsession-errors (when appears "warning"). 

```
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = ksmserver path = /usr/bin pid = 1119
KCrash: Arguments: /usr/bin/ksmserver 
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi from kdeinit
Warning: connect() failed: : Connection refused
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi directly

[12:46:19.179 UTC] :0 : Warning: env says KDE is running but SNI unavailable -- check KDE_FULL_SESSION and XDG_CURRENT_DESKTOP
[12:46:20.424 UTC] :0 : Warning: The X11 connection broke (error 1). Did the X11 server die?

Xsession: X session started for duns at ven  3 nov 2017, 13.46.28, CET
localuser:duns being added to access control list
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1

dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
startkde: Starting up...
dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1

WARNING: Cannot find style "org.kde.desktop" - fallback: "/usr/lib/x86_64-linux-gnu/qt5/qml/QtQuick/Controls/Styles/Desktop"

WARNING: Cannot find style "org.kde.desktop" - fallback: "/usr/lib/x86_64-linux-gnu/qt5/qml/QtQuick/Controls/Styles/Desktop"

(kerneloops-applet:3870): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
(kerneloops-applet:3870): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(amule:3970): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
(amule:3970): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

[3973] WARNING: pipe error (143): Connection reset by peer: file /build/firefox-9cfKiA/firefox-56.0+build6/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 353
(/usr/lib/firefox/plugin-container:4402): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
(/usr/lib/firefox/plugin-container:4402): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(amule:3970): Gdk-WARNING **: GdkWindow 0xa0018b unexpectedly destroyed
QXcbConnection: XCB error: 3 (BadWindow), sequence: 40114, resource id: 52428867, major code: 18 (ChangeProperty), minor code: 0
QXcbConnection: XCB error: 3 (BadWindow), sequence: 40480, resource id: 46137354, major code: 18 (ChangeProperty), minor code: 0
QXcbConnection: XCB error: 3 (BadWindow), sequence: 40484, resource id: 37748740, major code: 18 (ChangeProperty), minor code: 0

(amule:3970): Gtk-CRITICAL **: IA__gtk_image_set_from_pixbuf: assertion 'GTK_IS_IMAGE (image)' failed
(amule:3970): Gtk-CRITICAL **: IA__gtk_widget_set_tooltip_text: assertion 'GTK_IS_WIDGET (widget)' failed
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.

(amule:1704): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
(amule:1704): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = ksmserver path = /usr/bin pid = 1205
KCrash: Arguments: /usr/bin/ksmserver 
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi from kdeinit
Warning: connect() failed: : Connection refused
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi directly
KCrash: Attempting to start /usr/bin/kdeinit5 from kdeinit
Warning: connect() failed: : Connection refused
KCrash: Attempting to start /usr/bin/kdeinit5 directly
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kdeinit5 path = /usr/bin pid = 1186
KCrash: Arguments: /usr/bin/kdeinit5 
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi from kdeinit
Warning: connect() failed: : Connection refused
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi directly
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/libexec/kf5/klauncher'
kdeinit5: Launched KLauncher, pid = 2458, result = 0
amule: Fatal IO error 0 (Success) on X server :0.
QXcbConnection: Could not connect to display :0
QXcbConnection: Could not connect to display :0
QXcbConnection: Could not connect to display :0
Unable to start Dr. Konqi
Re-raising signal for core dump handling.
kdeinit5: Communication error with launcher. Exiting!
Unable to start Dr. Konqi
Re-raising signal for core dump handling.

--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.

```

And something on my hardware. 

```
"duns@duns-novissimum:~$ sudo lshw
[sudo] password for duns: 
duns-novissimum             
    description: Desktop Computer
    product: MS-7A74 (Default string)
    vendor: MSI
    version: 1.0
    serial: Default string
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
     configuration: boot=normal chassis=desktop family=Default string  sku=Default string uuid=00000000-0000-0000-0000-4CCC6AD8709F
  *-core
       description: Motherboard
       product: B250M PRO-VD (MS-7A74)
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: H216419196
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.20
          date: 12/02/2016
          size: 64KiB
          capacity: 8128KiB
           capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd  int13floppy1200 int13floppy720 int13floppy2880 int5printscreen  int9keyboard int14serial int17printer acpi usb biosbootspecification  uefi
     *-memory
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR4 Synchronous 2400 MHz (0,4 ns)
             product: PSD48G240082
             vendor: 8502
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: 42
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 43
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 44
          slot: L3 Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz
          vendor: Intel Corp.
          physical id: 45
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-7100 CPU @ 3.90GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1200MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art  arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid  aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est  tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt  aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault  intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1  avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt  xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window  hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:123 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Skylake Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:df12f000-df12ffff
        *-usb
             description: USB controller
             product: 200 Series PCH USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:120 memory:df110000-df11ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-16-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Logitech
                   physical id: 4
                   bus info: usb@1:4
                   version: 64.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=90mA speed=1Mbit/s
              *-usb:2
                   description: Modem
                   product: SAMSUNG_Android
                   vendor: SAMSUNG
                   physical id: 5
                   bus info: usb@1:5
                   version: 4.00
                   serial: 364e30260a22503a
                   capabilities: usb-2.00 atcommands
                   configuration: driver=cdc_acm maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Generic USB device
                   product: USB WLAN
                   vendor: 802.11n
                   physical id: 6
                   bus info: usb@1:6
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.00
                   configuration: driver=rtl8192cu maxpower=500mA speed=480Mbit/s
              *-usb:4
                   description: Mass storage device
                   product: Cruzer Fit
                   vendor: SanDisk
                   physical id: 7
                   bus info: usb@1:7
                   logical name: scsi6
                   version: 1.27
                   serial: 4C530006050920107423
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer Fit
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdc
                      version: 1.27
                      serial: 4C530006050920107423
                      size: 7633MiB (8004MB)
                      capabilities: removable
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdc
                         size: 7633MiB (8004MB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=0009c02f
                       *-volume:0
                            description: Windows NTFS volume
                            physical id: 1
                            logical name: /dev/sdc1
                            version: 3.1
                            serial: 70a1-0761
                            size: 3396MiB
                            capacity: 3396MiB
                            capabilities: primary ntfs initialized
                            configuration: clustersize=4096 created=2016-06-07 17:37:19 filesystem=ntfs label=4giga state=clean
                       *-volume:1
                            description: Extended partition
                            physical id: 2
                            logical name: /dev/sdc2
                            size: 4226MiB
                            capacity: 4226MiB
                            capabilities: primary extended partitioned partitioned:extended
                          *-logicalvolume
                               description: EXT4 volume
                               vendor: Linux
                               physical id: 5
                               logical name: /dev/sdc5
                               version: 1.0
                               serial: efce76d0-a633-436c-a1a6-d7a52f5cc56e
                               size: 4226MiB
                               capacity: 4226MiB
                                capabilities: journaled extended_attributes large_files huge_files  dir_nlink extents ext4 ext2 initialized
                                configuration: created=2017-05-06 16:46:02 filesystem=ext4  label=neo-dati lastmountpoint=/media/duns/neo-dati modified=2017-11-02  21:33:15 mounted=2017-11-02 19:52:46 state=unknown
              *-usb:5
                   description: Mass storage device
                   product: Mass Storage Device
                   vendor: Generic
                   physical id: 8
                   bus info: usb@1:8
                   logical name: scsi7
                   version: 1.00
                   serial: 00000000000006
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Storage Device
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@7:0.0.0
                      logical name: /dev/sdd
                      version: 0.00
                      capabilities: removable
                      configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdd
              *-usb:6
                   description: Video
                   product: USB 2.0 Camera
                   vendor: Sonix Technology Co., Ltd.
                   physical id: a
                   bus info: usb@1:a
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=98mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-16-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: 200 Series PCH Thermal Subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:df12e000-df12efff
        *-communication
             description: Communication controller
             product: 200 Series PCH CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:124 memory:df12d000-df12dfff
        *-storage
             description: SATA controller
             product: 200 Series PCH SATA controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              resources: irq:121 memory:df128000-df129fff memory:df12c000-df12c0ff  ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32)  memory:df12b000-df12b7ff
        *-pci
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:df000000-df0fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 15
                serial: 4c:cc:6a:d8:70:9f
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
                configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full  firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.100 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
                resources: irq:122 ioport:e000(size=256) memory:df004000-df004fff memory:df000000-df003fff
        *-isa
             description: ISA bridge
             product: 200 Series PCH LPC Controller (B250)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: 200 Series PCH PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:df124000-df127fff
        *-multimedia
             description: Audio device
             product: 200 Series PCH HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:125 memory:df120000-df123fff memory:df100000-df10ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 200 Series PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df12a000-df12a0ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SHFS37A
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: BBF0
             serial: 50026B7773008927
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=48a2edfb
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: e6f0-1229
                size: 498MiB
                capacity: 500MiB
                capabilities: primary bootable ntfs initialized
                 configuration: clustersize=4096 created=2017-07-01 17:58:53  filesystem=ntfs label=Riservato per il sistema modified_by_chkdsk=true  mounted_on_nt4=true resize_log_file=true state=dirty  upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: faa9b955-76b0-3642-96fb-492243f532a9
                size: 42GiB
                capacity: 42GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2017-07-01 17:59:28 filesystem=ntfs state=clean
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 94ffcd90-e9a9-4431-8801-f3dfb83004a1
                size: 35GiB
                capacity: 35GiB
                 capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 19:28:04 filesystem=ext4  lastmountpoint=/media/duns/94ffcd90-e9a9-4431-8801-f3dfb83004a1  modified=2017-11-02 18:52:23 mounted=2017-11-02 16:38:14 state=clean
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /
                version: 1.0
                serial: 342bde2d-dcb7-474e-9a05-248f12665c12
                size: 33GiB
                capacity: 33GiB
                 capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-11-01 16:19:00 filesystem=ext4  lastmountpoint=/ modified=2017-11-03 07:05:21 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2017-11-03 07:05:22 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM010-2EP1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CC43
             serial: Z9A9KJ9Q
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=592bd6f8-5d87-4446-8ca7-46605d9b38b9 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /mnt/condivisa
                version: 3.1
                serial: 1a961a5e-64b5-bc4e-b2cf-6dbb6a0e1812
                size: 50GiB
                capacity: 50GiB
                capabilities: ntfs initialized
                 configuration: clustersize=4096 created=2017-07-04 22:23:26  filesystem=ntfs label=condivisa mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096  state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                logical name: /mnt/dati
                version: 1.0
                serial: 5e8b182e-a05e-46fb-a8fa-08eb498ffe06
                size: 10GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:28 filesystem=ext4 label=dati  lastmountpoint=/mnt/dati modified=2017-11-03 07:05:22 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2017-11-03  07:05:22 state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sdb3
                logical name: /mnt/settings
                version: 1.0
                serial: 5c91e4f6-a7ee-4a74-8c7d-8ea391a4cac3
                size: 2009MiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:30 filesystem=ext4  label=settings lastmountpoint=/mnt/settings modified=2017-11-03 07:05:23  mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered  mounted=2017-11-03 07:05:23 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sdb4
                logical name: /mnt/programs
                version: 1.0
                serial: 7b250ce3-15f4-42b5-9fed-5f42184da3c2
                size: 3090MiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:31 filesystem=ext4  label=programs lastmountpoint=/mnt/programs modified=2017-11-03 07:05:23  mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered  mounted=2017-11-03 07:05:23 state=mounted
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sdb5
                logical name: /mnt/zippati
                version: 1.0
                serial: a919f450-1e32-41fa-887c-dca44efcb8ab
                size: 10GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:33 filesystem=ext4  label=zippati lastmountpoint=/mnt/zippati modified=2017-11-03 07:05:23  mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered  mounted=2017-11-03 07:05:23 state=mounted
           *-volume:5
                description: EXT4 volume
                vendor: Linux
                physical id: 6
                bus info: scsi@1:0.0.0,6
                logical name: /dev/sdb6
                logical name: /mnt/musica
                version: 1.0
                serial: 2692905f-1773-4aa0-8bd2-f24795f3159a
                size: 43GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:35 filesystem=ext4 label=musica  lastmountpoint=/mnt/musica modified=2017-11-03 07:05:23  mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered  mounted=2017-11-03 07:05:23 state=mounted
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@1:0.0.0,7
                logical name: /dev/sdb7
                logical name: /mnt/video
                version: 1.0
                serial: d70838f5-9690-4740-8cd9-1c648cf60c83
                size: 801GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2017-07-04 22:23:38 filesystem=ext4 label=video  lastmountpoint=/mnt/video modified=2017-11-03 07:05:23 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2017-11-03  07:05:23 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@1:0.0.0,8
                logical name: /dev/sdb8
                version: 1
                serial: c01f6820-2e26-495a-8f6a-f639209e64b3
                size: 2999MiB
                capacity: 2999MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NSD1
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: LB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
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
       bus info: usb@1:6
       logical name: wlxc46e1f288735
       serial: c4:6e:1f:28:87:35
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rtl8192cu  driverversion=4.13.0-16-generic firmware=N/A ip=192.168.1.101 link=yes  multicast=yes wireless=IEEE 802.11"
```

Even having recently created a swap partition (7 gb with 8 gb of ram) crash has repeated.

Can you help me? Thank you

---

### Post by vasa1 on 2017-11-10
What if you don't run amule? Do you still get crashes?

---

### Post by jduns on 2017-11-10
yes

---

### Post by jduns on 2017-11-16
As I said, I have frequent crashes not only with kubuntu 17.10, but also with both pclinuxos desktop kde plasma 5 and with Neon 5.11.3. 
I observed with pclos coming out of the session, this message: "modemmanager is shut down".
Then I looked a bit on Google and found these commands, which I gave on kubuntu:
```
duns@duns-neos:~$ ps ax | grep Modem
  935 ?        Ssl    0:00 /usr/sbin/ModemManager
 7795 pts/1    S+     0:00 grep --color=auto Modem

duns@duns-neos:~$ sudo /usr/sbin/ModemManager --debug
[sudo] password for duns: 

ModemManager[7801]: <info>  [1510848508.697689] [main.c:158] main(): ModemManager (version 1.6.8) starting in system bus...
ModemManager[7801]: <debug> [1510848508.698251] [mm-sleep-monitor.c:245] mm_sleep_monitor_get(): create MMSleepMonitor singleton (0x55bf0aeeac90)
ModemManager[7801]: <debug> [1510848508.699369] [main.c:83] bus_acquired_cb(): Bus acquired, creating manager...
ModemManager[7801]: <debug> [1510848508.701558] [mm-plugin-manager.c:1559] load_plugins(): [plugin manager] looking for plugins in '/usr/lib/x86_64-linux-gnu/ModemManager'
ModemManager[7801]: <debug> [1510848508.703140] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Sierra (legacy)'
ModemManager[7801]: <debug> [1510848508.704974] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Via CBP7'
ModemManager[7801]: <debug> [1510848508.706232] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Longcheer'
ModemManager[7801]: <debug> [1510848508.706468] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'ZTE'
ModemManager[7801]: <debug> [1510848508.706935] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Ericsson MBM'
ModemManager[7801]: <debug> [1510848508.707607] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Cinterion'
ModemManager[7801]: <debug> [1510848508.708245] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Dell'
ModemManager[7801]: <debug> [1510848508.708543] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Nokia'
ModemManager[7801]: <debug> [1510848508.708623] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Sierra'
ModemManager[7801]: <debug> [1510848508.708739] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Novatel'
ModemManager[7801]: <debug> [1510848508.708830] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Samsung'
ModemManager[7801]: <debug> [1510848508.708923] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Altair LTE'
ModemManager[7801]: <debug> [1510848508.709029] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Linktop'
ModemManager[7801]: <debug> [1510848508.709126] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'SimTech'
ModemManager[7801]: <debug> [1510848508.709223] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Generic'
ModemManager[7801]: <debug> [1510848508.709428] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'MTK'
ModemManager[7801]: <debug> [1510848508.709610] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Nokia (Icera)'
ModemManager[7801]: <debug> [1510848508.709724] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Huawei'
ModemManager[7801]: <debug> [1510848508.709820] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Novatel LTE'
ModemManager[7801]: <debug> [1510848508.709897] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'AnyDATA'
ModemManager[7801]: <debug> [1510848508.709970] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Wavecom'
ModemManager[7801]: <debug> [1510848508.710093] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Option High-Speed'
ModemManager[7801]: <debug> [1510848508.710193] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Thuraya'
ModemManager[7801]: <debug> [1510848508.710275] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'X22X'
ModemManager[7801]: <debug> [1510848508.710347] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Pantech'
ModemManager[7801]: <debug> [1510848508.710458] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Option'
ModemManager[7801]: <debug> [1510848508.710563] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Telit'
ModemManager[7801]: <debug> [1510848508.710640] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Motorola'
ModemManager[7801]: <debug> [1510848508.710706] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Haier'
ModemManager[7801]: <debug> [1510848508.710785] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Iridium'
ModemManager[7801]: <debug> [1510848508.710796] [mm-plugin-manager.c:1609] load_plugins(): [plugin manager] successfully loaded 30 plugins
ModemManager[7801]: <warn>  [1510848508.711093] [main.c:123] name_lost_cb(): Could not acquire the 'org.freedesktop.ModemManager1' service name
ModemManager[7801]: <debug> [1510848508.711114] [mm-base-manager.c:842] set_property(): Stopping connection in object manager server
ModemManager[7801]: <info>  [1510848508.711788] [main.c:218] main(): ModemManager is shut down
ModemManager[7801]: <debug> [1510848508.711838] [mm-sleep-monitor.c:245] _singleton_instance_weak_ref_cb(): disposing MMSleepMonitor singleton (0x55bf0aeeac90)

```

And in Pclos: 
```
[duns@duns-neos ~]$ ps ax | grep Modem
 1232 ?        Sl     0:00 /usr/sbin/ModemManager
 4769 pts/1    S+     0:00 grep --color Modem
[duns@duns-neos ~]$ su
Password: 
[root@duns-neos duns]# /usr/sbin/ModemManager --debug
ModemManager[4810]: <info>  [1510849166.098760] [main.c:158] main(): ModemManager (version 1.6.4) starting in system bus...
ModemManager[4810]: <debug> [1510849166.099884] [main.c:83] bus_acquired_cb(): Bus acquired, creating manager...
ModemManager[4810]: <debug> [1510849166.100118] [mm-plugin-manager.c:1559] load_plugins(): [plugin manager] looking for plugins in '/usr/lib64/ModemManager'
ModemManager[4810]: <debug> [1510849166.100259] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Via CBP7'
ModemManager[4810]: <debug> [1510849166.100332] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Dell'
ModemManager[4810]: <debug> [1510849166.100391] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Option High-Speed'
ModemManager[4810]: <debug> [1510849166.100448] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Cinterion'
ModemManager[4810]: <debug> [1510849166.100502] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Novatel'
ModemManager[4810]: <debug> [1510849166.100550] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Novatel LTE'
ModemManager[4810]: <debug> [1510849166.100594] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Nokia'
ModemManager[4810]: <debug> [1510849166.100642] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'X22X'
ModemManager[4810]: <debug> [1510849166.100708] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Option'
ModemManager[4810]: <debug> [1510849166.100762] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Wavecom'
ModemManager[4810]: <debug> [1510849166.100812] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'AnyDATA'
ModemManager[4810]: <debug> [1510849166.100877] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Motorola'
ModemManager[4810]: <debug> [1510849166.100926] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Generic'
ModemManager[4810]: <debug> [1510849166.100974] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Haier'
ModemManager[4810]: <debug> [1510849166.101022] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Sierra'
ModemManager[4810]: <debug> [1510849166.101083] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Altair LTE'
ModemManager[4810]: <debug> [1510849166.101144] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Samsung'
ModemManager[4810]: <debug> [1510849166.101198] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Longcheer'
ModemManager[4810]: <debug> [1510849166.101246] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Linktop'
ModemManager[4810]: <debug> [1510849166.101297] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'MTK'
ModemManager[4810]: <debug> [1510849166.101347] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Pantech'
ModemManager[4810]: <debug> [1510849166.101399] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Iridium'
ModemManager[4810]: <debug> [1510849166.101460] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Telit'
ModemManager[4810]: <debug> [1510849166.101519] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Thuraya'
ModemManager[4810]: <debug> [1510849166.101580] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Ericsson MBM'
ModemManager[4810]: <debug> [1510849166.101645] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Nokia (Icera)'
ModemManager[4810]: <debug> [1510849166.101710] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'ZTE'
ModemManager[4810]: <debug> [1510849166.101763] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'SimTech'
ModemManager[4810]: <debug> [1510849166.101828] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Huawei'
ModemManager[4810]: <debug> [1510849166.101889] [mm-plugin-manager.c:1584] load_plugins(): [plugin manager] loaded plugin 'Sierra (legacy)'
ModemManager[4810]: <debug> [1510849166.101897] [mm-plugin-manager.c:1609] load_plugins(): [plugin manager] successfully loaded 30 plugins
ModemManager[4810]: <warn>  [1510849166.102122] [main.c:123] name_lost_cb(): Could not acquire the 'org.freedesktop.ModemManager1' service name
ModemManager[4810]: <debug> [1510849166.102135] [mm-base-manager.c:849] set_property(): Stopping connection in object manager server
ModemManager[4810]: <info>  [1510849166.102527] [main.c:218] main(): ModemManager is shut down 
``` 

Perhaps the cause of the crashes is modemmager?
Thank you

note that at this time the modem is running, although the message at the terminal is that "modemmanager is shut down"

---

