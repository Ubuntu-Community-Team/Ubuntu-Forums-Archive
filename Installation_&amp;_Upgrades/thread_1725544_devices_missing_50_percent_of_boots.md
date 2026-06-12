---
title: "devices missing 50 percent of boots"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by DocShaman on 2011-04-09
Hi All,

I wasn't sure of etiquette on reopening a solved thread so I started a new one. Besides I've repartitioned and reloaded both Dual Boot OS since then. Now Marverick 10.10 and Win7 Ultimate. Bios Current.

Original Thread here : [http://ubuntuforums.org/showthread.php?t=1656802](http://ubuntuforums.org/showthread.php?t=1656802)

I really want to get Linux to boot consistently but right now i'm about 50% failure booting. Usually I give up and use Windows because it's just easier but I want to work in Linux.So I need your help please. I've tried so many permutations of bios settings and forum reading etc,

Problem:
About 50% of the time I boot I get dumped to the initramfs/busybox prompt thingy. Alert!: /dev/disk/bu-uuid... does not exist, There are no /dev/sd[abc] devices. Even when booting from Live CD (once this starts happening) no devices. It "appears" to happen next boot after I click on shut down on desktop in Ubuntu (not hard shut down) but reboot seems to come back fine. Also "seems" to fail after booting in to Windows.  Then it stays until I launch into Win7. Sometimes I have to chkdsk, sometimes just boot in to Win7. So im guessing this is all somewhat random.

I am dual boot (not wubi). But I moved grub to the second disk and boot it from the bios boot selector menu and reloaded the Win7 MBR to avoid MBR rewriting problems.

Went through these:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Especially the "Alert!" one which looks right on.
But the results don't look a match to me.

doc-linux%   sudo BLKID_DEBUG=0xffff blkid -p /dev/sda1 | grep "minix: magic"
minix: magic sboff=510, kboff=0
(all sda[123] partitions return same)
(all sbd[1234] partitions return nothing, empty,null)
doc-linux% sudo BLKID_DEBUG=0xffff blkid -p /dev/sdb1 | grep "minix: magic"
doc-linux% sudo BLKID_DEBUG=0xffff blkid -p /dev/sdb2 | grep "minix: magic"
doc-linux% sudo BLKID_DEBUG=0xffff blkid -p /dev/sdb3 | grep "minix: magic"
doc-linux% sudo BLKID_DEBUG=0xffff blkid -p /dev/sdb4 | grep "minix: magic"


doc-linux% sudo hexdump -s 0x410 -n 2 /dev/sda1
0000410 0000                                  
0000412

#############################
Bootinfoscript: (from a good boot)


```

                Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
    partition #2 for (,msdos2)/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System: 
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System: 
    Boot files/dirs:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   209,715,199   209,508,352   7 HPFS/NTFS
/dev/sda3         209,715,200   976,773,119   767,057,920   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    16,779,263    16,777,216  82 Linux swap / Solaris
/dev/sdb2          16,779,264    17,803,263     1,024,000  83 Linux
/dev/sdb3          17,803,264   122,660,863   104,857,600  83 Linux
/dev/sdb4         122,660,864   976,768,064   854,107,201  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 129     3,907,007     3,906,879   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/sda1        0C487E11487DFA32                       ntfs       System Reserved              
/dev/sda2        C2708003707FFC83                       ntfs                                    
/dev/sda3        0590842476625666                       ntfs       Storage                      
/dev/sda: PTTYPE="dos"
/dev/sdb1        d7a0ef6e-a9b2-49f2-b7ee-bf9dcd71dc60   swap       linux-swap                   
/dev/sdb2        04889777-31cc-4e9e-9c5a-482969c9a19e   ext2                                    
/dev/sdb3        4982a7f7-6738-4658-88c7-9c63b40c7ce3   ext3                                    
/dev/sdb4        67a2d807-8bfa-4dfe-af95-15a40d1065ac   ext4                                    
/dev/sdb: PTTYPE="dos"
/dev/sdd1        9C9B-5055                              vfat                                    
/dev/sdd: PTTYPE="dos"
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /boot                    ext2       (rw)
/dev/sdb4        /sl                      ext4       (rw,commit=0)
/dev/sdd1        /media/9C9B-5055         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sdb2/grub/grub.cfg: =============================

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
set root='(hd2,msdos3)'
search --no-floppy --fs-uuid --set 4982a7f7-6738-4658-88c7-9c63b40c7ce3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    linux    /vmlinuz-2.6.35-28-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro   quiet splash
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /vmlinuz-2.6.35-28-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    linux    /vmlinuz-2.6.35-22-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 04889777-31cc-4e9e-9c5a-482969c9a19e
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0c487e11487dfa32
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

=================== sdb2: Location of files loaded by Grub: ===================


   8.8GB: grub/core.img
   8.8GB: grub/grub.cfg
   8.6GB: initrd.img-2.6.35-22-generic
   8.6GB: initrd.img-2.6.35-28-generic
   8.6GB: vmlinuz-2.6.35-22-generic
   8.6GB: vmlinuz-2.6.35-28-generic

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=04889777-31cc-4e9e-9c5a-482969c9a19e /boot           ext2    defaults        0       2
# /storage was on /dev/sda3 during installation
UUID=0590842476625666 /storage        ntfs    defaults,noauto,umask=007,gid=46 0       0
# /storage2 was on /dev/sdb4 during installation, recreated to ext4 by rg
UUID=67a2d807-8bfa-4dfe-af95-15a40d1065ac /sl    ext4    defaults
# swap was on /dev/sdb1 during installation
UUID=d7a0ef6e-a9b2-49f2-b7ee-bf9dcd71dc60 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


   9.1GB: initrd.img
   9.1GB: initrd.img.old
   9.1GB: vmlinuz
   9.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc



```



#############################
DMESG (from a bad boot) Also tried pci-nocrs which gave reverse error.

```


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.35-28-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000250000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x250000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 100000000 mask F00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 240000000 mask FF0000000 write-back
[    0.000000]   3 base 000000000 mask F80000000 write-back
[    0.000000]   4 base 080000000 mask FE0000000 write-back
[    0.000000]   5 base 0A0000000 mask FF0000000 write-back
[    0.000000]   6 base 0AFF00000 mask FFFF00000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xafef0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b800 (usable)
[    0.000000]  modified: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  modified: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  modified: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  modified: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000250000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f41d0] f41d0
[    0.000000] init_memory_mapping: 0000000000000000-00000000afef0000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afef0000 page 4k
[    0.000000] kernel direct mapping tables up to afef0000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000250000000
[    0.000000]  0100000000 - 0250000000 page 2M
[    0.000000] kernel direct mapping tables up to 250000000 @ 19000-24000
[    0.000000] RAMDISK: 37570000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f8190 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 00000000afef3040 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 00000000afef30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 00000000afef3180 05453 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000afef0000 00040
[    0.000000] ACPI: HPET 00000000afef8740 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 00000000afef87c0 00047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 00000000afef8880 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 00000000afef8640 00098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: OEMN 00000000afef8900 03F98 (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000250000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000250000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00081fffff] PMD -> [ffff880100200000-ffff8801073fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00250000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000afef0
[    0.000000]     0: 0x00100000 -> 0x00250000
[    0.000000] On node 0 totalpages: 2096763
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3923 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702248 pages, LIFO batch:31
[    0.000000]   Normal zone: 18816 pages used for memmap
[    0.000000]   Normal zone: 1357440 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1f000 - 1f7ff]
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afef0000 - 00000000afef3000
[    0.000000] PM: Registered nosave memory: 00000000afef3000 - 00000000aff00000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:20100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2063611
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-28-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (55 early reservations)
[    0.000000]   #1 [0001000000 - 0001d18114]   TEXT DATA BSS
[    0.000000]   #2 [0037570000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d19000 - 0001d190b2]             BRK
[    0.000000]   #4 [00000f41e0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f41d0 - 00000f41e0]    MP-table mpf
[    0.000000]   #6 [000009b800 - 00000f24d4]   BIOS reserved
[    0.000000]   #7 [00000f2660 - 00000f41d0]   BIOS reserved
[    0.000000]   #8 [00000f24d4 - 00000f2660]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001f000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d190c0 - 0001d1a0c0]         BOOTMEM
[    0.000000]   #15 [0001d18140 - 0001d18740]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0107400000]        MEMMAP 0
[    0.000000]   #19 [0001d18740 - 0001d188c0]         BOOTMEM
[    0.000000]   #20 [0001d1a0c0 - 0001d320c0]         BOOTMEM
[    0.000000]   #21 [0001d320c0 - 0001d4a0c0]         BOOTMEM
[    0.000000]   #22 [0001d4b000 - 0001d4c000]         BOOTMEM
[    0.000000]   #23 [0001d188c0 - 0001d18901]         BOOTMEM
[    0.000000]   #24 [0001d18940 - 0001d18983]         BOOTMEM
[    0.000000]   #25 [0001d189c0 - 0001d18bf0]         BOOTMEM
[    0.000000]   #26 [0001d18c00 - 0001d18c68]         BOOTMEM
[    0.000000]   #27 [0001d18c80 - 0001d18ce8]         BOOTMEM
[    0.000000]   #28 [0001d18d00 - 0001d18d68]         BOOTMEM
[    0.000000]   #29 [0001d18d80 - 0001d18de8]         BOOTMEM
[    0.000000]   #30 [0001d18e00 - 0001d18e68]         BOOTMEM
[    0.000000]   #31 [0001d18e80 - 0001d18ee8]         BOOTMEM
[    0.000000]   #32 [0001d18f00 - 0001d18f68]         BOOTMEM
[    0.000000]   #33 [0001d18f80 - 0001d18fe8]         BOOTMEM
[    0.000000]   #34 [0001d4a0c0 - 0001d4a128]         BOOTMEM
[    0.000000]   #35 [0001d4a140 - 0001d4a160]         BOOTMEM
[    0.000000]   #36 [0001d4a180 - 0001d4a1a0]         BOOTMEM
[    0.000000]   #37 [0001d4a1c0 - 0001d4a225]         BOOTMEM
[    0.000000]   #38 [0001d4a240 - 0001d4a2a5]         BOOTMEM
[    0.000000]   #39 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #40 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #41 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #42 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #43 [0001d4a2c0 - 0001d4a2c8]         BOOTMEM
[    0.000000]   #44 [0001d4a300 - 0001d4a308]         BOOTMEM
[    0.000000]   #45 [0001d4a340 - 0001d4a350]         BOOTMEM
[    0.000000]   #46 [0001d4a380 - 0001d4a3a0]         BOOTMEM
[    0.000000]   #47 [0001d4a3c0 - 0001d4a4f0]         BOOTMEM
[    0.000000]   #48 [0001d4a500 - 0001d4a550]         BOOTMEM
[    0.000000]   #49 [0001d4a580 - 0001d4a5d0]         BOOTMEM
[    0.000000]   #50 [0001d4c000 - 0001d54000]         BOOTMEM
[    0.000000]   #51 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #52 [0001d54000 - 0001d74000]         BOOTMEM
[    0.000000]   #53 [0001d74000 - 0001db4000]         BOOTMEM
[    0.000000]   #54 [000001f800 - 0000027800]         BOOTMEM
[    0.000000] Memory: 8179392k/9699328k available (5716k kernel code, 1312276k absent, 207660k reserved, 5375k data, 912k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2400.457 MHz processor.
[    0.010011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.91 BogoMIPS (lpj=24004570)
[    0.010015] pid_max: default: 32768 minimum: 301
[    0.010037] Security Framework initialized
[    0.010057] AppArmor: AppArmor initialized
[    0.010059] Yama: becoming mindful.
[    0.010848] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.015173] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.017066] Mount-cache hash table entries: 256
[    0.017215] Initializing cgroup subsys ns
[    0.017221] Initializing cgroup subsys cpuacct
[    0.017225] Initializing cgroup subsys memory
[    0.017234] Initializing cgroup subsys devices
[    0.017236] Initializing cgroup subsys freezer
[    0.017238] Initializing cgroup subsys net_cls
[    0.017268] CPU: Physical Processor ID: 0
[    0.017270] CPU: Processor Core ID: 0
[    0.017272] mce: CPU supports 6 MCE banks
[    0.017279] CPU0: Thermal monitoring enabled (TM1)
[    0.017284] using mwait in idle threads.
[    0.017286] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.017290] PEBS disabled due to CPU errata.
[    0.017295] ... version:                2
[    0.017296] ... bit width:              40
[    0.017297] ... generic registers:      2
[    0.017299] ... value mask:             000000ffffffffff
[    0.017300] ... max period:             000000007fffffff
[    0.017302] ... fixed-purpose events:   3
[    0.017303] ... event mask:             0000000700000003
[    0.021226] ACPI: Core revision 20100428
[    0.027839] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.027845] ftrace: allocating 22688 entries in 89 pages
[    0.030052] Setting APIC routing to flat
[    0.030454] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136355] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.140000] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.640008] Brought up 4 CPUs
[    0.640011] Total of 4 processors activated (19200.90 BogoMIPS).
[    0.641564] devtmpfs: initialized
[    0.641564] regulator: core version 0.5
[    0.641564] Time: 18:53:19  Date: 04/09/11
[    0.641564] NET: Registered protocol family 16
[    0.641564] ACPI: bus type pci registered
[    0.641564] Trying to unpack rootfs image as initramfs...
[    0.641564] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.641564] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.684418] PCI: Using configuration type 1 for base access
[    0.685037] bio: create slab <bio-0> at 0
[    0.685121] ACPI: EC: Look up EC in DSDT
[    0.692195] ACPI: Interpreter enabled
[    0.692198] ACPI: (supports S0 S1 S3 S4 S5)
[    0.692222] ACPI: Using IOAPIC for interrupt routing
[    0.692450] ACPI: BIOS _OSI(Linux) query ignored
[    0.701103] ACPI: No dock devices found.
[    0.701106] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.701313] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.701475] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.701478] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.701480] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.701483] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.701485] pci_root PNP0A08:00: host bridge window [mem 0xaff00000-0xcfffffff]
[    0.702306] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.702310] pci 0000:00:03.0: PME# disabled
[    0.702485] pci 0000:00:0a.0: reg 10: [io  0xfc00-0xfc7f]
[    0.702531] pci 0000:00:0a.1: reg 10: [io  0xf800-0xf83f]
[    0.702546] pci 0000:00:0a.1: reg 20: [io  0xf400-0xf43f]
[    0.702551] pci 0000:00:0a.1: reg 24: [io  0xf000-0xf03f]
[    0.702576] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.702582] pci 0000:00:0a.1: PME# disabled
[    0.702616] pci 0000:00:0b.0: reg 10: [mem 0xcffff000-0xcfffffff]
[    0.702647] pci 0000:00:0b.0: supports D1 D2
[    0.702649] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.702653] pci 0000:00:0b.0: PME# disabled
[    0.702676] pci 0000:00:0b.1: reg 10: [mem 0xcfffe000-0xcfffe0ff]
[    0.702709] pci 0000:00:0b.1: supports D1 D2
[    0.702710] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.702714] pci 0000:00:0b.1: PME# disabled
[    0.702753] pci 0000:00:0d.0: reg 20: [io  0xec00-0xec0f]
[    0.702795] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
[    0.702799] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.702804] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
[    0.702808] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
[    0.702813] pci 0000:00:0e.0: reg 20: [io  0xd800-0xd80f]
[    0.702817] pci 0000:00:0e.0: reg 24: [mem 0xcfffd000-0xcfffdfff]
[    0.702862] pci 0000:00:0e.1: reg 10: [io  0x09e0-0x09e7]
[    0.702866] pci 0000:00:0e.1: reg 14: [io  0x0be0-0x0be3]
[    0.702871] pci 0000:00:0e.1: reg 18: [io  0x0960-0x0967]
[    0.702875] pci 0000:00:0e.1: reg 1c: [io  0x0b60-0x0b63]
[    0.702880] pci 0000:00:0e.1: reg 20: [io  0xc400-0xc40f]
[    0.702884] pci 0000:00:0e.1: reg 24: [mem 0xcfffc000-0xcfffcfff]
[    0.702929] pci 0000:00:0e.2: reg 10: [io  0xc000-0xc007]
[    0.702934] pci 0000:00:0e.2: reg 14: [io  0xbc00-0xbc03]
[    0.702939] pci 0000:00:0e.2: reg 18: [io  0xb800-0xb807]
[    0.702944] pci 0000:00:0e.2: reg 1c: [io  0xb400-0xb403]
[    0.702949] pci 0000:00:0e.2: reg 20: [io  0xb000-0xb00f]
[    0.702953] pci 0000:00:0e.2: reg 24: [mem 0xcfffb000-0xcfffbfff]
[    0.703044] pci 0000:00:0f.1: reg 10: [mem 0xcfff0000-0xcfff3fff]
[    0.703081] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.703085] pci 0000:00:0f.1: PME# disabled
[    0.703130] pci 0000:00:11.0: reg 10: [mem 0xcfffa000-0xcfffafff]
[    0.703134] pci 0000:00:11.0: reg 14: [io  0xac00-0xac07]
[    0.703139] pci 0000:00:11.0: reg 18: [mem 0xcfff9000-0xcfff90ff]
[    0.703144] pci 0000:00:11.0: reg 1c: [mem 0xcfff8000-0xcfff800f]
[    0.703175] pci 0000:00:11.0: supports D1 D2
[    0.703177] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.703181] pci 0000:00:11.0: PME# disabled
[    0.703216] pci 0000:00:12.0: reg 10: [mem 0xcfff7000-0xcfff7fff]
[    0.703221] pci 0000:00:12.0: reg 14: [io  0xa800-0xa807]
[    0.703225] pci 0000:00:12.0: reg 18: [mem 0xcfff6000-0xcfff60ff]
[    0.703230] pci 0000:00:12.0: reg 1c: [mem 0xcfff5000-0xcfff500f]
[    0.703261] pci 0000:00:12.0: supports D1 D2
[    0.703263] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.703268] pci 0000:00:12.0: PME# disabled
[    0.703319] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.703323] pci 0000:00:13.0: PME# disabled
[    0.703421] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.703424] pci 0000:01:00.0: PME# disabled
[    0.720009] pci 0000:00:03.0: PCI bridge to [bus 01-04]
[    0.720014] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.720017] pci 0000:00:03.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.720021] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.720095] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.720099] pci 0000:02:00.0: PME# disabled
[    0.720146] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.720150] pci 0000:02:02.0: PME# disabled
[    0.720181] pci 0000:01:00.0: PCI bridge to [bus 02-04]
[    0.720186] pci 0000:01:00.0:   bridge window [io  0x9000-0x9fff]
[    0.720190] pci 0000:01:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.720195] pci 0000:01:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.720240] pci 0000:03:00.0: reg 10: [mem 0xcc000000-0xccffffff]
[    0.720251] pci 0000:03:00.0: reg 14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.720262] pci 0000:03:00.0: reg 1c: [mem 0xca000000-0xcbffffff 64bit]
[    0.720268] pci 0000:03:00.0: reg 24: [io  0x9c00-0x9c7f]
[    0.720275] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.740010] pci 0000:02:00.0: PCI bridge to [bus 03-03]
[    0.740015] pci 0000:02:00.0:   bridge window [io  0x9000-0x9fff]
[    0.740019] pci 0000:02:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.740024] pci 0000:02:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.740051] pci 0000:02:02.0: PCI bridge to [bus 04-04]
[    0.740056] pci 0000:02:02.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.740060] pci 0000:02:02.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.740065] pci 0000:02:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.740123] pci 0000:05:07.0: reg 10: [mem 0xcfeff000-0xcfeff7ff]
[    0.740129] pci 0000:05:07.0: reg 14: [mem 0xcfef8000-0xcfefbfff]
[    0.740167] pci 0000:05:07.0: supports D1 D2
[    0.740169] pci 0000:05:07.0: PME# supported from D0 D1 D2 D3hot
[    0.740172] pci 0000:05:07.0: PME# disabled
[    0.740204] pci 0000:00:0f.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.740207] pci 0000:00:0f.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.740211] pci 0000:00:0f.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.740214] pci 0000:00:0f.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.740216] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.740219] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.740221] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.740223] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.740225] pci 0000:00:0f.0:   bridge window [mem 0xaff00000-0xcfffffff] (subtractive decode)
[    0.740263] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.740267] pci 0000:00:13.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.740270] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.740275] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.740288] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.740629] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.810806] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.810937] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.811065] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.811195] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.811323] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[    0.811450] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.811578] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.811706] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.811835] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.811964] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.812092] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.812222] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.812348] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.812477] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.812604] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.812732] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.812865] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.812992] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.813155] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.813314] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.813472] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.813637] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.813795] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.813953] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.814114] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.814274] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.814433] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0
[    0.814591] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0
[    0.814751] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0
[    0.814911] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[    0.815068] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.815227] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.815385] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.815543] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0
[    0.815701] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.815860] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0
[    0.816018] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0
[    0.816177] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0
[    0.816221] HEST: Table is not found!
[    0.816308] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.816311] vgaarb: loaded
[    0.816437] SCSI subsystem initialized
[    0.816446] libata version 3.00 loaded.
[    0.816446] usbcore: registered new interface driver usbfs
[    0.816446] usbcore: registered new interface driver hub
[    0.816446] usbcore: registered new device driver usb
[    0.816446] ACPI: WMI: Mapper loaded
[    0.816446] PCI: Using ACPI for IRQ routing
[    0.816446] PCI: pci_cache_line_size set to 64 bytes
[    0.816446] reserve RAM buffer: 000000000009b800 - 000000000009ffff
[    0.816446] reserve RAM buffer: 00000000afef0000 - 00000000afffffff
[    0.816446] NetLabel: Initializing
[    0.816446] NetLabel:  domain hash size = 128
[    0.816446] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.816446] NetLabel:  unlabeled traffic allowed by default
[    0.816446] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.816446] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.816446] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.850024] Switching to clocksource tsc
[    0.858743] AppArmor: AppArmor Filesystem Enabled
[    0.858762] pnp: PnP ACPI init
[    0.858785] ACPI: bus type pnp registered
[    0.861858] pnp: PnP ACPI: found 13 devices
[    0.861860] ACPI: ACPI bus type pnp unregistered
[    0.861870] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.861873] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.861875] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.861878] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.861880] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.861882] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.861888] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.861890] system 00:02: [io  0x0295-0x0314] has been reserved
[    0.861893] system 00:02: [io  0x0880-0x088f] has been reserved
[    0.861905] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.861910] system 00:0c: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.861913] system 00:0c: [mem 0x000d5800-0x000d7fff] has been reserved
[    0.861915] system 00:0c: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.861918] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.861920] system 00:0c: [mem 0xafef0000-0xafefffff] could not be reserved
[    0.861923] system 00:0c: [mem 0xffff0000-0xffffffff] has been reserved
[    0.861925] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.861928] system 00:0c: [mem 0x00100000-0xafeeffff] could not be reserved
[    0.861930] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.861933] system 00:0c: [mem 0xd0000000-0xdfffffff] has been reserved
[    0.861935] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.861938] system 00:0c: [mem 0xfeff0000] has been reserved
[    0.862438] Freeing initrd memory: 10752k freed
[    0.867967] pci 0000:03:00.0: BAR 6: assigned [mem 0xcd000000-0xcd01ffff pref]
[    0.867970] pci 0000:02:00.0: PCI bridge to [bus 03-03]
[    0.867973] pci 0000:02:00.0:   bridge window [io  0x9000-0x9fff]
[    0.867977] pci 0000:02:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.867981] pci 0000:02:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.867986] pci 0000:02:02.0: PCI bridge to [bus 04-04]
[    0.867988] pci 0000:02:02.0:   bridge window [io  disabled]
[    0.867992] pci 0000:02:02.0:   bridge window [mem disabled]
[    0.867995] pci 0000:02:02.0:   bridge window [mem pref disabled]
[    0.868000] pci 0000:01:00.0: PCI bridge to [bus 02-04]
[    0.868003] pci 0000:01:00.0:   bridge window [io  0x9000-0x9fff]
[    0.868007] pci 0000:01:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.868011] pci 0000:01:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.868016] pci 0000:00:03.0: PCI bridge to [bus 01-04]
[    0.868018] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.868022] pci 0000:00:03.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.868025] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.868029] pci 0000:00:0f.0: PCI bridge to [bus 05-05]
[    0.868031] pci 0000:00:0f.0:   bridge window [io  disabled]
[    0.868034] pci 0000:00:0f.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.868037] pci 0000:00:0f.0:   bridge window [mem pref disabled]
[    0.868042] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.868043] pci 0000:00:13.0:   bridge window [io  disabled]
[    0.868047] pci 0000:00:13.0:   bridge window [mem disabled]
[    0.868049] pci 0000:00:13.0:   bridge window [mem pref disabled]
[    0.868060] pci 0000:00:03.0: setting latency timer to 64
[    0.868069] pci 0000:01:00.0: setting latency timer to 64
[    0.868076] pci 0000:02:00.0: setting latency timer to 64
[    0.868084] pci 0000:02:02.0: setting latency timer to 64
[    0.868089] pci 0000:00:0f.0: setting latency timer to 64
[    0.868096] pci 0000:00:13.0: setting latency timer to 64
[    0.868100] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.868102] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.868104] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.868106] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.868107] pci_bus 0000:00: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.868110] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.868112] pci_bus 0000:01: resource 1 [mem 0xca000000-0xcdffffff]
[    0.868114] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.868116] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.868118] pci_bus 0000:02: resource 1 [mem 0xca000000-0xcdffffff]
[    0.868120] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.868122] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.868124] pci_bus 0000:03: resource 1 [mem 0xca000000-0xcdffffff]
[    0.868126] pci_bus 0000:03: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.868128] pci_bus 0000:05: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.868130] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.868132] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.868134] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.868136] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.868138] pci_bus 0000:05: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.868169] NET: Registered protocol family 2
[    0.868395] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.870000] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.873773] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.874262] TCP: Hash tables configured (established 524288 bind 65536)
[    0.874264] TCP reno registered
[    0.874279] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.874353] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.874529] NET: Registered protocol family 1
[    0.889744] pci 0000:03:00.0: Boot video device
[    0.889750] PCI: CLS 64 bytes, default 64
[    0.889753] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.889755] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    0.889757] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    0.890079] Scanning for low memory corruption every 60 seconds
[    0.890197] audit: initializing netlink socket (disabled)
[    0.890207] type=2000 audit(1302375198.880:1): initialized
[    0.903384] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.904751] VFS: Disk quotas dquot_6.5.2
[    0.904802] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.905346] fuse init (API version 7.14)
[    0.905418] msgmni has been set to 15996
[    0.907903] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.907906] io scheduler noop registered
[    0.907908] io scheduler deadline registered
[    0.907939] io scheduler cfq registered (default)
[    0.908060] pcieport 0000:00:03.0: setting latency timer to 64
[    0.908084]   alloc irq_desc for 40 on node -1
[    0.908086]   alloc kstat_irqs on node -1
[    0.908095] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.908145] pcieport 0000:00:13.0: setting latency timer to 64
[    0.908170]   alloc irq_desc for 41 on node -1
[    0.908172]   alloc kstat_irqs on node -1
[    0.908178] pcieport 0000:00:13.0: irq 41 for MSI/MSI-X
[    0.908262] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.908280] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.908351] intel_idle: MWAIT substates: 0x20
[    0.908353] intel_idle: does not run on family 6 model 15
[    0.908446] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.908451] ACPI: Power Button [PWRB]
[    0.908503] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.908506] ACPI: Power Button [PWRF]
[    0.908881] ACPI: acpi_idle registered with cpuidle
[    0.912129] ERST: Table is not found!
[    0.912299] Linux agpgart interface v0.103
[    0.912321] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.912420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.912732] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.913699] brd: module loaded
[    0.914130] loop: module loaded
[    0.914316] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.914588] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.914592]   alloc irq_desc for 21 on node -1
[    0.914594]   alloc kstat_irqs on node -1
[    0.914599] pata_acpi 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    0.914614] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.914621] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.914871] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.914874]   alloc irq_desc for 20 on node -1
[    0.914875]   alloc kstat_irqs on node -1
[    0.914879] pata_acpi 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    0.914894] pata_acpi 0000:00:0e.1: setting latency timer to 64
[    0.914901] pata_acpi 0000:00:0e.1: PCI INT B disabled
[    0.915149] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    0.915152] pata_acpi 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    0.915167] pata_acpi 0000:00:0e.2: setting latency timer to 64
[    0.915173] pata_acpi 0000:00:0e.2: PCI INT C disabled
[    0.915414] Fixed MDIO Bus: probed
[    0.915441] PPP generic driver version 2.4.2
[    0.915471] tun: Universal TUN/TAP device driver, 1.6
[    0.915472] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.915538] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.915797] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23
[    0.915800]   alloc irq_desc for 23 on node -1
[    0.915802]   alloc kstat_irqs on node -1
[    0.915806] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23
[    0.915825] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.915831] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.915863] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.915887] ehci_hcd 0000:00:0b.1: debug port 1
[    0.915894] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.915911] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000
[    0.929620] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.929759] hub 1-0:1.0: USB hub found
[    0.929765] hub 1-0:1.0: 10 ports detected
[    0.929859] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.930116] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[    0.930118]   alloc irq_desc for 22 on node -1
[    0.930120]   alloc kstat_irqs on node -1
[    0.930124] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22
[    0.930133] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.930136] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.930165] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.930186] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000
[    0.991754] hub 2-0:1.0: USB hub found
[    0.991759] hub 2-0:1.0: 10 ports detected
[    0.991828] uhci_hcd: USB Universal Host Controller Interface driver
[    0.991922] PNP: No PS/2 controller found. Probing ports directly.
[    0.994594] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.994599] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.994656] mice: PS/2 mouse device common for all mice
[    0.994741] rtc_cmos 00:05: RTC can wake from S4
[    0.994768] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.994798] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.994873] device-mapper: uevent: version 1.0.3
[    0.994976] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.995124] device-mapper: multipath: version 1.1.1 loaded
[    0.995127] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.995477] cpuidle: using governor ladder
[    0.995480] cpuidle: using governor menu
[    0.995702] TCP cubic registered
[    0.995806] NET: Registered protocol family 10
[    0.996097] lo: Disabled Privacy Extensions
[    0.996257] NET: Registered protocol family 17
[    0.996378] PM: Resume from disk failed.
[    0.996388] registered taskstats version 1
[    0.996688]   Magic number: 7:910:897
[    0.996777] rtc_cmos 00:05: setting system clock to 2011-04-09 18:53:19 UTC (1302375199)
[    0.996785] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.996786] EDD information not available.
[    0.996845] Freeing unused kernel memory: 912k freed
[    0.997121] Write protecting the kernel read-only data: 10240k
[    0.997307] Freeing unused kernel memory: 408k freed
[    0.997578] Freeing unused kernel memory: 1640k freed
[    1.013119] udev[98]: starting version 163
[    1.047920] pata_amd 0000:00:0d.0: version 0.4.1
[    1.047965] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.065530] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.065541]   alloc irq_desc for 19 on node -1
[    1.065543]   alloc kstat_irqs on node -1
[    1.065555] firewire_ohci 0000:05:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.065762] scsi0 : pata_amd
[    1.073873] scsi1 : pata_amd
[    1.074515] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    1.074518] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    1.074571] sata_nv 0000:00:0e.0: version 3.5
[    1.074591] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    1.074594] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.074851] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.081867] scsi2 : sata_nv
[    1.082000] scsi3 : sata_nv
[    1.082213] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    1.082216] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    1.082257] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    1.082260] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    1.082324] sata_nv 0000:00:0e.1: setting latency timer to 64
[    1.083861] Floppy drive(s): fd0 is 1.44M
[    1.084612] scsi4 : sata_nv
[    1.084826] scsi5 : sata_nv
[    1.085000] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    1.085003] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    1.085037] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    1.085040] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    1.085107] sata_nv 0000:00:0e.2: setting latency timer to 64
[    1.085841] scsi6 : sata_nv
[    1.085931] scsi7 : sata_nv
[    1.086127] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    1.086131] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    1.086161] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.086497] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    1.086503] forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.086509] forcedeth 0000:00:11.0: setting latency timer to 64
[    1.086586] nv_probe: set workaround bit for reversed mac addr
[    1.103905] FDC 0 is a post-1991 82077
[    1.120070] firewire_ohci: Added fw-ohci device 0000:05:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.242393] ata2: port disabled. ignoring.
[    1.311285] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.410073] ata7: SATA link down (SStatus 0 SControl 300)
[    1.461367] hub 1-2:1.0: USB hub found
[    1.461457] hub 1-2:1.0: 2 ports detected
[    1.570024] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.590158] ata5.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[    1.610630] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:14:cc:0c
[    1.610633] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.610928] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    1.610933] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 22 (level, low) -> IRQ 22
[    1.610937] forcedeth 0000:00:12.0: setting latency timer to 64
[    1.610976] nv_probe: set workaround bit for reversed mac addr
[    1.630104] firewire_core: created device fw0: GUID 5ad1245800044b16, S400
[    1.630172] ata5.00: configured for UDMA/66
[    1.870013] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.140650] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:14:cc:0e
[    2.140654] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    2.440019] usb 2-6: new low speed USB device using ohci_hcd and address 3
[    2.679862] usbcore: registered new interface driver hiddev
[    2.685629] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
[    2.685709] generic-usb 0003:045E:0084.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1/input0
[    2.692629] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input3
[    2.692688] generic-usb 0003:03F0:0024.0002: input,hidraw1: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:0b.0-6/input0
[    2.692701] usbcore: registered new interface driver usbhid
[    2.692703] usbhid: USB HID core driver
[    2.780700] usb 1-2.1: new high speed USB device using ehci_hcd and address 5
[    2.917903] Initializing USB Mass Storage driver...
[    2.918052] scsi8 : usb-storage 1-2.1:1.3
[    2.918167] usbcore: registered new interface driver usb-storage
[    2.918169] USB Mass Storage support registered.
[    3.000656] usb 1-2.2: new low speed USB device using ehci_hcd and address 6
[    3.111080] input: USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input4
[    3.111166] generic-usb 0003:0557:2404.0003: input,hidraw2: USB HID v1.10 Keyboard [USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch] on usb-0000:00:0b.1-2.2/input0
[    3.116967] generic-usb 0003:0557:2404.0004: hiddev96,hidraw3: USB HID v1.10 Device [USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch] on usb-0000:00:0b.1-2.2/input1
[    3.911631] scsi 8:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[    3.912235] sd 8:0:0:0: Attached scsi generic sg0 type 0
[    3.913599] sd 8:0:0:0: [sda] Attached SCSI removable disk
[    6.620008] ata3: link is slow to respond, please be patient (ready=0)
[   11.120010] ata3: SRST failed (errno=-16)
[   16.650008] ata3: link is slow to respond, please be patient (ready=0)
[   21.150008] ata3: SRST failed (errno=-16)
[   26.680008] ata3: link is slow to respond, please be patient (ready=0)
[   34.620041] hub 2-0:1.0: unable to enumerate USB device on port 8
[   35.300021] hub 2-0:1.0: unable to enumerate USB device on port 8
[   35.920027] usb 2-8: new full speed USB device using ohci_hcd and address 6
[   36.134673] usb 2-8: not running at top speed; connect to a high speed hub
[   36.155921] scsi9 : usb-storage 2-8:1.0
[   37.158503] scsi 9:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[   37.159145] sd 9:0:0:0: Attached scsi generic sg1 type 0
[   37.169478] sd 9:0:0:0: [sdb] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[   37.176471] sd 9:0:0:0: [sdb] Write Protect is off
[   37.176475] sd 9:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   37.176478] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[   37.202466] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[   37.202471]  sdb: sdb1
[   37.242459] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[   37.242464] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[   55.877771] usb 2-1: USB disconnect, address 2
[   56.200012] ata3: SRST failed (errno=-16)
[   56.200017] ata3: limiting SATA link speed to 1.5 Gbps
[   57.690010] usb 2-1: new low speed USB device using ohci_hcd and address 7
[   57.930598] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input5
[   57.930669] generic-usb 0003:045E:0084.0005: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1/input0
[   61.250017] ata3: SRST failed (errno=-16)
[   61.250020] ata3: reset failed, giving up
[   66.783777] ata4: link is slow to respond, please be patient (ready=0)
[   71.280007] ata4: SRST failed (errno=-16)
[   76.810008] ata4: link is slow to respond, please be patient (ready=0)
[   81.310009] ata4: SRST failed (errno=-16)
[   86.840012] ata4: link is slow to respond, please be patient (ready=0)
[  111.097748] usb 2-1: USB disconnect, address 7
[  112.910009] usb 2-1: new low speed USB device using ohci_hcd and address 8
[  113.150568] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input6
[  113.150637] generic-usb 0003:045E:0084.0006: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1/input0
[  116.360009] ata4: SRST failed (errno=-16)
[  116.360013] ata4: limiting SATA link speed to 1.5 Gbps
[  121.410007] ata4: SRST failed (errno=-16)
[  121.410010] ata4: reset failed, giving up
[  121.410602] scsi 4:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[  121.413921] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[  121.413925] Uniform CD-ROM driver Revision: 3.20
[  121.414040] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  121.414090] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  121.730034] ata6: SATA link down (SStatus 0 SControl 300)
[  122.060018] ata8: SATA link down (SStatus 0 SControl 300)
[  166.381714] usb 2-1: USB disconnect, address 8
[  168.200011] usb 2-1: new low speed USB device using ohci_hcd and address 9
[  168.440589] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input7
[  168.440681] generic-usb 0003:045E:0084.0007: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1/input0


```

Doc

---

### Post by Hedgehog1 on 2011-04-10
Hi Doc!

Thanks for including the boot script.  Would you please put the CODE tags before and after listing (use the '#' button to get them).

I think the logical thing to try it add a 'rootdelay' to the boot parameters, and then rebuild grub.

Please boot into Ubuntu.  If you get the busybox, count to 5 and then type: **exit**

Then do these commands from the terminal:

```
gksudo gedit /etc/default/grub
```

[COLOR="red"]Add the text in red:[/COLOR]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR="Red"]rootdelay=120[/COLOR]**"

[COLOR="red"]Save the file and exit the editor[/COLOR]

```
sudo update-grub
```

Then reboot into Ubuntu and see of this solves the booting error.

***The Hedge***

:KS

---

### Post by DocShaman on 2011-04-10
Thanks for the reply.

Waited 5 sec, exit at busybox does nothing. Just drops me back to busybox. 

run CHKDSK via windows to "temp fix again.
Then, edited via a good boot and added rootdelay=120

next boot /proc/cmdline:

```
BOOT_IMAGE=/vmlinuz-2.6.35-28-generic root=UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 ro quiet splash rootdelay=120

```Same behavior but (obviously) takes much longer to fail the boot. Still no sd[ab] devices are seen in /dev. In the past I have tried much higher, rootdelay=300 at least.

If of any interest I can still mount a USB stick from busybox. It shows up as sda,sda1. 

Thanks, other ideas?
Doc

---

### Post by DocShaman on 2011-04-17
Anyone else have an idea I can try? My devices are not showing up under /dev at all when this happens. It "seems" to be after clicking "Shutdown" in menu not reboot. I am guessing it must be some kind of Bios or kernel probing issue. chkdsk seems to resolve it temporarily until I shut down again. It's bizarre. I've tried just about everything I can find. Thanks.

---

### Post by kelvin spratt on 2011-04-17
You need to comment out  these entries in your fstab 
# / was on /dev/sdb3 during installation UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 /               ext3    errors=remount-ro 0
This is a conflicting entry that needs removing it does not exist since you installed the system. then run #"os-prober" then run #"update-grub" then it should boot correctly. i had the same problem.

---

### Post by DocShaman on 2011-04-17
Thanks for the reply. I tried as you suggested but same results (busybox prompt):

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
#UUID=4982a7f7-6738-4658-88c7-9c63b40c7ce3 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=04889777-31cc-4e9e-9c5a-482969c9a19e /boot           ext2    defaults        0       2
# /storage was on /dev/sda3 during installation
UUID=0590842476625666 /storage        ntfs    defaults,noauto,umask=007,gid=46 0       0
# /storage2 was on /dev/sdb4 during installation, recreated to ext4 by rg
UUID=67a2d807-8bfa-4dfe-af95-15a40d1065ac /sl    ext4    defaults
# swap was on /dev/sdb1 during installation
UUID=d7a0ef6e-a9b2-49f2-b7ee-bf9dcd71dc60 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Note that my device does exist when I get a good boot.

```
doc-linux% ls -l /dev/disk/by-uuid/4982a7f7-6738-4658-88c7-9c63b40c7ce3 
lrwxrwxrwx 1 root root 10 2011-04-17 10:34 /dev/disk/by-uuid/4982a7f7-6738-4658-88c7-9c63b40c7ce3 -> ../../sdb3
```

When I don't get a goot boot I get NO /dev/sd[abc] devices listed under busybox.

Any other ideas?

---

### Post by dino99 on 2011-04-17
most of the times this happen when windows has been closed badly, so the solution is to restart windows then check it (defrag, chkdsk or similar with w7) and maybe run ccleaner.

then reboot on ubuntu and run:

sudo blkid to let you know if it match with fstab

to regenerate initramfs:  sudo update-initramfs -u

[https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)

but dont forget to watch your logs: /home/user/.xsession-errors & /var/log (system admin logviewer)

Others questions:
- is it a fresh install or a dist-upgrade with an old grub1
- how is/are set your(s) hdd into bios (settings/order)

---

### Post by DocShaman on 2011-04-17
Thanks for the response. 

chkdsk gets me back up and running each  time. But this also happens when I don't ever go in to Windows. Just  shutdown via menu in Ubnutu does it also. Reboot seems to be fine  though. Which kind of makes me think bios/hardware thing. But not sure  what to check. Chkdsk fix makes me think harddisks.
I did have these  in RAID-1+0 (or 0+1?) once upon a time for testing but undid them. I  think I read something about that can cause issue. I've repartitioned  and reloaded since then, not sure if i've zeroed.

blkid seems to  match up but I currently have "/" commented out in fstab from the  previous posters suggestion. (I just re-added "/" to fstab, and  commented out the /storage ntfs partition to avoid any issues with that)

```
doc-linux% sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="0C487E11487DFA32" TYPE="ntfs"
/dev/sda2: UUID="C2708003707FFC83" TYPE="ntfs"
/dev/sda3: LABEL="Storage" UUID="0590842476625666" TYPE="ntfs"
/dev/sdb1: LABEL="linux-swap" UUID="d7a0ef6e-a9b2-49f2-b7ee-bf9dcd71dc60" TYPE="swap"
/dev/sdb2: UUID="04889777-31cc-4e9e-9c5a-482969c9a19e" TYPE="ext2"
/dev/sdb3: UUID="4982a7f7-6738-4658-88c7-9c63b40c7ce3" TYPE="ext3"
/dev/sdb4: UUID="67a2d807-8bfa-4dfe-af95-15a40d1065ac" TYPE="ext4"
/dev/sdc1: SEC_TYPE="msdos" UUID="9C9B-5055" TYPE="vfat" 
```

I reloaded initramfs per your suggestion, same problem after shutdown and boot up.

On  a failed boot I see no entries via blkid but my vfat flash drive. No  logs in /var on failed boot. DMESG from failed boot in original post.

I checked my logs on good boot, syslog is showing some ERST and HEST table not found messages which look ACPI related.

Per your questions:

-it  is a fresh install of 10.10 from a live CD dual boot with Windows 7. In  fact I had the same problem before with 10.10 and win98 on the same  host/drives. But repartitioned and reloaded switching to win7 and seeing  the same issue.
-Updated Pheonix Bios to the latest version per EVGA  (mainboard) website last week. SATA drives are probably about 3(?)  years old at this point.

---

### Post by DocShaman on 2011-04-22
Anyone else have ideas on fixes for this? Thanks

---

### Post by DocShaman on 2011-04-23
Made some progress:

This appears to only happen after shutdown (cold boot)

Booting into windows fixes it (no chkdsk needed)

Once the problem occurs:
    can NOT boot from 10.10 Live CD or Hard drive.
    CAN boot from 8.04 Live CD

I notice a lot of problems reported by others with my drive type WD5000AAKS for Linux. Quick test in Windows using WD software came back clean. Need to do a more complete scan. However, once this occurs ALL my devices are gone. Though I can manually mount a vfat usb. But thats a different controller right? 

Another interesting note is when booting of the HD it can see the drive to load the kernel, then it can't see the drive to boot the system. 

I am guessing the answer lies in the files output but its taking forever slow picking up what everything means and how they relate to one another. 

I tried rebuilding a new kernel based on this bug report which looks similar: 
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448/comments/32)

But I must have done something wrong:

```
    cat /boot/config-2.6.35-28-generic | grep AHCI
        CONFIG_SATA_AHCI=m
        CONFIG_SATA_AHCI_PLATFORM=m
```Since 8_04 can see the drives, even in the funky state, im guessing a new kernel setup should be doable if I can figure it out.

Im looking through the files, i'd apprecite if anyone else could take a peak and see if you see anything.

First the 8.04 files (which boot after this occurs):

8.04: dmidecode -q 
```

BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version:   P10 
    Release Date: 12/30/2009
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

System Information
    Manufacturer:  EVGA 
    Product Name: 132-CK-NF78
    Version: 2
    Serial Number: 1
    UUID: 5824D15A-164B-0400-0000-000000000000
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

Base Board Information
    Manufacturer:  EVGA 
    Product Name: 132-CK-NF78
    Version: 2
    Serial Number: 1

Chassis Information
    Manufacturer:  EVGA 
    Type: Desktop
    Lock: Not Present
    Version: 132-CK-NF78
    Serial Number:  
    Asset Tag:  
    Boot-up State: Unknown
    Power Supply State: Unknown
    Thermal State: Unknown
    Security Status: Unknown
    OEM Information: 0x00000000

Processor Information
    Socket Designation: Socket 775
    Type: Central Processor
    Family: Other
    Manufacturer: Intel
    ID: FB 06 00 00 FF FB EB BF
    Version: Intel(R) Core(TM)2 Quad CPU
    Voltage: 1.7 V
    External Clock: 267 MHz
    Max Speed: 200 MHz
    Current Speed: 2403 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    Serial Number:  
    Asset Tag:  
    Part Number:  

Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 32 MB
    Maximum Total Memory Size: 128 MB
    Supported Speeds:
        70 ns
        60 ns
    Supported Memory Types:
        Standard
        EDO
    Memory Module Voltage: 5.0 V
    Associated Memory Slots: 4
        0x0006
        0x0007
        0x0008
        0x0009
    Enabled Error Correcting Capabilities: None

Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Memory Module Information
    Socket Designation: A1
    Bank Connections: 2 3
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Memory Module Information
    Socket Designation: A2
    Bank Connections: 4 5
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Memory Module Information
    Socket Designation: A3
    Bank Connections: 6 7
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Cache Information
    Socket Designation: Internal Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: None
    System Type: Instruction
    Associativity: 8-way Set-associative

Cache Information
    Socket Designation: External Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: External
    Installed Size: 4096 KB
    Maximum Size: 4096 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Port Connector Information
    Internal Reference Designator: Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB0
    External Connector Type: Other
    Port Type: USB

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Other
    Port Type: USB

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Other
    Port Type: USB

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Other
    Port Type: USB

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Other
    Port Type: USB

Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Other
    Port Type: USB

System Slot Information
    Designation: PCI0
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Number Of Devices: 4

Memory Device
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz (1.2 ns)
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Memory Device
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz (1.2 ns)
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Memory Device
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz (1.2 ns)
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Memory Device
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz (1.2 ns)
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Partition Width: 0

Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Partition Row Position: 1

Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Partition Row Position: 1

Memory Device Mapped Address
    Starting Address: 0x00100000000
    Ending Address: 0x0017FFFFFFF
    Range Size: 2 GB
    Partition Row Position: 1

Memory Device Mapped Address
    Starting Address: 0x00180000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 2 GB
    Partition Row Position: 1

System Boot Information
    Status: No errors detected


```8.04: lspci
```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Capabilities: [40] HyperTransport: Host or Secondary Interface
        Command: WarmRst+ DblEnd-
        Link Control: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
        Link Config: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
        Revision ID: 0.16

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: ca000000-cdffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
    Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0f00c  Data: 4149
    Capabilities: [60] HyperTransport: MSI Mapping
    Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
        Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 0
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 0, PowerLimit 0.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Off, PwrInd On, Power-
        Root: Correctable- Non-Fatal- Fatal- PME-

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=9 UnitCnt=15 MastHost- DefDir- DUL-
        Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Revision ID: 1.03
        Link Frequency 0: 1.0GHz
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
        Link Frequency 1: 200MHz
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
        Prefetchable memory behind bridge Upper: 00-00
        Bus Number: 00
    Capabilities: [dc] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Region 0: I/O ports at fc00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Interrupt: pin A routed to IRQ 255
    Region 0: I/O ports at f800 [size=64]
    Region 4: I/O ports at f400 [size=64]
    Region 5: I/O ports at f000 [size=64]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 23
    Region 0: Memory at cfffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Unknown device f0de:c55e
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at ec00 [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at 09f0 [size=8]
    Region 1: I/O ports at 0bf0 [size=4]
    Region 2: I/O ports at 0970 [size=8]
    Region 3: I/O ports at 0b70 [size=4]
    Region 4: I/O ports at d800 [size=16]
    Region 5: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 20
    Region 0: I/O ports at 09e0 [size=8]
    Region 1: I/O ports at 0be0 [size=4]
    Region 2: I/O ports at 0960 [size=8]
    Region 3: I/O ports at 0b60 [size=4]
    Region 4: I/O ports at c400 [size=16]
    Region 5: Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin C routed to IRQ 21
    Region 0: I/O ports at c000 [size=8]
    Region 1: I/O ports at bc00 [size=4]
    Region 2: I/O ports at b800 [size=8]
    Region 3: I/O ports at b400 [size=4]
    Region 4: I/O ports at b000 [size=16]
    Region 5: Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: cfe00000-cfefffff
    Prefetchable memory behind bridge: fff00000-000fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
    Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
    Capabilities: [8c] HyperTransport: MSI Mapping

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
    Subsystem: Unknown device 0175:10de
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin B routed to IRQ 23
    Region 0: Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 508
    Region 0: Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at ac00 [size=8]
    Region 2: Memory at cfff9000 (32-bit, non-prefetchable) [size=256]
    Region 3: Memory at cfff8000 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
    Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Vector table: BAR=2 offset=00000000
        PBA: BAR=3 offset=00000000
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
        Address: 00000000fee0f00c  Data: 4189
        Masking: 000000fe  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 509
    Region 0: Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at a800 [size=8]
    Region 2: Memory at cfff6000 (32-bit, non-prefetchable) [size=256]
    Region 3: Memory at cfff5000 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
    Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Vector table: BAR=2 offset=00000000
        PBA: BAR=3 offset=00000000
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
        Address: 00000000fee0f00c  Data: 4181
        Masking: 000000fe  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping

00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
    Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0f00c  Data: 4151
    Capabilities: [60] HyperTransport: MSI Mapping
    Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 256 bytes, MaxReadReq 512 bytes
        Link: Supported Speed 2.5Gb/s, Width x8, ASPM L0s L1, Port 5
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
        Link: Speed 2.5Gb/s, Width x8
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 0, PowerLimit 0.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Off, PwrInd On, Power-
        Root: Correctable- Non-Fatal- Fatal- PME-

01:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=01, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: ca000000-cdffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express Upstream Port IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <64ns, L1 <1us
        Device: AtnBtn- AtnInd- PwrInd-
        Device: SlotPowerLimit 0.000000
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
        Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
        Link: Supported Speed unknown, Width x16, ASPM L0s, Port 0
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16
    Capabilities: [a0] Subsystem: nVidia Corporation Unknown device c55e

02:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: ca000000-cdffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express Downstream Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
        Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
        Link: Supported Speed unknown, Width x16, ASPM L0s, Port 0
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 1, PowerLimit 0.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Unknown, PwrInd Unknown, Power-

02:02.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2) (prog-if 00 [Normal decode])
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express Downstream Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
        Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
        Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 2
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 3, PowerLimit 0.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Unknown, PwrInd Unknown, Power-

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2) (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Unknown device 2330
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at ca000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at 9c00 [size=128]
    [virtual] Expansion ROM at cd000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express Endpoint IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <512ns, L1 <4us
        Device: AtnBtn- AtnInd- PwrInd-
        Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
        Link: Supported Speed unknown, Width x16, ASPM L0s L1, Port 0
        Link: Latency L0s <512ns, L1 <1us
        Link: ASPM Disabled RCB 128 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16

05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at cfeff000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at cfef8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+


```8.04: lsmod

```

Module                  Size  Used by
nls_iso8859_1           6656  1 
vfat                   16256  1 
fat                    60592  1 vfat
ipv6                  311720  14 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
acpi_cpufreq           10832  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  4 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
ac                      8328  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
snd_hda_intel         440408  3 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
usblp                  17664  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                46236  0 
evdev                  14976  4 
snd_timer              27912  2 snd_pcm,snd_seq
serio_raw               9092  0 
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4992  0 
button                 10912  0 
soundcore              10400  1 snd
i2c_nforce2             8704  0 
shpchp                 38172  0 
i2c_core               28544  1 i2c_nforce2
pci_hotplug            34608  1 shpchp
battery                16776  0 
squashfs               46352  1 
loop                   21508  2 
unionfs                87264  1 
nls_cp437               8320  2 
isofs                  39464  1 
ext3                  149264  0 
jbd                    57000  1 ext3
ext2                   80400  0 
mbcache                11392  2 ext3,ext2
sg                     41880  0 
sr_mod                 20132  1 
sd_mod                 33280  4 
cdrom                  41512  1 sr_mod
usb_storage            82496  1 
libusual               23520  1 usb_storage
usbhid                 35168  0 
hid                    44992  1 usbhid
sata_nv                31624  2 
pata_amd               16772  0 
pata_acpi               9856  0 
floppy                 69096  0 
forcedeth              55564  0 
ata_generic             9988  0 
ohci1394               36532  0 
ieee1394              106968  1 ohci1394
libata                176304  4 sata_nv,pata_amd,pata_acpi,ata_generic
scsi_mod              178488  5 sg,sr_mod,sd_mod,usb_storage,libata
ohci_hcd               27524  0 
ehci_hcd               41996  0 
usbcore               169904  7 usblp,usb_storage,libusual,usbhid,ohci_hcd,ehci_hcd
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```8.04: dmesg

```

[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000250000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720624) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 2424832) 2 entries of 3200 used
[    0.000000] end_pfn_map = 2424832
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8190 checksum 0
[    0.000000] ACPI: RSDP 000F8190, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT AFEF3040, 0040 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT AFEF3180, 5453 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS AFEF0000, 0040
[    0.000000] ACPI: HPET AFEF8740, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT AFEF87C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG AFEF8880, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC AFEF8640, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: OEMN AFEF8900, 3F98 (r1 NVIDIA NTUNEOEM 20302E31 NVDA        0)
[    0.000000] ACPI: SSDT AFEFD1C0, 03A8 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000250000000
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720624) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 2424832) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000250000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  2424832
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      155
[    0.000000]     0:      256 ->   720624
[    0.000000]     0:  1048576 ->  2424832
[    0.000000] On node 0 totalpages: 2096779
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1230 pages reserved
[    0.000000]   DMA zone: 2709 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702248 pages, LIFO batch:31
[    0.000000]   Normal zone: 18816 pages used for memmap
[    0.000000]   Normal zone: 1357440 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 000000000009c000
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000afef0000 - 00000000afef3000
[    0.000000] swsusp: Registered nosave memory region: 00000000afef3000 - 00000000aff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000aff00000 - 00000000d0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000d0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:20100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062397
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   40.064753] time.c: Detected 2399.977 MHz processor.
[   40.066561] Console: colour VGA+ 80x25
[   40.066564] console [tty0] enabled
[   40.066580] Checking aperture...
[   40.066589] Calgary: detecting Calgary via BIOS EBDA area
[   40.066590] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   40.066592] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   40.097585] Placing software IO TLB between 0x105f000 - 0x505f000
[   40.160600] Memory: 8175108k/9699328k available (2466k kernel code, 212008k reserved, 1309k data, 316k init)
[   40.160631] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   40.238465] Calibrating delay using timer specific routine.. 4803.78 BogoMIPS (lpj=9607566)
[   40.238493] Security Framework initialized
[   40.238499] SELinux:  Disabled at boot.
[   40.238509] AppArmor: AppArmor initialized
[   40.238511] Failure registering capabilities with primary security module.
[   40.239146] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   40.243353] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   40.245287] Mount-cache hash table entries: 256
[   40.245411] CPU: L1 I cache: 32K, L1 D cache: 32K
[   40.245413] CPU: L2 cache: 4096K
[   40.245415] CPU 0/0 -> Node 0
[   40.245417] using mwait in idle threads.
[   40.245418] CPU: Physical Processor ID: 0
[   40.245419] CPU: Processor Core ID: 0
[   40.245424] CPU0: Thermal monitoring enabled (TM1)
[   40.245435] SMP alternatives: switching to UP code
[   40.246042] Early unpacking initramfs... done
[   40.551436] ACPI: Core revision 20070126
[   40.551468] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.596132] Using local APIC timer interrupts.
[   40.637737] APIC timer calibration result 16666512
[   40.637738] Detected 16.666 MHz APIC timer.
[   40.637800] SMP alternatives: switching to SMP code
[   40.638306] Booting processor 1/4 APIC 0x3
[   40.648647] Initializing CPU#1
[   40.725604] Calibrating delay using timer specific routine.. 4800.06 BogoMIPS (lpj=9600126)
[   40.725609] CPU: L1 I cache: 32K, L1 D cache: 32K
[   40.725610] CPU: L2 cache: 4096K
[   40.725612] CPU 1/3 -> Node 0
[   40.725613] CPU: Physical Processor ID: 0
[   40.725614] CPU: Processor Core ID: 3
[   40.725619] CPU1: Thermal monitoring enabled (TM1)
[   40.726014] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   40.726094] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   40.746121] SMP alternatives: switching to SMP code
[   40.746493] Booting processor 2/4 APIC 0x1
[   40.756957] Initializing CPU#2
[   40.833434] Calibrating delay using timer specific routine.. 4800.02 BogoMIPS (lpj=9600058)
[   40.833439] CPU: L1 I cache: 32K, L1 D cache: 32K
[   40.833440] CPU: L2 cache: 4096K
[   40.833442] CPU 2/1 -> Node 0
[   40.833443] CPU: Physical Processor ID: 0
[   40.833444] CPU: Processor Core ID: 1
[   40.833449] CPU2: Thermal monitoring enabled (TM1)
[   40.833842] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   40.833881] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   40.853918] SMP alternatives: switching to SMP code
[   40.854447] Booting processor 3/4 APIC 0x2
[   40.864788] Initializing CPU#3
[   40.945258] Calibrating delay using timer specific routine.. 4800.05 BogoMIPS (lpj=9600109)
[   40.945263] CPU: L1 I cache: 32K, L1 D cache: 32K
[   40.945264] CPU: L2 cache: 4096K
[   40.945266] CPU 3/2 -> Node 0
[   40.945267] CPU: Physical Processor ID: 0
[   40.945268] CPU: Processor Core ID: 2
[   40.945273] CPU3: Thermal monitoring enabled (TM1)
[   40.945668] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   40.945734] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   40.965716] Brought up 4 CPUs
[   40.965823] CPU0 attaching sched-domain:
[   40.965825]  domain 0: span 05
[   40.965826]   groups: 01 04
[   40.965828]   domain 1: span 0f
[   40.965829]    groups: 05 0a
[   40.965831]    domain 2: span 0f
[   40.965832]     groups: 0f
[   40.965833] CPU1 attaching sched-domain:
[   40.965834]  domain 0: span 0a
[   40.965835]   groups: 02 08
[   40.965837]   domain 1: span 0f
[   40.965838]    groups: 0a 05
[   40.965840]    domain 2: span 0f
[   40.965841]     groups: 0f
[   40.965842] CPU2 attaching sched-domain:
[   40.965843]  domain 0: span 05
[   40.965844]   groups: 04 01
[   40.965846]   domain 1: span 0f
[   40.965847]    groups: 05 0a
[   40.965848]    domain 2: span 0f
[   40.965849]     groups: 0f
[   40.965851] CPU3 attaching sched-domain:
[   40.965852]  domain 0: span 0a
[   40.965853]   groups: 08 02
[   40.965854]   domain 1: span 0f
[   40.965856]    groups: 0a 05
[   40.965857]    domain 2: span 0f
[   40.965858]     groups: 0f
[   40.966112] net_namespace: 120 bytes
[   40.966427] Time:  9:50:02  Date: 04/23/11
[   40.966446] NET: Registered protocol family 16
[   40.966584] ACPI: bus type pci registered
[   40.966636] PCI: Using configuration type 1
[   40.967928] ACPI: EC: Look up EC in DSDT
[   40.972775] ACPI: Interpreter enabled
[   40.972777] ACPI: (supports S0 S1 S3 S4 S5)
[   40.972789] ACPI: Using IOAPIC for interrupt routing
[   40.972994] ACPI: BIOS _OSI(Linux) query ignored
[   40.972995] ACPI: DMI System Vendor:  EVGA 
[   40.972996] ACPI: DMI Product Name: 132-CK-NF78
[   40.972997] ACPI: DMI Product Version: 2
[   40.972998] ACPI: DMI Board Name: 132-CK-NF78
[   40.972999] ACPI: DMI BIOS Vendor: Phoenix Technologies, LTD
[   40.973000] ACPI: DMI BIOS Date: 12/30/2009
[   40.973001] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[   40.973003] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   40.980002] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.981735] PCI: Transparent bridge - 0000:00:0f.0
[   40.981809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.982208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   41.042192] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.042333] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.042475] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.042614] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[   41.042753] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[   41.042891] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.043029] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.043167] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.043308] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   41.043448] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[   41.043586] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   41.043730] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   41.043867] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.044006] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   41.044144] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   41.044283] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[   41.044422] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[   41.044564] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[   41.044733] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   41.044898] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   41.045059] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   41.045223] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   41.045383] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[   41.045544] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[   41.045704] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[   41.045865] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[   41.046026] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0
[   41.046186] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0
[   41.046347] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0
[   41.046507] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[   41.046667] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[   41.046829] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[   41.046989] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[   41.047150] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0
[   41.047311] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[   41.047472] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0
[   41.047632] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0
[   41.047793] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0
[   41.047910] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.047931] pnp: PnP ACPI init
[   41.047936] ACPI: bus type pnp registered
[   41.051021] pnp: PnP ACPI: found 13 devices
[   41.051022] ACPI: ACPI bus type pnp unregistered
[   41.051192] PCI: Using ACPI for IRQ routing
[   41.051194] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.065161] NET: Registered protocol family 8
[   41.065163] NET: Registered protocol family 20
[   41.065200] PCI-GART: No AMD northbridge found.
[   41.065207] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   41.065211] hpet0: 3 32-bit timers, 25000000 Hz
[   41.066242] AppArmor: AppArmor Filesystem Enabled
[   41.069142] Time: tsc clocksource has been installed.
[   41.069150] Switched to high resolution mode on CPU 0
[   41.069613] Switched to high resolution mode on CPU 2
[   41.070131] Switched to high resolution mode on CPU 3
[   41.070444] Switched to high resolution mode on CPU 1
[   41.077134] system 00:00: ioport range 0x1000-0x107f has been reserved
[   41.077137] system 00:00: ioport range 0x1080-0x10ff has been reserved
[   41.077140] system 00:00: ioport range 0x1400-0x147f has been reserved
[   41.077142] system 00:00: ioport range 0x1480-0x14ff has been reserved
[   41.077145] system 00:00: ioport range 0x1800-0x187f has been reserved
[   41.077147] system 00:00: ioport range 0x1880-0x18ff has been reserved
[   41.077153] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   41.077156] system 00:02: ioport range 0x295-0x314 has been reserved
[   41.077158] system 00:02: ioport range 0x880-0x88f has been reserved
[   41.077170] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   41.077176] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[   41.077178] system 00:0c: iomem range 0xd5800-0xd7fff has been reserved
[   41.077181] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved
[   41.077183] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   41.077186] system 00:0c: iomem range 0xafef0000-0xafefffff could not be reserved
[   41.077189] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[   41.077192] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   41.077195] system 00:0c: iomem range 0x100000-0xafeeffff could not be reserved
[   41.077197] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   41.077200] system 00:0c: iomem range 0xd0000000-0xdfffffff could not be reserved
[   41.077203] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   41.077206] system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved
[   41.077514] PCI: Bridge: 0000:02:00.0
[   41.077516]   IO window: 9000-9fff
[   41.077519]   MEM window: ca000000-cdffffff
[   41.077522]   PREFETCH window: b0000000-bfffffff
[   41.077525] PCI: Bridge: 0000:02:02.0
[   41.077526]   IO window: disabled.
[   41.077529]   MEM window: disabled.
[   41.077531]   PREFETCH window: disabled.
[   41.077534] PCI: Bridge: 0000:01:00.0
[   41.077536]   IO window: 9000-9fff
[   41.077539]   MEM window: ca000000-cdffffff
[   41.077542]   PREFETCH window: b0000000-bfffffff
[   41.077545] PCI: Bridge: 0000:00:03.0
[   41.077546]   IO window: 9000-9fff
[   41.077549]   MEM window: ca000000-cdffffff
[   41.077551]   PREFETCH window: b0000000-bfffffff
[   41.077553] PCI: Bridge: 0000:00:0f.0
[   41.077554]   IO window: disabled.
[   41.077557]   MEM window: cfe00000-cfefffff
[   41.077559]   PREFETCH window: disabled.
[   41.077561] PCI: Bridge: 0000:00:13.0
[   41.077562]   IO window: disabled.
[   41.077564]   MEM window: disabled.
[   41.077566]   PREFETCH window: disabled.
[   41.077577] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   41.077586] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   41.077599] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   41.077614] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   41.077621] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   41.077631] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   41.077637] NET: Registered protocol family 2
[   41.113293] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   41.114485] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   41.117844] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   41.118321] TCP: Hash tables configured (established 524288 bind 65536)
[   41.118323] TCP reno registered
[   41.129204] checking if image is initramfs... it is
[   41.729291] Freeing initrd memory: 8171k freed
[   41.733655] audit: initializing netlink socket (disabled)
[   41.733669] audit(1303552202.588:1): initialized
[   41.736444] VFS: Disk quotas dquot_6.5.1
[   41.736511] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   41.736635] io scheduler noop registered
[   41.736638] io scheduler anticipatory registered
[   41.736639] io scheduler deadline registered
[   41.736752] io scheduler cfq registered (default)
[   41.755800] Boot video device is 0000:03:00.0
[   41.755993] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   41.756023] assign_interrupt_mode Found MSI capability
[   41.756046] Allocate Port Service[0000:00:03.0:pcie00]
[   41.756150] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   41.756195] assign_interrupt_mode Found MSI capability
[   41.756225] Allocate Port Service[0000:00:13.0:pcie00]
[   41.756314] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   41.756350] Allocate Port Service[0000:01:00.0:pcie10]
[   41.756432] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   41.756465] Allocate Port Service[0000:02:00.0:pcie20]
[   41.756561] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   41.756594] Allocate Port Service[0000:02:02.0:pcie20]
[   41.785785] Real Time Clock Driver v1.12ac
[   41.785980] hpet_resources: 0xfeff0000 is busy
[   41.786012] Linux agpgart interface v0.102
[   41.786015] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   41.786148] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.786730] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.787556] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.787622] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   41.787776] PNP: No PS/2 controller found. Probing ports directly.
[   41.790636] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.790642] serio: i8042 AUX port at 0x60,0x64 irq 12
[   41.800096] mice: PS/2 mouse device common for all mice
[   41.800137] cpuidle: using governor ladder
[   41.800139] cpuidle: using governor menu
[   41.800243] NET: Registered protocol family 1
[   41.800285] registered taskstats version 1
[   41.800414]   Magic number: 7:456:829
[   41.800502]   hash matches device ptyt9
[   41.800510]   hash matches device ptyqc
[   41.800554] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   41.800556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   41.800557] EDD information not available.
[   41.800562] Freeing unused kernel memory: 316k freed
[   42.952269] fuse init (API version 7.9)
[   42.967159] ACPI: SSDT AFEFC8E0, 02AE (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[   42.967343] ACPI: Processor [CPU0] (supports 8 throttling states)
[   42.967466] ACPI: SSDT AFEFCDA0, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   42.967735] ACPI: SSDT AFEFCF00, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20040311)
[   42.968003] ACPI: SSDT AFEFD060, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20040311)
[   43.188542] usbcore: registered new interface driver usbfs
[   43.188562] usbcore: registered new interface driver hub
[   43.188594] usbcore: registered new device driver usb
[   43.189710] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23
[   43.189716] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [AUS2] -> GSI 23 (level, low) -> IRQ 23
[   43.191221] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   43.191227] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   43.191286] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   43.191467] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   43.191501] ehci_hcd 0000:00:0b.1: debug port 1
[   43.191504] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   43.191513] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xcfffe000
[   43.202147] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.202247] usb usb1: configuration #1 chosen from 1 choice
[   43.202265] hub 1-0:1.0: USB hub found
[   43.202272] hub 1-0:1.0: 10 ports detected
[   43.210431] SCSI subsystem initialized
[   43.216630] libata version 3.00 loaded.
[   43.243693] Floppy drive(s): fd0 is 1.44M
[   43.262533] FDC 0 is a post-1991 82077
[   43.306369] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[   43.306375] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [AUBA] -> GSI 22 (level, low) -> IRQ 22
[   43.307778] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   43.307782] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   43.307823] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   43.307844] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xcffff000
[   43.367453] usb usb2: configuration #1 chosen from 1 choice
[   43.367470] hub 2-0:1.0: USB hub found
[   43.367478] hub 2-0:1.0: 10 ports detected
[   43.469314] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   43.469603] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[   43.469606] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [AMAC] -> GSI 23 (level, low) -> IRQ 23
[   43.469611] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   43.728793] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   43.865921] usb 1-2: configuration #1 chosen from 1 choice
[   43.865991] hub 1-2:1.0: USB hub found
[   43.866098] hub 1-2:1.0: 2 ports detected
[   43.988747] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:14:cc:0c
[   43.988749] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   43.989026] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[   43.989028] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [AMA1] -> GSI 22 (level, low) -> IRQ 22
[   43.989033] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   44.323832] end_request: I/O error, dev fd0, sector 0
[   44.443622] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   44.507902] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:14:cc:0e
[   44.507904] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   44.508281] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   44.508289] ACPI: PCI Interrupt 0000:05:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   44.558374] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   44.560461] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   44.560754] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[   44.560761] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [ASA0] -> GSI 21 (level, low) -> IRQ 21
[   44.560775] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   44.560781] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   44.561028] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[   44.561030] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [ASA1] -> GSI 20 (level, low) -> IRQ 20
[   44.561045] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   44.561051] ACPI: PCI interrupt for device 0000:00:0e.1 disabled
[   44.561294] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[   44.561296] ACPI: PCI Interrupt 0000:00:0e.2[C] -> Link [ASA2] -> GSI 21 (level, low) -> IRQ 21
[   44.561310] PCI: Setting latency timer of device 0000:00:0e.2 to 64
[   44.561316] ACPI: PCI interrupt for device 0000:00:0e.2 disabled
[   44.562829] pata_amd 0000:00:0d.0: version 0.3.10
[   44.562866] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   44.562944] scsi0 : pata_amd
[   44.562975] scsi1 : pata_amd
[   44.563353] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[   44.563355] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[   44.660442] usb 2-1: configuration #1 chosen from 1 choice
[   44.726331] ata2: port disabled. ignoring.
[   44.726395] sata_nv 0000:00:0e.0: version 3.5
[   44.726405] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [ASA0] -> GSI 21 (level, low) -> IRQ 21
[   44.727449] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   44.727516] scsi2 : sata_nv
[   44.727574] scsi3 : sata_nv
[   44.727707] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[   44.727709] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[   44.950822] usb 2-6: new low speed USB device using ohci_hcd and address 3
[   45.167642] usb 2-6: configuration #1 chosen from 1 choice
[   45.195425] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   45.218610] ata3.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   45.218613] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   45.226586] ata3.00: configured for UDMA/133
[   45.354167] end_request: I/O error, dev fd0, sector 0
[   45.386208] usb 1-2.1: new high speed USB device using ehci_hcd and address 5
[   45.499855] usb 1-2.1: configuration #1 chosen from 1 choice
[   45.693795] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   45.701707] usb 1-2.2: new low speed USB device using ehci_hcd and address 6
[   45.708496] ata4.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   45.708499] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   45.722245] ata4.00: configured for UDMA/133
[   45.722351] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   45.722467] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   45.722528] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [ASA1] -> GSI 20 (level, low) -> IRQ 20
[   45.723499] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   45.723572] scsi4 : sata_nv
[   45.723643] scsi5 : sata_nv
[   45.723825] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[   45.723828] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[   45.817735] usb 1-2.2: configuration #1 chosen from 1 choice
[   45.818533] usbcore: registered new interface driver hiddev
[   45.818560] usbcore: registered new interface driver libusual
[   45.821043] Initializing USB Mass Storage driver...
[   45.824688] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input1
[   45.829450] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[5ad1245800044b16]
[   45.854373] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1
[   45.861669] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input2
[   45.877312] input,hidraw1: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:0b.0-6
[   45.877361] scsi6 : SCSI emulation for USB Mass Storage devices
[   45.877393] usb-storage: device found at 5
[   45.877394] usb-storage: waiting for device to settle before scanning
[   45.881112] input: USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input3
[   45.889294] input,hidraw2: USB HID v1.10 Keyboard [USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch] on usb-0000:00:0b.1-2.2
[   45.895567] hiddev96hidraw3: USB HID v1.10 Device [USB 2.0 Peripheral Switch USB 2.0 Peripheral Switch] on usb-0000:00:0b.1-2.2
[   45.895588] usbcore: registered new interface driver usbhid
[   45.895590] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.895592] usbcore: registered new interface driver usb-storage
[   45.895594] USB Mass Storage support registered.
[   46.188944] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   46.352646] ata5.00: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66
[   46.384486] end_request: I/O error, dev fd0, sector 0
[   46.524379] ata5.00: configured for UDMA/66
[   46.835740] ata6: SATA link down (SStatus 0 SControl 300)
[   46.846766] scsi 4:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.02 PQ: 0 ANSI: 5
[   46.846847] ACPI: PCI Interrupt 0000:00:0e.2[C] -> Link [ASA2] -> GSI 21 (level, low) -> IRQ 21
[   46.847853] PCI: Setting latency timer of device 0000:00:0e.2 to 64
[   46.847897] scsi7 : sata_nv
[   46.848061] scsi8 : sata_nv
[   46.848188] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[   46.848190] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[   47.159220] ata7: SATA link down (SStatus 0 SControl 300)
[   47.414806] end_request: I/O error, dev fd0, sector 0
[   47.478699] ata8: SATA link down (SStatus 0 SControl 300)
[   47.495136] Driver 'sd' needs updating - please use bus_type methods
[   47.495206] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   47.495214] sd 2:0:0:0: [sda] Write Protect is off
[   47.495216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.495227] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.495271] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   47.495277] sd 2:0:0:0: [sda] Write Protect is off
[   47.495279] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.495290] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.495292]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   47.517222]  sda1 sda2 sda3
[   47.517311] sd 2:0:0:0: [sda] Attached SCSI disk
[   47.517381] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   47.517390] sd 3:0:0:0: [sdb] Write Protect is off
[   47.517391] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   47.517403] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.517436] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   47.517443] sd 3:0:0:0: [sdb] Write Protect is off
[   47.517444] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   47.517455] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.517457]  sdb: sdb1 sdb2 sdb3 sdb4
[   47.531392] sd 3:0:0:0: [sdb] Attached SCSI disk
[   47.534219] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   47.534233] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   47.534246] sr 4:0:0:0: Attached scsi generic sg2 type 5
[   47.540696] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   47.540699] Uniform CD-ROM driver Revision: 3.20
[   47.540732] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   48.449120] end_request: I/O error, dev fd0, sector 0
[   48.973835] kjournald starting.  Commit interval 5 seconds
[   48.973842] EXT3-fs: mounted filesystem with ordered data mode.
[   49.370243] ISO 9660 Extensions: Microsoft Joliet Level 3
[   49.410855] ISO 9660 Extensions: RRIP_1991A
[   49.675657] Registering unionfs 1.4
[   49.675660] unionfs: debugging is not enabled
[   49.680584] loop: module loaded
[   49.950777] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   50.870230] usb-storage: device scan complete
[   50.870848] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[   50.874733] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   50.874759] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   87.039987] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   87.328102] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   87.410218] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   87.410237] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   87.553463] input: Power Button (FF) as /devices/virtual/input/input4
[   87.574776] ACPI: Power Button (FF) [PWRF]
[   87.574850] input: Power Button (CM) as /devices/virtual/input/input5
[   87.606722] ACPI: Power Button (CM) [PWRB]
[   87.745687] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   88.951907] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[   88.951919] usbcore: registered new interface driver usblp
[   89.238981] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   89.238986] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   89.240422] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   89.273371] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   91.414555] Adding 8388600k swap on /dev/sdb1.  Priority:-1 extents:1 across:8388600k
[   91.921322] ip_tables: (C) 2000-2006 Netfilter Core Team
[   92.897043] No dock devices found.
[   96.470285] lp: driver loaded but no devices found
[   96.521867] ppdev: user-space parallel port driver
[   99.010836] usb 2-1: USB disconnect, address 2
[  100.751759] usb 2-1: new low speed USB device using ohci_hcd and address 4
[  100.964816] usb 2-1: configuration #1 chosen from 1 choice
[  100.977950] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input7
[  101.011367] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:0b.0-1
[  102.148130] eth1: no link during initialization.
[  102.439604] Bluetooth: Core ver 2.11
[  102.439733] NET: Registered protocol family 31
[  102.439736] Bluetooth: HCI device and connection manager initialized
[  102.439740] Bluetooth: HCI socket layer initialized
[  102.609527] Bluetooth: L2CAP ver 2.9
[  102.609535] Bluetooth: L2CAP socket layer initialized
[  102.633212] Bluetooth: RFCOMM socket layer initialized
[  102.633226] Bluetooth: RFCOMM TTY layer initialized
[  102.633228] Bluetooth: RFCOMM ver 1.8
[  105.087773] NET: Registered protocol family 17
[  113.377548] NET: Registered protocol family 10
[  113.377772] lo: Disabled Privacy Extensions
[  113.378805] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  124.147089] eth0: no IPv6 routers present
[  178.464978] usb 1-8: new high speed USB device using ehci_hcd and address 8
[  178.598355] usb 1-8: configuration #1 chosen from 1 choice
[  178.598592] scsi9 : SCSI emulation for USB Mass Storage devices
[  178.598643] usb-storage: device found at 8
[  178.598647] usb-storage: waiting for device to settle before scanning
[  183.588803] usb-storage: device scan complete
[  183.589919] scsi 9:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[  183.593772] sd 9:0:0:0: [sdd] 3907583 512-byte hardware sectors (2001 MB)
[  183.596643] sd 9:0:0:0: [sdd] Write Protect is off
[  183.596648] sd 9:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  183.596652] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  183.604758] sd 9:0:0:0: [sdd] 3907583 512-byte hardware sectors (2001 MB)
[  183.607628] sd 9:0:0:0: [sdd] Write Protect is off
[  183.607633] sd 9:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  183.607636] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  183.607642]  sdd: sdd1
[  183.611643] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[  183.611676] sd 9:0:0:0: Attached scsi generic sg4 type 0

```

---

### Post by oldfred on 2011-04-23
This entry seems to be missing the parameters at the end. Not sure if it is part of the problem or not. I have no clue as to what dump is.

# /storage2 was on /dev/sdb4 during installation, recreated to ext4 by rg
UUID=67a2d807-8bfa-4dfe-af95-15a40d1065ac /sl    ext4    defaults


# /storage2 was on /dev/sdb4 during installation, recreated to ext4 by rg
UUID=67a2d807-8bfa-4dfe-af95-15a40d1065ac /sl    ext4    defaults   0    2

man fstab:
       The fifth field, (fs_freq),  is  used  for  these  filesystems  by  the
       dump(8)  command  to determine which filesystems need to be dumped.  If the fifth field is not present, a value of zero is  returned  and  dump  will assume that the filesystem does not need to be dumped.

# The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.

---

### Post by DocShaman on 2011-04-23
So narrowing in on the SATA controller for now. I notice some differences in the lspci from 8.04 to 10.10 for the controller (sata_nv module). Possibly nothing may just be upgrades in the querying for all I know. 

Additions in 10.10
Control: **DisINTx-**
Status: **INTx-**
    Capabilities: [44] Power Management version 2
        Status: **NoSoftRst- **
    Capabilities: [b0] 
        **Count=1/4 Maskable-**
    Capabilities: [cc] HyperTransport: MSI Mapping** Enable- Fixed+**
[B]    Kernel driver in use: sata_nv
    Kernel modules: sata_nv
[/B] 

Lost in 10.10
    Capabilities: [b0] 
        Queue=0/2




8.04
```
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Unknown device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at 09f0 [size=8]
    Region 1: I/O ports at 0bf0 [size=4]
    Region 2: I/O ports at 0970 [size=8]
    Region 3: I/O ports at 0b70 [size=4]
    Region 4: I/O ports at d800 [size=16]
    Region 5: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [cc] HyperTransport: MSI Mapping
```10.10
```
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device c55e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at 09f0 [size=8]
    Region 1: I/O ports at 0bf0 [size=4]
    Region 2: I/O ports at 0970 [size=8]
    Region 3: I/O ports at 0b70 [size=4]
    Region 4: I/O ports at d800 [size=16]
    Region 5: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [b0] MSI: Enable- Count=1/4 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

```

I realized one of the  kernel compiling options in that bug report prearch <-> perarch. Recompiling  now. But now, i'm not sure if this chipset even supports AHCI as I dont see it when I grep for it in above. So not expecting that to work now. Maybe that is a new path to research, what to try for that chipset. MCP55 SATA Controller (rev a3)

---

### Post by DocShaman on 2011-04-23
Some more progress.  I am at a point now where I can boot after a shutdown (hard reset, cold boot). though now it takes over a minute for the ata is slow to respond stuff to go away. Maybe now I am at a point where kernel params might actually help.

What I did:

These were all tried but I didn't wait a full minute for them to so I'm not 100% sure which worked.

-recompile kernel and build in sata_nv. (Probably not)
-removed DVD Burner ASUS (Others reported problems)
-switched channels of Win HD and Linux HD
-removed Windows HD + DVD, Linux on First channel.
-Put them all back, but moved them all to their own controller. It looked 3 controllers in lspci with 2 slots each. So I separated them since the HD are not the same they might be acting inconsistent on the same controller. Perhaps.
-Tried enabling a few BIOS options that previously seemed to do nothing. Most notably was turning back on the RAID controller. RAID Enabled/Disabled.

Though now i'm not seeing my ata1 which is m windows disk. 

```
[    6.450007] ata1: link is slow to respond, please be patient (ready=0)
[   10.950007] ata1: SRST failed (errno=-16)
...
[   56.030025] ata1: limiting SATA link speed to 1.5 Gbps
[   61.080019] ata1: SRST failed (errno=-16)
[   61.080022] ata1: reset failed, giving up
```
It looks like it gives up on it. 

Is there a way to tell it to not even try the first sata_nv controller slot or disk? Its windows and I dont even really need it.

---

### Post by DocShaman on 2011-04-24
Ok I am working I think. Survived 3 hard boots and booted up in about 15 seconds each time.

BTW, thanks for the fdisk catch, I don't think it was actually related to this but it was a mistake that I needed to correct.

I was trying to decide if the problem was with the first controller or the hard disk so I moved the drive (Samsung w/ Windows) to the third controller on the same with the DVD and after the WD drive w/ Linux Boots up fine and recognizes the drive. So it looks like there is a problem of some kind with the first controller.

I think I can set whichever drive I want as the primary boot in my BIOS so Windows or Linux being first shouldn't be an issue since I have separated the boot loaders each to their own disks.

---

### Post by DocShaman on 2011-04-24
I do seem to be working now. I have cold booted many times and all has gone well so far. So getting ready to mark this solved. This one has bugged me for a couple years now. I decided I had to figure it out or give up all together. 

I am a bit puzzled why the 8.04 and Windows would boot fine but not the 10.10 (an 9.x if I remember correctly). Also why would booting in to windows fix it? A guess. Perhaps the newer Linux drivers included new features over time and one of those new features was not implemented well (per standards) by one of my components or the combination of components. 

I also noted this discussion which talked about hard reset issue being unreliable with my chipset. I don't know but I include it for completeness in case someone else needs it. Seems to sort of match my weirdness.
[http://lkml.org/lkml/2009/2/4/376](http://lkml.org/lkml/2009/2/4/376)

Looking forward to trying out 11.x here in a few days. Ill probably start fresh now that I think its fixed to see if I really am fixed. :) 

Doc

---

### Post by Hedgehog1 on 2011-04-25
Well my suggestion was completely off base (it happens all to often) but I am glad you figured it out!

***The Hedge***

:KS

p.s. Will you be loading Natty now that you are working? :D

---

### Post by DocShaman on 2011-04-25
Hedgehog1,

Well, I appreciate the response none the less. I probably learned more by reading anyway. 
I hadn't compiled a kernel in probably 8 years.

Yes ill be upgrading to Natty. 28th? I am interested to see if it will work after all this. I was just hoping to get this solved before then.

Doc

---

