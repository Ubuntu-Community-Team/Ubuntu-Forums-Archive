---
title: "Hard drive/Grub help"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by tommah04 on 2010-12-08
hey all,

got a problem here and not really sure how to proceed.

I have 2 internal hard drives, lets call them A and B

I recently had to reinstall ubuntu on A and everything went fine.  when I restarted it said something along the lines of Grub Error: no such disk.  I turned off the computer and unplugged B and restarted just fine, no errors or anything.  I even dual-boot Win 7 and that works just fine.  Turned it off and plugged B back in, same thing Grub Error.... 

confused I restarted and went to BIOS to look at boot devices with both A and B plugged in.  It only lists B as a bootable hard drive and doesn't even show A.  shut the computer down and unplugged B, went into BIOS and now A shows up as bootable.

Its like B is taking priority over A when I want it the other way around.  Is it possible I accidentally installed Grub on B so B keeps trying to boot to an OS?  or is something seriously wrong?

thanks in advance!

Tom

---

### Post by ronparent on 2010-12-08
It sounds like a hardware problem. Possibly a loose connection on drive a, possibly a failing drive, a failing bios, etc. You would need to chase that down. You could change the boot order and reinstall grub to boot on b, but if a hardware problem, that wouldn't solve anything.

---

### Post by sikander3786 on 2010-12-09
The HDDs are IDE? It might be a simple Master/Slave problem. Make your Grub HDD master drive and the other one slave, plug both and try to boot from the Grub one.

If thats not the problem, while both the HDDs are plugged in, boot from an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by tommah04 on 2010-12-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=eac45c51-7efc-4021-8b2e-dd3d58859a50)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdb3: _________________________________________________________________________

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

Disk /dev/sda: 800.2 GB, 800166076416 bytes
255 heads, 63 sectors/track, 97281 cylinders, total 1562824368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,562,820,607 1,562,818,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848 1,113,316,878 1,113,110,031   7 HPFS/NTFS
/dev/sdb3       1,113,317,374 1,953,523,711   840,206,338   5 Extended
/dev/sdb5       1,113,317,376 1,953,093,631   839,776,256  83 Linux
/dev/sdb6       1,953,095,680 1,953,523,711       428,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F664B91A64B8DF15                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA78EBD978EBA295                       ntfs       System Reserved               
/dev/sdb2        A638EF2F38EEFCE5                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        3486dfce-5e4a-42ac-a4ee-9ee832ec70b4   ext4                                     
/dev/sdb6        e3596b89-0e22-49cc-99ca-f15722d58ac6   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3486dfce-5e4a-42ac-a4ee-9ee832ec70b4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3486dfce-5e4a-42ac-a4ee-9ee832ec70b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3486dfce-5e4a-42ac-a4ee-9ee832ec70b4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ea78ebd978eba295
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
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 580.9GB: boot/grub/core.img
 583.1GB: boot/grub/grub.cfg
 570.5GB: boot/initrd.img-2.6.35-22-generic
 580.8GB: boot/vmlinuz-2.6.35-22-generic
 570.5GB: initrd.img
 580.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by tommah04 on 2010-12-09
I believe it says that Grub 2 is install on sdb, but there shouldn't be Grub there cause there isn't supposed to be any OS... sda is the only HDD with operating systems

oh, and my HDD's are SATA


EDIT:
nvm I think I mixed up sdb and sda...

---

### Post by dino99 on 2010-12-09
you have grub2 installed on both sda & sdb mbr, and might be only on /dev/sdb

so you need to clean the room with synaptic:

run the ubuntu system with both hdds plugged but set the bios to "compatible" (the best) or "ahci" and select to boot on the ubuntu hdd

then with synaptic:
- remove/purge: grub-common and grub-pc
- then reinstall grub-pc and choose /dev/sdb when asked for installation

next boot might be ok

---

### Post by tommah04 on 2010-12-09
ok, I figured it out.  I started to do what you ^ told me to do and while I was in the BIOS I noticed that BIOS changed around my hard drives so that sda was my master and sdb was slave.  switch that back and Hazaah, done.

although I still want to work on what you said since I'm more than certain Grub is installed on my "storage" hdd

thanks yet again ubuntu forums!

---

### Post by sikander3786 on 2010-12-09
> I noticed that BIOS changed around my hard drives so that sda was my master and sdb was slave

There was a hint in my above post for master/slave problem ;-)

> I'm more than certain Grub is installed on my "storage" hdd

Grub is installed not only to your 'storage' HDD but actually both of them. Did you read this in your boot script output?

>  => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=eac45c51-7efc-4021-8b2e-dd3d58859a50)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

So, what **dino99** said, is the best workaround here.

---

