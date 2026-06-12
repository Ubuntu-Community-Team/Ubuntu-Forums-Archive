---
title: "Drivers problems with Aspire 1410"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by eu-ericruiz on 2015-02-03
Hi guys!

Today I Decided to install Lubuntu 14.04 LTS on my Acer Aspire 1410...
Well Livepen made, easy! Everything fine running from livepen...
But after all instalation process and reboot, wireless don't work, touchpad too... poor screen resolution.

Well, why running from livepen it worked fine and after instalation it simple don't work anymore, it doesn't make any sense for me.

Is there a way to fix It? *(I know is possible, but I don't know how)*
Is possible to run from livepen again and take working drivers from live to HDD instalation??

Thanks all.
English is not my native language, sorry for that.
Best Regards.

**[EDIT] Added hardware info got from live and hdd**. 
[B]
NOTE: [/B]nothing has returned from _**lsmod**_ in hdd, but from live everthing looks good.

This is some information from live:
```

[FONT=courier new]###
### Release Info ###
###
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
NAME="Ubuntu"
VERSION="14.04.1 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.1 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


###
### lspci ###
###
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
01:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 5100


###
### lsmod ###
###
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
zram                   18478  1 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
dm_crypt               23177  0 
snd_hda_intel          52355  1 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
acerhdf                18738  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
dm_multipath           22873  0 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               80885  0 
kvm                   451511  0 
videobuf2_vmalloc      13216  1 uvcvideo
scsi_dh                14882  1 dm_multipath
snd_rawmidi            30144  1 snd_seq_midi
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12608  2 
videobuf2_core         40664  1 uvcvideo
iwldvm                232285  0 
mac80211              630653  1 iwldvm
videodev              134688  2 uvcvideo,videobuf2_core
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
iwlwifi               169932  1 iwldvm
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13462  0 
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
snd                    69238  13  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
squashfs               48362  1 
overlayfs              27916  1 
nls_iso8859_1          12713  1 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
usb_storage            62209  1 
i915                  783805  2 
i2c_algo_bit           13413  1 i915
psmouse               106678  0 
drm_kms_helper         53081  1 i915
atl1c                  46086  0 
drm                   303102  3 i915,drm_kms_helper
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi


###
### lshw ###
###
lubuntu
    description: Computer
    product: Aspire 1410 (Montevina_Fab)
    vendor: Acer
    version: v0.3108
    serial: LXSAB0X0739310B14A2500
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 ldt16 vsyscall32
    configuration: boot=normal family=Intel_Mobile sku=Montevina_Fab uuid=A90543DB-C3F4-4D38-9D66-D09C9CF2A049
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: v0.3108
          date: 06/25/2009
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect  socketedrom edd int13floppynec int13floppytoshiba int13floppy360  int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video  acpi usb
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Solo CPU    U3500  @ 1.40GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Solo CPU    U3500  @ 1.40GHz
          slot: CPU
          size: 1400MHz
          capacity: 1400MHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts  rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3  cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority  cpufreq
        *-cache:0
             description: L2 cache
             physical id: 17
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 19
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 18
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T5663EH3-CE6
             vendor: Samsung
             physical id: 0
             serial: 9560BBE8
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: DIMM2
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:90000000-903fffff memory:80000000-8fffffff ioport:3100(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:92400000-924fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3080(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:94504400-945047ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:94500000-94503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:93500000-944fffff ioport:90400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c0
                serial: 00:26:9e:08:05:f6
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd  autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes  port=twisted pair
                resources: irq:45 memory:93500000-9353ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:92500000-934fffff ioport:91400000(size=16777216)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fb:65:35:b6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi  driverversion=3.13.0-32-generic firmware=8.83.5.1 build 33692  ip=192.168.25.3 latency=0 link=yes multicast=yes wireless=IEEE  802.11abgn
                resources: irq:43 memory:92500000-92501fff
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3060(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3040(size=32)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3020(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:94504000-945043ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:30f8(size=8) ioport:3114(size=4)  ioport:30f0(size=8) ioport:3110(size=4) ioport:30d0(size=16)  ioport:30c0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:94504800-945048ff ioport:3000(size=32)
        *-ide:1
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:30e8(size=8) ioport:310c(size=4)  ioport:30e0(size=8) ioport:3108(size=4) ioport:30b0(size=16)  ioport:30a0(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54322
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: FBEO
             serial: 090528FB0D0CLJCP7DZC
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=52d29fa7
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 9e2998e0-fe6a-49a3-8906-7dd79401726d
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink extents ext4 ext2  initialized
                configuration: created=2015-02-04 13:28:57  filesystem=ext4 lastmountpoint=/ modified=2015-02-04 13:41:13  mounted=2015-02-04 13:41:14 state=clean
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: ab833cd5-f5b7-448b-8997-6d5fdc966365
                size: 4GiB
                capacity: 4GiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /mnt
                version: 1.0
                serial: e75446ef-19ac-4f4f-96c0-a4079461bc8f
                size: 214GiB
                capacity: 214GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2013-03-09 04:46:01  filesystem=ext3 lastmountpoint=/mnt modified=2015-02-04 14:03:25  mount.fstype=ext3 mount.options=rw,relatime,data=ordered  mounted=2015-02-04 14:03:25 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@2:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 1918MiB (2011MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=00059bb0
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: 1f26-144c
                size: 1916MiB
                capacity: 1917MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=New Volume  mount.fstype=vfat  mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro  state=mounted
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define4
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define5
       serial: OEM_Define2
       capacity: 75mWh
[/FONT]
```


And here is informations from hdd:
```



###
### Release Info ###
###
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
NAME="Ubuntu"
VERSION="14.04.1 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.1 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


###
### lspci ###
###
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
01:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 5100


###
### lsmod ###
###
Module                  Size  Used by


###
### lshw ###
###
computer-pc
    descrição: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2013-04-07 17:30+0000Last-Translator: Neliton Pereira Jr. <nelitonpjr@gmail.com>Language-Team: Brazilian Portuguese <pt_BR@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-04-10 12:53+0000X-Generator: Launchpad (build 16976)
    produto: Aspire 1410 (Montevina_Fab)
    fabricante: Acer
    versão: v0.3108
    serial: LXSAB0X0739310B14A2500
    largura: 64 bits
    capacidades: smbios-2.6 dmi-2.6 vsyscall32
    configuração: boot=normal family=Intel_Mobile sku=Montevina_Fab uuid=A90543DB-C3F4-4D38-9D66-D09C9CF2A049
  *-core
       descrição: Placa-mãe
       produto: Base Board Product Name
       fabricante: Acer
       ID físico: 0
       versão: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          descrição: BIOS
          fabricante: INSYDE
          ID físico: 0
          versão: v0.3108
          date: 06/25/2009
          tamanho: 1MiB
          capacidade: 1984KiB
          capacidades: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          descrição: CPU
          produto: Intel(R) Core(TM)2 Solo CPU    U3500  @ 1.40GHz
          fabricante: Intel Corp.
          ID físico: 16
          informações do barramento: cpu@0
          versão: Intel(R) Core(TM)2 Solo CPU    U3500  @ 1.40GHz
          slot: CPU
          tamanho: 1400MHz
          capacidade: 1400MHz
          largura: 64 bits
          clock: 800MHz
          capacidades: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx x86-64 constant_tsc up arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             descrição: L2 cache
             ID físico: 17
             slot: Unknown
             tamanho: 3MiB
             capacidade: 3MiB
             capacidades: synchronous internal write-back unified
        *-cache:1
             descrição: L1 cache
             ID físico: 19
             slot: Unknown
             tamanho: 32KiB
             capacidade: 32KiB
             capacidades: synchronous internal write-back data
     *-cache
          descrição: L1 cache
          ID físico: 18
          slot: Unknown
          tamanho: 32KiB
          capacidade: 32KiB
          capacidades: synchronous internal write-back instruction
     *-memory
          descrição: Memória do sistema
          ID físico: 1a
          slot: Placa do sistema ou placa-mãe
          tamanho: 2GiB
        *-bank:0
             descrição: SODIMM DDR2 Síncrono 667 MHz (1,5 ns)
             produto: M4 70T5663EH3-CE6
             fabricante: Samsung
             ID físico: 0
             serial: 9560BBE8
             slot: DIMM0
             tamanho: 2GiB
             largura: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             descrição: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2013-04-07 17:30+0000Last-Translator: Neliton Pereira Jr. <nelitonpjr@gmail.com>Language-Team: Brazilian Portuguese <pt_BR@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-04-10 12:53+0000X-Generator: Launchpad (build 16976) [vazio]
             ID físico: 1
             slot: DIMM2
     *-pci
          descrição: Host bridge
          produto: Mobile 4 Series Chipset Memory Controller Hub
          fabricante: Intel Corporation
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 07
          largura: 32 bits
          clock: 33MHz
          configuração: driver=agpgart-intel
          recursos: irq:0
        *-display:0 DISPONÍVEL
             descrição: VGA compatible controller
             produto: Mobile 4 Series Chipset Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2
             informações do barramento: pci@0000:00:02.0
             versão: 07
             largura: 64 bits
             clock: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list
             configuração: latency=0
             recursos: memória:90000000-903fffff memória:80000000-8fffffff porta de E/S:3100(tamanho=8)
        *-display:1 DISPONÍVEL
             descrição: Display controller
             produto: Mobile 4 Series Chipset Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2.1
             informações do barramento: pci@0000:00:02.1
             versão: 07
             largura: 64 bits
             clock: 33MHz
             capacidades: pm bus_master cap_list
             configuração: latency=0
             recursos: memória:92400000-924fffff
        *-usb:0
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB UHCI Controller #4
             fabricante: Intel Corporation
             ID físico: 1a
             informações do barramento: pci@0000:00:1a.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master cap_list
             configuração: driver=uhci_hcd latency=0
             recursos: irq:16 porta de E/S:3080(tamanho=32)
        *-usb:1
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB2 EHCI Controller #2
             fabricante: Intel Corporation
             ID físico: 1a.7
             informações do barramento: pci@0000:00:1a.7
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci_hcd latency=0
             recursos: irq:19 memória:94504400-945047ff
        *-multimedia DISPONÍVEL
             descrição: Audio device
             produto: 82801I (ICH9 Family) HD Audio Controller
             fabricante: Intel Corporation
             ID físico: 1b
             informações do barramento: pci@0000:00:1b.0
             versão: 03
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: latency=0
             recursos: memória:94500000-94503fff
        *-pci:0
             descrição: PCI bridge
             produto: 82801I (ICH9 Family) PCI Express Port 1
             fabricante: Intel Corporation
             ID físico: 1c
             informações do barramento: pci@0000:00:1c.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:40 porta de E/S:2000(tamanho=4096) memória:93500000-944fffff porta de E/S:90400000(tamanho=16777216)
           *-network DISPONÍVEL
                descrição: Ethernet controller
                produto: AR8131 Gigabit Ethernet
                fabricante: Qualcomm Atheros
                ID físico: 0
                informações do barramento: pci@0000:01:00.0
                versão: c0
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress vpd bus_master cap_list
                configuração: latency=0
                recursos: memória:93500000-9353ffff porta de E/S:2000(tamanho=128)
        *-pci:1
             descrição: PCI bridge
             produto: 82801I (ICH9 Family) PCI Express Port 4
             fabricante: Intel Corporation
             ID físico: 1c.3
             informações do barramento: pci@0000:00:1c.3
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:41 porta de E/S:1000(tamanho=4096) memória:92500000-934fffff porta de E/S:91400000(tamanho=16777216)
           *-network DISPONÍVEL
                descrição: Network controller
                produto: WiFi Link 5100
                fabricante: Intel Corporation
                ID físico: 0
                informações do barramento: pci@0000:02:00.0
                versão: 00
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list
                configuração: latency=0
                recursos: memória:92500000-92501fff
        *-usb:2
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB UHCI Controller #1
             fabricante: Intel Corporation
             ID físico: 1d
             informações do barramento: pci@0000:00:1d.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master cap_list
             configuração: driver=uhci_hcd latency=0
             recursos: irq:23 porta de E/S:3060(tamanho=32)
        *-usb:3
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB UHCI Controller #2
             fabricante: Intel Corporation
             ID físico: 1d.1
             informações do barramento: pci@0000:00:1d.1
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master cap_list
             configuração: driver=uhci_hcd latency=0
             recursos: irq:19 porta de E/S:3040(tamanho=32)
        *-usb:4
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB UHCI Controller #3
             fabricante: Intel Corporation
             ID físico: 1d.2
             informações do barramento: pci@0000:00:1d.2
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master cap_list
             configuração: driver=uhci_hcd latency=0
             recursos: irq:16 porta de E/S:3020(tamanho=32)
        *-usb:5
             descrição: USB controller
             produto: 82801I (ICH9 Family) USB2 EHCI Controller #1
             fabricante: Intel Corporation
             ID físico: 1d.7
             informações do barramento: pci@0000:00:1d.7
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci_hcd latency=0
             recursos: irq:23 memória:94504000-945043ff
        *-pci:2
             descrição: PCI bridge
             produto: 82801 Mobile PCI Bridge
             fabricante: Intel Corporation
             ID físico: 1e
             informações do barramento: pci@0000:00:1e.0
             versão: 93
             largura: 32 bits
             clock: 33MHz
             capacidades: pci subtractive_decode bus_master cap_list
        *-isa
             descrição: ISA bridge
             produto: ICH9M-E LPC Interface Controller
             fabricante: Intel Corporation
             ID físico: 1f
             informações do barramento: pci@0000:00:1f.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: isa bus_master cap_list
             configuração: latency=0
        *-ide:0
             descrição: IDE interface
             produto: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             fabricante: Intel Corporation
             ID físico: 1f.2
             informações do barramento: pci@0000:00:1f.2
             nome lógico: scsi0
             versão: 03
             largura: 32 bits
             clock: 66MHz
             capacidades: ide pm bus_master cap_list emulated
             configuração: driver=ata_piix latency=0
             recursos: irq:19 porta de E/S:30f8(tamanho=8) porta de E/S:3114(tamanho=4) porta de E/S:30f0(tamanho=8) porta de E/S:3110(tamanho=4) porta de E/S:30d0(tamanho=16) porta de E/S:30c0(tamanho=16)
           *-disk
                descrição: ATA Disk
                produto: Hitachi HTS54322
                fabricante: Hitachi
                ID físico: 0.0.0
                informações do barramento: scsi@0:0.0.0
                nome lógico: /dev/sda
                versão: FBEO
                serial: 090528FB0D0CLJCP7DZC
                tamanho: 232GiB (250GB)
                capacidades: partitioned partitioned:dos
                configuração: ansiversion=5 sectorsize=512 signature=52d29fa7
              *-volume:0
                   descrição: volume EXT4
                   fabricante: Linux
                   ID físico: 1
                   informações do barramento: scsi@0:0.0.0,1
                   nome lógico: /dev/sda1
                   nome lógico: /
                   versão: 1.0
                   serial: 9e2998e0-fe6a-49a3-8906-7dd79401726d
                   tamanho: 14GiB
                   capacidade: 14GiB
                   capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuração: created=2015-02-04 11:28:57 filesystem=ext4 lastmountpoint=/target modified=2015-02-04 11:41:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2015-02-04 11:41:14 state=mounted
              *-volume:1
                   descrição: Linux swap volume
                   ID físico: 2
                   informações do barramento: scsi@0:0.0.0,2
                   nome lógico: /dev/sda2
                   versão: 1
                   serial: ab833cd5-f5b7-448b-8997-6d5fdc966365
                   tamanho: 4GiB
                   capacidade: 4GiB
                   capacidades: primary nofs swap initialized
                   configuração: filesystem=swap pagesize=4096
              *-volume:2
                   descrição: volume EXT3
                   fabricante: Linux
                   ID físico: 3
                   informações do barramento: scsi@0:0.0.0,3
                   nome lógico: /dev/sda3
                   nome lógico: /mnt
                   versão: 1.0
                   serial: e75446ef-19ac-4f4f-96c0-a4079461bc8f
                   tamanho: 214GiB
                   capacidade: 214GiB
                   capacidades: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuração: created=2013-03-09 01:46:01 filesystem=ext3 lastmountpoint=/mnt modified=2015-02-04 11:42:51 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered mounted=2015-02-04 11:42:51 state=mounted
        *-serial DISPONÍVEL
             descrição: SMBus
             produto: 82801I (ICH9 Family) SMBus Controller
             fabricante: Intel Corporation
             ID físico: 1f.3
             informações do barramento: pci@0000:00:1f.3
             versão: 03
             largura: 64 bits
             clock: 33MHz
             configuração: latency=0
             recursos: memória:94504800-945048ff porta de E/S:3000(tamanho=32)
        *-ide:1
             descrição: IDE interface
             produto: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             fabricante: Intel Corporation
             ID físico: 1f.5
             informações do barramento: pci@0000:00:1f.5
             versão: 03
             largura: 32 bits
             clock: 66MHz
             capacidades: ide pm bus_master cap_list
             configuração: driver=ata_piix latency=0
             recursos: irq:19 porta de E/S:30e8(tamanho=8) porta de E/S:310c(tamanho=4) porta de E/S:30e0(tamanho=8) porta de E/S:3108(tamanho=4) porta de E/S:30b0(tamanho=16) porta de E/S:30a0(tamanho=16)
  *-power DISPONÍVEL
       descrição: OEM_Define1
       produto: OEM_Define4
       fabricante: OEM_Define2
       ID físico: 1
       versão: OEM_Define5
       serial: OEM_Define2
       capacidade: 75mWh

```

---

### Post by eu-ericruiz on 2015-02-04
Hardware info update: from hdd and livepen to compare it: lsmod don't show nothing on hdd instalation.

---

### Post by mörgæs on 2015-02-04
From time to time the Intel Mobile 4 Series has given problems for Buntu (some googling will show you). I would try a fresh install of Lubuntu 14.10 with wired internet access and see if it works better.


Is there any particular reason that you use ext3 formatting?

---

### Post by eu-ericruiz on 2015-02-04
> **mörgæs said:**
> From time to time the Intel Mobile 4 Series has given problems for Buntu (some googling will show you). I would try a fresh install of Lubuntu 14.10 with wired internet access and see if it works better.


Is there any particular reason that you use ext3 formatting?

:p Thank you **mörgæs**!

No special reason for ext3, that is just my old /home, I will migrate that to ext4. Actualy is not mounted on hdd instalation yet ;).
Good point! I will try 14.10, then I will post results here. I got 14.04 because is LTS, nevermind.

---

### Post by mörgæs on 2015-02-04
When you do I suggest that you create a new /home, leaving the old one unmounted to begin with.

---

### Post by eu-ericruiz on 2015-02-05
Hey!

Well, I've tried Lubuntu 14.10 but I had exactly same problems...

Then, I downloaded Debian 7 (Wheezy) LXDE iso, unetbootin, installation _**WIRED**_, and... tadam! Working pretty well. Actually I had wireless driver problem, with installation process warned me. After installation, I followed _[this instructions]("https://wiki.debian.org/iwlwifi")_ and wireless card is running shinny. 

:confused: I can't explain why, but at first try with Debian, I was unconnected to internet, the instalations process fails, no grub instalation, etc...

Well, this is it! For now I will continue with Debian, one day, when it will be possible, I came back to Buntu.

:guitar:

Thank you **mörgæs**.
Sorry my bad english, I did my best.
Best Regards.

---

