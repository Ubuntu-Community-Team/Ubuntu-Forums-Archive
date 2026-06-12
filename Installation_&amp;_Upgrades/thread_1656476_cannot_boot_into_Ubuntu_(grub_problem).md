---
title: "cannot boot into Ubuntu (grub problem?)"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by irockonguitar on 2010-12-30
Hi, I initially posted this here: [http://ubuntuforums.org/showthread.php?t=1622388&highlight=understanding+ubiquity&page=9]("http://ubuntuforums.org/showthread.php?t=1622388&highlight=understanding+ubiquity&page=9")

but figured I should maybe make a thread about it since other people may have the same problem and it would be easier to search.

> **irockonguitar said:**
> hey guys,

I did my best to follow the advice here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

and installed ubuntu on the entirety of my second hard drive (D in windows-speak, sdb in ubuntu-speak). It seemed to work, and took me through the whole process of creating my username and determining my keyboard layout, etc etc, and then it said that I needed to reboot in order to finish installation. When I clicked on the "reboot now" button, it ejected the live CD and shut down. Then when I tried to reboot into ubuntu, it gave an error saying that it could not find a medium with live file system (the live CD, is what I took from the message). So I popped the live CD in again and it booted into that. 

Why didn't it actually install ubuntu on sdb? Windows still seems to be intact on sda (or C, in its own words).

EDIT: when it gets to the part where it tells me it can't find the live cd, it also says "Enter 'help' for a list of built-in commands" and sits there waiting for me to give it a command. Is there something I'm supposed to do at this step that I'm missing?



to which Herman responded:

> **Herman said:**
> :) Hello irockonguitar,
I think  that's an error message from GRUB, so it could be that your GRUB is  misconfigured or your file system has something wrong with it.

I would try booting with the Ubuntu Live CD and mounting the file system of the new installation first to see if it looks okay.

Probably if you can mount it the file system is okay, but if you can't find it in your 'Places' Menu, it might just need a file system check. You can use GParted for that. 

Then I would try booting it again and if it still doesn't boot I would try booting up from a different GRUB such as from a GRUB CD or Super Grub Disk, which can also be found in Parted Magic Live CD. 
You can usually boot Ubuntu if it's bootable or at least get an error message telling you why not by booting with GRUB in CLI mode. [GRUB How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")
That would help if the problem has anything to do with a misconfigured GRUB.

If it boots up without any problem from some other GRUB, just try getting updates and likely that will fix it without the need for you to do anything much.

If nothing works, since it's a new installation and you won't have any personal files in there yet, sometimes it's quicker just to try again and re-install and hope for better luck the second time. Ubuntu crams a lot of files into the Live CD, so sometimes it doesn't take much to have IO errors while copying them to the hard disk during an installation, and also there are some files that will be downloaded from the internet during the installation process. I'm not sure if those can be corrupted in any way. I do know that I can run the installation in the same machine and not get the same installation every time, it could be because I use older hardware for some of my testing too. Sometimes just trying again results in a better installation.


and I replied:

> **irockonguitar said:**
> Thanks,

I actually tried re-installing first, and that didn't work. So I checked the file system and it appears ok. I then followed the advice in your link and booted using a Parted Magic Live CD. I am in the process of downloading updates right now, but I don't see any in the list that pertain to Grub. Then again, if it doesn't say "grub" in the title, I wouldn't know what it was. 

I noticed though, that when I did:

```
search -f /vmlinuz

search -f /sbin/init
```

that both returned

```
hd1,msdos1
```

I'm not experienced enough to know what that really means, but the fact that msdos is involved suggests to me that something ended up on sda, the hard drive with Windows, when it was supposed to end up on sdb, where I put Ubuntu. Is that right? Can I do anything about it? Does it matter? Will getting all the updates solve it?


and then later I said:

> **irockonguitar said:**
> Ok, apparently installing updates does not solve the problem. :(  What can I do now?


Also, just another observation, when I try to boot into Ubuntu, prior to it giving me the error about being unable to find a live medium, it also always gives this warning: 

(process:415): GLib-WARNING **: getpwid_r(): failed due to unknown user id (0)

Does that mean anything I should be concerned about?


So, if anybody out there has any advice, or is experiencing a similar problem, I'd be glad to hear it. :)

Thanks

---

### Post by kansasnoob on 2010-12-31
The first thing we should see is the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by irockonguitar on 2010-12-31
Here are my results:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/media/sdb1/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176    29,566,975       204,800   7 HPFS/NTFS
/dev/sda3          29,566,976   976,771,071   947,204,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   972,861,391   972,861,329  83 Linux
/dev/sdb2         972,863,486   976,771,071     3,907,586   5 Extended
/dev/sdb5         972,863,488   976,771,071     3,907,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C08EA9358EA924BE                       ntfs       PQSERVICE                     
/dev/sda2        969AAA8C9AAA6887                       ntfs       SYSTEM RESERVED               
/dev/sda3        C086ACE586ACDCE2                       ntfs       Windoze                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4961d9f3-421d-4bff-95c7-cfac8eec7b87   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b808a47e-1f03-4860-a6f8-a10b84da46c3   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Parted Magic      iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c08ea9358ea924be
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 969aaa8c9aaa6887
	chainloader +1
}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b808a47e-1f03-4860-a6f8-a10b84da46c3 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 468.2GB: boot/grub/core.img
 206.3GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-24-generic-pae
 468.2GB: boot/vmlinuz-2.6.35-24-generic-pae
   1.0GB: initrd.img
 468.2GB: vmlinuz
```

---

### Post by irockonguitar on 2011-01-01
in case it helps, here is my output from 

```
sudo lshw
```


```
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: EBJ41UF8BAS0-DJ-F
             vendor: 02FE
             physical id: 1
             serial: 5204AC16
             slot: M2
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: SODIMM Synchronous [empty]
             physical id: 2
             slot: M3
        *-bank:3
             description: SODIMM Synchronous [empty]
             physical id: 3
             slot: M4
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          size: 1199MHz
          capacity: 1199MHz
          capabilities: vmx ht cpufreq
          configuration: id=5
        *-logicalcpu:0
             description: Logical CPU
             physical id: 5.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 5.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 5.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 5.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 5.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 5.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 5.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 5.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 5.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 5.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 5.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 5.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 5.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 5.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 5.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 5.10
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f8500000-f85fffff ioport:f0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: Redwood [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:47 memory:f0000000-f7ffffff memory:f8500000-f851ffff ioport:2000(size=256) memory:f8540000-f855ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:48 memory:f8520000-f8523fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f8000000-f83fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f8905000-f890500f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f8905800-f8905bff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:f8900000-f8903fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f8400000-f84fffff ioport:a0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: c8:0a:a9:b7:bd:13
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:46 memory:f8400000-f843ffff ioport:3000(size=128)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=4096) memory:f8600000-f86fffff ioport:a0200000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth1
                version: 01
                serial: c4:46:19:07:8c:9d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=136.159.132.27 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f8600000-f8603fff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8905c00-f8905fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi5
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:4030(size=8) ioport:4024(size=4) ioport:4028(size=8) ioport:4020(size=4) ioport:4000(size=32) memory:fe9ff800-fe9fffff
           *-disk:0
                description: ATA Disk
                product: WDC WD5000BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX21A5072732
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2e25a6c2
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8ea9-24be
                   size: 13GiB
                   capacity: 14GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-06-11 07:19:01 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 9aaa-6887
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-06-11 07:19:04 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 2cc7c53f-43f9-534a-893f-fcc79686cd51
                   size: 451GiB
                   capacity: 451GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-06-11 07:19:06 filesystem=ntfs label=Windoze state=clean
           *-cdrom
                description: DVD-RAM writer
                product: BDDVDRW CT21N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Parted Magic
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Parted Magic
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 signature=13af8630 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD5000BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WX21A50P4564
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2e25a6e0
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 4961d9f3-421d-4bff-95c7-cfac8eec7b87
                   size: 463GiB
                   capacity: 463GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-12-30 13:42:58 filesystem=ext4 lastmountpoint=/=8&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P&#1937;&#65533;&#65533;"&#65533;&#65533;&#65533;+&#65533;@&#1937;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;h&#1937;&#65533;9"&#65533;&#65533; modified=2010-12-30 14:31:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-12-30 19:43:31 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdb2
                   size: 1908MiB
                   capacity: 1908MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1908MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f8906000-f89060ff ioport:1820(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f8904000-f8904fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: outbound
```

---

### Post by wilee-nilee on 2011-01-01
Do you have the sdb HD first to be read in the bios.

Just a suggestion with a quick look at the script.

---

### Post by drs305 on 2011-01-01
Can you get a grub prompt? 

Your grub files are deep into the hard drive. It's possible the BIOS can't see them. From the prompt, first see if grub can find the grub files:
```
ls (hd1,1)/boot/grub
```
Does it see a lot of *.mod files? If so, run the next set of commands to try to boot. 

If it doesn't see them, reboot, enter BIOS, and make sure the BIOS sees the full size of your sdb drive (500GB). If it doesn't, there should be a setting to allow BIOS to correctly see the entire drive, or you may need to try to update it if it reports a smaller size (such as 137GB).


```
set prefix=(hd1,1)**/boot/grub**
set root=(hd1,1)
insmod (hd1,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```

---

### Post by irockonguitar on 2011-01-01
> **wilee-nilee said:**
> Do you have the sdb HD first to be read in the bios.

Just a suggestion with a quick look at the script.


I don't understand what that means, sorry. I don't really know anything about bios. :(





> **drs305 said:**
> Can you get a grub prompt? 

Your grub files are deep into the hard drive. It's possible the BIOS can't see them. From the prompt, first see if grub can find the grub files:
```
ls (hd1,1)/boot/grub
```
Does it see a lot of *.mod files? If so, run the next set of commands to try to boot. 

If it doesn't see them, reboot, enter BIOS, and make sure the BIOS sees the full size of your sdb drive (500GB). If it doesn't, there should be a setting to allow BIOS to correctly see the entire drive, or you may need to try to update it if it reports a smaller size (such as 137GB).


```
set prefix=(hd1,1)
set root=(hd1,1)
insmod (hd1,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot

```


Yes, it sees a lot of *.mod files, but when I run those commands, it gives me these errors:

```
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

```

I don't know what "Try passing init= bootarg" means either :(

---

### Post by drs305 on 2011-01-01
> **irockonguitar said:**
> 
I don't know what "Try passing init= bootarg" means either :(

It means I dropped part of the code and you may still get it to boot. I'll correct the previous post (in bold). The "set prefix" part was missing a section. ](*,)

---

### Post by irockonguitar on 2011-01-01
Oh, I didn't notice this the first time I tried, but after 

```
insmod (hd1,1)/boot/grub/linux.mod
```

I get:

```
error: 'linux' is already loaded.
```

Does that have anything to do with it? Sorry I'm a bit of a noob, I've been using Ubuntu for 3 years but I still have only a very, very basic knowledge of it, particularly when it comes to problem-solving.

---

### Post by drs305 on 2011-01-01
> **irockonguitar said:**
> Oh, I didn't notice this the first time I tried, but after 

```
insmod (hd1,1)/boot/grub/linux.mod
```

I get:

```
error: 'linux' is already loaded.
```

Does that have anything to do with it? 

No, that is actually a good sign in that at least Grub is loading the modules. On the other hand, it doesn't explain why it isn't working in the first place if it's finding its parts...

---

### Post by irockonguitar on 2011-01-01
> It means I dropped part of the code and you may still get it to boot. I'll correct the previous post (in bold). The "set prefix" part was missing a section.

Ok now I can get it to boot with that, but it still won't boot by itself automatically. It keeps giving me the error about not finding the live medium.

> **drs305 said:**
> No, that is actually a good sign in that at least Grub is loading the modules. On the other hand, it doesn't explain why it isn't working in the first place if it's finding its parts...

Ok, so at least it's doing part of something right... :)


EDIT: Not sure why, but it never recognized my wired internet before (only wireless), and now suddenly it does. Maybe if I try to fix some other problem, my booting problem will go away? :P

---

### Post by drs305 on 2011-01-01
> **irockonguitar said:**
> Ok now I can get it to boot with that, but it still won't boot by itself automatically. It keeps giving me the error about not finding the live medium.
Ok, so at least it's doing part of something right... :)
EDIT: Not sure why, but it never recognized my wired internet before (only wireless), and now suddenly it does. Maybe if I try to fix some other problem, my booting problem will go away? :P

Yes, definitely try to update your packages, then also update grub and hopefully repair it:
```

sudo apt-get update && sudo apt-get upgrade
sudo update-grub
```

If you get messages about inserting the disk when you run the updates open Synaptic or Software Sources via System, Admin. Go to Settings, Repositories and make sure the CD is *unticked* in the lower section of the Ubuntu Software tab.

---

### Post by irockonguitar on 2011-01-01
> **drs305 said:**
> Yes, definitely try to update your packages, then also update grub and hopefully repair it:
```

sudo apt-get update && sudo apt-get upgrade
sudo update-grub
```

If you get messages about inserting the disk when you run the updates open Synaptic or Software Sources via System, Admin. Go to Settings, Repositories and make sure the CD is *unticked* in the lower section of the Ubuntu Software tab.

Didn't get any messages about inserting the disk. :)

And this is what it gave me when I did 

```
sudo update-grub
```

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```


is that what it was supposed to find? It still asks for a live medium when I reboot. :(

---

### Post by irockonguitar on 2011-01-02
In the thread where I originally posted this (the link to it is in my first post in this thread), Herman responded saying he thinks it might not be a grub problem, but a problem with my installation. He also says that there may be info in the bottom of my syslog, messages, and kern.log files that are useful, but I looked at those and don't really understand what they mean, so what would I be looking for there? Or are there any other ideas for what might be wrong? Is it possible that I just got a bad install and if I burn another live CD it might work better?

---

### Post by kansasnoob on 2011-01-04
I don't have any answers ATM but thought I'd bump this.

---

### Post by irockonguitar on 2011-01-04
> **kansasnoob said:**
> I don't have any answers ATM but thought I'd bump this.

Thanks :)

---

### Post by drs305 on 2011-01-04
I've gone over the files several times and think I may have found one of the problems. In the first lines of the RESULTS.txt, it shows:
> 
Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)[COLOR="Red"]/media[/COLOR]/sdb1/boot/grub.


This is an unusual entry. Since /media is usually a mount point for a removable device, this may be triggering the error message.

Since you can boot using the manual instructions I provided, boot to the Desktop. Then run the following command (don't use these commands if you have booted from a LiveCD):

```
sudo grub-install /dev/sdb
sudo update-grub
```

Maybe it is just this simple!

---

### Post by irockonguitar on 2011-01-04
> **drs305 said:**
> I've gone over the files several times and think I may have found one of the problems. In the first lines of the RESULTS.txt, it shows:


This is an unusual entry. Since /media is usually a mount point for a removable device, this may be triggering the error message.

Since you can boot using the manual instructions I provided, boot to the Desktop. Then run the following command (don't use these commands if you have booted from a LiveCD):

```
sudo grub-install /dev/sdb
sudo update-grub
```

Maybe it is just this simple!



Thanks, but unfortunately it seems that it is not that simple :(  I did that, and it still gives me the exact same error asking for a live CD if I don't go to the grub prompt and enter those booting commands.

However, I ran the boot info script again and it did update that part so now it says:

```
Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in partition #1 for (,msdos1)/boot/grub.
```

---

### Post by drs305 on 2011-01-05
Sorry it didn't work, but I am more comfortable with the new designation for the grub location...

I've tried searching for "live medium" errors but the posts seem all over the spectrum, from IRQ settings, etc.

I can't say whether or not a reinstallation would fix things or not. I do know that troubleshooting often takes longer than reinstalling does.

---

### Post by irockonguitar on 2011-01-19
So... I just installed some updates and had to restart the computer, and now it won't boot Ubuntu at all, even with the grub prompts. Any fresh ideas?

---

### Post by drs305 on 2011-01-20
> **irockonguitar said:**
> So... I just installed some updates and had to restart the computer, and now it won't boot Ubuntu at all, even with the grub prompts. Any fresh ideas?

Since the configuration files may have changed, running the boot info script and posting a new copy of RESULTS.txt is probably warranted.

---

### Post by irockonguitar on 2011-01-21
I can't even boot from the Parted Magic CD anymore, so I booted from the maverick live CD and here's the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176    29,566,975       204,800   7 HPFS/NTFS
/dev/sda3          29,566,976   976,771,071   947,204,096   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   972,861,391   972,861,329  83 Linux
/dev/sdd2         972,863,486   976,771,071     3,907,586   5 Extended
/dev/sdd5         972,863,488   976,771,071     3,907,584  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1031 MB, 1031798272 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62     2,013,759     2,013,698   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C08EA9358EA924BE                       ntfs       PQSERVICE                     
/dev/sda2        969AAA8C9AAA6887                       ntfs       SYSTEM RESERVED               
/dev/sda3        C086ACE586ACDCE2                       ntfs       Windoze                       
/dev/sda: PTTYPE="dos" 
/dev/sdc1        42B0CAADB0CAA72F                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4961d9f3-421d-4bff-95c7-cfac8eec7b87   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        b808a47e-1f03-4860-a6f8-a10b84da46c3   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        2A280E26280DF19D                       ntfs                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/4961d9f3-421d-4bff-95c7-cfac8eec7b87 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4961d9f3-421d-4bff-95c7-cfac8eec7b87
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c08ea9358ea924be
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 969aaa8c9aaa6887
    chainloader +1
}
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4961d9f3-421d-4bff-95c7-cfac8eec7b87 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b808a47e-1f03-4860-a6f8-a10b84da46c3 none            swap    sw              0       0

=================== sdd1: Location of files loaded by Grub: ===================


 468.2GB: boot/grub/core.img
 468.3GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-24-generic-pae
 468.2GB: boot/vmlinuz-2.6.35-24-generic-pae
   1.0GB: initrd.img
 468.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

So, what happened to my second hard drive, sdb? Please tell me this is fixable... :S

Thanks

---

### Post by drs305 on 2011-01-21
It looks like if the BIOS is set to boot sda Windows should boot normally, and if you set BIOS to first look at your Ubuntu drive (sdd) Grub should boot and include menu entries for Windows. 

In BIOS, check the drive sizes as what appears as sda and sdd in RESULTS.txt may not be the same as what the BIOS is seeing. Also check to see if the BIOS recognizes sdb. I'd check the physical connections if it's a SATA drive to ensure the second SATA connector is securely fastened and that the drive is powered.

Also take a look at what the BIOS reports as your Ubuntu drive size. Make sure it sees at least 470GB, since some of your Grub2 boot files are located 468GB deep into the drive.

---

### Post by irockonguitar on 2011-01-24
> **drs305 said:**
> It looks like if the BIOS is set to boot sda Windows should boot normally, and if you set BIOS to first look at your Ubuntu drive (sdd) Grub should boot and include menu entries for Windows. 

In BIOS, check the drive sizes as what appears as sda and sdd in RESULTS.txt may not be the same as what the BIOS is seeing. Also check to see if the BIOS recognizes sdb. I'd check the physical connections if it's a SATA drive to ensure the second SATA connector is securely fastened and that the drive is powered.

Also take a look at what the BIOS reports as your Ubuntu drive size. Make sure it sees at least 470GB, since some of your Grub2 boot files are located 468GB deep into the drive.

Thank you! All it took was to set BIOS to look at the Ubuntu drive first, and now I can boot either OS just fine! I still don't understand why that should make the difference, but at least it works :D

---

### Post by drs305 on 2011-01-24
> **irockonguitar said:**
>  I still don't understand why that should make the difference, but at least it works :D

When the computer boots, it looks at the MBR of the drive determined by the BIOS setting. With these BIOS settings is the instruction on which partition to look for the actual boot files.

Originally, your BIOS pointed to the drive in which the BIOS said 'Look at the Windows partition' and then proceeded to follow the Windows boot instructions. When you changed the boot order, the BIOS now found instructions in the MBR which told it to go to the Ubuntu partition for further instructions (and thus booted Ubuntu).

The only reason this may be important to you is if Grub/Ubuntu stop working and you need to access Windows. Since the Windows drive MBR still points to Windows (but is currently ignored), all you would need to do is tell BIOS to once again look at the Windows drive first. Nothing else will be necessary to regain use of the Windows bootloader and OS.

---

