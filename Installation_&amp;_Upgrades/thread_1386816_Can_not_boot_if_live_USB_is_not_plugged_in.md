---
title: "Can not boot if live USB is not plugged in"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by terranoid on 2010-01-21
I used a live system on a USB stick to install Karmic on a Acer Aspire One netbook. It had windows 7 preinstalled. All went well, the windows partition was resized, a extended partition and two logical partitions were created and Karmic was installed. I rebooted and grub loaded and displayed a boot menu, from which I could now boot the installed system. (the USB-stick was still plugged in) When I started the netbook the next day I got the boot menu but after selecting to boot Karmic the screen went black with a cursor blinking in the upper left corner and nothing else happened. I found out that the system boots only if the live USB is plugged in. I unmounted and removed the USB-stick, installed all updates that also included a new kernel. When I restarted, the newly installed kernel showed up in the grub menu, but trying to start still gave me the black screen with the blinking cursor. After restarting with the USB-stick plugged in I could boot using the new kernel. Strange, because I removed the USB-stick before installing the updates. I also tried to reinstall grub-pc (after umounting and removing the USB-stick), but it still gives me the same result.

---

### Post by darkod on 2010-01-21
Plug in the usb stick.
Download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. It will have detailed info about your boot process and files. Copy the content of the file here and wrap it in CODE tags (with the text selected hit the # button in the toolbar above) for easier reading.

It will help figure out how the boot process is going.

---

### Post by terranoid on 2010-01-21
Thanks a lot for looking into that.
I was buying that (second) netbook with the intention to install ubuntu on it, because I run into the known update troubles with a wubi install on the first one. Once I know how to get it right, the windoze 7 will have to go.

Here is the output of the script:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x386d89a0

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   267,482,249   242,099,550   7 HPFS/NTFS
/dev/sda4         267,482,250   488,392,064   220,909,815   5 Extended
/dev/sda5         267,482,313   482,431,949   214,949,637  83 Linux
/dev/sda6         482,432,013   488,392,064     5,960,052  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
64 heads, 32 sectors/track, 15283 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    31,299,583    31,299,552   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="EAC8DF2BC8DEF533" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="B010DF7A10DF464E" LABEL="SYSTEM RESERVED" TYPE="ntfs" 
/dev/sda3: UUID="6AF4E0E6F4E0B58B" LABEL="Acer" TYPE="ntfs" 
/dev/sda5: UUID="5f1433df-58e0-44d0-bbf9-f9e8f7ee307f" TYPE="ext4" 
/dev/sda6: UUID="0226c19d-21d6-4bec-956d-ca5af34751ec" TYPE="swap" 
/dev/sdb1: LABEL="CRUZER" UUID="481F-9569" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/terranoid/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=terranoid)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=terranoid)
/dev/sdb1 on /media/CRUZER type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 5f1433df-58e0-44d0-bbf9-f9e8f7ee307f
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f1433df-58e0-44d0-bbf9-f9e8f7ee307f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5f1433df-58e0-44d0-bbf9-f9e8f7ee307f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f1433df-58e0-44d0-bbf9-f9e8f7ee307f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5f1433df-58e0-44d0-bbf9-f9e8f7ee307f ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f1433df-58e0-44d0-bbf9-f9e8f7ee307f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f1433df-58e0-44d0-bbf9-f9e8f7ee307f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f1433df-58e0-44d0-bbf9-f9e8f7ee307f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f1433df-58e0-44d0-bbf9-f9e8f7ee307f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set eac8df2bc8def533
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set b010df7a10df464e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5f1433df-58e0-44d0-bbf9-f9e8f7ee307f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0226c19d-21d6-4bec-956d-ca5af34751ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 136.9GB: boot/grub/core.img
 136.9GB: boot/grub/grub.cfg
 136.9GB: boot/initrd.img-2.6.31-14-generic
 136.9GB: boot/initrd.img-2.6.31-16-generic
 136.9GB: boot/vmlinuz-2.6.31-14-generic
 136.9GB: boot/vmlinuz-2.6.31-16-generic
 136.9GB: initrd.img
 136.9GB: initrd.img.old
 136.9GB: vmlinuz
 136.9GB: vmlinuz.old

```

---

### Post by darkod on 2010-01-21
To be honest, I can't see anything wrong. It should work fine for you without the stick.
One thing to try, and not sure if it will change anything:
Boot with your stick plugged in, because that's the only way you can. Unmount and remove it. In terminal execute:
sudo grub-install --recheck
sudo update-grub

Reboot without the stick and see if anything changed.

---

### Post by terranoid on 2010-01-21
Thanks again. I will try what You suggested. It will take some time because I am about to leave my office. I should be back online (from my favorite pizza's wireless LAN) within 40 minutes or so.

---

### Post by efflandt on 2010-01-21
Does your Cruzer have U3?  When I booted iso on USB Cruzer, it took much longer than other USB flash (much longer than even iso on microSD).  U3 is firmware that shows up as a separate sr device (like cdrom) even if you totally repartition/format flash on the stick.

---

### Post by darkod on 2010-01-21
> **efflandt said:**
> Does your Cruzer have U3?  When I booted iso on USB Cruzer, it took much longer than other USB flash (much longer than even iso on microSD).  U3 is firmware that shows up as a separate sr device (like cdrom) even if you totally repartition/format flash on the stick.

If you are interested in removing it there is U3 uninstall application. After that you get standard non-U3 usb stick. The latest version I have seen even backs up the usb stick content temporarily and restores it back afterwards (although it's better to make your own backup first).

---

