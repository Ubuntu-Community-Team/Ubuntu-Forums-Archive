---
title: "Natty CD works fine, upgrade or fresh install does not"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by rquint on 2011-05-04
I've run into a problem upgrading from 10.10 to 11.04.  Running the LIVE CD everything appears to work fine but when I upgraded (and later from a fresh install) the first boot into the new system ran fine, but in the next boot I got a message that my hardware didn't support Unity and I got the old UI.  When I tried to shut down I ended up with an almost blank screen (a few randomly coloured pixels) and the machine hung. Here's my output from sudo lshw.  The same happened with both the 64 bit and 32 bit CDs.

```

wrobi
description: Desktop Computer
product: System Product Name
vendor: System manufacturer
version: System Version
serial: System Serial Number
width: 64 bits
capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
configuration: boot=normal chassis=desktop
*-core
description: Motherboard
product: A8N-E
vendor: ASUSTeK Computer INC.
physical id: 0
version: 2.XX
serial: 123456789000
*-firmware
description: BIOS
vendor: Phoenix Technologies, LTD
physical id: 0
version: ASUS A8N-E ACPI BIOS Revision 1013 (04/07/2006)
size: 128KiB
capacity: 448KiB
capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
*-cpu
description: CPU
product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
vendor: Advanced Micro Devices [AMD]
physical id: 3
bus info: cpu@0
version: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
slot: Socket 939
size: 2400MHz
capacity: 3700MHz
width: 64 bits
clock: 200MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
*-cache:0
description: L1 cache
physical id: a
slot: L1 Cache
size: 128KiB
capacity: 128KiB
capabilities: synchronous internal write-back data
*-cache:1
description: L2 cache
physical id: b
slot: L2 Cache
size: 1MiB
capacity: 1MiB
capabilities: synchronous internal write-back unified
*-memory:0
description: System Memory
physical id: 3c
slot: System board or motherboard
size: 3GiB
*-bank:0
description: DIMM 333 MHz (3.0 ns)
product: None
vendor: None
physical id: 0
serial: None
slot: A0
size: 1GiB
width: 64 bits
clock: 333MHz (3.0ns)
*-bank:1
description: DIMM 333 MHz (3.0 ns)
product: None
vendor: None
physical id: 1
serial: None
slot: A1
size: 512MiB
width: 64 bits
clock: 333MHz (3.0ns)
*-bank:2
description: DIMM 333 MHz (3.0 ns)
product: None
vendor: None
physical id: 2
serial: None
slot: A2
size: 1GiB
width: 64 bits
clock: 333MHz (3.0ns)
*-bank:3
description: DIMM 333 MHz (3.0 ns)
product: None
vendor: None
physical id: 3
serial: None
slot: A3
size: 512MiB
width: 64 bits
clock: 333MHz (3.0ns)
*-memory:1 UNCLAIMED
description: Memory controller
product: CK804 Memory Controller
vendor: nVidia Corporation
physical id: 4
bus info: pci@0000:00:00.0
version: a3
width: 32 bits
clock: 66MHz (15.2ns)
capabilities: ht bus_master cap_list
configuration: latency=0
*-isa
description: ISA bridge
product: CK804 ISA Bridge
vendor: nVidia Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: isa bus_master
configuration: latency=0
*-serial
description: SMBus
product: CK804 SMBus
vendor: nVidia Corporation
physical id: 1.1
bus info: pci@0000:00:01.1
version: a2
width: 32 bits
clock: 66MHz
capabilities: pm cap_list
configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
resources: irq:11 ioport:e400(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
*-usb:0
description: USB Controller
product: CK804 USB Controller
vendor: nVidia Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: a2
width: 32 bits
clock: 66MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
resources: irq:20 memory:d4004000-d4004fff
*-usb:1
description: USB Controller
product: CK804 USB Controller
vendor: nVidia Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: a3
width: 32 bits
clock: 66MHz
capabilities: debug pm ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
resources: irq:21 memory:d4005000-d40050ff
*-multimedia
description: Multimedia audio controller
product: CK804 AC'97 Audio Controller
vendor: nVidia Corporation
physical id: 5
bus info: pci@0000:00:04.0
version: a2
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d4003000-d4003fff
*-ide:0
description: IDE interface
product: CK804 IDE
vendor: nVidia Corporation
physical id: 6
bus info: pci@0000:00:06.0
logical name: scsi1
version: f2
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
resources: irq:0 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:f000(size=16)
*-cdrom
description: DVD writer
product: DVDR PX-708A
vendor: PLEXTOR
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.12
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 status=nodisc
*-ide:1
description: IDE interface
product: CK804 Serial ATA Controller
vendor: nVidia Corporation
physical id: 7
bus info: pci@0000:00:07.0
version: f3
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list
configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
resources: irq:23 ioport:9f0(size= ioport:bf0(size=4) ioport:970(size= ioport:b70(size=4) ioport:d800(size=16) memory:d4002000-d4002fff
*-ide:2
description: IDE interface
product: CK804 Serial ATA Controller
vendor: nVidia Corporation
physical id: 8
bus info: pci@0000:00:08.0
logical name: scsi5
version: f3
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
resources: irq:22 ioport:9e0(size= ioport:be0(size=4) ioport:960(size= ioport:b60(size=4) ioport:c400(size=16) memory:d4001000-d4001fff
*-disk
description: ATA Disk
product: Maxtor 6B200M0
vendor: Maxtor
physical id: 0.0.0
bus info: scsi@5:0.0.0
logical name: /dev/sdb
version: BANC
serial: B427A4KH
size: 186GiB (200GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=0001fd8a
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@5:0.0.0,1
logical name: /dev/sdb1
logical name: /
version: 1.0
serial: a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
size: 178GiB
capacity: 178GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration: created=2011-05-04 12:59:08 filesystem=ext4 lastmountpoint=/&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-05-04 13:13:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-04 15:25:18 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@5:0.0.0,2
logical name: /dev/sdb2
size: 7777MiB
capacity: 7777MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sdb5
capacity: 7777MiB
capabilities: nofs
*-pci:0
description: PCI bridge
product: CK804 PCI Bridge
vendor: nVidia Corporation
physical id: 9
bus info: pci@0000:00:09.0
version: a2
width: 32 bits
clock: 66MHz
capabilities: pci subtractive_decode bus_master
resources: memory:d2000000-d3ffffff
*-usb:0
description: USB Controller
product: USB 1.1 Controller
vendor: ALi Corporation
physical id: 6
bus info: pci@0000:05:06.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=ohci_hcd latency=32 maxlatency=80
resources: irq:17 memory:d3013000-d3013fff
*-usb:1
description: USB Controller
product: USB 1.1 Controller
vendor: ALi Corporation
physical id: 6.1
bus info: pci@0000:05:06.1
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=ohci_hcd latency=32 maxlatency=80
resources: irq:17 memory:d3014000-d3014fff
*-usb:2
description: USB Controller
product: USB 1.1 Controller
vendor: ALi Corporation
physical id: 6.2
bus info: pci@0000:05:06.2
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=ohci_hcd latency=32 maxlatency=80
resources: irq:17 memory:d3010000-d3010fff
*-usb:3
description: USB Controller
product: USB 2.0 Controller
vendor: ALi Corporation
physical id: 6.3
bus info: pci@0000:05:06.3
version: 01
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci_hcd latency=32 maxlatency=80
resources: irq:16 memory:d3011000-d30110ff
*-firewire
description: FireWire (IEEE 1394)
product: M5253 P1394 OHCI 1.1 Controller
vendor: ALi Corporation
physical id: 6.4
bus info: pci@0000:05:06.4
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm ohci bus_master cap_list rom
configuration: driver=firewire_ohci latency=32 maxlatency=3
resources: irq:18 memory:d3012000-d30127ff memory:d2000000-d200ffff
*-network
description: Wireless interface
product: Atheros AR5001X+ Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 7
bus info: pci@0000:05:07.0
logical name: wlan0
version: 01
serial: 00:1b:2f:ce:34:9e
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.6 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:d3000000-d300ffff
*-bridge
description: Ethernet interface
product: CK804 Ethernet Controller
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a3
serial: 00:13:d4:b4:44:f6
capacity: 1000000000
width: 32 bits
clock: 66MHz
capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: irq:23 memory:d4000000-d4000fff ioport:b000(size=
*-pci:1
description: PCI bridge
product: CK804 PCIE Bridge
vendor: nVidia Corporation
physical id: b
bus info: pci@0000:00:0b.0
version: a3
width: 32 bits
clock: 33MHz
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:40
*-pci:2
description: PCI bridge
product: CK804 PCIE Bridge
vendor: nVidia Corporation
physical id: c
bus info: pci@0000:00:0c.0
version: a3
width: 32 bits
clock: 33MHz
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:41
*-pci:3
description: PCI bridge
product: CK804 PCIE Bridge
vendor: nVidia Corporation
physical id: d
bus info: pci@0000:00:0d.0
version: a3
width: 32 bits
clock: 33MHz
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:42
*-pci:4
description: PCI bridge
product: CK804 PCIE Bridge
vendor: nVidia Corporation
physical id: e
bus info: pci@0000:00:0e.0
version: a3
width: 32 bits
clock: 33MHz
capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:43 ioport:a000(size=4096) memory:d0000000-d1ffffff ioport:c0000000(size=268435456)
*-display:0
description: VGA compatible controller
product: R430 [Radeon X800 (PCIE)]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:44 memory:c0000000-cfffffff memory:d1000000-d100ffff ioport:a000(size=256) memory:d0000000-d001ffff
*-display:1 UNCLAIMED
description: Display controller
product: R430 [Radeon X800] (PCIE) (Secondary)
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@0000:01:00.1
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress cap_list
configuration: latency=0
resources: memory:d1010000-d101ffff
*-pci:5
description: Host bridge
product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
vendor: Advanced Micro Devices [AMD]
physical id: 100
bus info: pci@0000:00:18.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:6
description: Host bridge
product: K8 [Athlon64/Opteron] Address Map
vendor: Advanced Micro Devices [AMD]
physical id: 101
bus info: pci@0000:00:18.1
version: 00
width: 32 bits
clock: 33MHz
*-pci:7
description: Host bridge
product: K8 [Athlon64/Opteron] DRAM Controller
vendor: Advanced Micro Devices [AMD]
physical id: 102
bus info: pci@0000:00:18.2
version: 00
width: 32 bits
clock: 33MHz
*-pci:8
description: Host bridge
product: K8 [Athlon64/Opteron] Miscellaneous Control
vendor: Advanced Micro Devices [AMD]
physical id: 103
bus info: pci@0000:00:18.3
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=k8temp
resources: irq:0
*-scsi
physical id: f
bus info: usb@1:3
logical name: scsi2
capabilities: emulated scsi-host
configuration: driver=usb-storage
*-disk
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sda

```

---

### Post by rquint on 2011-05-10
A follow up that someone may be able to explain.  The following behaviour is consistent and reproducible.

If I boot into recovery mode and then reboot, either hard or soft works as expected, into the normal mode I get the new Unity UI and shutdown works correctly.  However if I reboot again I get the old interface and shutdown and logout bring an almost blank screen and the machine hangs.  

Are there configuration files that are modified during boot that can cause this behaviour?

---

### Post by Hedgehog1 on 2011-05-11
First - Please modify/edit your first post and place that giant block of text inside these statements: 

[noparse]```
 your text here 
```[/noparse] 

That gives us this:

```
 your text here 
```


We need to get a look at what is going on with your PC.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by rquint on 2011-05-11
Sorry about the bad etiquette.  Here's the output from boot_info_script055.
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   374,792,191   374,790,144  83 Linux
/dev/sda2         374,794,238   390,721,535    15,927,298   5 Extended
/dev/sda5         374,794,240   390,721,535    15,927,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2a9948c0-1bf6-4536-bccb-cd6cf2ef1ba4   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a7bf4bcb-636a-419a-8dc4-38ab3fb8ef00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2a9948c0-1bf6-4536-bccb-cd6cf2ef1ba4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 171.9GB: boot/grub/core.img
   3.2GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-28-generic
 157.0GB: boot/initrd.img-2.6.38-8-generic
    .8GB: boot/vmlinuz-2.6.35-28-generic
   3.8GB: boot/vmlinuz-2.6.38-8-generic
 157.0GB: initrd.img
   1.0GB: initrd.img.old
   3.8GB: vmlinuz
    .8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```
A further note--booting with the old kernel 2.6.35-28-generic #50 brings up 11.04 with the nice new Unity interface.

---

### Post by Hedgehog1 on 2011-05-12
> **rquint said:**
> A further note--booting with the old kernel 2.6.35-28-generic #50 brings up 11.04 with the nice new Unity interface.

Your install is very strait forward; It is a nice change from some of the wild installs we see...

It also tells me that what I was expecting to be the cause, is not even present to cause this issue.  It was SUCH a good idea, too.

**I am now hoping some other fourm members will see this and take a guess at what is happening to your PC.**


***The Hedge***

:KS

---

### Post by Quackers on 2011-05-12
Does the older kernel work ok when you reboot? If so, it seems that the new kernel is the problem.

---

### Post by rquint on 2011-05-12
Yes, it's something in the kernel.  I decided to widen the pool of updates and downloaded the next kernel 2.6.38-9-generic #43.  Things are working fine now.  This reminds me that a similar thing happened when the AMD64 version of 10.10 came out.  That time, the kernel shipped with the install CD caused all sorts of mayhem with SATA hard disks.  The first update fixed that.

---

### Post by rquint on 2011-06-08
Upgrading to kernel 2.6.38-10-generic from 2.6.38-9-generic has reintroduced this problem.  I'll file a bug report.

---

