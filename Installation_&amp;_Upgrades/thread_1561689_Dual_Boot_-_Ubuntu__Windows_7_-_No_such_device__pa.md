---
title: "Dual Boot - Ubuntu / Windows 7 - No such device / partition / invalid signature"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by andypike on 2010-08-26
Hi,

I had a dual boot Windows 7 / OpenSUSE setup but have just ditched OpenSUSE for Ubuntu.  After the installation Ubuntu boots without any problems.  It also detected two two Windows 7 installations (both on separate drives) but I am currently unable to boot into either of them - can someone please help?

I am not really new to Linux but am new to Ubuntu and Grub2.  As such, I'm finding the fix somewhat difficult to figure out.  After reading another post, someone ran a boot_info_script from:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

My output after running 'sudo bash boot_info_script*.sh' is:

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sde

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sde2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   312,578,047   312,371,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848 2,930,274,303 2,930,067,456   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3000.0 GB, 2999999004672 bytes
255 heads, 63 sectors/track, 364729 cylinders, total 5859373056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sde1           2,048         4,095         2,048 Bios Boot Partition
/dev/sde2           4,096 2,565,943,295 2,565,939,200 Linux or Data
/dev/sde3   2,565,943,296 2,638,145,535    72,202,240 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0E8E004E8E0030AF                       ntfs       System Reserved               
/dev/sda2        D414081F14080768                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9C9215B99215993A                       ntfs       System Reserved               
/dev/sdb2        84FE1821FE180DD4                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sde2        2bfb0a2e-30bd-45e8-882a-2e758b5f2314   ext4                                     
/dev/sde3        dc9be1d7-0bbc-4350-8740-e433fe0b3fe6   swap                                     
/dev/sde: PTTYPE="gpt" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde2        /                        ext4       (rw,errors=remount-ro)


=========================== sde2/boot/grub/grub.cfg: ===========================

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
set root='(hd2,2)'
search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
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
set root='(hd2,2)'
search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2bfb0a2e-30bd-45e8-882a-2e758b5f2314 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2bfb0a2e-30bd-45e8-882a-2e758b5f2314 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2bfb0a2e-30bd-45e8-882a-2e758b5f2314 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2bfb0a2e-30bd-45e8-882a-2e758b5f2314 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 2bfb0a2e-30bd-45e8-882a-2e758b5f2314
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e8e004e8e0030af
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9c9215b99215993a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde2 during installation
UUID=2bfb0a2e-30bd-45e8-882a-2e758b5f2314 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde3 during installation
UUID=dc9be1d7-0bbc-4350-8740-e433fe0b3fe6 none            swap    sw              0       0

=================== sde2: Location of files loaded by Grub: ===================


1030.9GB: boot/grub/core.img
1761.4GB: boot/grub/grub.cfg
1030.9GB: boot/initrd.img-2.6.32-21-generic
1030.9GB: boot/initrd.img-2.6.32-24-generic
1030.9GB: boot/vmlinuz-2.6.32-21-generic
1030.9GB: boot/vmlinuz-2.6.32-24-generic
1030.9GB: initrd.img
1030.9GB: initrd.img.old
1030.9GB: vmlinuz
1030.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 

```If someone could let me know what the problem is here and suggest a way to fix it - I would be very grateful.

Also, should I be worried about anything else highlighted in the output?  Specifically:

```

error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

```Many thanks for your help.

---

### Post by srs5694 on 2010-08-26
The /dev/sdc and /dev/sdd "no medium found" messages make sense if you've got any removable disks (Zip disks, MO drives, etc.). If you've only got traditional fixed disks, they're more puzzling. You'll need to describe your disk hardware if you need more advice on that one.

As to the main problem, I note that /dev/sde uses a GUID Partition Table (GPT) rather than the more common Master Boot Record (MBR), but /dev/sda and /dev/sdb are both MBR disks. I've seen some posts suggesting that GRUB can get confused in such mixed-table setups. There's a solution that involves adding a couple of lines to the GRUB configuration file, but I don't recall the exact commands. I believe that a user here with the username "oldfred" has posted the solution several times, so maybe you could look for his recent posts.

---

### Post by oldfred on 2010-08-26
This is my standard post on gpt.

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
Or:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
I added insmod part_msdos to 40_custom & both windows on sda1 and Ubuntu
on sdc5 booted without any issues. 


The newest versions of grub seem to be adding this automatically as I see it in my Maverick install which I put on my gpt drive.

---

### Post by andypike on 2010-08-28
Hi and thank you both for identifying the problem.

srs5694, I think the "no medium found" errors are to do with the fake RAID controller I'm using.  I have an Intel SASWT4I with 4 drives connected in a RAID 0+1 configuration (plus the two Windows drives).  I think sdc and sdd are two of the four disks?!  I'm still not sure whether this means there is a problem with my RAID or not.  All appears to be okay from the BIOS.  Any help would be appreciated.

oldfred, thanks for the links - they were very useful / interesting.  I fixed the problem by doing as you said:

```

sudo gedit /etc/default/grub

```# Added the following line:
GRUB_PRELOAD_MODULES="part_msdos"

And then ran:

```

sudo update-grub

```Once I rebooted I could boot to both the other Windows 7 drives.  Nice one, thanks!

I tried to run the boot info script again to see if I still got the "no medium" errors... I do.  Is this still part of the mixed partition tables problem?

---

### Post by oldfred on 2010-08-28
It may not be a problem. It may just be the script.

The script is designed to parse a lot of different commands and try to determine from them what configuration you have. Raid is not too common on desktops and it usually just says RAID, your version may be something it just cannot parse as it has a list of responses and if it is not one of the standards it returns an error.

---

### Post by srs5694 on 2010-08-28
Try posting the output of the following commands:

```

udevadm info -a -p $(udevadm info -q path -n /dev/sda)
udevadm info -a -p $(udevadm info -q path -n /dev/sdb)
udevadm info -a -p $(udevadm info -q path -n /dev/sdc)
udevadm info -a -p $(udevadm info -q path -n /dev/sdd)
udevadm info -a -p $(udevadm info -q path -n /dev/sde)

```

Note that each one produces over 70 lines of output, so that'll be quite a bit in total. These commands, though, will produce technical information on the hardware to which each of the device files points, which should help us figure out what's going on.

That said, I doubt if there's really a serious problem, in the sense of something that will cause data loss or other detrimental effects. Chances are it's something quirky about the configuration or drivers -- perhaps an issue with your RAID setup, as you suggested.

---

### Post by andypike on 2010-08-29
Thanks so much for your reply.  Here are the outputs you asked for:

sudo udevadm info -a -p $(udevadm info -q path -n /dev/sda):
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="312581808"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="52"
    ATTR{stat}=="     159        3     1296      730        0        0        0        0        0      580      730"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0':
    KERNELS=="0:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="Hitachi HDS72101"
    ATTRS{rev}=="JPEO"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xca"
    ATTRS{iodone_cnt}=="0xca"
    ATTRS{ioerr_cnt}=="0xd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="31"
    ATTRS{queue_type}=="simple"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0':
    KERNELS=="target0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0':
    KERNELS=="host0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2':
    KERNELS=="0000:00:1f.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ahci"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a22"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x010601"
    ATTRS{irq}=="56"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00003A22sv00001043sd000082D4bc01sc06i01"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```sudo udevadm info -a -p $(udevadm info -q path -n /dev/sdb):
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0/5:0:0:0/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="2930277168"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="52"
    ATTR{stat}=="     159        3     1296      310        0        0        0        0        0      260      310"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0/5:0:0:0':
    KERNELS=="5:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="ST31500341AS    "
    ATTRS{rev}=="CC1H"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xc9"
    ATTRS{iodone_cnt}=="0xc7"
    ATTRS{ioerr_cnt}=="0xa"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="31"
    ATTRS{queue_type}=="simple"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0':
    KERNELS=="target5:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5':
    KERNELS=="host5"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2':
    KERNELS=="0000:00:1f.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ahci"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a22"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x010601"
    ATTRS{irq}=="56"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00003A22sv00001043sd000082D4bc01sc06i01"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```sudo udevadm info -a -p $(udevadm info -q path -n /dev/sdc):
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host6/target6:0:0/6:0:0:0/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="234441648"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="52"
    ATTR{stat}=="     181     8220     9060     1420        0        0        0        0        0     1080     1420"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Ext Hard"
    ATTRS{model}==" Disk           "
    ATTRS{rev}=="    "
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xce"
    ATTRS{iodone_cnt}=="0xce"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host6/target6:0:0':
    KERNELS=="target6:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host6':
    KERNELS=="host6"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0':
    KERNELS=="2-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v059Bp027Ad0000dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"
    ATTRS{interface}=="Mass Storage"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-5':
    KERNELS=="2-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="Config0"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="743"
    ATTRS{idVendor}=="059b"
    ATTRS{idProduct}=="027a"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Iomega"
    ATTRS{product}=="Iomega HDD USB2.0 Drive"
    ATTRS{serial}=="S07I2501A00000282232"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="64"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-24-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a3a"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```sudo udevadm info -a -p $(udevadm info -q path -n /dev/sdd):
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0/0000:04:00.0/host7/target7:1:0/7:1:0:0/block/sdd':
    KERNEL=="sdd"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="5859373056"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="52"
    ATTR{stat}=="   11416     5410   891242   389110     3099     5441    67936  2165350        0    99140  2554460"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0/0000:04:00.0/host7/target7:1:0/7:1:0:0':
    KERNELS=="7:1:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Intel   "
    ATTRS{model}=="Logical Volume  "
    ATTRS{rev}=="3000"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x38a4"
    ATTRS{iodone_cnt}=="0x38a4"
    ATTRS{ioerr_cnt}=="0x7"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="64"
    ATTRS{queue_type}=="simple"

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0/0000:04:00.0/host7/target7:1:0':
    KERNELS=="target7:1:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0/0000:04:00.0/host7':
    KERNELS=="host7"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0/0000:04:00.0':
    KERNELS=="0000:04:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="mptsas"
    ATTRS{vendor}=="0x1000"
    ATTRS{device}=="0x0056"
    ATTRS{subsystem_vendor}=="0x1000"
    ATTRS{subsystem_device}=="0x3090"
    ATTRS{class}=="0x010000"
    ATTRS{irq}=="24"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001000d00000056sv00001000sd00003090bc01sc00i00"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0/0000:03:00.0':
    KERNELS=="0000:03:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x05b1"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd000005B1sv00000000sd00000000bc06sc04i00"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:03.0/0000:02:00.0':
    KERNELS=="0000:02:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x05b1"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd000005B1sv00000000sd00000000bc06sc04i00"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:03.0':
    KERNELS=="0000:00:03.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x340a"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="49"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d0000340Asv00000000sd00000000bc06sc04i00"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="2"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```sudo udevadm info -a -p $(udevadm info -q path -n /dev/sde):
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1/2-3.1.1:1.0/host8/target8:0:0/8:0:0:0/block/sde':
    KERNEL=="sde"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="       0        0        0        0        0        0        0        0        0        0        0"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1/2-3.1.1:1.0/host8/target8:0:0/8:0:0:0':
    KERNELS=="8:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="Generic "
    ATTRS{model}=="Flash HS-CF     "
    ATTRS{rev}=="4.44"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xd5a"
    ATTRS{iodone_cnt}=="0xd5a"
    ATTRS{ioerr_cnt}=="0xd59"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1/2-3.1.1:1.0/host8/target8:0:0':
    KERNELS=="target8:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1/2-3.1.1:1.0/host8':
    KERNELS=="host8"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1/2-3.1.1:1.0':
    KERNELS=="2-3.1.1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v0424p2228d0444dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1.1':
    KERNELS=="2-3.1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="34187"
    ATTRS{idVendor}=="0424"
    ATTRS{idProduct}=="2228"
    ATTRS{bcdDevice}=="0444"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="9"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Generic"
    ATTRS{product}=="Flash Card Reader"
    ATTRS{serial}=="070717200626"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1':
    KERNELS=="2-3.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="29"
    ATTRS{idVendor}=="0424"
    ATTRS{idProduct}=="2602"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="02"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="8"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="4"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3':
    KERNELS=="2-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="24"
    ATTRS{idVendor}=="0424"
    ATTRS{idProduct}=="2502"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="64"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-24-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a3a"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="00000000,000000ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20"
    ATTRS{numa_node}=="-1"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by srs5694 on 2010-08-29
It appears that /dev/sda and /dev/sdb are normal SATA disks made by Hitachi and Seagate, respectively. /dev/sdc is an Iomega USB device (a Zip drive, perhaps?). /dev/sdd I'm less clear about, but it seems to be some sort of Intel meta-device. Perhaps you've got RAID mode enabled on your motherboard and it's turning up like this? /dev/sde is a generic USB flash drive.

---

### Post by RobChem on 2011-10-26
This solution worked for me as well.
The difference is the second OS was Windows XP-64, all the other features are the same i.e. GUID Partition Table (GPT) on linux and Master Boot Record (MBR) for windows.
 
I reinstalled ubuntu on a new disk after the old one died.
Somewhere in the process the windows disk got changed so it wouldn't boot by itself any more or with GRUB. I fixed it using "Boot-repair-disk" to redo the MBR
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
After this GRUB still wouldn't boot to windows, reporting "no such device/invalid siganture"
Adding the line to /etc/default/grub fixed it.
 
Thank you for posting the fix
 
[QUOTE=andypike;9777123]I fixed the problem by doing as you said:
 
```

sudo gedit /etc/default/grub

```# Added the following line:
GRUB_PRELOAD_MODULES="part_msdos"
 
And then ran:
 
```

sudo update-grub

```

---

