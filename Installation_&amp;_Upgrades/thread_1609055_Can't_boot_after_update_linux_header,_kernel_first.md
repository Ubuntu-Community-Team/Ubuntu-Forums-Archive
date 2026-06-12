---
title: "Can't boot after update: linux header, kernel first"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by crazyjpeters on 2010-10-29
After getting everything running nicely on 10.10 (after dozens of installs - long story, partially raid problem, partially noob, partially partitioning and Windows), I'm stuck with an unbootable 10.10.

I selected all the "important security updates" when the update manager told me I needed to update everything.  Upon rebooting, and picking ubuntu in grub, I get:

Error: unknown command 'record fail'
Error: cannot read the Linux header
Error: you need to load the kernel first

Not exactly sure why at this point.  Can anyone point me in the right direction? I can probably get in either through a 10.04 version that I have on another HDD, or through the livecd.

Note: if it's important, I did not elect to install the ATI proprietary drivers, and this is also the first update that I've done after installing medibuntu - a few boot cycles in between, so I don't think it's related.

Please help, if you can...

Thanks,

---

### Post by drs305 on 2010-10-29
crazyjpeters,

Welcome to the Ubuntu forums.

You can try to boot from the grub rescue prompt (if you get one) with the following link:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

or boot to the LiveCD and run the boot info script from this site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
Post the contents of the RESULTS.txt here, between code tags which you generate by pressing the # icon in the post's menubar.

I'm signing off for the night but will check back in the morning to see if someone has assisted you.

---

### Post by crazyjpeters on 2010-10-29
Here it is.  Note that the RAID1 boot disk is isw_ghgbeighe_System, consisting of sda and sdb.  sde is where my old 10.04 resides.

               ```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
# funny since sda and sdb share the RAID1, I would have thought sdb would also have Grub 2
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.
# that's the 10.04 I mentioned
 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_chbdeieafg_RAID1(Data)
 => Grub 2 is installed in the MBR of /dev/mapper/isw_ghgbeighe_System and 
    looks on the same drive in partition #3 for (,msdos3)/grub.
#what I was booting too is /dev/mapper/isw_ghgbeighe_System and the Grub still works there

#deleted a bunch of junk about sda1 to sda7 not being able to mount

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_chbdeieafg_RAID1(Data)1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_chbdeieafg_RAID1(Data)2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_chbdeieafg_RAID1(Data)3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_ghgbeighe_System1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

isw_ghgbeighe_System2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_ghgbeighe_System3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

isw_ghgbeighe_System4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_ghgbeighe_System5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_ghgbeighe_System6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

isw_ghgbeighe_System7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   167,774,207   167,772,160   7 HPFS/NTFS
/dev/sda2         167,774,208   399,894,527   232,120,320   7 HPFS/NTFS
/dev/sda3         399,894,528   400,099,327       204,800  83 Linux
/dev/sda4         400,101,374   488,390,655    88,289,282   5 Extended
/dev/sda5         400,101,376   412,684,287    12,582,912  82 Linux swap / Solaris
/dev/sda6         412,686,336   446,240,767    33,554,432  83 Linux
/dev/sda7         446,242,816   488,390,655    42,147,840  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   955,625,471   955,623,424  83 Linux
/dev/sde2         955,627,518   976,773,119    21,145,602   5 Extended
/dev/sde5         955,627,520   976,773,119    21,145,600  82 Linux swap / Solaris


Drive: isw_chbdeieafg_RAID1(Data) ___________________ _____________________________________________________

Disk /dev/mapper/isw_chbdeieafg_RAID1(Data): 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_chbdeieafg_RAID1(Data)1                 63   419,425,019   419,424,957   7 HPFS/NTFS
/dev/mapper/isw_chbdeieafg_RAID1(Data)2        419,425,020   629,137,529   209,712,510   7 HPFS/NTFS
/dev/mapper/isw_chbdeieafg_RAID1(Data)3        629,137,530   976,751,999   347,614,470   7 HPFS/NTFS


Drive: isw_ghgbeighe_System ___________________ _____________________________________________________

Disk /dev/mapper/isw_ghgbeighe_System: 250.1 GB, 250056151040 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488390920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_ghgbeighe_System1   *          2,048   167,774,207   167,772,160   7 HPFS/NTFS
/dev/mapper/isw_ghgbeighe_System2        167,774,208   399,894,527   232,120,320   7 HPFS/NTFS
/dev/mapper/isw_ghgbeighe_System3        399,894,528   400,099,327       204,800  83 Linux
/dev/mapper/isw_ghgbeighe_System4        400,101,374   488,390,655    88,289,282   5 Extended
/dev/mapper/isw_ghgbeighe_System5        400,101,376   412,684,287    12,582,912  82 Linux swap / Solaris
/dev/mapper/isw_ghgbeighe_System6        412,686,336   446,240,767    33,554,432  83 Linux
/dev/mapper/isw_ghgbeighe_System7        446,242,816   488,390,655    42,147,840  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_chbdeieafg_RAID1(Data)1 3C48484C484806DC                       ntfs       DOCS_MAIN                     
/dev/mapper/isw_chbdeieafg_RAID1(Data)2 8A04E60604E5F55B                       ntfs       DOCS_PICS                     
/dev/mapper/isw_chbdeieafg_RAID1(Data)3 6600FDEF00FDC5D9                       ntfs       DOCS_VIDS                     
/dev/mapper/isw_chbdeieafg_RAID1(Data): PTTYPE="dos" 
/dev/mapper/isw_ghgbeighe_System1 5C8692558692300E                       ntfs       Windows7                      
/dev/mapper/isw_ghgbeighe_System2 C46AA20D6AA1FC74                       ntfs       Storage                       
/dev/mapper/isw_ghgbeighe_System3 79743d7b-3800-4264-8282-d5c154f89bde   ext3       boot                          
/dev/mapper/isw_ghgbeighe_System5 1c48c1bc-f63c-4eaa-8afd-5dcdef3698a5   swap                                     
/dev/mapper/isw_ghgbeighe_System6 3253ffe5-03af-44e5-8b4a-de4a15408f60   ext4       uroot                         
/dev/mapper/isw_ghgbeighe_System7 8ef9893a-2d3c-4b16-a854-e995e2f22515   ext4       uhome                         
/dev/mapper/isw_ghgbeighe_System: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
/dev/sde1        bca95aff-177e-4d62-90ee-4aed8f4551bd   ext4                                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        8412a766-a7d5-421c-9655-22283e68ac1d   swap                                     
/dev/sde: PTTYPE="dos" 
error: and: No such file or directory
error: /dev/mapper//dev/sda:: No such file or directory
error: /dev/mapper//dev/sdb:: No such file or directory
error: /dev/mapper/isw_ghgbeighe_System4: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory
error: /dev/sda7: No such file or directory
error: discovered: No such file or directory
error: formats: No such file or directory
error: "isw": No such file or directory
error: isw)!: No such file or directory
error: "pdc": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_chbdeieafg_RAID1(Data)
isw_chbdeieafg_RAID1(Data)1
isw_chbdeieafg_RAID1(Data)2
isw_chbdeieafg_RAID1(Data)3
isw_ghgbeighe_System
isw_ghgbeighe_System1
isw_ghgbeighe_System2
isw_ghgbeighe_System3
isw_ghgbeighe_System5
isw_ghgbeighe_System6
isw_ghgbeighe_System7

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/mapper/isw_cdeibeagdc_RAID1(System)1)" {
    insmod ntfs
    set root='(hd4,1)'
    search --no-floppy --fs-uuid --set 0c947fac947f9744
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=8412a766-a7d5-421c-9655-22283e68ac1d none            swap    sw              0       0

=================== sde1: Location of files loaded by Grub: ===================


 313.7GB: boot/grub/core.img
  56.0GB: boot/grub/grub.cfg
 313.9GB: boot/initrd.img-2.6.32-23-generic-pae
    .9GB: boot/initrd.img-2.6.32-24-generic-pae
 313.8GB: boot/vmlinuz-2.6.32-23-generic-pae
 314.0GB: boot/vmlinuz-2.6.32-24-generic-pae
    .9GB: initrd.img
 313.9GB: initrd.img.old
 314.0GB: vmlinuz
 313.8GB: vmlinuz.old

===================== isw_ghgbeighe_System3/grub/grub.cfg: =====================

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
set root='(/dev/mapper/isw_ghgbeighe_System,msdos6)'
search --no-floppy --fs-uuid --set 3253ffe5-03af-44e5-8b4a-de4a15408f60
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_ghgbeighe_System,msdos3)'
search --no-floppy --fs-uuid --set 79743d7b-3800-4264-8282-d5c154f89bde
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_ghgbeighe_System,msdos3)'
    search --no-floppy --fs-uuid --set 79743d7b-3800-4264-8282-d5c154f89bde
    linux    /vmlinuz-2.6.35-22-generic root=UUID=3253ffe5-03af-44e5-8b4a-de4a15408f60 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_ghgbeighe_System,msdos3)'
    search --no-floppy --fs-uuid --set 79743d7b-3800-4264-8282-d5c154f89bde
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=3253ffe5-03af-44e5-8b4a-de4a15408f60 ro single 
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
    set root='(/dev/mapper/isw_ghgbeighe_System,msdos3)'
    search --no-floppy --fs-uuid --set 79743d7b-3800-4264-8282-d5c154f89bde
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_ghgbeighe_System,msdos3)'
    search --no-floppy --fs-uuid --set 79743d7b-3800-4264-8282-d5c154f89bde
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode) (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set bca95aff-177e-4d62-90ee-4aed8f4551bd
    linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=bca95aff-177e-4d62-90ee-4aed8f4551bd ro single
    initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Windows 7 (loader) (on /dev/mapper/isw_ghgbeighe_System1)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_ghgbeighe_System,msdos1)'
    search --no-floppy --fs-uuid --set 5c8692558692300e
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

=========== isw_ghgbeighe_System3: Location of files loaded by Grub: ===========


 204.8GB: grub/core.img
 204.8GB: grub/grub.cfg
 204.7GB: initrd.img-2.6.35-22-generic
 204.7GB: vmlinuz-2.6.35-22-generic

======================= isw_ghgbeighe_System6/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_ghgbeighe_System6 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_ghgbeighe_System3 /boot           ext3    defaults        0       2
/dev/mapper/isw_ghgbeighe_System7 /home           ext4    defaults        0       2
/dev/mapper/isw_ghgbeighe_System5 none            swap    sw              0       0
# swap was on /dev/sde5 during installation
UUID=8412a766-a7d5-421c-9655-22283e68ac1d none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on isw_ghgbeighe_System4



=======Devices which don't seem to have a corresponding hard drive==============

sdb: "pdc" and "isw" formats discovered (using isw)! sda: "pdc" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: only one argument allowed for this option
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/mapper/isw_ghgbeighe_System4: No such file or directory
hexdump: /dev/mapper/isw_ghgbeighe_System4: No such file or directory
ERROR: only one argument allowed for this option

```

---

### Post by ronparent on 2010-10-30
On installing you apparently setup isw_ghgbeighe_System3 as a boot partition. The kernel update should have gone there. Did it or is it in isw_ghgbeighe_System6 where 10.10 is installed? I would examine both partitions to see what is in /boot (if any) in each. Post back what you find.

---

### Post by ronparent on 2010-10-30
On looking over the boot info summary in your results file I realized you had added you own notes. To clarify, to boot to a 'fake' raid system the operative grub boot loader has to be on /dev/mapper/isw_ghgbeighe_System and that should be set as boot in bios also.

Also, although booting to a separate /boot partition is permitted, it is not necessary in your case and perhaps over complicates a complicated setup to begin with. With a raid1 system especially it is, in the right circumstance, possible to boot to an individual drive for one of the raid members but I don't think for your system. And in any case it would not be valid to retain the integrity of the raid between the raid pair. 

I think you may have to fix the boot to the raid before you will be able to make any headway on any remaining problems.

---

### Post by crazyjpeters on 2010-11-01
The /dev/mapper/isw_ghgbeighe_System was set as the location for the bootloader.  And BIOS starts booting there also (if no USB-HDD and CD-ROM are found).
 
I recovered my Windows MBR, and tried formatting all the partitions in Gparted (gparted livecd, not the ubuntu distribution), and reinstalling 10.10 cleanly.  No go.  Made it all the way through installation, and just boots straight into windows again.
 
Not sure how, but when I reformat the entire disk, partition in Gparted, and clean install 10.10, it works fine (until I update ubuntu w/ update manager).  So something is not being done the same when I clean out the partitions and clean up the mbr with Win7 rescue disk.  Grub is either not being seen, or???
 
I'm pretty close to giving up.  Anyone have luck with a RAID1 and 10.04.1 dual boot win7?

---

