---
title: "grub2 rebooting computer after changing OS"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by oldmannow on 2011-03-25
I have installed ubuntu netbook 10.10 on a samsung n150 netbook. then I installed windows XP. After this, I reinstalled grub2 (due to windows boot loader wiping grub's set-up) by doing grub-install /dev/sda. I also removed memtest (by removing the executable permission in /etc/grub.d) and the recovery mode (uncommenting GRUB_DISABLE_LINUX_RECOVERY="true" in /etc/default/grub). 

Now I just have 2 entries in grub on boot up: ubuntu & winxp. if i boot up winxp after last shutdown was from ubuntu, the system automatically reboots after selection and leaving the grub menu. after rebooting and coming to the menu again, winxp boots up fine. the exact same happens in reverse: try booting ubuntu after last shutdown was from winxp and the system reboots after selection and leaving the grub menu; works fine after reboot. if the same OS is selected in the grub menu as the one that was used for the last shutdown, there are no problems. how can I prevent/solve this? do I make sense? 

Thanks,

Oldmannow

---

### Post by Dutch70 on 2011-03-25
Hi and welcome to UF

It's always advised to install windows first, but some do it the other way.
Have a look at these links...
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")
[[COLOR="RoyalBlue"]http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/[/COLOR]]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by oldmannow on 2011-03-25
Thanks for the reply. but been there, done that. i am using grub 1.98+20100804-5ubuntu3. that's what I did: installed ubuntu, then winxp, then used booting off usb to reinstall grub (grub-install --root-directory=/mnt/linux /dev/sda). the menu comes up fine with the correct options. update-grub2 managed to locate winxp. but it's this automatic reboot that happens when changing OS that I cannot see why it happens.

---

### Post by Rubi1200 on 2011-03-25
Hi,
please do the following so we can get a better overview of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldmannow on 2011-03-25
ok, this is what I got:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   253,955,519   253,955,457   7 HPFS/NTFS
/dev/sda2         253,964,286   488,396,799   234,432,514   5 Extended
/dev/sda5         253,964,288   258,064,383     4,100,096  82 Linux swap / Solaris
/dev/sda6         258,066,432   488,396,799   230,330,368  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3933 MB, 3933208576 bytes
82 heads, 17 sectors/track, 5510 cylinders, total 7682048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          1,360     7,682,047     7,680,688   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8AFC0950FC0937C9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        11ffe816-30ae-49ea-9708-01a8fd819762   swap                                     
/dev/sda6        9f6e53ec-0ff6-4507-9714-82200c0d1908   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        1A49-EB69                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 9f6e53ec-0ff6-4507-9714-82200c0d1908
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 9f6e53ec-0ff6-4507-9714-82200c0d1908
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9f6e53ec-0ff6-4507-9714-82200c0d1908
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9f6e53ec-0ff6-4507-9714-82200c0d1908 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8afc0950fc0937c9
	drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9f6e53ec-0ff6-4507-9714-82200c0d1908 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 207.4GB: boot/grub/core.img
 229.8GB: boot/grub/grub.cfg
 133.4GB: boot/initrd.img-2.6.35-28-generic
 207.4GB: boot/vmlinuz-2.6.35-28-generic
 133.4GB: initrd.img
 207.4GB: vmlinuz

```

hope this helps.

Thanks,

oldmannow

---

### Post by drs305 on 2011-03-25
I've reread this thread about ten times. It's very odd.

I don't have a solution - I was thinking it might be a BIOS disk size limitation but your menu is beyond 137GB so I don't think that is the problem.

Here are a couple of things to try that might shed some light. Do this after you have exited/shutdown from Windows:

At the original grub menu, press "c" and then see if Grub can find the Ubuntu boot files. Type the following, then press TAB:
```
ls (hd0,6)/boot/vml
```
Does it see the vmlinuz-2.6... file?
Do the same with "ls (hd0,6)/boot/initrd" and TAB. Does it see the initrd... file?

Press ESC to go back to the grub menu, then press 'e' to edit the first menuentry. Use the cursor to go to the 'linux' line and remove "quiet splash". This will allow text to display as it boots. Press CTRL-x to boot and see if any messages provide a hint as to what is happening.

---

### Post by oldmannow on 2011-03-25
it sees vmlinuz & initrd (kernel 2.6.35-28-generic). removed quiet splash and booted. the messages that flashed up seemed normal (no kernel panic or something that doesn't look out of place), but I am unsure - would their be a log of this part (possibly from dmesg)? it literally just flashes up with a screen full of what it is doing for 1-2 seconds and then rebooted. thanks for the suggestion though.

---

### Post by drs305 on 2011-03-25
After Grub passes control events may be logged in /var/log/dmesg of your Ubuntu partition.

Have you tried running an fsck or e2fsck check on the Ubuntu partition?

Have you tried booting without the flash drive (sdc) inserted?

I'll keep thinking but I'm afraid I'm not coming up with much.  ](*,)

---

### Post by oldmannow on 2011-03-25
the usb drive is not inserted when this rebooting is happening. the boot_info_script was run from a usb stick with the "try ubuntu-netbook" option. i just have the 3 partitions ntfs (winxp), swap, ext4 (ubuntu) & only have 1 hard drive. ok, so I started ubuntu to cause a reboot & then booted from usb to get the dmesg and to do fsck. fsck gave this:

```
fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda6: clean, 158146/7200768 files, 12347779/28791296 blocks
```

/var/log/dmesg was this:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  modified: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  modified: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  modified: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7d40] f7d40
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ad000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a9000 - 013eb337
[    0.000000] Move RAMDISK from 00000000375ad000 - 0000000037fef336 to 009a9000 - 013eb336
[    0.000000] ACPI: RSDP 000f7d10 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f5b83f6 0007C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5bfc76 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5b9f00 05C82 (v01  INTEL BEARG31A 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f5c2fc0 00040
[    0.000000] ACPI: MCFG 7f5bfd6a 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7f5bfda6 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7f5bfdde 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5bfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f5bfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f5b9030 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8f8a 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8ee4 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8e3e 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8472 009CC (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5b0
[    0.000000] On node 0 totalpages: 521533
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c13ed200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292022 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=9f6e53ec-0ff6-4507-9714-82200c0d1908 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10432640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (54 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a5000 - 00009a81c0]             BRK
[    0.000000]   #4 [00000f7d50 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7d40 - 00000f7d50]    MP-table mpf
[    0.000000]   #6 [000009dc00 - 000009e071]   BIOS reserved
[    0.000000]   #7 [000009e1c5 - 00000f7d40]   BIOS reserved
[    0.000000]   #8 [000009e071 - 000009e1c5]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a9000 - 00013ec000]     NEW RAMDISK
[    0.000000]   #13 [00013ec000 - 00013ed000]         BOOTMEM
[    0.000000]   #14 [00013ed000 - 00023dd000]         BOOTMEM
[    0.000000]   #15 [00023dd000 - 00023dd004]         BOOTMEM
[    0.000000]   #16 [00023dd040 - 00023dd100]         BOOTMEM
[    0.000000]   #17 [00023dd100 - 00023dd154]         BOOTMEM
[    0.000000]   #18 [00023dd180 - 00023e0180]         BOOTMEM
[    0.000000]   #19 [00023e0180 - 00023e01ec]         BOOTMEM
[    0.000000]   #20 [00023e0200 - 00023e6200]         BOOTMEM
[    0.000000]   #21 [00023e6200 - 00023e6225]         BOOTMEM
[    0.000000]   #22 [00023e6240 - 00023e6267]         BOOTMEM
[    0.000000]   #23 [00023e6280 - 00023e6408]         BOOTMEM
[    0.000000]   #24 [00023e6440 - 00023e6480]         BOOTMEM
[    0.000000]   #25 [00023e6480 - 00023e64c0]         BOOTMEM
[    0.000000]   #26 [00023e64c0 - 00023e6500]         BOOTMEM
[    0.000000]   #27 [00023e6500 - 00023e6540]         BOOTMEM
[    0.000000]   #28 [00023e6540 - 00023e6580]         BOOTMEM
[    0.000000]   #29 [00023e6580 - 00023e65c0]         BOOTMEM
[    0.000000]   #30 [00023e65c0 - 00023e6600]         BOOTMEM
[    0.000000]   #31 [00023e6600 - 00023e6640]         BOOTMEM
[    0.000000]   #32 [00023e6640 - 00023e6680]         BOOTMEM
[    0.000000]   #33 [00023e6680 - 00023e66c0]         BOOTMEM
[    0.000000]   #34 [00023e66c0 - 00023e6700]         BOOTMEM
[    0.000000]   #35 [00023e6700 - 00023e6740]         BOOTMEM
[    0.000000]   #36 [00023e6740 - 00023e6780]         BOOTMEM
[    0.000000]   #37 [00023e6780 - 00023e6790]         BOOTMEM
[    0.000000]   #38 [00023e67c0 - 00023e682a]         BOOTMEM
[    0.000000]   #39 [00023e6840 - 00023e68aa]         BOOTMEM
[    0.000000]   #40 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #41 [0002500000 - 000250e000]         BOOTMEM
[    0.000000]   #42 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #43 [0002700000 - 000270e000]         BOOTMEM
[    0.000000]   #44 [00023e88c0 - 00023e88c4]         BOOTMEM
[    0.000000]   #45 [00023e8900 - 00023e8904]         BOOTMEM
[    0.000000]   #46 [00023e8940 - 00023e8950]         BOOTMEM
[    0.000000]   #47 [00023e8980 - 00023e8990]         BOOTMEM
[    0.000000]   #48 [00023e89c0 - 00023e8a60]         BOOTMEM
[    0.000000]   #49 [00023e8a80 - 00023e8ac8]         BOOTMEM
[    0.000000]   #50 [00023e8b00 - 00023ecb00]         BOOTMEM
[    0.000000]   #51 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #52 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #53 [000270e000 - 0003101080]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5b0)
[    0.000000] Memory: 2039164k/2086592k available (4935k kernel code, 46968k reserved, 2337k data, 688k init, 1177288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fde - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fde   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.091 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.18 BogoMIPS (lpj=5984364)
[    0.004023] pid_max: default: 32768 minimum: 301
[    0.008029] Security Framework initialized
[    0.008067] AppArmor: AppArmor initialized
[    0.008072] Yama: becoming mindful.
[    0.008198] Mount-cache hash table entries: 512
[    0.008455] Initializing cgroup subsys ns
[    0.008465] Initializing cgroup subsys cpuacct
[    0.008477] Initializing cgroup subsys memory
[    0.008496] Initializing cgroup subsys devices
[    0.008502] Initializing cgroup subsys freezer
[    0.008509] Initializing cgroup subsys net_cls
[    0.008561] CPU: Physical Processor ID: 0
[    0.008566] CPU: Processor Core ID: 0
[    0.008572] mce: CPU supports 5 MCE banks
[    0.008585] CPU0: Thermal monitoring handled by SMI
[    0.008595] using mwait in idle threads.
[    0.008608] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.008629] ... version:                3
[    0.008634] ... bit width:              40
[    0.008639] ... generic registers:      2
[    0.008645] ... value mask:             000000ffffffffff
[    0.008651] ... max period:             000000007fffffff
[    0.008656] ... fixed-purpose events:   3
[    0.008661] ... event mask:             0000000700000003
[    0.013764] ACPI: Core revision 20100428
[    0.032020] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032033] ftrace: allocating 21762 entries in 43 pages
[    0.036106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078265] CPU0: Intel(R) Atom(TM) CPU N550   @ 1.50GHz stepping 0a
[    0.080000] APIC calibration not consistent with PM-Timer: 291ms instead of 100ms
[    0.080000] APIC delta adjusted to PM-Timer: 1039060 (3034025)
[    0.080000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.168165]  #2
[    0.008000] Initializing CPU#2
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.260216]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.352000] TSC synchronization [CPU#0 -> CPU#3]:
[    0.352000] Measured 99 cycles TSC warp between CPUs, turning off TSC clock.
[    0.352000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.352021] Brought up 4 CPUs
[    0.352028] Total of 4 processors activated (11969.83 BogoMIPS).
[    0.354117] devtmpfs: initialized
[    0.358472] regulator: core version 0.5
[    0.358516] Time:  1:18:41  Date: 03/26/11
[    0.358602] NET: Registered protocol family 16
[    0.358898] EISA bus registered
[    0.358921] ACPI: bus type pci registered
[    0.358628] Trying to unpack rootfs image as initramfs...
[    0.359076] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.359086] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.359091] PCI: Using MMCONFIG for extended config space
[    0.359096] PCI: Using configuration type 1 for base access
[    0.361084] bio: create slab <bio-0> at 0
[    0.364346] ACPI: EC: Look up EC in DSDT
[    0.376000] ACPI: SSDT 7f5b9ac3 001C1 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.376000] ACPI: Dynamic OEM Table Load:
[    0.376000] ACPI: SSDT (null) 001C1 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.376000] ACPI: SSDT 7f5b928f 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.376000] ACPI: Dynamic OEM Table Load:
[    0.376000] ACPI: SSDT (null) 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.380900] ACPI: SSDT 7f5b9c84 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.381653] ACPI: Dynamic OEM Table Load:
[    0.381662] ACPI: SSDT (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.382033] ACPI: SSDT 7f5b9934 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.382762] ACPI: Dynamic OEM Table Load:
[    0.382771] ACPI: SSDT (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.383757] ACPI: SSDT 7f5b9d58 000D4 (v02  PmRef  Cpu2Ist 00003000 INTL 20050624)
[    0.384535] ACPI: Dynamic OEM Table Load:
[    0.384544] ACPI: SSDT (null) 000D4 (v02  PmRef  Cpu2Ist 00003000 INTL 20050624)
[    0.384920] ACPI: SSDT 7f5b99b9 00085 (v02  PmRef  Cpu2Cst 00003000 INTL 20050624)
[    0.385651] ACPI: Dynamic OEM Table Load:
[    0.385659] ACPI: SSDT (null) 00085 (v02  PmRef  Cpu2Cst 00003000 INTL 20050624)
[    0.386641] ACPI: SSDT 7f5b9e2c 000D4 (v02  PmRef  Cpu3Ist 00003000 INTL 20050624)
[    0.387401] ACPI: Dynamic OEM Table Load:
[    0.387410] ACPI: SSDT (null) 000D4 (v02  PmRef  Cpu3Ist 00003000 INTL 20050624)
[    0.387780] ACPI: SSDT 7f5b9a3e 00085 (v02  PmRef  Cpu3Cst 00003000 INTL 20050624)
[    0.388533] ACPI: Dynamic OEM Table Load:
[    0.388542] ACPI: SSDT (null) 00085 (v02  PmRef  Cpu3Cst 00003000 INTL 20050624)
[    0.390256] ACPI: Interpreter enabled
[    0.390256] ACPI: (supports S0 S3 S4 S5)
[    0.390256] ACPI: Using IOAPIC for interrupt routing
[    0.402557] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.404212] ACPI: No dock devices found.
[    0.404223] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.406632] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.406649] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    0.406666] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.406717] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.411126] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.411136] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.411144] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.411151] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.411158] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.411165] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.411173] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.411180] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.411268] pci 0000:00:02.0: reg 10: [mem 0xf0300000-0xf037ffff]
[    0.411278] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.411287] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.411297] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.411346] pci 0000:00:02.1: reg 10: [mem 0xf0380000-0xf03fffff]
[    0.411484] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.411563] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.411573] pci 0000:00:1b.0: PME# disabled
[    0.411706] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.411716] pci 0000:00:1c.0: PME# disabled
[    0.411849] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.411858] pci 0000:00:1c.1: PME# disabled
[    0.411989] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.412010] pci 0000:00:1c.2: PME# disabled
[    0.412146] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.412157] pci 0000:00:1c.3: PME# disabled
[    0.412245] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.412333] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.412418] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.412504] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.412588] pci 0000:00:1d.7: reg 10: [mem 0xf0604000-0xf06043ff]
[    0.412674] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.412684] pci 0000:00:1d.7: PME# disabled
[    0.412878] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.412959] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.412973] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.412985] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.412998] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.413011] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.413024] pci 0000:00:1f.2: reg 24: [mem 0xf0604400-0xf06047ff]
[    0.413074] pci 0000:00:1f.2: PME# supported from D3hot
[    0.413083] pci 0000:00:1f.2: PME# disabled
[    0.413151] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.413360] pci 0000:05:00.0: reg 10: [mem 0xf0100000-0xf0103fff 64bit]
[    0.413470] pci 0000:05:00.0: supports D1 D2
[    0.413475] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.413486] pci 0000:05:00.0: PME# disabled
[    0.420076] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.420094] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.420104] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.420118] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.420205] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.420215] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.420225] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.420238] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.420602] pci 0000:09:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.420657] pci 0000:09:00.0: reg 18: [io  0x2000-0x20ff]
[    0.421146] pci 0000:09:00.0: supports D1 D2
[    0.421152] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.421179] pci 0000:09:00.0: PME# disabled
[    0.428120] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.428130] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.428141] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.428155] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.428241] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.428251] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0000] (disabled)
[    0.428261] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.428275] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.428386] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.428396] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.428406] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.428419] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.428427] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.428435] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.428442] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.428449] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.428457] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.428464] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.428471] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.428479] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.428522] pci_bus 0000:00: on NUMA node 0
[    0.428534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.428779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.428936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.429086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.429239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.429391] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.429806] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.429822] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    0.445795] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.446021] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.446239] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.446455] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.446686] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.446918] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.447149] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.447380] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.447496] HEST: Table is not found!
[    0.447663] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.447687] vgaarb: loaded
[    0.448091] SCSI subsystem initialized
[    0.448124] libata version 3.00 loaded.
[    0.448152] usbcore: registered new interface driver usbfs
[    0.448184] usbcore: registered new interface driver hub
[    0.448200] usbcore: registered new device driver usb
[    0.448200] ACPI: WMI: Mapper loaded
[    0.448200] PCI: Using ACPI for IRQ routing
[    0.448200] PCI: pci_cache_line_size set to 64 bytes
[    0.448343] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.448351] reserve RAM buffer: 000000007f5b0000 - 000000007fffffff 
[    0.448576] NetLabel: Initializing
[    0.448582] NetLabel:  domain hash size = 128
[    0.448586] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.448613] NetLabel:  unlabeled traffic allowed by default
[    0.448705] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.448718] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.448730] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.464050] Switching to clocksource hpet
[    0.487122] AppArmor: AppArmor Filesystem Enabled
[    0.487159] pnp: PnP ACPI init
[    0.487201] ACPI: bus type pnp registered
[    0.493200] pnp: PnP ACPI: found 9 devices
[    0.493208] ACPI: ACPI bus type pnp unregistered
[    0.493216] PnPBIOS: Disabled by ACPI PNP
[    0.493245] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.493254] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.493261] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.493269] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.493276] system 00:01: [io  0xfe00] has been reserved
[    0.493283] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.493292] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.493300] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.493308] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.493316] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.531973] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.531985] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.531995] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.532004] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.532013] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80800000-0x809fffff]
[    0.532022] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.532032] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.532041] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.532049] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.532057] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.532065] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.532077] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.532087] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.532100] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.532108] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.532119] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff]
[    0.532128] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.532142] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.532149] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.532161] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.532171] pci 0000:00:1c.2:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.532184] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.532191] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.532202] pci 0000:00:1c.3:   bridge window [mem 0x80800000-0x809fffff]
[    0.532212] pci 0000:00:1c.3:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.532226] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.532231] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.532241] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.532249] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.532282]   alloc irq_desc for 16 on node -1
[    0.532287]   alloc kstat_irqs on node -1
[    0.532302] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.532313] pci 0000:00:1c.0: setting latency timer to 64
[    0.532331] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.532339]   alloc irq_desc for 17 on node -1
[    0.532344]   alloc kstat_irqs on node -1
[    0.532354] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.532365] pci 0000:00:1c.1: setting latency timer to 64
[    0.532382]   alloc irq_desc for 18 on node -1
[    0.532387]   alloc kstat_irqs on node -1
[    0.532396] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.532405] pci 0000:00:1c.2: setting latency timer to 64
[    0.532422] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.532430]   alloc irq_desc for 19 on node -1
[    0.532435]   alloc kstat_irqs on node -1
[    0.532444] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.532454] pci 0000:00:1c.3: setting latency timer to 64
[    0.532469] pci 0000:00:1e.0: setting latency timer to 64
[    0.532479] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.532486] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.532493] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.532499] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.532506] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.532513] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.532520] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.532527] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.532533] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.532540] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.532547] pci_bus 0000:05: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.532554] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.532560] pci_bus 0000:07: resource 1 [mem 0x80200000-0x803fffff]
[    0.532567] pci_bus 0000:07: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.532574] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.532580] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.532587] pci_bus 0000:09: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.532594] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.532601] pci_bus 0000:0b: resource 1 [mem 0x80800000-0x809fffff]
[    0.532608] pci_bus 0000:0b: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.532615] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.532622] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.532628] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.532635] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.532641] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.532648] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.532655] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.532661] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.532738] NET: Registered protocol family 2
[    0.532890] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.533441] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.534477] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.535001] TCP: Hash tables configured (established 131072 bind 65536)
[    0.535008] TCP reno registered
[    0.535017] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.535039] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.535267] NET: Registered protocol family 1
[    0.535309] pci 0000:00:02.0: Boot video device
[    0.535536] PCI: CLS 32 bytes, default 64
[    0.535586] Simple Boot Flag at 0x36 set to 0x1
[    0.536238] cpufreq-nforce2: No nForce2 chipset.
[    0.536306] Scanning for low memory corruption every 60 seconds
[    0.536572] audit: initializing netlink socket (disabled)
[    0.536596] type=2000 audit(1301102320.532:1): initialized
[    0.557241] highmem bounce pool size: 64 pages
[    0.557255] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.561174] VFS: Disk quotas dquot_6.5.2
[    0.561364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.562875] fuse init (API version 7.14)
[    0.563117] msgmni has been set to 1683
[    1.209160] Freeing initrd memory: 10508k freed
[    1.225041] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.225050] io scheduler noop registered
[    1.225056] io scheduler deadline registered
[    1.225102] io scheduler cfq registered (default)
[    1.225342] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.225404]   alloc irq_desc for 40 on node -1
[    1.225410]   alloc kstat_irqs on node -1
[    1.225430] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.225632] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.225693]   alloc irq_desc for 41 on node -1
[    1.225699]   alloc kstat_irqs on node -1
[    1.225714] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.225888] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.225946]   alloc irq_desc for 42 on node -1
[    1.225951]   alloc kstat_irqs on node -1
[    1.225967] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.226140] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.226198]   alloc irq_desc for 43 on node -1
[    1.226203]   alloc kstat_irqs on node -1
[    1.226218] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.226444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.226679] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.226695] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.226966] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.226981] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.227240] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.227255] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.227512] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.227526] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.227832] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.227847] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.228117] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.228132] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.228393] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.228408] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.228668] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    1.228683] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701be88), AE_ALREADY_EXISTS
[    1.228770] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.228977] intel_idle: MWAIT substates: 0x20220
[    1.228984] intel_idle: v0.4 model 0x1C
[    1.228989] intel_idle: lapic_timer_reliable_states 0x2
[    1.229904] ACPI: AC Adapter [ADP1] (on-line)
[    1.230105] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.230183] ACPI: Lid Switch [LID0]
[    1.230290] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.230309] ACPI: Power Button [PWRB]
[    1.230419] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.230429] ACPI: Sleep Button [SLPB]
[    1.230535] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.230545] ACPI: Power Button [PWRF]
[    1.230965] ACPI: acpi_idle yielding to intel_idle
[    1.246441] thermal LNXTHERM:01: registered as thermal_zone0
[    1.246462] ACPI: Thermal Zone [TZ00] (56 C)
[    1.246641] ERST: Table is not found!
[    1.246894] isapnp: Scanning for PnP cards...
[    1.246983] ACPI: Battery Slot [BAT1] (battery absent)
[    1.246999] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.250423] brd: module loaded
[    1.251795] loop: module loaded
[    1.252987] Fixed MDIO Bus: probed
[    1.253100] PPP generic driver version 2.4.2
[    1.253196] tun: Universal TUN/TAP device driver, 1.6
[    1.253202] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.253385] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.253434]   alloc irq_desc for 23 on node -1
[    1.253439]   alloc kstat_irqs on node -1
[    1.253455] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.253489] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.253497] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.253598] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.253639] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.253658] ehci_hcd 0000:00:1d.7: debug port 1
[    1.257544] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.257586] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    1.273059] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.273359] hub 1-0:1.0: USB hub found
[    1.273372] hub 1-0:1.0: 8 ports detected
[    1.273545] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.273580] uhci_hcd: USB Universal Host Controller Interface driver
[    1.273649] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.273663] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.273671] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.273765] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.273805] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.274099] hub 2-0:1.0: USB hub found
[    1.274111] hub 2-0:1.0: 2 ports detected
[    1.274242] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.274256] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.274263] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.274352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.274414] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.274692] hub 3-0:1.0: USB hub found
[    1.274704] hub 3-0:1.0: 2 ports detected
[    1.274831] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.274844] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.274851] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.274944] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.274998] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.275284] hub 4-0:1.0: USB hub found
[    1.275295] hub 4-0:1.0: 2 ports detected
[    1.275418] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.275432] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.275439] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.275533] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.275588] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.275883] hub 5-0:1.0: USB hub found
[    1.275898] hub 5-0:1.0: 2 ports detected
[    1.276143] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.278795] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.278815] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.279022] mice: PS/2 mouse device common for all mice
[    1.279505] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.279552] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.279834] device-mapper: uevent: version 1.0.3
[    1.280166] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.280535] device-mapper: multipath: version 1.1.1 loaded
[    1.280545] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.280862] EISA: Probing bus 0 at eisa.0
[    1.280869] EISA: Cannot allocate resource for mainboard
[    1.280875] Cannot allocate resource for EISA slot 1
[    1.280880] Cannot allocate resource for EISA slot 2
[    1.280885] Cannot allocate resource for EISA slot 3
[    1.280891] Cannot allocate resource for EISA slot 4
[    1.280896] Cannot allocate resource for EISA slot 5
[    1.280901] Cannot allocate resource for EISA slot 6
[    1.280906] Cannot allocate resource for EISA slot 7
[    1.280911] Cannot allocate resource for EISA slot 8
[    1.280916] EISA: Detected 0 cards.
[    1.281640] cpuidle: using governor ladder
[    1.282108] cpuidle: using governor menu
[    1.282802] TCP cubic registered
[    1.283144] NET: Registered protocol family 10
[    1.283964] lo: Disabled Privacy Extensions
[    1.284496] NET: Registered protocol family 17
[    1.286498] Using IPI No-Shortcut mode
[    1.286728] PM: Resume from disk failed.
[    1.286759] registered taskstats version 1
[    1.287391]   Magic number: 3:309:307
[    1.287435] tty tty36: hash matches
[    1.287544] rtc_cmos 00:04: setting system clock to 2011-03-26 01:18:42 UTC (1301102322)
[    1.287552] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.287557] EDD information not available.
[    1.312412] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.601004] isapnp: No Plug & Play device found
[    1.601097] Freeing unused kernel memory: 688k freed
[    1.601742] Write protecting the kernel text: 4936k
[    1.601842] Write protecting the kernel read-only data: 1980k
[    1.644068] udev[99]: starting version 163
[    1.756583] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    1.842712] sky2: driver version 1.28
[    1.842886] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.842954] sky2 0000:09:00.0: setting latency timer to 64
[    1.843099] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.843701]   alloc irq_desc for 44 on node -1
[    1.843708]   alloc kstat_irqs on node -1
[    1.843798] sky2 0000:09:00.0: irq 44 for MSI/MSI-X
[    1.845954] sky2 0000:09:00.0: eth0: addr e8:11:32:01:b1:47
[    1.863537] ahci 0000:00:1f.2: version 3.0
[    1.863580] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.863675]   alloc irq_desc for 45 on node -1
[    1.863684]   alloc kstat_irqs on node -1
[    1.863713] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.863877] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.863890] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.863904] ahci 0000:00:1f.2: setting latency timer to 64
[    1.864568] scsi0 : ahci
[    1.864914] scsi1 : ahci
[    1.865150] scsi2 : ahci
[    1.865386] scsi3 : ahci
[    1.865777] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 45
[    1.865788] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 45
[    1.865796] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 45
[    1.865804] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 45
[    2.127218] CE: hpet increased min_delta_ns to 7500 nsec
[    2.148171] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.184151] ata4: SATA link down (SStatus 0 SControl 300)
[    2.184198] ata2: SATA link down (SStatus 0 SControl 300)
[    2.184202] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.184251] ata3: SATA link down (SStatus 0 SControl 300)
[    2.194049] ata1.00: ATA-8: SAMSUNG HM250HI, 2AC101C4, max UDMA/133
[    2.194058] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.204080] ata1.00: configured for UDMA/133
[    2.220496] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250HI  2AC1 PQ: 0 ANSI: 5
[    2.221006] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.221260] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.221431] sd 0:0:0:0: [sda] Write Protect is off
[    2.221440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.221515] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.222229]  sda: sda1 sda2 < sda5 sda6 >
[    2.292729] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.355042] usbcore: registered new interface driver hiddev
[    2.375105] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    2.375641] generic-usb 0003:1BCF:0007.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1/input0
[    2.375704] usbcore: registered new interface driver usbhid
[    2.375713] usbhid: USB HID core driver
[    2.556630] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    2.683608] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   14.426636] Adding 2050044k swap on /dev/sda5.  Priority:-1 extents:1 across:2050044k 
[   14.483501] udev[355]: starting version 163
[   14.637417] Linux agpgart interface v0.103
[   14.654822] lib80211: common routines for IEEE802.11 drivers
[   14.654833] lib80211_crypt: registered algorithm 'NULL'
[   14.672306] lp: driver loaded but no devices found
[   14.711794] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[   14.712750] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   14.742123] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.742134] Disabling lock debugging due to kernel taint
[   14.791024] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.945379] wl 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.945400] wl 0000:05:00.0: setting latency timer to 64
[   15.004778] type=1400 audit(1301102336.213:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=549 comm="apparmor_parser"
[   15.022745] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.033285] type=1400 audit(1301102336.241:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=549 comm="apparmor_parser"
[   15.033815] type=1400 audit(1301102336.241:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=549 comm="apparmor_parser"
[   15.071619] [drm] Initialized drm 1.1.0 20060810
[   15.109286] Bluetooth: Core ver 2.15
[   15.109356] NET: Registered protocol family 31
[   15.109363] Bluetooth: HCI device and connection manager initialized
[   15.109372] Bluetooth: HCI socket layer initialized
[   15.128483] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.137973] Linux video capture interface: v2.00
[   15.146296] lib80211_crypt: registered algorithm 'TKIP'
[   15.146660] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   15.149191] usbcore: registered new interface driver btusb
[   15.225310] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   15.228466] input: WebCam SCB-0340N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[   15.228941] usbcore: registered new interface driver uvcvideo
[   15.228951] USB Video Class driver (v0.1.0)
[   15.252088] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.304259] psmouse serio1: ID: 10 00 64
[   15.340407] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.340422] i915 0000:00:02.0: setting latency timer to 64
[   15.373521] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.375502] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   15.375514] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   15.375522] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   15.403566]   alloc irq_desc for 46 on node -1
[   15.403578]   alloc kstat_irqs on node -1
[   15.403603] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   15.403630] [drm] set up 7M of stolen space
[   15.487840] elantech: assuming hardware version 2, firmware version 4.2.22
[   15.513699] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.514160] [drm] initialized overlay support
[   15.614547] elantech: Synaptics capabilities query result 0x09, 0x14, 0x0b.
[   15.627392] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.710734] type=1400 audit(1301102336.917:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=818 comm="apparmor_parser"
[   15.725147] type=1400 audit(1301102336.933:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=819 comm="apparmor_parser"
[   15.726054] type=1400 audit(1301102336.933:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"
[   15.726591] type=1400 audit(1301102336.933:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
[   15.735882] type=1400 audit(1301102336.941:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=826 comm="apparmor_parser"
[   15.745654] type=1400 audit(1301102336.953:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=826 comm="apparmor_parser"
[   15.747481] type=1400 audit(1301102336.953:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=831 comm="apparmor_parser"
[   15.775172] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
[   15.856711] Skipping EDID probe due to cached edid
[   15.942837] sky2 0000:09:00.0: eth0: enabling interface
[   15.943584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.278080] Console: switching to colour frame buffer device 128x37
[   16.285568] fb0: inteldrmfb frame buffer device
[   16.285574] drm: registered panic notifier
[   16.285586] Slow work thread pool: Starting up
[   16.285871] Slow work thread pool: Ready
[   16.289225] ACPI Warning: _BQC returned an invalid level (20100428/video-640)
[   16.291745] acpi device:03: registered as cooling_device4
[   16.295192] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   16.295773] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[   16.296252] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.296443]   alloc irq_desc for 22 on node -1
[   16.296455]   alloc kstat_irqs on node -1
[   16.296477] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.296671]   alloc irq_desc for 47 on node -1
[   16.296680]   alloc kstat_irqs on node -1
[   16.296724] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   16.296835] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.395934] hda_codec: ALC269: BIOS auto-probing.
[   16.404308] Skipping EDID probe due to cached edid

```

I don't think that it logged it though. when I look at the other dmesg log files in /var/log/, they look about the same. I presume also that the numbers on the left are seconds, so the log with the fault should not be 16 seconds long as it doesn't last that long. on another point, I am unsure what this fault is - software, hardware, OS ? as the rebooting also happens when starting windows after leaving grub. maybe it's an error with the MBR with windows and grub boot loaders wanting to run their own OS ?

---

### Post by drs305 on 2011-03-26
> **oldmannow said:**
> 
I don't think that it logged it though. 

You could take a look at dmesg.0, which would be the boot prior to the one you are running. That might include the log of how far it got before it rebooted.

If this were my machine I could have fun all day trying different things, but none of them are really worth discussing here as the probability of success for each one would be very low.

I tend to agree the problem is most likely occurring after G2 passes control to the system. The only things I can think of related to Grub would be some sort of BIOS limitation that is not allowing *certain* boot files to be seen, or something to do with the grubenv. (cat /boot/grub/grubenv )

Does the same thing happen if you do a warm reboot vs a complete poweroff and restart? 

When it reboots, does it go all the way back to the Grub menu and display it again?

---

### Post by oldmannow on 2011-03-26
ok, well hehe, I decided to wipe the linux partition and did a fresh install thinking that may do something. but no, same thing happens. even tried the older kernel - same thing still happens. even tried recovery mode - again same scenario. so I'm thinking that the OS isn't doing it, it must be grub. would it be worth getting a different version of grub? 

I looked at all the dmesg* files before - they were all pretty much the same. the same thing happens when I do a warm reboot or a complete poweroff and restart. When it reboots, it displays the grub menu as before. However, I have noticed that, after the forced reboot there is no countdown timer in the grub menu. I'm not sure if that is relevent, but it should have a 10 sec countdown before carrying on with the current selected choice. "cat /boot/grub/grubenv" just displays "# GRUB Environment Block" followed by lots of "#".

Currently trying memtest now.

---

### Post by drs305 on 2011-03-26
> **oldmannow said:**
> When it reboots, it displays the grub menu as before. However, I have noticed that, after the forced reboot there is no countdown timer in the grub menu. 

When the OS fails to complete the boot a marker is created and the next time G2 boots it awaits user input. The thinking behind it is that if an OS failed perhaps the user would want to try something different the next time... That's why you don't get the countdown.

You could try installing lilo as the bootloader. Normally we only use lilo to change where the MBR points, but you could run the installation and setup commands. I'm not convinced it's a Grub problem since you did a reinstall and the problem persists. But if you want to try lilo that will certainly take G2 out of the list of possible offenders.

From the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
You will get messages about needing to create the lilo configuration files.
I believe the next command is 
```
sudo liloconfig
```
I completely installed it once just to see how it worked. I didn't take notes but I don't recall having too much trouble getting it installed and it worked as it should, at least with Ubuntu. I didn't have Windows on the machine so I don't know how it treats multiple OS's.

---

### Post by Rubi1200 on 2011-03-26
I hope drs305 doesn't mind me jumping in, but here is a wild idea.

Even though you are not suffering some of the more usual symptoms, perhaps this has something to do with the problem?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

If you have any of the programs installed mentioned in this link, let us know please.

---

### Post by oldmannow on 2011-03-26
ok, I first updated grub to 1.99 from the natty release. slightly different menu, but same problem experienced. then I tried lilo from a live set up with a usb stick. running liloconfig brought up a warning: "your /etc/fstab configuration file gives device aufs as the root filesystem device...etc". there seems to be no option to specify the root directory, so that it is installed on /dev/sda rather than the usb stick. so, I tried it without the live set-up. this time the same error comes up but now the device is "UUID=a36...etc". the problem seemed to be that it couldn't create /etc/lilo.conf, so I wrote one. after all this, it came up with a kernel panic for linux - it has been a while since i last used lilo, but the lilo.conf was:

```


boot=/dev/sda
map=/boot/map
install=/boot/boot.b
compact
prompt
timeout=50
image=/boot/vmlinuz-2.6.35-28-generic
	label=linux
        initrd=initrd.img-2.6.35-28-generic
	root=/dev/sda6
	read-only
other=/dev/sda1
	label=winxp
```

Anyway, long story short: same thing happens, as I tried booting windows
xp and it rebooted. is it a hardward issue?

---

### Post by oldmannow on 2011-03-26
interesting link rubi. i am going to return to grub and try solution 1 on that webpage. I don't use any of the mentioned programs. the pre-install that came with the machine was formatted. I installed windows xp with this method:

[http://www.windowsvalley.com/install-windows-2000xp2003-using-usb-storage-device-pen-drive/](http://www.windowsvalley.com/install-windows-2000xp2003-using-usb-storage-device-pen-drive/)

could this have something to do with it?

---

### Post by Rubi1200 on 2011-03-26
> **oldmannow said:**
> interesting link rubi. i am going to return to grub and try solution 1 on that webpage. I don't use any of the mentioned programs. the pre-install that came with the machine was formatted. I installed windows xp with this method:

[http://www.windowsvalley.com/install-windows-2000xp2003-using-usb-storage-device-pen-drive/](http://www.windowsvalley.com/install-windows-2000xp2003-using-usb-storage-device-pen-drive/)

could this have something to do with it?
I don't know enough about installing Windows using this method to comment on whether it might affect the MBR.

Just another thought, was this disk ever part of a RAID array?

We have sometimes seen odd things happening when RAID metadata is left on a disk.

You could check from the LiveCD/USB:
```
sudo dmraid -r -E /dev/sda
```If it ask you to remove metadata, then you know this might be the problem.

Removing it will hopefully help us get further.

---

### Post by oldmannow on 2011-03-26
> **Rubi1200 said:**
> was this disk ever part of a RAID array?


Nope. dmraid confirmed it's not a raid disk.

ok, so I tried solution 1 in [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR) . But there is no difference. I did something like this:

```
sudo hexdump -C /bad_mbr > badmbr
sudo hexdump -C /mnt/good_mbr > goodmbr

diff badmbr goodmbr
```

This is enough to cook anyone's noodle  ](*,)

---

### Post by oldmannow on 2011-03-26
at least it's not just me: [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-netbook-winxp-dual-boot-grub-reboot-issue-811821/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-netbook-winxp-dual-boot-grub-reboot-issue-811821/)

---

### Post by Rubi1200 on 2011-03-26
> **oldmannow said:**
> at least it's not just me: [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-netbook-winxp-dual-boot-grub-reboot-issue-811821/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-netbook-winxp-dual-boot-grub-reboot-issue-811821/)
Indeed, and did you also notice that those users had Windows XP installed?

Have you considered trying solutions #2, 3, or 4 in the link I provided earlier? You could even use a USB stick for solution #4 I believe.

The only other thing I can think of right now would be to check if there is an update available for your BIOS or check the ACPI/Power Management settings in BIOS.

---

### Post by oldmannow on 2011-03-26
See also here

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612010](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612010)

has this bug expired? ->** "status**:                       Incomplete &#8594; Expired"

this explains what the problem is:

[http://www.sammynetbook.com/forum/threads/14035-N150-Multi-OS-Switching-gt-Reboots-Bios-Issues](http://www.sammynetbook.com/forum/threads/14035-N150-Multi-OS-Switching-gt-Reboots-Bios-Issues)

> AHCI Mode Control (initially set to auto).  The description claims it  auto detects XP and auto turns off AHCI mode which I suspect is causing  the reboots.  However manually setting AHCI mode on which should cause  no harddrive to be found on any normal XP install with no addtional  drivers does not. So even in "manual" mode the bios is still switching  harddrive modes which I believe is causing the reboots.  This I suspect  also makes installing linux based OSs difficult because they often probe  the hardware and a IDE probe / AHCI probe will both make the n150  reboot. 

My next question is then can grub work around this :?:

BTW, I do have the latest BIOS update.

---

### Post by oldmannow on 2011-03-26
Another question: if it is a winxp issue, how can i install windows 2k with no CD rom? couldn't find a usb boot loader for it. this is why i have winxp. i don't have to have winxp, just a windows release before vista that is nice and lightweight.

[Edit:] the previous link of how i installed winxp had a problem with win2k in that it keep crashing just before set-up begins.

---

### Post by Rubi1200 on 2011-03-26
> **oldmannow said:**
> See also here

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612010](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612010)

has this bug expired? ->** "status**:                       Incomplete &#8594; Expired"

this explains what the problem is:

[http://www.sammynetbook.com/forum/threads/14035-N150-Multi-OS-Switching-gt-Reboots-Bios-Issues](http://www.sammynetbook.com/forum/threads/14035-N150-Multi-OS-Switching-gt-Reboots-Bios-Issues)

 

My next question is then can grub work around this :?:

BTW, I do have the latest BIOS update.
To answer this and your next question;

1. did you notice post #10 in the bug report? Apparently reverting to legacy-GRUB resolved the issue for that user
2. I am not suggesting this is a Windows XP issue, I just thought it was interesting that it appears to be only with XP installed

If BIOS is not the issue, then perhaps it is an AHCI problem and the workaround might be to try reverting to the older version of GRUB (you can always change this afterwards if it doesn't help).

---

### Post by oldmannow on 2011-03-26
tried the older version of grub, but the same issue experienced.

---

### Post by Rubi1200 on 2011-03-26
I'm not giving up, but I have to admit I am out of ideas right now.

I don't know if you have backups of your respective systems, which would be a good idea anyway, but you might want to consider doing so and then starting afresh.

You mentioned having installed Ubuntu and then XP followed by a GRUB reinstall.

Perhaps try installing XP first, make sure it works, and then Ubuntu.

GRUB will then default to creating a dual-boot configuration.

I don't know if you want to go to the trouble of doing this and I will continue to look for alternative solutions.

---

### Post by oldmannow on 2011-03-26
I can wipe the whole disk if needed, but i believe it has to do something with the bios - ahci probing from grub or something? for now, I leave it for tomorrow :wink:

---

### Post by oldmannow on 2011-04-03
In case anyone is interested, this is now solved. The solution was to use Windows 7 instead of Windows XP. The problem isn't grub, ubuntu or anything else. It is just how XP is made/supported. XP doesn't support SATA natively, but can do it in legacy mode. The bios tries to attempt to figure out the settings automatically, and I think the rebooting is the bios trying to change the setting. The XP SATA drivers from Intel actually don't do much or have any significant effect. The options available in the samsung n150 are quite poor and you basically cannot set it strictly manually to be just one mode for AHCI. It relies on the bios finding out most of the information and seems to do some background configuration, whatever option is selected. The only reason why I chose XP was to have a fast windows OS to run some things. windows 7 seems quick enough though.

In short, there is no problem with ubuntu/grub :)

---

