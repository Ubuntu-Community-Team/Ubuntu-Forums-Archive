---
title: "Grub2, sda=Win7, sdb=10.04"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2010-09-15
Two SATA drives with 
Windows 7 OEM on the first SATA (sda0)
Ubuntu 10.04  on the next SATA (sdb0)

The install went correctly up until the Synaptic Update for Grub2. No boot after that. None of the Command-Line recipes seems to fix Grub for me.

I would like to fix Grub and make sure Windows still runs. I have attached the RESULTS.txt of [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

[[ Note: if you look at RESULTS.txt, it will show partition sdb3 has a copy of ubuntu 10.04, ubuntu 10.10, it says, is on sdb1. For now I just want grub to boot the Windows partition and the ubuntu 10.10 ]]*

======
*My iso of 10.10 is mis-labled as a download, as an iso, as a running install and other places. When that version is running, 'Help=>About' says it is 10.04 LTS. After I fix GRUB I may use the CD that is the for-real 10.04 ubuntu for a re-install, but Grub2 has failed me thrice.

---

### Post by wilee-nilee on 2010-09-15
The script output text is not attached, post the whole text and put it in code tags, as described in my signature.

---

### Post by Unterseeboot_234 on 2010-09-15
okay, here is posted RESULTS.txt. Let's evaluate it. And, see paragraph following at end of this new thread...

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

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

/dev/sda1               2,048   944,531,455   944,529,408   7 HPFS/NTFS
/dev/sda2    *    944,531,456   976,771,071    32,239,616  27 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   625,249,799   625,247,752  83 Linux
/dev/sdb2       1,235,575,215 1,929,759,929   694,184,715  83 Linux
/dev/sdb3       1,929,764,862 1,953,523,711    23,758,850   5 Extended
/dev/sdb5       1,929,764,864 1,953,523,711    23,758,848  82 Linux swap / Solaris
/dev/sdb4         625,249,800 1,235,575,214   610,325,415   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        02FEE389FEE37379                       ntfs                                     
/dev/sda2        72B4B092B4B05A75                       ntfs       SYSTEM                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c   ext4                                     
/dev/sdb2        ef08babd-fcbb-49b5-bc40-93781cea3f6a   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        0281F3BD44A3B39D                       ntfs                                     
/dev/sdb5        b8ad57a3-687c-4fac-8959-37c9a4d82dd6   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
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
menuentry 'Ubuntu, with Linux 2.6.34-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    linux    /boot/vmlinuz-2.6.34-5-generic root=UUID=46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c ro   quiet splash
    initrd    /boot/initrd.img-2.6.34-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    echo    'Loading Linux 2.6.34-5-generic ...'
    linux    /boot/vmlinuz-2.6.34-5-generic root=UUID=46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.34-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 02fee389fee37379
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 72b4b092b4b05a75
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
UUID=46bc1b6d-fc48-40d5-a6e4-ef111f11cd3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b8ad57a3-687c-4fac-8959-37c9a4d82dd6 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
 169.8GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.34-5-generic
 141.8GB: boot/vmlinuz-2.6.34-5-generic
 142.0GB: initrd.img
 141.8GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ef08babd-fcbb-49b5-bc40-93781cea3f6a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 02fee389fee37379
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 72b4b092b4b05a75
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ef08babd-fcbb-49b5-bc40-93781cea3f6a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b8ad57a3-687c-4fac-8959-37c9a4d82dd6 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 802.4GB: boot/grub/core.img
 632.9GB: boot/grub/grub.cfg
 802.4GB: boot/initrd.img-2.6.32-21-generic
 802.5GB: boot/initrd.img-2.6.32-24-generic
 802.4GB: boot/vmlinuz-2.6.32-21-generic
 802.5GB: boot/vmlinuz-2.6.32-24-generic
 802.5GB: initrd.img
 802.4GB: initrd.img.old
 802.5GB: vmlinuz
 802.4GB: vmlinuz.old

```

I opened the computer case. Because I have SATAs it is easy to disconnect a hard drive. I disconnected the Ubuntu first. OEM Windows and MS-Restore CD did not work. The Windows rescue utilities do not see any Windows.

Shutdown, disconnect Win SATA, plug in Ubuntu SATA. Reboot and Grub error 'can not find grub_xput'. Shut down, replug with both drives connected, thinking I could use OEM Windows CD maybe to restore MBR. Grub functioned at that point !!!!!!

So, I have an Ubuntu 10.10 installation installed, even though the .iso and the LiveCD installer said 10.04. The desktop however is 10.10. The RESULTS.txt says it is vers. 10.10. The Gnome desktop menu Help->About says 10.04. I have issues with the Radeon Graphics driver in 10.10 and had to use a technique I found online (not the Ubuntu). 

In other words I have a flakey 10.10 installed that is working. I may want to use the installer for 10.04 that I KNOW is vers. 10.04 and I would like to know how to fix GRUB2.

Thanks, I am away for the next 3 hours for an appointment. I would like to finish this thread to help myself and anyone else because most Grub issues are on a single hard drive. My setup is 2 drives and maybe it will help those with USB startups and so forth.

---

### Post by dino99 on 2010-09-15
uuid are not static: if you remove a hdd (unplug) then plug it back, the allowed uuid is a new one, so the grub2 config is not updated, so take care, a workaround is to use label instead of uuid but its not the default ubuntu choice.

you might rebuilt a grub2 config:

sudo grub-mkconfig
sudo update-grub

or into synaptic: remove/purge then reinstall grub-pc

---

### Post by Unterseeboot_234 on 2010-09-15
Thanks, I did reboot. I did 
sudo grub-mkconfig
sudo update-grub

The 10.10 install seems to be stabilizing. The Help=>About says 10.10 now when originally it said 10.04. However, some of the windows in Maverick have garbled buttons and I would have to clean up the menus. Just my luck I had a development branch when I went to the iso downloads for Ubuntu. Besides the little problems in 10.10, 10.04 LTS (Lucid) has a prettier choice for the Gnome GUI colors and the video driver included Radeon's ATI driver control panel.

I may format sdb1 once more and go for the 10.04 install. That hung on the Grub2 install just like this current problem. Give me a day or so and I will post another question, or mark this one solved. The machine I'm trying to dual-boot is the office machine, not the programmer's toy.

Thanks.

---

### Post by oldfred on 2010-09-15
If you reinstall grub2 to the MBR of sdb to boot from sdb2 that should boot your 10.04 install. You then need to run the sudo update-grub to get it to find your windows installs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You can run this from the liveCD or your 10.10 install.

sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

Then in BIOS set sdb as the boot drive.

With 2 drives you need to use the advanced button. Maverick may be different, but I have not installed it lately.
Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by coffeecat on 2010-09-15
> **dino99 said:**
> uuid are not static: if you remove a hdd (unplug) then plug it back, the allowed uuid is a new one,

If you are saying what I think you are saying, then that is simply not correct.

A UUID is applied to a partition, not a drive and it is static. Unless you change it by reformatting the partition or with the use of tune2fs. That is the whole point of using UUIDs in /etc/fstab and grub - so that you can change hard drives around without continually editing configuration files.

---

### Post by Unterseeboot_234 on 2010-09-20
OK, a short history. When Maverick 10.10 first came out I tried downloading it and strange, but it was dial-up modem speed. Not sure what happened. The iso did not have a GUI installer or LiveCD. At a later date I did another download. That said 10.04 Lucid LTS. Installed that, but it was a mislabeled Maverick. There were issues with the Radeon driver. Desktop movement of a window was jerky without the ATI download center driver. The Update for Ubuntu to the new kernel kept blocking the ATI Radeon driver, other updates for Ubuntu would not install. However, the updates did make the About menu change from 10.04 to 10.10. Really strange.

I reformat the partition with a CD I knew had Lucid-64 and install. I tried the Ubuntu restricted drivers and that does not work. Furthermore, I tried apt-get install build-essential and THAT won't install -- conflicts with fglrx. I reformat once more, install build-essential just after the install, then install the ATI Radeon installer, let it install automatic. Reboot and finally, I get accelerated desktop effects options after using Catalyst Center -- the graphics gui --one time to make internal links. (Whew).

Now, Lucid 10.04 offers the best compromise for this Office computer. The people in the office like Ubuntu, and boot into Lucid instead of Windows 7 for just about everything. We still have to have Windows 7 to fax. We bought a cheap external USB fax/modem and that works with Windows 7 fax program. If there was an easy answer for fax on Linux, well... I just might format the Win7 SATA.

Finish up: build ffmpeg with the firewire support to get QuickTime -- make and make install work rapidly on this hexacore AMD-Phenom-II. Installed cenelerra and it renders video almost 1-to-1 in real time.

Changed the interface to German, reboot.

Now I'll do a backup. (and grub works)

---

