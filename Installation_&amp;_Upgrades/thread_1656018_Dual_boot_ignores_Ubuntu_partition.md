---
title: "Dual boot ignores Ubuntu partition"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by G1ZmO65 on 2010-12-30
Hi,

I've done a clean install of XP Pro on my HP XW8200 (Boot drive is 2x73GB SCSI drives set up as RAID 1)

I've run the Ubuntu 10.10 desktop installer and partitioned the drive, installed ubuntu and rebooted when requested.

No OS selection screen appears after POST though. Just goes straight into WinXP. The startup options in XP only show XP.

Rebooted from the Ub10.10 live cd and checked that the partition is there and the OS files are there.

Any ideas why the grub menu doesnt appear?

I'm assuming it's something to do with Ubuntu not seeing the RAID drive but it did install ok.....

Thanks

Paul

---

### Post by Rubi1200 on 2010-12-30
Hi Paul,
the most likely explanation I can think of right now is that GRUB was not installed properly.

To confirm this, and/or other booting issues, please boot the computer with the LiveCD.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by G1ZmO65 on 2010-12-30
Thanks Rubi

I'll give this a go. PC is at work and I'm not due back until the 5th so I'll not get a chance before then.

Will let you know how it goes

Paul

---

### Post by Rubi1200 on 2010-12-30
Sure, no problem.

I will check back on this thread once you have posted the results.

Enjoy your holiday.

---

### Post by G1ZmO65 on 2011-01-05
Here are the results Rubi,

Thanks

Paul

---

### Post by Rubi1200 on 2011-01-05
Hi Paul,
thanks for the results.

There are a couple of things here I don't understand.

1. what is/was on sda? Right now nothing is showing up.

2. in your first post you mentioned a RAID1 setup, but I don't see that either?

3. how is the boot priority set in BIOS; sda or sdb as first boot device?

Once we get this clarified, then I will explain why Ubuntu is not booting (with the current setup).


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 129434080 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 73.3 GB, 73272393728 bytes
255 heads, 63 sectors/track, 8908 cylinders, total 143110144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   103,974,039   103,973,977   7 HPFS/NTFS
/dev/sdb2         103,974,910   143,108,095    39,133,186   5 Extended
/dev/sdb5         103,974,912   141,385,727    37,410,816  83 Linux
/dev/sdb6         141,387,776   143,108,095     1,720,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1CC01AFBC01ADABA                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3   ext4                                     
/dev/sdb6        baf52bcb-0baf-40f2-913b-37005d5ace56   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 1cc01afbc01adaba
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=4486dfde-85d9-46c0-9e7d-fe9fdfb5e4b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=baf52bcb-0baf-40f2-913b-37005d5ace56 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  66.2GB: boot/grub/core.img
  53.5GB: boot/grub/grub.cfg
  54.1GB: boot/initrd.img-2.6.35-24-generic-pae
  66.2GB: boot/vmlinuz-2.6.35-24-generic-pae
  54.1GB: initrd.img
  66.2GB: vmlinuz
```

---

### Post by G1ZmO65 on 2011-01-05
> **Rubi1200 said:**
> Hi Paul,
1. what is/was on sda? Right now nothing is showing up. - This is an unused 160GB SATA drive 

2. in your first post you mentioned a RAID1 setup, but I don't see that either? - /dev/sdb: 73.3 GB is the RAID1 drive

3. how is the boot priority set in BIOS; sda or sdb as first boot device?
- Controller order is 1-RAID 2-IDE 3-SATA


See above for answers 

Paul

---

### Post by Rubi1200 on 2011-01-05
Okay, so here is the problem (as I see it according to the results):

> Grub 2 is installed in the MBR of /dev/sda and looks at sector 129434080 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

GRUB needs to be installed in the MBR of sdb.

So, from a LiveCD this is what we can do:

```
sudo mount /dev/sdb5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Once back in Ubuntu, run this to pick up the Windows install for a dual-boot:
```
sudo update-grub
```

---

### Post by G1ZmO65 on 2011-01-05
Brilliant! Sorted, thank you so much.

Can you explain briefly why this happened though?

Many thanks 

Paul

---

### Post by Rubi1200 on 2011-01-05
No problem, you are more than welcome :-)

Why did this happen? 

Just speculating here, but perhaps the installer recognized sda as the main drive rather than the RAID. 

In any event, I am glad this worked out for you.

Please mark the thread Solved using the Thread Tools near the top of the page.

---

