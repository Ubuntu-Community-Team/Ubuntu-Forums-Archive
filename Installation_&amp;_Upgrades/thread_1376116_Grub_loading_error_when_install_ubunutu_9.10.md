---
title: "Grub loading error when install ubunutu 9.10"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by 7o7YlUcb on 2010-01-08
Hi,
I went through the procedure to install Ubuntu 9.10 alongside Windows XP. The installation completed without complaint. But when I reboot the PC I get the error message "Grub loading error: no such partition...". and the keyboard is dead.
I am using a Sony vaio PCG-FR215H laptop on which I have fitted new HDD and  CD-drive.
I carried out the installation by first booting up a live version of Ubuntu on a USB thumb drive and then clicking on the 'install Ubuntu' icon on the Live Ubuntu desktop. (I coudn't use a Live CD to install as this fails for some reason). 
I regained use of Windows XP on the PC by booting with a Windows 95 boot floppy and typing "fdisk /mbr".
So, does anyone know what might have cased this grub error? 
Also, are there ways to try and fix the problem manually. I.e. can I get a copy of good versions of the files that are likely corrupted and then replace the stuff that I will have written over when I did the "fdisk /mbr"?
Thanks.

---

### Post by presence1960 on 2010-01-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by 7o7YlUcb on 2010-01-09
Thanks presence1960. Here is the result. sdb is my usb thumb drive. I should mention that previously I had Ubuntu 9.04 working fine on my laptop. But I have since replaced the HDD and CD-drive. So I'm not sure if the problem is caused by the new hardware or the new Ubuntu version. If you cant find anything wrong here I'll experiment by trying to re-install Ubuntu 9.04.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51145113

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,022,069    43,022,007   7 HPFS/NTFS
/dev/sda2          43,022,070   312,576,704   269,554,635   5 Extended
/dev/sda5          43,022,133   281,201,759   238,179,627   7 HPFS/NTFS
/dev/sda6         281,201,823   311,162,984    29,961,162  83 Linux
/dev/sda7         311,163,048   312,576,704     1,413,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            249     3,967,487     3,967,239   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="A85831A258317064" LABEL="VAIO" TYPE="ntfs" 
sda5: UUID="2000015E0FD3747E" LABEL="VAIO_D" TYPE="ntfs" 
sda6: UUID="9f206ac4-cb30-43de-80e1-8f43881496df" TYPE="ext4" 
sda7: UUID="0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be" TYPE="swap" 
sdb1: LABEL="SDMMC1_2GB" UUID="88AB-56EF" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /isodevice type vfat (rw)
/dev/loop0 on /cdrom type iso9660 (rw)
/dev/loop1 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr0 on /media/plop_bootmanager type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a85831a258317064
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=9f206ac4-cb30-43de-80e1-8f43881496df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 143.9GB: boot/grub/core.img
 143.9GB: boot/grub/grub.cfg
 143.9GB: boot/initrd.img-2.6.31-14-generic
 143.9GB: boot/vmlinuz-2.6.31-14-generic
 143.9GB: initrd.img
 143.9GB: vmlinuz

================================ sdb1/menu.lst: ================================

default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
# Splash Image
splashimage=/splash.xpm.gz
foreground=FFFFFF
background=0066FF

title Boot Parted Magic 4.5
find --set-root /pmagic-4.5.iso
map /pmagic-4.5.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

# Linux Mint 8 Menu Item Submitted by Szymon Silski
title Boot Linux Mint 8
find --set-root /LinuxMint-8.iso
map /LinuxMint-8.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/LinuxMint-8.iso splash
initrd /casper/initrd.lz
boot

title Boot Ubuntu 9.10
find --set-root /ubuntu-9.10-desktop-i386.iso
map /ubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Xubuntu 9.10
find --set-root /xubuntu-9.10-desktop-i386.iso
map /xubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper persistent iso-scan/filename=/xubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Kubuntu 9.10
find --set-root /kubuntu-9.10-desktop-i386.iso
map /kubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper persistent iso-scan/filename=/kubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot DSL 4.4.10
find --set-root /dsl-4.4.10-initrd.iso
map --mem /dsl-4.4.10-initrd.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

title Boot Ultimate Boot CD 4.11
find --set-root /ubcd411.iso
map /ubcd411.iso (hd32)
map --hook
chainloader (hd32)
boot

title Boot OphCrack XP 2.3.1
find --set-root /ophcrack-xp-livecd-2.3.1.iso
map /ophcrack-xp-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot OphCrack Vista 2.3.1
find --set-root /ophcrack-vista-livecd-2.3.1.iso
map /ophcrack-vista-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot SliTaz 2.0
find --set-root /slitaz-2.0.iso
map --mem /slitaz-2.0.iso (hd32)
map --hook
chainloader (hd32)
boot

title Riplinux 9.3
find --set-root /RIPLinuX-9.3.iso
map --heads=0 --sectors-per-track=0 /RIPLinuX-9.3.iso (0xff) || map --heads=0 --sectors-per-track=0 --mem /RIPLinuX-9.3.iso (0xff)
map --hook
chainloader (0xff)
boot

# Suggested by Relst relst.nl@gmail.com
title Boot another OS via Internet
kernel /gpxe.lkrn
boot

# Not working yet
# title Boot Slax 6.1.2
# find --set-root /slax-6.1.2.iso
# map /slax-6.1.2.iso (0xff)
# map --hook
# root (0xff)
# chainloader (0xff)
# boot


title Parted Magic 1.8 ISO Boot
find --set-root /pmagic-1.8.iso
map /pmagic-1.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.1 ISO Boot
find --set-root /pmagic-4.1.iso
map /pmagic-4.1.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.2 ISO Boot
find --set-root /pmagic-4.2.iso
map /pmagic-4.2.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.3 ISO Boot
find --set-root /pmagic-4.3.iso
map /pmagic-4.3.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.8 ISO Boot
find --set-root /pmagic-4.8.iso
map /pmagic-4.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: menu.lst

```

---

### Post by presence1960 on 2010-01-09
You want to put GRUB on MBR of your internal disk. Boot the Live CD/USB and select "try ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal).

Run this command ```
sudo mount /dev/sda6 /mnt
```
This will mount your / partition.

Next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB on MBR of your internal disk. Reboot without the Live CD/USB and choose Ubuntu at the GRUB menu. When Ubuntu loads open a terminal and run ```
sudo update-grub
```

You should now be good to go. reboot and check that you can boot into windows also.

---

### Post by 7o7YlUcb on 2010-01-09
This gives the same error (Grub loading error: no such partition...).

The result of running your commands...
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the  contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$
```I ran the boot-info_script again ......
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,022,069    43,022,007   7 HPFS/NTFS
/dev/sda2          43,022,070   312,576,704   269,554,635   5 Extended
/dev/sda5          43,022,133   281,201,759   238,179,627   7 HPFS/NTFS
/dev/sda6         281,201,823   311,162,984    29,961,162  83 Linux
/dev/sda7         311,163,048   312,576,704     1,413,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            249     3,967,487     3,967,239   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="A85831A258317064" LABEL="VAIO" TYPE="ntfs" 
sda5: UUID="2000015E0FD3747E" LABEL="VAIO_D" TYPE="ntfs" 
sda6: UUID="9f206ac4-cb30-43de-80e1-8f43881496df" TYPE="ext4" 
sda7: UUID="0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be" TYPE="swap" 
sdb1: LABEL="SDMMC1_2GB" UUID="88AB-56EF" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /isodevice type vfat (rw)
/dev/loop0 on /cdrom type iso9660 (rw)
/dev/loop1 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr0 on /media/plop_bootmanager type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a85831a258317064
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=9f206ac4-cb30-43de-80e1-8f43881496df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 143.9GB: boot/grub/core.img
 143.9GB: boot/grub/grub.cfg
 143.9GB: boot/grub/stage2
 143.9GB: boot/initrd.img-2.6.31-14-generic
 143.9GB: boot/vmlinuz-2.6.31-14-generic
 143.9GB: initrd.img
 143.9GB: vmlinuz

================================ sdb1/menu.lst: ================================

default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
# Splash Image
splashimage=/splash.xpm.gz
foreground=FFFFFF
background=0066FF

title Boot Parted Magic 4.5
find --set-root /pmagic-4.5.iso
map /pmagic-4.5.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

# Linux Mint 8 Menu Item Submitted by Szymon Silski
title Boot Linux Mint 8
find --set-root /LinuxMint-8.iso
map /LinuxMint-8.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/LinuxMint-8.iso splash
initrd /casper/initrd.lz
boot

title Boot Ubuntu 9.10
find --set-root /ubuntu-9.10-desktop-i386.iso
map /ubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Xubuntu 9.10
find --set-root /xubuntu-9.10-desktop-i386.iso
map /xubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper persistent iso-scan/filename=/xubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Kubuntu 9.10
find --set-root /kubuntu-9.10-desktop-i386.iso
map /kubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper persistent iso-scan/filename=/kubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot DSL 4.4.10
find --set-root /dsl-4.4.10-initrd.iso
map --mem /dsl-4.4.10-initrd.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

title Boot Ultimate Boot CD 4.11
find --set-root /ubcd411.iso
map /ubcd411.iso (hd32)
map --hook
chainloader (hd32)
boot

title Boot OphCrack XP 2.3.1
find --set-root /ophcrack-xp-livecd-2.3.1.iso
map /ophcrack-xp-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot OphCrack Vista 2.3.1
find --set-root /ophcrack-vista-livecd-2.3.1.iso
map /ophcrack-vista-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot SliTaz 2.0
find --set-root /slitaz-2.0.iso
map --mem /slitaz-2.0.iso (hd32)
map --hook
chainloader (hd32)
boot

title Riplinux 9.3
find --set-root /RIPLinuX-9.3.iso
map --heads=0 --sectors-per-track=0 /RIPLinuX-9.3.iso (0xff) || map --heads=0 --sectors-per-track=0 --mem /RIPLinuX-9.3.iso (0xff)
map --hook
chainloader (0xff)
boot

# Suggested by Relst relst.nl@gmail.com
title Boot another OS via Internet
kernel /gpxe.lkrn
boot

# Not working yet
# title Boot Slax 6.1.2
# find --set-root /slax-6.1.2.iso
# map /slax-6.1.2.iso (0xff)
# map --hook
# root (0xff)
# chainloader (0xff)
# boot


title Parted Magic 1.8 ISO Boot
find --set-root /pmagic-1.8.iso
map /pmagic-1.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.1 ISO Boot
find --set-root /pmagic-4.1.iso
map /pmagic-4.1.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.2 ISO Boot
find --set-root /pmagic-4.2.iso
map /pmagic-4.2.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.3 ISO Boot
find --set-root /pmagic-4.3.iso
map /pmagic-4.3.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.8 ISO Boot
find --set-root /pmagic-4.8.iso
map /pmagic-4.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
```
A diff between the two RESULTS.txt files ....

```
ubuntu@ubuntu:~$ diff Desktop/RESULTS.txt Downloads/RESULTS.txt
3,4c3
<  => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
<     in partition #6 for /boot/grub.
---
>  => Windows is installed in the MBR of /dev/sda
57c56
< Disk identifier: 0x00000000
---
> Disk identifier: 0x51145113
234d232
<  143.9GB: boot/grub/stage2
ubuntu@ubuntu:~$ 
```I was wondering if, as well as installing grub to the MBR, I also need to re-install it to the the sda6 partition?

Cheers.

---

### Post by presence1960 on 2010-01-09
> **RevRhubar said:**
> This gives the same error (Grub loading error: no such partition...).

The result of running your commands...
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the  contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$
```I ran the boot-info_script again ......
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,022,069    43,022,007   7 HPFS/NTFS
/dev/sda2          43,022,070   312,576,704   269,554,635   5 Extended
/dev/sda5          43,022,133   281,201,759   238,179,627   7 HPFS/NTFS
/dev/sda6         281,201,823   311,162,984    29,961,162  83 Linux
/dev/sda7         311,163,048   312,576,704     1,413,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            249     3,967,487     3,967,239   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="A85831A258317064" LABEL="VAIO" TYPE="ntfs" 
sda5: UUID="2000015E0FD3747E" LABEL="VAIO_D" TYPE="ntfs" 
sda6: UUID="9f206ac4-cb30-43de-80e1-8f43881496df" TYPE="ext4" 
sda7: UUID="0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be" TYPE="swap" 
sdb1: LABEL="SDMMC1_2GB" UUID="88AB-56EF" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /isodevice type vfat (rw)
/dev/loop0 on /cdrom type iso9660 (rw)
/dev/loop1 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr0 on /media/plop_bootmanager type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 9f206ac4-cb30-43de-80e1-8f43881496df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9f206ac4-cb30-43de-80e1-8f43881496df ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a85831a258317064
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=9f206ac4-cb30-43de-80e1-8f43881496df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0cc20c2d-13fb-4363-ab2f-1e8a3a96b8be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 143.9GB: boot/grub/core.img
 143.9GB: boot/grub/grub.cfg
 143.9GB: boot/grub/stage2
 143.9GB: boot/initrd.img-2.6.31-14-generic
 143.9GB: boot/vmlinuz-2.6.31-14-generic
 143.9GB: initrd.img
 143.9GB: vmlinuz

================================ sdb1/menu.lst: ================================

default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
# Splash Image
splashimage=/splash.xpm.gz
foreground=FFFFFF
background=0066FF

title Boot Parted Magic 4.5
find --set-root /pmagic-4.5.iso
map /pmagic-4.5.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

# Linux Mint 8 Menu Item Submitted by Szymon Silski
title Boot Linux Mint 8
find --set-root /LinuxMint-8.iso
map /LinuxMint-8.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/LinuxMint-8.iso splash
initrd /casper/initrd.lz
boot

title Boot Ubuntu 9.10
find --set-root /ubuntu-9.10-desktop-i386.iso
map /ubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Xubuntu 9.10
find --set-root /xubuntu-9.10-desktop-i386.iso
map /xubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper persistent iso-scan/filename=/xubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot Kubuntu 9.10
find --set-root /kubuntu-9.10-desktop-i386.iso
map /kubuntu-9.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper persistent iso-scan/filename=/kubuntu-9.10-desktop-i386.iso splash
initrd /casper/initrd.lz
boot

title Boot DSL 4.4.10
find --set-root /dsl-4.4.10-initrd.iso
map --mem /dsl-4.4.10-initrd.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
boot

title Boot Ultimate Boot CD 4.11
find --set-root /ubcd411.iso
map /ubcd411.iso (hd32)
map --hook
chainloader (hd32)
boot

title Boot OphCrack XP 2.3.1
find --set-root /ophcrack-xp-livecd-2.3.1.iso
map /ophcrack-xp-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot OphCrack Vista 2.3.1
find --set-root /ophcrack-vista-livecd-2.3.1.iso
map /ophcrack-vista-livecd-2.3.1.iso (0xff)
map --hook
root (0xff)
kernel /boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin
initrd /boot/rootfs.gz
boot

title Boot SliTaz 2.0
find --set-root /slitaz-2.0.iso
map --mem /slitaz-2.0.iso (hd32)
map --hook
chainloader (hd32)
boot

title Riplinux 9.3
find --set-root /RIPLinuX-9.3.iso
map --heads=0 --sectors-per-track=0 /RIPLinuX-9.3.iso (0xff) || map --heads=0 --sectors-per-track=0 --mem /RIPLinuX-9.3.iso (0xff)
map --hook
chainloader (0xff)
boot

# Suggested by Relst relst.nl@gmail.com
title Boot another OS via Internet
kernel /gpxe.lkrn
boot

# Not working yet
# title Boot Slax 6.1.2
# find --set-root /slax-6.1.2.iso
# map /slax-6.1.2.iso (0xff)
# map --hook
# root (0xff)
# chainloader (0xff)
# boot


title Parted Magic 1.8 ISO Boot
find --set-root /pmagic-1.8.iso
map /pmagic-1.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.1 ISO Boot
find --set-root /pmagic-4.1.iso
map /pmagic-4.1.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.2 ISO Boot
find --set-root /pmagic-4.2.iso
map /pmagic-4.2.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.3 ISO Boot
find --set-root /pmagic-4.3.iso
map /pmagic-4.3.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Parted Magic 4.8 ISO Boot
find --set-root /pmagic-4.8.iso
map /pmagic-4.8.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
```
A diff between the two RESULTS.txt files ....

```
ubuntu@ubuntu:~$ diff Desktop/RESULTS.txt Downloads/RESULTS.txt
3,4c3
<  => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
<     in partition #6 for /boot/grub.
---
>  => Windows is installed in the MBR of /dev/sda
57c56
< Disk identifier: 0x00000000
---
> Disk identifier: 0x51145113
234d232
<  143.9GB: boot/grub/stage2
ubuntu@ubuntu:~$ 
```I was wondering if, as well as installing grub to the MBR, I also need to re-install it to the the sda6 partition?

Cheers.

Boot without the USB inserted and see what happens. Installing GRUB to sda6 will not help. GRUB is on sda MBR and looks to /boot/grub for grub.cfg

---

### Post by 7o7YlUcb on 2010-01-10
I removed all USB devices and rebooted. Same error message.

---

### Post by presence1960 on 2010-01-10
> **RevRhubar said:**
> I removed all USB devices and rebooted. Same error message.

Your disk identifier in fdisk from the two script outputs is different. I don't know why that is. I am going to PM someone I know who may understand this.

---

### Post by kansasnoob on 2010-01-10
I'd like you to try a slightly different method of reinstalling grub to the mbr. I know sometimes the aforementioned procedure just doesn't work for me.

I know these commands look incredibly long, just double click to highlight, then right click and copy-n-paste please:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then if Ubuntu boots be sure to run:

```
sudo update-grub
```

And wait until it says "done".

---

### Post by meierfra. on 2010-01-10
Edit: kansasnoob posted while I was working on my response. Go ahead a try his "chroot" approach. It won't hurt.


> < Disk identifier: 0x00000000
---
> Disk identifier: 0x51145113


I never have seen a case where Grub erases the disk identifier. But I know that "fdisk /mbr" erases it.  Did you run "fdisk /mbr"  in between to the two RESULTS.txt?

Ubuntu does not care about the disk  identifier.
But Windows XP does not like the disk  identifier to be changed. On the otherhand, if it is set the "00000000" XP  usually just generates a new one. Also, you already used "fdisk /mbr"  earlier and were able to boot into XP.
So I don't think you need to worry about the disk identifier


> I have fitted a new HDD 
> I should mention that previously I had Ubuntu 9.04 working fine 
> dev/sda6         281,201,823   311,162,984    29,961,162  83 Linux

> "Grub loading error: no such partition...". 


Some bios are  only able to see the first 137GB of a hard drive. Your Ubuntu partition  starts at roughly 140 GB.  That might cause your Ubuntu partition to be invisible to Grub2.

You might have a look in your Bios. Does it report your  hard drive to have size 137 GB?  You might also have some setting in the bios you can change (look for LBA mode, or anything which looks promising) 
But if you change something, make sure to write down the original settings.

I read somewhere that installing grub2 via

```
sudo mount  /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt [COLOR="Red"]--disk-module=ata[/COLOR] /dev/sda
```
might solve the problem. But I never seen anybody try it. So I'm not sure it makes a difference.

If none of this works, I would suggest to create a small boot partition at the beginning of the drive. But we'll worry about that later.



.

---

### Post by 7o7YlUcb on 2010-01-12
Hi,

I did do a fdisk /mbr (to regain access to windows xp) between ubuntu installs.

Right enough BIOS reports that it can only see 137GB. So I repartitioned and made a blank area on the HDD between 20GB and 40GB and reinstalled ubuntu. This time I did get a grub menu but with two different memtest options and windows XP - but no option to boot linux. When I move the cursor key to try to select' windows XP boot', the keyboard freezes up. Why on earth would ubuntu not give itself a boot option? I doesnt complain at all when I install it?
Though the extended partition that ubuntu installed itself within extends beyond 137GB does this matter?

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7e8b7e8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,022,069    43,022,007   7 HPFS/NTFS
/dev/sda2          43,022,070   312,576,704   269,554,635   5 Extended
/dev/sda5          83,971,818   312,576,704   228,604,887   7 HPFS/NTFS
/dev/sda6          43,022,196    82,172,474    39,150,279  83 Linux
/dev/sda7          82,172,538    83,971,754     1,799,217  82 Linux swap / Solaris
```

kansasnoob, I ran your suggestions - no change when try to boot PC.

meierfra, I ran your suggestions - on boot grub crashes at 'Loading grub'


on my hdd: /media/3c67d9b7-5a5e-4733-a3a6-a19d527741bd/boot/grub/grub.cfg
```

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 3c67d9b7-5a5e-4733-a3a6-a19d527741bd
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a85831a258317064
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Are there any good files I can inspect to see if Ubuntu is reporting any installation errors?
I found this file - apart for a few 'error0's it doesnt report any errors 
/media/3c67d9b7-5a5e-4733-a3a6-a19d527741bd/var/log/dpkg.log
```
2009-10-28 20:55:15 startup archives install
2009-10-28 20:55:15 install base-files <none> 5.0.0ubuntu7
2009-10-28 20:55:15 status half-installed base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 install base-passwd <none> 3.5.21
2009-10-28 20:55:17 status half-installed base-passwd 3.5.21
2009-10-28 20:55:17 status unpacked base-passwd 3.5.21
2009-10-28 20:55:17 status unpacked base-passwd 3.5.21
2009-10-28 20:55:17 configure base-passwd 3.5.21 3.5.21
2009-10-28 20:55:17 status unpacked base-passwd 3.5.21
2009-10-28 20:55:17 status half-configured base-passwd 3.5.21
2009-10-28 20:55:17 status installed base-passwd 3.5.21
2009-10-28 20:55:17 configure base-files 5.0.0ubuntu7 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status half-configured base-files 5.0.0ubuntu7
2009-10-28 20:55:17 status installed base-files 5.0.0ubuntu7
2009-10-28 20:55:17 startup archives install
2009-10-28 20:55:17 upgrade dpkg 1.15.4ubuntu2 1.15.4ubuntu2
2009-10-28 20:55:17 status half-configured dpkg 1.15.4ubuntu2
2009-10-28 20:55:17 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:17 status half-installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:17 status half-installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 configure dpkg 1.15.4ubuntu2 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status half-configured dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 status installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:18 startup archives install
2009-10-28 20:55:18 install libc6 <none> 2.10.1-0ubuntu15
2009-10-28 20:55:18 status half-installed libc6 2.10.1-0ubuntu15
2009-10-28 20:55:19 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 configure libc6 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:20 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 status half-configured libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 status installed libc6 2.10.1-0ubuntu15
2009-10-28 20:55:20 startup archives install
2009-10-28 20:55:20 install perl-base <none> 5.10.0-24ubuntu4
2009-10-28 20:55:20 status half-installed perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 configure perl-base 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 20:55:20 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 status half-configured perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 status installed perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:20 startup archives install
2009-10-28 20:55:20 install mawk <none> 1.3.3-15ubuntu1
2009-10-28 20:55:20 status half-installed mawk 1.3.3-15ubuntu1
2009-10-28 20:55:20 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:20 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:20 configure mawk 1.3.3-15ubuntu1 1.3.3-15ubuntu1
2009-10-28 20:55:20 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:20 status half-configured mawk 1.3.3-15ubuntu1
2009-10-28 20:55:21 update-alternatives: run with --quiet --install /usr/bin/awk awk /usr/bin/mawk 5 --slave /usr/share/man/man1/awk.1.gz awk.1.gz /usr/share/man/man1/mawk.1.gz --slave /usr/bin/nawk nawk /usr/bin/mawk --slave /usr/share/man/man1/nawk.1.gz nawk.1.gz /usr/share/man/man1/mawk.1.gz
2009-10-28 20:55:21 update-alternatives: link group awk updated to point to /usr/bin/mawk
2009-10-28 20:55:21 status installed mawk 1.3.3-15ubuntu1
2009-10-28 20:55:21 startup archives install
2009-10-28 20:55:21 install debconf <none> 1.5.27ubuntu2
2009-10-28 20:55:21 status half-installed debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 configure debconf 1.5.27ubuntu2 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status half-configured debconf 1.5.27ubuntu2
2009-10-28 20:55:21 status installed debconf 1.5.27ubuntu2
2009-10-28 20:55:21 startup archives unpack
2009-10-28 20:55:21 upgrade base-files 5.0.0ubuntu7 5.0.0ubuntu7
2009-10-28 20:55:21 status half-configured base-files 5.0.0ubuntu7
2009-10-28 20:55:21 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:21 status half-installed base-files 5.0.0ubuntu7
2009-10-28 20:55:21 status half-installed base-files 5.0.0ubuntu7
2009-10-28 20:55:21 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:21 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:21 upgrade base-passwd 3.5.21 3.5.21
2009-10-28 20:55:21 status half-configured base-passwd 3.5.21
2009-10-28 20:55:21 status unpacked base-passwd 3.5.21
2009-10-28 20:55:21 status half-installed base-passwd 3.5.21
2009-10-28 20:55:21 status half-installed base-passwd 3.5.21
2009-10-28 20:55:21 status unpacked base-passwd 3.5.21
2009-10-28 20:55:21 status unpacked base-passwd 3.5.21
2009-10-28 20:55:21 install bash <none> 4.0-5ubuntu2
2009-10-28 20:55:21 status half-installed bash 4.0-5ubuntu2
2009-10-28 20:55:21 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:21 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:21 install bsdutils <none> 1:2.16-1ubuntu5
2009-10-28 20:55:21 status half-installed bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:21 status unpacked bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:21 status unpacked bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:21 install coreutils <none> 7.4-2ubuntu1
2009-10-28 20:55:21 status half-installed coreutils 7.4-2ubuntu1
2009-10-28 20:55:22 status unpacked coreutils 7.4-2ubuntu1
2009-10-28 20:55:22 status unpacked coreutils 7.4-2ubuntu1
2009-10-28 20:55:22 install dash <none> 0.5.5.1-2ubuntu3
2009-10-28 20:55:22 status half-installed dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:22 status unpacked dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:22 status unpacked dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:22 upgrade debconf 1.5.27ubuntu2 1.5.27ubuntu2
2009-10-28 20:55:22 status half-configured debconf 1.5.27ubuntu2
2009-10-28 20:55:22 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:22 status half-installed debconf 1.5.27ubuntu2
2009-10-28 20:55:22 status half-installed debconf 1.5.27ubuntu2
2009-10-28 20:55:22 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:22 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:22 install debconf-i18n <none> 1.5.27ubuntu2
2009-10-28 20:55:22 status half-installed debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:22 status unpacked debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:22 status unpacked debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:22 install debianutils <none> 2.30ubuntu3
2009-10-28 20:55:22 status half-installed debianutils 2.30ubuntu3
2009-10-28 20:55:22 status unpacked debianutils 2.30ubuntu3
2009-10-28 20:55:22 status unpacked debianutils 2.30ubuntu3
2009-10-28 20:55:22 install diff <none> 2.8.1-13
2009-10-28 20:55:22 status half-installed diff 2.8.1-13
2009-10-28 20:55:22 status unpacked diff 2.8.1-13
2009-10-28 20:55:22 status unpacked diff 2.8.1-13
2009-10-28 20:55:22 upgrade dpkg 1.15.4ubuntu2 1.15.4ubuntu2
2009-10-28 20:55:22 status half-configured dpkg 1.15.4ubuntu2
2009-10-28 20:55:22 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:22 status half-installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:22 status half-installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:23 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:23 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:23 install e2fslibs <none> 1.41.9-1ubuntu3
2009-10-28 20:55:23 status half-installed e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:23 status unpacked e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:23 status unpacked e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:23 install e2fsprogs <none> 1.41.9-1ubuntu3
2009-10-28 20:55:23 status half-installed e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:23 status unpacked e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:23 status unpacked e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:23 install findutils <none> 4.4.2-1
2009-10-28 20:55:23 status half-installed findutils 4.4.2-1
2009-10-28 20:55:23 status unpacked findutils 4.4.2-1
2009-10-28 20:55:23 status unpacked findutils 4.4.2-1
2009-10-28 20:55:23 install gcc-4.4-base <none> 4.4.1-4ubuntu8
2009-10-28 20:55:23 status half-installed gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:23 status unpacked gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:23 status unpacked gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:23 install grep <none> 2.5.4-4
2009-10-28 20:55:23 status half-installed grep 2.5.4-4
2009-10-28 20:55:23 status unpacked grep 2.5.4-4
2009-10-28 20:55:23 status unpacked grep 2.5.4-4
2009-10-28 20:55:23 install gzip <none> 1.3.12-8ubuntu1
2009-10-28 20:55:23 status half-installed gzip 1.3.12-8ubuntu1
2009-10-28 20:55:23 status unpacked gzip 1.3.12-8ubuntu1
2009-10-28 20:55:23 status unpacked gzip 1.3.12-8ubuntu1
2009-10-28 20:55:23 install hostname <none> 2.95ubuntu1
2009-10-28 20:55:23 status half-installed hostname 2.95ubuntu1
2009-10-28 20:55:23 status unpacked hostname 2.95ubuntu1
2009-10-28 20:55:23 status unpacked hostname 2.95ubuntu1
2009-10-28 20:55:23 install initscripts <none> 2.87dsf-4ubuntu11
2009-10-28 20:55:23 status half-installed initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:23 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:23 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:23 install insserv <none> 1.12.0-11
2009-10-28 20:55:23 status half-installed insserv 1.12.0-11
2009-10-28 20:55:23 status unpacked insserv 1.12.0-11
2009-10-28 20:55:23 status unpacked insserv 1.12.0-11
2009-10-28 20:55:23 install libacl1 <none> 2.2.47-2
2009-10-28 20:55:23 status half-installed libacl1 2.2.47-2
2009-10-28 20:55:23 status unpacked libacl1 2.2.47-2
2009-10-28 20:55:23 status unpacked libacl1 2.2.47-2
2009-10-28 20:55:24 install libattr1 <none> 1:2.4.43-3
2009-10-28 20:55:24 status half-installed libattr1 1:2.4.43-3
2009-10-28 20:55:24 status unpacked libattr1 1:2.4.43-3
2009-10-28 20:55:24 status unpacked libattr1 1:2.4.43-3
2009-10-28 20:55:24 install libblkid1 <none> 2.16-1ubuntu5
2009-10-28 20:55:24 status half-installed libblkid1 2.16-1ubuntu5
2009-10-28 20:55:24 status unpacked libblkid1 2.16-1ubuntu5
2009-10-28 20:55:24 status unpacked libblkid1 2.16-1ubuntu5
2009-10-28 20:55:24 install libc-bin <none> 2.10.1-0ubuntu15
2009-10-28 20:55:24 status half-installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:24 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:24 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:24 upgrade libc6 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:24 status half-configured libc6 2.10.1-0ubuntu15
2009-10-28 20:55:24 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:24 status half-installed libc6 2.10.1-0ubuntu15
2009-10-28 20:55:24 status half-installed libc6 2.10.1-0ubuntu15
2009-10-28 20:55:25 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:25 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:25 install libcomerr2 <none> 1.41.9-1ubuntu3
2009-10-28 20:55:25 status half-installed libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:25 status unpacked libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:25 status unpacked libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:25 install libdb4.7 <none> 4.7.25-7ubuntu2
2009-10-28 20:55:25 status half-installed libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:25 status unpacked libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:25 status unpacked libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:25 install libdbus-1-3 <none> 1.2.16-0ubuntu9
2009-10-28 20:55:25 status half-installed libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:25 status unpacked libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:25 status unpacked libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:25 install libgcc1 <none> 1:4.4.1-4ubuntu8
2009-10-28 20:55:25 status half-installed libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:25 status unpacked libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:25 status unpacked libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:25 install liblocale-gettext-perl <none> 1.05-4build1
2009-10-28 20:55:25 status half-installed liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:25 status unpacked liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:25 status unpacked liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:25 install libncurses5 <none> 5.7+20090803-2ubuntu2
2009-10-28 20:55:25 status half-installed libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:25 status unpacked libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:25 status unpacked libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:25 install libpam-modules <none> 1.1.0-2ubuntu1
2009-10-28 20:55:25 status half-installed libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:25 install libpam-runtime <none> 1.1.0-2ubuntu1
2009-10-28 20:55:25 status half-installed libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:25 install libpam0g <none> 1.1.0-2ubuntu1
2009-10-28 20:55:25 status half-installed libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:25 status unpacked libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:25 install libselinux1 <none> 2.0.85-2ubuntu2
2009-10-28 20:55:25 status half-installed libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:25 status unpacked libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:25 status unpacked libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:25 install libsepol1 <none> 2.0.37-1
2009-10-28 20:55:25 status half-installed libsepol1 2.0.37-1
2009-10-28 20:55:26 status unpacked libsepol1 2.0.37-1
2009-10-28 20:55:26 status unpacked libsepol1 2.0.37-1
2009-10-28 20:55:26 install libslang2 <none> 2.1.4-3
2009-10-28 20:55:26 status half-installed libslang2 2.1.4-3
2009-10-28 20:55:26 status unpacked libslang2 2.1.4-3
2009-10-28 20:55:26 status unpacked libslang2 2.1.4-3
2009-10-28 20:55:26 install libss2 <none> 1.41.9-1ubuntu3
2009-10-28 20:55:26 status half-installed libss2 1.41.9-1ubuntu3
2009-10-28 20:55:26 status unpacked libss2 1.41.9-1ubuntu3
2009-10-28 20:55:26 status unpacked libss2 1.41.9-1ubuntu3
2009-10-28 20:55:26 install libssl0.9.8 <none> 0.9.8g-16ubuntu3
2009-10-28 20:55:26 status half-installed libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:26 status unpacked libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:26 status unpacked libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:26 install libstdc++6 <none> 4.4.1-4ubuntu8
2009-10-28 20:55:26 status half-installed libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:26 status unpacked libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:26 status unpacked libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:26 install libtext-charwidth-perl <none> 0.04-5build1
2009-10-28 20:55:26 status half-installed libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:26 status unpacked libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:26 status unpacked libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:26 install libtext-iconv-perl <none> 1.7-1build1
2009-10-28 20:55:26 status half-installed libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:26 status unpacked libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:26 status unpacked libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:26 install libtext-wrapi18n-perl <none> 0.06-7
2009-10-28 20:55:26 status half-installed libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:26 status unpacked libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:26 status unpacked libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:26 install libudev0 <none> 147~-6
2009-10-28 20:55:26 status half-installed libudev0 147~-6
2009-10-28 20:55:26 status unpacked libudev0 147~-6
2009-10-28 20:55:26 status unpacked libudev0 147~-6
2009-10-28 20:55:26 install libuuid1 <none> 2.16-1ubuntu5
2009-10-28 20:55:26 status half-installed libuuid1 2.16-1ubuntu5
2009-10-28 20:55:26 status unpacked libuuid1 2.16-1ubuntu5
2009-10-28 20:55:26 status unpacked libuuid1 2.16-1ubuntu5
2009-10-28 20:55:26 install locales <none> 2.9+git20090617-3
2009-10-28 20:55:26 status half-installed locales 2.9+git20090617-3
2009-10-28 20:55:28 status unpacked locales 2.9+git20090617-3
2009-10-28 20:55:28 status unpacked locales 2.9+git20090617-3
2009-10-28 20:55:28 install login <none> 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:28 status half-installed login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:28 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:28 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:28 install lsb-base <none> 4.0-0ubuntu5
2009-10-28 20:55:28 status half-installed lsb-base 4.0-0ubuntu5
2009-10-28 20:55:28 status unpacked lsb-base 4.0-0ubuntu5
2009-10-28 20:55:28 status unpacked lsb-base 4.0-0ubuntu5
2009-10-28 20:55:28 install lzma <none> 4.43-14ubuntu1
2009-10-28 20:55:28 status half-installed lzma 4.43-14ubuntu1
2009-10-28 20:55:28 status unpacked lzma 4.43-14ubuntu1
2009-10-28 20:55:28 status unpacked lzma 4.43-14ubuntu1
2009-10-28 20:55:28 install makedev <none> 2.3.1-88
2009-10-28 20:55:28 status half-installed makedev 2.3.1-88
2009-10-28 20:55:28 status unpacked makedev 2.3.1-88
2009-10-28 20:55:28 status unpacked makedev 2.3.1-88
2009-10-28 20:55:28 upgrade mawk 1.3.3-15ubuntu1 1.3.3-15ubuntu1
2009-10-28 20:55:28 status half-configured mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 status half-installed mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 status half-installed mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:28 install mount <none> 2.16-1ubuntu5
2009-10-28 20:55:28 status half-installed mount 2.16-1ubuntu5
2009-10-28 20:55:28 status unpacked mount 2.16-1ubuntu5
2009-10-28 20:55:28 status unpacked mount 2.16-1ubuntu5
2009-10-28 20:55:28 install mountall <none> 1.0
2009-10-28 20:55:28 status half-installed mountall 1.0
2009-10-28 20:55:28 status unpacked mountall 1.0
2009-10-28 20:55:28 status unpacked mountall 1.0
2009-10-28 20:55:28 install ncurses-base <none> 5.7+20090803-2ubuntu2
2009-10-28 20:55:28 status half-installed ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 status unpacked ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 status unpacked ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 install ncurses-bin <none> 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 status half-installed ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 status unpacked ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 status unpacked ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:29 install passwd <none> 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:29 status half-installed passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:29 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:29 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:29 upgrade perl-base 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 20:55:29 status half-configured perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 status half-installed perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 status half-installed perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:29 install procps <none> 1:3.2.8-1ubuntu3
2009-10-28 20:55:29 status half-installed procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:29 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:29 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:29 install python-minimal <none> 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:29 status half-installed python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:29 status unpacked python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:29 status unpacked python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:29 install python2.6-minimal <none> 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:29 status half-installed python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:30 status unpacked python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:30 status unpacked python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:30 install sed <none> 4.2.1-1
2009-10-28 20:55:30 status half-installed sed 4.2.1-1
2009-10-28 20:55:30 status unpacked sed 4.2.1-1
2009-10-28 20:55:30 status unpacked sed 4.2.1-1
2009-10-28 20:55:30 install sysv-rc <none> 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status half-installed sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status unpacked sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status unpacked sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:30 install sysvinit-utils <none> 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status half-installed sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status unpacked sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:30 status unpacked sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:30 install tar <none> 1.22-1
2009-10-28 20:55:30 status half-installed tar 1.22-1
2009-10-28 20:55:30 status unpacked tar 1.22-1
2009-10-28 20:55:30 status unpacked tar 1.22-1
2009-10-28 20:55:30 install tzdata <none> 2009o-1ubuntu2
2009-10-28 20:55:30 status half-installed tzdata 2009o-1ubuntu2
2009-10-28 20:55:31 status unpacked tzdata 2009o-1ubuntu2
2009-10-28 20:55:31 status unpacked tzdata 2009o-1ubuntu2
2009-10-28 20:55:31 install upstart <none> 0.6.3-10
2009-10-28 20:55:31 status half-installed upstart 0.6.3-10
2009-10-28 20:55:31 status unpacked upstart 0.6.3-10
2009-10-28 20:55:31 status unpacked upstart 0.6.3-10
2009-10-28 20:55:31 install util-linux <none> 2.16-1ubuntu5
2009-10-28 20:55:31 status half-installed util-linux 2.16-1ubuntu5
2009-10-28 20:55:31 status unpacked util-linux 2.16-1ubuntu5
2009-10-28 20:55:31 status unpacked util-linux 2.16-1ubuntu5
2009-10-28 20:55:31 install zlib1g <none> 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:31 status half-installed zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:31 status unpacked zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:31 status unpacked zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:31 startup packages configure
2009-10-28 20:55:31 configure libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:31 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 status unpacked libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:31 configure gcc-4.4-base 4.4.1-4ubuntu8 4.4.1-4ubuntu8
2009-10-28 20:55:31 status unpacked gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:31 status half-configured gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:31 status installed gcc-4.4-base 4.4.1-4ubuntu8
2009-10-28 20:55:31 configure perl-base 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 20:55:31 status unpacked perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:31 status half-configured perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:31 status installed perl-base 5.10.0-24ubuntu4
2009-10-28 20:55:31 configure libtext-iconv-perl 1.7-1build1 1.7-1build1
2009-10-28 20:55:31 status unpacked libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:31 status half-configured libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:31 status installed libtext-iconv-perl 1.7-1build1
2009-10-28 20:55:31 configure liblocale-gettext-perl 1.05-4build1 1.05-4build1
2009-10-28 20:55:31 status unpacked liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:31 status half-configured liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:31 status installed liblocale-gettext-perl 1.05-4build1
2009-10-28 20:55:31 configure libtext-charwidth-perl 0.04-5build1 0.04-5build1
2009-10-28 20:55:31 status unpacked libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:31 status half-configured libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:31 status installed libtext-charwidth-perl 0.04-5build1
2009-10-28 20:55:31 configure libtext-wrapi18n-perl 0.06-7 0.06-7
2009-10-28 20:55:31 status unpacked libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:31 status half-configured libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:31 status installed libtext-wrapi18n-perl 0.06-7
2009-10-28 20:55:31 configure debconf-i18n 1.5.27ubuntu2 1.5.27ubuntu2
2009-10-28 20:55:31 status unpacked debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:31 status half-configured debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:31 status installed debconf-i18n 1.5.27ubuntu2
2009-10-28 20:55:31 configure debconf 1.5.27ubuntu2 1.5.27ubuntu2
2009-10-28 20:55:31 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:31 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:31 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:31 status unpacked debconf 1.5.27ubuntu2
2009-10-28 20:55:31 status half-configured debconf 1.5.27ubuntu2
2009-10-28 20:55:32 status installed debconf 1.5.27ubuntu2
2009-10-28 20:55:32 configure tzdata 2009o-1ubuntu2 2009o-1ubuntu2
2009-10-28 20:55:32 status unpacked tzdata 2009o-1ubuntu2
2009-10-28 20:55:32 status half-configured tzdata 2009o-1ubuntu2
2009-10-28 20:55:32 status installed tzdata 2009o-1ubuntu2
2009-10-28 20:55:32 configure libc6 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:32 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:32 status unpacked libc6 2.10.1-0ubuntu15
2009-10-28 20:55:32 status half-configured libc6 2.10.1-0ubuntu15
2009-10-28 20:55:32 status installed libc6 2.10.1-0ubuntu15
2009-10-28 20:55:32 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:32 configure debianutils 2.30ubuntu3 2.30ubuntu3
2009-10-28 20:55:32 status unpacked debianutils 2.30ubuntu3
2009-10-28 20:55:32 status half-configured debianutils 2.30ubuntu3
2009-10-28 20:55:32 status installed debianutils 2.30ubuntu3
2009-10-28 20:55:32 configure libdbus-1-3 1.2.16-0ubuntu9 1.2.16-0ubuntu9
2009-10-28 20:55:32 status unpacked libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:32 status half-configured libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:32 status installed libdbus-1-3 1.2.16-0ubuntu9
2009-10-28 20:55:32 configure libpam0g 1.1.0-2ubuntu1 1.1.0-2ubuntu1
2009-10-28 20:55:32 status unpacked libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:32 status half-configured libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:33 status installed libpam0g 1.1.0-2ubuntu1
2009-10-28 20:55:33 configure bsdutils 1:2.16-1ubuntu5 1:2.16-1ubuntu5
2009-10-28 20:55:33 status unpacked bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:33 status half-configured bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:33 status installed bsdutils 1:2.16-1ubuntu5
2009-10-28 20:55:33 configure libsepol1 2.0.37-1 2.0.37-1
2009-10-28 20:55:33 status unpacked libsepol1 2.0.37-1
2009-10-28 20:55:33 status half-configured libsepol1 2.0.37-1
2009-10-28 20:55:34 status installed libsepol1 2.0.37-1
2009-10-28 20:55:34 configure libudev0 147~-6 147~-6
2009-10-28 20:55:34 status unpacked libudev0 147~-6
2009-10-28 20:55:34 status half-configured libudev0 147~-6
2009-10-28 20:55:34 status installed libudev0 147~-6
2009-10-28 20:55:34 configure mountall 1.0 1.0
2009-10-28 20:55:34 status unpacked mountall 1.0
2009-10-28 20:55:34 status unpacked mountall 1.0
2009-10-28 20:55:34 status unpacked mountall 1.0
2009-10-28 20:55:34 status unpacked mountall 1.0
2009-10-28 20:55:34 status unpacked mountall 1.0
2009-10-28 20:55:34 status half-configured mountall 1.0
2009-10-28 20:55:34 status installed mountall 1.0
2009-10-28 20:55:34 configure tar 1.22-1 1.22-1
2009-10-28 20:55:34 status unpacked tar 1.22-1
2009-10-28 20:55:34 status unpacked tar 1.22-1
2009-10-28 20:55:34 status half-configured tar 1.22-1
2009-10-28 20:55:34 update-alternatives: run with --install /usr/sbin/rmt rmt /usr/sbin/rmt-tar 50 --slave /usr/share/man/man8/rmt.8.gz rmt.8.gz /usr/share/man/man8/rmt-tar.8.gz
2009-10-28 20:55:34 update-alternatives: link group rmt updated to point to /usr/sbin/rmt-tar
2009-10-28 20:55:34 status installed tar 1.22-1
2009-10-28 20:55:34 configure zlib1g 1:1.2.3.3.dfsg-13ubuntu3 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:34 status unpacked zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:34 status half-configured zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:34 status installed zlib1g 1:1.2.3.3.dfsg-13ubuntu3
2009-10-28 20:55:34 configure locales 2.9+git20090617-3 2.9+git20090617-3
2009-10-28 20:55:34 status unpacked locales 2.9+git20090617-3
2009-10-28 20:55:34 status unpacked locales 2.9+git20090617-3
2009-10-28 20:55:34 status half-configured locales 2.9+git20090617-3
2009-10-28 20:55:34 status installed locales 2.9+git20090617-3
2009-10-28 20:55:34 configure libgcc1 1:4.4.1-4ubuntu8 1:4.4.1-4ubuntu8
2009-10-28 20:55:34 status unpacked libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:34 status half-configured libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:34 status installed libgcc1 1:4.4.1-4ubuntu8
2009-10-28 20:55:34 configure libncurses5 5.7+20090803-2ubuntu2 5.7+20090803-2ubuntu2
2009-10-28 20:55:34 status unpacked libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:34 status half-configured libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:34 status installed libncurses5 5.7+20090803-2ubuntu2
2009-10-28 20:55:34 configure libattr1 1:2.4.43-3 1:2.4.43-3
2009-10-28 20:55:34 status unpacked libattr1 1:2.4.43-3
2009-10-28 20:55:34 status half-configured libattr1 1:2.4.43-3
2009-10-28 20:55:34 status installed libattr1 1:2.4.43-3
2009-10-28 20:55:34 configure e2fslibs 1.41.9-1ubuntu3 1.41.9-1ubuntu3
2009-10-28 20:55:34 status unpacked e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:34 status half-configured e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:34 status installed e2fslibs 1.41.9-1ubuntu3
2009-10-28 20:55:34 configure base-passwd 3.5.21 3.5.21
2009-10-28 20:55:34 status unpacked base-passwd 3.5.21
2009-10-28 20:55:34 status half-configured base-passwd 3.5.21
2009-10-28 20:55:34 status installed base-passwd 3.5.21
2009-10-28 20:55:34 configure libcomerr2 1.41.9-1ubuntu3 1.41.9-1ubuntu3
2009-10-28 20:55:34 status unpacked libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:34 status half-configured libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:34 status installed libcomerr2 1.41.9-1ubuntu3
2009-10-28 20:55:34 configure mawk 1.3.3-15ubuntu1 1.3.3-15ubuntu1
2009-10-28 20:55:34 status unpacked mawk 1.3.3-15ubuntu1
2009-10-28 20:55:34 status half-configured mawk 1.3.3-15ubuntu1
2009-10-28 20:55:34 update-alternatives: run with --quiet --install /usr/bin/awk awk /usr/bin/mawk 5 --slave /usr/share/man/man1/awk.1.gz awk.1.gz /usr/share/man/man1/mawk.1.gz --slave /usr/bin/nawk nawk /usr/bin/mawk --slave /usr/share/man/man1/nawk.1.gz nawk.1.gz /usr/share/man/man1/mawk.1.gz
2009-10-28 20:55:34 status installed mawk 1.3.3-15ubuntu1
2009-10-28 20:55:34 configure libdb4.7 4.7.25-7ubuntu2 4.7.25-7ubuntu2
2009-10-28 20:55:34 status unpacked libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:34 status half-configured libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:34 status installed libdb4.7 4.7.25-7ubuntu2
2009-10-28 20:55:34 configure grep 2.5.4-4 2.5.4-4
2009-10-28 20:55:34 status unpacked grep 2.5.4-4
2009-10-28 20:55:34 status half-configured grep 2.5.4-4
2009-10-28 20:55:34 status installed grep 2.5.4-4
2009-10-28 20:55:34 configure libacl1 2.2.47-2 2.2.47-2
2009-10-28 20:55:34 status unpacked libacl1 2.2.47-2
2009-10-28 20:55:34 status half-configured libacl1 2.2.47-2
2009-10-28 20:55:34 status installed libacl1 2.2.47-2
2009-10-28 20:55:34 configure libslang2 2.1.4-3 2.1.4-3
2009-10-28 20:55:34 status unpacked libslang2 2.1.4-3
2009-10-28 20:55:34 status half-configured libslang2 2.1.4-3
2009-10-28 20:55:34 status installed libslang2 2.1.4-3
2009-10-28 20:55:34 configure libss2 1.41.9-1ubuntu3 1.41.9-1ubuntu3
2009-10-28 20:55:34 status unpacked libss2 1.41.9-1ubuntu3
2009-10-28 20:55:34 status half-configured libss2 1.41.9-1ubuntu3
2009-10-28 20:55:34 status installed libss2 1.41.9-1ubuntu3
2009-10-28 20:55:34 configure findutils 4.4.2-1 4.4.2-1
2009-10-28 20:55:34 status unpacked findutils 4.4.2-1
2009-10-28 20:55:34 status half-configured findutils 4.4.2-1
2009-10-28 20:55:34 status installed findutils 4.4.2-1
2009-10-28 20:55:34 configure insserv 1.12.0-11 1.12.0-11
2009-10-28 20:55:34 status unpacked insserv 1.12.0-11
2009-10-28 20:55:34 status unpacked insserv 1.12.0-11
2009-10-28 20:55:34 status unpacked insserv 1.12.0-11
2009-10-28 20:55:34 status half-configured insserv 1.12.0-11
2009-10-28 20:55:34 status installed insserv 1.12.0-11
2009-10-28 20:55:34 configure gzip 1.3.12-8ubuntu1 1.3.12-8ubuntu1
2009-10-28 20:55:34 status unpacked gzip 1.3.12-8ubuntu1
2009-10-28 20:55:34 status half-configured gzip 1.3.12-8ubuntu1
2009-10-28 20:55:34 status installed gzip 1.3.12-8ubuntu1
2009-10-28 20:55:34 configure diff 2.8.1-13 2.8.1-13
2009-10-28 20:55:34 status unpacked diff 2.8.1-13
2009-10-28 20:55:34 status half-configured diff 2.8.1-13
2009-10-28 20:55:34 status installed diff 2.8.1-13
2009-10-28 20:55:34 configure libselinux1 2.0.85-2ubuntu2 2.0.85-2ubuntu2
2009-10-28 20:55:34 status unpacked libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:34 status half-configured libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:34 status installed libselinux1 2.0.85-2ubuntu2
2009-10-28 20:55:34 configure libstdc++6 4.4.1-4ubuntu8 4.4.1-4ubuntu8
2009-10-28 20:55:34 status unpacked libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:34 status half-configured libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:34 status installed libstdc++6 4.4.1-4ubuntu8
2009-10-28 20:55:34 configure dash 0.5.5.1-2ubuntu3 0.5.5.1-2ubuntu3
2009-10-28 20:55:34 status unpacked dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:34 status half-configured dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:35 status installed dash 0.5.5.1-2ubuntu3
2009-10-28 20:55:35 configure coreutils 7.4-2ubuntu1 7.4-2ubuntu1
2009-10-28 20:55:35 status unpacked coreutils 7.4-2ubuntu1
2009-10-28 20:55:35 status half-configured coreutils 7.4-2ubuntu1
2009-10-28 20:55:35 status installed coreutils 7.4-2ubuntu1
2009-10-28 20:55:35 configure makedev 2.3.1-88 2.3.1-88
2009-10-28 20:55:35 status unpacked makedev 2.3.1-88
2009-10-28 20:55:35 status half-configured makedev 2.3.1-88
2009-10-28 20:55:38 status installed makedev 2.3.1-88
2009-10-28 20:55:38 configure lzma 4.43-14ubuntu1 4.43-14ubuntu1
2009-10-28 20:55:38 status unpacked lzma 4.43-14ubuntu1
2009-10-28 20:55:38 status half-configured lzma 4.43-14ubuntu1
2009-10-28 20:55:38 status installed lzma 4.43-14ubuntu1
2009-10-28 20:55:38 configure ncurses-base 5.7+20090803-2ubuntu2 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status unpacked ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status unpacked ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status half-configured ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status installed ncurses-base 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 configure libssl0.9.8 0.9.8g-16ubuntu3 0.9.8g-16ubuntu3
2009-10-28 20:55:38 status unpacked libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:38 status half-configured libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:38 status installed libssl0.9.8 0.9.8g-16ubuntu3
2009-10-28 20:55:38 configure ncurses-bin 5.7+20090803-2ubuntu2 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status unpacked ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status half-configured ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 status installed ncurses-bin 5.7+20090803-2ubuntu2
2009-10-28 20:55:38 configure libpam-modules 1.1.0-2ubuntu1 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status unpacked libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status half-configured libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 status installed libpam-modules 1.1.0-2ubuntu1
2009-10-28 20:55:38 configure base-files 5.0.0ubuntu7 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status unpacked base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status half-configured base-files 5.0.0ubuntu7
2009-10-28 20:55:38 status installed base-files 5.0.0ubuntu7
2009-10-28 20:55:38 configure sed 4.2.1-1 4.2.1-1
2009-10-28 20:55:38 status unpacked sed 4.2.1-1
2009-10-28 20:55:38 status half-configured sed 4.2.1-1
2009-10-28 20:55:38 status installed sed 4.2.1-1
2009-10-28 20:55:38 configure passwd 1:4.1.4.1-1ubuntu2 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status unpacked passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status half-configured passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 status installed passwd 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:38 configure python2.6-minimal 2.6.4~rc2-0ubuntu1 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:38 status unpacked python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:38 status unpacked python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:38 status half-configured python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:39 status installed python2.6-minimal 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:39 configure libpam-runtime 1.1.0-2ubuntu1 1.1.0-2ubuntu1
2009-10-28 20:55:39 status unpacked libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:39 status unpacked libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:39 status unpacked libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:39 status half-configured libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:39 status installed libpam-runtime 1.1.0-2ubuntu1
2009-10-28 20:55:39 configure dpkg 1.15.4ubuntu2 1.15.4ubuntu2
2009-10-28 20:55:39 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status unpacked dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status half-configured dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 status installed dpkg 1.15.4ubuntu2
2009-10-28 20:55:39 configure sysvinit-utils 2.87dsf-4ubuntu11 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status half-configured sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status installed sysvinit-utils 2.87dsf-4ubuntu11
2009-10-28 20:55:39 configure bash 4.0-5ubuntu2 4.0-5ubuntu2
2009-10-28 20:55:39 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:39 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:39 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:39 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:39 status unpacked bash 4.0-5ubuntu2
2009-10-28 20:55:39 status half-configured bash 4.0-5ubuntu2
2009-10-28 20:55:39 update-alternatives: run with --install /usr/share/man/man7/builtins.7.gz builtins.7.gz /usr/share/man/man7/bash-builtins.7.gz 10
2009-10-28 20:55:39 update-alternatives: link group builtins.7.gz updated to point to /usr/share/man/man7/bash-builtins.7.gz
2009-10-28 20:55:39 status installed bash 4.0-5ubuntu2
2009-10-28 20:55:39 configure login 1:4.1.4.1-1ubuntu2 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status unpacked login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status half-configured login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 status installed login 1:4.1.4.1-1ubuntu2
2009-10-28 20:55:39 configure libuuid1 2.16-1ubuntu5 2.16-1ubuntu5
2009-10-28 20:55:39 status unpacked libuuid1 2.16-1ubuntu5
2009-10-28 20:55:39 status half-configured libuuid1 2.16-1ubuntu5
2009-10-28 20:55:39 status installed libuuid1 2.16-1ubuntu5
2009-10-28 20:55:39 configure lsb-base 4.0-0ubuntu5 4.0-0ubuntu5
2009-10-28 20:55:39 status unpacked lsb-base 4.0-0ubuntu5
2009-10-28 20:55:39 status unpacked lsb-base 4.0-0ubuntu5
2009-10-28 20:55:39 status half-configured lsb-base 4.0-0ubuntu5
2009-10-28 20:55:39 status installed lsb-base 4.0-0ubuntu5
2009-10-28 20:55:39 configure python-minimal 2.6.4~rc1-0ubuntu1 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:39 status unpacked python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:39 status half-configured python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:39 status installed python-minimal 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:39 configure sysv-rc 2.87dsf-4ubuntu11 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status half-configured sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status installed sysv-rc 2.87dsf-4ubuntu11
2009-10-28 20:55:39 configure libblkid1 2.16-1ubuntu5 2.16-1ubuntu5
2009-10-28 20:55:39 status unpacked libblkid1 2.16-1ubuntu5
2009-10-28 20:55:39 status unpacked libblkid1 2.16-1ubuntu5
2009-10-28 20:55:39 status half-configured libblkid1 2.16-1ubuntu5
2009-10-28 20:55:39 status installed libblkid1 2.16-1ubuntu5
2009-10-28 20:55:39 configure e2fsprogs 1.41.9-1ubuntu3 1.41.9-1ubuntu3
2009-10-28 20:55:39 status unpacked e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:39 status unpacked e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:39 status half-configured e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:39 status installed e2fsprogs 1.41.9-1ubuntu3
2009-10-28 20:55:39 configure mount 2.16-1ubuntu5 2.16-1ubuntu5
2009-10-28 20:55:39 status unpacked mount 2.16-1ubuntu5
2009-10-28 20:55:39 status half-configured mount 2.16-1ubuntu5
2009-10-28 20:55:39 status installed mount 2.16-1ubuntu5
2009-10-28 20:55:39 configure initscripts 2.87dsf-4ubuntu11 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status unpacked initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:39 status half-configured initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:40 status installed initscripts 2.87dsf-4ubuntu11
2009-10-28 20:55:40 configure upstart 0.6.3-10 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status unpacked upstart 0.6.3-10
2009-10-28 20:55:40 status half-configured upstart 0.6.3-10
2009-10-28 20:55:40 status installed upstart 0.6.3-10
2009-10-28 20:55:40 configure hostname 2.95ubuntu1 2.95ubuntu1
2009-10-28 20:55:40 status unpacked hostname 2.95ubuntu1
2009-10-28 20:55:40 status unpacked hostname 2.95ubuntu1
2009-10-28 20:55:40 status half-configured hostname 2.95ubuntu1
2009-10-28 20:55:40 status installed hostname 2.95ubuntu1
2009-10-28 20:55:40 configure util-linux 2.16-1ubuntu5 2.16-1ubuntu5
2009-10-28 20:55:40 status unpacked util-linux 2.16-1ubuntu5
2009-10-28 20:55:40 status unpacked util-linux 2.16-1ubuntu5
2009-10-28 20:55:40 status unpacked util-linux 2.16-1ubuntu5
2009-10-28 20:55:40 status half-configured util-linux 2.16-1ubuntu5
2009-10-28 20:55:40 update-alternatives: run with --install /usr/bin/pager pager /bin/more 50 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/more.1.gz
2009-10-28 20:55:40 update-alternatives: link group pager updated to point to /bin/more
2009-10-28 20:55:40 update-alternatives: run with --install /usr/bin/pager pager /usr/bin/pg 10 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/pg.1.gz
2009-10-28 20:55:40 status installed util-linux 2.16-1ubuntu5
2009-10-28 20:55:40 configure procps 1:3.2.8-1ubuntu3 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status unpacked procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 status half-configured procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 update-alternatives: run with --install /usr/bin/w w /usr/bin/w.procps 50 --slave /usr/share/man/man1/w.1.gz w.1.gz /usr/share/man/man1/w.procps.1.gz
2009-10-28 20:55:40 update-alternatives: link group w updated to point to /usr/bin/w.procps
2009-10-28 20:55:40 status installed procps 1:3.2.8-1ubuntu3
2009-10-28 20:55:40 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:40 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:40 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:41 startup archives unpack
2009-10-28 20:55:41 install adduser <none> 3.110ubuntu6
2009-10-28 20:55:41 status half-installed adduser 3.110ubuntu6
2009-10-28 20:55:41 status unpacked adduser 3.110ubuntu6
2009-10-28 20:55:41 status unpacked adduser 3.110ubuntu6
2009-10-28 20:55:41 install apt <none> 0.7.23.1ubuntu2
2009-10-28 20:55:41 status half-installed apt 0.7.23.1ubuntu2
2009-10-28 20:55:42 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:42 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:42 install apt-utils <none> 0.7.23.1ubuntu2
2009-10-28 20:55:42 status half-installed apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:42 status unpacked apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:42 status unpacked apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:42 install aptitude <none> 0.4.11.11-1ubuntu6
2009-10-28 20:55:42 status half-installed aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:55:42 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:55:42 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:55:42 install busybox-initramfs <none> 1:1.13.3-1ubuntu7
2009-10-28 20:55:42 status half-installed busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:43 status unpacked busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:43 status unpacked busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:43 install bzip2 <none> 1.0.5-3
2009-10-28 20:55:43 status half-installed bzip2 1.0.5-3
2009-10-28 20:55:43 status unpacked bzip2 1.0.5-3
2009-10-28 20:55:43 status unpacked bzip2 1.0.5-3
2009-10-28 20:55:43 install ca-certificates <none> 20090814
2009-10-28 20:55:43 status half-installed ca-certificates 20090814
2009-10-28 20:55:43 status unpacked ca-certificates 20090814
2009-10-28 20:55:43 status unpacked ca-certificates 20090814
2009-10-28 20:55:43 install console-setup <none> 1.34ubuntu4
2009-10-28 20:55:43 status half-installed console-setup 1.34ubuntu4
2009-10-28 20:55:43 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:55:43 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:55:43 install console-terminus <none> 4.28-1
2009-10-28 20:55:43 status half-installed console-terminus 4.28-1
2009-10-28 20:55:43 status unpacked console-terminus 4.28-1
2009-10-28 20:55:43 status unpacked console-terminus 4.28-1
2009-10-28 20:55:43 install cpio <none> 2.10-1ubuntu1
2009-10-28 20:55:43 status half-installed cpio 2.10-1ubuntu1
2009-10-28 20:55:43 status unpacked cpio 2.10-1ubuntu1
2009-10-28 20:55:43 status unpacked cpio 2.10-1ubuntu1
2009-10-28 20:55:43 install dhcp3-client <none> 3.1.2-1ubuntu7
2009-10-28 20:55:43 status half-installed dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:43 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:43 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:43 install dhcp3-common <none> 3.1.2-1ubuntu7
2009-10-28 20:55:43 status half-installed dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:43 status unpacked dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:43 status unpacked dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:43 install dmidecode <none> 2.9-1ubuntu2
2009-10-28 20:55:43 status half-installed dmidecode 2.9-1ubuntu2
2009-10-28 20:55:43 status unpacked dmidecode 2.9-1ubuntu2
2009-10-28 20:55:43 status unpacked dmidecode 2.9-1ubuntu2
2009-10-28 20:55:43 install dmsetup <none> 2:1.02.27-4ubuntu7
2009-10-28 20:55:43 status half-installed dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:55:43 status unpacked dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:55:43 status unpacked dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:55:43 install eject <none> 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:43 status half-installed eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:43 status unpacked eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:43 status unpacked eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:43 install file <none> 5.03-1ubuntu1
2009-10-28 20:55:43 status half-installed file 5.03-1ubuntu1
2009-10-28 20:55:43 status unpacked file 5.03-1ubuntu1
2009-10-28 20:55:43 status unpacked file 5.03-1ubuntu1
2009-10-28 20:55:43 install gnupg <none> 1.4.9-4ubuntu7
2009-10-28 20:55:43 status half-installed gnupg 1.4.9-4ubuntu7
2009-10-28 20:55:44 status unpacked gnupg 1.4.9-4ubuntu7
2009-10-28 20:55:44 status unpacked gnupg 1.4.9-4ubuntu7
2009-10-28 20:55:44 install gpgv <none> 1.4.9-4ubuntu7
2009-10-28 20:55:44 status half-installed gpgv 1.4.9-4ubuntu7
2009-10-28 20:55:44 status unpacked gpgv 1.4.9-4ubuntu7
2009-10-28 20:55:44 status unpacked gpgv 1.4.9-4ubuntu7
2009-10-28 20:55:44 install ifupdown <none> 0.6.8ubuntu21
2009-10-28 20:55:44 status half-installed ifupdown 0.6.8ubuntu21
2009-10-28 20:55:44 status unpacked ifupdown 0.6.8ubuntu21
2009-10-28 20:55:44 status unpacked ifupdown 0.6.8ubuntu21
2009-10-28 20:55:44 install initramfs-tools <none> 0.92bubuntu53
2009-10-28 20:55:44 status half-installed initramfs-tools 0.92bubuntu53
2009-10-28 20:55:44 status unpacked initramfs-tools 0.92bubuntu53
2009-10-28 20:55:44 status unpacked initramfs-tools 0.92bubuntu53
2009-10-28 20:55:44 install iproute <none> 20090324-1
2009-10-28 20:55:44 status half-installed iproute 20090324-1
2009-10-28 20:55:44 status unpacked iproute 20090324-1
2009-10-28 20:55:44 status unpacked iproute 20090324-1
2009-10-28 20:55:44 install iputils-ping <none> 3:20071127-1build1
2009-10-28 20:55:44 status half-installed iputils-ping 3:20071127-1build1
2009-10-28 20:55:44 status unpacked iputils-ping 3:20071127-1build1
2009-10-28 20:55:44 status unpacked iputils-ping 3:20071127-1build1
2009-10-28 20:55:44 install kbd <none> 1.15-1ubuntu1
2009-10-28 20:55:44 status half-installed kbd 1.15-1ubuntu1
2009-10-28 20:55:44 status unpacked kbd 1.15-1ubuntu1
2009-10-28 20:55:44 status unpacked kbd 1.15-1ubuntu1
2009-10-28 20:55:44 install klibc-utils <none> 1.5.15-1ubuntu2
2009-10-28 20:55:44 status half-installed klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:44 status unpacked klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:44 status unpacked klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:44 install laptop-detect <none> 0.13.7ubuntu1
2009-10-28 20:55:44 status half-installed laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:44 status unpacked laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:44 status unpacked laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:44 install less <none> 429-2
2009-10-28 20:55:44 status half-installed less 429-2
2009-10-28 20:55:44 status unpacked less 429-2
2009-10-28 20:55:44 status unpacked less 429-2
2009-10-28 20:55:44 install libatm1 <none> 2.4.1-17.2
2009-10-28 20:55:44 status half-installed libatm1 2.4.1-17.2
2009-10-28 20:55:44 status unpacked libatm1 2.4.1-17.2
2009-10-28 20:55:44 status unpacked libatm1 2.4.1-17.2
2009-10-28 20:55:44 install libbz2-1.0 <none> 1.0.5-3
2009-10-28 20:55:44 status half-installed libbz2-1.0 1.0.5-3
2009-10-28 20:55:44 status unpacked libbz2-1.0 1.0.5-3
2009-10-28 20:55:44 status unpacked libbz2-1.0 1.0.5-3
2009-10-28 20:55:44 install libc6-i686 <none> 2.10.1-0ubuntu15
2009-10-28 20:55:44 status half-installed libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:44 status unpacked libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:45 status unpacked libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:45 install libcap2 <none> 1:2.16-5ubuntu1
2009-10-28 20:55:45 status half-installed libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:45 status unpacked libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:45 status unpacked libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:45 install libclass-accessor-perl <none> 0.33-1
2009-10-28 20:55:45 status half-installed libclass-accessor-perl 0.33-1
2009-10-28 20:55:45 status unpacked libclass-accessor-perl 0.33-1
2009-10-28 20:55:45 status unpacked libclass-accessor-perl 0.33-1
2009-10-28 20:55:45 install libcurl3-gnutls <none> 7.19.5-1ubuntu2
2009-10-28 20:55:45 status half-installed libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:55:45 status unpacked libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:55:45 status unpacked libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:55:45 install libcwidget3 <none> 0.5.12-4ubuntu4
2009-10-28 20:55:45 status half-installed libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:55:45 status unpacked libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:55:45 status unpacked libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:55:45 install libdevmapper1.02.1 <none> 2:1.02.27-4ubuntu7
2009-10-28 20:55:45 status half-installed libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:45 status unpacked libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:45 status unpacked libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:45 install libept0 <none> 0.5.26ubuntu3
2009-10-28 20:55:45 status half-installed libept0 0.5.26ubuntu3
2009-10-28 20:55:45 status unpacked libept0 0.5.26ubuntu3
2009-10-28 20:55:45 status unpacked libept0 0.5.26ubuntu3
2009-10-28 20:55:45 install libfribidi0 <none> 0.10.9-1build1
2009-10-28 20:55:45 status half-installed libfribidi0 0.10.9-1build1
2009-10-28 20:55:45 status unpacked libfribidi0 0.10.9-1build1
2009-10-28 20:55:45 status unpacked libfribidi0 0.10.9-1build1
2009-10-28 20:55:45 install libgcrypt11 <none> 1.4.4-2ubuntu2
2009-10-28 20:55:45 status half-installed libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:45 status unpacked libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:45 status unpacked libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:45 install libgdbm3 <none> 1.8.3-4
2009-10-28 20:55:45 status half-installed libgdbm3 1.8.3-4
2009-10-28 20:55:45 status unpacked libgdbm3 1.8.3-4
2009-10-28 20:55:45 status unpacked libgdbm3 1.8.3-4
2009-10-28 20:55:45 install libglib2.0-0 <none> 2.22.2-0ubuntu1
2009-10-28 20:55:45 status half-installed libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:45 status unpacked libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:45 status unpacked libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:45 install libglib2.0-data <none> 2.22.2-0ubuntu1
2009-10-28 20:55:45 status half-installed libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:45 status unpacked libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:45 status unpacked libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:45 install libgnutls26 <none> 2.8.3-2
2009-10-28 20:55:45 status half-installed libgnutls26 2.8.3-2
2009-10-28 20:55:45 status unpacked libgnutls26 2.8.3-2
2009-10-28 20:55:45 status unpacked libgnutls26 2.8.3-2
2009-10-28 20:55:45 install libgpg-error0 <none> 1.6-1ubuntu1
2009-10-28 20:55:45 status half-installed libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:45 status unpacked libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:45 status unpacked libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:45 install libgpm2 <none> 1.20.4-3.2ubuntu1
2009-10-28 20:55:45 status half-installed libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:45 status unpacked libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:45 status unpacked libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:45 install libgssapi-krb5-2 <none> 1.7dfsg~beta3-1
2009-10-28 20:55:45 status half-installed libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:55:45 status unpacked libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:55:45 status unpacked libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:55:45 install libidn11 <none> 1.15-1
2009-10-28 20:55:45 status half-installed libidn11 1.15-1
2009-10-28 20:55:45 status unpacked libidn11 1.15-1
2009-10-28 20:55:45 status unpacked libidn11 1.15-1
2009-10-28 20:55:45 install libio-string-perl <none> 1.08-2
2009-10-28 20:55:45 status half-installed libio-string-perl 1.08-2
2009-10-28 20:55:45 status unpacked libio-string-perl 1.08-2
2009-10-28 20:55:45 status unpacked libio-string-perl 1.08-2
2009-10-28 20:55:45 install libk5crypto3 <none> 1.7dfsg~beta3-1
2009-10-28 20:55:45 status half-installed libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:46 install libkeyutils1 <none> 1.2-10
2009-10-28 20:55:46 status half-installed libkeyutils1 1.2-10
2009-10-28 20:55:46 status unpacked libkeyutils1 1.2-10
2009-10-28 20:55:46 status unpacked libkeyutils1 1.2-10
2009-10-28 20:55:46 install libklibc <none> 1.5.15-1ubuntu2
2009-10-28 20:55:46 status half-installed libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:46 status unpacked libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:46 status unpacked libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:46 install libkrb5-3 <none> 1.7dfsg~beta3-1
2009-10-28 20:55:46 status half-installed libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:55:46 install libkrb5support0 <none> 1.7dfsg~beta3-1
2009-10-28 20:55:46 status half-installed libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:46 status unpacked libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:46 install libldap-2.4-2 <none> 2.4.18-0ubuntu1
2009-10-28 20:55:46 status half-installed libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:55:46 status unpacked libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:55:46 status unpacked libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:55:46 install liblockfile1 <none> 1.08-3
2009-10-28 20:55:46 status half-installed liblockfile1 1.08-3
2009-10-28 20:55:46 status unpacked liblockfile1 1.08-3
2009-10-28 20:55:46 status unpacked liblockfile1 1.08-3
2009-10-28 20:55:46 install libmagic1 <none> 5.03-1ubuntu1
2009-10-28 20:55:46 status half-installed libmagic1 5.03-1ubuntu1
2009-10-28 20:55:46 status unpacked libmagic1 5.03-1ubuntu1
2009-10-28 20:55:46 status unpacked libmagic1 5.03-1ubuntu1
2009-10-28 20:55:46 install libncursesw5 <none> 5.7+20090803-2ubuntu2
2009-10-28 20:55:46 status half-installed libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:46 status unpacked libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:46 status unpacked libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:46 install libnewt0.52 <none> 0.52.10-4ubuntu1
2009-10-28 20:55:46 status half-installed libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:46 status unpacked libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:46 status unpacked libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:46 install libparse-debianchangelog-perl <none> 1.1.1-2ubuntu1
2009-10-28 20:55:46 status half-installed libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:55:46 status unpacked libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:55:46 status unpacked libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:55:46 install libpcre3 <none> 7.8-3
2009-10-28 20:55:46 status half-installed libpcre3 7.8-3
2009-10-28 20:55:46 status unpacked libpcre3 7.8-3
2009-10-28 20:55:46 status unpacked libpcre3 7.8-3
2009-10-28 20:55:46 install libpopt0 <none> 1.14-4
2009-10-28 20:55:46 status half-installed libpopt0 1.14-4
2009-10-28 20:55:46 status unpacked libpopt0 1.14-4
2009-10-28 20:55:46 status unpacked libpopt0 1.14-4
2009-10-28 20:55:46 install libreadline6 <none> 6.0-5
2009-10-28 20:55:46 status half-installed libreadline6 6.0-5
2009-10-28 20:55:46 status unpacked libreadline6 6.0-5
2009-10-28 20:55:46 status unpacked libreadline6 6.0-5
2009-10-28 20:55:46 install libsasl2-2 <none> 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status half-installed libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status unpacked libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status unpacked libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 install libsasl2-modules <none> 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status half-installed libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status unpacked libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 status unpacked libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:55:46 install libsigc++-2.0-0c2a <none> 2.0.18-2
2009-10-28 20:55:46 status half-installed libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:46 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:47 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:47 install libsqlite3-0 <none> 3.6.16-1ubuntu1
2009-10-28 20:55:47 status half-installed libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:47 status unpacked libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:47 status unpacked libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:47 install libsub-name-perl <none> 0.04-1
2009-10-28 20:55:47 status half-installed libsub-name-perl 0.04-1
2009-10-28 20:55:47 status unpacked libsub-name-perl 0.04-1
2009-10-28 20:55:47 status unpacked libsub-name-perl 0.04-1
2009-10-28 20:55:47 install libtasn1-3 <none> 2.2-1
2009-10-28 20:55:47 status half-installed libtasn1-3 2.2-1
2009-10-28 20:55:47 status unpacked libtasn1-3 2.2-1
2009-10-28 20:55:47 status unpacked libtasn1-3 2.2-1
2009-10-28 20:55:47 install libtimedate-perl <none> 1.1600-9
2009-10-28 20:55:47 status half-installed libtimedate-perl 1.1600-9
2009-10-28 20:55:47 status unpacked libtimedate-perl 1.1600-9
2009-10-28 20:55:47 status unpacked libtimedate-perl 1.1600-9
2009-10-28 20:55:47 install libusb-0.1-4 <none> 2:0.1.12-13
2009-10-28 20:55:47 status half-installed libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:47 status unpacked libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:47 status unpacked libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:47 install libxapian15 <none> 1.0.15-2ubuntu2
2009-10-28 20:55:47 status half-installed libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:47 status unpacked libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:47 status unpacked libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:47 install libxml2 <none> 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:47 status half-installed libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:47 status unpacked libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:47 status unpacked libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:47 install lockfile-progs <none> 0.1.13
2009-10-28 20:55:47 status half-installed lockfile-progs 0.1.13
2009-10-28 20:55:47 status unpacked lockfile-progs 0.1.13
2009-10-28 20:55:47 status unpacked lockfile-progs 0.1.13
2009-10-28 20:55:47 install lsb-release <none> 4.0-0ubuntu5
2009-10-28 20:55:47 status half-installed lsb-release 4.0-0ubuntu5
2009-10-28 20:55:47 status unpacked lsb-release 4.0-0ubuntu5
2009-10-28 20:55:47 status unpacked lsb-release 4.0-0ubuntu5
2009-10-28 20:55:47 install make <none> 3.81-6
2009-10-28 20:55:47 status half-installed make 3.81-6
2009-10-28 20:55:47 status unpacked make 3.81-6
2009-10-28 20:55:47 status unpacked make 3.81-6
2009-10-28 20:55:47 install mime-support <none> 3.46-1ubuntu1
2009-10-28 20:55:47 status half-installed mime-support 3.46-1ubuntu1
2009-10-28 20:55:47 status unpacked mime-support 3.46-1ubuntu1
2009-10-28 20:55:47 status unpacked mime-support 3.46-1ubuntu1
2009-10-28 20:55:47 install module-init-tools <none> 3.10-3
2009-10-28 20:55:47 status half-installed module-init-tools 3.10-3
2009-10-28 20:55:47 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:47 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:47 install net-tools <none> 1.60-23ubuntu1
2009-10-28 20:55:47 status half-installed net-tools 1.60-23ubuntu1
2009-10-28 20:55:48 status unpacked net-tools 1.60-23ubuntu1
2009-10-28 20:55:48 status unpacked net-tools 1.60-23ubuntu1
2009-10-28 20:55:48 install netbase <none> 4.35ubuntu2
2009-10-28 20:55:48 status half-installed netbase 4.35ubuntu2
2009-10-28 20:55:48 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:48 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:48 install netcat <none> 1.10-38
2009-10-28 20:55:48 status half-installed netcat 1.10-38
2009-10-28 20:55:48 status unpacked netcat 1.10-38
2009-10-28 20:55:48 status unpacked netcat 1.10-38
2009-10-28 20:55:48 install netcat-traditional <none> 1.10-38
2009-10-28 20:55:48 status half-installed netcat-traditional 1.10-38
2009-10-28 20:55:48 status unpacked netcat-traditional 1.10-38
2009-10-28 20:55:48 status unpacked netcat-traditional 1.10-38
2009-10-28 20:55:48 install ntpdate <none> 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:55:48 status half-installed ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:55:48 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:55:48 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:55:48 install openssl <none> 0.9.8g-16ubuntu3
2009-10-28 20:55:48 status half-installed openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:48 status unpacked openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:48 status unpacked openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:48 install perl <none> 5.10.0-24ubuntu4
2009-10-28 20:55:48 status half-installed perl 5.10.0-24ubuntu4
2009-10-28 20:55:49 status unpacked perl 5.10.0-24ubuntu4
2009-10-28 20:55:49 status unpacked perl 5.10.0-24ubuntu4
2009-10-28 20:55:49 install perl-modules <none> 5.10.0-24ubuntu4
2009-10-28 20:55:49 status half-installed perl-modules 5.10.0-24ubuntu4
2009-10-28 20:55:50 status unpacked perl-modules 5.10.0-24ubuntu4
2009-10-28 20:55:50 status unpacked perl-modules 5.10.0-24ubuntu4
2009-10-28 20:55:50 install python <none> 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:50 status half-installed python 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:50 status unpacked python 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:50 status unpacked python 2.6.4~rc1-0ubuntu1
2009-10-28 20:55:50 install python-central <none> 0.6.11ubuntu9
2009-10-28 20:55:50 status half-installed python-central 0.6.11ubuntu9
2009-10-28 20:55:50 status unpacked python-central 0.6.11ubuntu9
2009-10-28 20:55:50 status unpacked python-central 0.6.11ubuntu9
2009-10-28 20:55:50 install python2.6 <none> 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:50 status half-installed python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:51 status unpacked python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:51 status unpacked python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:55:51 install readline-common <none> 6.0-5
2009-10-28 20:55:51 status half-installed readline-common 6.0-5
2009-10-28 20:55:51 status unpacked readline-common 6.0-5
2009-10-28 20:55:51 status unpacked readline-common 6.0-5
2009-10-28 20:55:51 install rsyslog <none> 4.2.0-2ubuntu5
2009-10-28 20:55:51 status half-installed rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:51 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:51 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:51 install sgml-base <none> 1.26
2009-10-28 20:55:51 status half-installed sgml-base 1.26
2009-10-28 20:55:51 status unpacked sgml-base 1.26
2009-10-28 20:55:51 status unpacked sgml-base 1.26
2009-10-28 20:55:51 install shared-mime-info <none> 0.70-0ubuntu1
2009-10-28 20:55:51 status half-installed shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:51 status unpacked shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:51 status unpacked shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:51 install sudo <none> 1.7.0-1ubuntu2
2009-10-28 20:55:51 status half-installed sudo 1.7.0-1ubuntu2
2009-10-28 20:55:51 status unpacked sudo 1.7.0-1ubuntu2
2009-10-28 20:55:51 status unpacked sudo 1.7.0-1ubuntu2
2009-10-28 20:55:51 install tasksel <none> 2.73ubuntu23
2009-10-28 20:55:51 status half-installed tasksel 2.73ubuntu23
2009-10-28 20:55:51 status unpacked tasksel 2.73ubuntu23
2009-10-28 20:55:51 status unpacked tasksel 2.73ubuntu23
2009-10-28 20:55:51 install tasksel-data <none> 2.73ubuntu23
2009-10-28 20:55:51 status half-installed tasksel-data 2.73ubuntu23
2009-10-28 20:55:51 status unpacked tasksel-data 2.73ubuntu23
2009-10-28 20:55:51 status unpacked tasksel-data 2.73ubuntu23
2009-10-28 20:55:51 install ubuntu-keyring <none> 2009.08.28
2009-10-28 20:55:51 status half-installed ubuntu-keyring 2009.08.28
2009-10-28 20:55:51 status unpacked ubuntu-keyring 2009.08.28
2009-10-28 20:55:51 status unpacked ubuntu-keyring 2009.08.28
2009-10-28 20:55:51 install ubuntu-minimal <none> 1.175
2009-10-28 20:55:51 status half-installed ubuntu-minimal 1.175
2009-10-28 20:55:52 status unpacked ubuntu-minimal 1.175
2009-10-28 20:55:52 status unpacked ubuntu-minimal 1.175
2009-10-28 20:55:52 install ucf <none> 3.0018ubuntu1
2009-10-28 20:55:52 status half-installed ucf 3.0018ubuntu1
2009-10-28 20:55:52 status unpacked ucf 3.0018ubuntu1
2009-10-28 20:55:52 status unpacked ucf 3.0018ubuntu1
2009-10-28 20:55:52 install udev <none> 147~-6
2009-10-28 20:55:52 status half-installed udev 147~-6
2009-10-28 20:55:52 status unpacked udev 147~-6
2009-10-28 20:55:52 status unpacked udev 147~-6
2009-10-28 20:55:52 install vim-common <none> 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status half-installed vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status unpacked vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status unpacked vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 install vim-tiny <none> 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status half-installed vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status unpacked vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 status unpacked vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:52 install whiptail <none> 0.52.10-4ubuntu1
2009-10-28 20:55:52 status half-installed whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:52 status unpacked whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:52 status unpacked whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:52 install xkb-data <none> 1.6-1ubuntu5
2009-10-28 20:55:52 status half-installed xkb-data 1.6-1ubuntu5
2009-10-28 20:55:52 status unpacked xkb-data 1.6-1ubuntu5
2009-10-28 20:55:52 status unpacked xkb-data 1.6-1ubuntu5
2009-10-28 20:55:52 install xml-core <none> 0.12
2009-10-28 20:55:52 status half-installed xml-core 0.12
2009-10-28 20:55:52 status unpacked xml-core 0.12
2009-10-28 20:55:52 status unpacked xml-core 0.12
2009-10-28 20:55:53 startup packages configure
2009-10-28 20:55:53 configure sudo 1.7.0-1ubuntu2 1.7.0-1ubuntu2
2009-10-28 20:55:53 status unpacked sudo 1.7.0-1ubuntu2
2009-10-28 20:55:53 status unpacked sudo 1.7.0-1ubuntu2
2009-10-28 20:55:53 status half-configured sudo 1.7.0-1ubuntu2
2009-10-28 20:55:53 status installed sudo 1.7.0-1ubuntu2
2009-10-28 20:55:53 configure libxml2 2.7.5.dfsg-1ubuntu1 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:53 status unpacked libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:53 status half-configured libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:53 status installed libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:55:53 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 20:55:53 configure module-init-tools 3.10-3 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status unpacked module-init-tools 3.10-3
2009-10-28 20:55:53 status half-configured module-init-tools 3.10-3
2009-10-28 20:55:53 status installed module-init-tools 3.10-3
2009-10-28 20:55:53 configure libgdbm3 1.8.3-4 1.8.3-4
2009-10-28 20:55:53 status unpacked libgdbm3 1.8.3-4
2009-10-28 20:55:53 status half-configured libgdbm3 1.8.3-4
2009-10-28 20:55:53 status installed libgdbm3 1.8.3-4
2009-10-28 20:55:53 configure libtasn1-3 2.2-1 2.2-1
2009-10-28 20:55:53 status unpacked libtasn1-3 2.2-1
2009-10-28 20:55:53 status half-configured libtasn1-3 2.2-1
2009-10-28 20:55:53 status installed libtasn1-3 2.2-1
2009-10-28 20:55:53 configure libpopt0 1.14-4 1.14-4
2009-10-28 20:55:53 status unpacked libpopt0 1.14-4
2009-10-28 20:55:53 status half-configured libpopt0 1.14-4
2009-10-28 20:55:53 status installed libpopt0 1.14-4
2009-10-28 20:55:53 configure libusb-0.1-4 2:0.1.12-13 2:0.1.12-13
2009-10-28 20:55:53 status unpacked libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:53 status half-configured libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:53 status installed libusb-0.1-4 2:0.1.12-13
2009-10-28 20:55:53 configure libgpg-error0 1.6-1ubuntu1 1.6-1ubuntu1
2009-10-28 20:55:53 status unpacked libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:53 status half-configured libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:53 status installed libgpg-error0 1.6-1ubuntu1
2009-10-28 20:55:53 configure ucf 3.0018ubuntu1 3.0018ubuntu1
2009-10-28 20:55:53 status unpacked ucf 3.0018ubuntu1
2009-10-28 20:55:53 status unpacked ucf 3.0018ubuntu1
2009-10-28 20:55:53 status half-configured ucf 3.0018ubuntu1
2009-10-28 20:55:53 status installed ucf 3.0018ubuntu1
2009-10-28 20:55:53 configure vim-common 2:7.2.245-2ubuntu2 2:7.2.245-2ubuntu2
2009-10-28 20:55:53 status unpacked vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:53 status unpacked vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:53 status half-configured vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:53 status installed vim-common 2:7.2.245-2ubuntu2
2009-10-28 20:55:53 configure openssl 0.9.8g-16ubuntu3 0.9.8g-16ubuntu3
2009-10-28 20:55:53 status unpacked openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:53 status unpacked openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:53 status half-configured openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:53 status installed openssl 0.9.8g-16ubuntu3
2009-10-28 20:55:53 configure apt 0.7.23.1ubuntu2 0.7.23.1ubuntu2
2009-10-28 20:55:53 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status unpacked apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status half-configured apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 status installed apt 0.7.23.1ubuntu2
2009-10-28 20:55:53 configure netbase 4.35ubuntu2 4.35ubuntu2
2009-10-28 20:55:53 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:53 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:53 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:53 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:53 status unpacked netbase 4.35ubuntu2
2009-10-28 20:55:53 status half-configured netbase 4.35ubuntu2
2009-10-28 20:55:53 status installed netbase 4.35ubuntu2
2009-10-28 20:55:53 configure libmagic1 5.03-1ubuntu1 5.03-1ubuntu1
2009-10-28 20:55:53 status unpacked libmagic1 5.03-1ubuntu1
2009-10-28 20:55:53 status half-configured libmagic1 5.03-1ubuntu1
2009-10-28 20:55:53 status installed libmagic1 5.03-1ubuntu1
2009-10-28 20:55:53 configure libxapian15 1.0.15-2ubuntu2 1.0.15-2ubuntu2
2009-10-28 20:55:53 status unpacked libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:53 status half-configured libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:53 status installed libxapian15 1.0.15-2ubuntu2
2009-10-28 20:55:53 configure dmidecode 2.9-1ubuntu2 2.9-1ubuntu2
2009-10-28 20:55:53 status unpacked dmidecode 2.9-1ubuntu2
2009-10-28 20:55:54 status half-configured dmidecode 2.9-1ubuntu2
2009-10-28 20:55:54 status installed dmidecode 2.9-1ubuntu2
2009-10-28 20:55:54 configure file 5.03-1ubuntu1 5.03-1ubuntu1
2009-10-28 20:55:54 status unpacked file 5.03-1ubuntu1
2009-10-28 20:55:54 status unpacked file 5.03-1ubuntu1
2009-10-28 20:55:54 status unpacked file 5.03-1ubuntu1
2009-10-28 20:55:54 status half-configured file 5.03-1ubuntu1
2009-10-28 20:55:54 status installed file 5.03-1ubuntu1
2009-10-28 20:55:54 configure libfribidi0 0.10.9-1build1 0.10.9-1build1
2009-10-28 20:55:54 status unpacked libfribidi0 0.10.9-1build1
2009-10-28 20:55:54 status half-configured libfribidi0 0.10.9-1build1
2009-10-28 20:55:54 status installed libfribidi0 0.10.9-1build1
2009-10-28 20:55:54 configure adduser 3.110ubuntu6 3.110ubuntu6
2009-10-28 20:55:54 status unpacked adduser 3.110ubuntu6
2009-10-28 20:55:54 status unpacked adduser 3.110ubuntu6
2009-10-28 20:55:54 status half-configured adduser 3.110ubuntu6
2009-10-28 20:55:54 status installed adduser 3.110ubuntu6
2009-10-28 20:55:54 configure libklibc 1.5.15-1ubuntu2 1.5.15-1ubuntu2
2009-10-28 20:55:54 status unpacked libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:54 status half-configured libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:54 status installed libklibc 1.5.15-1ubuntu2
2009-10-28 20:55:54 configure libsqlite3-0 3.6.16-1ubuntu1 3.6.16-1ubuntu1
2009-10-28 20:55:54 status unpacked libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:54 status half-configured libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:54 status installed libsqlite3-0 3.6.16-1ubuntu1
2009-10-28 20:55:54 configure libkeyutils1 1.2-10 1.2-10
2009-10-28 20:55:54 status unpacked libkeyutils1 1.2-10
2009-10-28 20:55:54 status half-configured libkeyutils1 1.2-10
2009-10-28 20:55:54 status installed libkeyutils1 1.2-10
2009-10-28 20:55:54 configure iproute 20090324-1 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status unpacked iproute 20090324-1
2009-10-28 20:55:54 status half-configured iproute 20090324-1
2009-10-28 20:55:54 status installed iproute 20090324-1
2009-10-28 20:55:54 configure libdevmapper1.02.1 2:1.02.27-4ubuntu7 2:1.02.27-4ubuntu7
2009-10-28 20:55:54 status unpacked libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:54 status half-configured libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:54 status installed libdevmapper1.02.1 2:1.02.27-4ubuntu7
2009-10-28 20:55:54 configure libidn11 1.15-1 1.15-1
2009-10-28 20:55:54 status unpacked libidn11 1.15-1
2009-10-28 20:55:54 status half-configured libidn11 1.15-1
2009-10-28 20:55:54 status installed libidn11 1.15-1
2009-10-28 20:55:54 configure libatm1 2.4.1-17.2 2.4.1-17.2
2009-10-28 20:55:54 status unpacked libatm1 2.4.1-17.2
2009-10-28 20:55:54 status half-configured libatm1 2.4.1-17.2
2009-10-28 20:55:54 status installed libatm1 2.4.1-17.2
2009-10-28 20:55:54 configure klibc-utils 1.5.15-1ubuntu2 1.5.15-1ubuntu2
2009-10-28 20:55:54 status unpacked klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:54 status half-configured klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:54 status installed klibc-utils 1.5.15-1ubuntu2
2009-10-28 20:55:54 configure libkrb5support0 1.7dfsg~beta3-1 1.7dfsg~beta3-1
2009-10-28 20:55:54 status unpacked libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:54 status half-configured libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:54 status installed libkrb5support0 1.7dfsg~beta3-1
2009-10-28 20:55:54 configure libnewt0.52 0.52.10-4ubuntu1 0.52.10-4ubuntu1
2009-10-28 20:55:54 status unpacked libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:54 status half-configured libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:54 status installed libnewt0.52 0.52.10-4ubuntu1
2009-10-28 20:55:54 configure net-tools 1.60-23ubuntu1 1.60-23ubuntu1
2009-10-28 20:55:54 status unpacked net-tools 1.60-23ubuntu1
2009-10-28 20:55:54 status half-configured net-tools 1.60-23ubuntu1
2009-10-28 20:55:54 status installed net-tools 1.60-23ubuntu1
2009-10-28 20:55:54 configure xkb-data 1.6-1ubuntu5 1.6-1ubuntu5
2009-10-28 20:55:54 status unpacked xkb-data 1.6-1ubuntu5
2009-10-28 20:55:54 status unpacked xkb-data 1.6-1ubuntu5
2009-10-28 20:55:54 status half-configured xkb-data 1.6-1ubuntu5
2009-10-28 20:55:54 status installed xkb-data 1.6-1ubuntu5
2009-10-28 20:55:54 configure libsigc++-2.0-0c2a 2.0.18-2 2.0.18-2
2009-10-28 20:55:54 status unpacked libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:54 status half-configured libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:54 status installed libsigc++-2.0-0c2a 2.0.18-2
2009-10-28 20:55:54 configure netcat-traditional 1.10-38 1.10-38
2009-10-28 20:55:54 status unpacked netcat-traditional 1.10-38
2009-10-28 20:55:54 status half-configured netcat-traditional 1.10-38
2009-10-28 20:55:54 update-alternatives: run with --install /bin/nc nc /bin/nc.traditional 10 --slave /bin/netcat netcat /bin/nc.traditional --slave /usr/share/man/man1/nc.1.gz nc.1.gz /usr/share/man/man1/nc_traditional.1.gz --slave /usr/share/man/man1/netcat.1.gz netcat.1.gz /usr/share/man/man1/nc_traditional.1.gz
2009-10-28 20:55:54 update-alternatives: link group nc updated to point to /bin/nc.traditional
2009-10-28 20:55:54 status installed netcat-traditional 1.10-38
2009-10-28 20:55:54 configure libgpm2 1.20.4-3.2ubuntu1 1.20.4-3.2ubuntu1
2009-10-28 20:55:54 status unpacked libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:54 status half-configured libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:54 status installed libgpm2 1.20.4-3.2ubuntu1
2009-10-28 20:55:54 configure libpcre3 7.8-3 7.8-3
2009-10-28 20:55:54 status unpacked libpcre3 7.8-3
2009-10-28 20:55:54 status half-configured libpcre3 7.8-3
2009-10-28 20:55:54 status installed libpcre3 7.8-3
2009-10-28 20:55:54 configure libept0 0.5.26ubuntu3 0.5.26ubuntu3
2009-10-28 20:55:54 status unpacked libept0 0.5.26ubuntu3
2009-10-28 20:55:54 status half-configured libept0 0.5.26ubuntu3
2009-10-28 20:55:54 status installed libept0 0.5.26ubuntu3
2009-10-28 20:55:54 configure libncursesw5 5.7+20090803-2ubuntu2 5.7+20090803-2ubuntu2
2009-10-28 20:55:54 status unpacked libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:54 status half-configured libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:54 status installed libncursesw5 5.7+20090803-2ubuntu2
2009-10-28 20:55:54 configure eject 2.1.5+deb1+cvs20081104-6 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:54 status unpacked eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:54 status half-configured eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:54 status installed eject 2.1.5+deb1+cvs20081104-6
2009-10-28 20:55:54 configure busybox-initramfs 1:1.13.3-1ubuntu7 1:1.13.3-1ubuntu7
2009-10-28 20:55:54 status unpacked busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:54 status half-configured busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:54 status installed busybox-initramfs 1:1.13.3-1ubuntu7
2009-10-28 20:55:54 configure iputils-ping 3:20071127-1build1 3:20071127-1build1
2009-10-28 20:55:54 status unpacked iputils-ping 3:20071127-1build1
2009-10-28 20:55:54 status half-configured iputils-ping 3:20071127-1build1
2009-10-28 20:55:54 status installed iputils-ping 3:20071127-1build1
2009-10-28 20:55:54 configure libbz2-1.0 1.0.5-3 1.0.5-3
2009-10-28 20:55:54 status unpacked libbz2-1.0 1.0.5-3
2009-10-28 20:55:54 status half-configured libbz2-1.0 1.0.5-3
2009-10-28 20:55:54 status installed libbz2-1.0 1.0.5-3
2009-10-28 20:55:54 configure console-terminus 4.28-1 4.28-1
2009-10-28 20:55:54 status unpacked console-terminus 4.28-1
2009-10-28 20:55:54 status half-configured console-terminus 4.28-1
2009-10-28 20:55:54 status installed console-terminus 4.28-1
2009-10-28 20:55:54 configure libc6-i686 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:55:54 status unpacked libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:54 status half-configured libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:54 status installed libc6-i686 2.10.1-0ubuntu15
2009-10-28 20:55:54 configure mime-support 3.46-1ubuntu1 3.46-1ubuntu1
2009-10-28 20:55:54 status unpacked mime-support 3.46-1ubuntu1
2009-10-28 20:55:54 status unpacked mime-support 3.46-1ubuntu1
2009-10-28 20:55:54 status unpacked mime-support 3.46-1ubuntu1
2009-10-28 20:55:54 status half-configured mime-support 3.46-1ubuntu1
2009-10-28 20:55:54 update-alternatives: run with --install /usr/bin/view view /usr/bin/see 1 --slave /usr/share/man/man1/view.1.gz view.1.gz /usr/share/man/man1/see.1.gz
2009-10-28 20:55:54 update-alternatives: link group view updated to point to /usr/bin/see
2009-10-28 20:55:54 status installed mime-support 3.46-1ubuntu1
2009-10-28 20:55:54 configure dhcp3-common 3.1.2-1ubuntu7 3.1.2-1ubuntu7
2009-10-28 20:55:54 status unpacked dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:54 status half-configured dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:54 status installed dhcp3-common 3.1.2-1ubuntu7
2009-10-28 20:55:54 configure apt-utils 0.7.23.1ubuntu2 0.7.23.1ubuntu2
2009-10-28 20:55:54 status unpacked apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:54 status half-configured apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:54 status installed apt-utils 0.7.23.1ubuntu2
2009-10-28 20:55:54 configure make 3.81-6 3.81-6
2009-10-28 20:55:54 status unpacked make 3.81-6
2009-10-28 20:55:55 status half-configured make 3.81-6
2009-10-28 20:55:55 status installed make 3.81-6
2009-10-28 20:55:55 configure rsyslog 4.2.0-2ubuntu5 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status unpacked rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status half-configured rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 status installed rsyslog 4.2.0-2ubuntu5
2009-10-28 20:55:55 configure cpio 2.10-1ubuntu1 2.10-1ubuntu1
2009-10-28 20:55:55 status unpacked cpio 2.10-1ubuntu1
2009-10-28 20:55:55 status half-configured cpio 2.10-1ubuntu1
2009-10-28 20:55:55 update-alternatives: run with --install /bin/mt mt /bin/mt-gnu 10 --slave /usr/share/man/man1/mt.1.gz mt.1.gz /usr/share/man/man1/mt-gnu.1.gz
2009-10-28 20:55:55 update-alternatives: link group mt updated to point to /bin/mt-gnu
2009-10-28 20:55:55 status installed cpio 2.10-1ubuntu1
2009-10-28 20:55:55 configure ca-certificates 20090814 20090814
2009-10-28 20:55:55 status unpacked ca-certificates 20090814
2009-10-28 20:55:55 status half-configured ca-certificates 20090814
2009-10-28 20:55:58 status installed ca-certificates 20090814
2009-10-28 20:55:58 configure vim-tiny 2:7.2.245-2ubuntu2 2:7.2.245-2ubuntu2
2009-10-28 20:55:58 status unpacked vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:58 status unpacked vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:58 status half-configured vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:58 update-alternatives: run with --install /usr/bin/rview rview /usr/bin/vim.tiny 10
2009-10-28 20:55:58 update-alternatives: link group rview updated to point to /usr/bin/vim.tiny
2009-10-28 20:55:58 update-alternatives: run with --install /usr/bin/vi vi /usr/bin/vim.tiny 10 --slave /usr/share/man/fr/man1/vi.1.gz vi.fr.1.gz /usr/share/man/fr/man1/vim.1.gz --slave /usr/share/man/it/man1/vi.1.gz vi.it.1.gz /usr/share/man/it/man1/vim.1.gz --slave /usr/share/man/pl/man1/vi.1.gz vi.pl.1.gz /usr/share/man/pl/man1/vim.1.gz --slave /usr/share/man/ru/man1/vi.1.gz vi.ru.1.gz /usr/share/man/ru/man1/vim.1.gz --slave /usr/share/man/man1/vi.1.gz vi.1.gz /usr/share/man/man1/vim.1.gz
2009-10-28 20:55:58 update-alternatives: link group vi updated to point to /usr/bin/vim.tiny
2009-10-28 20:55:58 update-alternatives: run with --install /usr/bin/view view /usr/bin/vim.tiny 10 --slave /usr/share/man/fr/man1/view.1.gz view.fr.1.gz /usr/share/man/fr/man1/vim.1.gz --slave /usr/share/man/it/man1/view.1.gz view.it.1.gz /usr/share/man/it/man1/vim.1.gz --slave /usr/share/man/pl/man1/view.1.gz view.pl.1.gz /usr/share/man/pl/man1/vim.1.gz --slave /usr/share/man/ru/man1/view.1.gz view.ru.1.gz /usr/share/man/ru/man1/vim.1.gz --slave /usr/share/man/man1/view.1.gz view.1.gz /usr/share/man/man1/vim.1.gz
2009-10-28 20:55:58 update-alternatives: link group view updated to point to /usr/bin/vim.tiny
2009-10-28 20:55:58 update-alternatives: run with --install /usr/bin/ex ex /usr/bin/vim.tiny 10 --slave /usr/share/man/fr/man1/ex.1.gz ex.fr.1.gz /usr/share/man/fr/man1/vim.1.gz --slave /usr/share/man/it/man1/ex.1.gz ex.it.1.gz /usr/share/man/it/man1/vim.1.gz --slave /usr/share/man/pl/man1/ex.1.gz ex.pl.1.gz /usr/share/man/pl/man1/vim.1.gz --slave /usr/share/man/ru/man1/ex.1.gz ex.ru.1.gz /usr/share/man/ru/man1/vim.1.gz --slave /usr/share/man/man1/ex.1.gz ex.1.gz /usr/share/man/man1/vim.1.gz
2009-10-28 20:55:58 update-alternatives: link group ex updated to point to /usr/bin/vim.tiny
2009-10-28 20:55:58 update-alternatives: run with --install /usr/bin/editor editor /usr/bin/vim.tiny 10 --slave /usr/share/man/fr/man1/editor.1.gz editor.fr.1.gz /usr/share/man/fr/man1/vim.1.gz --slave /usr/share/man/it/man1/editor.1.gz editor.it.1.gz /usr/share/man/it/man1/vim.1.gz --slave /usr/share/man/pl/man1/editor.1.gz editor.pl.1.gz /usr/share/man/pl/man1/vim.1.gz --slave /usr/share/man/ru/man1/editor.1.gz editor.ru.1.gz /usr/share/man/ru/man1/vim.1.gz --slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/vim.1.gz
2009-10-28 20:55:58 update-alternatives: link group editor updated to point to /usr/bin/vim.tiny
2009-10-28 20:55:58 status installed vim-tiny 2:7.2.245-2ubuntu2
2009-10-28 20:55:58 configure less 429-2 429-2
2009-10-28 20:55:58 status unpacked less 429-2
2009-10-28 20:55:58 status half-configured less 429-2
2009-10-28 20:55:58 update-alternatives: run with --quiet --install /usr/bin/pager pager /bin/less 77 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/less.1.gz
2009-10-28 20:55:58 update-alternatives: link group pager updated to point to /bin/less
2009-10-28 20:55:58 update-alternatives: run with --quiet --install /usr/bin/pager pager /bin/less 77 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/less.1.gz
2009-10-28 20:55:58 status installed less 429-2
2009-10-28 20:55:58 configure libglib2.0-0 2.22.2-0ubuntu1 2.22.2-0ubuntu1
2009-10-28 20:55:58 status unpacked libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:58 status half-configured libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:58 status installed libglib2.0-0 2.22.2-0ubuntu1
2009-10-28 20:55:58 configure readline-common 6.0-5 6.0-5
2009-10-28 20:55:58 status unpacked readline-common 6.0-5
2009-10-28 20:55:58 status half-configured readline-common 6.0-5
2009-10-28 20:55:58 status installed readline-common 6.0-5
2009-10-28 20:55:58 configure libcap2 1:2.16-5ubuntu1 1:2.16-5ubuntu1
2009-10-28 20:55:58 status unpacked libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:58 status half-configured libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:58 status installed libcap2 1:2.16-5ubuntu1
2009-10-28 20:55:58 configure netcat 1.10-38 1.10-38
2009-10-28 20:55:58 status unpacked netcat 1.10-38
2009-10-28 20:55:58 status half-configured netcat 1.10-38
2009-10-28 20:55:58 status installed netcat 1.10-38
2009-10-28 20:55:58 configure liblockfile1 1.08-3 1.08-3
2009-10-28 20:55:58 status unpacked liblockfile1 1.08-3
2009-10-28 20:55:58 status half-configured liblockfile1 1.08-3
2009-10-28 20:55:58 status installed liblockfile1 1.08-3
2009-10-28 20:55:58 configure shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2009-10-28 20:55:58 status unpacked shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:58 status half-configured shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:59 status installed shared-mime-info 0.70-0ubuntu1
2009-10-28 20:55:59 configure laptop-detect 0.13.7ubuntu1 0.13.7ubuntu1
2009-10-28 20:55:59 status unpacked laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:59 status half-configured laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:59 status installed laptop-detect 0.13.7ubuntu1
2009-10-28 20:55:59 configure libgcrypt11 1.4.4-2ubuntu2 1.4.4-2ubuntu2
2009-10-28 20:55:59 status unpacked libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:59 status half-configured libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:59 status installed libgcrypt11 1.4.4-2ubuntu2
2009-10-28 20:55:59 configure bzip2 1.0.5-3 1.0.5-3
2009-10-28 20:55:59 status unpacked bzip2 1.0.5-3
2009-10-28 20:55:59 status half-configured bzip2 1.0.5-3
2009-10-28 20:55:59 status installed bzip2 1.0.5-3
2009-10-28 20:55:59 configure libglib2.0-data 2.22.2-0ubuntu1 2.22.2-0ubuntu1
2009-10-28 20:55:59 status unpacked libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:59 status half-configured libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:59 status installed libglib2.0-data 2.22.2-0ubuntu1
2009-10-28 20:55:59 configure libk5crypto3 1.7dfsg~beta3-1 1.7dfsg~beta3-1
2009-10-28 20:55:59 status unpacked libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:59 status half-configured libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:59 status installed libk5crypto3 1.7dfsg~beta3-1
2009-10-28 20:55:59 configure whiptail 0.52.10-4ubuntu1 0.52.10-4ubuntu1
2009-10-28 20:55:59 status unpacked whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:59 status half-configured whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:59 status installed whiptail 0.52.10-4ubuntu1
2009-10-28 20:55:59 configure ifupdown 0.6.8ubuntu21 0.6.8ubuntu21
2009-10-28 20:55:59 status unpacked ifupdown 0.6.8ubuntu21
2009-10-28 20:55:59 status half-configured ifupdown 0.6.8ubuntu21
2009-10-28 20:55:59 status installed ifupdown 0.6.8ubuntu21
2009-10-28 20:55:59 configure dhcp3-client 3.1.2-1ubuntu7 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status unpacked dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status half-configured dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 status installed dhcp3-client 3.1.2-1ubuntu7
2009-10-28 20:55:59 configure libreadline6 6.0-5 6.0-5
2009-10-28 20:55:59 status unpacked libreadline6 6.0-5
2009-10-28 20:55:59 status half-configured libreadline6 6.0-5
2009-10-28 20:55:59 status installed libreadline6 6.0-5
2009-10-28 20:55:59 configure lockfile-progs 0.1.13 0.1.13
2009-10-28 20:55:59 status unpacked lockfile-progs 0.1.13
2009-10-28 20:55:59 status half-configured lockfile-progs 0.1.13
2009-10-28 20:55:59 status installed lockfile-progs 0.1.13
2009-10-28 20:55:59 configure libcwidget3 0.5.12-4ubuntu4 0.5.12-4ubuntu4
2009-10-28 20:55:59 status unpacked libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:55:59 status half-configured libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:55:59 status installed libcwidget3 0.5.12-4ubuntu4
2009-10-28 20:56:00 configure libgnutls26 2.8.3-2 2.8.3-2
2009-10-28 20:56:00 status unpacked libgnutls26 2.8.3-2
2009-10-28 20:56:00 status half-configured libgnutls26 2.8.3-2
2009-10-28 20:56:00 status installed libgnutls26 2.8.3-2
2009-10-28 20:56:00 configure aptitude 0.4.11.11-1ubuntu6 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status unpacked aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status half-configured aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 status installed aptitude 0.4.11.11-1ubuntu6
2009-10-28 20:56:00 configure ntpdate 1:4.2.4p6+dfsg-1ubuntu5 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status unpacked ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status half-configured ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 status installed ntpdate 1:4.2.4p6+dfsg-1ubuntu5
2009-10-28 20:56:00 configure libkrb5-3 1.7dfsg~beta3-1 1.7dfsg~beta3-1
2009-10-28 20:56:00 status unpacked libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:56:00 status half-configured libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:56:00 status installed libkrb5-3 1.7dfsg~beta3-1
2009-10-28 20:56:00 configure gpgv 1.4.9-4ubuntu7 1.4.9-4ubuntu7
2009-10-28 20:56:00 status unpacked gpgv 1.4.9-4ubuntu7
2009-10-28 20:56:00 status half-configured gpgv 1.4.9-4ubuntu7
2009-10-28 20:56:00 status installed gpgv 1.4.9-4ubuntu7
2009-10-28 20:56:00 configure libgssapi-krb5-2 1.7dfsg~beta3-1 1.7dfsg~beta3-1
2009-10-28 20:56:00 status unpacked libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:56:00 status half-configured libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:56:00 status installed libgssapi-krb5-2 1.7dfsg~beta3-1
2009-10-28 20:56:00 configure python2.6 2.6.4~rc2-0ubuntu1 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:00 status unpacked python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:00 status half-configured python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:02 status installed python2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:02 configure python 2.6.4~rc1-0ubuntu1 2.6.4~rc1-0ubuntu1
2009-10-28 20:56:02 status unpacked python 2.6.4~rc1-0ubuntu1
2009-10-28 20:56:02 status half-configured python 2.6.4~rc1-0ubuntu1
2009-10-28 20:56:02 status installed python 2.6.4~rc1-0ubuntu1
2009-10-28 20:56:02 configure python-central 0.6.11ubuntu9 0.6.11ubuntu9
2009-10-28 20:56:02 status unpacked python-central 0.6.11ubuntu9
2009-10-28 20:56:02 status half-configured python-central 0.6.11ubuntu9
2009-10-28 20:56:02 status installed python-central 0.6.11ubuntu9
2009-10-28 20:56:02 configure lsb-release 4.0-0ubuntu5 4.0-0ubuntu5
2009-10-28 20:56:02 status unpacked lsb-release 4.0-0ubuntu5
2009-10-28 20:56:02 status half-configured lsb-release 4.0-0ubuntu5
2009-10-28 20:56:02 status installed lsb-release 4.0-0ubuntu5
2009-10-28 20:56:02 configure udev 147~-6 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status unpacked udev 147~-6
2009-10-28 20:56:02 status half-configured udev 147~-6
2009-10-28 20:56:02 status installed udev 147~-6
2009-10-28 20:56:02 configure initramfs-tools 0.92bubuntu53 0.92bubuntu53
2009-10-28 20:56:02 status unpacked initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 status unpacked initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 status unpacked initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 status half-configured initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 status installed initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 status triggers-pending initramfs-tools 0.92bubuntu53
2009-10-28 20:56:02 configure perl-modules 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 20:56:02 status unpacked perl-modules 5.10.0-24ubuntu4
2009-10-28 20:56:02 status unpacked perl-modules 5.10.0-24ubuntu4
2009-10-28 20:56:02 status half-configured perl-modules 5.10.0-24ubuntu4
2009-10-28 20:56:02 status installed perl-modules 5.10.0-24ubuntu4
2009-10-28 20:56:02 configure console-setup 1.34ubuntu4 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:02 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status unpacked console-setup 1.34ubuntu4
2009-10-28 20:56:03 status half-configured console-setup 1.34ubuntu4
2009-10-28 20:56:06 status installed console-setup 1.34ubuntu4
2009-10-28 20:56:06 configure tasksel-data 2.73ubuntu23 2.73ubuntu23
2009-10-28 20:56:06 status unpacked tasksel-data 2.73ubuntu23
2009-10-28 20:56:06 status half-configured tasksel-data 2.73ubuntu23
2009-10-28 20:56:06 status installed tasksel-data 2.73ubuntu23
2009-10-28 20:56:06 configure kbd 1.15-1ubuntu1 1.15-1ubuntu1
2009-10-28 20:56:06 status unpacked kbd 1.15-1ubuntu1
2009-10-28 20:56:06 status unpacked kbd 1.15-1ubuntu1
2009-10-28 20:56:06 status unpacked kbd 1.15-1ubuntu1
2009-10-28 20:56:06 status half-configured kbd 1.15-1ubuntu1
2009-10-28 20:56:06 status installed kbd 1.15-1ubuntu1
2009-10-28 20:56:06 configure libsasl2-modules 2.1.23.dfsg1-1ubuntu3 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status unpacked libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status half-configured libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status installed libsasl2-modules 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 configure libsasl2-2 2.1.23.dfsg1-1ubuntu3 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status unpacked libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status half-configured libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 status installed libsasl2-2 2.1.23.dfsg1-1ubuntu3
2009-10-28 20:56:06 configure dmsetup 2:1.02.27-4ubuntu7 2:1.02.27-4ubuntu7
2009-10-28 20:56:06 status unpacked dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:56:06 status half-configured dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:56:06 status installed dmsetup 2:1.02.27-4ubuntu7
2009-10-28 20:56:06 configure perl 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 20:56:06 status unpacked perl 5.10.0-24ubuntu4
2009-10-28 20:56:06 status half-configured perl 5.10.0-24ubuntu4
2009-10-28 20:56:06 update-alternatives: run with --install /usr/bin/rename rename /usr/bin/prename 60 --slave /usr/share/man/man1/rename.1.gz rename.1.gz /usr/share/man/man1/prename.1.gz
2009-10-28 20:56:06 update-alternatives: link group rename updated to point to /usr/bin/prename
2009-10-28 20:56:06 status installed perl 5.10.0-24ubuntu4
2009-10-28 20:56:06 configure libsub-name-perl 0.04-1 0.04-1
2009-10-28 20:56:06 status unpacked libsub-name-perl 0.04-1
2009-10-28 20:56:06 status half-configured libsub-name-perl 0.04-1
2009-10-28 20:56:06 status installed libsub-name-perl 0.04-1
2009-10-28 20:56:06 configure libldap-2.4-2 2.4.18-0ubuntu1 2.4.18-0ubuntu1
2009-10-28 20:56:06 status unpacked libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:56:06 status unpacked libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:56:06 status half-configured libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:56:06 status installed libldap-2.4-2 2.4.18-0ubuntu1
2009-10-28 20:56:06 configure libio-string-perl 1.08-2 1.08-2
2009-10-28 20:56:06 status unpacked libio-string-perl 1.08-2
2009-10-28 20:56:06 status half-configured libio-string-perl 1.08-2
2009-10-28 20:56:06 status installed libio-string-perl 1.08-2
2009-10-28 20:56:06 configure libclass-accessor-perl 0.33-1 0.33-1
2009-10-28 20:56:06 status unpacked libclass-accessor-perl 0.33-1
2009-10-28 20:56:06 status half-configured libclass-accessor-perl 0.33-1
2009-10-28 20:56:06 status installed libclass-accessor-perl 0.33-1
2009-10-28 20:56:06 configure libcurl3-gnutls 7.19.5-1ubuntu2 7.19.5-1ubuntu2
2009-10-28 20:56:06 status unpacked libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:56:06 status half-configured libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:56:06 status installed libcurl3-gnutls 7.19.5-1ubuntu2
2009-10-28 20:56:06 configure libtimedate-perl 1.1600-9 1.1600-9
2009-10-28 20:56:06 status unpacked libtimedate-perl 1.1600-9
2009-10-28 20:56:06 status half-configured libtimedate-perl 1.1600-9
2009-10-28 20:56:06 status installed libtimedate-perl 1.1600-9
2009-10-28 20:56:06 configure sgml-base 1.26 1.26
2009-10-28 20:56:06 status unpacked sgml-base 1.26
2009-10-28 20:56:06 status half-configured sgml-base 1.26
2009-10-28 20:56:06 status installed sgml-base 1.26
2009-10-28 20:56:06 configure tasksel 2.73ubuntu23 2.73ubuntu23
2009-10-28 20:56:06 status unpacked tasksel 2.73ubuntu23
2009-10-28 20:56:06 status half-configured tasksel 2.73ubuntu23
2009-10-28 20:56:06 status installed tasksel 2.73ubuntu23
2009-10-28 20:56:06 configure gnupg 1.4.9-4ubuntu7 1.4.9-4ubuntu7
2009-10-28 20:56:06 status unpacked gnupg 1.4.9-4ubuntu7
2009-10-28 20:56:06 status half-configured gnupg 1.4.9-4ubuntu7
2009-10-28 20:56:06 status installed gnupg 1.4.9-4ubuntu7
2009-10-28 20:56:06 configure ubuntu-keyring 2009.08.28 2009.08.28
2009-10-28 20:56:06 status unpacked ubuntu-keyring 2009.08.28
2009-10-28 20:56:06 status half-configured ubuntu-keyring 2009.08.28
2009-10-28 20:56:06 status installed ubuntu-keyring 2009.08.28
2009-10-28 20:56:06 configure xml-core 0.12 0.12
2009-10-28 20:56:06 status unpacked xml-core 0.12
2009-10-28 20:56:06 status half-configured xml-core 0.12
2009-10-28 20:56:07 status installed xml-core 0.12
2009-10-28 20:56:07 configure libparse-debianchangelog-perl 1.1.1-2ubuntu1 1.1.1-2ubuntu1
2009-10-28 20:56:07 status unpacked libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:56:07 status half-configured libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:56:07 status installed libparse-debianchangelog-perl 1.1.1-2ubuntu1
2009-10-28 20:56:07 configure ubuntu-minimal 1.175 1.175
2009-10-28 20:56:07 status unpacked ubuntu-minimal 1.175
2009-10-28 20:56:07 status half-configured ubuntu-minimal 1.175
2009-10-28 20:56:07 status installed ubuntu-minimal 1.175
2009-10-28 20:56:07 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:56:07 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 20:56:07 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:56:07 trigproc initramfs-tools 0.92bubuntu53 0.92bubuntu53
2009-10-28 20:56:07 status half-configured initramfs-tools 0.92bubuntu53
2009-10-28 20:56:07 status installed initramfs-tools 0.92bubuntu53
2009-10-28 20:56:44 startup archives unpack
2009-10-28 20:56:44 install libfuse2 <none> 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status half-installed libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 install fuse-utils <none> 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status half-installed fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 install libntfs-3g54 <none> 1:2009.4.4-1ubuntu4
2009-10-28 20:56:44 status half-installed libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 20:56:44 status unpacked libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 20:56:44 status unpacked libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 20:56:44 startup packages configure
2009-10-28 20:56:44 configure libfuse2 2.7.4-1.1ubuntu4 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status half-configured libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status installed libfuse2 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 20:56:44 configure fuse-utils 2.7.4-1.1ubuntu4 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status unpacked fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status half-configured fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status installed fuse-utils 2.7.4-1.1ubuntu4
2009-10-28 20:56:44 status triggers-pending initramfs-tools 0.92bubuntu53
2009-10-28 20:56:44 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:56:44 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 20:56:44 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:56:44 trigproc initramfs-tools 0.92bubuntu53 0.92bubuntu53
2009-10-28 20:56:44 status half-configured initramfs-tools 0.92bubuntu53
2009-10-28 20:56:44 status installed initramfs-tools 0.92bubuntu53
2009-10-28 20:56:44 startup archives unpack
2009-10-28 20:56:44 install ntfs-3g <none> 1:2009.4.4-1ubuntu4
2009-10-28 20:56:44 status half-installed ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 20:56:45 status unpacked ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 20:56:45 status unpacked ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 20:56:45 install x11-common <none> 1:7.4+3ubuntu7
2009-10-28 20:56:45 status half-installed x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:45 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:45 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:45 install libxau6 <none> 1:1.0.4-2
2009-10-28 20:56:45 status half-installed libxau6 1:1.0.4-2
2009-10-28 20:56:45 status unpacked libxau6 1:1.0.4-2
2009-10-28 20:56:45 status unpacked libxau6 1:1.0.4-2
2009-10-28 20:56:45 install libxdmcp6 <none> 1:1.0.2-3
2009-10-28 20:56:45 status half-installed libxdmcp6 1:1.0.2-3
2009-10-28 20:56:45 status unpacked libxdmcp6 1:1.0.2-3
2009-10-28 20:56:45 status unpacked libxdmcp6 1:1.0.2-3
2009-10-28 20:56:45 install libxcb1 <none> 1.4-1
2009-10-28 20:56:45 status half-installed libxcb1 1.4-1
2009-10-28 20:56:45 status unpacked libxcb1 1.4-1
2009-10-28 20:56:45 status unpacked libxcb1 1.4-1
2009-10-28 20:56:45 install libx11-data <none> 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status half-installed libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status unpacked libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status unpacked libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 install libx11-6 <none> 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status half-installed libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status unpacked libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 status unpacked libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:56:45 install libxext6 <none> 2:1.0.99.1-0ubuntu4
2009-10-28 20:56:45 status half-installed libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:56:45 status unpacked libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:56:45 status unpacked libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:56:46 install libxmuu1 <none> 2:1.0.4-2
2009-10-28 20:56:46 status half-installed libxmuu1 2:1.0.4-2
2009-10-28 20:56:46 status unpacked libxmuu1 2:1.0.4-2
2009-10-28 20:56:46 status unpacked libxmuu1 2:1.0.4-2
2009-10-28 20:56:46 startup packages configure
2009-10-28 20:56:46 configure x11-common 1:7.4+3ubuntu7 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status unpacked x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status half-configured x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 status installed x11-common 1:7.4+3ubuntu7
2009-10-28 20:56:46 startup archives unpack
2009-10-28 20:56:46 install xauth <none> 1:1.0.3-2
2009-10-28 20:56:46 status half-installed xauth 1:1.0.3-2
2009-10-28 20:56:46 status unpacked xauth 1:1.0.3-2
2009-10-28 20:56:46 status unpacked xauth 1:1.0.3-2
2009-10-28 20:56:46 install sgml-data <none> 2.0.3
2009-10-28 20:56:46 status half-installed sgml-data 2.0.3
2009-10-28 20:56:47 status unpacked sgml-data 2.0.3
2009-10-28 20:56:47 status unpacked sgml-data 2.0.3
2009-10-28 20:56:47 install docbook-xml <none> 4.5-6
2009-10-28 20:56:47 status half-installed docbook-xml 4.5-6
2009-10-28 20:56:47 status unpacked docbook-xml 4.5-6
2009-10-28 20:56:47 status unpacked docbook-xml 4.5-6
2009-10-28 20:56:47 install libavahi-common-data <none> 0.6.25-1ubuntu5
2009-10-28 20:56:47 status half-installed libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:56:47 install libavahi-common3 <none> 0.6.25-1ubuntu5
2009-10-28 20:56:47 status half-installed libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:56:47 install libavahi-client3 <none> 0.6.25-1ubuntu5
2009-10-28 20:56:47 status half-installed libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:56:47 status unpacked libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:56:47 install libcups2 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:47 status half-installed libcups2 1.4.1-5ubuntu2
2009-10-28 20:56:47 status unpacked libcups2 1.4.1-5ubuntu2
2009-10-28 20:56:47 status unpacked libcups2 1.4.1-5ubuntu2
2009-10-28 20:56:47 install libjpeg62 <none> 6b-14build1
2009-10-28 20:56:47 status half-installed libjpeg62 6b-14build1
2009-10-28 20:56:47 status unpacked libjpeg62 6b-14build1
2009-10-28 20:56:47 status unpacked libjpeg62 6b-14build1
2009-10-28 20:56:47 install libpng12-0 <none> 1.2.37-1
2009-10-28 20:56:47 status half-installed libpng12-0 1.2.37-1
2009-10-28 20:56:47 status unpacked libpng12-0 1.2.37-1
2009-10-28 20:56:47 status unpacked libpng12-0 1.2.37-1
2009-10-28 20:56:47 install libtiff4 <none> 3.8.2-13
2009-10-28 20:56:47 status half-installed libtiff4 3.8.2-13
2009-10-28 20:56:47 status unpacked libtiff4 3.8.2-13
2009-10-28 20:56:47 status unpacked libtiff4 3.8.2-13
2009-10-28 20:56:47 install libcupsimage2 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:47 status half-installed libcupsimage2 1.4.1-5ubuntu2
2009-10-28 20:56:47 status unpacked libcupsimage2 1.4.1-5ubuntu2
2009-10-28 20:56:47 status unpacked libcupsimage2 1.4.1-5ubuntu2
2009-10-28 20:56:47 install libexpat1 <none> 2.0.1-4ubuntu1
2009-10-28 20:56:47 status half-installed libexpat1 2.0.1-4ubuntu1
2009-10-28 20:56:47 status unpacked libexpat1 2.0.1-4ubuntu1
2009-10-28 20:56:47 status unpacked libexpat1 2.0.1-4ubuntu1
2009-10-28 20:56:47 install libfreetype6 <none> 2.3.9-5
2009-10-28 20:56:47 status half-installed libfreetype6 2.3.9-5
2009-10-28 20:56:47 status unpacked libfreetype6 2.3.9-5
2009-10-28 20:56:47 status unpacked libfreetype6 2.3.9-5
2009-10-28 20:56:48 install defoma <none> 0.11.10-0.2ubuntu1
2009-10-28 20:56:48 status half-installed defoma 0.11.10-0.2ubuntu1
2009-10-28 20:56:48 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:56:48 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:56:48 install ttf-freefont <none> 20090104-2
2009-10-28 20:56:48 status half-installed ttf-freefont 20090104-2
2009-10-28 20:56:48 status unpacked ttf-freefont 20090104-2
2009-10-28 20:56:48 status unpacked ttf-freefont 20090104-2
2009-10-28 20:56:48 install fontconfig-config <none> 2.6.0-1ubuntu12
2009-10-28 20:56:48 status half-installed fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:56:48 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:56:48 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:56:48 install libfontconfig1 <none> 2.6.0-1ubuntu12
2009-10-28 20:56:48 status half-installed libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:56:48 status unpacked libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:56:48 status unpacked libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:56:48 install libpaper1 <none> 1.1.23+nmu1
2009-10-28 20:56:48 status half-installed libpaper1 1.1.23+nmu1
2009-10-28 20:56:48 status unpacked libpaper1 1.1.23+nmu1
2009-10-28 20:56:48 status unpacked libpaper1 1.1.23+nmu1
2009-10-28 20:56:48 install libgs8 <none> 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:48 status half-installed libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:49 status unpacked libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:49 status unpacked libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:49 install foomatic-filters <none> 4.0.3-0ubuntu2
2009-10-28 20:56:49 status half-installed foomatic-filters 4.0.3-0ubuntu2
2009-10-28 20:56:49 status unpacked foomatic-filters 4.0.3-0ubuntu2
2009-10-28 20:56:49 status unpacked foomatic-filters 4.0.3-0ubuntu2
2009-10-28 20:56:49 install gsfonts <none> 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 20:56:49 status half-installed gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 20:56:49 status unpacked gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 20:56:49 status unpacked gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 20:56:49 install ghostscript <none> 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:49 status half-installed ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:50 status unpacked ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:50 status unpacked ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 20:56:50 install libcupscgi1 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:50 status half-installed libcupscgi1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupscgi1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupscgi1 1.4.1-5ubuntu2
2009-10-28 20:56:50 install libcupsdriver1 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:50 status half-installed libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 20:56:50 install libcupsmime1 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:50 status half-installed libcupsmime1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsmime1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsmime1 1.4.1-5ubuntu2
2009-10-28 20:56:50 install libcupsppdc1 <none> 1.4.1-5ubuntu2
2009-10-28 20:56:50 status half-installed libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 20:56:50 status unpacked libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 20:56:50 install libijs-0.35 <none> 0.35-7
2009-10-28 20:56:50 status half-installed libijs-0.35 0.35-7
2009-10-28 20:56:50 status unpacked libijs-0.35 0.35-7
2009-10-28 20:56:50 status unpacked libijs-0.35 0.35-7
2009-10-28 20:56:50 install liblcms1 <none> 1.18.dfsg-1ubuntu1
2009-10-28 20:56:50 status half-installed liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 20:56:50 status unpacked liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 20:56:50 status unpacked liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 20:56:50 install libpoppler5 <none> 0.12.0-0ubuntu2
2009-10-28 20:56:50 status half-installed libpoppler5 0.12.0-0ubuntu2
2009-10-28 20:56:50 status unpacked libpoppler5 0.12.0-0ubuntu2
2009-10-28 20:56:50 status unpacked libpoppler5 0.12.0-0ubuntu2
2009-10-28 20:56:50 install libslp1 <none> 1.2.1-7.5
2009-10-28 20:56:50 status half-installed libslp1 1.2.1-7.5
2009-10-28 20:56:50 status unpacked libslp1 1.2.1-7.5
2009-10-28 20:56:50 status unpacked libslp1 1.2.1-7.5
2009-10-28 20:56:50 install poppler-utils <none> 0.12.0-0ubuntu2
2009-10-28 20:56:50 status half-installed poppler-utils 0.12.0-0ubuntu2
2009-10-28 20:56:50 status unpacked poppler-utils 0.12.0-0ubuntu2
2009-10-28 20:56:50 status unpacked poppler-utils 0.12.0-0ubuntu2
2009-10-28 20:56:50 install cups-common <none> 1.4.1-5ubuntu2
2009-10-28 20:56:50 status half-installed cups-common 1.4.1-5ubuntu2
2009-10-28 20:56:51 status unpacked cups-common 1.4.1-5ubuntu2
2009-10-28 20:56:51 status unpacked cups-common 1.4.1-5ubuntu2
2009-10-28 20:56:51 install cups-client <none> 1.4.1-5ubuntu2
2009-10-28 20:56:51 status half-installed cups-client 1.4.1-5ubuntu2
2009-10-28 20:56:51 status unpacked cups-client 1.4.1-5ubuntu2
2009-10-28 20:56:51 status unpacked cups-client 1.4.1-5ubuntu2
2009-10-28 20:56:51 install ssl-cert <none> 1.0.23ubuntu2
2009-10-28 20:56:51 status half-installed ssl-cert 1.0.23ubuntu2
2009-10-28 20:56:51 status unpacked ssl-cert 1.0.23ubuntu2
2009-10-28 20:56:51 status unpacked ssl-cert 1.0.23ubuntu2
2009-10-28 20:56:51 install bc <none> 1.06.94-3.1ubuntu2
2009-10-28 20:56:51 status half-installed bc 1.06.94-3.1ubuntu2
2009-10-28 20:56:51 status unpacked bc 1.06.94-3.1ubuntu2
2009-10-28 20:56:51 status unpacked bc 1.06.94-3.1ubuntu2
2009-10-28 20:56:51 install cups <none> 1.4.1-5ubuntu2
2009-10-28 20:56:51 status half-installed cups 1.4.1-5ubuntu2
2009-10-28 20:56:52 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 20:56:52 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 20:56:52 install foomatic-db <none> 20090825-0ubuntu4
2009-10-28 20:56:52 status half-installed foomatic-db 20090825-0ubuntu4
2009-10-28 20:56:54 status unpacked foomatic-db 20090825-0ubuntu4
2009-10-28 20:56:54 status unpacked foomatic-db 20090825-0ubuntu4
2009-10-28 20:56:54 install wget <none> 1.11.4-2ubuntu2
2009-10-28 20:56:54 status half-installed wget 1.11.4-2ubuntu2
2009-10-28 20:56:54 status unpacked wget 1.11.4-2ubuntu2
2009-10-28 20:56:54 status unpacked wget 1.11.4-2ubuntu2
2009-10-28 20:56:54 install foomatic-db-engine <none> 4.0.3-0ubuntu2
2009-10-28 20:56:54 status half-installed foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 20:56:54 status unpacked foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 20:56:54 status unpacked foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 20:56:54 install libatk1.0-0 <none> 1.28.0-0ubuntu1
2009-10-28 20:56:54 status half-installed libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:56:54 status unpacked libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:56:54 status unpacked libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:56:54 install libbonobo2-common <none> 2.24.2-1
2009-10-28 20:56:54 status half-installed libbonobo2-common 2.24.2-1
2009-10-28 20:56:54 status unpacked libbonobo2-common 2.24.2-1
2009-10-28 20:56:54 status unpacked libbonobo2-common 2.24.2-1
2009-10-28 20:56:54 install libdbus-glib-1-2 <none> 0.80-4ubuntu1
2009-10-28 20:56:54 status half-installed libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 20:56:54 status unpacked libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 20:56:54 status unpacked libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 20:56:54 install libgmp3c2 <none> 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:56:54 status half-installed libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:56:54 status unpacked libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:56:54 status unpacked libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:56:54 install libmpfr1ldbl <none> 2.4.1-1ubuntu1
2009-10-28 20:56:54 status half-installed libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 20:56:54 status unpacked libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 20:56:55 status unpacked libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 20:56:55 install cpp-4.4 <none> 4.4.1-4ubuntu8
2009-10-28 20:56:55 status half-installed cpp-4.4 4.4.1-4ubuntu8
2009-10-28 20:56:55 status unpacked cpp-4.4 4.4.1-4ubuntu8
2009-10-28 20:56:55 status unpacked cpp-4.4 4.4.1-4ubuntu8
2009-10-28 20:56:55 install cpp <none> 4:4.4.1-1ubuntu2
2009-10-28 20:56:55 status half-installed cpp 4:4.4.1-1ubuntu2
2009-10-28 20:56:55 status unpacked cpp 4:4.4.1-1ubuntu2
2009-10-28 20:56:55 status unpacked cpp 4:4.4.1-1ubuntu2
2009-10-28 20:56:55 install libidl0 <none> 0.8.13-0.1
2009-10-28 20:56:55 status half-installed libidl0 0.8.13-0.1
2009-10-28 20:56:55 status unpacked libidl0 0.8.13-0.1
2009-10-28 20:56:55 status unpacked libidl0 0.8.13-0.1
2009-10-28 20:56:55 install liborbit2 <none> 1:2.14.17-0.1
2009-10-28 20:56:55 status half-installed liborbit2 1:2.14.17-0.1
2009-10-28 20:56:55 status unpacked liborbit2 1:2.14.17-0.1
2009-10-28 20:56:55 status unpacked liborbit2 1:2.14.17-0.1
2009-10-28 20:56:55 install libbonobo2-0 <none> 2.24.2-1
2009-10-28 20:56:55 status half-installed libbonobo2-0 2.24.2-1
2009-10-28 20:56:55 status unpacked libbonobo2-0 2.24.2-1
2009-10-28 20:56:56 status unpacked libbonobo2-0 2.24.2-1
2009-10-28 20:56:56 install libart-2.0-2 <none> 2.3.20-2
2009-10-28 20:56:56 status half-installed libart-2.0-2 2.3.20-2
2009-10-28 20:56:56 status unpacked libart-2.0-2 2.3.20-2
2009-10-28 20:56:56 status unpacked libart-2.0-2 2.3.20-2
2009-10-28 20:56:56 install libsysfs2 <none> 2.1.0-5
2009-10-28 20:56:56 status half-installed libsysfs2 2.1.0-5
2009-10-28 20:56:56 status unpacked libsysfs2 2.1.0-5
2009-10-28 20:56:56 status unpacked libsysfs2 2.1.0-5
2009-10-28 20:56:56 install tsconf <none> 1.0-7
2009-10-28 20:56:56 status half-installed tsconf 1.0-7
2009-10-28 20:56:56 status unpacked tsconf 1.0-7
2009-10-28 20:56:56 status unpacked tsconf 1.0-7
2009-10-28 20:56:56 install libts-0.0-0 <none> 1.0-7
2009-10-28 20:56:56 status half-installed libts-0.0-0 1.0-7
2009-10-28 20:56:56 status unpacked libts-0.0-0 1.0-7
2009-10-28 20:56:56 status unpacked libts-0.0-0 1.0-7
2009-10-28 20:56:56 install libdirectfb-1.2-0 <none> 1.2.7-2ubuntu1
2009-10-28 20:56:56 status half-installed libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:56:56 status unpacked libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:56:56 status unpacked libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:56:56 install libpixman-1-0 <none> 0.14.0-1
2009-10-28 20:56:56 status half-installed libpixman-1-0 0.14.0-1
2009-10-28 20:56:56 status unpacked libpixman-1-0 0.14.0-1
2009-10-28 20:56:56 status unpacked libpixman-1-0 0.14.0-1
2009-10-28 20:56:56 install libxcb-render0 <none> 1.4-1
2009-10-28 20:56:56 status half-installed libxcb-render0 1.4-1
2009-10-28 20:56:56 status unpacked libxcb-render0 1.4-1
2009-10-28 20:56:56 status unpacked libxcb-render0 1.4-1
2009-10-28 20:56:56 install libxcb-render-util0 <none> 0.3.6-1
2009-10-28 20:56:56 status half-installed libxcb-render-util0 0.3.6-1
2009-10-28 20:56:56 status unpacked libxcb-render-util0 0.3.6-1
2009-10-28 20:56:56 status unpacked libxcb-render-util0 0.3.6-1
2009-10-28 20:56:56 install libxrender1 <none> 1:0.9.4-2ubuntu1
2009-10-28 20:56:56 status half-installed libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:56:57 status unpacked libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:56:57 status unpacked libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:56:57 install libcairo2 <none> 1.8.8-2ubuntu1
2009-10-28 20:56:57 status half-installed libcairo2 1.8.8-2ubuntu1
2009-10-28 20:56:57 status unpacked libcairo2 1.8.8-2ubuntu1
2009-10-28 20:56:57 status unpacked libcairo2 1.8.8-2ubuntu1
2009-10-28 20:56:57 install dbus <none> 1.2.16-0ubuntu9
2009-10-28 20:56:57 status half-installed dbus 1.2.16-0ubuntu9
2009-10-28 20:56:57 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 20:56:57 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 20:56:57 install gconf2-common <none> 2.28.0-0ubuntu2
2009-10-28 20:56:57 status half-installed gconf2-common 2.28.0-0ubuntu2
2009-10-28 20:56:57 status unpacked gconf2-common 2.28.0-0ubuntu2
2009-10-28 20:56:57 status unpacked gconf2-common 2.28.0-0ubuntu2
2009-10-28 20:56:57 install libgconf2-4 <none> 2.28.0-0ubuntu2
2009-10-28 20:56:57 status half-installed libgconf2-4 2.28.0-0ubuntu2
2009-10-28 20:56:57 status unpacked libgconf2-4 2.28.0-0ubuntu2
2009-10-28 20:56:57 status unpacked libgconf2-4 2.28.0-0ubuntu2
2009-10-28 20:56:57 install libgtk2.0-common <none> 2.18.3-1
2009-10-28 20:56:57 status half-installed libgtk2.0-common 2.18.3-1
2009-10-28 20:56:57 status unpacked libgtk2.0-common 2.18.3-1
2009-10-28 20:56:57 status unpacked libgtk2.0-common 2.18.3-1
2009-10-28 20:56:57 install libjasper1 <none> 1.900.1-6
2009-10-28 20:56:57 status half-installed libjasper1 1.900.1-6
2009-10-28 20:56:57 status unpacked libjasper1 1.900.1-6
2009-10-28 20:56:57 status unpacked libjasper1 1.900.1-6
2009-10-28 20:56:57 install fontconfig <none> 2.6.0-1ubuntu12
2009-10-28 20:56:57 status half-installed fontconfig 2.6.0-1ubuntu12
2009-10-28 20:56:57 status unpacked fontconfig 2.6.0-1ubuntu12
2009-10-28 20:56:57 status unpacked fontconfig 2.6.0-1ubuntu12
2009-10-28 20:56:57 install libpango1.0-common <none> 1.26.0-1
2009-10-28 20:56:57 status half-installed libpango1.0-common 1.26.0-1
2009-10-28 20:56:57 status unpacked libpango1.0-common 1.26.0-1
2009-10-28 20:56:57 status unpacked libpango1.0-common 1.26.0-1
2009-10-28 20:56:57 install libdatrie1 <none> 0.2.2-1
2009-10-28 20:56:57 status half-installed libdatrie1 0.2.2-1
2009-10-28 20:56:57 status unpacked libdatrie1 0.2.2-1
2009-10-28 20:56:57 status unpacked libdatrie1 0.2.2-1
2009-10-28 20:56:57 install libthai-data <none> 0.1.12-1
2009-10-28 20:56:57 status half-installed libthai-data 0.1.12-1
2009-10-28 20:56:57 status unpacked libthai-data 0.1.12-1
2009-10-28 20:56:57 status unpacked libthai-data 0.1.12-1
2009-10-28 20:56:57 install libthai0 <none> 0.1.12-1
2009-10-28 20:56:57 status half-installed libthai0 0.1.12-1
2009-10-28 20:56:57 status unpacked libthai0 0.1.12-1
2009-10-28 20:56:57 status unpacked libthai0 0.1.12-1
2009-10-28 20:56:57 install libxft2 <none> 2.1.13-3ubuntu1
2009-10-28 20:56:57 status half-installed libxft2 2.1.13-3ubuntu1
2009-10-28 20:56:58 status unpacked libxft2 2.1.13-3ubuntu1
2009-10-28 20:56:58 status unpacked libxft2 2.1.13-3ubuntu1
2009-10-28 20:56:58 install libpango1.0-0 <none> 1.26.0-1
2009-10-28 20:56:58 status half-installed libpango1.0-0 1.26.0-1
2009-10-28 20:56:58 status unpacked libpango1.0-0 1.26.0-1
2009-10-28 20:56:58 status unpacked libpango1.0-0 1.26.0-1
2009-10-28 20:56:58 install libxfixes3 <none> 1:4.0.3-2build1
2009-10-28 20:56:58 status half-installed libxfixes3 1:4.0.3-2build1
2009-10-28 20:56:58 status unpacked libxfixes3 1:4.0.3-2build1
2009-10-28 20:56:58 status unpacked libxfixes3 1:4.0.3-2build1
2009-10-28 20:56:58 install libxcomposite1 <none> 1:0.4.0-4
2009-10-28 20:56:58 status half-installed libxcomposite1 1:0.4.0-4
2009-10-28 20:56:58 status unpacked libxcomposite1 1:0.4.0-4
2009-10-28 20:56:58 status unpacked libxcomposite1 1:0.4.0-4
2009-10-28 20:56:58 install libxcursor1 <none> 1:1.1.9-1build1
2009-10-28 20:56:58 status half-installed libxcursor1 1:1.1.9-1build1
2009-10-28 20:56:58 status unpacked libxcursor1 1:1.1.9-1build1
2009-10-28 20:56:58 status unpacked libxcursor1 1:1.1.9-1build1
2009-10-28 20:56:58 install libxdamage1 <none> 1:1.1.1-4
2009-10-28 20:56:58 status half-installed libxdamage1 1:1.1.1-4
2009-10-28 20:56:58 status unpacked libxdamage1 1:1.1.1-4
2009-10-28 20:56:58 status unpacked libxdamage1 1:1.1.1-4
2009-10-28 20:56:58 install libxi6 <none> 2:1.2.1-2ubuntu1
2009-10-28 20:56:58 status half-installed libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:56:58 status unpacked libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:56:58 status unpacked libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:56:58 install libxinerama1 <none> 2:1.0.3-2
2009-10-28 20:56:58 status half-installed libxinerama1 2:1.0.3-2
2009-10-28 20:56:58 status unpacked libxinerama1 2:1.0.3-2
2009-10-28 20:56:58 status unpacked libxinerama1 2:1.0.3-2
2009-10-28 20:56:58 install libxrandr2 <none> 2:1.3.0-2
2009-10-28 20:56:58 status half-installed libxrandr2 2:1.3.0-2
2009-10-28 20:56:58 status unpacked libxrandr2 2:1.3.0-2
2009-10-28 20:56:58 status unpacked libxrandr2 2:1.3.0-2
2009-10-28 20:56:58 install libgtk2.0-0 <none> 2.18.3-1
2009-10-28 20:56:58 status half-installed libgtk2.0-0 2.18.3-1
2009-10-28 20:56:58 status unpacked libgtk2.0-0 2.18.3-1
2009-10-28 20:56:58 status unpacked libgtk2.0-0 2.18.3-1
2009-10-28 20:56:58 install libglade2-0 <none> 1:2.6.4-1
2009-10-28 20:56:58 status half-installed libglade2-0 1:2.6.4-1
2009-10-28 20:56:58 status unpacked libglade2-0 1:2.6.4-1
2009-10-28 20:56:58 status unpacked libglade2-0 1:2.6.4-1
2009-10-28 20:56:59 install libaudiofile0 <none> 0.2.6-7ubuntu2
2009-10-28 20:56:59 status half-installed libaudiofile0 0.2.6-7ubuntu2
2009-10-28 20:56:59 status unpacked libaudiofile0 0.2.6-7ubuntu2
2009-10-28 20:56:59 status unpacked libaudiofile0 0.2.6-7ubuntu2
2009-10-28 20:56:59 install libpython2.6 <none> 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:59 status half-installed libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:59 status unpacked libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:59 status unpacked libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:56:59 install libasound2 <none> 1.0.20-3ubuntu6
2009-10-28 20:56:59 status half-installed libasound2 1.0.20-3ubuntu6
2009-10-28 20:56:59 status unpacked libasound2 1.0.20-3ubuntu6
2009-10-28 20:57:00 status unpacked libasound2 1.0.20-3ubuntu6
2009-10-28 20:57:00 install esound-common <none> 0.2.41-5
2009-10-28 20:57:00 status half-installed esound-common 0.2.41-5
2009-10-28 20:57:00 status unpacked esound-common 0.2.41-5
2009-10-28 20:57:00 status unpacked esound-common 0.2.41-5
2009-10-28 20:57:00 install libesd-alsa0 <none> 0.2.41-5
2009-10-28 20:57:00 status half-installed libesd-alsa0 0.2.41-5
2009-10-28 20:57:00 status unpacked libesd-alsa0 0.2.41-5
2009-10-28 20:57:00 status unpacked libesd-alsa0 0.2.41-5
2009-10-28 20:57:00 install libavahi-glib1 <none> 0.6.25-1ubuntu5
2009-10-28 20:57:00 status half-installed libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 20:57:00 status unpacked libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 20:57:00 status unpacked libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 20:57:00 install gamin <none> 0.1.10-1ubuntu2
2009-10-28 20:57:00 status half-installed gamin 0.1.10-1ubuntu2
2009-10-28 20:57:00 status unpacked gamin 0.1.10-1ubuntu2
2009-10-28 20:57:00 status unpacked gamin 0.1.10-1ubuntu2
2009-10-28 20:57:00 install libgamin0 <none> 0.1.10-1ubuntu2
2009-10-28 20:57:00 status half-installed libgamin0 0.1.10-1ubuntu2
2009-10-28 20:57:00 status unpacked libgamin0 0.1.10-1ubuntu2
2009-10-28 20:57:00 status unpacked libgamin0 0.1.10-1ubuntu2
2009-10-28 20:57:00 install libhal1 <none> 0.5.13-1ubuntu8
2009-10-28 20:57:00 status half-installed libhal1 0.5.13-1ubuntu8
2009-10-28 20:57:00 status unpacked libhal1 0.5.13-1ubuntu8
2009-10-28 20:57:00 status unpacked libhal1 0.5.13-1ubuntu8
2009-10-28 20:57:00 install libhal-storage1 <none> 0.5.13-1ubuntu8
2009-10-28 20:57:00 status half-installed libhal-storage1 0.5.13-1ubuntu8
2009-10-28 20:57:00 status unpacked libhal-storage1 0.5.13-1ubuntu8
2009-10-28 20:57:00 status unpacked libhal-storage1 0.5.13-1ubuntu8
2009-10-28 20:57:00 install psmisc <none> 22.7-1
2009-10-28 20:57:00 status half-installed psmisc 22.7-1
2009-10-28 20:57:00 status unpacked psmisc 22.7-1
2009-10-28 20:57:00 status unpacked psmisc 22.7-1
2009-10-28 20:57:00 install dbus-x11 <none> 1.2.16-0ubuntu9
2009-10-28 20:57:00 status half-installed dbus-x11 1.2.16-0ubuntu9
2009-10-28 20:57:00 status unpacked dbus-x11 1.2.16-0ubuntu9
2009-10-28 20:57:00 status unpacked dbus-x11 1.2.16-0ubuntu9
2009-10-28 20:57:00 install gconf2 <none> 2.28.0-0ubuntu2
2009-10-28 20:57:00 status half-installed gconf2 2.28.0-0ubuntu2
2009-10-28 20:57:00 status unpacked gconf2 2.28.0-0ubuntu2
2009-10-28 20:57:00 status unpacked gconf2 2.28.0-0ubuntu2
2009-10-28 20:57:00 install gnome-mime-data <none> 2.18.0-1
2009-10-28 20:57:00 status half-installed gnome-mime-data 2.18.0-1
2009-10-28 20:57:01 status unpacked gnome-mime-data 2.18.0-1
2009-10-28 20:57:01 status unpacked gnome-mime-data 2.18.0-1
2009-10-28 20:57:01 install libgnomevfs2-common <none> 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status half-installed libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status unpacked libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status unpacked libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 install libgnomevfs2-0 <none> 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status half-installed libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status unpacked libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 status unpacked libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 20:57:01 install libgnome2-common <none> 2.28.0-0ubuntu3
2009-10-28 20:57:01 status half-installed libgnome2-common 2.28.0-0ubuntu3
2009-10-28 20:57:01 status unpacked libgnome2-common 2.28.0-0ubuntu3
2009-10-28 20:57:01 status unpacked libgnome2-common 2.28.0-0ubuntu3
2009-10-28 20:57:01 install libgnome-keyring0 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:01 status half-installed libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 20:57:01 status unpacked libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 20:57:01 status unpacked libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 20:57:01 install libgdu0 <none> 2.28.0+git20091012-0ubuntu1
2009-10-28 20:57:01 status half-installed libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:57:01 status unpacked libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:57:01 status unpacked libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:57:01 install libgvfscommon0 <none> 1.4.1-0ubuntu1
2009-10-28 20:57:01 status half-installed libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 20:57:01 status unpacked libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 20:57:01 status unpacked libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 20:57:01 install libatasmart4 <none> 0.16-1
2009-10-28 20:57:01 status half-installed libatasmart4 0.16-1
2009-10-28 20:57:01 status unpacked libatasmart4 0.16-1
2009-10-28 20:57:01 status unpacked libatasmart4 0.16-1
2009-10-28 20:57:01 install libgudev-1.0-0 <none> 1:147~-6
2009-10-28 20:57:01 status half-installed libgudev-1.0-0 1:147~-6
2009-10-28 20:57:01 status unpacked libgudev-1.0-0 1:147~-6
2009-10-28 20:57:01 status unpacked libgudev-1.0-0 1:147~-6
2009-10-28 20:57:01 install libparted1.8-12 <none> 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:57:01 status half-installed libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:57:01 status unpacked libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:57:01 status unpacked libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:57:01 install libeggdbus-1-0 <none> 0.5-1
2009-10-28 20:57:01 status half-installed libeggdbus-1-0 0.5-1
2009-10-28 20:57:01 status unpacked libeggdbus-1-0 0.5-1
2009-10-28 20:57:01 status unpacked libeggdbus-1-0 0.5-1
2009-10-28 20:57:02 install libpolkit-gobject-1-0 <none> 0.94-1ubuntu1
2009-10-28 20:57:02 status half-installed libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 install libpolkit-backend-1-0 <none> 0.94-1ubuntu1
2009-10-28 20:57:02 status half-installed libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 install libsgutils2-2 <none> 1.27-0.1
2009-10-28 20:57:02 status half-installed libsgutils2-2 1.27-0.1
2009-10-28 20:57:02 status unpacked libsgutils2-2 1.27-0.1
2009-10-28 20:57:02 status unpacked libsgutils2-2 1.27-0.1
2009-10-28 20:57:02 install devicekit-disks <none> 007-2ubuntu3
2009-10-28 20:57:02 status half-installed devicekit-disks 007-2ubuntu3
2009-10-28 20:57:02 status unpacked devicekit-disks 007-2ubuntu3
2009-10-28 20:57:02 status unpacked devicekit-disks 007-2ubuntu3
2009-10-28 20:57:02 install libpolkit-agent-1-0 <none> 0.94-1ubuntu1
2009-10-28 20:57:02 status half-installed libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 20:57:02 install libck-connector0 <none> 0.3.1-0ubuntu2
2009-10-28 20:57:02 status half-installed libck-connector0 0.3.1-0ubuntu2
2009-10-28 20:57:02 status unpacked libck-connector0 0.3.1-0ubuntu2
2009-10-28 20:57:02 status unpacked libck-connector0 0.3.1-0ubuntu2
2009-10-28 20:57:02 install consolekit <none> 0.3.1-0ubuntu2
2009-10-28 20:57:02 status half-installed consolekit 0.3.1-0ubuntu2
2009-10-28 20:57:02 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 20:57:02 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 20:57:02 install policykit-1 <none> 0.94-1ubuntu1
2009-10-28 20:57:02 status half-installed policykit-1 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 20:57:02 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 20:57:02 install policykit-1-gnome <none> 0.94-1+1git.230873
2009-10-28 20:57:02 status half-installed policykit-1-gnome 0.94-1+1git.230873
2009-10-28 20:57:02 status unpacked policykit-1-gnome 0.94-1+1git.230873
2009-10-28 20:57:02 status unpacked policykit-1-gnome 0.94-1+1git.230873
2009-10-28 20:57:03 install gvfs <none> 1.4.1-0ubuntu1
2009-10-28 20:57:03 status half-installed gvfs 1.4.1-0ubuntu1
2009-10-28 20:57:03 status unpacked gvfs 1.4.1-0ubuntu1
2009-10-28 20:57:03 status unpacked gvfs 1.4.1-0ubuntu1
2009-10-28 20:57:03 install libgnome2-0 <none> 2.28.0-0ubuntu3
2009-10-28 20:57:03 status half-installed libgnome2-0 2.28.0-0ubuntu3
2009-10-28 20:57:03 status unpacked libgnome2-0 2.28.0-0ubuntu3
2009-10-28 20:57:03 status unpacked libgnome2-0 2.28.0-0ubuntu3
2009-10-28 20:57:03 install libgail18 <none> 2.18.3-1
2009-10-28 20:57:03 status half-installed libgail18 2.18.3-1
2009-10-28 20:57:03 status unpacked libgail18 2.18.3-1
2009-10-28 20:57:03 status unpacked libgail18 2.18.3-1
2009-10-28 20:57:03 install libgail-common <none> 2.18.3-1
2009-10-28 20:57:03 status half-installed libgail-common 2.18.3-1
2009-10-28 20:57:03 status unpacked libgail-common 2.18.3-1
2009-10-28 20:57:03 status unpacked libgail-common 2.18.3-1
2009-10-28 20:57:03 install libgnomecanvas2-common <none> 2.26.0-1
2009-10-28 20:57:03 status half-installed libgnomecanvas2-common 2.26.0-1
2009-10-28 20:57:03 status unpacked libgnomecanvas2-common 2.26.0-1
2009-10-28 20:57:03 status unpacked libgnomecanvas2-common 2.26.0-1
2009-10-28 20:57:03 install libgnomecanvas2-0 <none> 2.26.0-1
2009-10-28 20:57:03 status half-installed libgnomecanvas2-0 2.26.0-1
2009-10-28 20:57:03 status unpacked libgnomecanvas2-0 2.26.0-1
2009-10-28 20:57:03 status unpacked libgnomecanvas2-0 2.26.0-1
2009-10-28 20:57:03 install libice6 <none> 2:1.0.5-1
2009-10-28 20:57:03 status half-installed libice6 2:1.0.5-1
2009-10-28 20:57:03 status unpacked libice6 2:1.0.5-1
2009-10-28 20:57:03 status unpacked libice6 2:1.0.5-1
2009-10-28 20:57:03 install libsm6 <none> 2:1.1.0-2
2009-10-28 20:57:03 status half-installed libsm6 2:1.1.0-2
2009-10-28 20:57:03 status unpacked libsm6 2:1.1.0-2
2009-10-28 20:57:03 status unpacked libsm6 2:1.1.0-2
2009-10-28 20:57:03 install libbonoboui2-common <none> 2.24.2-1ubuntu2
2009-10-28 20:57:03 status half-installed libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 20:57:03 status unpacked libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 20:57:03 status unpacked libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 20:57:03 install libbonoboui2-0 <none> 2.24.2-1ubuntu2
2009-10-28 20:57:03 status half-installed libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 20:57:03 status unpacked libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 20:57:03 status unpacked libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 20:57:03 install libxcb-atom1 <none> 0.3.6-1
2009-10-28 20:57:03 status half-installed libxcb-atom1 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-atom1 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-atom1 0.3.6-1
2009-10-28 20:57:03 install libxcb-aux0 <none> 0.3.6-1
2009-10-28 20:57:03 status half-installed libxcb-aux0 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-aux0 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-aux0 0.3.6-1
2009-10-28 20:57:03 install libxcb-event1 <none> 0.3.6-1
2009-10-28 20:57:03 status half-installed libxcb-event1 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-event1 0.3.6-1
2009-10-28 20:57:03 status unpacked libxcb-event1 0.3.6-1
2009-10-28 20:57:03 install libstartup-notification0 <none> 0.10-1
2009-10-28 20:57:03 status half-installed libstartup-notification0 0.10-1
2009-10-28 20:57:03 status unpacked libstartup-notification0 0.10-1
2009-10-28 20:57:03 status unpacked libstartup-notification0 0.10-1
2009-10-28 20:57:04 install libgnome-desktop-2-11 <none> 1:2.28.1-0ubuntu2
2009-10-28 20:57:04 status half-installed libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 20:57:04 install libxkbfile1 <none> 1:1.0.5-1ubuntu2
2009-10-28 20:57:04 status half-installed libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 20:57:04 status unpacked libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 20:57:04 status unpacked libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 20:57:04 install libxt6 <none> 1:1.0.5-3ubuntu1
2009-10-28 20:57:04 status half-installed libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:57:04 status unpacked libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:57:04 status unpacked libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:57:04 install libxmu6 <none> 2:1.0.4-2
2009-10-28 20:57:04 status half-installed libxmu6 2:1.0.4-2
2009-10-28 20:57:04 status unpacked libxmu6 2:1.0.4-2
2009-10-28 20:57:04 status unpacked libxmu6 2:1.0.4-2
2009-10-28 20:57:04 install libxpm4 <none> 1:3.5.7-2
2009-10-28 20:57:04 status half-installed libxpm4 1:3.5.7-2
2009-10-28 20:57:04 status unpacked libxpm4 1:3.5.7-2
2009-10-28 20:57:04 status unpacked libxpm4 1:3.5.7-2
2009-10-28 20:57:04 install libxaw7 <none> 2:1.0.6-1
2009-10-28 20:57:04 status half-installed libxaw7 2:1.0.6-1
2009-10-28 20:57:04 status unpacked libxaw7 2:1.0.6-1
2009-10-28 20:57:04 status unpacked libxaw7 2:1.0.6-1
2009-10-28 20:57:04 install x11-xkb-utils <none> 7.4+3
2009-10-28 20:57:04 status half-installed x11-xkb-utils 7.4+3
2009-10-28 20:57:04 status unpacked x11-xkb-utils 7.4+3
2009-10-28 20:57:04 status unpacked x11-xkb-utils 7.4+3
2009-10-28 20:57:04 install libxklavier15 <none> 4.0-0ubuntu5
2009-10-28 20:57:04 status half-installed libxklavier15 4.0-0ubuntu5
2009-10-28 20:57:04 status unpacked libxklavier15 4.0-0ubuntu5
2009-10-28 20:57:04 status unpacked libxklavier15 4.0-0ubuntu5
2009-10-28 20:57:04 install libgnomekbd-common <none> 2.28.0-0ubuntu2
2009-10-28 20:57:04 status half-installed libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 20:57:04 install libgnomekbd4 <none> 2.28.0-0ubuntu2
2009-10-28 20:57:04 status half-installed libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 20:57:04 install libgnomekbdui4 <none> 2.28.0-0ubuntu2
2009-10-28 20:57:04 status half-installed libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 20:57:04 status unpacked libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 20:57:04 install libgtop2-common <none> 2.26.1-0ubuntu1
2009-10-28 20:57:04 status half-installed libgtop2-common 2.26.1-0ubuntu1
2009-10-28 20:57:04 status unpacked libgtop2-common 2.26.1-0ubuntu1
2009-10-28 20:57:05 status unpacked libgtop2-common 2.26.1-0ubuntu1
2009-10-28 20:57:05 install libgtop2-7 <none> 2.26.1-0ubuntu1
2009-10-28 20:57:05 status half-installed libgtop2-7 2.26.1-0ubuntu1
2009-10-28 20:57:05 status unpacked libgtop2-7 2.26.1-0ubuntu1
2009-10-28 20:57:05 status unpacked libgtop2-7 2.26.1-0ubuntu1
2009-10-28 20:57:05 install liblaunchpad-integration1 <none> 0.1.26
2009-10-28 20:57:05 status half-installed liblaunchpad-integration1 0.1.26
2009-10-28 20:57:05 status unpacked liblaunchpad-integration1 0.1.26
2009-10-28 20:57:05 status unpacked liblaunchpad-integration1 0.1.26
2009-10-28 20:57:05 install libgucharmap7 <none> 1:2.28.0-0ubuntu1
2009-10-28 20:57:05 status half-installed libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 20:57:05 status unpacked libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 20:57:05 status unpacked libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 20:57:05 install libproxy0 <none> 0.2.3-0ubuntu5
2009-10-28 20:57:05 status half-installed libproxy0 0.2.3-0ubuntu5
2009-10-28 20:57:05 status unpacked libproxy0 0.2.3-0ubuntu5
2009-10-28 20:57:05 status unpacked libproxy0 0.2.3-0ubuntu5
2009-10-28 20:57:05 install libsoup2.4-1 <none> 2.28.1-2
2009-10-28 20:57:05 status half-installed libsoup2.4-1 2.28.1-2
2009-10-28 20:57:05 status unpacked libsoup2.4-1 2.28.1-2
2009-10-28 20:57:05 status unpacked libsoup2.4-1 2.28.1-2
2009-10-28 20:57:05 install libsoup-gnome2.4-1 <none> 2.28.1-2
2009-10-28 20:57:05 status half-installed libsoup-gnome2.4-1 2.28.1-2
2009-10-28 20:57:05 status unpacked libsoup-gnome2.4-1 2.28.1-2
2009-10-28 20:57:05 status unpacked libsoup-gnome2.4-1 2.28.1-2
2009-10-28 20:57:05 install libgweather-common <none> 2.28.0-1ubuntu2
2009-10-28 20:57:05 status half-installed libgweather-common 2.28.0-1ubuntu2
2009-10-28 20:57:05 status unpacked libgweather-common 2.28.0-1ubuntu2
2009-10-28 20:57:05 status unpacked libgweather-common 2.28.0-1ubuntu2
2009-10-28 20:57:05 install libgweather1 <none> 2.28.0-1ubuntu2
2009-10-28 20:57:05 status half-installed libgweather1 2.28.0-1ubuntu2
2009-10-28 20:57:05 status unpacked libgweather1 2.28.0-1ubuntu2
2009-10-28 20:57:05 status unpacked libgweather1 2.28.0-1ubuntu2
2009-10-28 20:57:05 install libnotify1 <none> 0.4.5-1ubuntu1
2009-10-28 20:57:05 status half-installed libnotify1 0.4.5-1ubuntu1
2009-10-28 20:57:05 status unpacked libnotify1 0.4.5-1ubuntu1
2009-10-28 20:57:05 status unpacked libnotify1 0.4.5-1ubuntu1
2009-10-28 20:57:05 install libpanel-applet2-0 <none> 1:2.28.0-0ubuntu6
2009-10-28 20:57:05 status half-installed libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 20:57:06 status unpacked libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 20:57:06 status unpacked libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 20:57:06 install libxres1 <none> 2:1.0.3-2
2009-10-28 20:57:06 status half-installed libxres1 2:1.0.3-2
2009-10-28 20:57:06 status unpacked libxres1 2:1.0.3-2
2009-10-28 20:57:06 status unpacked libxres1 2:1.0.3-2
2009-10-28 20:57:06 install libwnck-common <none> 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status half-installed libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status unpacked libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status unpacked libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 install libwnck22 <none> 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status half-installed libwnck22 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status unpacked libwnck22 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 status unpacked libwnck22 1:2.28.0-0ubuntu1
2009-10-28 20:57:06 install librarian0 <none> 0.8.1-2ubuntu3
2009-10-28 20:57:06 status half-installed librarian0 0.8.1-2ubuntu3
2009-10-28 20:57:06 status unpacked librarian0 0.8.1-2ubuntu3
2009-10-28 20:57:06 status unpacked librarian0 0.8.1-2ubuntu3
2009-10-28 20:57:06 install rarian-compat <none> 0.8.1-2ubuntu3
2009-10-28 20:57:06 status half-installed rarian-compat 0.8.1-2ubuntu3
2009-10-28 20:57:06 status unpacked rarian-compat 0.8.1-2ubuntu3
2009-10-28 20:57:06 status unpacked rarian-compat 0.8.1-2ubuntu3
2009-10-28 20:57:06 install python-support <none> 1.0.3ubuntu1
2009-10-28 20:57:06 status half-installed python-support 1.0.3ubuntu1
2009-10-28 20:57:06 status unpacked python-support 1.0.3ubuntu1
2009-10-28 20:57:06 status unpacked python-support 1.0.3ubuntu1
2009-10-28 20:57:06 install gnome-applets-data <none> 2.28.0-0ubuntu2
2009-10-28 20:57:06 status half-installed gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 20:57:07 status unpacked gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 20:57:07 status unpacked gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 20:57:07 install libnspr4-0d <none> 4.8-0ubuntu1
2009-10-28 20:57:07 status half-installed libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:57:08 status unpacked libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:57:08 status unpacked libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:57:08 install libedataserver1.2-11 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 20:57:08 install libical0 <none> 0.43-3
2009-10-28 20:57:08 status half-installed libical0 0.43-3
2009-10-28 20:57:08 status unpacked libical0 0.43-3
2009-10-28 20:57:08 status unpacked libical0 0.43-3
2009-10-28 20:57:08 install libecal1.2-7 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 20:57:08 install libnss3-1d <none> 3.12.3.1-0ubuntu2
2009-10-28 20:57:08 status half-installed libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:57:08 status unpacked libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:57:08 status unpacked libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:57:08 install libcamel1.2-14 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 20:57:08 install libebook1.2-9 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 20:57:08 install evolution-data-server-common <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 20:57:08 install libedataserverui1.2-8 <none> 2.28.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 20:57:08 install libgnome-menu2 <none> 2.28.0.1-0ubuntu1
2009-10-28 20:57:08 status half-installed libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 20:57:08 status unpacked libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 20:57:09 install libgnomeui-common <none> 2.24.2-1
2009-10-28 20:57:09 status half-installed libgnomeui-common 2.24.2-1
2009-10-28 20:57:09 status unpacked libgnomeui-common 2.24.2-1
2009-10-28 20:57:09 status unpacked libgnomeui-common 2.24.2-1
2009-10-28 20:57:09 install libgnomeui-0 <none> 2.24.2-1
2009-10-28 20:57:09 status half-installed libgnomeui-0 2.24.2-1
2009-10-28 20:57:09 status unpacked libgnomeui-0 2.24.2-1
2009-10-28 20:57:09 status unpacked libgnomeui-0 2.24.2-1
2009-10-28 20:57:09 install libcroco3 <none> 0.6.1-2
2009-10-28 20:57:09 status half-installed libcroco3 0.6.1-2
2009-10-28 20:57:09 status unpacked libcroco3 0.6.1-2
2009-10-28 20:57:09 status unpacked libcroco3 0.6.1-2
2009-10-28 20:57:09 install libgsf-1-common <none> 1.14.15-1ubuntu1
2009-10-28 20:57:09 status half-installed libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 20:57:09 status unpacked libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 20:57:09 status unpacked libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 20:57:09 install libgsf-1-114 <none> 1.14.15-1ubuntu1
2009-10-28 20:57:09 status half-installed libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 20:57:09 status unpacked libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 20:57:09 status unpacked libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 20:57:09 install librsvg2-2 <none> 2.26.0-1
2009-10-28 20:57:09 status half-installed librsvg2-2 2.26.0-1
2009-10-28 20:57:09 status unpacked librsvg2-2 2.26.0-1
2009-10-28 20:57:09 status unpacked librsvg2-2 2.26.0-1
2009-10-28 20:57:09 install gnome-panel-data <none> 1:2.28.0-0ubuntu6
2009-10-28 20:57:09 status half-installed gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 20:57:10 status unpacked gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 20:57:10 status unpacked gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 20:57:10 install gnome-desktop-data <none> 1:2.28.1-0ubuntu2
2009-10-28 20:57:10 status half-installed gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 20:57:10 status unpacked gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 20:57:10 status unpacked gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 20:57:10 install libltdl7 <none> 2.2.6a-4
2009-10-28 20:57:10 status half-installed libltdl7 2.2.6a-4
2009-10-28 20:57:10 status unpacked libltdl7 2.2.6a-4
2009-10-28 20:57:10 status unpacked libltdl7 2.2.6a-4
2009-10-28 20:57:10 install libogg0 <none> 1.1.4~dfsg-1
2009-10-28 20:57:10 status half-installed libogg0 1.1.4~dfsg-1
2009-10-28 20:57:10 status unpacked libogg0 1.1.4~dfsg-1
2009-10-28 20:57:10 status unpacked libogg0 1.1.4~dfsg-1
2009-10-28 20:57:10 install libtdb1 <none> 1.1.5-1
2009-10-28 20:57:10 status half-installed libtdb1 1.1.5-1
2009-10-28 20:57:10 status unpacked libtdb1 1.1.5-1
2009-10-28 20:57:10 status unpacked libtdb1 1.1.5-1
2009-10-28 20:57:10 install libvorbis0a <none> 1.2.0.dfsg-6
2009-10-28 20:57:10 status half-installed libvorbis0a 1.2.0.dfsg-6
2009-10-28 20:57:10 status unpacked libvorbis0a 1.2.0.dfsg-6
2009-10-28 20:57:10 status unpacked libvorbis0a 1.2.0.dfsg-6
2009-10-28 20:57:10 install libvorbisfile3 <none> 1.2.0.dfsg-6
2009-10-28 20:57:10 status half-installed libvorbisfile3 1.2.0.dfsg-6
2009-10-28 20:57:10 status unpacked libvorbisfile3 1.2.0.dfsg-6
2009-10-28 20:57:10 status unpacked libvorbisfile3 1.2.0.dfsg-6
2009-10-28 20:57:10 install libcanberra0 <none> 0.15-0ubuntu7
2009-10-28 20:57:10 status half-installed libcanberra0 0.15-0ubuntu7
2009-10-28 20:57:10 status unpacked libcanberra0 0.15-0ubuntu7
2009-10-28 20:57:10 status unpacked libcanberra0 0.15-0ubuntu7
2009-10-28 20:57:10 install libcanberra-gtk0 <none> 0.15-0ubuntu7
2009-10-28 20:57:10 status half-installed libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 20:57:10 status unpacked libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 20:57:10 status unpacked libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 20:57:10 install libgnome-window-settings1 <none> 1:2.28.1-0ubuntu1
2009-10-28 20:57:10 status half-installed libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 20:57:10 status unpacked libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 20:57:10 status unpacked libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 20:57:10 install metacity-common <none> 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status half-installed metacity-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status unpacked metacity-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status unpacked metacity-common 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 install libmetacity0 <none> 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status half-installed libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status unpacked libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 status unpacked libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 20:57:10 install libunique-1.0-0 <none> 1.1.2-1ubuntu1
2009-10-28 20:57:10 status half-installed libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 20:57:10 status unpacked libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 20:57:10 status unpacked libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 20:57:10 install libxss1 <none> 1:1.1.3-1
2009-10-28 20:57:10 status half-installed libxss1 1:1.1.3-1
2009-10-28 20:57:11 status unpacked libxss1 1:1.1.3-1
2009-10-28 20:57:11 status unpacked libxss1 1:1.1.3-1
2009-10-28 20:57:11 install capplets-data <none> 1:2.28.1-0ubuntu1
2009-10-28 20:57:11 status half-installed capplets-data 1:2.28.1-0ubuntu1
2009-10-28 20:57:11 status triggers-pending shared-mime-info 0.70-0ubuntu1
2009-10-28 20:57:11 status half-installed capplets-data 1:2.28.1-0ubuntu1
2009-10-28 20:57:11 status unpacked capplets-data 1:2.28.1-0ubuntu1
2009-10-28 20:57:11 status unpacked capplets-data 1:2.28.1-0ubuntu1
2009-10-28 20:57:11 install libflac8 <none> 1.2.1-2build1
2009-10-28 20:57:11 status half-installed libflac8 1.2.1-2build1
2009-10-28 20:57:11 status unpacked libflac8 1.2.1-2build1
2009-10-28 20:57:11 status unpacked libflac8 1.2.1-2build1
2009-10-28 20:57:11 install libvorbisenc2 <none> 1.2.0.dfsg-6
2009-10-28 20:57:11 status half-installed libvorbisenc2 1.2.0.dfsg-6
2009-10-28 20:57:11 status unpacked libvorbisenc2 1.2.0.dfsg-6
2009-10-28 20:57:11 status unpacked libvorbisenc2 1.2.0.dfsg-6
2009-10-28 20:57:11 install libsndfile1 <none> 1.0.20-1ubuntu1
2009-10-28 20:57:11 status half-installed libsndfile1 1.0.20-1ubuntu1
2009-10-28 20:57:11 status unpacked libsndfile1 1.0.20-1ubuntu1
2009-10-28 20:57:11 status unpacked libsndfile1 1.0.20-1ubuntu1
2009-10-28 20:57:11 install libwrap0 <none> 7.6.q-16
2009-10-28 20:57:11 status half-installed libwrap0 7.6.q-16
2009-10-28 20:57:11 status unpacked libwrap0 7.6.q-16
2009-10-28 20:57:11 status unpacked libwrap0 7.6.q-16
2009-10-28 20:57:11 install libxtst6 <none> 2:1.0.3-1ubuntu2
2009-10-28 20:57:11 status half-installed libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:57:11 status unpacked libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:57:11 status unpacked libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:57:12 install libpulse0 <none> 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status half-installed libpulse0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status unpacked libpulse0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status unpacked libpulse0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 install libpulse-mainloop-glib0 <none> 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status half-installed libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status unpacked libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 status unpacked libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 20:57:12 install libxxf86misc1 <none> 1:1.0.1-3
2009-10-28 20:57:12 status half-installed libxxf86misc1 1:1.0.1-3
2009-10-28 20:57:12 status unpacked libxxf86misc1 1:1.0.1-3
2009-10-28 20:57:12 status unpacked libxxf86misc1 1:1.0.1-3
2009-10-28 20:57:12 install gnome-settings-daemon <none> 2.28.1-0ubuntu1
2009-10-28 20:57:12 status half-installed gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 20:57:12 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 20:57:12 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 20:57:12 install python-cairo <none> 1.8.6-1ubuntu1
2009-10-28 20:57:12 status half-installed python-cairo 1.8.6-1ubuntu1
2009-10-28 20:57:12 status unpacked python-cairo 1.8.6-1ubuntu1
2009-10-28 20:57:12 status unpacked python-cairo 1.8.6-1ubuntu1
2009-10-28 20:57:12 install libffi5 <none> 3.0.7-2ubuntu1
2009-10-28 20:57:12 status half-installed libffi5 3.0.7-2ubuntu1
2009-10-28 20:57:12 status unpacked libffi5 3.0.7-2ubuntu1
2009-10-28 20:57:12 status unpacked libffi5 3.0.7-2ubuntu1
2009-10-28 20:57:12 install python-gobject <none> 2.18.0-0ubuntu2
2009-10-28 20:57:12 status half-installed python-gobject 2.18.0-0ubuntu2
2009-10-28 20:57:12 status unpacked python-gobject 2.18.0-0ubuntu2
2009-10-28 20:57:12 status unpacked python-gobject 2.18.0-0ubuntu2
2009-10-28 20:57:12 install python-gtk2 <none> 2.16.0-0ubuntu1
2009-10-28 20:57:12 status half-installed python-gtk2 2.16.0-0ubuntu1
2009-10-28 20:57:12 status unpacked python-gtk2 2.16.0-0ubuntu1
2009-10-28 20:57:12 status unpacked python-gtk2 2.16.0-0ubuntu1
2009-10-28 20:57:12 install python-gmenu <none> 2.28.0.1-0ubuntu1
2009-10-28 20:57:12 status half-installed python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 status unpacked python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 status unpacked python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 install gnome-menus <none> 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 status half-installed gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 status unpacked gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 status unpacked gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 20:57:13 install hicolor-icon-theme <none> 0.10-2
2009-10-28 20:57:13 status half-installed hicolor-icon-theme 0.10-2
2009-10-28 20:57:13 status unpacked hicolor-icon-theme 0.10-2
2009-10-28 20:57:13 status unpacked hicolor-icon-theme 0.10-2
2009-10-28 20:57:13 install libgtk2.0-bin <none> 2.18.3-1
2009-10-28 20:57:13 status half-installed libgtk2.0-bin 2.18.3-1
2009-10-28 20:57:13 status unpacked libgtk2.0-bin 2.18.3-1
2009-10-28 20:57:13 status unpacked libgtk2.0-bin 2.18.3-1
2009-10-28 20:57:13 install librsvg2-common <none> 2.26.0-1
2009-10-28 20:57:13 status half-installed librsvg2-common 2.26.0-1
2009-10-28 20:57:13 status unpacked librsvg2-common 2.26.0-1
2009-10-28 20:57:13 status unpacked librsvg2-common 2.26.0-1
2009-10-28 20:57:13 install gnome-icon-theme <none> 2.28.0-0ubuntu1
2009-10-28 20:57:13 status half-installed gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 20:57:15 status unpacked gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 20:57:15 status unpacked gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 20:57:15 install desktop-file-utils <none> 0.15-2ubuntu1
2009-10-28 20:57:15 status half-installed desktop-file-utils 0.15-2ubuntu1
2009-10-28 20:57:16 status unpacked desktop-file-utils 0.15-2ubuntu1
2009-10-28 20:57:16 status unpacked desktop-file-utils 0.15-2ubuntu1
2009-10-28 20:57:16 install python-apt <none> 0.7.13.2ubuntu4
2009-10-28 20:57:16 status half-installed python-apt 0.7.13.2ubuntu4
2009-10-28 20:57:16 status unpacked python-apt 0.7.13.2ubuntu4
2009-10-28 20:57:16 status unpacked python-apt 0.7.13.2ubuntu4
2009-10-28 20:57:16 install python-dbus <none> 0.83.0-1ubuntu2
2009-10-28 20:57:16 status half-installed python-dbus 0.83.0-1ubuntu2
2009-10-28 20:57:16 status unpacked python-dbus 0.83.0-1ubuntu2
2009-10-28 20:57:16 status unpacked python-dbus 0.83.0-1ubuntu2
2009-10-28 20:57:16 install ubuntu-system-service <none> 0.1.16
2009-10-28 20:57:16 status half-installed ubuntu-system-service 0.1.16
2009-10-28 20:57:16 status unpacked ubuntu-system-service 0.1.16
2009-10-28 20:57:16 status unpacked ubuntu-system-service 0.1.16
2009-10-28 20:57:16 install gnome-control-center <none> 1:2.28.1-0ubuntu1
2009-10-28 20:57:16 status half-installed gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 20:57:16 status unpacked gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 20:57:16 status unpacked gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 20:57:16 install python-gnomecanvas <none> 2.28.0-0ubuntu1
2009-10-28 20:57:16 status half-installed python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 20:57:16 install python-pyorbit <none> 2.24.0-0ubuntu3
2009-10-28 20:57:16 status half-installed python-pyorbit 2.24.0-0ubuntu3
2009-10-28 20:57:16 status unpacked python-pyorbit 2.24.0-0ubuntu3
2009-10-28 20:57:16 status unpacked python-pyorbit 2.24.0-0ubuntu3
2009-10-28 20:57:16 install python-gconf <none> 2.28.0-0ubuntu1
2009-10-28 20:57:16 status half-installed python-gconf 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gconf 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gconf 2.28.0-0ubuntu1
2009-10-28 20:57:16 install python-gnome2 <none> 2.28.0-0ubuntu1
2009-10-28 20:57:16 status half-installed python-gnome2 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gnome2 2.28.0-0ubuntu1
2009-10-28 20:57:16 status unpacked python-gnome2 2.28.0-0ubuntu1
2009-10-28 20:57:16 install gnome-about <none> 1:2.28.1-0ubuntu2
2009-10-28 20:57:16 status half-installed gnome-about 1:2.28.1-0ubuntu2
2009-10-28 20:57:16 status unpacked gnome-about 1:2.28.1-0ubuntu2
2009-10-28 20:57:16 status unpacked gnome-about 1:2.28.1-0ubuntu2
2009-10-28 20:57:16 install gnome-panel <none> 1:2.28.0-0ubuntu6
2009-10-28 20:57:16 status half-installed gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 20:57:17 status unpacked gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 20:57:17 status unpacked gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 20:57:17 install gnome-applets <none> 2.28.0-0ubuntu2
2009-10-28 20:57:17 status half-installed gnome-applets 2.28.0-0ubuntu2
2009-10-28 20:57:17 status unpacked gnome-applets 2.28.0-0ubuntu2
2009-10-28 20:57:17 status unpacked gnome-applets 2.28.0-0ubuntu2
2009-10-28 20:57:17 install libexif12 <none> 0.6.17-1
2009-10-28 20:57:17 status half-installed libexif12 0.6.17-1
2009-10-28 20:57:17 status unpacked libexif12 0.6.17-1
2009-10-28 20:57:17 status unpacked libexif12 0.6.17-1
2009-10-28 20:57:17 install libgphoto2-port0 <none> 2.4.6-1ubuntu6
2009-10-28 20:57:17 status half-installed libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 20:57:17 status unpacked libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 20:57:17 status unpacked libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 20:57:17 install libgphoto2-2 <none> 2.4.6-1ubuntu6
2009-10-28 20:57:17 status half-installed libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 20:57:17 status unpacked libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 20:57:17 status unpacked libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 20:57:17 install libieee1284-3 <none> 0.2.11-5ubuntu2
2009-10-28 20:57:17 status half-installed libieee1284-3 0.2.11-5ubuntu2
2009-10-28 20:57:17 status unpacked libieee1284-3 0.2.11-5ubuntu2
2009-10-28 20:57:17 status unpacked libieee1284-3 0.2.11-5ubuntu2
2009-10-28 20:57:17 install libv4l-0 <none> 0.6.0-1
2009-10-28 20:57:17 status half-installed libv4l-0 0.6.0-1
2009-10-28 20:57:17 status unpacked libv4l-0 0.6.0-1
2009-10-28 20:57:17 status unpacked libv4l-0 0.6.0-1
2009-10-28 20:57:17 install libsane <none> 1.0.20-4ubuntu3
2009-10-28 20:57:17 status half-installed libsane 1.0.20-4ubuntu3
2009-10-28 20:57:18 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 20:57:18 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 20:57:18 install libsnmp-base <none> 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:18 status half-installed libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:18 status unpacked libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:18 status unpacked libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:18 install libperl5.10 <none> 5.10.0-24ubuntu4
2009-10-28 20:57:18 status half-installed libperl5.10 5.10.0-24ubuntu4
2009-10-28 20:57:18 status unpacked libperl5.10 5.10.0-24ubuntu4
2009-10-28 20:57:18 status unpacked libperl5.10 5.10.0-24ubuntu4
2009-10-28 20:57:18 install libsensors3 <none> 1:2.10.8-1
2009-10-28 20:57:18 status half-installed libsensors3 1:2.10.8-1
2009-10-28 20:57:18 status unpacked libsensors3 1:2.10.8-1
2009-10-28 20:57:18 status unpacked libsensors3 1:2.10.8-1
2009-10-28 20:57:18 install libsnmp15 <none> 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:18 status half-installed libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:19 status unpacked libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:19 status unpacked libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 20:57:19 install python-imaging <none> 1.1.6-3ubuntu1
2009-10-28 20:57:19 status half-installed python-imaging 1.1.6-3ubuntu1
2009-10-28 20:57:19 status unpacked python-imaging 1.1.6-3ubuntu1
2009-10-28 20:57:19 status unpacked python-imaging 1.1.6-3ubuntu1
2009-10-28 20:57:19 install hplip-data <none> 3.9.8-1ubuntu2
2009-10-28 20:57:19 status half-installed hplip-data 3.9.8-1ubuntu2
2009-10-28 20:57:21 status unpacked hplip-data 3.9.8-1ubuntu2
2009-10-28 20:57:21 status unpacked hplip-data 3.9.8-1ubuntu2
2009-10-28 20:57:21 install hplip <none> 3.9.8-1ubuntu2
2009-10-28 20:57:21 status half-installed hplip 3.9.8-1ubuntu2
2009-10-28 20:57:21 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 20:57:21 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 20:57:21 install wireless-crda <none> 1.10
2009-10-28 20:57:21 status half-installed wireless-crda 1.10
2009-10-28 20:57:21 status unpacked wireless-crda 1.10
2009-10-28 20:57:21 status unpacked wireless-crda 1.10
2009-10-28 20:57:21 install linux-image-2.6.31-14-generic <none> 2.6.31-14.48
2009-10-28 20:57:21 status half-installed linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 20:57:34 status unpacked linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 20:57:34 status unpacked linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 20:57:34 install openoffice.org-style-human <none> 1:3.1.1-5ubuntu1
2009-10-28 20:57:34 status half-installed openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:35 status unpacked openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:35 status unpacked openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:35 install openoffice.org-common <none> 1:3.1.1-5ubuntu1
2009-10-28 20:57:35 status half-installed openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:39 status half-installed openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 install ttf-opensymbol <none> 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 status half-installed ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 status unpacked ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 status unpacked ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:40 install libgstreamer0.10-0 <none> 0.10.25-2
2009-10-28 20:57:40 status half-installed libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:40 status unpacked libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:40 status unpacked libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:41 install libgstreamer-plugins-base0.10-0 <none> 0.10.25-2ubuntu1
2009-10-28 20:57:41 status half-installed libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:41 status unpacked libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:41 status unpacked libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:41 install libhunspell-1.2-0 <none> 1.2.8-4ubuntu2
2009-10-28 20:57:41 status half-installed libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:57:41 status unpacked libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:57:41 status unpacked libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:57:41 install libhyphen0 <none> 2.4-4
2009-10-28 20:57:41 status half-installed libhyphen0 2.4-4
2009-10-28 20:57:41 status unpacked libhyphen0 2.4-4
2009-10-28 20:57:41 status unpacked libhyphen0 2.4-4
2009-10-28 20:57:41 install libicu40 <none> 4.0.1-2ubuntu2
2009-10-28 20:57:41 status half-installed libicu40 4.0.1-2ubuntu2
2009-10-28 20:57:42 status unpacked libicu40 4.0.1-2ubuntu2
2009-10-28 20:57:42 status unpacked libicu40 4.0.1-2ubuntu2
2009-10-28 20:57:42 install libneon27-gnutls <none> 0.28.6-1
2009-10-28 20:57:42 status half-installed libneon27-gnutls 0.28.6-1
2009-10-28 20:57:42 status unpacked libneon27-gnutls 0.28.6-1
2009-10-28 20:57:42 status unpacked libneon27-gnutls 0.28.6-1
2009-10-28 20:57:42 install mysql-common <none> 5.1.37-1ubuntu5
2009-10-28 20:57:42 status half-installed mysql-common 5.1.37-1ubuntu5
2009-10-28 20:57:42 status unpacked mysql-common 5.1.37-1ubuntu5
2009-10-28 20:57:42 status unpacked mysql-common 5.1.37-1ubuntu5
2009-10-28 20:57:42 install libmysqlclient16 <none> 5.1.37-1ubuntu5
2009-10-28 20:57:42 status half-installed libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:57:42 status unpacked libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:57:42 status unpacked libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:57:42 install libpq5 <none> 8.4.1-1
2009-10-28 20:57:42 status half-installed libpq5 8.4.1-1
2009-10-28 20:57:42 status unpacked libpq5 8.4.1-1
2009-10-28 20:57:42 status unpacked libpq5 8.4.1-1
2009-10-28 20:57:42 install libxslt1.1 <none> 1.1.24-2ubuntu2
2009-10-28 20:57:42 status half-installed libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:57:43 status unpacked libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:57:43 status unpacked libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:57:43 install libraptor1 <none> 1.4.19-1
2009-10-28 20:57:43 status half-installed libraptor1 1.4.19-1
2009-10-28 20:57:43 status unpacked libraptor1 1.4.19-1
2009-10-28 20:57:43 status unpacked libraptor1 1.4.19-1
2009-10-28 20:57:43 install librasqal1 <none> 0.9.16-1
2009-10-28 20:57:43 status half-installed librasqal1 0.9.16-1
2009-10-28 20:57:43 status unpacked librasqal1 0.9.16-1
2009-10-28 20:57:43 status unpacked librasqal1 0.9.16-1
2009-10-28 20:57:43 install librdf0 <none> 1.0.9-2
2009-10-28 20:57:43 status half-installed librdf0 1.0.9-2
2009-10-28 20:57:43 status unpacked librdf0 1.0.9-2
2009-10-28 20:57:43 status unpacked librdf0 1.0.9-2
2009-10-28 20:57:43 install libstlport4.6ldbl <none> 4.6.2-5build1
2009-10-28 20:57:43 status half-installed libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:57:43 status unpacked libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:57:43 status unpacked libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:57:43 install uno-libs3 <none> 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:43 status half-installed uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:43 status unpacked uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:43 status unpacked uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:43 install ure <none> 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:43 status half-installed ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:44 status unpacked ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:44 status unpacked ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:57:44 install openoffice.org-core <none> 1:3.1.1-5ubuntu1
2009-10-28 20:57:44 status half-installed openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 status unpacked openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 status unpacked openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 install python-uno <none> 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 status half-installed python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 status unpacked python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 status unpacked python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:57:56 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2009-10-28 20:57:56 status half-configured shared-mime-info 0.70-0ubuntu1
2009-10-28 20:57:57 status installed shared-mime-info 0.70-0ubuntu1
2009-10-28 20:57:57 startup packages configure
2009-10-28 20:57:57 configure openoffice.org-style-human 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status half-configured openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status installed openoffice.org-style-human 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 configure openoffice.org-common 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status half-configured openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status installed openoffice.org-common 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 configure ttf-opensymbol 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status unpacked ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status half-configured ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 status installed ttf-opensymbol 1:3.1.1-5ubuntu1
2009-10-28 20:57:57 configure libsysfs2 2.1.0-5 2.1.0-5
2009-10-28 20:57:57 status unpacked libsysfs2 2.1.0-5
2009-10-28 20:57:57 status half-configured libsysfs2 2.1.0-5
2009-10-28 20:57:57 status installed libsysfs2 2.1.0-5
2009-10-28 20:57:57 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 20:57:57 configure tsconf 1.0-7 1.0-7
2009-10-28 20:57:57 status unpacked tsconf 1.0-7
2009-10-28 20:57:57 status unpacked tsconf 1.0-7
2009-10-28 20:57:57 status half-configured tsconf 1.0-7
2009-10-28 20:57:57 status installed tsconf 1.0-7
2009-10-28 20:57:57 configure libts-0.0-0 1.0-7 1.0-7
2009-10-28 20:57:57 status unpacked libts-0.0-0 1.0-7
2009-10-28 20:57:57 status half-configured libts-0.0-0 1.0-7
2009-10-28 20:57:57 status installed libts-0.0-0 1.0-7
2009-10-28 20:57:57 configure libdirectfb-1.2-0 1.2.7-2ubuntu1 1.2.7-2ubuntu1
2009-10-28 20:57:57 status unpacked libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:57:57 status half-configured libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:57:57 status installed libdirectfb-1.2-0 1.2.7-2ubuntu1
2009-10-28 20:57:57 configure libexpat1 2.0.1-4ubuntu1 2.0.1-4ubuntu1
2009-10-28 20:57:57 status unpacked libexpat1 2.0.1-4ubuntu1
2009-10-28 20:57:57 status half-configured libexpat1 2.0.1-4ubuntu1
2009-10-28 20:57:57 status installed libexpat1 2.0.1-4ubuntu1
2009-10-28 20:57:57 configure libfreetype6 2.3.9-5 2.3.9-5
2009-10-28 20:57:57 status unpacked libfreetype6 2.3.9-5
2009-10-28 20:57:57 status half-configured libfreetype6 2.3.9-5
2009-10-28 20:57:57 status installed libfreetype6 2.3.9-5
2009-10-28 20:57:57 configure defoma 0.11.10-0.2ubuntu1 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status unpacked defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status half-configured defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 status installed defoma 0.11.10-0.2ubuntu1
2009-10-28 20:57:57 configure ttf-freefont 20090104-2 20090104-2
2009-10-28 20:57:57 status unpacked ttf-freefont 20090104-2
2009-10-28 20:57:57 status unpacked ttf-freefont 20090104-2
2009-10-28 20:57:57 status half-configured ttf-freefont 20090104-2
2009-10-28 20:57:57 status installed ttf-freefont 20090104-2
2009-10-28 20:57:57 configure fontconfig-config 2.6.0-1ubuntu12 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status half-configured fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 status installed fontconfig-config 2.6.0-1ubuntu12
2009-10-28 20:57:57 configure libfontconfig1 2.6.0-1ubuntu12 2.6.0-1ubuntu12
2009-10-28 20:57:57 status unpacked libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:57:57 status half-configured libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:57:57 status installed libfontconfig1 2.6.0-1ubuntu12
2009-10-28 20:57:57 configure libpixman-1-0 0.14.0-1 0.14.0-1
2009-10-28 20:57:57 status unpacked libpixman-1-0 0.14.0-1
2009-10-28 20:57:58 status half-configured libpixman-1-0 0.14.0-1
2009-10-28 20:57:58 status installed libpixman-1-0 0.14.0-1
2009-10-28 20:57:58 configure libpng12-0 1.2.37-1 1.2.37-1
2009-10-28 20:57:58 status unpacked libpng12-0 1.2.37-1
2009-10-28 20:57:58 status half-configured libpng12-0 1.2.37-1
2009-10-28 20:57:58 status installed libpng12-0 1.2.37-1
2009-10-28 20:57:58 configure libxau6 1:1.0.4-2 1:1.0.4-2
2009-10-28 20:57:58 status unpacked libxau6 1:1.0.4-2
2009-10-28 20:57:58 status half-configured libxau6 1:1.0.4-2
2009-10-28 20:57:58 status installed libxau6 1:1.0.4-2
2009-10-28 20:57:58 configure libxdmcp6 1:1.0.2-3 1:1.0.2-3
2009-10-28 20:57:58 status unpacked libxdmcp6 1:1.0.2-3
2009-10-28 20:57:58 status half-configured libxdmcp6 1:1.0.2-3
2009-10-28 20:57:58 status installed libxdmcp6 1:1.0.2-3
2009-10-28 20:57:58 configure libxcb1 1.4-1 1.4-1
2009-10-28 20:57:58 status unpacked libxcb1 1.4-1
2009-10-28 20:57:58 status half-configured libxcb1 1.4-1
2009-10-28 20:57:58 status installed libxcb1 1.4-1
2009-10-28 20:57:58 configure libx11-data 2:1.2.2-1ubuntu1 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status unpacked libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status half-configured libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status installed libx11-data 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 configure libx11-6 2:1.2.2-1ubuntu1 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status unpacked libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status half-configured libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 status installed libx11-6 2:1.2.2-1ubuntu1
2009-10-28 20:57:58 configure libxcb-render0 1.4-1 1.4-1
2009-10-28 20:57:58 status unpacked libxcb-render0 1.4-1
2009-10-28 20:57:58 status half-configured libxcb-render0 1.4-1
2009-10-28 20:57:58 status installed libxcb-render0 1.4-1
2009-10-28 20:57:58 configure libxcb-render-util0 0.3.6-1 0.3.6-1
2009-10-28 20:57:58 status unpacked libxcb-render-util0 0.3.6-1
2009-10-28 20:57:58 status half-configured libxcb-render-util0 0.3.6-1
2009-10-28 20:57:58 status installed libxcb-render-util0 0.3.6-1
2009-10-28 20:57:58 configure libxrender1 1:0.9.4-2ubuntu1 1:0.9.4-2ubuntu1
2009-10-28 20:57:58 status unpacked libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:57:58 status half-configured libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:57:58 status installed libxrender1 1:0.9.4-2ubuntu1
2009-10-28 20:57:58 configure libcairo2 1.8.8-2ubuntu1 1.8.8-2ubuntu1
2009-10-28 20:57:58 status unpacked libcairo2 1.8.8-2ubuntu1
2009-10-28 20:57:58 status half-configured libcairo2 1.8.8-2ubuntu1
2009-10-28 20:57:58 status installed libcairo2 1.8.8-2ubuntu1
2009-10-28 20:57:58 configure libgstreamer0.10-0 0.10.25-2 0.10.25-2
2009-10-28 20:57:58 status unpacked libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:58 status half-configured libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:58 status installed libgstreamer0.10-0 0.10.25-2
2009-10-28 20:57:58 configure libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1 0.10.25-2ubuntu1
2009-10-28 20:57:58 status unpacked libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:58 status half-configured libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:58 status installed libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1
2009-10-28 20:57:58 configure libgtk2.0-common 2.18.3-1 2.18.3-1
2009-10-28 20:57:58 status unpacked libgtk2.0-common 2.18.3-1
2009-10-28 20:57:58 status half-configured libgtk2.0-common 2.18.3-1
2009-10-28 20:57:58 status installed libgtk2.0-common 2.18.3-1
2009-10-28 20:57:58 configure libatk1.0-0 1.28.0-0ubuntu1 1.28.0-0ubuntu1
2009-10-28 20:57:58 status unpacked libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:57:58 status half-configured libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:57:58 status installed libatk1.0-0 1.28.0-0ubuntu1
2009-10-28 20:57:58 configure libavahi-common-data 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 20:57:58 status unpacked libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:57:58 status half-configured libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:57:58 status installed libavahi-common-data 0.6.25-1ubuntu5
2009-10-28 20:57:58 configure libavahi-common3 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 20:57:58 status unpacked libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:57:58 status half-configured libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:57:58 status installed libavahi-common3 0.6.25-1ubuntu5
2009-10-28 20:57:58 configure libavahi-client3 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 20:57:58 status unpacked libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:57:58 status half-configured libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:57:58 status installed libavahi-client3 0.6.25-1ubuntu5
2009-10-28 20:57:58 configure libcups2 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 20:57:58 status unpacked libcups2 1.4.1-5ubuntu2
2009-10-28 20:57:58 status half-configured libcups2 1.4.1-5ubuntu2
2009-10-28 20:57:58 status installed libcups2 1.4.1-5ubuntu2
2009-10-28 20:57:58 configure libjpeg62 6b-14build1 6b-14build1
2009-10-28 20:57:58 status unpacked libjpeg62 6b-14build1
2009-10-28 20:57:58 status half-configured libjpeg62 6b-14build1
2009-10-28 20:57:58 status installed libjpeg62 6b-14build1
2009-10-28 20:57:58 configure libjasper1 1.900.1-6 1.900.1-6
2009-10-28 20:57:58 status unpacked libjasper1 1.900.1-6
2009-10-28 20:57:58 status half-configured libjasper1 1.900.1-6
2009-10-28 20:57:58 status installed libjasper1 1.900.1-6
2009-10-28 20:57:58 configure fontconfig 2.6.0-1ubuntu12 2.6.0-1ubuntu12
2009-10-28 20:57:58 status unpacked fontconfig 2.6.0-1ubuntu12
2009-10-28 20:57:58 status half-configured fontconfig 2.6.0-1ubuntu12
2009-10-28 20:58:09 status installed fontconfig 2.6.0-1ubuntu12
2009-10-28 20:58:09 configure libpango1.0-common 1.26.0-1 1.26.0-1
2009-10-28 20:58:09 status unpacked libpango1.0-common 1.26.0-1
2009-10-28 20:58:09 status unpacked libpango1.0-common 1.26.0-1
2009-10-28 20:58:09 status half-configured libpango1.0-common 1.26.0-1
2009-10-28 20:58:10 status installed libpango1.0-common 1.26.0-1
2009-10-28 20:58:10 configure libdatrie1 0.2.2-1 0.2.2-1
2009-10-28 20:58:10 status unpacked libdatrie1 0.2.2-1
2009-10-28 20:58:10 status half-configured libdatrie1 0.2.2-1
2009-10-28 20:58:10 status installed libdatrie1 0.2.2-1
2009-10-28 20:58:10 configure libthai-data 0.1.12-1 0.1.12-1
2009-10-28 20:58:10 status unpacked libthai-data 0.1.12-1
2009-10-28 20:58:10 status half-configured libthai-data 0.1.12-1
2009-10-28 20:58:10 status installed libthai-data 0.1.12-1
2009-10-28 20:58:10 configure libthai0 0.1.12-1 0.1.12-1
2009-10-28 20:58:10 status unpacked libthai0 0.1.12-1
2009-10-28 20:58:10 status half-configured libthai0 0.1.12-1
2009-10-28 20:58:10 status installed libthai0 0.1.12-1
2009-10-28 20:58:10 configure libxft2 2.1.13-3ubuntu1 2.1.13-3ubuntu1
2009-10-28 20:58:10 status unpacked libxft2 2.1.13-3ubuntu1
2009-10-28 20:58:10 status half-configured libxft2 2.1.13-3ubuntu1
2009-10-28 20:58:10 status installed libxft2 2.1.13-3ubuntu1
2009-10-28 20:58:10 configure libpango1.0-0 1.26.0-1 1.26.0-1
2009-10-28 20:58:10 status unpacked libpango1.0-0 1.26.0-1
2009-10-28 20:58:10 status half-configured libpango1.0-0 1.26.0-1
2009-10-28 20:58:10 status installed libpango1.0-0 1.26.0-1
2009-10-28 20:58:10 configure libtiff4 3.8.2-13 3.8.2-13
2009-10-28 20:58:10 status unpacked libtiff4 3.8.2-13
2009-10-28 20:58:10 status half-configured libtiff4 3.8.2-13
2009-10-28 20:58:10 status installed libtiff4 3.8.2-13
2009-10-28 20:58:10 configure libxext6 2:1.0.99.1-0ubuntu4 2:1.0.99.1-0ubuntu4
2009-10-28 20:58:10 status unpacked libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:58:10 status half-configured libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:58:10 status installed libxext6 2:1.0.99.1-0ubuntu4
2009-10-28 20:58:10 configure libxfixes3 1:4.0.3-2build1 1:4.0.3-2build1
2009-10-28 20:58:10 status unpacked libxfixes3 1:4.0.3-2build1
2009-10-28 20:58:10 status half-configured libxfixes3 1:4.0.3-2build1
2009-10-28 20:58:10 status installed libxfixes3 1:4.0.3-2build1
2009-10-28 20:58:10 configure libxcomposite1 1:0.4.0-4 1:0.4.0-4
2009-10-28 20:58:10 status unpacked libxcomposite1 1:0.4.0-4
2009-10-28 20:58:10 status half-configured libxcomposite1 1:0.4.0-4
2009-10-28 20:58:10 status installed libxcomposite1 1:0.4.0-4
2009-10-28 20:58:10 configure libxcursor1 1:1.1.9-1build1 1:1.1.9-1build1
2009-10-28 20:58:10 status unpacked libxcursor1 1:1.1.9-1build1
2009-10-28 20:58:10 status half-configured libxcursor1 1:1.1.9-1build1
2009-10-28 20:58:10 status installed libxcursor1 1:1.1.9-1build1
2009-10-28 20:58:10 configure libxdamage1 1:1.1.1-4 1:1.1.1-4
2009-10-28 20:58:10 status unpacked libxdamage1 1:1.1.1-4
2009-10-28 20:58:10 status half-configured libxdamage1 1:1.1.1-4
2009-10-28 20:58:10 status installed libxdamage1 1:1.1.1-4
2009-10-28 20:58:10 configure libxi6 2:1.2.1-2ubuntu1 2:1.2.1-2ubuntu1
2009-10-28 20:58:10 status unpacked libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:58:10 status half-configured libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:58:10 status installed libxi6 2:1.2.1-2ubuntu1
2009-10-28 20:58:10 configure libxinerama1 2:1.0.3-2 2:1.0.3-2
2009-10-28 20:58:10 status unpacked libxinerama1 2:1.0.3-2
2009-10-28 20:58:10 status half-configured libxinerama1 2:1.0.3-2
2009-10-28 20:58:10 status installed libxinerama1 2:1.0.3-2
2009-10-28 20:58:10 configure libxrandr2 2:1.3.0-2 2:1.3.0-2
2009-10-28 20:58:10 status unpacked libxrandr2 2:1.3.0-2
2009-10-28 20:58:10 status half-configured libxrandr2 2:1.3.0-2
2009-10-28 20:58:10 status installed libxrandr2 2:1.3.0-2
2009-10-28 20:58:10 configure libgtk2.0-0 2.18.3-1 2.18.3-1
2009-10-28 20:58:10 status unpacked libgtk2.0-0 2.18.3-1
2009-10-28 20:58:10 status unpacked libgtk2.0-0 2.18.3-1
2009-10-28 20:58:10 status half-configured libgtk2.0-0 2.18.3-1
2009-10-28 20:58:10 status installed libgtk2.0-0 2.18.3-1
2009-10-28 20:58:10 configure libhunspell-1.2-0 1.2.8-4ubuntu2 1.2.8-4ubuntu2
2009-10-28 20:58:10 status unpacked libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:58:10 status half-configured libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:58:10 status installed libhunspell-1.2-0 1.2.8-4ubuntu2
2009-10-28 20:58:10 configure libhyphen0 2.4-4 2.4-4
2009-10-28 20:58:10 status unpacked libhyphen0 2.4-4
2009-10-28 20:58:10 status half-configured libhyphen0 2.4-4
2009-10-28 20:58:10 status installed libhyphen0 2.4-4
2009-10-28 20:58:10 configure libice6 2:1.0.5-1 2:1.0.5-1
2009-10-28 20:58:10 status unpacked libice6 2:1.0.5-1
2009-10-28 20:58:10 status half-configured libice6 2:1.0.5-1
2009-10-28 20:58:10 status installed libice6 2:1.0.5-1
2009-10-28 20:58:10 configure libicu40 4.0.1-2ubuntu2 4.0.1-2ubuntu2
2009-10-28 20:58:10 status unpacked libicu40 4.0.1-2ubuntu2
2009-10-28 20:58:10 status half-configured libicu40 4.0.1-2ubuntu2
2009-10-28 20:58:10 status installed libicu40 4.0.1-2ubuntu2
2009-10-28 20:58:10 configure libneon27-gnutls 0.28.6-1 0.28.6-1
2009-10-28 20:58:10 status unpacked libneon27-gnutls 0.28.6-1
2009-10-28 20:58:10 status half-configured libneon27-gnutls 0.28.6-1
2009-10-28 20:58:10 status installed libneon27-gnutls 0.28.6-1
2009-10-28 20:58:10 configure libnspr4-0d 4.8-0ubuntu1 4.8-0ubuntu1
2009-10-28 20:58:10 status unpacked libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:58:10 status half-configured libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:58:10 status installed libnspr4-0d 4.8-0ubuntu1
2009-10-28 20:58:10 configure libnss3-1d 3.12.3.1-0ubuntu2 3.12.3.1-0ubuntu2
2009-10-28 20:58:10 status unpacked libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:58:10 status half-configured libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:58:10 status installed libnss3-1d 3.12.3.1-0ubuntu2
2009-10-28 20:58:10 configure mysql-common 5.1.37-1ubuntu5 5.1.37-1ubuntu5
2009-10-28 20:58:10 status unpacked mysql-common 5.1.37-1ubuntu5
2009-10-28 20:58:10 status unpacked mysql-common 5.1.37-1ubuntu5
2009-10-28 20:58:10 status half-configured mysql-common 5.1.37-1ubuntu5
2009-10-28 20:58:10 status installed mysql-common 5.1.37-1ubuntu5
2009-10-28 20:58:10 configure libmysqlclient16 5.1.37-1ubuntu5 5.1.37-1ubuntu5
2009-10-28 20:58:10 status unpacked libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:58:10 status half-configured libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:58:10 status installed libmysqlclient16 5.1.37-1ubuntu5
2009-10-28 20:58:10 configure libpq5 8.4.1-1 8.4.1-1
2009-10-28 20:58:10 status unpacked libpq5 8.4.1-1
2009-10-28 20:58:10 status half-configured libpq5 8.4.1-1
2009-10-28 20:58:10 status installed libpq5 8.4.1-1
2009-10-28 20:58:10 configure libxslt1.1 1.1.24-2ubuntu2 1.1.24-2ubuntu2
2009-10-28 20:58:10 status unpacked libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:58:10 status half-configured libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:58:10 status installed libxslt1.1 1.1.24-2ubuntu2
2009-10-28 20:58:10 configure libraptor1 1.4.19-1 1.4.19-1
2009-10-28 20:58:10 status unpacked libraptor1 1.4.19-1
2009-10-28 20:58:10 status half-configured libraptor1 1.4.19-1
2009-10-28 20:58:10 status installed libraptor1 1.4.19-1
2009-10-28 20:58:10 configure libgmp3c2 2:4.3.1+dfsg-1ubuntu3 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:58:10 status unpacked libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:58:10 status half-configured libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:58:10 status installed libgmp3c2 2:4.3.1+dfsg-1ubuntu3
2009-10-28 20:58:10 configure librasqal1 0.9.16-1 0.9.16-1
2009-10-28 20:58:10 status unpacked librasqal1 0.9.16-1
2009-10-28 20:58:10 status half-configured librasqal1 0.9.16-1
2009-10-28 20:58:10 status installed librasqal1 0.9.16-1
2009-10-28 20:58:10 configure librdf0 1.0.9-2 1.0.9-2
2009-10-28 20:58:10 status unpacked librdf0 1.0.9-2
2009-10-28 20:58:10 status half-configured librdf0 1.0.9-2
2009-10-28 20:58:10 status installed librdf0 1.0.9-2
2009-10-28 20:58:10 configure libsm6 2:1.1.0-2 2:1.1.0-2
2009-10-28 20:58:10 status unpacked libsm6 2:1.1.0-2
2009-10-28 20:58:10 status half-configured libsm6 2:1.1.0-2
2009-10-28 20:58:10 status installed libsm6 2:1.1.0-2
2009-10-28 20:58:10 configure libstlport4.6ldbl 4.6.2-5build1 4.6.2-5build1
2009-10-28 20:58:10 status unpacked libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:58:10 status half-configured libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:58:10 status installed libstlport4.6ldbl 4.6.2-5build1
2009-10-28 20:58:10 configure libxt6 1:1.0.5-3ubuntu1 1:1.0.5-3ubuntu1
2009-10-28 20:58:10 status unpacked libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:58:10 status half-configured libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:58:10 status installed libxt6 1:1.0.5-3ubuntu1
2009-10-28 20:58:10 configure libxmu6 2:1.0.4-2 2:1.0.4-2
2009-10-28 20:58:10 status unpacked libxmu6 2:1.0.4-2
2009-10-28 20:58:10 status half-configured libxmu6 2:1.0.4-2
2009-10-28 20:58:10 status installed libxmu6 2:1.0.4-2
2009-10-28 20:58:10 configure libxpm4 1:3.5.7-2 1:3.5.7-2
2009-10-28 20:58:10 status unpacked libxpm4 1:3.5.7-2
2009-10-28 20:58:10 status half-configured libxpm4 1:3.5.7-2
2009-10-28 20:58:10 status installed libxpm4 1:3.5.7-2
2009-10-28 20:58:10 configure libxaw7 2:1.0.6-1 2:1.0.6-1
2009-10-28 20:58:10 status unpacked libxaw7 2:1.0.6-1
2009-10-28 20:58:10 status half-configured libxaw7 2:1.0.6-1
2009-10-28 20:58:10 status installed libxaw7 2:1.0.6-1
2009-10-28 20:58:10 configure libxtst6 2:1.0.3-1ubuntu2 2:1.0.3-1ubuntu2
2009-10-28 20:58:10 status unpacked libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:58:10 status half-configured libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:58:10 status installed libxtst6 2:1.0.3-1ubuntu2
2009-10-28 20:58:10 configure uno-libs3 1.5.1+OOo3.1.1-5ubuntu1 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status unpacked uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status half-configured uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status installed uno-libs3 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 configure ure 1.5.1+OOo3.1.1-5ubuntu1 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status unpacked ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status half-configured ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 status installed ure 1.5.1+OOo3.1.1-5ubuntu1
2009-10-28 20:58:10 configure openoffice.org-core 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 20:58:10 status unpacked openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:58:10 status half-configured openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:58:10 status installed openoffice.org-core 1:3.1.1-5ubuntu1
2009-10-28 20:58:10 configure libpython2.6 2.6.4~rc2-0ubuntu1 2.6.4~rc2-0ubuntu1
2009-10-28 20:58:10 status unpacked libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:58:10 status half-configured libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:58:11 status installed libpython2.6 2.6.4~rc2-0ubuntu1
2009-10-28 20:58:11 configure python-uno 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status unpacked python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status half-configured python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status installed python-uno 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 20:58:11 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 20:58:11 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 20:58:11 startup archives unpack
2009-10-28 20:58:11 install openoffice.org-emailmerge <none> 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status half-installed openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status unpacked openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 status unpacked openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 20:58:11 install ttf-wqy-zenhei <none> 0.8.38-1ubuntu1
2009-10-28 20:58:11 status half-installed ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 20:58:13 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 20:58:13 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 20:58:13 install xulrunner-1.9.1 <none> 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:58:13 status half-installed xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:58:14 status unpacked xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:58:14 status unpacked xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:58:14 install python-libxml2 <none> 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status half-installed python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status unpacked python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status unpacked python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 install libxml2-utils <none> 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status half-installed libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status unpacked libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 status unpacked libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 20:58:14 install xsltproc <none> 1.1.24-2ubuntu2
2009-10-28 20:58:14 status half-installed xsltproc 1.1.24-2ubuntu2
2009-10-28 20:58:14 status unpacked xsltproc 1.1.24-2ubuntu2
2009-10-28 20:58:14 status unpacked xsltproc 1.1.24-2ubuntu2
2009-10-28 20:58:14 install gnome-doc-utils <none> 0.18.0-0ubuntu1
2009-10-28 20:58:14 status half-installed gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 20:58:15 status unpacked gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 20:58:15 status unpacked gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 20:58:15 install groff-base <none> 1.20.1-5
2009-10-28 20:58:15 status half-installed groff-base 1.20.1-5
2009-10-28 20:58:15 status unpacked groff-base 1.20.1-5
2009-10-28 20:58:15 status unpacked groff-base 1.20.1-5
2009-10-28 20:58:15 install bsdmainutils <none> 6.1.10ubuntu4
2009-10-28 20:58:15 status half-installed bsdmainutils 6.1.10ubuntu4
2009-10-28 20:58:15 status unpacked bsdmainutils 6.1.10ubuntu4
2009-10-28 20:58:15 status unpacked bsdmainutils 6.1.10ubuntu4
2009-10-28 20:58:15 install man-db <none> 2.5.6-2
2009-10-28 20:58:15 status half-installed man-db 2.5.6-2
2009-10-28 20:58:15 status unpacked man-db 2.5.6-2
2009-10-28 20:58:15 status unpacked man-db 2.5.6-2
2009-10-28 20:58:15 install yelp <none> 2.28.0-0ubuntu2
2009-10-28 20:58:15 status half-installed yelp 2.28.0-0ubuntu2
2009-10-28 20:58:15 status unpacked yelp 2.28.0-0ubuntu2
2009-10-28 20:58:15 status unpacked yelp 2.28.0-0ubuntu2
2009-10-28 20:58:15 install gnome-user-guide <none> 2.28.0+git20090921ubuntu2
2009-10-28 20:58:15 status half-installed gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 20:58:16 status unpacked gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 20:58:16 status unpacked gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 20:58:16 install ubuntu-docs <none> 9.10.11
2009-10-28 20:58:16 status half-installed ubuntu-docs 9.10.11
2009-10-28 20:58:19 status unpacked ubuntu-docs 9.10.11
2009-10-28 20:58:19 status unpacked ubuntu-docs 9.10.11
2009-10-28 20:58:19 install x11-apps <none> 7.4+2
2009-10-28 20:58:19 status half-installed x11-apps 7.4+2
2009-10-28 20:58:19 status unpacked x11-apps 7.4+2
2009-10-28 20:58:19 status unpacked x11-apps 7.4+2
2009-10-28 20:58:19 install x11-session-utils <none> 7.3+1build1
2009-10-28 20:58:19 status half-installed x11-session-utils 7.3+1build1
2009-10-28 20:58:19 status unpacked x11-session-utils 7.3+1build1
2009-10-28 20:58:19 status unpacked x11-session-utils 7.3+1build1
2009-10-28 20:58:19 install libfontenc1 <none> 1:1.0.4-3
2009-10-28 20:58:19 status half-installed libfontenc1 1:1.0.4-3
2009-10-28 20:58:19 status unpacked libfontenc1 1:1.0.4-3
2009-10-28 20:58:19 status unpacked libfontenc1 1:1.0.4-3
2009-10-28 20:58:19 install libdrm2 <none> 2.4.14-1ubuntu1
2009-10-28 20:58:19 status half-installed libdrm2 2.4.14-1ubuntu1
2009-10-28 20:58:19 status unpacked libdrm2 2.4.14-1ubuntu1
2009-10-28 20:58:19 status unpacked libdrm2 2.4.14-1ubuntu1
2009-10-28 20:58:19 install libxxf86vm1 <none> 1:1.0.2-1ubuntu1
2009-10-28 20:58:19 status half-installed libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 20:58:19 status unpacked libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 20:58:19 status unpacked libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 20:58:20 install libgl1-mesa-glx <none> 7.6.0-1ubuntu4
2009-10-28 20:58:20 status half-installed libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 20:58:20 status unpacked libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 20:58:20 status unpacked libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 20:58:20 install libxv1 <none> 2:1.0.4-1
2009-10-28 20:58:20 status half-installed libxv1 2:1.0.4-1
2009-10-28 20:58:20 status unpacked libxv1 2:1.0.4-1
2009-10-28 20:58:20 status unpacked libxv1 2:1.0.4-1
2009-10-28 20:58:20 install libxxf86dga1 <none> 2:1.0.2-1build1
2009-10-28 20:58:20 status half-installed libxxf86dga1 2:1.0.2-1build1
2009-10-28 20:58:20 status unpacked libxxf86dga1 2:1.0.2-1build1
2009-10-28 20:58:20 status unpacked libxxf86dga1 2:1.0.2-1build1
2009-10-28 20:58:20 install x11-utils <none> 7.4+1build1
2009-10-28 20:58:20 status half-installed x11-utils 7.4+1build1
2009-10-28 20:58:20 status unpacked x11-utils 7.4+1build1
2009-10-28 20:58:20 status unpacked x11-utils 7.4+1build1
2009-10-28 20:58:20 install libfs6 <none> 2:1.0.2-1
2009-10-28 20:58:20 status half-installed libfs6 2:1.0.2-1
2009-10-28 20:58:20 status unpacked libfs6 2:1.0.2-1
2009-10-28 20:58:20 status unpacked libfs6 2:1.0.2-1
2009-10-28 20:58:20 install x11-xfs-utils <none> 7.4+1build1
2009-10-28 20:58:20 status half-installed x11-xfs-utils 7.4+1build1
2009-10-28 20:58:20 status unpacked x11-xfs-utils 7.4+1build1
2009-10-28 20:58:20 status unpacked x11-xfs-utils 7.4+1build1
2009-10-28 20:58:20 install libxtrap6 <none> 2:1.0.0-5build1
2009-10-28 20:58:20 status half-installed libxtrap6 2:1.0.0-5build1
2009-10-28 20:58:20 status unpacked libxtrap6 2:1.0.0-5build1
2009-10-28 20:58:20 status unpacked libxtrap6 2:1.0.0-5build1
2009-10-28 20:58:20 install x11-xserver-utils <none> 7.4+2ubuntu3
2009-10-28 20:58:20 status half-installed x11-xserver-utils 7.4+2ubuntu3
2009-10-28 20:58:20 status unpacked x11-xserver-utils 7.4+2ubuntu3
2009-10-28 20:58:20 status unpacked x11-xserver-utils 7.4+2ubuntu3
2009-10-28 20:58:20 install xbitmaps <none> 1.0.1-2ubuntu1
2009-10-28 20:58:20 status half-installed xbitmaps 1.0.1-2ubuntu1
2009-10-28 20:58:20 status unpacked xbitmaps 1.0.1-2ubuntu1
2009-10-28 20:58:20 status unpacked xbitmaps 1.0.1-2ubuntu1
2009-10-28 20:58:20 install apparmor <none> 2.3.1+1403-0ubuntu27
2009-10-28 20:58:20 status half-installed apparmor 2.3.1+1403-0ubuntu27
2009-10-28 20:58:21 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 20:58:21 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 20:58:21 install libterm-readkey-perl <none> 2.30-4
2009-10-28 20:58:21 status half-installed libterm-readkey-perl 2.30-4
2009-10-28 20:58:21 status unpacked libterm-readkey-perl 2.30-4
2009-10-28 20:58:21 status unpacked libterm-readkey-perl 2.30-4
2009-10-28 20:58:21 install liburi-perl <none> 1.37+dfsg-1ubuntu1
2009-10-28 20:58:21 status half-installed liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 20:58:22 status unpacked liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 20:58:22 status unpacked liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 20:58:22 install libhtml-tagset-perl <none> 3.20-2
2009-10-28 20:58:22 status half-installed libhtml-tagset-perl 3.20-2
2009-10-28 20:58:22 status unpacked libhtml-tagset-perl 3.20-2
2009-10-28 20:58:22 status unpacked libhtml-tagset-perl 3.20-2
2009-10-28 20:58:22 install libhtml-parser-perl <none> 3.61-1
2009-10-28 20:58:22 status half-installed libhtml-parser-perl 3.61-1
2009-10-28 20:58:22 status unpacked libhtml-parser-perl 3.61-1
2009-10-28 20:58:22 status unpacked libhtml-parser-perl 3.61-1
2009-10-28 20:58:22 install libhtml-tree-perl <none> 3.23-1
2009-10-28 20:58:22 status half-installed libhtml-tree-perl 3.23-1
2009-10-28 20:58:22 status unpacked libhtml-tree-perl 3.23-1
2009-10-28 20:58:22 status unpacked libhtml-tree-perl 3.23-1
2009-10-28 20:58:22 install libwww-perl <none> 5.831-1
2009-10-28 20:58:22 status half-installed libwww-perl 5.831-1
2009-10-28 20:58:22 status unpacked libwww-perl 5.831-1
2009-10-28 20:58:22 status unpacked libwww-perl 5.831-1
2009-10-28 20:58:22 install libxml-parser-perl <none> 2.36-1.1build2
2009-10-28 20:58:22 status half-installed libxml-parser-perl 2.36-1.1build2
2009-10-28 20:58:22 status unpacked libxml-parser-perl 2.36-1.1build2
2009-10-28 20:58:22 status unpacked libxml-parser-perl 2.36-1.1build2
2009-10-28 20:58:23 install librpc-xml-perl <none> 0.64-1
2009-10-28 20:58:23 status half-installed librpc-xml-perl 0.64-1
2009-10-28 20:58:23 status unpacked librpc-xml-perl 0.64-1
2009-10-28 20:58:23 status unpacked librpc-xml-perl 0.64-1
2009-10-28 20:58:23 install libapparmor1 <none> 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status half-installed libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 install libapparmor-perl <none> 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status half-installed libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 install apparmor-utils <none> 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status half-installed apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 status unpacked apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 20:58:23 install apt-transport-https <none> 0.7.23.1ubuntu2
2009-10-28 20:58:23 status half-installed apt-transport-https 0.7.23.1ubuntu2
2009-10-28 20:58:23 status unpacked apt-transport-https 0.7.23.1ubuntu2
2009-10-28 20:58:23 status unpacked apt-transport-https 0.7.23.1ubuntu2
2009-10-28 20:58:23 install at <none> 3.1.11-1ubuntu4
2009-10-28 20:58:23 status half-installed at 3.1.11-1ubuntu4
2009-10-28 20:58:23 status unpacked at 3.1.11-1ubuntu4
2009-10-28 20:58:23 status unpacked at 3.1.11-1ubuntu4
2009-10-28 20:58:23 install bash-completion <none> 1:1.0-3ubuntu2
2009-10-28 20:58:23 status half-installed bash-completion 1:1.0-3ubuntu2
2009-10-28 20:58:23 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 20:58:23 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 20:58:23 install libgeoip1 <none> 1.4.6.dfsg-5
2009-10-28 20:58:23 status half-installed libgeoip1 1.4.6.dfsg-5
2009-10-28 20:58:23 status unpacked libgeoip1 1.4.6.dfsg-5
2009-10-28 20:58:23 status unpacked libgeoip1 1.4.6.dfsg-5
2009-10-28 20:58:23 install libisc50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status half-installed libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 install libdns50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status half-installed libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 install libisccc50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status half-installed libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:23 status unpacked libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install libisccfg50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status half-installed libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install libbind9-50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status half-installed libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install liblwres50 <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status half-installed liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install bind9-host <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status half-installed bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install command-not-found-data <none> 0.2.38ubuntu4
2009-10-28 20:58:24 status half-installed command-not-found-data 0.2.38ubuntu4
2009-10-28 20:58:24 status unpacked command-not-found-data 0.2.38ubuntu4
2009-10-28 20:58:24 status unpacked command-not-found-data 0.2.38ubuntu4
2009-10-28 20:58:24 install python-gdbm <none> 2.6.3-0ubuntu1
2009-10-28 20:58:24 status half-installed python-gdbm 2.6.3-0ubuntu1
2009-10-28 20:58:24 status unpacked python-gdbm 2.6.3-0ubuntu1
2009-10-28 20:58:24 status unpacked python-gdbm 2.6.3-0ubuntu1
2009-10-28 20:58:24 install command-not-found <none> 0.2.38ubuntu4
2009-10-28 20:58:24 status half-installed command-not-found 0.2.38ubuntu4
2009-10-28 20:58:24 status unpacked command-not-found 0.2.38ubuntu4
2009-10-28 20:58:24 status unpacked command-not-found 0.2.38ubuntu4
2009-10-28 20:58:24 install cron <none> 3.0pl1-106ubuntu3
2009-10-28 20:58:24 status half-installed cron 3.0pl1-106ubuntu3
2009-10-28 20:58:24 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 20:58:24 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 20:58:24 install dnsutils <none> 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status half-installed dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 status unpacked dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 20:58:24 install dosfstools <none> 3.0.3-1
2009-10-28 20:58:24 status half-installed dosfstools 3.0.3-1
2009-10-28 20:58:24 status unpacked dosfstools 3.0.3-1
2009-10-28 20:58:24 status unpacked dosfstools 3.0.3-1
2009-10-28 20:58:24 install ed <none> 1.4-1
2009-10-28 20:58:24 status half-installed ed 1.4-1
2009-10-28 20:58:25 status unpacked ed 1.4-1
2009-10-28 20:58:25 status unpacked ed 1.4-1
2009-10-28 20:58:25 install friendly-recovery <none> 0.2.8.2
2009-10-28 20:58:25 status half-installed friendly-recovery 0.2.8.2
2009-10-28 20:58:25 status unpacked friendly-recovery 0.2.8.2
2009-10-28 20:58:25 status unpacked friendly-recovery 0.2.8.2
2009-10-28 20:58:25 install ftp <none> 0.17-19
2009-10-28 20:58:25 status half-installed ftp 0.17-19
2009-10-28 20:58:25 status unpacked ftp 0.17-19
2009-10-28 20:58:25 status unpacked ftp 0.17-19
2009-10-28 20:58:25 install geoip-database <none> 1.4.6.dfsg-5
2009-10-28 20:58:25 status half-installed geoip-database 1.4.6.dfsg-5
2009-10-28 20:58:25 status unpacked geoip-database 1.4.6.dfsg-5
2009-10-28 20:58:25 status unpacked geoip-database 1.4.6.dfsg-5
2009-10-28 20:58:25 install gettext-base <none> 0.17-8ubuntu2
2009-10-28 20:58:25 status half-installed gettext-base 0.17-8ubuntu2
2009-10-28 20:58:25 status unpacked gettext-base 0.17-8ubuntu2
2009-10-28 20:58:25 status unpacked gettext-base 0.17-8ubuntu2
2009-10-28 20:58:25 install hdparm <none> 9.15-1ubuntu4
2009-10-28 20:58:25 status half-installed hdparm 9.15-1ubuntu4
2009-10-28 20:58:25 status unpacked hdparm 9.15-1ubuntu4
2009-10-28 20:58:25 status unpacked hdparm 9.15-1ubuntu4
2009-10-28 20:58:25 install install-info <none> 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status half-installed install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status unpacked install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status unpacked install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 install info <none> 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status half-installed info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status unpacked info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 status unpacked info 4.13a.dfsg.1-4ubuntu1
2009-10-28 20:58:25 install iptables <none> 1.4.4-1ubuntu1
2009-10-28 20:58:25 status half-installed iptables 1.4.4-1ubuntu1
2009-10-28 20:58:25 status unpacked iptables 1.4.4-1ubuntu1
2009-10-28 20:58:25 status unpacked iptables 1.4.4-1ubuntu1
2009-10-28 20:58:25 install iputils-arping <none> 3:20071127-1build1
2009-10-28 20:58:25 status half-installed iputils-arping 3:20071127-1build1
2009-10-28 20:58:26 status unpacked iputils-arping 3:20071127-1build1
2009-10-28 20:58:26 status unpacked iputils-arping 3:20071127-1build1
2009-10-28 20:58:26 install iputils-tracepath <none> 3:20071127-1build1
2009-10-28 20:58:26 status half-installed iputils-tracepath 3:20071127-1build1
2009-10-28 20:58:26 status unpacked iputils-tracepath 3:20071127-1build1
2009-10-28 20:58:26 status unpacked iputils-tracepath 3:20071127-1build1
2009-10-28 20:58:26 install iso-codes <none> 3.10.2-1
2009-10-28 20:58:26 status half-installed iso-codes 3.10.2-1
2009-10-28 20:58:27 status unpacked iso-codes 3.10.2-1
2009-10-28 20:58:27 status unpacked iso-codes 3.10.2-1
2009-10-28 20:58:27 install libbsd0 <none> 0.1.4-1
2009-10-28 20:58:27 status half-installed libbsd0 0.1.4-1
2009-10-28 20:58:27 status unpacked libbsd0 0.1.4-1
2009-10-28 20:58:27 status unpacked libbsd0 0.1.4-1
2009-10-28 20:58:27 install libcompress-bzip2-perl <none> 2.09-2
2009-10-28 20:58:27 status half-installed libcompress-bzip2-perl 2.09-2
2009-10-28 20:58:27 status unpacked libcompress-bzip2-perl 2.09-2
2009-10-28 20:58:27 status unpacked libcompress-bzip2-perl 2.09-2
2009-10-28 20:58:28 install libedit2 <none> 2.11-20080614-1
2009-10-28 20:58:28 status half-installed libedit2 2.11-20080614-1
2009-10-28 20:58:28 status unpacked libedit2 2.11-20080614-1
2009-10-28 20:58:28 status unpacked libedit2 2.11-20080614-1
2009-10-28 20:58:28 install libelf1 <none> 0.141-2ubuntu2
2009-10-28 20:58:28 status half-installed libelf1 0.141-2ubuntu2
2009-10-28 20:58:28 status unpacked libelf1 0.141-2ubuntu2
2009-10-28 20:58:28 status unpacked libelf1 0.141-2ubuntu2
2009-10-28 20:58:28 install libfont-afm-perl <none> 1.20-1
2009-10-28 20:58:28 status half-installed libfont-afm-perl 1.20-1
2009-10-28 20:58:28 status unpacked libfont-afm-perl 1.20-1
2009-10-28 20:58:28 status unpacked libfont-afm-perl 1.20-1
2009-10-28 20:58:28 install libgc1c2 <none> 1:6.8-1.2
2009-10-28 20:58:28 status half-installed libgc1c2 1:6.8-1.2
2009-10-28 20:58:28 status unpacked libgc1c2 1:6.8-1.2
2009-10-28 20:58:28 status unpacked libgc1c2 1:6.8-1.2
2009-10-28 20:58:28 install libhtml-format-perl <none> 2.04-2
2009-10-28 20:58:28 status half-installed libhtml-format-perl 2.04-2
2009-10-28 20:58:28 status unpacked libhtml-format-perl 2.04-2
2009-10-28 20:58:28 status unpacked libhtml-format-perl 2.04-2
2009-10-28 20:58:28 install libjs-jquery <none> 1.3.3-1ubuntu1
2009-10-28 20:58:28 status half-installed libjs-jquery 1.3.3-1ubuntu1
2009-10-28 20:58:28 status unpacked libjs-jquery 1.3.3-1ubuntu1
2009-10-28 20:58:28 status unpacked libjs-jquery 1.3.3-1ubuntu1
2009-10-28 20:58:28 install libmailtools-perl <none> 2.04-1
2009-10-28 20:58:28 status half-installed libmailtools-perl 2.04-1
2009-10-28 20:58:28 status unpacked libmailtools-perl 2.04-1
2009-10-28 20:58:28 status unpacked libmailtools-perl 2.04-1
2009-10-28 20:58:28 install libpcap0.8 <none> 1.0.0-2ubuntu1
2009-10-28 20:58:28 status half-installed libpcap0.8 1.0.0-2ubuntu1
2009-10-28 20:58:28 status unpacked libpcap0.8 1.0.0-2ubuntu1
2009-10-28 20:58:28 status unpacked libpcap0.8 1.0.0-2ubuntu1
2009-10-28 20:58:28 install libpci3 <none> 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status half-installed libpci3 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status unpacked libpci3 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status unpacked libpci3 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 install anacron <none> 2.3-13.1ubuntu10
2009-10-28 20:58:28 status half-installed anacron 2.3-13.1ubuntu10
2009-10-28 20:58:28 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 20:58:28 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 20:58:28 install logrotate <none> 3.7.8-4ubuntu1
2009-10-28 20:58:28 status half-installed logrotate 3.7.8-4ubuntu1
2009-10-28 20:58:28 status unpacked logrotate 3.7.8-4ubuntu1
2009-10-28 20:58:28 status unpacked logrotate 3.7.8-4ubuntu1
2009-10-28 20:58:28 install pciutils <none> 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status half-installed pciutils 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status unpacked pciutils 1:3.0.0-4ubuntu13
2009-10-28 20:58:28 status unpacked pciutils 1:3.0.0-4ubuntu13
2009-10-28 20:58:29 install usbutils <none> 0.82-0ubuntu1
2009-10-28 20:58:29 status half-installed usbutils 0.82-0ubuntu1
2009-10-28 20:58:29 status unpacked usbutils 0.82-0ubuntu1
2009-10-28 20:58:29 status unpacked usbutils 0.82-0ubuntu1
2009-10-28 20:58:29 install lshw <none> 02.14-1
2009-10-28 20:58:29 status half-installed lshw 02.14-1
2009-10-28 20:58:29 status unpacked lshw 02.14-1
2009-10-28 20:58:29 status unpacked lshw 02.14-1
2009-10-28 20:58:29 install lsof <none> 4.81.dfsg.1-1
2009-10-28 20:58:29 status half-installed lsof 4.81.dfsg.1-1
2009-10-28 20:58:29 status unpacked lsof 4.81.dfsg.1-1
2009-10-28 20:58:29 status unpacked lsof 4.81.dfsg.1-1
2009-10-28 20:58:29 install ltrace <none> 0.5.3-2ubuntu2
2009-10-28 20:58:29 status half-installed ltrace 0.5.3-2ubuntu2
2009-10-28 20:58:29 status unpacked ltrace 0.5.3-2ubuntu2
2009-10-28 20:58:29 status unpacked ltrace 0.5.3-2ubuntu2
2009-10-28 20:58:29 install manpages <none> 3.21-1
2009-10-28 20:58:29 status half-installed manpages 3.21-1
2009-10-28 20:58:29 status unpacked manpages 3.21-1
2009-10-28 20:58:29 status unpacked manpages 3.21-1
2009-10-28 20:58:29 install memtest86+ <none> 2.11-3ubuntu5
2009-10-28 20:58:29 status half-installed memtest86+ 2.11-3ubuntu5
2009-10-28 20:58:29 status unpacked memtest86+ 2.11-3ubuntu5
2009-10-28 20:58:29 status unpacked memtest86+ 2.11-3ubuntu5
2009-10-28 20:58:29 install mlocate <none> 0.21.1-2
2009-10-28 20:58:29 status half-installed mlocate 0.21.1-2
2009-10-28 20:58:29 status unpacked mlocate 0.21.1-2
2009-10-28 20:58:29 status unpacked mlocate 0.21.1-2
2009-10-28 20:58:29 install mtr-tiny <none> 0.75-2
2009-10-28 20:58:29 status half-installed mtr-tiny 0.75-2
2009-10-28 20:58:29 status unpacked mtr-tiny 0.75-2
2009-10-28 20:58:29 status unpacked mtr-tiny 0.75-2
2009-10-28 20:58:29 install nano <none> 2.0.9-2
2009-10-28 20:58:29 status half-installed nano 2.0.9-2
2009-10-28 20:58:29 status unpacked nano 2.0.9-2
2009-10-28 20:58:29 status unpacked nano 2.0.9-2
2009-10-28 20:58:29 install openssh-client <none> 1:5.1p1-6ubuntu2
2009-10-28 20:58:29 status half-installed openssh-client 1:5.1p1-6ubuntu2
2009-10-28 20:58:30 status unpacked openssh-client 1:5.1p1-6ubuntu2
2009-10-28 20:58:30 status unpacked openssh-client 1:5.1p1-6ubuntu2
2009-10-28 20:58:30 install parted <none> 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:58:30 status half-installed parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:58:30 status unpacked parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:58:30 status unpacked parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 20:58:30 install popularity-contest <none> 1.48ubuntu1
2009-10-28 20:58:30 status half-installed popularity-contest 1.48ubuntu1
2009-10-28 20:58:30 status unpacked popularity-contest 1.48ubuntu1
2009-10-28 20:58:30 status unpacked popularity-contest 1.48ubuntu1
2009-10-28 20:58:30 install powermgmt-base <none> 1.30+nmu1
2009-10-28 20:58:30 status half-installed powermgmt-base 1.30+nmu1
2009-10-28 20:58:30 status unpacked powermgmt-base 1.30+nmu1
2009-10-28 20:58:30 status unpacked powermgmt-base 1.30+nmu1
2009-10-28 20:58:30 install ppp <none> 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 20:58:30 status half-installed ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 20:58:30 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 20:58:30 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 20:58:30 install pppconfig <none> 2.3.18ubuntu2
2009-10-28 20:58:30 status half-installed pppconfig 2.3.18ubuntu2
2009-10-28 20:58:30 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 20:58:30 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 20:58:30 install pppoeconf <none> 1.18ubuntu1
2009-10-28 20:58:30 status half-installed pppoeconf 1.18ubuntu1
2009-10-28 20:58:30 status unpacked pppoeconf 1.18ubuntu1
2009-10-28 20:58:30 status unpacked pppoeconf 1.18ubuntu1
2009-10-28 20:58:30 install python-gnupginterface <none> 0.3.2-9ubuntu2
2009-10-28 20:58:30 status half-installed python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 20:58:30 status unpacked python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 20:58:30 status unpacked python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 20:58:30 install rsync <none> 3.0.6-1ubuntu1
2009-10-28 20:58:30 status half-installed rsync 3.0.6-1ubuntu1
2009-10-28 20:58:30 status unpacked rsync 3.0.6-1ubuntu1
2009-10-28 20:58:30 status unpacked rsync 3.0.6-1ubuntu1
2009-10-28 20:58:30 install strace <none> 4.5.18-1ubuntu2
2009-10-28 20:58:30 status half-installed strace 4.5.18-1ubuntu2
2009-10-28 20:58:30 status unpacked strace 4.5.18-1ubuntu2
2009-10-28 20:58:30 status unpacked strace 4.5.18-1ubuntu2
2009-10-28 20:58:30 install tcpdump <none> 4.0.0-2ubuntu2
2009-10-28 20:58:30 status half-installed tcpdump 4.0.0-2ubuntu2
2009-10-28 20:58:30 status unpacked tcpdump 4.0.0-2ubuntu2
2009-10-28 20:58:30 status unpacked tcpdump 4.0.0-2ubuntu2
2009-10-28 20:58:31 install telnet <none> 0.17-36
2009-10-28 20:58:31 status half-installed telnet 0.17-36
2009-10-28 20:58:31 status unpacked telnet 0.17-36
2009-10-28 20:58:31 status unpacked telnet 0.17-36
2009-10-28 20:58:31 install time <none> 1.7-23
2009-10-28 20:58:31 status half-installed time 1.7-23
2009-10-28 20:58:31 status unpacked time 1.7-23
2009-10-28 20:58:31 status unpacked time 1.7-23
2009-10-28 20:58:31 install ubuntu-standard <none> 1.175
2009-10-28 20:58:31 status half-installed ubuntu-standard 1.175
2009-10-28 20:58:31 status unpacked ubuntu-standard 1.175
2009-10-28 20:58:31 status unpacked ubuntu-standard 1.175
2009-10-28 20:58:31 install ufw <none> 0.29-4ubuntu1
2009-10-28 20:58:31 status half-installed ufw 0.29-4ubuntu1
2009-10-28 20:58:31 status unpacked ufw 0.29-4ubuntu1
2009-10-28 20:58:31 status unpacked ufw 0.29-4ubuntu1
2009-10-28 20:58:31 install update-manager-core <none> 1:0.126.6
2009-10-28 20:58:31 status half-installed update-manager-core 1:0.126.6
2009-10-28 20:58:31 status unpacked update-manager-core 1:0.126.6
2009-10-28 20:58:31 status unpacked update-manager-core 1:0.126.6
2009-10-28 20:58:31 install uuid-runtime <none> 2.16-1ubuntu5
2009-10-28 20:58:31 status half-installed uuid-runtime 2.16-1ubuntu5
2009-10-28 20:58:31 status unpacked uuid-runtime 2.16-1ubuntu5
2009-10-28 20:58:31 status unpacked uuid-runtime 2.16-1ubuntu5
2009-10-28 20:58:31 install w3m <none> 0.5.2-2ubuntu1
2009-10-28 20:58:31 status half-installed w3m 0.5.2-2ubuntu1
2009-10-28 20:58:31 status unpacked w3m 0.5.2-2ubuntu1
2009-10-28 20:58:31 status unpacked w3m 0.5.2-2ubuntu1
2009-10-28 20:58:31 install laptop-mode-tools <none> 1.47-1ubuntu2
2009-10-28 20:58:31 status half-installed laptop-mode-tools 1.47-1ubuntu2
2009-10-28 20:58:31 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 20:58:31 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 20:58:31 install acpid <none> 1.0.6-9ubuntu8
2009-10-28 20:58:31 status half-installed acpid 1.0.6-9ubuntu8
2009-10-28 20:58:31 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 20:58:31 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 20:58:31 install finger <none> 0.17-13
2009-10-28 20:58:31 status half-installed finger 0.17-13
2009-10-28 20:58:32 status unpacked finger 0.17-13
2009-10-28 20:58:32 status unpacked finger 0.17-13
2009-10-28 20:58:32 install pm-utils <none> 1.2.5-2ubuntu7
2009-10-28 20:58:32 status half-installed pm-utils 1.2.5-2ubuntu7
2009-10-28 20:58:32 status unpacked pm-utils 1.2.5-2ubuntu7
2009-10-28 20:58:32 status unpacked pm-utils 1.2.5-2ubuntu7
2009-10-28 20:58:32 install acpi-support <none> 0.129
2009-10-28 20:58:32 status half-installed acpi-support 0.129
2009-10-28 20:58:32 status unpacked acpi-support 0.129
2009-10-28 20:58:32 status unpacked acpi-support 0.129
2009-10-28 20:58:32 install guile-1.8-libs <none> 1.8.7+1-1ubuntu3
2009-10-28 20:58:32 status half-installed guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 20:58:32 status unpacked guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 20:58:32 status unpacked guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 20:58:32 install gnome-games-common <none> 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status half-installed gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status unpacked gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status unpacked gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 install aisleriot <none> 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status half-installed aisleriot 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status unpacked aisleriot 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 status unpacked aisleriot 1:2.28.0-0ubuntu1
2009-10-28 20:58:32 install alacarte <none> 0.12.4-0ubuntu2
2009-10-28 20:58:32 status half-installed alacarte 0.12.4-0ubuntu2
2009-10-28 20:58:32 status unpacked alacarte 0.12.4-0ubuntu2
2009-10-28 20:58:32 status unpacked alacarte 0.12.4-0ubuntu2
2009-10-28 20:58:32 install linux-sound-base <none> 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:32 status half-installed linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:32 status unpacked linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 status unpacked linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 install alsa-base <none> 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 status half-installed alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 20:58:33 install alsa-utils <none> 1.0.20-2ubuntu6
2009-10-28 20:58:33 status half-installed alsa-utils 1.0.20-2ubuntu6
2009-10-28 20:58:33 status unpacked alsa-utils 1.0.20-2ubuntu6
2009-10-28 20:58:33 status unpacked alsa-utils 1.0.20-2ubuntu6
2009-10-28 20:58:33 install app-install-data <none> 0.9.10.11
2009-10-28 20:58:33 status half-installed app-install-data 0.9.10.11
2009-10-28 20:58:35 status unpacked app-install-data 0.9.10.11
2009-10-28 20:58:35 status unpacked app-install-data 0.9.10.11
2009-10-28 20:58:35 install app-install-data-partner <none> 12.9.10
2009-10-28 20:58:35 status half-installed app-install-data-partner 12.9.10
2009-10-28 20:58:35 status unpacked app-install-data-partner 12.9.10
2009-10-28 20:58:35 status unpacked app-install-data-partner 12.9.10
2009-10-28 20:58:35 install python-problem-report <none> 1.9.3-0ubuntu4
2009-10-28 20:58:35 status half-installed python-problem-report 1.9.3-0ubuntu4
2009-10-28 20:58:35 status unpacked python-problem-report 1.9.3-0ubuntu4
2009-10-28 20:58:35 status unpacked python-problem-report 1.9.3-0ubuntu4
2009-10-28 20:58:35 install python-simplejson <none> 2.0.9-1
2009-10-28 20:58:35 status half-installed python-simplejson 2.0.9-1
2009-10-28 20:58:35 status unpacked python-simplejson 2.0.9-1
2009-10-28 20:58:35 status unpacked python-simplejson 2.0.9-1
2009-10-28 20:58:36 install python-lazr-uri <none> 1.0-0ubuntu1
2009-10-28 20:58:36 status half-installed python-lazr-uri 1.0-0ubuntu1
2009-10-28 20:58:36 status unpacked python-lazr-uri 1.0-0ubuntu1
2009-10-28 20:58:36 status unpacked python-lazr-uri 1.0-0ubuntu1
2009-10-28 20:58:36 install python-wadllib <none> 1.1.2-0ubuntu1
2009-10-28 20:58:36 status half-installed python-wadllib 1.1.2-0ubuntu1
2009-10-28 20:58:36 status unpacked python-wadllib 1.1.2-0ubuntu1
2009-10-28 20:58:36 status unpacked python-wadllib 1.1.2-0ubuntu1
2009-10-28 20:58:36 install python-httplib2 <none> 0.4.0-0ubuntu2
2009-10-28 20:58:36 status half-installed python-httplib2 0.4.0-0ubuntu2
2009-10-28 20:58:36 status unpacked python-httplib2 0.4.0-0ubuntu2
2009-10-28 20:58:36 status unpacked python-httplib2 0.4.0-0ubuntu2
2009-10-28 20:58:36 install python-pkg-resources <none> 0.6c9-0ubuntu5
2009-10-28 20:58:36 status half-installed python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 20:58:36 status unpacked python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 20:58:36 status unpacked python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 20:58:36 install python-zope.interface <none> 3.5.2-1
2009-10-28 20:58:36 status half-installed python-zope.interface 3.5.2-1
2009-10-28 20:58:36 status unpacked python-zope.interface 3.5.2-1
2009-10-28 20:58:36 status unpacked python-zope.interface 3.5.2-1
2009-10-28 20:58:36 install python-lazr-restfulclient <none> 0.9.3-0ubuntu3
2009-10-28 20:58:36 status half-installed python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 20:58:36 status unpacked python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 20:58:36 status unpacked python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 20:58:36 install python-oauth <none> 1.0a~svn1124-0ubuntu2
2009-10-28 20:58:36 status half-installed python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 20:58:37 status unpacked python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 20:58:37 status unpacked python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 20:58:37 install python-launchpadlib <none> 1.5.1-0ubuntu1
2009-10-28 20:58:37 status half-installed python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 20:58:37 status unpacked python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 20:58:37 status unpacked python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 20:58:37 install python-apport <none> 1.9.3-0ubuntu4
2009-10-28 20:58:37 status half-installed python-apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked python-apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked python-apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 install apport <none> 1.9.3-0ubuntu4
2009-10-28 20:58:37 status half-installed apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 status triggers-pending shared-mime-info 0.70-0ubuntu1
2009-10-28 20:58:37 status half-installed apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 20:58:37 install python-xdg <none> 0.15-1.1ubuntu5
2009-10-28 20:58:37 status half-installed python-xdg 0.15-1.1ubuntu5
2009-10-28 20:58:37 status unpacked python-xdg 0.15-1.1ubuntu5
2009-10-28 20:58:37 status unpacked python-xdg 0.15-1.1ubuntu5
2009-10-28 20:58:37 install apport-gtk <none> 1.9.3-0ubuntu4
2009-10-28 20:58:37 status half-installed apport-gtk 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked apport-gtk 1.9.3-0ubuntu4
2009-10-28 20:58:37 status unpacked apport-gtk 1.9.3-0ubuntu4
2009-10-28 20:58:37 install apport-symptoms <none> 0.2
2009-10-28 20:58:37 status half-installed apport-symptoms 0.2
2009-10-28 20:58:37 status unpacked apport-symptoms 0.2
2009-10-28 20:58:37 status unpacked apport-symptoms 0.2
2009-10-28 20:58:37 install python-xapian <none> 1.0.14-1build1
2009-10-28 20:58:37 status half-installed python-xapian 1.0.14-1build1
2009-10-28 20:58:37 status unpacked python-xapian 1.0.14-1build1
2009-10-28 20:58:37 status unpacked python-xapian 1.0.14-1build1
2009-10-28 20:58:37 install python-debian <none> 0.1.14ubuntu1
2009-10-28 20:58:37 status half-installed python-debian 0.1.14ubuntu1
2009-10-28 20:58:37 status unpacked python-debian 0.1.14ubuntu1
2009-10-28 20:58:37 status unpacked python-debian 0.1.14ubuntu1
2009-10-28 20:58:37 install apt-xapian-index <none> 0.21ubuntu2
2009-10-28 20:58:37 status half-installed apt-xapian-index 0.21ubuntu2
2009-10-28 20:58:37 status unpacked apt-xapian-index 0.21ubuntu2
2009-10-28 20:58:37 status unpacked apt-xapian-index 0.21ubuntu2
2009-10-28 20:58:37 install apturl-common <none> 0.4.1ubuntu2
2009-10-28 20:58:37 status half-installed apturl-common 0.4.1ubuntu2
2009-10-28 20:58:37 status unpacked apturl-common 0.4.1ubuntu2
2009-10-28 20:58:37 status unpacked apturl-common 0.4.1ubuntu2
2009-10-28 20:58:38 install libgksu2-0 <none> 2.0.12-1ubuntu4
2009-10-28 20:58:38 status half-installed libgksu2-0 2.0.12-1ubuntu4
2009-10-28 20:58:38 status unpacked libgksu2-0 2.0.12-1ubuntu4
2009-10-28 20:58:38 status unpacked libgksu2-0 2.0.12-1ubuntu4
2009-10-28 20:58:38 install libgp11-0 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:38 status half-installed libgp11-0 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked libgp11-0 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked libgp11-0 2.28.1-0ubuntu1
2009-10-28 20:58:38 install libgcr0 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:38 status half-installed libgcr0 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked libgcr0 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked libgcr0 2.28.1-0ubuntu1
2009-10-28 20:58:38 install gnome-keyring <none> 2.28.1-0ubuntu1
2009-10-28 20:58:38 status half-installed gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:58:38 status unpacked gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:58:38 install gksu <none> 2.0.2-2ubuntu1
2009-10-28 20:58:38 status half-installed gksu 2.0.2-2ubuntu1
2009-10-28 20:58:38 status unpacked gksu 2.0.2-2ubuntu1
2009-10-28 20:58:38 status unpacked gksu 2.0.2-2ubuntu1
2009-10-28 20:58:38 install python-glade2 <none> 2.16.0-0ubuntu1
2009-10-28 20:58:38 status half-installed python-glade2 2.16.0-0ubuntu1
2009-10-28 20:58:38 status unpacked python-glade2 2.16.0-0ubuntu1
2009-10-28 20:58:38 status unpacked python-glade2 2.16.0-0ubuntu1
2009-10-28 20:58:38 install libvte-common <none> 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status half-installed libvte-common 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status unpacked libvte-common 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status unpacked libvte-common 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 install libvte9 <none> 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status half-installed libvte9 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status unpacked libvte9 1:0.22.2-0ubuntu2
2009-10-28 20:58:38 status unpacked libvte9 1:0.22.2-0ubuntu2
2009-10-28 20:58:39 install python-vte <none> 1:0.22.2-0ubuntu2
2009-10-28 20:58:39 status half-installed python-vte 1:0.22.2-0ubuntu2
2009-10-28 20:58:39 status unpacked python-vte 1:0.22.2-0ubuntu2
2009-10-28 20:58:39 status unpacked python-vte 1:0.22.2-0ubuntu2
2009-10-28 20:58:39 install synaptic <none> 0.62.7ubuntu6
2009-10-28 20:58:39 status half-installed synaptic 0.62.7ubuntu6
2009-10-28 20:58:40 status unpacked synaptic 0.62.7ubuntu6
2009-10-28 20:58:40 status unpacked synaptic 0.62.7ubuntu6
2009-10-28 20:58:40 install unattended-upgrades <none> 0.52ubuntu1
2009-10-28 20:58:40 status half-installed unattended-upgrades 0.52ubuntu1
2009-10-28 20:58:40 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 20:58:40 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 20:58:40 install python-software-properties <none> 0.75.4
2009-10-28 20:58:40 status half-installed python-software-properties 0.75.4
2009-10-28 20:58:40 status unpacked python-software-properties 0.75.4
2009-10-28 20:58:40 status unpacked python-software-properties 0.75.4
2009-10-28 20:58:40 install software-properties-gtk <none> 0.75.4
2009-10-28 20:58:40 status half-installed software-properties-gtk 0.75.4
2009-10-28 20:58:40 status half-installed software-properties-gtk 0.75.4
2009-10-28 20:58:40 status unpacked software-properties-gtk 0.75.4
2009-10-28 20:58:40 status unpacked software-properties-gtk 0.75.4
2009-10-28 20:58:40 install apturl <none> 0.4.1ubuntu2
2009-10-28 20:58:40 status half-installed apturl 0.4.1ubuntu2
2009-10-28 20:58:40 status unpacked apturl 0.4.1ubuntu2
2009-10-28 20:58:40 status unpacked apturl 0.4.1ubuntu2
2009-10-28 20:58:40 install libaspell15 <none> 0.60.6-2
2009-10-28 20:58:40 status half-installed libaspell15 0.60.6-2
2009-10-28 20:58:40 status unpacked libaspell15 0.60.6-2
2009-10-28 20:58:40 status unpacked libaspell15 0.60.6-2
2009-10-28 20:58:40 install dictionaries-common <none> 1.2.1ubuntu1
2009-10-28 20:58:40 status half-installed dictionaries-common 1.2.1ubuntu1
2009-10-28 20:58:40 status unpacked dictionaries-common 1.2.1ubuntu1
2009-10-28 20:58:40 status unpacked dictionaries-common 1.2.1ubuntu1
2009-10-28 20:58:41 install aspell <none> 0.60.6-2
2009-10-28 20:58:41 status half-installed aspell 0.60.6-2
2009-10-28 20:58:41 status unpacked aspell 0.60.6-2
2009-10-28 20:58:41 status unpacked aspell 0.60.6-2
2009-10-28 20:58:41 install aspell-en <none> 6.0-0-5.1ubuntu3
2009-10-28 20:58:41 status half-installed aspell-en 6.0-0-5.1ubuntu3
2009-10-28 20:58:41 status unpacked aspell-en 6.0-0-5.1ubuntu3
2009-10-28 20:58:41 status unpacked aspell-en 6.0-0-5.1ubuntu3
2009-10-28 20:58:41 install libatspi1.0-0 <none> 1.28.1-0ubuntu1
2009-10-28 20:58:41 status half-installed libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 20:58:41 status unpacked libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 20:58:41 status unpacked libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 20:58:41 install at-spi <none> 1.28.1-0ubuntu1
2009-10-28 20:58:41 status half-installed at-spi 1.28.1-0ubuntu1
2009-10-28 20:58:41 status unpacked at-spi 1.28.1-0ubuntu1
2009-10-28 20:58:41 status unpacked at-spi 1.28.1-0ubuntu1
2009-10-28 20:58:41 install libdaemon0 <none> 0.13-3
2009-10-28 20:58:41 status half-installed libdaemon0 0.13-3
2009-10-28 20:58:41 status unpacked libdaemon0 0.13-3
2009-10-28 20:58:41 status unpacked libdaemon0 0.13-3
2009-10-28 20:58:41 install avahi-autoipd <none> 0.6.25-1ubuntu5
2009-10-28 20:58:41 status half-installed avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 20:58:41 install libavahi-core6 <none> 0.6.25-1ubuntu5
2009-10-28 20:58:41 status half-installed libavahi-core6 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked libavahi-core6 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked libavahi-core6 0.6.25-1ubuntu5
2009-10-28 20:58:41 install avahi-daemon <none> 0.6.25-1ubuntu5
2009-10-28 20:58:41 status half-installed avahi-daemon 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 20:58:41 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 20:58:41 install bcmwl-modaliases <none> 5.10.91.9+bdcom-0ubuntu4
2009-10-28 20:58:41 status half-installed bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 20:58:41 status unpacked bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 20:58:41 status unpacked bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 20:58:41 install binfmt-support <none> 1.2.14
2009-10-28 20:58:41 status half-installed binfmt-support 1.2.14
2009-10-28 20:58:41 status unpacked binfmt-support 1.2.14
2009-10-28 20:58:41 status unpacked binfmt-support 1.2.14
2009-10-28 20:58:41 install binutils <none> 2.20-0ubuntu1
2009-10-28 20:58:41 status half-installed binutils 2.20-0ubuntu1
2009-10-28 20:58:41 status unpacked binutils 2.20-0ubuntu1
2009-10-28 20:58:41 status unpacked binutils 2.20-0ubuntu1
2009-10-28 20:58:42 install libbluetooth3 <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed libbluetooth3 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked libbluetooth3 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked libbluetooth3 4.51-0ubuntu2
2009-10-28 20:58:42 install libnl1 <none> 1.1-5
2009-10-28 20:58:42 status half-installed libnl1 1.1-5
2009-10-28 20:58:42 status unpacked libnl1 1.1-5
2009-10-28 20:58:42 status unpacked libnl1 1.1-5
2009-10-28 20:58:42 install bluez <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluez 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez 4.51-0ubuntu2
2009-10-28 20:58:42 install bluetooth <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluetooth 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluetooth 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluetooth 4.51-0ubuntu2
2009-10-28 20:58:42 install bluez-alsa <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluez-alsa 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-alsa 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-alsa 4.51-0ubuntu2
2009-10-28 20:58:42 install bluez-cups <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluez-cups 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-cups 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-cups 4.51-0ubuntu2
2009-10-28 20:58:42 install bluez-gstreamer <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluez-gstreamer 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-gstreamer 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-gstreamer 4.51-0ubuntu2
2009-10-28 20:58:42 install bluez-utils <none> 4.51-0ubuntu2
2009-10-28 20:58:42 status half-installed bluez-utils 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-utils 4.51-0ubuntu2
2009-10-28 20:58:42 status unpacked bluez-utils 4.51-0ubuntu2
2009-10-28 20:58:42 install libgsl0ldbl <none> 1.12+dfsg-1
2009-10-28 20:58:42 status half-installed libgsl0ldbl 1.12+dfsg-1
2009-10-28 20:58:42 status unpacked libgsl0ldbl 1.12+dfsg-1
2009-10-28 20:58:42 status unpacked libgsl0ldbl 1.12+dfsg-1
2009-10-28 20:58:42 install bogofilter-common <none> 1.2.0-3ubuntu1
2009-10-28 20:58:42 status half-installed bogofilter-common 1.2.0-3ubuntu1
2009-10-28 20:58:42 status unpacked bogofilter-common 1.2.0-3ubuntu1
2009-10-28 20:58:42 status unpacked bogofilter-common 1.2.0-3ubuntu1
2009-10-28 20:58:42 install bogofilter-bdb <none> 1.2.0-3ubuntu1
2009-10-28 20:58:42 status half-installed bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 20:58:42 status unpacked bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 20:58:42 status unpacked bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 20:58:43 install bogofilter <none> 1.2.0-3ubuntu1
2009-10-28 20:58:43 status half-installed bogofilter 1.2.0-3ubuntu1
2009-10-28 20:58:43 status unpacked bogofilter 1.2.0-3ubuntu1
2009-10-28 20:58:43 status unpacked bogofilter 1.2.0-3ubuntu1
2009-10-28 20:58:43 install libbeagle1 <none> 0.3.9-1
2009-10-28 20:58:43 status half-installed libbeagle1 0.3.9-1
2009-10-28 20:58:43 status unpacked libbeagle1 0.3.9-1
2009-10-28 20:58:43 status unpacked libbeagle1 0.3.9-1
2009-10-28 20:58:43 install libnautilus-extension1 <none> 1:2.28.1-0ubuntu1
2009-10-28 20:58:43 status half-installed libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 20:58:43 status unpacked libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 20:58:43 status unpacked libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 20:58:43 install libgmime-2.4-2 <none> 2.4.6-5
2009-10-28 20:58:43 status half-installed libgmime-2.4-2 2.4.6-5
2009-10-28 20:58:43 status unpacked libgmime-2.4-2 2.4.6-5
2009-10-28 20:58:43 status unpacked libgmime-2.4-2 2.4.6-5
2009-10-28 20:58:43 install libtotem-plparser12 <none> 2.28.1-1
2009-10-28 20:58:43 status half-installed libtotem-plparser12 2.28.1-1
2009-10-28 20:58:43 status unpacked libtotem-plparser12 2.28.1-1
2009-10-28 20:58:43 status unpacked libtotem-plparser12 2.28.1-1
2009-10-28 20:58:43 install libbrasero-media0 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:43 status half-installed libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 20:58:43 status unpacked libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 20:58:43 status unpacked libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 20:58:43 install wodim <none> 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status half-installed wodim 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status unpacked wodim 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status unpacked wodim 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 install genisoimage <none> 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status half-installed genisoimage 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status unpacked genisoimage 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 status unpacked genisoimage 9:1.1.9-1ubuntu2
2009-10-28 20:58:43 install dvd+rw-tools <none> 7.1-4
2009-10-28 20:58:43 status half-installed dvd+rw-tools 7.1-4
2009-10-28 20:58:43 status unpacked dvd+rw-tools 7.1-4
2009-10-28 20:58:43 status unpacked dvd+rw-tools 7.1-4
2009-10-28 20:58:43 install libcdparanoia0 <none> 3.10.2+debian-5
2009-10-28 20:58:43 status half-installed libcdparanoia0 3.10.2+debian-5
2009-10-28 20:58:44 status unpacked libcdparanoia0 3.10.2+debian-5
2009-10-28 20:58:44 status unpacked libcdparanoia0 3.10.2+debian-5
2009-10-28 20:58:44 install liboil0.3 <none> 0.3.16-1ubuntu1
2009-10-28 20:58:44 status half-installed liboil0.3 0.3.16-1ubuntu1
2009-10-28 20:58:44 status unpacked liboil0.3 0.3.16-1ubuntu1
2009-10-28 20:58:44 status unpacked liboil0.3 0.3.16-1ubuntu1
2009-10-28 20:58:44 install libtheora0 <none> 1.0-2.1build1
2009-10-28 20:58:44 status half-installed libtheora0 1.0-2.1build1
2009-10-28 20:58:44 status unpacked libtheora0 1.0-2.1build1
2009-10-28 20:58:44 status unpacked libtheora0 1.0-2.1build1
2009-10-28 20:58:44 install libvisual-0.4-0 <none> 0.4.0-2.1+ubuntu1
2009-10-28 20:58:44 status half-installed libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 20:58:44 status unpacked libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 20:58:44 status unpacked libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 20:58:44 install gstreamer0.10-plugins-base <none> 0.10.25-2ubuntu1
2009-10-28 20:58:44 status half-installed gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 20:58:44 status unpacked gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 20:58:44 status unpacked gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 20:58:44 install brasero <none> 2.28.1-0ubuntu1
2009-10-28 20:58:44 status half-installed brasero 2.28.1-0ubuntu1
2009-10-28 20:58:44 status half-installed brasero 2.28.1-0ubuntu1
2009-10-28 20:58:44 status unpacked brasero 2.28.1-0ubuntu1
2009-10-28 20:58:44 status unpacked brasero 2.28.1-0ubuntu1
2009-10-28 20:58:44 install screen <none> 4.0.3-13ubuntu4
2009-10-28 20:58:44 status half-installed screen 4.0.3-13ubuntu4
2009-10-28 20:58:44 status unpacked screen 4.0.3-13ubuntu4
2009-10-28 20:58:44 status unpacked screen 4.0.3-13ubuntu4
2009-10-28 20:58:45 install python-newt <none> 0.52.10-4ubuntu1
2009-10-28 20:58:45 status half-installed python-newt 0.52.10-4ubuntu1
2009-10-28 20:58:45 status unpacked python-newt 0.52.10-4ubuntu1
2009-10-28 20:58:45 status unpacked python-newt 0.52.10-4ubuntu1
2009-10-28 20:58:45 install byobu <none> 2.38-0ubuntu3
2009-10-28 20:58:45 status half-installed byobu 2.38-0ubuntu3
2009-10-28 20:58:45 status unpacked byobu 2.38-0ubuntu3
2009-10-28 20:58:45 status unpacked byobu 2.38-0ubuntu3
2009-10-28 20:58:45 install cdparanoia <none> 3.10.2+debian-5
2009-10-28 20:58:45 status half-installed cdparanoia 3.10.2+debian-5
2009-10-28 20:58:45 status unpacked cdparanoia 3.10.2+debian-5
2009-10-28 20:58:45 status unpacked cdparanoia 3.10.2+debian-5
2009-10-28 20:58:45 install checkbox <none> 0.8.5
2009-10-28 20:58:45 status half-installed checkbox 0.8.5
2009-10-28 20:58:45 status unpacked checkbox 0.8.5
2009-10-28 20:58:45 status unpacked checkbox 0.8.5
2009-10-28 20:58:45 install checkbox-gtk <none> 0.8.5
2009-10-28 20:58:45 status half-installed checkbox-gtk 0.8.5
2009-10-28 20:58:45 status unpacked checkbox-gtk 0.8.5
2009-10-28 20:58:45 status unpacked checkbox-gtk 0.8.5
2009-10-28 20:58:45 install cli-common <none> 0.7
2009-10-28 20:58:45 status half-installed cli-common 0.7
2009-10-28 20:58:45 status unpacked cli-common 0.7
2009-10-28 20:58:45 status unpacked cli-common 0.7
2009-10-28 20:58:45 install mesa-utils <none> 7.6.0-1ubuntu4
2009-10-28 20:58:45 status half-installed mesa-utils 7.6.0-1ubuntu4
2009-10-28 20:58:45 status unpacked mesa-utils 7.6.0-1ubuntu4
2009-10-28 20:58:45 status unpacked mesa-utils 7.6.0-1ubuntu4
2009-10-28 20:58:45 install compiz-wrapper <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status half-installed compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status unpacked compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status unpacked compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 install compiz-core <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status half-installed compiz-core 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status unpacked compiz-core 1:0.8.4-0ubuntu2
2009-10-28 20:58:45 status unpacked compiz-core 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 install libdecoration0 <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status half-installed libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 install libglu1-mesa <none> 7.6.0-1ubuntu4
2009-10-28 20:58:46 status half-installed libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 20:58:46 status unpacked libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 20:58:46 status unpacked libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 20:58:46 install compiz-plugins <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status half-installed compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 install libprotobuf3 <none> 2.0.3-2.2ubuntu2
2009-10-28 20:58:46 status half-installed libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 20:58:46 status unpacked libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 20:58:46 status unpacked libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 20:58:46 install libcompizconfig0 <none> 0.8.4-0ubuntu1
2009-10-28 20:58:46 status half-installed libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 20:58:46 status unpacked libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 20:58:46 status unpacked libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 20:58:46 install compizconfig-backend-gconf <none> 0.8.4-0ubuntu1
2009-10-28 20:58:46 status half-installed compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 20:58:46 status unpacked compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 20:58:46 status unpacked compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 20:58:46 install compiz-gnome <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status half-installed compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 20:58:46 status unpacked compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 20:58:47 install compiz-fusion-plugins-main <none> 0.8.4-0ubuntu1
2009-10-28 20:58:47 status half-installed compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 20:58:47 status unpacked compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 20:58:47 status unpacked compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 20:58:47 install compiz-fusion-plugins-extra <none> 0.8.4-0ubuntu2
2009-10-28 20:58:47 status half-installed compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 20:58:47 status unpacked compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 20:58:47 status unpacked compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 20:58:47 install compiz <none> 1:0.8.4-0ubuntu2
2009-10-28 20:58:47 status half-installed compiz 1:0.8.4-0ubuntu2
2009-10-28 20:58:47 status unpacked compiz 1:0.8.4-0ubuntu2
2009-10-28 20:58:47 status unpacked compiz 1:0.8.4-0ubuntu2
2009-10-28 20:58:47 install python-fstab <none> 1.4-0ubuntu1
2009-10-28 20:58:47 status half-installed python-fstab 1.4-0ubuntu1
2009-10-28 20:58:48 status unpacked python-fstab 1.4-0ubuntu1
2009-10-28 20:58:48 status unpacked python-fstab 1.4-0ubuntu1
2009-10-28 20:58:48 install computer-janitor <none> 1.13.3-0ubuntu2
2009-10-28 20:58:48 status half-installed computer-janitor 1.13.3-0ubuntu2
2009-10-28 20:58:48 status unpacked computer-janitor 1.13.3-0ubuntu2
2009-10-28 20:58:48 status unpacked computer-janitor 1.13.3-0ubuntu2
2009-10-28 20:58:48 install computer-janitor-gtk <none> 1.13.3-0ubuntu2
2009-10-28 20:58:48 status half-installed computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 20:58:48 status unpacked computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 20:58:48 status unpacked computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 20:58:48 install libcurl3 <none> 7.19.5-1ubuntu2
2009-10-28 20:58:48 status half-installed libcurl3 7.19.5-1ubuntu2
2009-10-28 20:58:48 status unpacked libcurl3 7.19.5-1ubuntu2
2009-10-28 20:58:48 status unpacked libcurl3 7.19.5-1ubuntu2
2009-10-28 20:58:48 install erlang-base <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status half-installed erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 install erlang-crypto <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status half-installed erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 install erlang-mnesia <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status half-installed erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 install erlang-public-key <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status half-installed erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:48 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 install erlang-runtime-tools <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status half-installed erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 install erlang-ssl <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status half-installed erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 install erlang-inets <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status half-installed erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 install erlang-xmerl <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status half-installed erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:49 install couchdb-bin <none> 0.10.0-0ubuntu3
2009-10-28 20:58:49 status half-installed couchdb-bin 0.10.0-0ubuntu3
2009-10-28 20:58:49 status unpacked couchdb-bin 0.10.0-0ubuntu3
2009-10-28 20:58:49 status unpacked couchdb-bin 0.10.0-0ubuntu3
2009-10-28 20:58:49 install libgutenprint2 <none> 5.2.4-0ubuntu2
2009-10-28 20:58:49 status half-installed libgutenprint2 5.2.4-0ubuntu2
2009-10-28 20:58:50 status unpacked libgutenprint2 5.2.4-0ubuntu2
2009-10-28 20:58:50 status unpacked libgutenprint2 5.2.4-0ubuntu2
2009-10-28 20:58:50 install ghostscript-cups <none> 8.70.dfsg.1-0ubuntu3
2009-10-28 20:58:50 status half-installed ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 20:58:50 status unpacked ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 20:58:50 status unpacked ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 20:58:50 install cups-driver-gutenprint <none> 5.2.4-0ubuntu2
2009-10-28 20:58:50 status half-installed cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 20:58:50 status unpacked cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 20:58:50 status unpacked cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 20:58:50 install dc <none> 1.06.94-3.1ubuntu2
2009-10-28 20:58:50 status half-installed dc 1.06.94-3.1ubuntu2
2009-10-28 20:58:50 status unpacked dc 1.06.94-3.1ubuntu2
2009-10-28 20:58:50 status unpacked dc 1.06.94-3.1ubuntu2
2009-10-28 20:58:50 install python-couchdb <none> 0.6-1
2009-10-28 20:58:50 status half-installed python-couchdb 0.6-1
2009-10-28 20:58:50 status unpacked python-couchdb 0.6-1
2009-10-28 20:58:50 status unpacked python-couchdb 0.6-1
2009-10-28 20:58:50 install python-twisted-bin <none> 8.2.0-3
2009-10-28 20:58:50 status half-installed python-twisted-bin 8.2.0-3
2009-10-28 20:58:50 status unpacked python-twisted-bin 8.2.0-3
2009-10-28 20:58:50 status unpacked python-twisted-bin 8.2.0-3
2009-10-28 20:58:50 install python-twisted-core <none> 8.2.0-3
2009-10-28 20:58:50 status half-installed python-twisted-core 8.2.0-3
2009-10-28 20:58:51 status unpacked python-twisted-core 8.2.0-3
2009-10-28 20:58:51 status unpacked python-twisted-core 8.2.0-3
2009-10-28 20:58:51 install python-avahi <none> 0.6.25-1ubuntu5
2009-10-28 20:58:51 status half-installed python-avahi 0.6.25-1ubuntu5
2009-10-28 20:58:51 status unpacked python-avahi 0.6.25-1ubuntu5
2009-10-28 20:58:51 status unpacked python-avahi 0.6.25-1ubuntu5
2009-10-28 20:58:51 install python-gnomekeyring <none> 2.28.0-0ubuntu1
2009-10-28 20:58:51 status half-installed python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 20:58:51 status unpacked python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 20:58:51 status unpacked python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 20:58:51 install python-desktopcouch <none> 0.5-0ubuntu1
2009-10-28 20:58:51 status half-installed python-desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked python-desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked python-desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 install python-desktopcouch-records <none> 0.5-0ubuntu1
2009-10-28 20:58:51 status half-installed python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 20:58:51 install desktopcouch <none> 0.5-0ubuntu1
2009-10-28 20:58:51 status half-installed desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 status unpacked desktopcouch 0.5-0ubuntu1
2009-10-28 20:58:51 install libdevkit-power-gobject1 <none> 011-1ubuntu1
2009-10-28 20:58:51 status half-installed libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 20:58:51 status unpacked libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 20:58:51 status unpacked libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 20:58:51 install devicekit-power <none> 011-1ubuntu1
2009-10-28 20:58:51 status half-installed devicekit-power 011-1ubuntu1
2009-10-28 20:58:51 status unpacked devicekit-power 011-1ubuntu1
2009-10-28 20:58:51 status unpacked devicekit-power 011-1ubuntu1
2009-10-28 20:58:51 install dmz-cursor-theme <none> 0.4.1
2009-10-28 20:58:51 status half-installed dmz-cursor-theme 0.4.1
2009-10-28 20:58:52 status unpacked dmz-cursor-theme 0.4.1
2009-10-28 20:58:52 status unpacked dmz-cursor-theme 0.4.1
2009-10-28 20:58:52 install dnsmasq-base <none> 2.50-1
2009-10-28 20:58:52 status half-installed dnsmasq-base 2.50-1
2009-10-28 20:58:52 status unpacked dnsmasq-base 2.50-1
2009-10-28 20:58:52 status unpacked dnsmasq-base 2.50-1
2009-10-28 20:58:52 install libuuid-perl <none> 0.02-3build1
2009-10-28 20:58:52 status half-installed libuuid-perl 0.02-3build1
2009-10-28 20:58:52 status unpacked libuuid-perl 0.02-3build1
2009-10-28 20:58:52 status unpacked libuuid-perl 0.02-3build1
2009-10-28 20:58:52 install libmldbm-perl <none> 2.01-2
2009-10-28 20:58:52 status half-installed libmldbm-perl 2.01-2
2009-10-28 20:58:52 status unpacked libmldbm-perl 2.01-2
2009-10-28 20:58:52 status unpacked libmldbm-perl 2.01-2
2009-10-28 20:58:52 install doc-base <none> 0.9.3
2009-10-28 20:58:52 status half-installed doc-base 0.9.3
2009-10-28 20:58:52 status unpacked doc-base 0.9.3
2009-10-28 20:58:52 status unpacked doc-base 0.9.3
2009-10-28 20:58:52 install libgssdp-1.0-1 <none> 0.6.4-2
2009-10-28 20:58:52 status half-installed libgssdp-1.0-1 0.6.4-2
2009-10-28 20:58:52 status unpacked libgssdp-1.0-1 0.6.4-2
2009-10-28 20:58:52 status unpacked libgssdp-1.0-1 0.6.4-2
2009-10-28 20:58:52 install libgupnp-1.0-2 <none> 0.12.6-3.1
2009-10-28 20:58:52 status half-installed libgupnp-1.0-2 0.12.6-3.1
2009-10-28 20:58:52 status unpacked libgupnp-1.0-2 0.12.6-3.1
2009-10-28 20:58:52 status unpacked libgupnp-1.0-2 0.12.6-3.1
2009-10-28 20:58:52 install libgupnp-igd-1.0-2 <none> 0.1.3-0ubuntu3
2009-10-28 20:58:52 status half-installed libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 20:58:52 status unpacked libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 20:58:52 status unpacked libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 20:58:52 install libnice0 <none> 0.0.9-2
2009-10-28 20:58:52 status half-installed libnice0 0.0.9-2
2009-10-28 20:58:52 status unpacked libnice0 0.0.9-2
2009-10-28 20:58:52 status unpacked libnice0 0.0.9-2
2009-10-28 20:58:52 install libaa1 <none> 1.4p5-38
2009-10-28 20:58:52 status half-installed libaa1 1.4p5-38
2009-10-28 20:58:52 status unpacked libaa1 1.4p5-38
2009-10-28 20:58:52 status unpacked libaa1 1.4p5-38
2009-10-28 20:58:53 install libraw1394-11 <none> 2.0.4-1ubuntu1
2009-10-28 20:58:53 status half-installed libraw1394-11 2.0.4-1ubuntu1
2009-10-28 20:58:53 status unpacked libraw1394-11 2.0.4-1ubuntu1
2009-10-28 20:58:53 status unpacked libraw1394-11 2.0.4-1ubuntu1
2009-10-28 20:58:53 install libavc1394-0 <none> 0.5.3-1build3
2009-10-28 20:58:53 status half-installed libavc1394-0 0.5.3-1build3
2009-10-28 20:58:53 status unpacked libavc1394-0 0.5.3-1build3
2009-10-28 20:58:53 status unpacked libavc1394-0 0.5.3-1build3
2009-10-28 20:58:53 install libcaca0 <none> 0.99.beta16-1
2009-10-28 20:58:53 status half-installed libcaca0 0.99.beta16-1
2009-10-28 20:58:53 status unpacked libcaca0 0.99.beta16-1
2009-10-28 20:58:53 status unpacked libcaca0 0.99.beta16-1
2009-10-28 20:58:53 install libdv4 <none> 1.0.0-2ubuntu1
2009-10-28 20:58:53 status half-installed libdv4 1.0.0-2ubuntu1
2009-10-28 20:58:53 status unpacked libdv4 1.0.0-2ubuntu1
2009-10-28 20:58:53 status unpacked libdv4 1.0.0-2ubuntu1
2009-10-28 20:58:53 install libiec61883-0 <none> 1.2.0-0.1
2009-10-28 20:58:53 status half-installed libiec61883-0 1.2.0-0.1
2009-10-28 20:58:53 status unpacked libiec61883-0 1.2.0-0.1
2009-10-28 20:58:53 status unpacked libiec61883-0 1.2.0-0.1
2009-10-28 20:58:53 install libspeex1 <none> 1.2~rc1-1
2009-10-28 20:58:53 status half-installed libspeex1 1.2~rc1-1
2009-10-28 20:58:53 status unpacked libspeex1 1.2~rc1-1
2009-10-28 20:58:53 status unpacked libspeex1 1.2~rc1-1
2009-10-28 20:58:53 install libshout3 <none> 2.2.2-5ubuntu1
2009-10-28 20:58:53 status half-installed libshout3 2.2.2-5ubuntu1
2009-10-28 20:58:53 status unpacked libshout3 2.2.2-5ubuntu1
2009-10-28 20:58:53 status unpacked libshout3 2.2.2-5ubuntu1
2009-10-28 20:58:53 install libtag1-vanilla <none> 1.6-2ubuntu2
2009-10-28 20:58:53 status half-installed libtag1-vanilla 1.6-2ubuntu2
2009-10-28 20:58:53 status unpacked libtag1-vanilla 1.6-2ubuntu2
2009-10-28 20:58:53 status unpacked libtag1-vanilla 1.6-2ubuntu2
2009-10-28 20:58:53 install libtag1c2a <none> 1.6-2ubuntu2
2009-10-28 20:58:53 status half-installed libtag1c2a 1.6-2ubuntu2
2009-10-28 20:58:53 status unpacked libtag1c2a 1.6-2ubuntu2
2009-10-28 20:58:53 status unpacked libtag1c2a 1.6-2ubuntu2
2009-10-28 20:58:53 install libwavpack1 <none> 4.50.1-1
2009-10-28 20:58:53 status half-installed libwavpack1 4.50.1-1
2009-10-28 20:58:53 status unpacked libwavpack1 4.50.1-1
2009-10-28 20:58:53 status unpacked libwavpack1 4.50.1-1
2009-10-28 20:58:53 install gstreamer0.10-plugins-good <none> 0.10.16-1ubuntu3
2009-10-28 20:58:53 status half-installed gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 20:58:54 status unpacked gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 20:58:54 status unpacked gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 20:58:54 install gstreamer0.10-nice <none> 0.0.9-2
2009-10-28 20:58:54 status half-installed gstreamer0.10-nice 0.0.9-2
2009-10-28 20:58:54 status unpacked gstreamer0.10-nice 0.0.9-2
2009-10-28 20:58:54 status unpacked gstreamer0.10-nice 0.0.9-2
2009-10-28 20:58:54 install libgstfarsight0.10-0 <none> 0.0.15-1ubuntu1
2009-10-28 20:58:54 status half-installed libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 20:58:54 status unpacked libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 20:58:54 status unpacked libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 20:58:54 install libnm-util1 <none> 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status half-installed libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status unpacked libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status unpacked libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 install libnm-glib2 <none> 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status half-installed libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status unpacked libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 status unpacked libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 20:58:54 install libtelepathy-glib0 <none> 0.9.0-1
2009-10-28 20:58:54 status half-installed libtelepathy-glib0 0.9.0-1
2009-10-28 20:58:54 status unpacked libtelepathy-glib0 0.9.0-1
2009-10-28 20:58:54 status unpacked libtelepathy-glib0 0.9.0-1
2009-10-28 20:58:54 install libtelepathy-farsight0 <none> 0.0.11-2
2009-10-28 20:58:54 status half-installed libtelepathy-farsight0 0.0.11-2
2009-10-28 20:58:55 status unpacked libtelepathy-farsight0 0.0.11-2
2009-10-28 20:58:55 status unpacked libtelepathy-farsight0 0.0.11-2
2009-10-28 20:58:55 install libempathy-common <none> 2.28.1-1ubuntu1
2009-10-28 20:58:55 status half-installed libempathy-common 2.28.1-1ubuntu1
2009-10-28 20:58:55 status unpacked libempathy-common 2.28.1-1ubuntu1
2009-10-28 20:58:55 status unpacked libempathy-common 2.28.1-1ubuntu1
2009-10-28 20:58:55 install telepathy-mission-control-5 <none> 5.3.1-1
2009-10-28 20:58:55 status half-installed telepathy-mission-control-5 5.3.1-1
2009-10-28 20:58:55 status unpacked telepathy-mission-control-5 5.3.1-1
2009-10-28 20:58:55 status unpacked telepathy-mission-control-5 5.3.1-1
2009-10-28 20:58:55 install libempathy30 <none> 2.28.1-1ubuntu1
2009-10-28 20:58:55 status half-installed libempathy30 2.28.1-1ubuntu1
2009-10-28 20:58:55 status unpacked libempathy30 2.28.1-1ubuntu1
2009-10-28 20:58:55 status unpacked libempathy30 2.28.1-1ubuntu1
2009-10-28 20:58:55 install libenchant1c2a <none> 1.5.0-0ubuntu2
2009-10-28 20:58:55 status half-installed libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 20:58:55 status unpacked libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 20:58:55 status unpacked libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 20:58:55 install libwebkit-1.0-common <none> 1.1.15.2-1
2009-10-28 20:58:55 status half-installed libwebkit-1.0-common 1.1.15.2-1
2009-10-28 20:58:55 status unpacked libwebkit-1.0-common 1.1.15.2-1
2009-10-28 20:58:55 status unpacked libwebkit-1.0-common 1.1.15.2-1
2009-10-28 20:58:55 install libwebkit-1.0-2 <none> 1.1.15.2-1
2009-10-28 20:58:55 status half-installed libwebkit-1.0-2 1.1.15.2-1
2009-10-28 20:58:56 status unpacked libwebkit-1.0-2 1.1.15.2-1
2009-10-28 20:58:56 status unpacked libwebkit-1.0-2 1.1.15.2-1
2009-10-28 20:58:56 install libempathy-gtk-common <none> 2.28.1-1ubuntu1
2009-10-28 20:58:56 status half-installed libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 20:58:57 install libempathy-gtk28 <none> 2.28.1-1ubuntu1
2009-10-28 20:58:57 status half-installed libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 20:58:57 install libindicate3 <none> 0.2.3-0ubuntu1
2009-10-28 20:58:57 status half-installed libindicate3 0.2.3-0ubuntu1
2009-10-28 20:58:57 status unpacked libindicate3 0.2.3-0ubuntu1
2009-10-28 20:58:57 status unpacked libindicate3 0.2.3-0ubuntu1
2009-10-28 20:58:57 install libindicate-gtk1 <none> 0.2.3-0ubuntu1
2009-10-28 20:58:57 status half-installed libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 20:58:57 status unpacked libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 20:58:57 status unpacked libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 20:58:57 install empathy-doc <none> 2.28.1-1ubuntu1
2009-10-28 20:58:57 status half-installed empathy-doc 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked empathy-doc 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked empathy-doc 2.28.1-1ubuntu1
2009-10-28 20:58:57 install empathy <none> 2.28.1-1ubuntu1
2009-10-28 20:58:57 status half-installed empathy 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked empathy 2.28.1-1ubuntu1
2009-10-28 20:58:57 status unpacked empathy 2.28.1-1ubuntu1
2009-10-28 20:58:57 install libexempi3 <none> 2.1.1-1build1
2009-10-28 20:58:57 status half-installed libexempi3 2.1.1-1build1
2009-10-28 20:58:57 status unpacked libexempi3 2.1.1-1build1
2009-10-28 20:58:57 status unpacked libexempi3 2.1.1-1build1
2009-10-28 20:58:57 install eog <none> 2.28.1-0ubuntu1
2009-10-28 20:58:57 status half-installed eog 2.28.1-0ubuntu1
2009-10-28 20:58:57 status unpacked eog 2.28.1-0ubuntu1
2009-10-28 20:58:57 status unpacked eog 2.28.1-0ubuntu1
2009-10-28 20:58:58 install erlang-syntax-tools <none> 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:58 status half-installed erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:58 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:58 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 20:58:58 install esound-clients <none> 0.2.41-5
2009-10-28 20:58:58 status half-installed esound-clients 0.2.41-5
2009-10-28 20:58:58 status unpacked esound-clients 0.2.41-5
2009-10-28 20:58:58 status unpacked esound-clients 0.2.41-5
2009-10-28 20:58:58 install libportaudio2 <none> 19+svn20090620-0ubuntu1
2009-10-28 20:58:58 status half-installed libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 20:58:58 status unpacked libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 20:58:58 status unpacked libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 20:58:58 install espeak-data <none> 1.41.01-0ubuntu1
2009-10-28 20:58:58 status half-installed espeak-data 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked espeak-data 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked espeak-data 1.41.01-0ubuntu1
2009-10-28 20:58:58 install libespeak1 <none> 1.41.01-0ubuntu1
2009-10-28 20:58:58 status half-installed libespeak1 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked libespeak1 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked libespeak1 1.41.01-0ubuntu1
2009-10-28 20:58:58 install espeak <none> 1.41.01-0ubuntu1
2009-10-28 20:58:58 status half-installed espeak 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked espeak 1.41.01-0ubuntu1
2009-10-28 20:58:58 status unpacked espeak 1.41.01-0ubuntu1
2009-10-28 20:58:58 install ethtool <none> 6+20090307-1
2009-10-28 20:58:58 status half-installed ethtool 6+20090307-1
2009-10-28 20:58:58 status unpacked ethtool 6+20090307-1
2009-10-28 20:58:58 status unpacked ethtool 6+20090307-1
2009-10-28 20:58:58 install libdjvulibre-text <none> 3.5.22-1ubuntu2
2009-10-28 20:58:58 status half-installed libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 20:58:58 status unpacked libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 20:58:58 status unpacked libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 20:58:58 install libdjvulibre21 <none> 3.5.22-1ubuntu2
2009-10-28 20:58:58 status half-installed libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 20:58:59 status unpacked libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 20:58:59 status unpacked libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 20:58:59 install libevdocument1 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libevdocument1 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libevdocument1 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libevdocument1 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libevview1 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libevview1 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libevview1 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libevview1 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libkpathsea4 <none> 2007.dfsg.2-7ubuntu1
2009-10-28 20:58:59 status half-installed libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 20:58:59 status unpacked libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 20:58:59 status unpacked libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 20:58:59 install libpoppler-glib4 <none> 0.12.0-0ubuntu2
2009-10-28 20:58:59 status half-installed libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 20:58:59 status unpacked libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 20:58:59 status unpacked libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 20:58:59 install libspectre1 <none> 0.2.2.ds-2
2009-10-28 20:58:59 status half-installed libspectre1 0.2.2.ds-2
2009-10-28 20:58:59 status unpacked libspectre1 0.2.2.ds-2
2009-10-28 20:58:59 status unpacked libspectre1 0.2.2.ds-2
2009-10-28 20:58:59 install evince <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed evince 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked evince 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked evince 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libebackend1.2-0 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libegroupwise1.2-13 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libexchange-storage1.2-3 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 20:58:59 status unpacked libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 20:58:59 install libgdata1.2-1 <none> 2.28.1-0ubuntu1
2009-10-28 20:58:59 status half-installed libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 install libgdata-google1.2-1 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:00 status half-installed libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 20:59:00 install libpisock9 <none> 0.12.4-3ubuntu1
2009-10-28 20:59:00 status half-installed libpisock9 0.12.4-3ubuntu1
2009-10-28 20:59:00 status unpacked libpisock9 0.12.4-3ubuntu1
2009-10-28 20:59:00 status unpacked libpisock9 0.12.4-3ubuntu1
2009-10-28 20:59:00 install libpisync1 <none> 0.12.4-3ubuntu1
2009-10-28 20:59:00 status half-installed libpisync1 0.12.4-3ubuntu1
2009-10-28 20:59:00 status unpacked libpisync1 0.12.4-3ubuntu1
2009-10-28 20:59:00 status unpacked libpisync1 0.12.4-3ubuntu1
2009-10-28 20:59:00 install libgnome-pilot2 <none> 2.0.17-0ubuntu2
2009-10-28 20:59:00 status half-installed libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 20:59:00 status unpacked libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 20:59:00 status unpacked libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 20:59:00 install libgtkhtml3.14-19 <none> 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status half-installed libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 install libgtkhtml-editor-common <none> 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status half-installed libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 install libgtkhtml-editor0 <none> 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status half-installed libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 status unpacked libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 20:59:00 install liblpint-bonobo0 <none> 0.1.26
2009-10-28 20:59:00 status half-installed liblpint-bonobo0 0.1.26
2009-10-28 20:59:00 status unpacked liblpint-bonobo0 0.1.26
2009-10-28 20:59:00 status unpacked liblpint-bonobo0 0.1.26
2009-10-28 20:59:00 install evolution-common <none> 2.28.1-0ubuntu1
2009-10-28 20:59:00 status half-installed evolution-common 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked evolution-common 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked evolution-common 2.28.1-0ubuntu1
2009-10-28 20:59:01 install libedata-book1.2-2 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:01 status half-installed libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 20:59:01 install libedata-cal1.2-6 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:01 status half-installed libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 20:59:01 install evolution-data-server <none> 2.28.1-0ubuntu1
2009-10-28 20:59:01 status half-installed evolution-data-server 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked evolution-data-server 2.28.1-0ubuntu1
2009-10-28 20:59:01 status unpacked evolution-data-server 2.28.1-0ubuntu1
2009-10-28 20:59:01 install evolution <none> 2.28.1-0ubuntu1
2009-10-28 20:59:01 status half-installed evolution 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution 2.28.1-0ubuntu1
2009-10-28 20:59:02 install libjson-glib-1.0-0 <none> 0.7.6-0ubuntu1
2009-10-28 20:59:02 status half-installed libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 20:59:02 status unpacked libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 20:59:02 status unpacked libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 20:59:02 install libcouchdb-glib-1.0-1 <none> 0.5.2-0ubuntu1
2009-10-28 20:59:02 status half-installed libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 20:59:02 status unpacked libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 20:59:02 status unpacked libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 20:59:02 install evolution-couchdb <none> 0.3.2-0ubuntu2
2009-10-28 20:59:02 status half-installed evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 20:59:02 status unpacked evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 20:59:02 status unpacked evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 20:59:02 install evolution-exchange <none> 2.28.1-0ubuntu1
2009-10-28 20:59:02 status half-installed evolution-exchange 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution-exchange 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution-exchange 2.28.1-0ubuntu1
2009-10-28 20:59:02 install libpst4 <none> 0.6.41-0ubuntu2
2009-10-28 20:59:02 status half-installed libpst4 0.6.41-0ubuntu2
2009-10-28 20:59:02 status unpacked libpst4 0.6.41-0ubuntu2
2009-10-28 20:59:02 status unpacked libpst4 0.6.41-0ubuntu2
2009-10-28 20:59:02 install evolution-plugins <none> 2.28.1-0ubuntu1
2009-10-28 20:59:02 status half-installed evolution-plugins 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution-plugins 2.28.1-0ubuntu1
2009-10-28 20:59:02 status unpacked evolution-plugins 2.28.1-0ubuntu1
2009-10-28 20:59:02 install evolution-webcal <none> 2.28.0-0ubuntu1
2009-10-28 20:59:02 status half-installed evolution-webcal 2.28.0-0ubuntu1
2009-10-28 20:59:03 status unpacked evolution-webcal 2.28.0-0ubuntu1
2009-10-28 20:59:03 status unpacked evolution-webcal 2.28.0-0ubuntu1
2009-10-28 20:59:03 install example-content <none> 38
2009-10-28 20:59:03 status half-installed example-content 38
2009-10-28 20:59:03 status unpacked example-content 38
2009-10-28 20:59:03 status unpacked example-content 38
2009-10-28 20:59:03 install libmono-corlib2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:03 status half-installed libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:03 status unpacked libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:03 status unpacked libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:03 install libmono-system2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:03 status half-installed libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install libmono-security2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install mono-2.0-gac <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install mono-gac <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed mono-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-gac 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install mono-runtime <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed mono-runtime 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install libmono-data-tds2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status unpacked libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:04 install libmono-system-data2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:04 status half-installed libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 install libsqlite0 <none> 2.8.17-6build1
2009-10-28 20:59:05 status half-installed libsqlite0 2.8.17-6build1
2009-10-28 20:59:05 status unpacked libsqlite0 2.8.17-6build1
2009-10-28 20:59:05 status unpacked libsqlite0 2.8.17-6build1
2009-10-28 20:59:05 install libmono-sqlite2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status half-installed libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 install libmono-posix2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status half-installed libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 install libmono-sharpzip2.84-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status half-installed libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 install libmono2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status half-installed libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status unpacked libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:05 install libgif4 <none> 4.1.6-6
2009-10-28 20:59:05 status half-installed libgif4 4.1.6-6
2009-10-28 20:59:05 status unpacked libgif4 4.1.6-6
2009-10-28 20:59:05 status unpacked libgif4 4.1.6-6
2009-10-28 20:59:05 install libgdiplus <none> 2.4.2-1
2009-10-28 20:59:05 status half-installed libgdiplus 2.4.2-1
2009-10-28 20:59:05 status unpacked libgdiplus 2.4.2-1
2009-10-28 20:59:05 status unpacked libgdiplus 2.4.2-1
2009-10-28 20:59:05 install libmono-system-web2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:05 status half-installed libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 status unpacked libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 status unpacked libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 install libflickrnet2.2-cil <none> 1:2.2.0-1
2009-10-28 20:59:06 status half-installed libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 20:59:06 status unpacked libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 20:59:06 status unpacked libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 20:59:06 install libglib2.0-cil <none> 2.12.9-1
2009-10-28 20:59:06 status half-installed libglib2.0-cil 2.12.9-1
2009-10-28 20:59:06 status unpacked libglib2.0-cil 2.12.9-1
2009-10-28 20:59:06 status unpacked libglib2.0-cil 2.12.9-1
2009-10-28 20:59:06 install libgconf2.0-cil <none> 2.24.1-4ubuntu1
2009-10-28 20:59:06 status half-installed libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:06 status unpacked libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:06 status unpacked libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:06 install libmono-cairo2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:06 status half-installed libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 status unpacked libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 status unpacked libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:06 install libgtk2.0-cil <none> 2.12.9-1
2009-10-28 20:59:06 status half-installed libgtk2.0-cil 2.12.9-1
2009-10-28 20:59:07 status unpacked libgtk2.0-cil 2.12.9-1
2009-10-28 20:59:07 status unpacked libgtk2.0-cil 2.12.9-1
2009-10-28 20:59:07 install libglade2.0-cil <none> 2.12.9-1
2009-10-28 20:59:07 status half-installed libglade2.0-cil 2.12.9-1
2009-10-28 20:59:07 status unpacked libglade2.0-cil 2.12.9-1
2009-10-28 20:59:07 status unpacked libglade2.0-cil 2.12.9-1
2009-10-28 20:59:07 install libglitz1 <none> 0.5.6-1
2009-10-28 20:59:07 status half-installed libglitz1 0.5.6-1
2009-10-28 20:59:07 status unpacked libglitz1 0.5.6-1
2009-10-28 20:59:07 status unpacked libglitz1 0.5.6-1
2009-10-28 20:59:07 install libglitz-glx1 <none> 0.5.6-1
2009-10-28 20:59:07 status half-installed libglitz-glx1 0.5.6-1
2009-10-28 20:59:07 status unpacked libglitz-glx1 0.5.6-1
2009-10-28 20:59:07 status unpacked libglitz-glx1 0.5.6-1
2009-10-28 20:59:07 install libndesk-dbus1.0-cil <none> 0.6.0-3
2009-10-28 20:59:07 status half-installed libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 20:59:07 status unpacked libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 20:59:07 status unpacked libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 20:59:07 install libgnome-keyring1.0-cil <none> 1.0.0-1
2009-10-28 20:59:07 status half-installed libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 20:59:07 status unpacked libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 20:59:07 status unpacked libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 20:59:07 install libgnome-vfs2.0-cil <none> 2.24.1-4ubuntu1
2009-10-28 20:59:07 status half-installed libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 install libart2.0-cil <none> 2.24.1-4ubuntu1
2009-10-28 20:59:07 status half-installed libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 install libgnome2.24-cil <none> 2.24.1-4ubuntu1
2009-10-28 20:59:07 status half-installed libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 status unpacked libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 20:59:07 install libmono-addins0.2-cil <none> 0.4-5
2009-10-28 20:59:07 status half-installed libmono-addins0.2-cil 0.4-5
2009-10-28 20:59:07 status unpacked libmono-addins0.2-cil 0.4-5
2009-10-28 20:59:07 status unpacked libmono-addins0.2-cil 0.4-5
2009-10-28 20:59:08 install libmono-addins-gui0.2-cil <none> 0.4-5
2009-10-28 20:59:08 status half-installed libmono-addins-gui0.2-cil 0.4-5
2009-10-28 20:59:08 status unpacked libmono-addins-gui0.2-cil 0.4-5
2009-10-28 20:59:08 status unpacked libmono-addins-gui0.2-cil 0.4-5
2009-10-28 20:59:08 install libndesk-dbus-glib1.0-cil <none> 0.4.1-2
2009-10-28 20:59:08 status half-installed libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 20:59:08 status unpacked libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 20:59:08 status unpacked libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 20:59:08 install gvfs-bin <none> 1.4.1-0ubuntu1
2009-10-28 20:59:08 status half-installed gvfs-bin 1.4.1-0ubuntu1
2009-10-28 20:59:08 status unpacked gvfs-bin 1.4.1-0ubuntu1
2009-10-28 20:59:08 status unpacked gvfs-bin 1.4.1-0ubuntu1
2009-10-28 20:59:08 install f-spot <none> 0.6.1.3-2
2009-10-28 20:59:08 status half-installed f-spot 0.6.1.3-2
2009-10-28 20:59:08 status unpacked f-spot 0.6.1.3-2
2009-10-28 20:59:08 status unpacked f-spot 0.6.1.3-2
2009-10-28 20:59:08 install unzip <none> 6.0-1
2009-10-28 20:59:08 status half-installed unzip 6.0-1
2009-10-28 20:59:08 status unpacked unzip 6.0-1
2009-10-28 20:59:08 status unpacked unzip 6.0-1
2009-10-28 20:59:08 install zip <none> 3.0-1ubuntu1
2009-10-28 20:59:08 status half-installed zip 3.0-1ubuntu1
2009-10-28 20:59:08 status unpacked zip 3.0-1ubuntu1
2009-10-28 20:59:08 status unpacked zip 3.0-1ubuntu1
2009-10-28 20:59:08 install file-roller <none> 2.28.1-0ubuntu1
2009-10-28 20:59:08 status half-installed file-roller 2.28.1-0ubuntu1
2009-10-28 20:59:09 status unpacked file-roller 2.28.1-0ubuntu1
2009-10-28 20:59:09 status unpacked file-roller 2.28.1-0ubuntu1
2009-10-28 20:59:09 install firefox-3.5-branding <none> 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 install firefox-3.5 <none> 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 install firefox <none> 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 install xulrunner-1.9.1-gnome-support <none> 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 install firefox-3.5-gnome-support <none> 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 install firefox-gnome-support <none> 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status half-installed firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:09 status unpacked firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 20:59:10 install mscompress <none> 0.3-3
2009-10-28 20:59:10 status half-installed mscompress 0.3-3
2009-10-28 20:59:10 status unpacked mscompress 0.3-3
2009-10-28 20:59:10 status unpacked mscompress 0.3-3
2009-10-28 20:59:10 install foo2zjs <none> 20090623-0ubuntu5
2009-10-28 20:59:10 status half-installed foo2zjs 20090623-0ubuntu5
2009-10-28 20:59:10 status unpacked foo2zjs 20090623-0ubuntu5
2009-10-28 20:59:10 status unpacked foo2zjs 20090623-0ubuntu5
2009-10-28 20:59:10 install gcalctool <none> 5.28.1-0ubuntu1
2009-10-28 20:59:10 status half-installed gcalctool 5.28.1-0ubuntu1
2009-10-28 20:59:10 status unpacked gcalctool 5.28.1-0ubuntu1
2009-10-28 20:59:10 status unpacked gcalctool 5.28.1-0ubuntu1
2009-10-28 20:59:10 install libgomp1 <none> 4.4.1-4ubuntu8
2009-10-28 20:59:10 status half-installed libgomp1 4.4.1-4ubuntu8
2009-10-28 20:59:10 status unpacked libgomp1 4.4.1-4ubuntu8
2009-10-28 20:59:10 status unpacked libgomp1 4.4.1-4ubuntu8
2009-10-28 20:59:10 install gcc-4.4 <none> 4.4.1-4ubuntu8
2009-10-28 20:59:10 status half-installed gcc-4.4 4.4.1-4ubuntu8
2009-10-28 20:59:11 status unpacked gcc-4.4 4.4.1-4ubuntu8
2009-10-28 20:59:11 status unpacked gcc-4.4 4.4.1-4ubuntu8
2009-10-28 20:59:11 install gcc <none> 4:4.4.1-1ubuntu2
2009-10-28 20:59:11 status half-installed gcc 4:4.4.1-1ubuntu2
2009-10-28 20:59:11 status unpacked gcc 4:4.4.1-1ubuntu2
2009-10-28 20:59:11 status unpacked gcc 4:4.4.1-1ubuntu2
2009-10-28 20:59:11 install gconf-defaults-service <none> 2.28.0-0ubuntu2
2009-10-28 20:59:11 status half-installed gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 20:59:11 status unpacked gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 20:59:11 status unpacked gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 20:59:11 install gconf-editor <none> 2.28.0-0ubuntu1
2009-10-28 20:59:11 status half-installed gconf-editor 2.28.0-0ubuntu1
2009-10-28 20:59:11 status unpacked gconf-editor 2.28.0-0ubuntu1
2009-10-28 20:59:11 status unpacked gconf-editor 2.28.0-0ubuntu1
2009-10-28 20:59:12 install gdb <none> 7.0-0ubuntu1
2009-10-28 20:59:12 status half-installed gdb 7.0-0ubuntu1
2009-10-28 20:59:12 status unpacked gdb 7.0-0ubuntu1
2009-10-28 20:59:12 status unpacked gdb 7.0-0ubuntu1
2009-10-28 20:59:12 install gdebi-core <none> 0.5.9
2009-10-28 20:59:12 status half-installed gdebi-core 0.5.9
2009-10-28 20:59:12 status unpacked gdebi-core 0.5.9
2009-10-28 20:59:12 status unpacked gdebi-core 0.5.9
2009-10-28 20:59:12 install gdebi <none> 0.5.9
2009-10-28 20:59:12 status half-installed gdebi 0.5.9
2009-10-28 20:59:12 status half-installed gdebi 0.5.9
2009-10-28 20:59:12 status unpacked gdebi 0.5.9
2009-10-28 20:59:12 status unpacked gdebi 0.5.9
2009-10-28 20:59:12 install gnome-session-bin <none> 2.28.0-0ubuntu5
2009-10-28 20:59:12 status half-installed gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 20:59:12 status unpacked gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 20:59:12 status unpacked gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 20:59:12 install hal-info <none> 20090716-0ubuntu1
2009-10-28 20:59:12 status half-installed hal-info 20090716-0ubuntu1
2009-10-28 20:59:12 status unpacked hal-info 20090716-0ubuntu1
2009-10-28 20:59:12 status unpacked hal-info 20090716-0ubuntu1
2009-10-28 20:59:12 install hal <none> 0.5.13-1ubuntu8
2009-10-28 20:59:12 status half-installed hal 0.5.13-1ubuntu8
2009-10-28 20:59:13 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 20:59:13 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 20:59:13 install gdm <none> 2.28.1-0ubuntu1
2009-10-28 20:59:13 status half-installed gdm 2.28.1-0ubuntu1
2009-10-28 20:59:13 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 20:59:13 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 20:59:13 install gdm-guest-session <none> 0.14
2009-10-28 20:59:13 status half-installed gdm-guest-session 0.14
2009-10-28 20:59:13 status unpacked gdm-guest-session 0.14
2009-10-28 20:59:13 status unpacked gdm-guest-session 0.14
2009-10-28 20:59:13 install libgtksourceview2.0-common <none> 2.8.1-1
2009-10-28 20:59:13 status half-installed libgtksourceview2.0-common 2.8.1-1
2009-10-28 20:59:13 status unpacked libgtksourceview2.0-common 2.8.1-1
2009-10-28 20:59:13 status unpacked libgtksourceview2.0-common 2.8.1-1
2009-10-28 20:59:14 install libgtksourceview2.0-0 <none> 2.8.1-1
2009-10-28 20:59:14 status half-installed libgtksourceview2.0-0 2.8.1-1
2009-10-28 20:59:14 status unpacked libgtksourceview2.0-0 2.8.1-1
2009-10-28 20:59:14 status unpacked libgtksourceview2.0-0 2.8.1-1
2009-10-28 20:59:14 install gedit-common <none> 2.28.0-0ubuntu2
2009-10-28 20:59:14 status half-installed gedit-common 2.28.0-0ubuntu2
2009-10-28 20:59:14 status unpacked gedit-common 2.28.0-0ubuntu2
2009-10-28 20:59:14 status unpacked gedit-common 2.28.0-0ubuntu2
2009-10-28 20:59:14 install python-gtksourceview2 <none> 2.8.0-1
2009-10-28 20:59:14 status half-installed python-gtksourceview2 2.8.0-1
2009-10-28 20:59:14 status unpacked python-gtksourceview2 2.8.0-1
2009-10-28 20:59:14 status unpacked python-gtksourceview2 2.8.0-1
2009-10-28 20:59:14 install gedit <none> 2.28.0-0ubuntu2
2009-10-28 20:59:14 status half-installed gedit 2.28.0-0ubuntu2
2009-10-28 20:59:14 status unpacked gedit 2.28.0-0ubuntu2
2009-10-28 20:59:14 status unpacked gedit 2.28.0-0ubuntu2
2009-10-28 20:59:14 install libggz2 <none> 0.0.14.1-1build1
2009-10-28 20:59:14 status half-installed libggz2 0.0.14.1-1build1
2009-10-28 20:59:14 status unpacked libggz2 0.0.14.1-1build1
2009-10-28 20:59:14 status unpacked libggz2 0.0.14.1-1build1
2009-10-28 20:59:14 install libggzcore9 <none> 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status half-installed libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 install libggzmod4 <none> 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status half-installed libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 install ggzcore-bin <none> 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status half-installed ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 status unpacked ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 20:59:14 install ghostscript-x <none> 8.70.dfsg.1-0ubuntu3
2009-10-28 20:59:14 status half-installed ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 20:59:14 status unpacked ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 20:59:14 status unpacked ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 20:59:14 install libgimp2.0 <none> 2.6.7-1ubuntu1
2009-10-28 20:59:14 status half-installed libgimp2.0 2.6.7-1ubuntu1
2009-10-28 20:59:15 status unpacked libgimp2.0 2.6.7-1ubuntu1
2009-10-28 20:59:15 status unpacked libgimp2.0 2.6.7-1ubuntu1
2009-10-28 20:59:15 install gimp-data <none> 2.6.7-1ubuntu1
2009-10-28 20:59:15 status half-installed gimp-data 2.6.7-1ubuntu1
2009-10-28 20:59:15 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 20:59:15 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 20:59:15 install libbabl-0.0-0 <none> 0.0.22-1
2009-10-28 20:59:15 status half-installed libbabl-0.0-0 0.0.22-1
2009-10-28 20:59:15 status unpacked libbabl-0.0-0 0.0.22-1
2009-10-28 20:59:15 status unpacked libbabl-0.0-0 0.0.22-1
2009-10-28 20:59:15 install libilmbase6 <none> 1.0.1-3build1
2009-10-28 20:59:15 status half-installed libilmbase6 1.0.1-3build1
2009-10-28 20:59:15 status unpacked libilmbase6 1.0.1-3build1
2009-10-28 20:59:15 status unpacked libilmbase6 1.0.1-3build1
2009-10-28 20:59:15 install libopenexr6 <none> 1.6.1-4ubuntu3
2009-10-28 20:59:15 status half-installed libopenexr6 1.6.1-4ubuntu3
2009-10-28 20:59:15 status unpacked libopenexr6 1.6.1-4ubuntu3
2009-10-28 20:59:15 status unpacked libopenexr6 1.6.1-4ubuntu3
2009-10-28 20:59:15 install libsdl1.2debian-alsa <none> 1.2.13-4ubuntu4
2009-10-28 20:59:15 status half-installed libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 20:59:16 status unpacked libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 20:59:16 status unpacked libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 20:59:16 install libsdl1.2debian <none> 1.2.13-4ubuntu4
2009-10-28 20:59:16 status half-installed libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 20:59:16 status unpacked libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 20:59:16 status unpacked libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 20:59:16 install libgegl-0.0-0 <none> 0.0.22-0ubuntu3
2009-10-28 20:59:16 status half-installed libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 20:59:16 status unpacked libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 20:59:16 status unpacked libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 20:59:16 install libmng1 <none> 1.0.9-1build1
2009-10-28 20:59:16 status half-installed libmng1 1.0.9-1build1
2009-10-28 20:59:16 status unpacked libmng1 1.0.9-1build1
2009-10-28 20:59:16 status unpacked libmng1 1.0.9-1build1
2009-10-28 20:59:16 install libwmf0.2-7 <none> 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:16 status half-installed libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:16 status unpacked libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:16 status unpacked libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:16 install gimp <none> 2.6.7-1ubuntu1
2009-10-28 20:59:16 status half-installed gimp 2.6.7-1ubuntu1
2009-10-28 20:59:17 status unpacked gimp 2.6.7-1ubuntu1
2009-10-28 20:59:17 status unpacked gimp 2.6.7-1ubuntu1
2009-10-28 20:59:17 install python-launchpad-integration <none> 0.1.26
2009-10-28 20:59:17 status half-installed python-launchpad-integration 0.1.26
2009-10-28 20:59:17 status unpacked python-launchpad-integration 0.1.26
2009-10-28 20:59:17 status unpacked python-launchpad-integration 0.1.26
2009-10-28 20:59:17 install glchess <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:17 status half-installed glchess 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked glchess 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked glchess 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 install glines <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status half-installed glines 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked glines 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked glines 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 install gnect <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status half-installed gnect 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked gnect 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked gnect 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 install gnibbles <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status half-installed gnibbles 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked gnibbles 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status unpacked gnibbles 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 install gnobots2 <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:18 status half-installed gnobots2 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 status unpacked gnobots2 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 status unpacked gnobots2 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 install gtk2-engines <none> 1:2.18.4-1ubuntu1
2009-10-28 20:59:19 status half-installed gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 20:59:19 status unpacked gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 20:59:19 status unpacked gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 20:59:19 install gnome-accessibility-themes <none> 2.28.1-0ubuntu1
2009-10-28 20:59:19 status half-installed gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 20:59:19 status unpacked gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 20:59:19 status unpacked gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 20:59:19 install gnome-blackjack <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 status half-installed gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 status unpacked gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 status unpacked gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 20:59:19 install libgnome-bluetooth7 <none> 2.28.1-0ubuntu2
2009-10-28 20:59:19 status half-installed libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 20:59:19 status unpacked libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 20:59:19 status unpacked libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 20:59:19 install libopenobex1 <none> 1.5-2
2009-10-28 20:59:19 status half-installed libopenobex1 1.5-2
2009-10-28 20:59:19 status unpacked libopenobex1 1.5-2
2009-10-28 20:59:19 status unpacked libopenobex1 1.5-2
2009-10-28 20:59:19 install obexd-client <none> 0.14-0ubuntu1
2009-10-28 20:59:19 status half-installed obexd-client 0.14-0ubuntu1
2009-10-28 20:59:19 status unpacked obexd-client 0.14-0ubuntu1
2009-10-28 20:59:19 status unpacked obexd-client 0.14-0ubuntu1
2009-10-28 20:59:19 install gnome-bluetooth <none> 2.28.1-0ubuntu2
2009-10-28 20:59:19 status half-installed gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 20:59:20 status unpacked gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 20:59:20 status unpacked gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 20:59:20 install python-gst0.10 <none> 0.10.17-1
2009-10-28 20:59:20 status half-installed python-gst0.10 0.10.17-1
2009-10-28 20:59:20 status unpacked python-gst0.10 0.10.17-1
2009-10-28 20:59:20 status unpacked python-gst0.10 0.10.17-1
2009-10-28 20:59:20 install gnome-codec-install <none> 0.4.1ubuntu1
2009-10-28 20:59:20 status half-installed gnome-codec-install 0.4.1ubuntu1
2009-10-28 20:59:20 status unpacked gnome-codec-install 0.4.1ubuntu1
2009-10-28 20:59:20 status unpacked gnome-codec-install 0.4.1ubuntu1
2009-10-28 20:59:20 install libgdu-gtk0 <none> 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status half-installed libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status unpacked libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status unpacked libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 install gnome-disk-utility <none> 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status half-installed gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status unpacked gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 status unpacked gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 20:59:20 install gnome-sudoku <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:20 status half-installed gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 20:59:20 status unpacked gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 20:59:20 status unpacked gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 20:59:20 install libclutter-1.0-0 <none> 1.0.6-0ubuntu1
2009-10-28 20:59:20 status half-installed libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 20:59:21 status unpacked libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 20:59:21 status unpacked libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 20:59:21 install libclutter-gtk-0.10-0 <none> 0.10.2-0ubuntu1
2009-10-28 20:59:21 status half-installed libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 20:59:21 status unpacked libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 20:59:21 status unpacked libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 20:59:21 install gnometris <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status half-installed gnometris 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnometris 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnometris 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 install gnomine <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status half-installed gnomine 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnomine 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnomine 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 install gnotravex <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status half-installed gnotravex 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnotravex 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnotravex 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 install gnotski <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status half-installed gnotski 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnotski 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status unpacked gnotski 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 install gtali <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:21 status half-installed gtali 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked gtali 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked gtali 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 install iagno <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status half-installed iagno 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked iagno 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked iagno 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 install gnome-mahjongg <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status half-installed gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 install same-gnome <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status half-installed same-gnome 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked same-gnome 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status unpacked same-gnome 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 install gnome-games <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:22 status half-installed gnome-games 1:2.28.0-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-games 1:2.28.0-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-games 1:2.28.0-0ubuntu1
2009-10-28 20:59:23 install libgnome-mag2 <none> 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status half-installed libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status unpacked libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status unpacked libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 install gnome-mag <none> 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status half-installed gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 20:59:23 install gnome-media-common <none> 2.28.1-0ubuntu1
2009-10-28 20:59:23 status half-installed gnome-media-common 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-media-common 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-media-common 2.28.1-0ubuntu1
2009-10-28 20:59:23 install libgnome-media0 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:23 status half-installed libgnome-media0 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked libgnome-media0 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked libgnome-media0 2.28.1-0ubuntu1
2009-10-28 20:59:23 install gstreamer0.10-alsa <none> 0.10.25-2ubuntu1
2009-10-28 20:59:23 status half-installed gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 20:59:23 status unpacked gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 20:59:23 status unpacked gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 20:59:23 install gstreamer0.10-pulseaudio <none> 0.10.16-1ubuntu3
2009-10-28 20:59:23 status half-installed gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 20:59:23 status unpacked gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 20:59:23 status unpacked gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 20:59:23 install gnome-media <none> 2.28.1-0ubuntu1
2009-10-28 20:59:23 status half-installed gnome-media 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-media 2.28.1-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-media 2.28.1-0ubuntu1
2009-10-28 20:59:23 install whois <none> 4.7.34ubuntu2
2009-10-28 20:59:23 status half-installed whois 4.7.34ubuntu2
2009-10-28 20:59:23 status unpacked whois 4.7.34ubuntu2
2009-10-28 20:59:23 status unpacked whois 4.7.34ubuntu2
2009-10-28 20:59:23 install gnome-nettool <none> 2.28.0-0ubuntu1
2009-10-28 20:59:23 status half-installed gnome-nettool 2.28.0-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-nettool 2.28.0-0ubuntu1
2009-10-28 20:59:23 status unpacked gnome-nettool 2.28.0-0ubuntu1
2009-10-28 20:59:23 install libdotconf1.0 <none> 1.0.13-2ubuntu1
2009-10-28 20:59:23 status half-installed libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 20:59:24 status unpacked libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 20:59:24 status unpacked libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 20:59:24 install libspeechd2 <none> 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status half-installed libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 install speech-dispatcher <none> 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status half-installed speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 install python-speechd <none> 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status half-installed python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 status unpacked python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 20:59:24 install libgail-gnome-module <none> 1.20.1-1ubuntu1
2009-10-28 20:59:24 status half-installed libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 20:59:24 status unpacked libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 20:59:24 status unpacked libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 20:59:24 install python-pyatspi <none> 1.28.1-0ubuntu1
2009-10-28 20:59:24 status half-installed python-pyatspi 1.28.1-0ubuntu1
2009-10-28 20:59:24 status unpacked python-pyatspi 1.28.1-0ubuntu1
2009-10-28 20:59:24 status unpacked python-pyatspi 1.28.1-0ubuntu1
2009-10-28 20:59:24 install libbrlapi0.5 <none> 4.0-7ubuntu2
2009-10-28 20:59:24 status half-installed libbrlapi0.5 4.0-7ubuntu2
2009-10-28 20:59:24 status unpacked libbrlapi0.5 4.0-7ubuntu2
2009-10-28 20:59:24 status unpacked libbrlapi0.5 4.0-7ubuntu2
2009-10-28 20:59:24 install python-brlapi <none> 4.0-7ubuntu2
2009-10-28 20:59:24 status half-installed python-brlapi 4.0-7ubuntu2
2009-10-28 20:59:24 status unpacked python-brlapi 4.0-7ubuntu2
2009-10-28 20:59:24 status unpacked python-brlapi 4.0-7ubuntu2
2009-10-28 20:59:24 install gnome-orca <none> 2.28.1-0ubuntu1
2009-10-28 20:59:24 status half-installed gnome-orca 2.28.1-0ubuntu1
2009-10-28 20:59:24 status unpacked gnome-orca 2.28.1-0ubuntu1
2009-10-28 20:59:24 status unpacked gnome-orca 2.28.1-0ubuntu1
2009-10-28 20:59:25 install notify-osd <none> 0.9.24-0ubuntu1
2009-10-28 20:59:25 status half-installed notify-osd 0.9.24-0ubuntu1
2009-10-28 20:59:25 status unpacked notify-osd 0.9.24-0ubuntu1
2009-10-28 20:59:25 status unpacked notify-osd 0.9.24-0ubuntu1
2009-10-28 20:59:25 install gnome-power-manager <none> 2.28.1-0ubuntu1
2009-10-28 20:59:25 status half-installed gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 20:59:25 status unpacked gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 20:59:25 status unpacked gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 20:59:26 install gnome-screensaver <none> 2.28.0-0ubuntu3
2009-10-28 20:59:26 status half-installed gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 20:59:26 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 20:59:26 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 20:59:26 install nautilus-data <none> 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 status half-installed nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 status half-installed nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 status unpacked nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 status unpacked nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 install nautilus <none> 1:2.28.1-0ubuntu1
2009-10-28 20:59:26 status half-installed nautilus 1:2.28.1-0ubuntu1
2009-10-28 20:59:27 status unpacked nautilus 1:2.28.1-0ubuntu1
2009-10-28 20:59:27 status unpacked nautilus 1:2.28.1-0ubuntu1
2009-10-28 20:59:27 install zenity <none> 2.28.0-0ubuntu2
2009-10-28 20:59:27 status half-installed zenity 2.28.0-0ubuntu2
2009-10-28 20:59:27 status unpacked zenity 2.28.0-0ubuntu2
2009-10-28 20:59:27 status unpacked zenity 2.28.0-0ubuntu2
2009-10-28 20:59:27 install metacity <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:27 status half-installed metacity 1:2.28.0-0ubuntu1
2009-10-28 20:59:27 status unpacked metacity 1:2.28.0-0ubuntu1
2009-10-28 20:59:27 status unpacked metacity 1:2.28.0-0ubuntu1
2009-10-28 20:59:27 install gnome-session <none> 2.28.0-0ubuntu5
2009-10-28 20:59:27 status half-installed gnome-session 2.28.0-0ubuntu5
2009-10-28 20:59:27 status unpacked gnome-session 2.28.0-0ubuntu5
2009-10-28 20:59:27 status unpacked gnome-session 2.28.0-0ubuntu5
2009-10-28 20:59:27 install gnome-session-canberra <none> 0.15-0ubuntu7
2009-10-28 20:59:27 status half-installed gnome-session-canberra 0.15-0ubuntu7
2009-10-28 20:59:27 status unpacked gnome-session-canberra 0.15-0ubuntu7
2009-10-28 20:59:27 status unpacked gnome-session-canberra 0.15-0ubuntu7
2009-10-28 20:59:27 install libglibmm-2.4-1c2a <none> 2.22.1-2
2009-10-28 20:59:27 status half-installed libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 20:59:27 status unpacked libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 20:59:27 status unpacked libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 20:59:27 install libcairomm-1.0-1 <none> 1.8.0-1build1
2009-10-28 20:59:27 status half-installed libcairomm-1.0-1 1.8.0-1build1
2009-10-28 20:59:27 status unpacked libcairomm-1.0-1 1.8.0-1build1
2009-10-28 20:59:28 status unpacked libcairomm-1.0-1 1.8.0-1build1
2009-10-28 20:59:28 install libpangomm-1.4-1 <none> 2.26.0-0ubuntu2
2009-10-28 20:59:28 status half-installed libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 20:59:28 status unpacked libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 20:59:28 status unpacked libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 20:59:28 install libgtkmm-2.4-1c2a <none> 1:2.18.2-1
2009-10-28 20:59:28 status half-installed libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 20:59:28 status unpacked libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 20:59:28 status unpacked libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 20:59:28 install gnome-system-monitor <none> 2.28.0-0ubuntu1
2009-10-28 20:59:28 status half-installed gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 20:59:28 install gnome-terminal-data <none> 2.28.1-0ubuntu1
2009-10-28 20:59:28 status half-installed gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 20:59:28 install gnome-terminal <none> 2.28.1-0ubuntu1
2009-10-28 20:59:28 status half-installed gnome-terminal 2.28.1-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-terminal 2.28.1-0ubuntu1
2009-10-28 20:59:28 status unpacked gnome-terminal 2.28.1-0ubuntu1
2009-10-28 20:59:28 install gtk2-engines-pixbuf <none> 2.18.3-1
2009-10-28 20:59:28 status half-installed gtk2-engines-pixbuf 2.18.3-1
2009-10-28 20:59:29 status unpacked gtk2-engines-pixbuf 2.18.3-1
2009-10-28 20:59:29 status unpacked gtk2-engines-pixbuf 2.18.3-1
2009-10-28 20:59:29 install gnome-themes-selected <none> 2.28.1-0ubuntu1
2009-10-28 20:59:29 status half-installed gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 20:59:29 status unpacked gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 20:59:29 status unpacked gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 20:59:29 install gtk2-engines-murrine <none> 0.90.3-1ubuntu1
2009-10-28 20:59:29 status half-installed gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 20:59:29 status unpacked gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 20:59:29 status unpacked gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 20:59:29 install humanity-icon-theme <none> 0.4.1ubuntu5
2009-10-28 20:59:29 status half-installed humanity-icon-theme 0.4.1ubuntu5
2009-10-28 20:59:31 status unpacked humanity-icon-theme 0.4.1ubuntu5
2009-10-28 20:59:31 status unpacked humanity-icon-theme 0.4.1ubuntu5
2009-10-28 20:59:31 install gnome-themes-ubuntu <none> 0.5.1
2009-10-28 20:59:31 status half-installed gnome-themes-ubuntu 0.5.1
2009-10-28 20:59:31 status unpacked gnome-themes-ubuntu 0.5.1
2009-10-28 20:59:31 status unpacked gnome-themes-ubuntu 0.5.1
2009-10-28 20:59:31 install libgdict-1.0-6 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:31 status half-installed libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 20:59:31 status unpacked libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 20:59:31 status unpacked libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 20:59:31 install gnome-utils <none> 2.28.1-0ubuntu1
2009-10-28 20:59:31 status half-installed gnome-utils 2.28.1-0ubuntu1
2009-10-28 20:59:32 status unpacked gnome-utils 2.28.1-0ubuntu1
2009-10-28 20:59:32 status unpacked gnome-utils 2.28.1-0ubuntu1
2009-10-28 20:59:32 install grub-common <none> 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status half-installed grub-common 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 install grub-pc <none> 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status half-installed grub-pc 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status unpacked grub-pc 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 status unpacked grub-pc 1.97~beta4-1ubuntu3
2009-10-28 20:59:32 install pkg-config <none> 0.22-1build1
2009-10-28 20:59:32 status half-installed pkg-config 0.22-1build1
2009-10-28 20:59:32 status unpacked pkg-config 0.22-1build1
2009-10-28 20:59:32 status unpacked pkg-config 0.22-1build1
2009-10-28 20:59:32 install gstreamer0.10-tools <none> 0.10.25-2
2009-10-28 20:59:32 status half-installed gstreamer0.10-tools 0.10.25-2
2009-10-28 20:59:32 status unpacked gstreamer0.10-tools 0.10.25-2
2009-10-28 20:59:32 status unpacked gstreamer0.10-tools 0.10.25-2
2009-10-28 20:59:32 install gstreamer0.10-plugins-base-apps <none> 0.10.25-2ubuntu1
2009-10-28 20:59:32 status half-installed gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 20:59:32 status unpacked gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 20:59:32 status unpacked gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 20:59:32 install gstreamer0.10-x <none> 0.10.25-2ubuntu1
2009-10-28 20:59:32 status half-installed gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 20:59:33 status unpacked gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 20:59:33 status unpacked gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 20:59:33 install gucharmap <none> 1:2.28.0-0ubuntu1
2009-10-28 20:59:33 status half-installed gucharmap 1:2.28.0-0ubuntu1
2009-10-28 20:59:33 status unpacked gucharmap 1:2.28.0-0ubuntu1
2009-10-28 20:59:33 status unpacked gucharmap 1:2.28.0-0ubuntu1
2009-10-28 20:59:33 install libarchive1 <none> 2.6.2-1
2009-10-28 20:59:33 status half-installed libarchive1 2.6.2-1
2009-10-28 20:59:33 status unpacked libarchive1 2.6.2-1
2009-10-28 20:59:33 status unpacked libarchive1 2.6.2-1
2009-10-28 20:59:33 install libcdio7 <none> 0.78.2+dfsg1-3
2009-10-28 20:59:33 status half-installed libcdio7 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio7 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio7 0.78.2+dfsg1-3
2009-10-28 20:59:33 install libcdio-cdda0 <none> 0.78.2+dfsg1-3
2009-10-28 20:59:33 status half-installed libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 20:59:33 install libcdio-paranoia0 <none> 0.78.2+dfsg1-3
2009-10-28 20:59:33 status half-installed libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 20:59:33 status unpacked libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 20:59:33 install libtalloc1 <none> 1.4.0~git20090718-1
2009-10-28 20:59:33 status half-installed libtalloc1 1.4.0~git20090718-1
2009-10-28 20:59:33 status unpacked libtalloc1 1.4.0~git20090718-1
2009-10-28 20:59:33 status unpacked libtalloc1 1.4.0~git20090718-1
2009-10-28 20:59:33 install libwbclient0 <none> 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status half-installed libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status unpacked libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status unpacked libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 install libsmbclient <none> 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status half-installed libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status unpacked libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 20:59:33 status unpacked libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 20:59:34 install gvfs-backends <none> 1.4.1-0ubuntu1
2009-10-28 20:59:34 status half-installed gvfs-backends 1.4.1-0ubuntu1
2009-10-28 20:59:34 status unpacked gvfs-backends 1.4.1-0ubuntu1
2009-10-28 20:59:34 status unpacked gvfs-backends 1.4.1-0ubuntu1
2009-10-28 20:59:34 install gvfs-fuse <none> 1.4.1-0ubuntu1
2009-10-28 20:59:34 status half-installed gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 20:59:34 status unpacked gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 20:59:34 status unpacked gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 20:59:34 install hpijs <none> 3.9.8-1ubuntu2
2009-10-28 20:59:34 status half-installed hpijs 3.9.8-1ubuntu2
2009-10-28 20:59:34 status unpacked hpijs 3.9.8-1ubuntu2
2009-10-28 20:59:34 status unpacked hpijs 3.9.8-1ubuntu2
2009-10-28 20:59:34 install human-theme <none> 0.37
2009-10-28 20:59:34 status half-installed human-theme 0.37
2009-10-28 20:59:34 status unpacked human-theme 0.37
2009-10-28 20:59:34 status unpacked human-theme 0.37
2009-10-28 20:59:34 install hunspell-en-us <none> 20070829-2ubuntu4
2009-10-28 20:59:34 status half-installed hunspell-en-us 20070829-2ubuntu4
2009-10-28 20:59:34 status unpacked hunspell-en-us 20070829-2ubuntu4
2009-10-28 20:59:34 status unpacked hunspell-en-us 20070829-2ubuntu4
2009-10-28 20:59:35 install libibus1 <none> 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status half-installed libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 install im-switch <none> 1.16ubuntu1
2009-10-28 20:59:35 status half-installed im-switch 1.16ubuntu1
2009-10-28 20:59:35 status unpacked im-switch 1.16ubuntu1
2009-10-28 20:59:35 status unpacked im-switch 1.16ubuntu1
2009-10-28 20:59:35 install python-ibus <none> 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status half-installed python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 install python-rsvg <none> 2.28.0-0ubuntu1
2009-10-28 20:59:35 status half-installed python-rsvg 2.28.0-0ubuntu1
2009-10-28 20:59:35 status unpacked python-rsvg 2.28.0-0ubuntu1
2009-10-28 20:59:35 status unpacked python-rsvg 2.28.0-0ubuntu1
2009-10-28 20:59:35 install ibus <none> 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status half-installed ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked ibus 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 install ibus-gtk <none> 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status half-installed ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 status unpacked ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 20:59:35 install libanthy0 <none> 9100h-0ubuntu1
2009-10-28 20:59:35 status half-installed libanthy0 9100h-0ubuntu1
2009-10-28 20:59:35 status unpacked libanthy0 9100h-0ubuntu1
2009-10-28 20:59:35 status unpacked libanthy0 9100h-0ubuntu1
2009-10-28 20:59:35 install libgd2-xpm <none> 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 20:59:35 status half-installed libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 20:59:35 status unpacked libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 20:59:35 status unpacked libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 20:59:36 install libotf0 <none> 0.9.9-1
2009-10-28 20:59:36 status half-installed libotf0 0.9.9-1
2009-10-28 20:59:36 status unpacked libotf0 0.9.9-1
2009-10-28 20:59:36 status unpacked libotf0 0.9.9-1
2009-10-28 20:59:36 install libm17n-0 <none> 1.5.4-1ubuntu1
2009-10-28 20:59:36 status half-installed libm17n-0 1.5.4-1ubuntu1
2009-10-28 20:59:36 status unpacked libm17n-0 1.5.4-1ubuntu1
2009-10-28 20:59:36 status unpacked libm17n-0 1.5.4-1ubuntu1
2009-10-28 20:59:36 install ibus-m17n <none> 1.2.0.20090930-1
2009-10-28 20:59:36 status half-installed ibus-m17n 1.2.0.20090930-1
2009-10-28 20:59:36 status unpacked ibus-m17n 1.2.0.20090930-1
2009-10-28 20:59:36 status unpacked ibus-m17n 1.2.0.20090930-1
2009-10-28 20:59:36 install ibus-table <none> 1.2.0.20090625-1
2009-10-28 20:59:36 status half-installed ibus-table 1.2.0.20090625-1
2009-10-28 20:59:36 status unpacked ibus-table 1.2.0.20090625-1
2009-10-28 20:59:36 status unpacked ibus-table 1.2.0.20090625-1
2009-10-28 20:59:36 install libdbusmenu-glib0 <none> 0.1.6-0ubuntu1
2009-10-28 20:59:36 status half-installed libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 20:59:36 status unpacked libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 20:59:36 status unpacked libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 20:59:36 install libdbusmenu-gtk0 <none> 0.1.6-0ubuntu1
2009-10-28 20:59:36 status half-installed libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 20:59:36 status unpacked libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 20:59:36 status unpacked libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 20:59:36 install indicator-messages <none> 0.2.6-0ubuntu1
2009-10-28 20:59:36 status half-installed indicator-messages 0.2.6-0ubuntu1
2009-10-28 20:59:36 status unpacked indicator-messages 0.2.6-0ubuntu1
2009-10-28 20:59:36 status unpacked indicator-messages 0.2.6-0ubuntu1
2009-10-28 20:59:36 install indicator-applet <none> 0.2.0-0ubuntu2
2009-10-28 20:59:36 status half-installed indicator-applet 0.2.0-0ubuntu2
2009-10-28 20:59:36 status unpacked indicator-applet 0.2.0-0ubuntu2
2009-10-28 20:59:36 status unpacked indicator-applet 0.2.0-0ubuntu2
2009-10-28 20:59:37 install indicator-session <none> 0.1.7-0ubuntu3
2009-10-28 20:59:37 status half-installed indicator-session 0.1.7-0ubuntu3
2009-10-28 20:59:37 status unpacked indicator-session 0.1.7-0ubuntu3
2009-10-28 20:59:37 status unpacked indicator-session 0.1.7-0ubuntu3
2009-10-28 20:59:37 install indicator-applet-session <none> 0.2.0-0ubuntu2
2009-10-28 20:59:37 status half-installed indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 20:59:37 status unpacked indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 20:59:37 status unpacked indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 20:59:37 install inputattach <none> 1.23-0ubuntu3
2009-10-28 20:59:37 status half-installed inputattach 1.23-0ubuntu3
2009-10-28 20:59:37 status unpacked inputattach 1.23-0ubuntu3
2009-10-28 20:59:37 status unpacked inputattach 1.23-0ubuntu3
2009-10-28 20:59:37 install python-xkit <none> 0.4.2
2009-10-28 20:59:37 status half-installed python-xkit 0.4.2
2009-10-28 20:59:37 status unpacked python-xkit 0.4.2
2009-10-28 20:59:37 status unpacked python-xkit 0.4.2
2009-10-28 20:59:37 install jockey-common <none> 0.5.5-0ubuntu2
2009-10-28 20:59:37 status half-installed jockey-common 0.5.5-0ubuntu2
2009-10-28 20:59:37 status unpacked jockey-common 0.5.5-0ubuntu2
2009-10-28 20:59:37 status unpacked jockey-common 0.5.5-0ubuntu2
2009-10-28 20:59:37 install python-notify <none> 0.1.1-2build2
2009-10-28 20:59:37 status half-installed python-notify 0.1.1-2build2
2009-10-28 20:59:37 status unpacked python-notify 0.1.1-2build2
2009-10-28 20:59:37 status unpacked python-notify 0.1.1-2build2
2009-10-28 20:59:37 install jockey-gtk <none> 0.5.5-0ubuntu2
2009-10-28 20:59:37 status half-installed jockey-gtk 0.5.5-0ubuntu2
2009-10-28 20:59:37 status unpacked jockey-gtk 0.5.5-0ubuntu2
2009-10-28 20:59:37 status unpacked jockey-gtk 0.5.5-0ubuntu2
2009-10-28 20:59:37 install kerneloops-daemon <none> 0.12+git20090217-1ubuntu4
2009-10-28 20:59:37 status half-installed kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 20:59:37 status unpacked kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 20:59:37 status unpacked kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 20:59:37 install language-selector-common <none> 0.4.18
2009-10-28 20:59:37 status half-installed language-selector-common 0.4.18
2009-10-28 20:59:38 status unpacked language-selector-common 0.4.18
2009-10-28 20:59:38 status unpacked language-selector-common 0.4.18
2009-10-28 20:59:38 install language-selector <none> 0.4.18
2009-10-28 20:59:38 status half-installed language-selector 0.4.18
2009-10-28 20:59:38 status unpacked language-selector 0.4.18
2009-10-28 20:59:38 status unpacked language-selector 0.4.18
2009-10-28 20:59:38 install launchpad-integration <none> 0.1.26
2009-10-28 20:59:38 status half-installed launchpad-integration 0.1.26
2009-10-28 20:59:38 status unpacked launchpad-integration 0.1.26
2009-10-28 20:59:38 status unpacked launchpad-integration 0.1.26
2009-10-28 20:59:38 install lftp <none> 3.7.15-1ubuntu2
2009-10-28 20:59:38 status half-installed lftp 3.7.15-1ubuntu2
2009-10-28 20:59:38 status unpacked lftp 3.7.15-1ubuntu2
2009-10-28 20:59:38 status unpacked lftp 3.7.15-1ubuntu2
2009-10-28 20:59:38 install libsamplerate0 <none> 0.1.7-2
2009-10-28 20:59:38 status half-installed libsamplerate0 0.1.7-2
2009-10-28 20:59:38 status unpacked libsamplerate0 0.1.7-2
2009-10-28 20:59:38 status unpacked libsamplerate0 0.1.7-2
2009-10-28 20:59:38 install libasound2-plugins <none> 1.0.20-1ubuntu8
2009-10-28 20:59:38 status half-installed libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 20:59:38 status unpacked libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 20:59:38 status unpacked libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 20:59:38 install libatk1.0-data <none> 1.28.0-0ubuntu1
2009-10-28 20:59:38 status half-installed libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 20:59:39 status unpacked libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 20:59:39 status unpacked libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 20:59:39 install libavahi-gobject0 <none> 0.6.25-1ubuntu5
2009-10-28 20:59:39 status half-installed libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 20:59:39 status unpacked libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 20:59:39 status unpacked libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 20:59:39 install libavahi-ui0 <none> 0.6.25-1ubuntu5
2009-10-28 20:59:39 status half-installed libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 20:59:39 status unpacked libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 20:59:39 status unpacked libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 20:59:39 install libc-dev-bin <none> 2.10.1-0ubuntu15
2009-10-28 20:59:39 status half-installed libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 20:59:39 status unpacked libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 20:59:39 status unpacked libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 20:59:39 install linux-libc-dev <none> 2.6.31-14.48
2009-10-28 20:59:39 status half-installed linux-libc-dev 2.6.31-14.48
2009-10-28 20:59:39 status unpacked linux-libc-dev 2.6.31-14.48
2009-10-28 20:59:39 status unpacked linux-libc-dev 2.6.31-14.48
2009-10-28 20:59:39 install libc6-dev <none> 2.10.1-0ubuntu15
2009-10-28 20:59:39 status half-installed libc6-dev 2.10.1-0ubuntu15
2009-10-28 20:59:41 status unpacked libc6-dev 2.10.1-0ubuntu15
2009-10-28 20:59:41 status unpacked libc6-dev 2.10.1-0ubuntu15
2009-10-28 20:59:41 install libcairo-perl <none> 1.061-1
2009-10-28 20:59:41 status half-installed libcairo-perl 1.061-1
2009-10-28 20:59:41 status unpacked libcairo-perl 1.061-1
2009-10-28 20:59:41 status unpacked libcairo-perl 1.061-1
2009-10-28 20:59:41 install libcanberra-gtk-module <none> 0.15-0ubuntu7
2009-10-28 20:59:41 status half-installed libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 20:59:41 status unpacked libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 20:59:41 status unpacked libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 20:59:41 install libspeexdsp1 <none> 1.2~rc1-1
2009-10-28 20:59:41 status half-installed libspeexdsp1 1.2~rc1-1
2009-10-28 20:59:41 status unpacked libspeexdsp1 1.2~rc1-1
2009-10-28 20:59:42 status unpacked libspeexdsp1 1.2~rc1-1
2009-10-28 20:59:42 install pulseaudio-module-udev <none> 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status half-installed pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status unpacked pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status unpacked pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 install pulseaudio <none> 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status half-installed pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 20:59:42 install libcanberra-pulse <none> 0.15-0ubuntu7
2009-10-28 20:59:42 status half-installed libcanberra-pulse 0.15-0ubuntu7
2009-10-28 20:59:42 status unpacked libcanberra-pulse 0.15-0ubuntu7
2009-10-28 20:59:42 status unpacked libcanberra-pulse 0.15-0ubuntu7
2009-10-28 20:59:42 install libcolamd2.7.1 <none> 1:3.4.0-1ubuntu2
2009-10-28 20:59:42 status half-installed libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 20:59:42 status unpacked libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 20:59:42 status unpacked libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 20:59:42 install libcryptui0 <none> 2.28.1-0ubuntu1
2009-10-28 20:59:42 status half-installed libcryptui0 2.28.1-0ubuntu1
2009-10-28 20:59:42 status unpacked libcryptui0 2.28.1-0ubuntu1
2009-10-28 20:59:42 status unpacked libcryptui0 2.28.1-0ubuntu1
2009-10-28 20:59:42 install libdrm-intel1 <none> 2.4.14-1ubuntu1
2009-10-28 20:59:42 status half-installed libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 20:59:42 status unpacked libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 20:59:42 status unpacked libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 20:59:42 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2009-10-28 20:59:42 status half-configured shared-mime-info 0.70-0ubuntu1
2009-10-28 20:59:43 status installed shared-mime-info 0.70-0ubuntu1
2009-10-28 20:59:43 startup archives unpack
2009-10-28 20:59:43 install libdrm-radeon1 <none> 2.4.14-1ubuntu1
2009-10-28 20:59:43 status half-installed libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 20:59:43 status unpacked libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 20:59:43 status unpacked libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 20:59:43 install libevent-1.4-2 <none> 1.4.11-stable-1
2009-10-28 20:59:43 status half-installed libevent-1.4-2 1.4.11-stable-1
2009-10-28 20:59:43 status unpacked libevent-1.4-2 1.4.11-stable-1
2009-10-28 20:59:43 status unpacked libevent-1.4-2 1.4.11-stable-1
2009-10-28 20:59:43 install libfreezethaw-perl <none> 0.45-1
2009-10-28 20:59:43 status half-installed libfreezethaw-perl 0.45-1
2009-10-28 20:59:44 status unpacked libfreezethaw-perl 0.45-1
2009-10-28 20:59:44 status unpacked libfreezethaw-perl 0.45-1
2009-10-28 20:59:44 install libgadu3 <none> 1:1.8.0+r592-3
2009-10-28 20:59:44 status half-installed libgadu3 1:1.8.0+r592-3
2009-10-28 20:59:44 status unpacked libgadu3 1:1.8.0+r592-3
2009-10-28 20:59:44 status unpacked libgadu3 1:1.8.0+r592-3
2009-10-28 20:59:44 install libgdata-common <none> 0.4.0-1
2009-10-28 20:59:44 status half-installed libgdata-common 0.4.0-1
2009-10-28 20:59:44 status unpacked libgdata-common 0.4.0-1
2009-10-28 20:59:44 status unpacked libgdata-common 0.4.0-1
2009-10-28 20:59:44 install libgdata5 <none> 0.4.0-1
2009-10-28 20:59:44 status half-installed libgdata5 0.4.0-1
2009-10-28 20:59:44 status unpacked libgdata5 0.4.0-1
2009-10-28 20:59:44 status unpacked libgdata5 0.4.0-1
2009-10-28 20:59:44 install libglib-perl <none> 1:1.221-1
2009-10-28 20:59:44 status half-installed libglib-perl 1:1.221-1
2009-10-28 20:59:44 status unpacked libglib-perl 1:1.221-1
2009-10-28 20:59:44 status unpacked libglib-perl 1:1.221-1
2009-10-28 20:59:44 install libgmime-2.0-2a <none> 2.2.22-4
2009-10-28 20:59:44 status half-installed libgmime-2.0-2a 2.2.22-4
2009-10-28 20:59:44 status unpacked libgmime-2.0-2a 2.2.22-4
2009-10-28 20:59:44 status unpacked libgmime-2.0-2a 2.2.22-4
2009-10-28 20:59:44 install libgmime2.2a-cil <none> 2.2.22-4
2009-10-28 20:59:44 status half-installed libgmime2.2a-cil 2.2.22-4
2009-10-28 20:59:44 status unpacked libgmime2.2a-cil 2.2.22-4
2009-10-28 20:59:44 status unpacked libgmime2.2a-cil 2.2.22-4
2009-10-28 20:59:44 install libpango-perl <none> 1.220-1
2009-10-28 20:59:44 status half-installed libpango-perl 1.220-1
2009-10-28 20:59:45 status unpacked libpango-perl 1.220-1
2009-10-28 20:59:45 status unpacked libpango-perl 1.220-1
2009-10-28 20:59:45 install libgtk2-perl <none> 1:1.221-4
2009-10-28 20:59:45 status half-installed libgtk2-perl 1:1.221-4
2009-10-28 20:59:45 status unpacked libgtk2-perl 1:1.221-4
2009-10-28 20:59:45 status unpacked libgtk2-perl 1:1.221-4
2009-10-28 20:59:45 install libgnome2-canvas-perl <none> 1.002-2
2009-10-28 20:59:45 status half-installed libgnome2-canvas-perl 1.002-2
2009-10-28 20:59:45 status unpacked libgnome2-canvas-perl 1.002-2
2009-10-28 20:59:45 status unpacked libgnome2-canvas-perl 1.002-2
2009-10-28 20:59:45 install libgnome2-vfs-perl <none> 1.081-1
2009-10-28 20:59:45 status half-installed libgnome2-vfs-perl 1.081-1
2009-10-28 20:59:45 status unpacked libgnome2-vfs-perl 1.081-1
2009-10-28 20:59:45 status unpacked libgnome2-vfs-perl 1.081-1
2009-10-28 20:59:45 install libgnome2-perl <none> 1.042-2
2009-10-28 20:59:45 status half-installed libgnome2-perl 1.042-2
2009-10-28 20:59:45 status unpacked libgnome2-perl 1.042-2
2009-10-28 20:59:45 status unpacked libgnome2-perl 1.042-2
2009-10-28 20:59:45 install libgnomepanel2.24-cil <none> 2.26.0-1
2009-10-28 20:59:45 status half-installed libgnomepanel2.24-cil 2.26.0-1
2009-10-28 20:59:45 status unpacked libgnomepanel2.24-cil 2.26.0-1
2009-10-28 20:59:45 status unpacked libgnomepanel2.24-cil 2.26.0-1
2009-10-28 20:59:45 install libgnomevfs2-extra <none> 1:2.24.2-1ubuntu1
2009-10-28 20:59:45 status half-installed libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 20:59:45 status unpacked libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 20:59:45 status unpacked libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 20:59:46 install libpth20 <none> 2.0.7-12
2009-10-28 20:59:46 status half-installed libpth20 2.0.7-12
2009-10-28 20:59:46 status unpacked libpth20 2.0.7-12
2009-10-28 20:59:46 status unpacked libpth20 2.0.7-12
2009-10-28 20:59:46 install libgpgme11 <none> 1.1.8-2ubuntu3
2009-10-28 20:59:46 status half-installed libgpgme11 1.1.8-2ubuntu3
2009-10-28 20:59:46 status unpacked libgpgme11 1.1.8-2ubuntu3
2009-10-28 20:59:46 status unpacked libgpgme11 1.1.8-2ubuntu3
2009-10-28 20:59:46 install libgpod4 <none> 0.7.2-1ubuntu1
2009-10-28 20:59:46 status half-installed libgpod4 0.7.2-1ubuntu1
2009-10-28 20:59:46 status unpacked libgpod4 0.7.2-1ubuntu1
2009-10-28 20:59:46 status unpacked libgpod4 0.7.2-1ubuntu1
2009-10-28 20:59:46 install libgpod-common <none> 0.7.2-1ubuntu1
2009-10-28 20:59:46 status half-installed libgpod-common 0.7.2-1ubuntu1
2009-10-28 20:59:46 status unpacked libgpod-common 0.7.2-1ubuntu1
2009-10-28 20:59:46 status unpacked libgpod-common 0.7.2-1ubuntu1
2009-10-28 20:59:46 install libgraphviz4 <none> 2.20.2-3ubuntu5
2009-10-28 20:59:46 status half-installed libgraphviz4 2.20.2-3ubuntu5
2009-10-28 20:59:46 status unpacked libgraphviz4 2.20.2-3ubuntu5
2009-10-28 20:59:46 status unpacked libgraphviz4 2.20.2-3ubuntu5
2009-10-28 20:59:46 install libgtk-vnc-1.0-0 <none> 0.3.9-1ubuntu2
2009-10-28 20:59:46 status half-installed libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 20:59:46 status unpacked libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 20:59:46 status unpacked libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 20:59:46 install libgtkhtml2-0 <none> 2.11.1-2ubuntu2
2009-10-28 20:59:46 status half-installed libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 20:59:46 status unpacked libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 20:59:46 status unpacked libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 20:59:46 install libgtkspell0 <none> 2.0.15-0ubuntu1
2009-10-28 20:59:46 status half-installed libgtkspell0 2.0.15-0ubuntu1
2009-10-28 20:59:46 status unpacked libgtkspell0 2.0.15-0ubuntu1
2009-10-28 20:59:46 status unpacked libgtkspell0 2.0.15-0ubuntu1
2009-10-28 20:59:46 install libiw29 <none> 29-2ubuntu6
2009-10-28 20:59:46 status half-installed libiw29 29-2ubuntu6
2009-10-28 20:59:47 status unpacked libiw29 29-2ubuntu6
2009-10-28 20:59:47 status unpacked libiw29 29-2ubuntu6
2009-10-28 20:59:47 install libloudmouth1-0 <none> 1.4.3-4
2009-10-28 20:59:47 status half-installed libloudmouth1-0 1.4.3-4
2009-10-28 20:59:47 status unpacked libloudmouth1-0 1.4.3-4
2009-10-28 20:59:47 status unpacked libloudmouth1-0 1.4.3-4
2009-10-28 20:59:47 install libmagickwand2 <none> 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status half-installed libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status unpacked libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status unpacked libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 install libmagickcore2 <none> 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status half-installed libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status unpacked libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 status unpacked libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 20:59:47 install libmeanwhile1 <none> 1.0.2-3build1
2009-10-28 20:59:47 status half-installed libmeanwhile1 1.0.2-3build1
2009-10-28 20:59:47 status unpacked libmeanwhile1 1.0.2-3build1
2009-10-28 20:59:47 status unpacked libmeanwhile1 1.0.2-3build1
2009-10-28 20:59:47 install libmono-i18n-west2.0-cil <none> 2.4.2.3+dfsg-2
2009-10-28 20:59:47 status half-installed libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:47 status unpacked libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:47 status unpacked libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 20:59:47 install libmtp8 <none> 0.3.7-3ubuntu2
2009-10-28 20:59:47 status half-installed libmtp8 0.3.7-3ubuntu2
2009-10-28 20:59:47 status unpacked libmtp8 0.3.7-3ubuntu2
2009-10-28 20:59:47 status unpacked libmtp8 0.3.7-3ubuntu2
2009-10-28 20:59:47 install libmusicbrainz4c2a <none> 2.1.5-2ubuntu1
2009-10-28 20:59:47 status half-installed libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 20:59:48 status unpacked libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 20:59:48 status unpacked libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 20:59:48 install libxml-twig-perl <none> 1:3.32-3ubuntu1
2009-10-28 20:59:48 status half-installed libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 20:59:48 status unpacked libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 20:59:48 status unpacked libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 20:59:48 install libnet-dbus-perl <none> 0.33.6-1build2
2009-10-28 20:59:48 status half-installed libnet-dbus-perl 0.33.6-1build2
2009-10-28 20:59:48 status unpacked libnet-dbus-perl 0.33.6-1build2
2009-10-28 20:59:48 status unpacked libnet-dbus-perl 0.33.6-1build2
2009-10-28 20:59:48 install libnss-mdns <none> 0.10-3ubuntu3
2009-10-28 20:59:48 status half-installed libnss-mdns 0.10-3ubuntu3
2009-10-28 20:59:48 status unpacked libnss-mdns 0.10-3ubuntu3
2009-10-28 20:59:48 status unpacked libnss-mdns 0.10-3ubuntu3
2009-10-28 20:59:48 install system-tools-backends <none> 2.8.2-1
2009-10-28 20:59:48 status half-installed system-tools-backends 2.8.2-1
2009-10-28 20:59:48 status unpacked system-tools-backends 2.8.2-1
2009-10-28 20:59:48 status unpacked system-tools-backends 2.8.2-1
2009-10-28 20:59:48 install liboobs-1-4 <none> 2.22.2-0ubuntu1
2009-10-28 20:59:48 status half-installed liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 20:59:48 status unpacked liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 20:59:48 status unpacked liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 20:59:48 install libpam-ck-connector <none> 0.3.1-0ubuntu2
2009-10-28 20:59:48 status half-installed libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 20:59:49 status unpacked libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 20:59:49 status unpacked libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 20:59:49 install libpam-gnome-keyring <none> 2.28.1-0ubuntu1
2009-10-28 20:59:49 status half-installed libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:59:49 status unpacked libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:59:49 status unpacked libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 20:59:49 install libpaper-utils <none> 1.1.23+nmu1
2009-10-28 20:59:49 status half-installed libpaper-utils 1.1.23+nmu1
2009-10-28 20:59:49 status unpacked libpaper-utils 1.1.23+nmu1
2009-10-28 20:59:49 status unpacked libpaper-utils 1.1.23+nmu1
2009-10-28 20:59:49 install libpcsclite1 <none> 1.5.3-1ubuntu1
2009-10-28 20:59:49 status half-installed libpcsclite1 1.5.3-1ubuntu1
2009-10-28 20:59:49 status unpacked libpcsclite1 1.5.3-1ubuntu1
2009-10-28 20:59:49 status unpacked libpcsclite1 1.5.3-1ubuntu1
2009-10-28 20:59:49 install libpolkit-gtk-1-0 <none> 0.94-1+1git.230873
2009-10-28 20:59:49 status half-installed libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 20:59:49 status unpacked libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 20:59:49 status unpacked libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 20:59:49 install libpulse-browse0 <none> 1:0.9.19-0ubuntu4
2009-10-28 20:59:49 status half-installed libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 20:59:49 status unpacked libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 20:59:49 status unpacked libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 20:59:49 install libpurple-bin <none> 1:2.6.2-1ubuntu7
2009-10-28 20:59:49 status half-installed libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 20:59:49 status unpacked libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 20:59:49 status unpacked libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 20:59:49 install libsilc-1.1-2 <none> 1.1.10-2
2009-10-28 20:59:49 status half-installed libsilc-1.1-2 1.1.10-2
2009-10-28 20:59:49 status unpacked libsilc-1.1-2 1.1.10-2
2009-10-28 20:59:49 status unpacked libsilc-1.1-2 1.1.10-2
2009-10-28 20:59:49 install libsilcclient-1.1-3 <none> 1.1.10-2
2009-10-28 20:59:49 status half-installed libsilcclient-1.1-3 1.1.10-2
2009-10-28 20:59:49 status unpacked libsilcclient-1.1-3 1.1.10-2
2009-10-28 20:59:49 status unpacked libsilcclient-1.1-3 1.1.10-2
2009-10-28 20:59:49 install libzephyr4 <none> 3.0~rc.2544-1
2009-10-28 20:59:49 status half-installed libzephyr4 3.0~rc.2544-1
2009-10-28 20:59:49 status unpacked libzephyr4 3.0~rc.2544-1
2009-10-28 20:59:49 status unpacked libzephyr4 3.0~rc.2544-1
2009-10-28 20:59:49 install libpurple0 <none> 1:2.6.2-1ubuntu7
2009-10-28 20:59:49 status half-installed libpurple0 1:2.6.2-1ubuntu7
2009-10-28 20:59:50 status unpacked libpurple0 1:2.6.2-1ubuntu7
2009-10-28 20:59:50 status unpacked libpurple0 1:2.6.2-1ubuntu7
2009-10-28 20:59:50 install libsctp1 <none> 1.0.10+dfsg-1
2009-10-28 20:59:50 status half-installed libsctp1 1.0.10+dfsg-1
2009-10-28 20:59:50 status unpacked libsctp1 1.0.10+dfsg-1
2009-10-28 20:59:50 status unpacked libsctp1 1.0.10+dfsg-1
2009-10-28 20:59:50 install libsexy2 <none> 0.1.11-2build1
2009-10-28 20:59:50 status half-installed libsexy2 0.1.11-2build1
2009-10-28 20:59:50 status unpacked libsexy2 0.1.11-2build1
2009-10-28 20:59:50 status unpacked libsexy2 0.1.11-2build1
2009-10-28 20:59:50 install libtie-ixhash-perl <none> 1.21-2
2009-10-28 20:59:50 status half-installed libtie-ixhash-perl 1.21-2
2009-10-28 20:59:50 status unpacked libtie-ixhash-perl 1.21-2
2009-10-28 20:59:50 status unpacked libtie-ixhash-perl 1.21-2
2009-10-28 20:59:50 install libtrackerclient0 <none> 0.6.95-1ubuntu3
2009-10-28 20:59:50 status half-installed libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 20:59:50 status unpacked libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 20:59:50 status unpacked libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 20:59:50 install libx86-1 <none> 1.1+ds1-4
2009-10-28 20:59:50 status half-installed libx86-1 1.1+ds1-4
2009-10-28 20:59:50 status unpacked libx86-1 1.1+ds1-4
2009-10-28 20:59:50 status unpacked libx86-1 1.1+ds1-4
2009-10-28 20:59:50 install libusplash0 <none> 0.5.49
2009-10-28 20:59:50 status half-installed libusplash0 0.5.49
2009-10-28 20:59:50 status unpacked libusplash0 0.5.49
2009-10-28 20:59:50 status unpacked libusplash0 0.5.49
2009-10-28 20:59:50 install libvisual-0.4-plugins <none> 0.4.0.dfsg.1-2ubuntu5
2009-10-28 20:59:50 status half-installed libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 20:59:50 status unpacked libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 20:59:50 status unpacked libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 20:59:50 install libwmf0.2-7-gtk <none> 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:50 status half-installed libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:50 status unpacked libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:50 status unpacked libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 20:59:50 install libwpd8c2a <none> 0.8.14-1
2009-10-28 20:59:50 status half-installed libwpd8c2a 0.8.14-1
2009-10-28 20:59:51 status unpacked libwpd8c2a 0.8.14-1
2009-10-28 20:59:51 status unpacked libwpd8c2a 0.8.14-1
2009-10-28 20:59:51 install libwps-0.1-1 <none> 0.1.2-1
2009-10-28 20:59:51 status half-installed libwps-0.1-1 0.1.2-1
2009-10-28 20:59:51 status unpacked libwps-0.1-1 0.1.2-1
2009-10-28 20:59:51 status unpacked libwps-0.1-1 0.1.2-1
2009-10-28 20:59:51 install libxfont1 <none> 1:1.4.0-1ubuntu1
2009-10-28 20:59:51 status half-installed libxfont1 1:1.4.0-1ubuntu1
2009-10-28 20:59:51 status unpacked libxfont1 1:1.4.0-1ubuntu1
2009-10-28 20:59:51 status unpacked libxfont1 1:1.4.0-1ubuntu1
2009-10-28 20:59:51 install libxml-xpath-perl <none> 1.13-6
2009-10-28 20:59:51 status half-installed libxml-xpath-perl 1.13-6
2009-10-28 20:59:51 status unpacked libxml-xpath-perl 1.13-6
2009-10-28 20:59:51 status unpacked libxml-xpath-perl 1.13-6
2009-10-28 20:59:51 install libxp6 <none> 1:1.0.0.xsf1-2
2009-10-28 20:59:51 status half-installed libxp6 1:1.0.0.xsf1-2
2009-10-28 20:59:51 status unpacked libxp6 1:1.0.0.xsf1-2
2009-10-28 20:59:51 status unpacked libxp6 1:1.0.0.xsf1-2
2009-10-28 20:59:51 install libxvmc1 <none> 2:1.0.4-2ubuntu2
2009-10-28 20:59:51 status half-installed libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 20:59:51 status unpacked libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 20:59:51 status unpacked libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 20:59:52 install linux-firmware <none> 1.24
2009-10-28 20:59:52 status half-installed linux-firmware 1.24
2009-10-28 20:59:53 status unpacked linux-firmware 1.24
2009-10-28 20:59:53 status unpacked linux-firmware 1.24
2009-10-28 20:59:53 install linux-image-generic <none> 2.6.31.14.27
2009-10-28 20:59:53 status half-installed linux-image-generic 2.6.31.14.27
2009-10-28 20:59:53 status unpacked linux-image-generic 2.6.31.14.27
2009-10-28 20:59:53 status unpacked linux-image-generic 2.6.31.14.27
2009-10-28 20:59:53 install linux-generic <none> 2.6.31.14.27
2009-10-28 20:59:53 status half-installed linux-generic 2.6.31.14.27
2009-10-28 20:59:53 status unpacked linux-generic 2.6.31.14.27
2009-10-28 20:59:53 status unpacked linux-generic 2.6.31.14.27
2009-10-28 20:59:53 install linux-headers-2.6.31-14 <none> 2.6.31-14.48
2009-10-28 20:59:53 status half-installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 20:59:59 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 20:59:59 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:00:00 install linux-headers-2.6.31-14-generic <none> 2.6.31-14.48
2009-10-28 21:00:00 status half-installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:00:01 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:00:01 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:00:01 install linux-headers-generic <none> 2.6.31.14.27
2009-10-28 21:00:01 status half-installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:00:01 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:00:01 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:00:01 install lksctp-tools <none> 1.0.10+dfsg-1
2009-10-28 21:00:01 status half-installed lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:00:01 status unpacked lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:00:02 status unpacked lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:00:02 install lp-solve <none> 5.5.0.13-6
2009-10-28 21:00:02 status half-installed lp-solve 5.5.0.13-6
2009-10-28 21:00:02 status unpacked lp-solve 5.5.0.13-6
2009-10-28 21:00:02 status unpacked lp-solve 5.5.0.13-6
2009-10-28 21:00:02 install m17n-db <none> 1.5.4-1
2009-10-28 21:00:02 status half-installed m17n-db 1.5.4-1
2009-10-28 21:00:02 status unpacked m17n-db 1.5.4-1
2009-10-28 21:00:02 status unpacked m17n-db 1.5.4-1
2009-10-28 21:00:02 install m17n-contrib <none> 1.1.9-1
2009-10-28 21:00:02 status half-installed m17n-contrib 1.1.9-1
2009-10-28 21:00:02 status unpacked m17n-contrib 1.1.9-1
2009-10-28 21:00:02 status unpacked m17n-contrib 1.1.9-1
2009-10-28 21:00:02 install media-player-info <none> 3-0ubuntu1
2009-10-28 21:00:02 status half-installed media-player-info 3-0ubuntu1
2009-10-28 21:00:02 status unpacked media-player-info 3-0ubuntu1
2009-10-28 21:00:02 status unpacked media-player-info 3-0ubuntu1
2009-10-28 21:00:02 install min12xxw <none> 0.0.9-3ubuntu1
2009-10-28 21:00:02 status half-installed min12xxw 0.0.9-3ubuntu1
2009-10-28 21:00:02 status unpacked min12xxw 0.0.9-3ubuntu1
2009-10-28 21:00:02 status unpacked min12xxw 0.0.9-3ubuntu1
2009-10-28 21:00:02 install modemmanager <none> 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:00:02 status half-installed modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:00:03 status unpacked modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:00:03 status unpacked modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:00:03 install mousetweaks <none> 2.28.1-0ubuntu1
2009-10-28 21:00:03 status half-installed mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:00:03 status unpacked mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:00:03 status unpacked mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:00:03 install mtools <none> 4.0.10-1
2009-10-28 21:00:03 status half-installed mtools 4.0.10-1
2009-10-28 21:00:03 status unpacked mtools 4.0.10-1
2009-10-28 21:00:03 status unpacked mtools 4.0.10-1
2009-10-28 21:00:03 install nautilus-sendto <none> 2.28.0-0ubuntu1
2009-10-28 21:00:03 status half-installed nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:00:03 status unpacked nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:00:03 status unpacked nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:00:03 install samba-common <none> 2:3.4.0-3ubuntu5
2009-10-28 21:00:03 status half-installed samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:00:03 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:00:03 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:00:03 install samba-common-bin <none> 2:3.4.0-3ubuntu5
2009-10-28 21:00:03 status half-installed samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:00:05 status unpacked samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:00:05 status unpacked samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:00:05 install nautilus-share <none> 0.7.2-12
2009-10-28 21:00:05 status half-installed nautilus-share 0.7.2-12
2009-10-28 21:00:05 status unpacked nautilus-share 0.7.2-12
2009-10-28 21:00:05 status unpacked nautilus-share 0.7.2-12
2009-10-28 21:00:05 install wpasupplicant <none> 0.6.9-3ubuntu1
2009-10-28 21:00:05 status half-installed wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:00:05 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:00:05 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:00:05 install update-notifier-common <none> 0.90
2009-10-28 21:00:05 status half-installed update-notifier-common 0.90
2009-10-28 21:00:05 status unpacked update-notifier-common 0.90
2009-10-28 21:00:05 status unpacked update-notifier-common 0.90
2009-10-28 21:00:05 install network-manager <none> 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:00:05 status half-installed network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:00:05 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:00:05 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:00:05 install mobile-broadband-provider-info <none> 20091009-0ubuntu1
2009-10-28 21:00:05 status half-installed mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:00:05 status unpacked mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:00:06 status unpacked mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:00:06 install network-manager-gnome <none> 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:00:06 status half-installed network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:00:06 status unpacked network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:00:06 status unpacked network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:00:06 install notify-osd-icons <none> 0.3
2009-10-28 21:00:06 status half-installed notify-osd-icons 0.3
2009-10-28 21:00:06 status unpacked notify-osd-icons 0.3
2009-10-28 21:00:06 status unpacked notify-osd-icons 0.3
2009-10-28 21:00:06 install nvidia-173-modaliases <none> 173.14.20-0ubuntu5
2009-10-28 21:00:06 status half-installed nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:00:07 status unpacked nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:00:07 status unpacked nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:00:07 install nvidia-185-modaliases <none> 185.18.36-0ubuntu9
2009-10-28 21:00:07 status half-installed nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:00:07 status unpacked nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:00:07 status unpacked nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:00:07 install nvidia-96-modaliases <none> 96.43.13-0ubuntu6
2009-10-28 21:00:07 status half-installed nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:00:07 status unpacked nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:00:07 status unpacked nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:00:07 install nvidia-common <none> 0.2.15
2009-10-28 21:00:07 status half-installed nvidia-common 0.2.15
2009-10-28 21:00:07 status unpacked nvidia-common 0.2.15
2009-10-28 21:00:07 status unpacked nvidia-common 0.2.15
2009-10-28 21:00:07 install obex-data-server <none> 0.4.4-2build1
2009-10-28 21:00:07 status half-installed obex-data-server 0.4.4-2build1
2009-10-28 21:00:07 status unpacked obex-data-server 0.4.4-2build1
2009-10-28 21:00:07 status unpacked obex-data-server 0.4.4-2build1
2009-10-28 21:00:07 install python-virtkey <none> 0.50ubuntu2
2009-10-28 21:00:07 status half-installed python-virtkey 0.50ubuntu2
2009-10-28 21:00:07 status unpacked python-virtkey 0.50ubuntu2
2009-10-28 21:00:07 status unpacked python-virtkey 0.50ubuntu2
2009-10-28 21:00:07 install onboard <none> 0.92.0-0ubuntu3
2009-10-28 21:00:07 status half-installed onboard 0.92.0-0ubuntu3
2009-10-28 21:00:07 status unpacked onboard 0.92.0-0ubuntu3
2009-10-28 21:00:07 status unpacked onboard 0.92.0-0ubuntu3
2009-10-28 21:00:07 install openoffice.org-base-core <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:07 status half-installed openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:00:07 status unpacked openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:00:07 status unpacked openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:00:08 install openoffice.org-calc <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:08 status half-installed openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:00:09 status unpacked openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:00:09 status unpacked openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:00:10 install libwpg-0.1-1 <none> 0.1.3-1
2009-10-28 21:00:10 status half-installed libwpg-0.1-1 0.1.3-1
2009-10-28 21:00:10 status unpacked libwpg-0.1-1 0.1.3-1
2009-10-28 21:00:10 status unpacked libwpg-0.1-1 0.1.3-1
2009-10-28 21:00:10 install openoffice.org-draw <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:10 status half-installed openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 install openoffice.org-gtk <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status half-installed openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 install openoffice.org-gnome <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status half-installed openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status unpacked openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 install openoffice.org-writer <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:11 status half-installed openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:00:13 status unpacked openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:00:13 status unpacked openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:00:13 install openoffice.org-help-en-us <none> 1:3.1.1-4ubuntu1
2009-10-28 21:00:13 status half-installed openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:00:15 status unpacked openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:00:15 status unpacked openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:00:15 install openoffice.org-impress <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:15 status half-installed openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 status unpacked openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 status unpacked openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 install openoffice.org-math <none> 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 status half-installed openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 status unpacked openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 status unpacked openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:00:16 install openprinting-ppds <none> 20090825-0ubuntu4
2009-10-28 21:00:16 status half-installed openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:00:17 status unpacked openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:00:17 status unpacked openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:00:17 install os-prober <none> 1.35
2009-10-28 21:00:17 status half-installed os-prober 1.35
2009-10-28 21:00:17 status unpacked os-prober 1.35
2009-10-28 21:00:17 status unpacked os-prober 1.35
2009-10-28 21:00:17 install pcmciautils <none> 014-4ubuntu3
2009-10-28 21:00:17 status half-installed pcmciautils 014-4ubuntu3
2009-10-28 21:00:17 status unpacked pcmciautils 014-4ubuntu3
2009-10-28 21:00:17 status unpacked pcmciautils 014-4ubuntu3
2009-10-28 21:00:17 install pnm2ppa <none> 1.12-16.2ubuntu2
2009-10-28 21:00:17 status half-installed pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:00:17 status unpacked pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:00:17 status unpacked pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:00:17 install psfontmgr <none> 0.11.10-0.2ubuntu1
2009-10-28 21:00:17 status half-installed psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:00:17 status unpacked psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:00:17 status unpacked psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:00:17 install pulseaudio-esound-compat <none> 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status half-installed pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status unpacked pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status unpacked pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 install pulseaudio-module-gconf <none> 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status half-installed pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status unpacked pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status unpacked pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 install pulseaudio-utils <none> 1:0.9.19-0ubuntu4
2009-10-28 21:00:17 status half-installed pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 status unpacked pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 status unpacked pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 install pulseaudio-module-x11 <none> 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 status half-installed pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 status unpacked pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 status unpacked pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:00:18 install pxljr <none> 1.1-0ubuntu7
2009-10-28 21:00:18 status half-installed pxljr 1.1-0ubuntu7
2009-10-28 21:00:18 status unpacked pxljr 1.1-0ubuntu7
2009-10-28 21:00:18 status unpacked pxljr 1.1-0ubuntu7
2009-10-28 21:00:18 install python-configglue <none> 0.2dev-0ubuntu2
2009-10-28 21:00:18 status half-installed python-configglue 0.2dev-0ubuntu2
2009-10-28 21:00:18 status unpacked python-configglue 0.2dev-0ubuntu2
2009-10-28 21:00:18 status unpacked python-configglue 0.2dev-0ubuntu2
2009-10-28 21:00:18 install python-crypto <none> 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:00:18 status half-installed python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:00:18 status unpacked python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:00:18 status unpacked python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:00:18 install python-cups <none> 1.9.46-0ubuntu2
2009-10-28 21:00:18 status half-installed python-cups 1.9.46-0ubuntu2
2009-10-28 21:00:18 status unpacked python-cups 1.9.46-0ubuntu2
2009-10-28 21:00:18 status unpacked python-cups 1.9.46-0ubuntu2
2009-10-28 21:00:18 install python-cupshelpers <none> 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:18 status half-installed python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:18 status unpacked python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:18 status unpacked python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:18 install python-gnomeapplet <none> 2.28.0-0ubuntu1
2009-10-28 21:00:18 status half-installed python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:00:18 status unpacked python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:00:18 status unpacked python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:00:18 install python-gtkhtml2 <none> 2.25.3-3ubuntu1
2009-10-28 21:00:18 status half-installed python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:00:18 status unpacked python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:00:18 status unpacked python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:00:18 install python-openssl <none> 0.9-1
2009-10-28 21:00:18 status half-installed python-openssl 0.9-1
2009-10-28 21:00:18 status unpacked python-openssl 0.9-1
2009-10-28 21:00:18 status unpacked python-openssl 0.9-1
2009-10-28 21:00:18 install python-pam <none> 0.4.2-12ubuntu3
2009-10-28 21:00:18 status half-installed python-pam 0.4.2-12ubuntu3
2009-10-28 21:00:18 status unpacked python-pam 0.4.2-12ubuntu3
2009-10-28 21:00:18 status unpacked python-pam 0.4.2-12ubuntu3
2009-10-28 21:00:19 install python-papyon <none> 0.4.3-1ubuntu1
2009-10-28 21:00:19 status half-installed python-papyon 0.4.3-1ubuntu1
2009-10-28 21:00:19 status unpacked python-papyon 0.4.3-1ubuntu1
2009-10-28 21:00:19 status unpacked python-papyon 0.4.3-1ubuntu1
2009-10-28 21:00:19 install python-pyinotify <none> 0.8.6-2ubuntu2
2009-10-28 21:00:19 status half-installed python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:00:19 status unpacked python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:00:19 status unpacked python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:00:19 install python-rdflib <none> 2.4.0-5ubuntu1
2009-10-28 21:00:19 status half-installed python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:00:19 status unpacked python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:00:19 status unpacked python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:00:19 install python-serial <none> 2.3-1
2009-10-28 21:00:19 status half-installed python-serial 2.3-1
2009-10-28 21:00:19 status unpacked python-serial 2.3-1
2009-10-28 21:00:19 status unpacked python-serial 2.3-1
2009-10-28 21:00:19 install python-sexy <none> 0.1.9-1ubuntu2
2009-10-28 21:00:19 status half-installed python-sexy 0.1.9-1ubuntu2
2009-10-28 21:00:19 status unpacked python-sexy 0.1.9-1ubuntu2
2009-10-28 21:00:19 status unpacked python-sexy 0.1.9-1ubuntu2
2009-10-28 21:00:20 install python-smbc <none> 1.0.6-0ubuntu2
2009-10-28 21:00:20 status half-installed python-smbc 1.0.6-0ubuntu2
2009-10-28 21:00:20 status unpacked python-smbc 1.0.6-0ubuntu2
2009-10-28 21:00:20 status unpacked python-smbc 1.0.6-0ubuntu2
2009-10-28 21:00:20 install python-telepathy <none> 0.15.11-1
2009-10-28 21:00:20 status half-installed python-telepathy 0.15.11-1
2009-10-28 21:00:20 status unpacked python-telepathy 0.15.11-1
2009-10-28 21:00:20 status unpacked python-telepathy 0.15.11-1
2009-10-28 21:00:20 install python-twisted-names <none> 8.2.0-1ubuntu2
2009-10-28 21:00:20 status half-installed python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:00:20 status unpacked python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:00:20 status unpacked python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:00:20 install python-twisted-web <none> 8.2.0-2ubuntu1
2009-10-28 21:00:20 status half-installed python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:00:20 status unpacked python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:00:20 status unpacked python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:00:20 install python-protobuf <none> 2.0.3-2.2ubuntu2
2009-10-28 21:00:20 status half-installed python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:00:20 status unpacked python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:00:20 status unpacked python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:00:20 install python-ubuntuone-storageprotocol <none> 1.0.0-0ubuntu1
2009-10-28 21:00:20 status half-installed python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:00:20 status unpacked python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:00:20 status unpacked python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:00:20 install xdg-utils <none> 1.0.2-6.1
2009-10-28 21:00:20 status half-installed xdg-utils 1.0.2-6.1
2009-10-28 21:00:20 status unpacked xdg-utils 1.0.2-6.1
2009-10-28 21:00:20 status unpacked xdg-utils 1.0.2-6.1
2009-10-28 21:00:20 install python-ubuntuone-client <none> 1.0.2-0ubuntu1
2009-10-28 21:00:20 status half-installed python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:21 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:21 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:21 install python-webkit <none> 1.1.5-1
2009-10-28 21:00:21 status half-installed python-webkit 1.1.5-1
2009-10-28 21:00:21 status unpacked python-webkit 1.1.5-1
2009-10-28 21:00:21 status unpacked python-webkit 1.1.5-1
2009-10-28 21:00:21 install libpciaccess0 <none> 0.10.6-2ubuntu1
2009-10-28 21:00:21 status half-installed libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:00:21 status unpacked libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:00:21 status unpacked libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:00:21 install radeontool <none> 1.5+git76606164-0ubuntu2
2009-10-28 21:00:21 status half-installed radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:00:21 status unpacked radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:00:21 status unpacked radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:00:21 install raptor-utils <none> 1.4.19-1
2009-10-28 21:00:21 status half-installed raptor-utils 1.4.19-1
2009-10-28 21:00:21 status unpacked raptor-utils 1.4.19-1
2009-10-28 21:00:21 status unpacked raptor-utils 1.4.19-1
2009-10-28 21:00:21 install rdesktop <none> 1.6.0-2ubuntu2
2009-10-28 21:00:21 status half-installed rdesktop 1.6.0-2ubuntu2
2009-10-28 21:00:21 status unpacked rdesktop 1.6.0-2ubuntu2
2009-10-28 21:00:21 status unpacked rdesktop 1.6.0-2ubuntu2
2009-10-28 21:00:21 install redland-utils <none> 1.0.9-2
2009-10-28 21:00:21 status half-installed redland-utils 1.0.9-2
2009-10-28 21:00:21 status unpacked redland-utils 1.0.9-2
2009-10-28 21:00:21 status unpacked redland-utils 1.0.9-2
2009-10-28 21:00:21 install liblircclient0 <none> 0.8.6-0ubuntu2
2009-10-28 21:00:21 status half-installed liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:00:21 status unpacked liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:00:21 status unpacked liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:00:22 install rhythmbox <none> 0.12.5-0ubuntu4
2009-10-28 21:00:22 status half-installed rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:00:22 status unpacked rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:00:22 status unpacked rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:00:22 install update-inetd <none> 4.31
2009-10-28 21:00:22 status half-installed update-inetd 4.31
2009-10-28 21:00:22 status unpacked update-inetd 4.31
2009-10-28 21:00:22 status unpacked update-inetd 4.31
2009-10-28 21:00:22 install sane-utils <none> 1.0.20-4ubuntu3
2009-10-28 21:00:22 status half-installed sane-utils 1.0.20-4ubuntu3
2009-10-28 21:00:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:00:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:00:23 install screen-resolution-extra <none> 0.11
2009-10-28 21:00:23 status half-installed screen-resolution-extra 0.11
2009-10-28 21:00:23 status unpacked screen-resolution-extra 0.11
2009-10-28 21:00:23 status unpacked screen-resolution-extra 0.11
2009-10-28 21:00:23 install xscreensaver-data <none> 5.08-0ubuntu5
2009-10-28 21:00:23 status half-installed xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:00:23 status unpacked xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:00:23 status unpacked xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:00:23 install screensaver-default-images <none> 0.2-1
2009-10-28 21:00:23 status half-installed screensaver-default-images 0.2-1
2009-10-28 21:00:24 status unpacked screensaver-default-images 0.2-1
2009-10-28 21:00:24 status unpacked screensaver-default-images 0.2-1
2009-10-28 21:00:24 install seahorse <none> 2.28.1-0ubuntu1
2009-10-28 21:00:24 status half-installed seahorse 2.28.1-0ubuntu1
2009-10-28 21:00:24 status unpacked seahorse 2.28.1-0ubuntu1
2009-10-28 21:00:24 status unpacked seahorse 2.28.1-0ubuntu1
2009-10-28 21:00:24 install smartdimmer <none> 0.8b4-1ubuntu2
2009-10-28 21:00:24 status half-installed smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:00:24 status unpacked smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:00:24 status unpacked smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:00:24 install smbclient <none> 2:3.4.0-3ubuntu5
2009-10-28 21:00:24 status half-installed smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:00:29 status unpacked smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:00:29 status unpacked smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:00:29 install python-aptdaemon <none> 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status half-installed python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 install python-aptdaemon-gtk <none> 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status half-installed python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 install aptdaemon <none> 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status half-installed aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 status unpacked aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:00:29 install software-center <none> 1.0.2
2009-10-28 21:00:29 status half-installed software-center 1.0.2
2009-10-28 21:00:29 status unpacked software-center 1.0.2
2009-10-28 21:00:29 status unpacked software-center 1.0.2
2009-10-28 21:00:29 install splix <none> 2.0.0-2ubuntu2
2009-10-28 21:00:29 status half-installed splix 2.0.0-2ubuntu2
2009-10-28 21:00:29 status unpacked splix 2.0.0-2ubuntu2
2009-10-28 21:00:29 status unpacked splix 2.0.0-2ubuntu2
2009-10-28 21:00:29 install sreadahead <none> 1.0-5
2009-10-28 21:00:29 status half-installed sreadahead 1.0-5
2009-10-28 21:00:29 status unpacked sreadahead 1.0-5
2009-10-28 21:00:29 status unpacked sreadahead 1.0-5
2009-10-28 21:00:30 install ssh-askpass-gnome <none> 1:5.1p1-6ubuntu2
2009-10-28 21:00:30 status half-installed ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:00:30 status unpacked ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:00:30 status unpacked ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:00:30 install syslinux <none> 2:3.63+dfsg-2ubuntu3
2009-10-28 21:00:30 status half-installed syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:00:30 status unpacked syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:00:30 status unpacked syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:00:30 install system-config-printer-common <none> 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status half-installed system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 install system-config-printer-gnome <none> 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status half-installed system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 install system-config-printer-udev <none> 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status half-installed system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 status unpacked system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:00:30 install tcl8.4 <none> 8.4.19-3
2009-10-28 21:00:30 status half-installed tcl8.4 8.4.19-3
2009-10-28 21:00:30 status unpacked tcl8.4 8.4.19-3
2009-10-28 21:00:30 status unpacked tcl8.4 8.4.19-3
2009-10-28 21:00:30 install tcpd <none> 7.6.q-16
2009-10-28 21:00:30 status half-installed tcpd 7.6.q-16
2009-10-28 21:00:31 status unpacked tcpd 7.6.q-16
2009-10-28 21:00:31 status unpacked tcpd 7.6.q-16
2009-10-28 21:00:31 install telepathy-butterfly <none> 0.5.2-0ubuntu1
2009-10-28 21:00:31 status half-installed telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:00:31 status unpacked telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:00:31 status unpacked telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:00:31 install telepathy-gabble <none> 0.8.7-1
2009-10-28 21:00:31 status half-installed telepathy-gabble 0.8.7-1
2009-10-28 21:00:31 status unpacked telepathy-gabble 0.8.7-1
2009-10-28 21:00:31 status unpacked telepathy-gabble 0.8.7-1
2009-10-28 21:00:31 install telepathy-haze <none> 0.3.2-1
2009-10-28 21:00:31 status half-installed telepathy-haze 0.3.2-1
2009-10-28 21:00:31 status unpacked telepathy-haze 0.3.2-1
2009-10-28 21:00:31 status unpacked telepathy-haze 0.3.2-1
2009-10-28 21:00:31 install telepathy-idle <none> 0.1.5-1
2009-10-28 21:00:31 status half-installed telepathy-idle 0.1.5-1
2009-10-28 21:00:31 status unpacked telepathy-idle 0.1.5-1
2009-10-28 21:00:31 status unpacked telepathy-idle 0.1.5-1
2009-10-28 21:00:31 install telepathy-salut <none> 0.3.10-1
2009-10-28 21:00:31 status half-installed telepathy-salut 0.3.10-1
2009-10-28 21:00:31 status unpacked telepathy-salut 0.3.10-1
2009-10-28 21:00:31 status unpacked telepathy-salut 0.3.10-1
2009-10-28 21:00:31 install tk8.4 <none> 8.4.19-3
2009-10-28 21:00:31 status half-installed tk8.4 8.4.19-3
2009-10-28 21:00:31 status unpacked tk8.4 8.4.19-3
2009-10-28 21:00:31 status unpacked tk8.4 8.4.19-3
2009-10-28 21:00:31 install tomboy <none> 1.0.0-0ubuntu2
2009-10-28 21:00:31 status half-installed tomboy 1.0.0-0ubuntu2
2009-10-28 21:00:32 status unpacked tomboy 1.0.0-0ubuntu2
2009-10-28 21:00:32 status unpacked tomboy 1.0.0-0ubuntu2
2009-10-28 21:00:32 install toshset <none> 1.75-1
2009-10-28 21:00:32 status half-installed toshset 1.75-1
2009-10-28 21:00:32 status unpacked toshset 1.75-1
2009-10-28 21:00:32 status unpacked toshset 1.75-1
2009-10-28 21:00:32 install totem-plugins <none> 2.28.1-0ubuntu4
2009-10-28 21:00:32 status half-installed totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:00:32 install totem-common <none> 2.28.1-0ubuntu4
2009-10-28 21:00:32 status half-installed totem-common 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem-common 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem-common 2.28.1-0ubuntu4
2009-10-28 21:00:32 install totem <none> 2.28.1-0ubuntu4
2009-10-28 21:00:32 status half-installed totem 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem 2.28.1-0ubuntu4
2009-10-28 21:00:32 status unpacked totem 2.28.1-0ubuntu4
2009-10-28 21:00:32 install totem-mozilla <none> 2.28.1-0ubuntu4
2009-10-28 21:00:32 status half-installed totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:00:33 status unpacked totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:00:33 status unpacked totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:00:33 install transmission-common <none> 1.75-0ubuntu2
2009-10-28 21:00:33 status half-installed transmission-common 1.75-0ubuntu2
2009-10-28 21:00:33 status unpacked transmission-common 1.75-0ubuntu2
2009-10-28 21:00:33 status unpacked transmission-common 1.75-0ubuntu2
2009-10-28 21:00:33 install transmission-gtk <none> 1.75-0ubuntu2
2009-10-28 21:00:33 status half-installed transmission-gtk 1.75-0ubuntu2
2009-10-28 21:00:33 status unpacked transmission-gtk 1.75-0ubuntu2
2009-10-28 21:00:33 status unpacked transmission-gtk 1.75-0ubuntu2
2009-10-28 21:00:33 install tsclient <none> 0.150-2ubuntu2
2009-10-28 21:00:33 status half-installed tsclient 0.150-2ubuntu2
2009-10-28 21:00:33 status unpacked tsclient 0.150-2ubuntu2
2009-10-28 21:00:33 status unpacked tsclient 0.150-2ubuntu2
2009-10-28 21:00:33 install ttf-dejavu-core <none> 2.29-2
2009-10-28 21:00:33 status half-installed ttf-dejavu-core 2.29-2
2009-10-28 21:00:33 status unpacked ttf-dejavu-core 2.29-2
2009-10-28 21:00:33 status unpacked ttf-dejavu-core 2.29-2
2009-10-28 21:00:33 install ttf-indic-fonts-core <none> 1:0.5.4ubuntu2
2009-10-28 21:00:33 status half-installed ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:00:33 status unpacked ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:00:33 status unpacked ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:00:34 install ttf-kacst <none> 2.0+mry-1
2009-10-28 21:00:34 status half-installed ttf-kacst 2.0+mry-1
2009-10-28 21:00:34 status unpacked ttf-kacst 2.0+mry-1
2009-10-28 21:00:34 status unpacked ttf-kacst 2.0+mry-1
2009-10-28 21:00:34 install ttf-lao <none> 0.0.20060226-2
2009-10-28 21:00:34 status half-installed ttf-lao 0.0.20060226-2
2009-10-28 21:00:34 status unpacked ttf-lao 0.0.20060226-2
2009-10-28 21:00:34 status unpacked ttf-lao 0.0.20060226-2
2009-10-28 21:00:34 install xfonts-encodings <none> 1:1.0.2-3
2009-10-28 21:00:34 status half-installed xfonts-encodings 1:1.0.2-3
2009-10-28 21:00:34 status unpacked xfonts-encodings 1:1.0.2-3
2009-10-28 21:00:34 status unpacked xfonts-encodings 1:1.0.2-3
2009-10-28 21:00:34 install xfonts-utils <none> 1:7.4+1ubuntu1
2009-10-28 21:00:34 status half-installed xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:00:34 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:00:34 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:00:34 install x-ttcidfont-conf <none> 32
2009-10-28 21:00:34 status half-installed x-ttcidfont-conf 32
2009-10-28 21:00:34 status unpacked x-ttcidfont-conf 32
2009-10-28 21:00:34 status unpacked x-ttcidfont-conf 32
2009-10-28 21:00:34 install ttf-thai-tlwg <none> 1:0.4.13-1ubuntu1
2009-10-28 21:00:34 status half-installed ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:00:35 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:00:35 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:00:35 install ttf-unfonts-core <none> 1.0.1-7ubuntu1
2009-10-28 21:00:35 status half-installed ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:00:36 status unpacked ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:00:36 status unpacked ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:00:36 install ttf-vlgothic <none> 20090612-2
2009-10-28 21:00:36 status half-installed ttf-vlgothic 20090612-2
2009-10-28 21:00:36 status unpacked ttf-vlgothic 20090612-2
2009-10-28 21:00:36 status unpacked ttf-vlgothic 20090612-2
2009-10-28 21:00:36 install ubufox <none> 0.8-0ubuntu1
2009-10-28 21:00:36 status half-installed ubufox 0.8-0ubuntu1
2009-10-28 21:00:36 status unpacked ubufox 0.8-0ubuntu1
2009-10-28 21:00:36 status unpacked ubufox 0.8-0ubuntu1
2009-10-28 21:00:36 install ubuntu-wallpapers <none> 0.30
2009-10-28 21:00:36 status half-installed ubuntu-wallpapers 0.30
2009-10-28 21:00:37 status unpacked ubuntu-wallpapers 0.30
2009-10-28 21:00:37 status unpacked ubuntu-wallpapers 0.30
2009-10-28 21:00:37 install ubuntu-artwork <none> 51
2009-10-28 21:00:37 status half-installed ubuntu-artwork 51
2009-10-28 21:00:37 status unpacked ubuntu-artwork 51
2009-10-28 21:00:37 status unpacked ubuntu-artwork 51
2009-10-28 21:00:37 install cups-bsd <none> 1.4.1-5ubuntu2
2009-10-28 21:00:37 status half-installed cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:00:37 status unpacked cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:00:37 status unpacked cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:00:37 install dcraw <none> 8.86-1
2009-10-28 21:00:37 status half-installed dcraw 8.86-1
2009-10-28 21:00:37 status unpacked dcraw 8.86-1
2009-10-28 21:00:37 status unpacked dcraw 8.86-1
2009-10-28 21:00:37 install gnome-system-tools <none> 2.28.1-0ubuntu2
2009-10-28 21:00:37 status half-installed gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:00:37 status unpacked gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:00:37 status unpacked gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:00:37 install ubuntu-sounds <none> 0.12
2009-10-28 21:00:37 status half-installed ubuntu-sounds 0.12
2009-10-28 21:00:37 status unpacked ubuntu-sounds 0.12
2009-10-28 21:00:37 status unpacked ubuntu-sounds 0.12
2009-10-28 21:00:37 install update-manager <none> 1:0.126.6
2009-10-28 21:00:37 status half-installed update-manager 1:0.126.6
2009-10-28 21:00:38 status unpacked update-manager 1:0.126.6
2009-10-28 21:00:38 status unpacked update-manager 1:0.126.6
2009-10-28 21:00:38 install update-notifier <none> 0.90
2009-10-28 21:00:38 status half-installed update-notifier 0.90
2009-10-28 21:00:38 status unpacked update-notifier 0.90
2009-10-28 21:00:38 status unpacked update-notifier 0.90
2009-10-28 21:00:38 install usplash <none> 0.5.49
2009-10-28 21:00:38 status half-installed usplash 0.5.49
2009-10-28 21:00:38 status unpacked usplash 0.5.49
2009-10-28 21:00:38 status unpacked usplash 0.5.49
2009-10-28 21:00:38 install usplash-theme-ubuntu <none> 0.27
2009-10-28 21:00:38 status half-installed usplash-theme-ubuntu 0.27
2009-10-28 21:00:38 status unpacked usplash-theme-ubuntu 0.27
2009-10-28 21:00:38 status unpacked usplash-theme-ubuntu 0.27
2009-10-28 21:00:38 install wireless-tools <none> 29-2ubuntu6
2009-10-28 21:00:38 status half-installed wireless-tools 29-2ubuntu6
2009-10-28 21:00:38 status unpacked wireless-tools 29-2ubuntu6
2009-10-28 21:00:38 status unpacked wireless-tools 29-2ubuntu6
2009-10-28 21:00:38 install xdg-user-dirs <none> 0.11-0ubuntu2
2009-10-28 21:00:38 status half-installed xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:00:38 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:00:38 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:00:38 install xdg-user-dirs-gtk <none> 0.8-1
2009-10-28 21:00:38 status half-installed xdg-user-dirs-gtk 0.8-1
2009-10-28 21:00:38 status unpacked xdg-user-dirs-gtk 0.8-1
2009-10-28 21:00:38 status unpacked xdg-user-dirs-gtk 0.8-1
2009-10-28 21:00:39 install xserver-common <none> 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status half-installed xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status unpacked xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status unpacked xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 install xserver-xorg-core <none> 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status half-installed xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:00:39 install xserver-xorg-video-apm <none> 1:1.2.1-2
2009-10-28 21:00:39 status half-installed xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:00:39 status unpacked xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:00:39 status unpacked xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:00:39 install xserver-xorg-video-ark <none> 1:0.7.1-2
2009-10-28 21:00:39 status half-installed xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:00:39 status unpacked xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:00:39 status unpacked xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:00:39 install xserver-xorg-video-r128 <none> 6.8.1-1
2009-10-28 21:00:39 status half-installed xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:00:39 status unpacked xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:00:39 status unpacked xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:00:39 install xserver-xorg-video-mach64 <none> 6.8.2-1
2009-10-28 21:00:39 status half-installed xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:00:39 status unpacked xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:00:39 status unpacked xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:00:39 install xserver-xorg-video-radeon <none> 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:39 status half-installed xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 install xserver-xorg-video-ati <none> 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 status half-installed xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:00:40 install xserver-xorg-video-chips <none> 1:1.2.1-3
2009-10-28 21:00:40 status half-installed xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:00:40 status unpacked xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:00:40 status unpacked xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:00:40 install xserver-xorg-video-cirrus <none> 1:1.3.1-1ubuntu2
2009-10-28 21:00:40 status half-installed xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:00:40 status unpacked xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:00:40 status unpacked xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:00:40 install xserver-xorg-video-fbdev <none> 1:0.4.0-4
2009-10-28 21:00:40 status half-installed xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:00:40 status unpacked xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:00:40 status unpacked xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:00:40 install xserver-xorg-video-geode <none> 2.11.6-1
2009-10-28 21:00:40 status half-installed xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:00:40 install xserver-xorg-video-i128 <none> 1:1.3.2-1
2009-10-28 21:00:40 status half-installed xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:00:40 install xserver-xorg-video-i740 <none> 1:1.3.0-1
2009-10-28 21:00:40 status half-installed xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:00:40 status unpacked xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:00:40 install xserver-xorg-video-intel <none> 2:2.9.0-1ubuntu2
2009-10-28 21:00:40 status half-installed xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:00:40 status unpacked xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:00:40 status unpacked xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:00:41 install xserver-xorg-video-mga <none> 1:1.4.11.dfsg-1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:00:41 install xserver-xorg-video-neomagic <none> 1:1.2.3-1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:00:41 install xserver-xorg-video-nv <none> 1:2.1.14-2ubuntu3
2009-10-28 21:00:41 status half-installed xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:00:41 status unpacked xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:00:41 status unpacked xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:00:41 install xserver-xorg-video-rendition <none> 1:4.2.1-1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:00:41 install xserver-xorg-video-s3 <none> 1:0.6.2-1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:00:41 install xserver-xorg-video-s3virge <none> 1:1.10.2-2
2009-10-28 21:00:41 status half-installed xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:00:41 status unpacked xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:00:41 status unpacked xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:00:41 install xserver-xorg-video-savage <none> 1:2.3.0-1ubuntu1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:00:41 install xserver-xorg-video-siliconmotion <none> 1:1.7.2-1
2009-10-28 21:00:41 status half-installed xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:00:41 status unpacked xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:00:41 install xserver-xorg-video-sis <none> 1:0.10.1-2
2009-10-28 21:00:41 status half-installed xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:00:41 status unpacked xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:00:41 status unpacked xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:00:42 install xserver-xorg-video-sisusb <none> 1:0.9.1-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:00:42 install xserver-xorg-video-tdfx <none> 1:1.4.1-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:00:42 install xserver-xorg-video-trident <none> 1:1.3.1-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:00:42 install xserver-xorg-video-tseng <none> 1:1.2.1-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:00:42 install xserver-xorg-video-vesa <none> 1:2.2.1-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:00:42 install xserver-xorg-video-openchrome <none> 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:00:42 install xserver-xorg-video-voodoo <none> 1:1.2.2-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:00:42 install xserver-xorg-video-vmware <none> 1:10.16.7-1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:00:42 install xserver-xorg-video-v4l <none> 1:0.2.0-3ubuntu1
2009-10-28 21:00:42 status half-installed xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:00:42 status unpacked xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:00:42 install xserver-xorg-video-all <none> 1:7.4+3ubuntu7
2009-10-28 21:00:42 status half-installed xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:00:42 status unpacked xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:00:42 status unpacked xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:00:42 install xserver-xorg-input-evdev <none> 1:2.2.5-1ubuntu6
2009-10-28 21:00:42 status half-installed xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:00:42 status unpacked xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:00:42 status unpacked xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:00:42 install xserver-xorg-input-synaptics <none> 1.1.2-1ubuntu7
2009-10-28 21:00:42 status half-installed xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:00:43 install xserver-xorg-input-mouse <none> 1:1.4.0-2
2009-10-28 21:00:43 status half-installed xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:00:43 status unpacked xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:00:43 status unpacked xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:00:43 install xserver-xorg-input-vmmouse <none> 1:12.6.4-1ubuntu3
2009-10-28 21:00:43 status half-installed xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:00:43 status unpacked xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:00:43 status unpacked xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:00:43 install xserver-xorg-input-wacom <none> 1:0.8.4.1-0ubuntu4
2009-10-28 21:00:43 status half-installed xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:00:43 status unpacked xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:00:43 status unpacked xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:00:43 install xserver-xorg-input-all <none> 1:7.4+3ubuntu7
2009-10-28 21:00:43 status half-installed xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:00:43 install xserver-xorg <none> 1:7.4+3ubuntu7
2009-10-28 21:00:43 status half-installed xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:00:43 status unpacked xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:00:43 install libgl1-mesa-dri <none> 7.6.0-1ubuntu4
2009-10-28 21:00:43 status half-installed libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:00:46 status unpacked libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:00:46 status unpacked libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:00:46 install xfonts-base <none> 1:1.0.0-6
2009-10-28 21:00:46 status half-installed xfonts-base 1:1.0.0-6
2009-10-28 21:00:47 status unpacked xfonts-base 1:1.0.0-6
2009-10-28 21:00:47 status unpacked xfonts-base 1:1.0.0-6
2009-10-28 21:00:47 install xfonts-100dpi <none> 1:1.0.0-4build1
2009-10-28 21:00:47 status half-installed xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:00:47 status unpacked xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:00:47 status unpacked xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:00:47 install xfonts-75dpi <none> 1:1.0.0-4build1
2009-10-28 21:00:47 status half-installed xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:00:48 status unpacked xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:00:48 status unpacked xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:00:48 install xinit <none> 1.1.1-1
2009-10-28 21:00:48 status half-installed xinit 1.1.1-1
2009-10-28 21:00:48 status unpacked xinit 1.1.1-1
2009-10-28 21:00:48 status unpacked xinit 1.1.1-1
2009-10-28 21:00:48 install xorg-docs-core <none> 1:1.4-5
2009-10-28 21:00:48 status half-installed xorg-docs-core 1:1.4-5
2009-10-28 21:00:48 status unpacked xorg-docs-core 1:1.4-5
2009-10-28 21:00:48 status unpacked xorg-docs-core 1:1.4-5
2009-10-28 21:00:48 install xterm <none> 243-1ubuntu1
2009-10-28 21:00:48 status half-installed xterm 243-1ubuntu1
2009-10-28 21:00:48 status unpacked xterm 243-1ubuntu1
2009-10-28 21:00:48 status unpacked xterm 243-1ubuntu1
2009-10-28 21:00:48 install xinput <none> 1.4.2-1
2009-10-28 21:00:48 status half-installed xinput 1.4.2-1
2009-10-28 21:00:48 status unpacked xinput 1.4.2-1
2009-10-28 21:00:48 status unpacked xinput 1.4.2-1
2009-10-28 21:00:49 install xorg <none> 1:7.4+3ubuntu7
2009-10-28 21:00:49 status half-installed xorg 1:7.4+3ubuntu7
2009-10-28 21:00:49 status unpacked xorg 1:7.4+3ubuntu7
2009-10-28 21:00:49 status unpacked xorg 1:7.4+3ubuntu7
2009-10-28 21:00:49 install xscreensaver-gl <none> 5.08-0ubuntu5
2009-10-28 21:00:49 status half-installed xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:00:49 status unpacked xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:00:49 status unpacked xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:00:49 install ubuntu-xsplash-artwork <none> 0.8.4-0ubuntu1
2009-10-28 21:00:49 status half-installed ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:00:49 install xsplash <none> 0.8.4-0ubuntu1
2009-10-28 21:00:49 status half-installed xsplash 0.8.4-0ubuntu1
2009-10-28 21:00:49 status unpacked xsplash 0.8.4-0ubuntu1
2009-10-28 21:00:49 status unpacked xsplash 0.8.4-0ubuntu1
2009-10-28 21:00:49 install ubuntu-desktop <none> 1.175
2009-10-28 21:00:49 status half-installed ubuntu-desktop 1.175
2009-10-28 21:00:49 status unpacked ubuntu-desktop 1.175
2009-10-28 21:00:49 status unpacked ubuntu-desktop 1.175
2009-10-28 21:00:49 install ubuntuone-client <none> 1.0.2-0ubuntu1
2009-10-28 21:00:49 status half-installed ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:00:49 install ubuntuone-client-gnome <none> 1.0.2-0ubuntu1
2009-10-28 21:00:49 status half-installed ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:00:49 status unpacked ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:00:49 install usb-creator-common <none> 0.2.12
2009-10-28 21:00:49 status half-installed usb-creator-common 0.2.12
2009-10-28 21:00:49 status unpacked usb-creator-common 0.2.12
2009-10-28 21:00:49 status unpacked usb-creator-common 0.2.12
2009-10-28 21:00:49 install usb-creator-gtk <none> 0.2.12
2009-10-28 21:00:49 status half-installed usb-creator-gtk 0.2.12
2009-10-28 21:00:49 status unpacked usb-creator-gtk 0.2.12
2009-10-28 21:00:49 status unpacked usb-creator-gtk 0.2.12
2009-10-28 21:00:50 install vbetool <none> 1.1-2
2009-10-28 21:00:50 status half-installed vbetool 1.1-2
2009-10-28 21:00:50 status unpacked vbetool 1.1-2
2009-10-28 21:00:50 status unpacked vbetool 1.1-2
2009-10-28 21:00:50 install vinagre <none> 2.28.1-0ubuntu1
2009-10-28 21:00:50 status half-installed vinagre 2.28.1-0ubuntu1
2009-10-28 21:00:50 status triggers-pending shared-mime-info 0.70-0ubuntu1
2009-10-28 21:00:50 status half-installed vinagre 2.28.1-0ubuntu1
2009-10-28 21:00:50 status unpacked vinagre 2.28.1-0ubuntu1
2009-10-28 21:00:50 status unpacked vinagre 2.28.1-0ubuntu1
2009-10-28 21:00:50 install vino <none> 2.28.1-0ubuntu2
2009-10-28 21:00:50 status half-installed vino 2.28.1-0ubuntu2
2009-10-28 21:00:50 status unpacked vino 2.28.1-0ubuntu2
2009-10-28 21:00:50 status unpacked vino 2.28.1-0ubuntu2
2009-10-28 21:00:50 install xcursor-themes <none> 1.0.1-5ubuntu1
2009-10-28 21:00:50 status half-installed xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:00:50 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:00:50 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:00:50 install xfonts-scalable <none> 1:1.0.0-7
2009-10-28 21:00:50 status half-installed xfonts-scalable 1:1.0.0-7
2009-10-28 21:00:50 status unpacked xfonts-scalable 1:1.0.0-7
2009-10-28 21:00:50 status unpacked xfonts-scalable 1:1.0.0-7
2009-10-28 21:00:50 install xsane-common <none> 0.996-2ubuntu1
2009-10-28 21:00:50 status half-installed xsane-common 0.996-2ubuntu1
2009-10-28 21:00:51 status unpacked xsane-common 0.996-2ubuntu1
2009-10-28 21:00:51 status unpacked xsane-common 0.996-2ubuntu1
2009-10-28 21:00:51 install xsane <none> 0.996-2ubuntu1
2009-10-28 21:00:51 status half-installed xsane 0.996-2ubuntu1
2009-10-28 21:00:51 status unpacked xsane 0.996-2ubuntu1
2009-10-28 21:00:51 status unpacked xsane 0.996-2ubuntu1
2009-10-28 21:00:51 install brltty <none> 4.0-7ubuntu2
2009-10-28 21:00:51 status half-installed brltty 4.0-7ubuntu2
2009-10-28 21:00:52 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:00:52 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:00:52 install brltty-x11 <none> 4.0-7ubuntu2
2009-10-28 21:00:52 status half-installed brltty-x11 4.0-7ubuntu2
2009-10-28 21:00:52 status unpacked brltty-x11 4.0-7ubuntu2
2009-10-28 21:00:52 status unpacked brltty-x11 4.0-7ubuntu2
2009-10-28 21:00:52 install evolution-documentation-en <none> 2.28.1-0ubuntu1
2009-10-28 21:00:52 status half-installed evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:00:52 status unpacked evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:00:52 status unpacked evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:00:52 install evolution-indicator <none> 0.2.4-0ubuntu2
2009-10-28 21:00:52 status half-installed evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:00:52 status unpacked evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:00:52 status unpacked evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:00:52 install fglrx-modaliases <none> 2:8.660-0ubuntu4
2009-10-28 21:00:52 status half-installed fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:00:52 status unpacked fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:00:52 status unpacked fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:00:52 install gnome-pilot <none> 2.0.17-0ubuntu2
2009-10-28 21:00:52 status half-installed gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:00:52 status unpacked gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:00:52 status unpacked gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:00:52 install gnome-pilot-conduits <none> 2.0.15-1.2
2009-10-28 21:00:52 status half-installed gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:00:53 status unpacked gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:00:53 status unpacked gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:00:53 install latex-xft-fonts <none> 0.1-8
2009-10-28 21:00:53 status half-installed latex-xft-fonts 0.1-8
2009-10-28 21:00:53 status unpacked latex-xft-fonts 0.1-8
2009-10-28 21:00:53 status unpacked latex-xft-fonts 0.1-8
2009-10-28 21:00:53 install liblouis-data <none> 1.7.0-1ubuntu1
2009-10-28 21:00:53 status half-installed liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:00:53 status unpacked liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:00:53 status unpacked liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:00:53 install liblouis0 <none> 1.7.0-1ubuntu1
2009-10-28 21:00:53 status half-installed liblouis0 1.7.0-1ubuntu1
2009-10-28 21:00:54 status unpacked liblouis0 1.7.0-1ubuntu1
2009-10-28 21:00:54 status unpacked liblouis0 1.7.0-1ubuntu1
2009-10-28 21:00:54 install protobuf-compiler <none> 2.0.3-2.2ubuntu2
2009-10-28 21:00:54 status half-installed protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:00:54 status unpacked protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:00:54 status unpacked protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:00:54 install pulseaudio-module-bluetooth <none> 1:0.9.19-0ubuntu4
2009-10-28 21:00:54 status half-installed pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:00:54 status unpacked pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:00:54 status unpacked pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:00:54 install python-louis <none> 1.7.0-1ubuntu1
2009-10-28 21:00:54 status half-installed python-louis 1.7.0-1ubuntu1
2009-10-28 21:00:54 status unpacked python-louis 1.7.0-1ubuntu1
2009-10-28 21:00:54 status unpacked python-louis 1.7.0-1ubuntu1
2009-10-28 21:00:54 install xfonts-mathml <none> 2
2009-10-28 21:00:54 status half-installed xfonts-mathml 2
2009-10-28 21:00:54 status unpacked xfonts-mathml 2
2009-10-28 21:00:54 status unpacked xfonts-mathml 2
2009-10-28 21:00:54 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2009-10-28 21:00:54 status half-configured shared-mime-info 0.70-0ubuntu1
2009-10-28 21:00:55 status installed shared-mime-info 0.70-0ubuntu1
2009-10-28 21:00:55 startup packages configure
2009-10-28 21:00:55 configure libntfs-3g54 1:2009.4.4-1ubuntu4 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status unpacked libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status half-configured libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status installed libntfs-3g54 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 21:00:55 configure ntfs-3g 1:2009.4.4-1ubuntu4 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status unpacked ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status half-configured ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status installed ntfs-3g 1:2009.4.4-1ubuntu4
2009-10-28 21:00:55 status triggers-pending initramfs-tools 0.92bubuntu53
2009-10-28 21:00:55 configure libxmuu1 2:1.0.4-2 2:1.0.4-2
2009-10-28 21:00:55 status unpacked libxmuu1 2:1.0.4-2
2009-10-28 21:00:55 status half-configured libxmuu1 2:1.0.4-2
2009-10-28 21:00:55 status installed libxmuu1 2:1.0.4-2
2009-10-28 21:00:55 configure xauth 1:1.0.3-2 1:1.0.3-2
2009-10-28 21:00:55 status unpacked xauth 1:1.0.3-2
2009-10-28 21:00:55 status half-configured xauth 1:1.0.3-2
2009-10-28 21:00:55 status installed xauth 1:1.0.3-2
2009-10-28 21:00:55 configure sgml-data 2.0.3 2.0.3
2009-10-28 21:00:55 status unpacked sgml-data 2.0.3
2009-10-28 21:00:55 status half-configured sgml-data 2.0.3
2009-10-28 21:00:56 status installed sgml-data 2.0.3
2009-10-28 21:00:56 configure docbook-xml 4.5-6 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status unpacked docbook-xml 4.5-6
2009-10-28 21:00:56 status half-configured docbook-xml 4.5-6
2009-10-28 21:00:59 status installed docbook-xml 4.5-6
2009-10-28 21:00:59 configure libcupsimage2 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:00:59 status unpacked libcupsimage2 1.4.1-5ubuntu2
2009-10-28 21:00:59 status half-configured libcupsimage2 1.4.1-5ubuntu2
2009-10-28 21:00:59 status installed libcupsimage2 1.4.1-5ubuntu2
2009-10-28 21:00:59 configure libpaper1 1.1.23+nmu1 1.1.23+nmu1
2009-10-28 21:00:59 status unpacked libpaper1 1.1.23+nmu1
2009-10-28 21:00:59 status half-configured libpaper1 1.1.23+nmu1
2009-10-28 21:01:00 status installed libpaper1 1.1.23+nmu1
2009-10-28 21:01:00 configure libgs8 8.70.dfsg.1-0ubuntu3 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:00 status unpacked libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:00 status half-configured libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:00 status installed libgs8 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:00 configure foomatic-filters 4.0.3-0ubuntu2 4.0.3-0ubuntu2
2009-10-28 21:01:00 status unpacked foomatic-filters 4.0.3-0ubuntu2
2009-10-28 21:01:00 status half-configured foomatic-filters 4.0.3-0ubuntu2
2009-10-28 21:01:01 status installed foomatic-filters 4.0.3-0ubuntu2
2009-10-28 21:01:01 configure gsfonts 1:8.11+urwcyr1.0.7~pre44-4 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 21:01:01 status unpacked gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 21:01:01 status unpacked gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 21:01:01 status half-configured gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 21:01:11 status installed gsfonts 1:8.11+urwcyr1.0.7~pre44-4
2009-10-28 21:01:12 configure ghostscript 8.70.dfsg.1-0ubuntu3 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:12 status unpacked ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:12 status half-configured ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:12 update-alternatives: run with --install /usr/bin/ps2pdf ps2pdf /usr/bin/ps2pdf14 50
2009-10-28 21:01:12 update-alternatives: link group ps2pdf updated to point to /usr/bin/ps2pdf14
2009-10-28 21:01:12 update-alternatives: run with --install /usr/bin/ps2pdf ps2pdf /usr/bin/ps2pdf12 30
2009-10-28 21:01:12 update-alternatives: run with --install /usr/bin/ps2pdf ps2pdf /usr/bin/ps2pdf13 40
2009-10-28 21:01:12 status installed ghostscript 8.70.dfsg.1-0ubuntu3
2009-10-28 21:01:12 configure libcupscgi1 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:12 status unpacked libcupscgi1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status half-configured libcupscgi1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status installed libcupscgi1 1.4.1-5ubuntu2
2009-10-28 21:01:12 configure libcupsdriver1 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:12 status unpacked libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status half-configured libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status installed libcupsdriver1 1.4.1-5ubuntu2
2009-10-28 21:01:12 configure libcupsmime1 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:12 status unpacked libcupsmime1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status half-configured libcupsmime1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status installed libcupsmime1 1.4.1-5ubuntu2
2009-10-28 21:01:12 configure libcupsppdc1 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:12 status unpacked libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status half-configured libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 21:01:12 status installed libcupsppdc1 1.4.1-5ubuntu2
2009-10-28 21:01:12 configure libijs-0.35 0.35-7 0.35-7
2009-10-28 21:01:12 status unpacked libijs-0.35 0.35-7
2009-10-28 21:01:12 status half-configured libijs-0.35 0.35-7
2009-10-28 21:01:12 status installed libijs-0.35 0.35-7
2009-10-28 21:01:12 configure liblcms1 1.18.dfsg-1ubuntu1 1.18.dfsg-1ubuntu1
2009-10-28 21:01:12 status unpacked liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 21:01:12 status half-configured liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 21:01:12 status installed liblcms1 1.18.dfsg-1ubuntu1
2009-10-28 21:01:12 configure libpoppler5 0.12.0-0ubuntu2 0.12.0-0ubuntu2
2009-10-28 21:01:12 status unpacked libpoppler5 0.12.0-0ubuntu2
2009-10-28 21:01:12 status half-configured libpoppler5 0.12.0-0ubuntu2
2009-10-28 21:01:12 status installed libpoppler5 0.12.0-0ubuntu2
2009-10-28 21:01:12 configure libslp1 1.2.1-7.5 1.2.1-7.5
2009-10-28 21:01:12 status unpacked libslp1 1.2.1-7.5
2009-10-28 21:01:12 status half-configured libslp1 1.2.1-7.5
2009-10-28 21:01:13 status installed libslp1 1.2.1-7.5
2009-10-28 21:01:13 configure poppler-utils 0.12.0-0ubuntu2 0.12.0-0ubuntu2
2009-10-28 21:01:13 status unpacked poppler-utils 0.12.0-0ubuntu2
2009-10-28 21:01:13 status half-configured poppler-utils 0.12.0-0ubuntu2
2009-10-28 21:01:13 status installed poppler-utils 0.12.0-0ubuntu2
2009-10-28 21:01:13 configure cups-common 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups-common 1.4.1-5ubuntu2
2009-10-28 21:01:13 status half-configured cups-common 1.4.1-5ubuntu2
2009-10-28 21:01:13 status installed cups-common 1.4.1-5ubuntu2
2009-10-28 21:01:13 configure cups-client 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups-client 1.4.1-5ubuntu2
2009-10-28 21:01:13 status half-configured cups-client 1.4.1-5ubuntu2
2009-10-28 21:01:13 status installed cups-client 1.4.1-5ubuntu2
2009-10-28 21:01:13 configure ssl-cert 1.0.23ubuntu2 1.0.23ubuntu2
2009-10-28 21:01:13 status unpacked ssl-cert 1.0.23ubuntu2
2009-10-28 21:01:13 status half-configured ssl-cert 1.0.23ubuntu2
2009-10-28 21:01:13 status installed ssl-cert 1.0.23ubuntu2
2009-10-28 21:01:13 configure bc 1.06.94-3.1ubuntu2 1.06.94-3.1ubuntu2
2009-10-28 21:01:13 status unpacked bc 1.06.94-3.1ubuntu2
2009-10-28 21:01:13 status half-configured bc 1.06.94-3.1ubuntu2
2009-10-28 21:01:13 status installed bc 1.06.94-3.1ubuntu2
2009-10-28 21:01:13 configure cups 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:13 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status unpacked cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status half-configured cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 status installed cups 1.4.1-5ubuntu2
2009-10-28 21:01:14 configure wget 1.11.4-2ubuntu2 1.11.4-2ubuntu2
2009-10-28 21:01:14 status unpacked wget 1.11.4-2ubuntu2
2009-10-28 21:01:14 status unpacked wget 1.11.4-2ubuntu2
2009-10-28 21:01:14 status half-configured wget 1.11.4-2ubuntu2
2009-10-28 21:01:14 status installed wget 1.11.4-2ubuntu2
2009-10-28 21:01:14 configure libbonobo2-common 2.24.2-1 2.24.2-1
2009-10-28 21:01:14 status unpacked libbonobo2-common 2.24.2-1
2009-10-28 21:01:14 status unpacked libbonobo2-common 2.24.2-1
2009-10-28 21:01:14 status half-configured libbonobo2-common 2.24.2-1
2009-10-28 21:01:14 status installed libbonobo2-common 2.24.2-1
2009-10-28 21:01:14 configure libdbus-glib-1-2 0.80-4ubuntu1 0.80-4ubuntu1
2009-10-28 21:01:14 status unpacked libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 21:01:14 status half-configured libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 21:01:14 status installed libdbus-glib-1-2 0.80-4ubuntu1
2009-10-28 21:01:14 configure libmpfr1ldbl 2.4.1-1ubuntu1 2.4.1-1ubuntu1
2009-10-28 21:01:14 status unpacked libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 21:01:14 status half-configured libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 21:01:14 status installed libmpfr1ldbl 2.4.1-1ubuntu1
2009-10-28 21:01:14 configure cpp-4.4 4.4.1-4ubuntu8 4.4.1-4ubuntu8
2009-10-28 21:01:14 status unpacked cpp-4.4 4.4.1-4ubuntu8
2009-10-28 21:01:14 status half-configured cpp-4.4 4.4.1-4ubuntu8
2009-10-28 21:01:14 status installed cpp-4.4 4.4.1-4ubuntu8
2009-10-28 21:01:14 configure cpp 4:4.4.1-1ubuntu2 4:4.4.1-1ubuntu2
2009-10-28 21:01:14 status unpacked cpp 4:4.4.1-1ubuntu2
2009-10-28 21:01:14 status half-configured cpp 4:4.4.1-1ubuntu2
2009-10-28 21:01:14 update-alternatives: run with --quiet --install /lib/cpp cpp /usr/bin/cpp 10
2009-10-28 21:01:14 update-alternatives: link group cpp updated to point to /usr/bin/cpp
2009-10-28 21:01:14 status installed cpp 4:4.4.1-1ubuntu2
2009-10-28 21:01:14 configure libidl0 0.8.13-0.1 0.8.13-0.1
2009-10-28 21:01:14 status unpacked libidl0 0.8.13-0.1
2009-10-28 21:01:14 status half-configured libidl0 0.8.13-0.1
2009-10-28 21:01:14 status installed libidl0 0.8.13-0.1
2009-10-28 21:01:14 configure liborbit2 1:2.14.17-0.1 1:2.14.17-0.1
2009-10-28 21:01:14 status unpacked liborbit2 1:2.14.17-0.1
2009-10-28 21:01:14 status half-configured liborbit2 1:2.14.17-0.1
2009-10-28 21:01:14 status installed liborbit2 1:2.14.17-0.1
2009-10-28 21:01:14 configure libbonobo2-0 2.24.2-1 2.24.2-1
2009-10-28 21:01:14 status unpacked libbonobo2-0 2.24.2-1
2009-10-28 21:01:14 status half-configured libbonobo2-0 2.24.2-1
2009-10-28 21:01:14 status installed libbonobo2-0 2.24.2-1
2009-10-28 21:01:14 configure libart-2.0-2 2.3.20-2 2.3.20-2
2009-10-28 21:01:14 status unpacked libart-2.0-2 2.3.20-2
2009-10-28 21:01:14 status half-configured libart-2.0-2 2.3.20-2
2009-10-28 21:01:14 status installed libart-2.0-2 2.3.20-2
2009-10-28 21:01:14 configure dbus 1.2.16-0ubuntu9 1.2.16-0ubuntu9
2009-10-28 21:01:14 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 21:01:14 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 21:01:14 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 21:01:14 status unpacked dbus 1.2.16-0ubuntu9
2009-10-28 21:01:14 status half-configured dbus 1.2.16-0ubuntu9
2009-10-28 21:01:15 status installed dbus 1.2.16-0ubuntu9
2009-10-28 21:01:15 configure gconf2-common 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:15 status unpacked gconf2-common 2.28.0-0ubuntu2
2009-10-28 21:01:15 status unpacked gconf2-common 2.28.0-0ubuntu2
2009-10-28 21:01:15 status half-configured gconf2-common 2.28.0-0ubuntu2
2009-10-28 21:01:15 status installed gconf2-common 2.28.0-0ubuntu2
2009-10-28 21:01:15 configure libgconf2-4 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:15 status unpacked libgconf2-4 2.28.0-0ubuntu2
2009-10-28 21:01:15 status half-configured libgconf2-4 2.28.0-0ubuntu2
2009-10-28 21:01:15 status installed libgconf2-4 2.28.0-0ubuntu2
2009-10-28 21:01:15 configure libglade2-0 1:2.6.4-1 1:2.6.4-1
2009-10-28 21:01:15 status unpacked libglade2-0 1:2.6.4-1
2009-10-28 21:01:15 status half-configured libglade2-0 1:2.6.4-1
2009-10-28 21:01:15 status installed libglade2-0 1:2.6.4-1
2009-10-28 21:01:15 configure libaudiofile0 0.2.6-7ubuntu2 0.2.6-7ubuntu2
2009-10-28 21:01:15 status unpacked libaudiofile0 0.2.6-7ubuntu2
2009-10-28 21:01:15 status half-configured libaudiofile0 0.2.6-7ubuntu2
2009-10-28 21:01:15 status installed libaudiofile0 0.2.6-7ubuntu2
2009-10-28 21:01:15 configure libasound2 1.0.20-3ubuntu6 1.0.20-3ubuntu6
2009-10-28 21:01:15 status unpacked libasound2 1.0.20-3ubuntu6
2009-10-28 21:01:15 status unpacked libasound2 1.0.20-3ubuntu6
2009-10-28 21:01:15 status half-configured libasound2 1.0.20-3ubuntu6
2009-10-28 21:01:15 status installed libasound2 1.0.20-3ubuntu6
2009-10-28 21:01:15 configure esound-common 0.2.41-5 0.2.41-5
2009-10-28 21:01:15 status unpacked esound-common 0.2.41-5
2009-10-28 21:01:15 status unpacked esound-common 0.2.41-5
2009-10-28 21:01:15 status half-configured esound-common 0.2.41-5
2009-10-28 21:01:15 status installed esound-common 0.2.41-5
2009-10-28 21:01:15 configure libesd-alsa0 0.2.41-5 0.2.41-5
2009-10-28 21:01:15 status unpacked libesd-alsa0 0.2.41-5
2009-10-28 21:01:15 status half-configured libesd-alsa0 0.2.41-5
2009-10-28 21:01:15 status installed libesd-alsa0 0.2.41-5
2009-10-28 21:01:15 configure libavahi-glib1 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:01:15 status unpacked libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 21:01:15 status half-configured libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 21:01:15 status installed libavahi-glib1 0.6.25-1ubuntu5
2009-10-28 21:01:15 configure libhal1 0.5.13-1ubuntu8 0.5.13-1ubuntu8
2009-10-28 21:01:15 status unpacked libhal1 0.5.13-1ubuntu8
2009-10-28 21:01:15 status half-configured libhal1 0.5.13-1ubuntu8
2009-10-28 21:01:15 status installed libhal1 0.5.13-1ubuntu8
2009-10-28 21:01:15 configure libhal-storage1 0.5.13-1ubuntu8 0.5.13-1ubuntu8
2009-10-28 21:01:15 status unpacked libhal-storage1 0.5.13-1ubuntu8
2009-10-28 21:01:15 status half-configured libhal-storage1 0.5.13-1ubuntu8
2009-10-28 21:01:15 status installed libhal-storage1 0.5.13-1ubuntu8
2009-10-28 21:01:15 configure psmisc 22.7-1 22.7-1
2009-10-28 21:01:15 status unpacked psmisc 22.7-1
2009-10-28 21:01:15 status half-configured psmisc 22.7-1
2009-10-28 21:01:15 status installed psmisc 22.7-1
2009-10-28 21:01:15 configure dbus-x11 1.2.16-0ubuntu9 1.2.16-0ubuntu9
2009-10-28 21:01:15 status unpacked dbus-x11 1.2.16-0ubuntu9
2009-10-28 21:01:15 status unpacked dbus-x11 1.2.16-0ubuntu9
2009-10-28 21:01:15 status half-configured dbus-x11 1.2.16-0ubuntu9
2009-10-28 21:01:15 status installed dbus-x11 1.2.16-0ubuntu9
2009-10-28 21:01:15 configure gconf2 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:15 status unpacked gconf2 2.28.0-0ubuntu2
2009-10-28 21:01:15 status half-configured gconf2 2.28.0-0ubuntu2
2009-10-28 21:01:15 update-alternatives: run with --install /usr/bin/gconftool gconftool /usr/bin/gconftool-2 25 --slave /usr/share/man/man1/gconftool.1.gz gconftool.1.gz /usr/share/man/man1/gconftool-2.1.gz
2009-10-28 21:01:15 update-alternatives: link group gconftool updated to point to /usr/bin/gconftool-2
2009-10-28 21:01:17 status installed gconf2 2.28.0-0ubuntu2
2009-10-28 21:01:17 configure gnome-mime-data 2.18.0-1 2.18.0-1
2009-10-28 21:01:17 status unpacked gnome-mime-data 2.18.0-1
2009-10-28 21:01:17 status unpacked gnome-mime-data 2.18.0-1
2009-10-28 21:01:17 status half-configured gnome-mime-data 2.18.0-1
2009-10-28 21:01:17 status installed gnome-mime-data 2.18.0-1
2009-10-28 21:01:17 configure libgnomevfs2-common 1:2.24.2-1ubuntu1 1:2.24.2-1ubuntu1
2009-10-28 21:01:17 status unpacked libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 21:01:17 status unpacked libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 21:01:17 status half-configured libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 21:01:18 status installed libgnomevfs2-common 1:2.24.2-1ubuntu1
2009-10-28 21:01:18 configure libgnome2-common 2.28.0-0ubuntu3 2.28.0-0ubuntu3
2009-10-28 21:01:18 status unpacked libgnome2-common 2.28.0-0ubuntu3
2009-10-28 21:01:18 status unpacked libgnome2-common 2.28.0-0ubuntu3
2009-10-28 21:01:18 status unpacked libgnome2-common 2.28.0-0ubuntu3
2009-10-28 21:01:18 status half-configured libgnome2-common 2.28.0-0ubuntu3
2009-10-28 21:01:18 status installed libgnome2-common 2.28.0-0ubuntu3
2009-10-28 21:01:18 configure libgnome-keyring0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:18 status unpacked libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 21:01:18 status half-configured libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 21:01:18 status installed libgnome-keyring0 2.28.1-0ubuntu1
2009-10-28 21:01:18 configure libgdu0 2.28.0+git20091012-0ubuntu1 2.28.0+git20091012-0ubuntu1
2009-10-28 21:01:18 status unpacked libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:01:18 status half-configured libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:01:18 status installed libgdu0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:01:18 configure libgvfscommon0 1.4.1-0ubuntu1 1.4.1-0ubuntu1
2009-10-28 21:01:18 status unpacked libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 21:01:18 status half-configured libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 21:01:18 status installed libgvfscommon0 1.4.1-0ubuntu1
2009-10-28 21:01:18 configure libatasmart4 0.16-1 0.16-1
2009-10-28 21:01:18 status unpacked libatasmart4 0.16-1
2009-10-28 21:01:18 status half-configured libatasmart4 0.16-1
2009-10-28 21:01:18 status installed libatasmart4 0.16-1
2009-10-28 21:01:18 configure libgudev-1.0-0 1:147~-6 1:147~-6
2009-10-28 21:01:18 status unpacked libgudev-1.0-0 1:147~-6
2009-10-28 21:01:18 status half-configured libgudev-1.0-0 1:147~-6
2009-10-28 21:01:18 status installed libgudev-1.0-0 1:147~-6
2009-10-28 21:01:18 configure libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:01:18 status unpacked libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:01:18 status half-configured libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:01:18 status installed libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:01:18 configure libeggdbus-1-0 0.5-1 0.5-1
2009-10-28 21:01:18 status unpacked libeggdbus-1-0 0.5-1
2009-10-28 21:01:18 status half-configured libeggdbus-1-0 0.5-1
2009-10-28 21:01:18 status installed libeggdbus-1-0 0.5-1
2009-10-28 21:01:18 configure libpolkit-gobject-1-0 0.94-1ubuntu1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status half-configured libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status installed libpolkit-gobject-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 configure libpolkit-backend-1-0 0.94-1ubuntu1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status half-configured libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status installed libpolkit-backend-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 configure libsgutils2-2 1.27-0.1 1.27-0.1
2009-10-28 21:01:18 status unpacked libsgutils2-2 1.27-0.1
2009-10-28 21:01:18 status half-configured libsgutils2-2 1.27-0.1
2009-10-28 21:01:18 status installed libsgutils2-2 1.27-0.1
2009-10-28 21:01:18 configure devicekit-disks 007-2ubuntu3 007-2ubuntu3
2009-10-28 21:01:18 status unpacked devicekit-disks 007-2ubuntu3
2009-10-28 21:01:18 status unpacked devicekit-disks 007-2ubuntu3
2009-10-28 21:01:18 status half-configured devicekit-disks 007-2ubuntu3
2009-10-28 21:01:18 status installed devicekit-disks 007-2ubuntu3
2009-10-28 21:01:18 configure libpolkit-agent-1-0 0.94-1ubuntu1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status half-configured libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 status installed libpolkit-agent-1-0 0.94-1ubuntu1
2009-10-28 21:01:18 configure libck-connector0 0.3.1-0ubuntu2 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked libck-connector0 0.3.1-0ubuntu2
2009-10-28 21:01:18 status half-configured libck-connector0 0.3.1-0ubuntu2
2009-10-28 21:01:18 status installed libck-connector0 0.3.1-0ubuntu2
2009-10-28 21:01:18 configure consolekit 0.3.1-0ubuntu2 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status unpacked consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status half-configured consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 status installed consolekit 0.3.1-0ubuntu2
2009-10-28 21:01:18 configure policykit-1 0.94-1ubuntu1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status unpacked policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status half-configured policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 status installed policykit-1 0.94-1ubuntu1
2009-10-28 21:01:18 configure policykit-1-gnome 0.94-1+1git.230873 0.94-1+1git.230873
2009-10-28 21:01:18 status unpacked policykit-1-gnome 0.94-1+1git.230873
2009-10-28 21:01:18 status unpacked policykit-1-gnome 0.94-1+1git.230873
2009-10-28 21:01:18 status half-configured policykit-1-gnome 0.94-1+1git.230873
2009-10-28 21:01:19 status installed policykit-1-gnome 0.94-1+1git.230873
2009-10-28 21:01:19 configure gvfs 1.4.1-0ubuntu1 1.4.1-0ubuntu1
2009-10-28 21:01:19 status unpacked gvfs 1.4.1-0ubuntu1
2009-10-28 21:01:19 status half-configured gvfs 1.4.1-0ubuntu1
2009-10-28 21:01:19 status installed gvfs 1.4.1-0ubuntu1
2009-10-28 21:01:19 configure libgail18 2.18.3-1 2.18.3-1
2009-10-28 21:01:19 status unpacked libgail18 2.18.3-1
2009-10-28 21:01:19 status half-configured libgail18 2.18.3-1
2009-10-28 21:01:19 status installed libgail18 2.18.3-1
2009-10-28 21:01:19 configure libgail-common 2.18.3-1 2.18.3-1
2009-10-28 21:01:19 status unpacked libgail-common 2.18.3-1
2009-10-28 21:01:19 status half-configured libgail-common 2.18.3-1
2009-10-28 21:01:19 status installed libgail-common 2.18.3-1
2009-10-28 21:01:19 configure libgnomecanvas2-common 2.26.0-1 2.26.0-1
2009-10-28 21:01:19 status unpacked libgnomecanvas2-common 2.26.0-1
2009-10-28 21:01:19 status half-configured libgnomecanvas2-common 2.26.0-1
2009-10-28 21:01:19 status installed libgnomecanvas2-common 2.26.0-1
2009-10-28 21:01:19 configure libgnomecanvas2-0 2.26.0-1 2.26.0-1
2009-10-28 21:01:19 status unpacked libgnomecanvas2-0 2.26.0-1
2009-10-28 21:01:19 status half-configured libgnomecanvas2-0 2.26.0-1
2009-10-28 21:01:19 status installed libgnomecanvas2-0 2.26.0-1
2009-10-28 21:01:19 configure libbonoboui2-common 2.24.2-1ubuntu2 2.24.2-1ubuntu2
2009-10-28 21:01:19 status unpacked libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 21:01:19 status half-configured libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 21:01:19 status installed libbonoboui2-common 2.24.2-1ubuntu2
2009-10-28 21:01:19 configure libxcb-atom1 0.3.6-1 0.3.6-1
2009-10-28 21:01:19 status unpacked libxcb-atom1 0.3.6-1
2009-10-28 21:01:19 status half-configured libxcb-atom1 0.3.6-1
2009-10-28 21:01:19 status installed libxcb-atom1 0.3.6-1
2009-10-28 21:01:19 configure libxcb-aux0 0.3.6-1 0.3.6-1
2009-10-28 21:01:19 status unpacked libxcb-aux0 0.3.6-1
2009-10-28 21:01:19 status half-configured libxcb-aux0 0.3.6-1
2009-10-28 21:01:19 status installed libxcb-aux0 0.3.6-1
2009-10-28 21:01:19 configure libxcb-event1 0.3.6-1 0.3.6-1
2009-10-28 21:01:19 status unpacked libxcb-event1 0.3.6-1
2009-10-28 21:01:19 status half-configured libxcb-event1 0.3.6-1
2009-10-28 21:01:19 status installed libxcb-event1 0.3.6-1
2009-10-28 21:01:19 configure libstartup-notification0 0.10-1 0.10-1
2009-10-28 21:01:19 status unpacked libstartup-notification0 0.10-1
2009-10-28 21:01:19 status half-configured libstartup-notification0 0.10-1
2009-10-28 21:01:19 status installed libstartup-notification0 0.10-1
2009-10-28 21:01:19 configure libgnome-desktop-2-11 1:2.28.1-0ubuntu2 1:2.28.1-0ubuntu2
2009-10-28 21:01:19 status unpacked libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 21:01:19 status half-configured libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 21:01:19 status installed libgnome-desktop-2-11 1:2.28.1-0ubuntu2
2009-10-28 21:01:19 configure libxkbfile1 1:1.0.5-1ubuntu2 1:1.0.5-1ubuntu2
2009-10-28 21:01:19 status unpacked libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 21:01:19 status half-configured libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 21:01:19 status installed libxkbfile1 1:1.0.5-1ubuntu2
2009-10-28 21:01:19 configure x11-xkb-utils 7.4+3 7.4+3
2009-10-28 21:01:19 status unpacked x11-xkb-utils 7.4+3
2009-10-28 21:01:19 status half-configured x11-xkb-utils 7.4+3
2009-10-28 21:01:19 status installed x11-xkb-utils 7.4+3
2009-10-28 21:01:19 configure libxklavier15 4.0-0ubuntu5 4.0-0ubuntu5
2009-10-28 21:01:19 status unpacked libxklavier15 4.0-0ubuntu5
2009-10-28 21:01:19 status half-configured libxklavier15 4.0-0ubuntu5
2009-10-28 21:01:19 status installed libxklavier15 4.0-0ubuntu5
2009-10-28 21:01:19 configure libgnomekbd-common 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:19 status unpacked libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 21:01:19 status half-configured libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 21:01:19 status installed libgnomekbd-common 2.28.0-0ubuntu2
2009-10-28 21:01:19 configure libgnomekbd4 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:19 status unpacked libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 21:01:19 status half-configured libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 21:01:19 status installed libgnomekbd4 2.28.0-0ubuntu2
2009-10-28 21:01:19 configure libgnomekbdui4 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:19 status unpacked libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 21:01:19 status half-configured libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 21:01:19 status installed libgnomekbdui4 2.28.0-0ubuntu2
2009-10-28 21:01:19 configure libgtop2-common 2.26.1-0ubuntu1 2.26.1-0ubuntu1
2009-10-28 21:01:19 status unpacked libgtop2-common 2.26.1-0ubuntu1
2009-10-28 21:01:19 status half-configured libgtop2-common 2.26.1-0ubuntu1
2009-10-28 21:01:19 status installed libgtop2-common 2.26.1-0ubuntu1
2009-10-28 21:01:19 configure libgtop2-7 2.26.1-0ubuntu1 2.26.1-0ubuntu1
2009-10-28 21:01:19 status unpacked libgtop2-7 2.26.1-0ubuntu1
2009-10-28 21:01:19 status half-configured libgtop2-7 2.26.1-0ubuntu1
2009-10-28 21:01:19 status installed libgtop2-7 2.26.1-0ubuntu1
2009-10-28 21:01:19 configure liblaunchpad-integration1 0.1.26 0.1.26
2009-10-28 21:01:19 status unpacked liblaunchpad-integration1 0.1.26
2009-10-28 21:01:19 status half-configured liblaunchpad-integration1 0.1.26
2009-10-28 21:01:19 status installed liblaunchpad-integration1 0.1.26
2009-10-28 21:01:19 configure libgucharmap7 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:01:19 status unpacked libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 21:01:19 status half-configured libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 21:01:19 status installed libgucharmap7 1:2.28.0-0ubuntu1
2009-10-28 21:01:19 configure libproxy0 0.2.3-0ubuntu5 0.2.3-0ubuntu5
2009-10-28 21:01:19 status unpacked libproxy0 0.2.3-0ubuntu5
2009-10-28 21:01:19 status half-configured libproxy0 0.2.3-0ubuntu5
2009-10-28 21:01:19 status installed libproxy0 0.2.3-0ubuntu5
2009-10-28 21:01:19 configure libsoup2.4-1 2.28.1-2 2.28.1-2
2009-10-28 21:01:19 status unpacked libsoup2.4-1 2.28.1-2
2009-10-28 21:01:19 status half-configured libsoup2.4-1 2.28.1-2
2009-10-28 21:01:19 status installed libsoup2.4-1 2.28.1-2
2009-10-28 21:01:19 configure libsoup-gnome2.4-1 2.28.1-2 2.28.1-2
2009-10-28 21:01:19 status unpacked libsoup-gnome2.4-1 2.28.1-2
2009-10-28 21:01:19 status half-configured libsoup-gnome2.4-1 2.28.1-2
2009-10-28 21:01:19 status installed libsoup-gnome2.4-1 2.28.1-2
2009-10-28 21:01:19 configure libgweather-common 2.28.0-1ubuntu2 2.28.0-1ubuntu2
2009-10-28 21:01:19 status unpacked libgweather-common 2.28.0-1ubuntu2
2009-10-28 21:01:19 status half-configured libgweather-common 2.28.0-1ubuntu2
2009-10-28 21:01:20 status installed libgweather-common 2.28.0-1ubuntu2
2009-10-28 21:01:20 configure libgweather1 2.28.0-1ubuntu2 2.28.0-1ubuntu2
2009-10-28 21:01:20 status unpacked libgweather1 2.28.0-1ubuntu2
2009-10-28 21:01:20 status half-configured libgweather1 2.28.0-1ubuntu2
2009-10-28 21:01:20 status installed libgweather1 2.28.0-1ubuntu2
2009-10-28 21:01:20 configure libnotify1 0.4.5-1ubuntu1 0.4.5-1ubuntu1
2009-10-28 21:01:20 status unpacked libnotify1 0.4.5-1ubuntu1
2009-10-28 21:01:20 status half-configured libnotify1 0.4.5-1ubuntu1
2009-10-28 21:01:20 status installed libnotify1 0.4.5-1ubuntu1
2009-10-28 21:01:20 configure libxres1 2:1.0.3-2 2:1.0.3-2
2009-10-28 21:01:20 status unpacked libxres1 2:1.0.3-2
2009-10-28 21:01:20 status half-configured libxres1 2:1.0.3-2
2009-10-28 21:01:21 status installed libxres1 2:1.0.3-2
2009-10-28 21:01:21 configure libwnck-common 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status unpacked libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status half-configured libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status installed libwnck-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 configure libwnck22 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status unpacked libwnck22 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status half-configured libwnck22 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 status installed libwnck22 1:2.28.0-0ubuntu1
2009-10-28 21:01:21 configure librarian0 0.8.1-2ubuntu3 0.8.1-2ubuntu3
2009-10-28 21:01:21 status unpacked librarian0 0.8.1-2ubuntu3
2009-10-28 21:01:21 status half-configured librarian0 0.8.1-2ubuntu3
2009-10-28 21:01:21 status installed librarian0 0.8.1-2ubuntu3
2009-10-28 21:01:21 configure rarian-compat 0.8.1-2ubuntu3 0.8.1-2ubuntu3
2009-10-28 21:01:21 status unpacked rarian-compat 0.8.1-2ubuntu3
2009-10-28 21:01:21 status half-configured rarian-compat 0.8.1-2ubuntu3
2009-10-28 21:01:21 status installed rarian-compat 0.8.1-2ubuntu3
2009-10-28 21:01:21 configure python-support 1.0.3ubuntu1 1.0.3ubuntu1
2009-10-28 21:01:21 status unpacked python-support 1.0.3ubuntu1
2009-10-28 21:01:21 status half-configured python-support 1.0.3ubuntu1
2009-10-28 21:01:23 status installed python-support 1.0.3ubuntu1
2009-10-28 21:01:23 configure gnome-applets-data 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:01:23 status unpacked gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 21:01:23 status unpacked gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 21:01:23 status half-configured gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 21:01:24 status installed gnome-applets-data 2.28.0-0ubuntu2
2009-10-28 21:01:24 status triggers-pending python-support 1.0.3ubuntu1
2009-10-28 21:01:24 configure libedataserver1.2-11 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed libedataserver1.2-11 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure libical0 0.43-3 0.43-3
2009-10-28 21:01:24 status unpacked libical0 0.43-3
2009-10-28 21:01:24 status half-configured libical0 0.43-3
2009-10-28 21:01:24 status installed libical0 0.43-3
2009-10-28 21:01:24 configure libecal1.2-7 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed libecal1.2-7 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure libcamel1.2-14 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed libcamel1.2-14 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure libebook1.2-9 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed libebook1.2-9 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure evolution-data-server-common 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed evolution-data-server-common 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure libedataserverui1.2-8 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 21:01:24 status installed libedataserverui1.2-8 2.28.1-0ubuntu1
2009-10-28 21:01:24 configure libgnome-menu2 2.28.0.1-0ubuntu1 2.28.0.1-0ubuntu1
2009-10-28 21:01:24 status unpacked libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 21:01:24 status half-configured libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 21:01:24 status installed libgnome-menu2 2.28.0.1-0ubuntu1
2009-10-28 21:01:24 configure libgnomeui-common 2.24.2-1 2.24.2-1
2009-10-28 21:01:24 status unpacked libgnomeui-common 2.24.2-1
2009-10-28 21:01:24 status half-configured libgnomeui-common 2.24.2-1
2009-10-28 21:01:24 status installed libgnomeui-common 2.24.2-1
2009-10-28 21:01:24 configure libcroco3 0.6.1-2 0.6.1-2
2009-10-28 21:01:24 status unpacked libcroco3 0.6.1-2
2009-10-28 21:01:24 status half-configured libcroco3 0.6.1-2
2009-10-28 21:01:24 status installed libcroco3 0.6.1-2
2009-10-28 21:01:24 configure libgsf-1-common 1.14.15-1ubuntu1 1.14.15-1ubuntu1
2009-10-28 21:01:24 status unpacked libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 21:01:24 status half-configured libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 21:01:24 status installed libgsf-1-common 1.14.15-1ubuntu1
2009-10-28 21:01:24 configure libgsf-1-114 1.14.15-1ubuntu1 1.14.15-1ubuntu1
2009-10-28 21:01:24 status unpacked libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 21:01:24 status half-configured libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 21:01:24 status installed libgsf-1-114 1.14.15-1ubuntu1
2009-10-28 21:01:24 configure librsvg2-2 2.26.0-1 2.26.0-1
2009-10-28 21:01:24 status unpacked librsvg2-2 2.26.0-1
2009-10-28 21:01:24 status half-configured librsvg2-2 2.26.0-1
2009-10-28 21:01:24 status installed librsvg2-2 2.26.0-1
2009-10-28 21:01:24 configure gnome-panel-data 1:2.28.0-0ubuntu6 1:2.28.0-0ubuntu6
2009-10-28 21:01:24 status unpacked gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 21:01:24 status unpacked gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 21:01:24 status half-configured gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 21:01:25 status installed gnome-panel-data 1:2.28.0-0ubuntu6
2009-10-28 21:01:25 configure gnome-desktop-data 1:2.28.1-0ubuntu2 1:2.28.1-0ubuntu2
2009-10-28 21:01:25 status unpacked gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 21:01:25 status half-configured gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 21:01:25 status installed gnome-desktop-data 1:2.28.1-0ubuntu2
2009-10-28 21:01:25 configure libltdl7 2.2.6a-4 2.2.6a-4
2009-10-28 21:01:25 status unpacked libltdl7 2.2.6a-4
2009-10-28 21:01:25 status half-configured libltdl7 2.2.6a-4
2009-10-28 21:01:25 status installed libltdl7 2.2.6a-4
2009-10-28 21:01:25 configure libogg0 1.1.4~dfsg-1 1.1.4~dfsg-1
2009-10-28 21:01:25 status unpacked libogg0 1.1.4~dfsg-1
2009-10-28 21:01:25 status half-configured libogg0 1.1.4~dfsg-1
2009-10-28 21:01:25 status installed libogg0 1.1.4~dfsg-1
2009-10-28 21:01:25 configure libtdb1 1.1.5-1 1.1.5-1
2009-10-28 21:01:25 status unpacked libtdb1 1.1.5-1
2009-10-28 21:01:25 status half-configured libtdb1 1.1.5-1
2009-10-28 21:01:25 status installed libtdb1 1.1.5-1
2009-10-28 21:01:25 configure libvorbis0a 1.2.0.dfsg-6 1.2.0.dfsg-6
2009-10-28 21:01:25 status unpacked libvorbis0a 1.2.0.dfsg-6
2009-10-28 21:01:25 status half-configured libvorbis0a 1.2.0.dfsg-6
2009-10-28 21:01:25 status installed libvorbis0a 1.2.0.dfsg-6
2009-10-28 21:01:25 configure libvorbisfile3 1.2.0.dfsg-6 1.2.0.dfsg-6
2009-10-28 21:01:25 status unpacked libvorbisfile3 1.2.0.dfsg-6
2009-10-28 21:01:25 status half-configured libvorbisfile3 1.2.0.dfsg-6
2009-10-28 21:01:25 status installed libvorbisfile3 1.2.0.dfsg-6
2009-10-28 21:01:25 configure libcanberra0 0.15-0ubuntu7 0.15-0ubuntu7
2009-10-28 21:01:25 status unpacked libcanberra0 0.15-0ubuntu7
2009-10-28 21:01:25 status half-configured libcanberra0 0.15-0ubuntu7
2009-10-28 21:01:26 status installed libcanberra0 0.15-0ubuntu7
2009-10-28 21:01:26 configure libcanberra-gtk0 0.15-0ubuntu7 0.15-0ubuntu7
2009-10-28 21:01:26 status unpacked libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 21:01:26 status half-configured libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 21:01:26 status installed libcanberra-gtk0 0.15-0ubuntu7
2009-10-28 21:01:26 configure libgnome-window-settings1 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status unpacked libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status half-configured libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status installed libgnome-window-settings1 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 configure metacity-common 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status unpacked metacity-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status half-configured metacity-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status installed metacity-common 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 configure libmetacity0 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status unpacked libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status half-configured libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 status installed libmetacity0 1:2.28.0-0ubuntu1
2009-10-28 21:01:26 configure libunique-1.0-0 1.1.2-1ubuntu1 1.1.2-1ubuntu1
2009-10-28 21:01:26 status unpacked libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 21:01:26 status half-configured libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 21:01:26 status installed libunique-1.0-0 1.1.2-1ubuntu1
2009-10-28 21:01:26 configure libxss1 1:1.1.3-1 1:1.1.3-1
2009-10-28 21:01:26 status unpacked libxss1 1:1.1.3-1
2009-10-28 21:01:26 status half-configured libxss1 1:1.1.3-1
2009-10-28 21:01:26 status installed libxss1 1:1.1.3-1
2009-10-28 21:01:26 configure capplets-data 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status unpacked capplets-data 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status unpacked capplets-data 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status unpacked capplets-data 1:2.28.1-0ubuntu1
2009-10-28 21:01:26 status half-configured capplets-data 1:2.28.1-0ubuntu1
2009-10-28 21:01:27 status installed capplets-data 1:2.28.1-0ubuntu1
2009-10-28 21:01:27 configure libflac8 1.2.1-2build1 1.2.1-2build1
2009-10-28 21:01:27 status unpacked libflac8 1.2.1-2build1
2009-10-28 21:01:27 status half-configured libflac8 1.2.1-2build1
2009-10-28 21:01:27 status installed libflac8 1.2.1-2build1
2009-10-28 21:01:27 configure libvorbisenc2 1.2.0.dfsg-6 1.2.0.dfsg-6
2009-10-28 21:01:27 status unpacked libvorbisenc2 1.2.0.dfsg-6
2009-10-28 21:01:27 status half-configured libvorbisenc2 1.2.0.dfsg-6
2009-10-28 21:01:27 status installed libvorbisenc2 1.2.0.dfsg-6
2009-10-28 21:01:27 configure libsndfile1 1.0.20-1ubuntu1 1.0.20-1ubuntu1
2009-10-28 21:01:27 status unpacked libsndfile1 1.0.20-1ubuntu1
2009-10-28 21:01:27 status half-configured libsndfile1 1.0.20-1ubuntu1
2009-10-28 21:01:27 status installed libsndfile1 1.0.20-1ubuntu1
2009-10-28 21:01:27 configure libwrap0 7.6.q-16 7.6.q-16
2009-10-28 21:01:27 status unpacked libwrap0 7.6.q-16
2009-10-28 21:01:27 status half-configured libwrap0 7.6.q-16
2009-10-28 21:01:27 status installed libwrap0 7.6.q-16
2009-10-28 21:01:28 configure libpulse0 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status unpacked libpulse0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status unpacked libpulse0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status half-configured libpulse0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status installed libpulse0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 configure libpulse-mainloop-glib0 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status unpacked libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status half-configured libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 status installed libpulse-mainloop-glib0 1:0.9.19-0ubuntu4
2009-10-28 21:01:28 configure libxxf86misc1 1:1.0.1-3 1:1.0.1-3
2009-10-28 21:01:28 status unpacked libxxf86misc1 1:1.0.1-3
2009-10-28 21:01:28 status half-configured libxxf86misc1 1:1.0.1-3
2009-10-28 21:01:28 status installed libxxf86misc1 1:1.0.1-3
2009-10-28 21:01:28 configure gnome-settings-daemon 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status unpacked gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:28 status half-configured gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:29 status installed gnome-settings-daemon 2.28.1-0ubuntu1
2009-10-28 21:01:29 configure python-cairo 1.8.6-1ubuntu1 1.8.6-1ubuntu1
2009-10-28 21:01:29 status unpacked python-cairo 1.8.6-1ubuntu1
2009-10-28 21:01:29 status half-configured python-cairo 1.8.6-1ubuntu1
2009-10-28 21:01:29 status installed python-cairo 1.8.6-1ubuntu1
2009-10-28 21:01:29 configure libffi5 3.0.7-2ubuntu1 3.0.7-2ubuntu1
2009-10-28 21:01:29 status unpacked libffi5 3.0.7-2ubuntu1
2009-10-28 21:01:29 status half-configured libffi5 3.0.7-2ubuntu1
2009-10-28 21:01:29 status installed libffi5 3.0.7-2ubuntu1
2009-10-28 21:01:29 configure python-gobject 2.18.0-0ubuntu2 2.18.0-0ubuntu2
2009-10-28 21:01:29 status unpacked python-gobject 2.18.0-0ubuntu2
2009-10-28 21:01:29 status half-configured python-gobject 2.18.0-0ubuntu2
2009-10-28 21:01:29 status installed python-gobject 2.18.0-0ubuntu2
2009-10-28 21:01:29 configure python-gtk2 2.16.0-0ubuntu1 2.16.0-0ubuntu1
2009-10-28 21:01:29 status unpacked python-gtk2 2.16.0-0ubuntu1
2009-10-28 21:01:29 status half-configured python-gtk2 2.16.0-0ubuntu1
2009-10-28 21:01:29 status installed python-gtk2 2.16.0-0ubuntu1
2009-10-28 21:01:29 configure python-gmenu 2.28.0.1-0ubuntu1 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status unpacked python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status half-configured python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status installed python-gmenu 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 configure gnome-menus 2.28.0.1-0ubuntu1 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status unpacked gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status unpacked gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status unpacked gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status half-configured gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 status installed gnome-menus 2.28.0.1-0ubuntu1
2009-10-28 21:01:29 configure hicolor-icon-theme 0.10-2 0.10-2
2009-10-28 21:01:29 status unpacked hicolor-icon-theme 0.10-2
2009-10-28 21:01:29 status half-configured hicolor-icon-theme 0.10-2
2009-10-28 21:01:29 status installed hicolor-icon-theme 0.10-2
2009-10-28 21:01:29 configure libgtk2.0-bin 2.18.3-1 2.18.3-1
2009-10-28 21:01:29 status unpacked libgtk2.0-bin 2.18.3-1
2009-10-28 21:01:29 status half-configured libgtk2.0-bin 2.18.3-1
2009-10-28 21:01:29 status installed libgtk2.0-bin 2.18.3-1
2009-10-28 21:01:29 configure librsvg2-common 2.26.0-1 2.26.0-1
2009-10-28 21:01:29 status unpacked librsvg2-common 2.26.0-1
2009-10-28 21:01:29 status half-configured librsvg2-common 2.26.0-1
2009-10-28 21:01:29 status installed librsvg2-common 2.26.0-1
2009-10-28 21:01:29 configure gnome-icon-theme 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:01:29 status unpacked gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 21:01:29 status half-configured gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 21:01:29 status installed gnome-icon-theme 2.28.0-0ubuntu1
2009-10-28 21:01:29 configure desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2009-10-28 21:01:29 status unpacked desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:01:29 status unpacked desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:01:29 status unpacked desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:01:29 status half-configured desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:01:30 status installed desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:01:30 configure python-apt 0.7.13.2ubuntu4 0.7.13.2ubuntu4
2009-10-28 21:01:30 status unpacked python-apt 0.7.13.2ubuntu4
2009-10-28 21:01:30 status half-configured python-apt 0.7.13.2ubuntu4
2009-10-28 21:01:30 status installed python-apt 0.7.13.2ubuntu4
2009-10-28 21:01:30 configure python-dbus 0.83.0-1ubuntu2 0.83.0-1ubuntu2
2009-10-28 21:01:30 status unpacked python-dbus 0.83.0-1ubuntu2
2009-10-28 21:01:30 status half-configured python-dbus 0.83.0-1ubuntu2
2009-10-28 21:01:30 status installed python-dbus 0.83.0-1ubuntu2
2009-10-28 21:01:30 configure ubuntu-system-service 0.1.16 0.1.16
2009-10-28 21:01:30 status unpacked ubuntu-system-service 0.1.16
2009-10-28 21:01:30 status unpacked ubuntu-system-service 0.1.16
2009-10-28 21:01:30 status half-configured ubuntu-system-service 0.1.16
2009-10-28 21:01:30 status installed ubuntu-system-service 0.1.16
2009-10-28 21:01:30 configure gnome-control-center 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:01:30 status unpacked gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 21:01:30 status half-configured gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 21:01:30 status installed gnome-control-center 1:2.28.1-0ubuntu1
2009-10-28 21:01:30 configure python-gnomecanvas 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:01:30 status unpacked python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 21:01:30 status half-configured python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 21:01:30 status installed python-gnomecanvas 2.28.0-0ubuntu1
2009-10-28 21:01:30 configure python-pyorbit 2.24.0-0ubuntu3 2.24.0-0ubuntu3
2009-10-28 21:01:30 status unpacked python-pyorbit 2.24.0-0ubuntu3
2009-10-28 21:01:30 status half-configured python-pyorbit 2.24.0-0ubuntu3
2009-10-28 21:01:30 status installed python-pyorbit 2.24.0-0ubuntu3
2009-10-28 21:01:30 configure python-gconf 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:01:30 status unpacked python-gconf 2.28.0-0ubuntu1
2009-10-28 21:01:30 status half-configured python-gconf 2.28.0-0ubuntu1
2009-10-28 21:01:30 status installed python-gconf 2.28.0-0ubuntu1
2009-10-28 21:01:30 configure libexif12 0.6.17-1 0.6.17-1
2009-10-28 21:01:30 status unpacked libexif12 0.6.17-1
2009-10-28 21:01:30 status half-configured libexif12 0.6.17-1
2009-10-28 21:01:30 status installed libexif12 0.6.17-1
2009-10-28 21:01:30 configure libgphoto2-port0 2.4.6-1ubuntu6 2.4.6-1ubuntu6
2009-10-28 21:01:30 status unpacked libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 21:01:30 status half-configured libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 21:01:30 status installed libgphoto2-port0 2.4.6-1ubuntu6
2009-10-28 21:01:30 configure libgphoto2-2 2.4.6-1ubuntu6 2.4.6-1ubuntu6
2009-10-28 21:01:30 status unpacked libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 21:01:30 status half-configured libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 21:01:30 status installed libgphoto2-2 2.4.6-1ubuntu6
2009-10-28 21:01:30 configure libieee1284-3 0.2.11-5ubuntu2 0.2.11-5ubuntu2
2009-10-28 21:01:30 status unpacked libieee1284-3 0.2.11-5ubuntu2
2009-10-28 21:01:30 status half-configured libieee1284-3 0.2.11-5ubuntu2
2009-10-28 21:01:30 status installed libieee1284-3 0.2.11-5ubuntu2
2009-10-28 21:01:30 configure libv4l-0 0.6.0-1 0.6.0-1
2009-10-28 21:01:30 status unpacked libv4l-0 0.6.0-1
2009-10-28 21:01:30 status half-configured libv4l-0 0.6.0-1
2009-10-28 21:01:30 status installed libv4l-0 0.6.0-1
2009-10-28 21:01:30 configure libsane 1.0.20-4ubuntu3 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:30 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status unpacked libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status half-configured libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 status installed libsane 1.0.20-4ubuntu3
2009-10-28 21:01:31 configure libsnmp-base 5.4.1~dfsg-12ubuntu7 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:31 status unpacked libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:31 status half-configured libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:31 status installed libsnmp-base 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:31 configure libperl5.10 5.10.0-24ubuntu4 5.10.0-24ubuntu4
2009-10-28 21:01:31 status unpacked libperl5.10 5.10.0-24ubuntu4
2009-10-28 21:01:31 status half-configured libperl5.10 5.10.0-24ubuntu4
2009-10-28 21:01:31 status installed libperl5.10 5.10.0-24ubuntu4
2009-10-28 21:01:31 configure libsensors3 1:2.10.8-1 1:2.10.8-1
2009-10-28 21:01:31 status unpacked libsensors3 1:2.10.8-1
2009-10-28 21:01:31 status half-configured libsensors3 1:2.10.8-1
2009-10-28 21:01:32 status installed libsensors3 1:2.10.8-1
2009-10-28 21:01:32 configure libsnmp15 5.4.1~dfsg-12ubuntu7 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:32 status unpacked libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:32 status half-configured libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:32 status installed libsnmp15 5.4.1~dfsg-12ubuntu7
2009-10-28 21:01:32 configure python-imaging 1.1.6-3ubuntu1 1.1.6-3ubuntu1
2009-10-28 21:01:32 status unpacked python-imaging 1.1.6-3ubuntu1
2009-10-28 21:01:32 status half-configured python-imaging 1.1.6-3ubuntu1
2009-10-28 21:01:32 status installed python-imaging 1.1.6-3ubuntu1
2009-10-28 21:01:32 configure hplip-data 3.9.8-1ubuntu2 3.9.8-1ubuntu2
2009-10-28 21:01:32 status unpacked hplip-data 3.9.8-1ubuntu2
2009-10-28 21:01:32 status half-configured hplip-data 3.9.8-1ubuntu2
2009-10-28 21:01:33 status installed hplip-data 3.9.8-1ubuntu2
2009-10-28 21:01:33 configure hplip 3.9.8-1ubuntu2 3.9.8-1ubuntu2
2009-10-28 21:01:33 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 21:01:33 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 21:01:33 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 21:01:33 status unpacked hplip 3.9.8-1ubuntu2
2009-10-28 21:01:33 status half-configured hplip 3.9.8-1ubuntu2
2009-10-28 21:01:34 status installed hplip 3.9.8-1ubuntu2
2009-10-28 21:01:34 configure wireless-crda 1.10 1.10
2009-10-28 21:01:34 status unpacked wireless-crda 1.10
2009-10-28 21:01:34 status half-configured wireless-crda 1.10
2009-10-28 21:01:34 status installed wireless-crda 1.10
2009-10-28 21:01:34 configure linux-image-2.6.31-14-generic 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:01:34 status unpacked linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:01:34 status half-configured linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:01:46 status installed linux-image-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:01:46 configure openoffice.org-emailmerge 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:01:46 status unpacked openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 21:01:46 status half-configured openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 21:01:50 status installed openoffice.org-emailmerge 1:3.1.1-5ubuntu1
2009-10-28 21:01:50 configure ttf-wqy-zenhei 0.8.38-1ubuntu1 0.8.38-1ubuntu1
2009-10-28 21:01:50 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:01:50 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:01:50 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:01:50 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:01:50 status unpacked ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:01:50 status half-configured ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:02:00 status installed ttf-wqy-zenhei 0.8.38-1ubuntu1
2009-10-28 21:02:00 configure xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 status unpacked xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 status unpacked xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 status unpacked xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 status half-configured xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 update-alternatives: run with --install /usr/bin/xulrunner xulrunner /usr/bin/xulrunner-1.9.1 50
2009-10-28 21:02:00 update-alternatives: link group xulrunner updated to point to /usr/bin/xulrunner-1.9.1
2009-10-28 21:02:00 status installed xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:02:00 configure python-libxml2 2.7.5.dfsg-1ubuntu1 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status unpacked python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status half-configured python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status installed python-libxml2 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 configure libxml2-utils 2.7.5.dfsg-1ubuntu1 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status unpacked libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status half-configured libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 status installed libxml2-utils 2.7.5.dfsg-1ubuntu1
2009-10-28 21:02:00 configure xsltproc 1.1.24-2ubuntu2 1.1.24-2ubuntu2
2009-10-28 21:02:00 status unpacked xsltproc 1.1.24-2ubuntu2
2009-10-28 21:02:00 status half-configured xsltproc 1.1.24-2ubuntu2
2009-10-28 21:02:00 status installed xsltproc 1.1.24-2ubuntu2
2009-10-28 21:02:00 configure gnome-doc-utils 0.18.0-0ubuntu1 0.18.0-0ubuntu1
2009-10-28 21:02:00 status unpacked gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 21:02:00 status half-configured gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 21:02:01 status installed gnome-doc-utils 0.18.0-0ubuntu1
2009-10-28 21:02:01 configure groff-base 1.20.1-5 1.20.1-5
2009-10-28 21:02:01 status unpacked groff-base 1.20.1-5
2009-10-28 21:02:01 status unpacked groff-base 1.20.1-5
2009-10-28 21:02:01 status unpacked groff-base 1.20.1-5
2009-10-28 21:02:01 status half-configured groff-base 1.20.1-5
2009-10-28 21:02:01 status installed groff-base 1.20.1-5
2009-10-28 21:02:01 configure bsdmainutils 6.1.10ubuntu4 6.1.10ubuntu4
2009-10-28 21:02:01 status unpacked bsdmainutils 6.1.10ubuntu4
2009-10-28 21:02:01 status unpacked bsdmainutils 6.1.10ubuntu4
2009-10-28 21:02:01 status unpacked bsdmainutils 6.1.10ubuntu4
2009-10-28 21:02:01 status half-configured bsdmainutils 6.1.10ubuntu4
2009-10-28 21:02:01 update-alternatives: run with --install /usr/bin/write write /usr/bin/bsd-write 100 --slave /usr/share/man/man1/write.1.gz write.1.gz /usr/share/man/man1/bsd-write.1.gz
2009-10-28 21:02:01 update-alternatives: link group write updated to point to /usr/bin/bsd-write
2009-10-28 21:02:01 status installed bsdmainutils 6.1.10ubuntu4
2009-10-28 21:02:01 configure man-db 2.5.6-2 2.5.6-2
2009-10-28 21:02:01 status unpacked man-db 2.5.6-2
2009-10-28 21:02:01 status unpacked man-db 2.5.6-2
2009-10-28 21:02:01 status unpacked man-db 2.5.6-2
2009-10-28 21:02:01 status unpacked man-db 2.5.6-2
2009-10-28 21:02:01 status half-configured man-db 2.5.6-2
2009-10-28 21:02:12 status installed man-db 2.5.6-2
2009-10-28 21:02:12 configure yelp 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:02:12 status unpacked yelp 2.28.0-0ubuntu2
2009-10-28 21:02:12 status half-configured yelp 2.28.0-0ubuntu2
2009-10-28 21:02:12 status installed yelp 2.28.0-0ubuntu2
2009-10-28 21:02:12 configure gnome-user-guide 2.28.0+git20090921ubuntu2 2.28.0+git20090921ubuntu2
2009-10-28 21:02:12 status unpacked gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 21:02:12 status half-configured gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 21:02:12 status installed gnome-user-guide 2.28.0+git20090921ubuntu2
2009-10-28 21:02:12 configure ubuntu-docs 9.10.11 9.10.11
2009-10-28 21:02:12 status unpacked ubuntu-docs 9.10.11
2009-10-28 21:02:12 status half-configured ubuntu-docs 9.10.11
2009-10-28 21:02:12 update-alternatives: run with --install /usr/share/ubuntu-artwork/home/index.html firefox-homepage /usr/share/ubuntu-artwork/home/firefox-index.html 40 --slave /usr/share/ubuntu-artwork/home/locales firefox-homepage-locales /usr/share/ubuntu-artwork/home/locales-ubuntu
2009-10-28 21:02:12 update-alternatives: link group firefox-homepage updated to point to /usr/share/ubuntu-artwork/home/firefox-index.html
2009-10-28 21:02:12 status installed ubuntu-docs 9.10.11
2009-10-28 21:02:12 configure x11-apps 7.4+2 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status unpacked x11-apps 7.4+2
2009-10-28 21:02:12 status half-configured x11-apps 7.4+2
2009-10-28 21:02:12 status installed x11-apps 7.4+2
2009-10-28 21:02:12 configure x11-session-utils 7.3+1build1 7.3+1build1
2009-10-28 21:02:12 status unpacked x11-session-utils 7.3+1build1
2009-10-28 21:02:12 status unpacked x11-session-utils 7.3+1build1
2009-10-28 21:02:12 status half-configured x11-session-utils 7.3+1build1
2009-10-28 21:02:12 status installed x11-session-utils 7.3+1build1
2009-10-28 21:02:12 configure libfontenc1 1:1.0.4-3 1:1.0.4-3
2009-10-28 21:02:12 status unpacked libfontenc1 1:1.0.4-3
2009-10-28 21:02:12 status half-configured libfontenc1 1:1.0.4-3
2009-10-28 21:02:12 status installed libfontenc1 1:1.0.4-3
2009-10-28 21:02:12 configure libdrm2 2.4.14-1ubuntu1 2.4.14-1ubuntu1
2009-10-28 21:02:12 status unpacked libdrm2 2.4.14-1ubuntu1
2009-10-28 21:02:12 status half-configured libdrm2 2.4.14-1ubuntu1
2009-10-28 21:02:12 status installed libdrm2 2.4.14-1ubuntu1
2009-10-28 21:02:12 configure libxxf86vm1 1:1.0.2-1ubuntu1 1:1.0.2-1ubuntu1
2009-10-28 21:02:12 status unpacked libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 21:02:12 status half-configured libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 21:02:12 status installed libxxf86vm1 1:1.0.2-1ubuntu1
2009-10-28 21:02:12 configure libgl1-mesa-glx 7.6.0-1ubuntu4 7.6.0-1ubuntu4
2009-10-28 21:02:12 status unpacked libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 21:02:12 status half-configured libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 21:02:12 status installed libgl1-mesa-glx 7.6.0-1ubuntu4
2009-10-28 21:02:12 configure libxv1 2:1.0.4-1 2:1.0.4-1
2009-10-28 21:02:12 status unpacked libxv1 2:1.0.4-1
2009-10-28 21:02:12 status half-configured libxv1 2:1.0.4-1
2009-10-28 21:02:12 status installed libxv1 2:1.0.4-1
2009-10-28 21:02:13 configure libxxf86dga1 2:1.0.2-1build1 2:1.0.2-1build1
2009-10-28 21:02:13 status unpacked libxxf86dga1 2:1.0.2-1build1
2009-10-28 21:02:13 status half-configured libxxf86dga1 2:1.0.2-1build1
2009-10-28 21:02:13 status installed libxxf86dga1 2:1.0.2-1build1
2009-10-28 21:02:13 configure x11-utils 7.4+1build1 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-utils 7.4+1build1
2009-10-28 21:02:13 status half-configured x11-utils 7.4+1build1
2009-10-28 21:02:13 status installed x11-utils 7.4+1build1
2009-10-28 21:02:13 configure libfs6 2:1.0.2-1 2:1.0.2-1
2009-10-28 21:02:13 status unpacked libfs6 2:1.0.2-1
2009-10-28 21:02:13 status half-configured libfs6 2:1.0.2-1
2009-10-28 21:02:13 status installed libfs6 2:1.0.2-1
2009-10-28 21:02:13 configure x11-xfs-utils 7.4+1build1 7.4+1build1
2009-10-28 21:02:13 status unpacked x11-xfs-utils 7.4+1build1
2009-10-28 21:02:13 status half-configured x11-xfs-utils 7.4+1build1
2009-10-28 21:02:13 status installed x11-xfs-utils 7.4+1build1
2009-10-28 21:02:13 configure libxtrap6 2:1.0.0-5build1 2:1.0.0-5build1
2009-10-28 21:02:13 status unpacked libxtrap6 2:1.0.0-5build1
2009-10-28 21:02:13 status half-configured libxtrap6 2:1.0.0-5build1
2009-10-28 21:02:13 status installed libxtrap6 2:1.0.0-5build1
2009-10-28 21:02:13 configure x11-xserver-utils 7.4+2ubuntu3 7.4+2ubuntu3
2009-10-28 21:02:13 status unpacked x11-xserver-utils 7.4+2ubuntu3
2009-10-28 21:02:13 status unpacked x11-xserver-utils 7.4+2ubuntu3
2009-10-28 21:02:13 status half-configured x11-xserver-utils 7.4+2ubuntu3
2009-10-28 21:02:13 status installed x11-xserver-utils 7.4+2ubuntu3
2009-10-28 21:02:13 configure xbitmaps 1.0.1-2ubuntu1 1.0.1-2ubuntu1
2009-10-28 21:02:13 status unpacked xbitmaps 1.0.1-2ubuntu1
2009-10-28 21:02:13 status half-configured xbitmaps 1.0.1-2ubuntu1
2009-10-28 21:02:13 status installed xbitmaps 1.0.1-2ubuntu1
2009-10-28 21:02:13 configure apparmor 2.3.1+1403-0ubuntu27 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status half-configured apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status installed apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status triggers-awaited apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 configure libterm-readkey-perl 2.30-4 2.30-4
2009-10-28 21:02:13 status unpacked libterm-readkey-perl 2.30-4
2009-10-28 21:02:13 status half-configured libterm-readkey-perl 2.30-4
2009-10-28 21:02:13 status installed libterm-readkey-perl 2.30-4
2009-10-28 21:02:13 configure liburi-perl 1.37+dfsg-1ubuntu1 1.37+dfsg-1ubuntu1
2009-10-28 21:02:13 status unpacked liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 21:02:13 status half-configured liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 21:02:13 status installed liburi-perl 1.37+dfsg-1ubuntu1
2009-10-28 21:02:13 configure libhtml-tagset-perl 3.20-2 3.20-2
2009-10-28 21:02:13 status unpacked libhtml-tagset-perl 3.20-2
2009-10-28 21:02:13 status half-configured libhtml-tagset-perl 3.20-2
2009-10-28 21:02:13 status installed libhtml-tagset-perl 3.20-2
2009-10-28 21:02:13 configure libhtml-parser-perl 3.61-1 3.61-1
2009-10-28 21:02:13 status unpacked libhtml-parser-perl 3.61-1
2009-10-28 21:02:13 status half-configured libhtml-parser-perl 3.61-1
2009-10-28 21:02:13 status installed libhtml-parser-perl 3.61-1
2009-10-28 21:02:13 configure libhtml-tree-perl 3.23-1 3.23-1
2009-10-28 21:02:13 status unpacked libhtml-tree-perl 3.23-1
2009-10-28 21:02:13 status half-configured libhtml-tree-perl 3.23-1
2009-10-28 21:02:13 status installed libhtml-tree-perl 3.23-1
2009-10-28 21:02:13 configure libwww-perl 5.831-1 5.831-1
2009-10-28 21:02:13 status unpacked libwww-perl 5.831-1
2009-10-28 21:02:13 status half-configured libwww-perl 5.831-1
2009-10-28 21:02:13 status installed libwww-perl 5.831-1
2009-10-28 21:02:13 configure libxml-parser-perl 2.36-1.1build2 2.36-1.1build2
2009-10-28 21:02:13 status unpacked libxml-parser-perl 2.36-1.1build2
2009-10-28 21:02:13 status half-configured libxml-parser-perl 2.36-1.1build2
2009-10-28 21:02:13 status installed libxml-parser-perl 2.36-1.1build2
2009-10-28 21:02:13 configure librpc-xml-perl 0.64-1 0.64-1
2009-10-28 21:02:13 status unpacked librpc-xml-perl 0.64-1
2009-10-28 21:02:13 status half-configured librpc-xml-perl 0.64-1
2009-10-28 21:02:13 status installed librpc-xml-perl 0.64-1
2009-10-28 21:02:13 configure libapparmor1 2.3.1+1403-0ubuntu27 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status half-configured libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status installed libapparmor1 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 configure libapparmor-perl 2.3.1+1403-0ubuntu27 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status unpacked libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status half-configured libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 status installed libapparmor-perl 2.3.1+1403-0ubuntu27
2009-10-28 21:02:13 configure apt-transport-https 0.7.23.1ubuntu2 0.7.23.1ubuntu2
2009-10-28 21:02:13 status unpacked apt-transport-https 0.7.23.1ubuntu2
2009-10-28 21:02:13 status half-configured apt-transport-https 0.7.23.1ubuntu2
2009-10-28 21:02:13 status installed apt-transport-https 0.7.23.1ubuntu2
2009-10-28 21:02:13 configure at 3.1.11-1ubuntu4 3.1.11-1ubuntu4
2009-10-28 21:02:13 status unpacked at 3.1.11-1ubuntu4
2009-10-28 21:02:13 status unpacked at 3.1.11-1ubuntu4
2009-10-28 21:02:13 status unpacked at 3.1.11-1ubuntu4
2009-10-28 21:02:13 status unpacked at 3.1.11-1ubuntu4
2009-10-28 21:02:13 status half-configured at 3.1.11-1ubuntu4
2009-10-28 21:02:13 status installed at 3.1.11-1ubuntu4
2009-10-28 21:02:13 configure bash-completion 1:1.0-3ubuntu2 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status unpacked bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:13 status half-configured bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:14 status installed bash-completion 1:1.0-3ubuntu2
2009-10-28 21:02:14 configure libgeoip1 1.4.6.dfsg-5 1.4.6.dfsg-5
2009-10-28 21:02:14 status unpacked libgeoip1 1.4.6.dfsg-5
2009-10-28 21:02:14 status half-configured libgeoip1 1.4.6.dfsg-5
2009-10-28 21:02:14 status installed libgeoip1 1.4.6.dfsg-5
2009-10-28 21:02:14 configure libisc50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed libisc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure libdns50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed libdns50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure libisccc50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed libisccc50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure libisccfg50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed libisccfg50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure libbind9-50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed libbind9-50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure liblwres50 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed liblwres50 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure bind9-host 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed bind9-host 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure command-not-found-data 0.2.38ubuntu4 0.2.38ubuntu4
2009-10-28 21:02:14 status unpacked command-not-found-data 0.2.38ubuntu4
2009-10-28 21:02:14 status half-configured command-not-found-data 0.2.38ubuntu4
2009-10-28 21:02:14 status installed command-not-found-data 0.2.38ubuntu4
2009-10-28 21:02:14 configure python-gdbm 2.6.3-0ubuntu1 2.6.3-0ubuntu1
2009-10-28 21:02:14 status unpacked python-gdbm 2.6.3-0ubuntu1
2009-10-28 21:02:14 status half-configured python-gdbm 2.6.3-0ubuntu1
2009-10-28 21:02:14 status installed python-gdbm 2.6.3-0ubuntu1
2009-10-28 21:02:14 configure command-not-found 0.2.38ubuntu4 0.2.38ubuntu4
2009-10-28 21:02:14 status unpacked command-not-found 0.2.38ubuntu4
2009-10-28 21:02:14 status unpacked command-not-found 0.2.38ubuntu4
2009-10-28 21:02:14 status half-configured command-not-found 0.2.38ubuntu4
2009-10-28 21:02:14 status installed command-not-found 0.2.38ubuntu4
2009-10-28 21:02:14 configure cron 3.0pl1-106ubuntu3 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status unpacked cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status half-configured cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 status installed cron 3.0pl1-106ubuntu3
2009-10-28 21:02:14 configure dnsutils 1:9.6.1.dfsg.P1-3 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status unpacked dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status half-configured dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 status installed dnsutils 1:9.6.1.dfsg.P1-3
2009-10-28 21:02:14 configure dosfstools 3.0.3-1 3.0.3-1
2009-10-28 21:02:14 status unpacked dosfstools 3.0.3-1
2009-10-28 21:02:14 status half-configured dosfstools 3.0.3-1
2009-10-28 21:02:14 status installed dosfstools 3.0.3-1
2009-10-28 21:02:14 configure ed 1.4-1 1.4-1
2009-10-28 21:02:14 status unpacked ed 1.4-1
2009-10-28 21:02:14 status half-configured ed 1.4-1
2009-10-28 21:02:14 update-alternatives: run with --quiet --install /usr/bin/editor editor /bin/ed -100 --slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/ed.1.gz
2009-10-28 21:02:14 status installed ed 1.4-1
2009-10-28 21:02:14 configure friendly-recovery 0.2.8.2 0.2.8.2
2009-10-28 21:02:14 status unpacked friendly-recovery 0.2.8.2
2009-10-28 21:02:14 status half-configured friendly-recovery 0.2.8.2
2009-10-28 21:02:14 status installed friendly-recovery 0.2.8.2
2009-10-28 21:02:14 configure ftp 0.17-19 0.17-19
2009-10-28 21:02:14 status unpacked ftp 0.17-19
2009-10-28 21:02:14 status half-configured ftp 0.17-19
2009-10-28 21:02:14 update-alternatives: run with --install /usr/bin/ftp ftp /usr/bin/netkit-ftp 100 --slave /usr/share/man/man1/ftp.1.gz ftp.1.gz /usr/share/man/man1/netkit-ftp.1.gz
2009-10-28 21:02:14 update-alternatives: link group ftp updated to point to /usr/bin/netkit-ftp
2009-10-28 21:02:14 status installed ftp 0.17-19
2009-10-28 21:02:14 configure geoip-database 1.4.6.dfsg-5 1.4.6.dfsg-5
2009-10-28 21:02:14 status unpacked geoip-database 1.4.6.dfsg-5
2009-10-28 21:02:15 status half-configured geoip-database 1.4.6.dfsg-5
2009-10-28 21:02:15 status installed geoip-database 1.4.6.dfsg-5
2009-10-28 21:02:15 configure gettext-base 0.17-8ubuntu2 0.17-8ubuntu2
2009-10-28 21:02:15 status unpacked gettext-base 0.17-8ubuntu2
2009-10-28 21:02:15 status half-configured gettext-base 0.17-8ubuntu2
2009-10-28 21:02:15 status installed gettext-base 0.17-8ubuntu2
2009-10-28 21:02:15 configure hdparm 9.15-1ubuntu4 9.15-1ubuntu4
2009-10-28 21:02:15 status unpacked hdparm 9.15-1ubuntu4
2009-10-28 21:02:15 status unpacked hdparm 9.15-1ubuntu4
2009-10-28 21:02:15 status unpacked hdparm 9.15-1ubuntu4
2009-10-28 21:02:15 status half-configured hdparm 9.15-1ubuntu4
2009-10-28 21:02:15 status installed hdparm 9.15-1ubuntu4
2009-10-28 21:02:15 configure install-info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 status unpacked install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 status half-configured install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 status installed install-info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 configure info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 status unpacked info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 status half-configured info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 update-alternatives: run with --install /usr/bin/infobrowser infobrowser /usr/bin/info 60 --slave /usr/share/man/man1/infobrowser.1.gz infobrowser.1.gz /usr/share/man/man1/info.1.gz
2009-10-28 21:02:15 update-alternatives: link group infobrowser updated to point to /usr/bin/info
2009-10-28 21:02:15 status installed info 4.13a.dfsg.1-4ubuntu1
2009-10-28 21:02:15 configure iptables 1.4.4-1ubuntu1 1.4.4-1ubuntu1
2009-10-28 21:02:15 status unpacked iptables 1.4.4-1ubuntu1
2009-10-28 21:02:15 status half-configured iptables 1.4.4-1ubuntu1
2009-10-28 21:02:15 status installed iptables 1.4.4-1ubuntu1
2009-10-28 21:02:15 configure iputils-arping 3:20071127-1build1 3:20071127-1build1
2009-10-28 21:02:15 status unpacked iputils-arping 3:20071127-1build1
2009-10-28 21:02:15 status half-configured iputils-arping 3:20071127-1build1
2009-10-28 21:02:15 status installed iputils-arping 3:20071127-1build1
2009-10-28 21:02:15 configure iputils-tracepath 3:20071127-1build1 3:20071127-1build1
2009-10-28 21:02:15 status unpacked iputils-tracepath 3:20071127-1build1
2009-10-28 21:02:15 status half-configured iputils-tracepath 3:20071127-1build1
2009-10-28 21:02:15 update-alternatives: run with --install /usr/bin/traceroute6 traceroute6 /usr/bin/traceroute6.iputils 100 --slave /usr/share/man/man8/traceroute6.8.gz traceroute6.8.gz /usr/share/man/man8/traceroute6.iputils.8.gz
2009-10-28 21:02:15 update-alternatives: link group traceroute6 updated to point to /usr/bin/traceroute6.iputils
2009-10-28 21:02:15 status installed iputils-tracepath 3:20071127-1build1
2009-10-28 21:02:15 configure iso-codes 3.10.2-1 3.10.2-1
2009-10-28 21:02:15 status unpacked iso-codes 3.10.2-1
2009-10-28 21:02:15 status half-configured iso-codes 3.10.2-1
2009-10-28 21:02:15 status installed iso-codes 3.10.2-1
2009-10-28 21:02:15 configure libbsd0 0.1.4-1 0.1.4-1
2009-10-28 21:02:15 status unpacked libbsd0 0.1.4-1
2009-10-28 21:02:15 status half-configured libbsd0 0.1.4-1
2009-10-28 21:02:15 status installed libbsd0 0.1.4-1
2009-10-28 21:02:15 configure libcompress-bzip2-perl 2.09-2 2.09-2
2009-10-28 21:02:15 status unpacked libcompress-bzip2-perl 2.09-2
2009-10-28 21:02:15 status half-configured libcompress-bzip2-perl 2.09-2
2009-10-28 21:02:15 status installed libcompress-bzip2-perl 2.09-2
2009-10-28 21:02:15 configure libedit2 2.11-20080614-1 2.11-20080614-1
2009-10-28 21:02:15 status unpacked libedit2 2.11-20080614-1
2009-10-28 21:02:15 status half-configured libedit2 2.11-20080614-1
2009-10-28 21:02:15 status installed libedit2 2.11-20080614-1
2009-10-28 21:02:15 configure libelf1 0.141-2ubuntu2 0.141-2ubuntu2
2009-10-28 21:02:15 status unpacked libelf1 0.141-2ubuntu2
2009-10-28 21:02:15 status half-configured libelf1 0.141-2ubuntu2
2009-10-28 21:02:15 status installed libelf1 0.141-2ubuntu2
2009-10-28 21:02:15 configure libfont-afm-perl 1.20-1 1.20-1
2009-10-28 21:02:15 status unpacked libfont-afm-perl 1.20-1
2009-10-28 21:02:15 status half-configured libfont-afm-perl 1.20-1
2009-10-28 21:02:15 status installed libfont-afm-perl 1.20-1
2009-10-28 21:02:15 configure libgc1c2 1:6.8-1.2 1:6.8-1.2
2009-10-28 21:02:15 status unpacked libgc1c2 1:6.8-1.2
2009-10-28 21:02:15 status half-configured libgc1c2 1:6.8-1.2
2009-10-28 21:02:15 status installed libgc1c2 1:6.8-1.2
2009-10-28 21:02:15 configure libhtml-format-perl 2.04-2 2.04-2
2009-10-28 21:02:15 status unpacked libhtml-format-perl 2.04-2
2009-10-28 21:02:15 status half-configured libhtml-format-perl 2.04-2
2009-10-28 21:02:15 status installed libhtml-format-perl 2.04-2
2009-10-28 21:02:15 configure libjs-jquery 1.3.3-1ubuntu1 1.3.3-1ubuntu1
2009-10-28 21:02:15 status unpacked libjs-jquery 1.3.3-1ubuntu1
2009-10-28 21:02:15 status half-configured libjs-jquery 1.3.3-1ubuntu1
2009-10-28 21:02:15 status installed libjs-jquery 1.3.3-1ubuntu1
2009-10-28 21:02:15 configure libmailtools-perl 2.04-1 2.04-1
2009-10-28 21:02:15 status unpacked libmailtools-perl 2.04-1
2009-10-28 21:02:15 status half-configured libmailtools-perl 2.04-1
2009-10-28 21:02:15 status installed libmailtools-perl 2.04-1
2009-10-28 21:02:15 configure libpcap0.8 1.0.0-2ubuntu1 1.0.0-2ubuntu1
2009-10-28 21:02:15 status unpacked libpcap0.8 1.0.0-2ubuntu1
2009-10-28 21:02:15 status half-configured libpcap0.8 1.0.0-2ubuntu1
2009-10-28 21:02:15 status installed libpcap0.8 1.0.0-2ubuntu1
2009-10-28 21:02:15 configure libpci3 1:3.0.0-4ubuntu13 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status unpacked libpci3 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status half-configured libpci3 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status installed libpci3 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 configure anacron 2.3-13.1ubuntu10 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status unpacked anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status half-configured anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 status installed anacron 2.3-13.1ubuntu10
2009-10-28 21:02:15 configure logrotate 3.7.8-4ubuntu1 3.7.8-4ubuntu1
2009-10-28 21:02:15 status unpacked logrotate 3.7.8-4ubuntu1
2009-10-28 21:02:15 status unpacked logrotate 3.7.8-4ubuntu1
2009-10-28 21:02:15 status unpacked logrotate 3.7.8-4ubuntu1
2009-10-28 21:02:15 status half-configured logrotate 3.7.8-4ubuntu1
2009-10-28 21:02:15 status installed logrotate 3.7.8-4ubuntu1
2009-10-28 21:02:15 configure pciutils 1:3.0.0-4ubuntu13 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status unpacked pciutils 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status half-configured pciutils 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 status installed pciutils 1:3.0.0-4ubuntu13
2009-10-28 21:02:15 configure usbutils 0.82-0ubuntu1 0.82-0ubuntu1
2009-10-28 21:02:15 status unpacked usbutils 0.82-0ubuntu1
2009-10-28 21:02:15 status half-configured usbutils 0.82-0ubuntu1
2009-10-28 21:02:15 status installed usbutils 0.82-0ubuntu1
2009-10-28 21:02:15 configure lshw 02.14-1 02.14-1
2009-10-28 21:02:15 status unpacked lshw 02.14-1
2009-10-28 21:02:15 status half-configured lshw 02.14-1
2009-10-28 21:02:15 status installed lshw 02.14-1
2009-10-28 21:02:15 configure lsof 4.81.dfsg.1-1 4.81.dfsg.1-1
2009-10-28 21:02:15 status unpacked lsof 4.81.dfsg.1-1
2009-10-28 21:02:15 status half-configured lsof 4.81.dfsg.1-1
2009-10-28 21:02:15 status installed lsof 4.81.dfsg.1-1
2009-10-28 21:02:15 configure ltrace 0.5.3-2ubuntu2 0.5.3-2ubuntu2
2009-10-28 21:02:15 status unpacked ltrace 0.5.3-2ubuntu2
2009-10-28 21:02:15 status unpacked ltrace 0.5.3-2ubuntu2
2009-10-28 21:02:15 status half-configured ltrace 0.5.3-2ubuntu2
2009-10-28 21:02:15 status installed ltrace 0.5.3-2ubuntu2
2009-10-28 21:02:15 configure manpages 3.21-1 3.21-1
2009-10-28 21:02:15 status unpacked manpages 3.21-1
2009-10-28 21:02:15 status half-configured manpages 3.21-1
2009-10-28 21:02:15 status installed manpages 3.21-1
2009-10-28 21:02:15 configure memtest86+ 2.11-3ubuntu5 2.11-3ubuntu5
2009-10-28 21:02:15 status unpacked memtest86+ 2.11-3ubuntu5
2009-10-28 21:02:15 status unpacked memtest86+ 2.11-3ubuntu5
2009-10-28 21:02:15 status half-configured memtest86+ 2.11-3ubuntu5
2009-10-28 21:02:15 status installed memtest86+ 2.11-3ubuntu5
2009-10-28 21:02:15 configure mlocate 0.21.1-2 0.21.1-2
2009-10-28 21:02:15 status unpacked mlocate 0.21.1-2
2009-10-28 21:02:15 status unpacked mlocate 0.21.1-2
2009-10-28 21:02:15 status unpacked mlocate 0.21.1-2
2009-10-28 21:02:15 status half-configured mlocate 0.21.1-2
2009-10-28 21:02:16 update-alternatives: run with --install /usr/bin/locate locate /usr/bin/mlocate 80 --slave /usr/share/man/man1/locate.1.gz locate.1.gz /usr/share/man/man1/mlocate.1.gz --slave /usr/bin/updatedb updatedb /usr/bin/updatedb.mlocate
2009-10-28 21:02:16 update-alternatives: link group locate updated to point to /usr/bin/mlocate
2009-10-28 21:02:16 status installed mlocate 0.21.1-2
2009-10-28 21:02:16 configure mtr-tiny 0.75-2 0.75-2
2009-10-28 21:02:16 status unpacked mtr-tiny 0.75-2
2009-10-28 21:02:16 status half-configured mtr-tiny 0.75-2
2009-10-28 21:02:16 status installed mtr-tiny 0.75-2
2009-10-28 21:02:16 configure nano 2.0.9-2 2.0.9-2
2009-10-28 21:02:16 status unpacked nano 2.0.9-2
2009-10-28 21:02:16 status unpacked nano 2.0.9-2
2009-10-28 21:02:16 status half-configured nano 2.0.9-2
2009-10-28 21:02:16 update-alternatives: run with --install /usr/bin/editor editor /bin/nano 40 --slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/nano.1.gz
2009-10-28 21:02:16 update-alternatives: link group editor updated to point to /bin/nano
2009-10-28 21:02:16 update-alternatives: run with --install /usr/bin/pico pico /bin/nano 10 --slave /usr/share/man/man1/pico.1.gz pico.1.gz /usr/share/man/man1/nano.1.gz
2009-10-28 21:02:16 update-alternatives: link group pico updated to point to /bin/nano
2009-10-28 21:02:16 status installed nano 2.0.9-2
2009-10-28 21:02:16 configure openssh-client 1:5.1p1-6ubuntu2 1:5.1p1-6ubuntu2
2009-10-28 21:02:16 status unpacked openssh-client 1:5.1p1-6ubuntu2
2009-10-28 21:02:16 status unpacked openssh-client 1:5.1p1-6ubuntu2
2009-10-28 21:02:16 status unpacked openssh-client 1:5.1p1-6ubuntu2
2009-10-28 21:02:16 status half-configured openssh-client 1:5.1p1-6ubuntu2
2009-10-28 21:02:16 update-alternatives: run with --quiet --install /usr/bin/rsh rsh /usr/bin/ssh 20 --slave /usr/share/man/man1/rsh.1.gz rsh.1.gz /usr/share/man/man1/ssh.1.gz
2009-10-28 21:02:16 update-alternatives: link group rsh updated to point to /usr/bin/ssh
2009-10-28 21:02:17 update-alternatives: run with --quiet --install /usr/bin/rlogin rlogin /usr/bin/slogin 20 --slave /usr/share/man/man1/rlogin.1.gz rlogin.1.gz /usr/share/man/man1/slogin.1.gz
2009-10-28 21:02:17 update-alternatives: link group rlogin updated to point to /usr/bin/slogin
2009-10-28 21:02:17 update-alternatives: run with --quiet --install /usr/bin/rcp rcp /usr/bin/scp 20 --slave /usr/share/man/man1/rcp.1.gz rcp.1.gz /usr/share/man/man1/scp.1.gz
2009-10-28 21:02:17 update-alternatives: link group rcp updated to point to /usr/bin/scp
2009-10-28 21:02:17 status installed openssh-client 1:5.1p1-6ubuntu2
2009-10-28 21:02:17 configure parted 1.8.8.git.2009.06.03-1ubuntu6 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:02:17 status unpacked parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:02:17 status half-configured parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:02:17 status installed parted 1.8.8.git.2009.06.03-1ubuntu6
2009-10-28 21:02:17 configure popularity-contest 1.48ubuntu1 1.48ubuntu1
2009-10-28 21:02:17 status unpacked popularity-contest 1.48ubuntu1
2009-10-28 21:02:17 status unpacked popularity-contest 1.48ubuntu1
2009-10-28 21:02:17 status half-configured popularity-contest 1.48ubuntu1
2009-10-28 21:02:17 status installed popularity-contest 1.48ubuntu1
2009-10-28 21:02:17 configure powermgmt-base 1.30+nmu1 1.30+nmu1
2009-10-28 21:02:17 status unpacked powermgmt-base 1.30+nmu1
2009-10-28 21:02:17 status half-configured powermgmt-base 1.30+nmu1
2009-10-28 21:02:18 status installed powermgmt-base 1.30+nmu1
2009-10-28 21:02:18 configure ppp 2.4.5~git20081126t100229-0ubuntu2 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status unpacked ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status half-configured ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 status installed ppp 2.4.5~git20081126t100229-0ubuntu2
2009-10-28 21:02:18 configure pppconfig 2.3.18ubuntu2 2.3.18ubuntu2
2009-10-28 21:02:18 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 status unpacked pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 status half-configured pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 status installed pppconfig 2.3.18ubuntu2
2009-10-28 21:02:18 configure pppoeconf 1.18ubuntu1 1.18ubuntu1
2009-10-28 21:02:18 status unpacked pppoeconf 1.18ubuntu1
2009-10-28 21:02:18 status half-configured pppoeconf 1.18ubuntu1
2009-10-28 21:02:18 status installed pppoeconf 1.18ubuntu1
2009-10-28 21:02:18 configure python-gnupginterface 0.3.2-9ubuntu2 0.3.2-9ubuntu2
2009-10-28 21:02:18 status unpacked python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 21:02:18 status half-configured python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 21:02:18 status installed python-gnupginterface 0.3.2-9ubuntu2
2009-10-28 21:02:18 configure rsync 3.0.6-1ubuntu1 3.0.6-1ubuntu1
2009-10-28 21:02:18 status unpacked rsync 3.0.6-1ubuntu1
2009-10-28 21:02:18 status unpacked rsync 3.0.6-1ubuntu1
2009-10-28 21:02:18 status unpacked rsync 3.0.6-1ubuntu1
2009-10-28 21:02:18 status half-configured rsync 3.0.6-1ubuntu1
2009-10-28 21:02:18 status installed rsync 3.0.6-1ubuntu1
2009-10-28 21:02:18 configure strace 4.5.18-1ubuntu2 4.5.18-1ubuntu2
2009-10-28 21:02:18 status unpacked strace 4.5.18-1ubuntu2
2009-10-28 21:02:18 status half-configured strace 4.5.18-1ubuntu2
2009-10-28 21:02:18 status installed strace 4.5.18-1ubuntu2
2009-10-28 21:02:18 configure tcpdump 4.0.0-2ubuntu2 4.0.0-2ubuntu2
2009-10-28 21:02:18 status unpacked tcpdump 4.0.0-2ubuntu2
2009-10-28 21:02:18 status unpacked tcpdump 4.0.0-2ubuntu2
2009-10-28 21:02:18 status half-configured tcpdump 4.0.0-2ubuntu2
2009-10-28 21:02:18 status installed tcpdump 4.0.0-2ubuntu2
2009-10-28 21:02:18 configure telnet 0.17-36 0.17-36
2009-10-28 21:02:18 status unpacked telnet 0.17-36
2009-10-28 21:02:18 status half-configured telnet 0.17-36
2009-10-28 21:02:18 update-alternatives: run with --install /usr/bin/telnet telnet /usr/bin/telnet.netkit 100 --slave /usr/share/man/man1/telnet.1.gz telnet.1.gz /usr/share/man/man1/telnet.netkit.1.gz
2009-10-28 21:02:18 update-alternatives: link group telnet updated to point to /usr/bin/telnet.netkit
2009-10-28 21:02:18 status installed telnet 0.17-36
2009-10-28 21:02:18 configure time 1.7-23 1.7-23
2009-10-28 21:02:18 status unpacked time 1.7-23
2009-10-28 21:02:18 status half-configured time 1.7-23
2009-10-28 21:02:18 status installed time 1.7-23
2009-10-28 21:02:18 configure ubuntu-standard 1.175 1.175
2009-10-28 21:02:18 status unpacked ubuntu-standard 1.175
2009-10-28 21:02:18 status half-configured ubuntu-standard 1.175
2009-10-28 21:02:18 status installed ubuntu-standard 1.175
2009-10-28 21:02:18 configure ufw 0.29-4ubuntu1 0.29-4ubuntu1
2009-10-28 21:02:18 status unpacked ufw 0.29-4ubuntu1
2009-10-28 21:02:18 status unpacked ufw 0.29-4ubuntu1
2009-10-28 21:02:18 status unpacked ufw 0.29-4ubuntu1
2009-10-28 21:02:18 status unpacked ufw 0.29-4ubuntu1
2009-10-28 21:02:18 status unpacked ufw 0.29-4ubuntu1
2009-10-28 21:02:18 status half-configured ufw 0.29-4ubuntu1
2009-10-28 21:02:20 status installed ufw 0.29-4ubuntu1
2009-10-28 21:02:20 configure update-manager-core 1:0.126.6 1:0.126.6
2009-10-28 21:02:20 status unpacked update-manager-core 1:0.126.6
2009-10-28 21:02:20 status unpacked update-manager-core 1:0.126.6
2009-10-28 21:02:20 status unpacked update-manager-core 1:0.126.6
2009-10-28 21:02:20 status half-configured update-manager-core 1:0.126.6
2009-10-28 21:02:20 status installed update-manager-core 1:0.126.6
2009-10-28 21:02:20 configure uuid-runtime 2.16-1ubuntu5 2.16-1ubuntu5
2009-10-28 21:02:20 status unpacked uuid-runtime 2.16-1ubuntu5
2009-10-28 21:02:20 status half-configured uuid-runtime 2.16-1ubuntu5
2009-10-28 21:02:20 status installed uuid-runtime 2.16-1ubuntu5
2009-10-28 21:02:20 configure w3m 0.5.2-2ubuntu1 0.5.2-2ubuntu1
2009-10-28 21:02:20 status unpacked w3m 0.5.2-2ubuntu1
2009-10-28 21:02:20 status unpacked w3m 0.5.2-2ubuntu1
2009-10-28 21:02:20 status unpacked w3m 0.5.2-2ubuntu1
2009-10-28 21:02:20 status half-configured w3m 0.5.2-2ubuntu1
2009-10-28 21:02:20 update-alternatives: run with --quiet --install /usr/bin/pager pager /usr/bin/w3m 25 --slave /usr/share/man/man1/pager.1.gz pager.1.gz /usr/share/man/man1/w3m.1.gz
2009-10-28 21:02:20 update-alternatives: run with --quiet --install /usr/bin/www-browser www-browser /usr/bin/w3m 25 --slave /usr/share/man/man1/www-browser.1.gz www-browser.1.gz /usr/share/man/man1/w3m.1.gz
2009-10-28 21:02:20 update-alternatives: link group www-browser updated to point to /usr/bin/w3m
2009-10-28 21:02:20 status installed w3m 0.5.2-2ubuntu1
2009-10-28 21:02:20 configure laptop-mode-tools 1.47-1ubuntu2 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status unpacked laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status half-configured laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 status installed laptop-mode-tools 1.47-1ubuntu2
2009-10-28 21:02:20 configure acpid 1.0.6-9ubuntu8 1.0.6-9ubuntu8
2009-10-28 21:02:20 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 21:02:20 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 21:02:20 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 21:02:20 status unpacked acpid 1.0.6-9ubuntu8
2009-10-28 21:02:20 status half-configured acpid 1.0.6-9ubuntu8
2009-10-28 21:02:20 status installed acpid 1.0.6-9ubuntu8
2009-10-28 21:02:21 configure finger 0.17-13 0.17-13
2009-10-28 21:02:21 status unpacked finger 0.17-13
2009-10-28 21:02:21 status half-configured finger 0.17-13
2009-10-28 21:02:21 status installed finger 0.17-13
2009-10-28 21:02:21 configure pm-utils 1.2.5-2ubuntu7 1.2.5-2ubuntu7
2009-10-28 21:02:21 status unpacked pm-utils 1.2.5-2ubuntu7
2009-10-28 21:02:21 status unpacked pm-utils 1.2.5-2ubuntu7
2009-10-28 21:02:21 status unpacked pm-utils 1.2.5-2ubuntu7
2009-10-28 21:02:21 status half-configured pm-utils 1.2.5-2ubuntu7
2009-10-28 21:02:21 status installed pm-utils 1.2.5-2ubuntu7
2009-10-28 21:02:21 configure acpi-support 0.129 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status unpacked acpi-support 0.129
2009-10-28 21:02:21 status half-configured acpi-support 0.129
2009-10-28 21:02:21 status installed acpi-support 0.129
2009-10-28 21:02:21 configure guile-1.8-libs 1.8.7+1-1ubuntu3 1.8.7+1-1ubuntu3
2009-10-28 21:02:21 status unpacked guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 21:02:21 status half-configured guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 21:02:21 status installed guile-1.8-libs 1.8.7+1-1ubuntu3
2009-10-28 21:02:21 configure gnome-games-common 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:21 status unpacked gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 21:02:21 status half-configured gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 status installed gnome-games-common 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 configure aisleriot 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 status unpacked aisleriot 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 status half-configured aisleriot 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 status installed aisleriot 1:2.28.0-0ubuntu1
2009-10-28 21:02:22 configure alacarte 0.12.4-0ubuntu2 0.12.4-0ubuntu2
2009-10-28 21:02:22 status unpacked alacarte 0.12.4-0ubuntu2
2009-10-28 21:02:22 status half-configured alacarte 0.12.4-0ubuntu2
2009-10-28 21:02:22 status installed alacarte 0.12.4-0ubuntu2
2009-10-28 21:02:22 configure linux-sound-base 1.0.20+dfsg-1ubuntu5 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:22 status unpacked linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:22 status half-configured linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status installed linux-sound-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 configure alsa-base 1.0.20+dfsg-1ubuntu5 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status unpacked alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status half-configured alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 status installed alsa-base 1.0.20+dfsg-1ubuntu5
2009-10-28 21:02:23 configure alsa-utils 1.0.20-2ubuntu6 1.0.20-2ubuntu6
2009-10-28 21:02:23 status unpacked alsa-utils 1.0.20-2ubuntu6
2009-10-28 21:02:23 status unpacked alsa-utils 1.0.20-2ubuntu6
2009-10-28 21:02:23 status half-configured alsa-utils 1.0.20-2ubuntu6
2009-10-28 21:02:23 status installed alsa-utils 1.0.20-2ubuntu6
2009-10-28 21:02:23 configure app-install-data 0.9.10.11 0.9.10.11
2009-10-28 21:02:23 status unpacked app-install-data 0.9.10.11
2009-10-28 21:02:23 status unpacked app-install-data 0.9.10.11
2009-10-28 21:02:23 status half-configured app-install-data 0.9.10.11
2009-10-28 21:02:23 status installed app-install-data 0.9.10.11
2009-10-28 21:02:23 configure app-install-data-partner 12.9.10 12.9.10
2009-10-28 21:02:23 status unpacked app-install-data-partner 12.9.10
2009-10-28 21:02:23 status half-configured app-install-data-partner 12.9.10
2009-10-28 21:02:23 status installed app-install-data-partner 12.9.10
2009-10-28 21:02:23 configure python-problem-report 1.9.3-0ubuntu4 1.9.3-0ubuntu4
2009-10-28 21:02:23 status unpacked python-problem-report 1.9.3-0ubuntu4
2009-10-28 21:02:23 status half-configured python-problem-report 1.9.3-0ubuntu4
2009-10-28 21:02:23 status installed python-problem-report 1.9.3-0ubuntu4
2009-10-28 21:02:23 configure python-simplejson 2.0.9-1 2.0.9-1
2009-10-28 21:02:23 status unpacked python-simplejson 2.0.9-1
2009-10-28 21:02:23 status half-configured python-simplejson 2.0.9-1
2009-10-28 21:02:23 status installed python-simplejson 2.0.9-1
2009-10-28 21:02:23 configure python-lazr-uri 1.0-0ubuntu1 1.0-0ubuntu1
2009-10-28 21:02:23 status unpacked python-lazr-uri 1.0-0ubuntu1
2009-10-28 21:02:23 status half-configured python-lazr-uri 1.0-0ubuntu1
2009-10-28 21:02:23 status installed python-lazr-uri 1.0-0ubuntu1
2009-10-28 21:02:23 configure python-wadllib 1.1.2-0ubuntu1 1.1.2-0ubuntu1
2009-10-28 21:02:23 status unpacked python-wadllib 1.1.2-0ubuntu1
2009-10-28 21:02:23 status half-configured python-wadllib 1.1.2-0ubuntu1
2009-10-28 21:02:24 status installed python-wadllib 1.1.2-0ubuntu1
2009-10-28 21:02:24 configure python-httplib2 0.4.0-0ubuntu2 0.4.0-0ubuntu2
2009-10-28 21:02:24 status unpacked python-httplib2 0.4.0-0ubuntu2
2009-10-28 21:02:24 status half-configured python-httplib2 0.4.0-0ubuntu2
2009-10-28 21:02:24 status installed python-httplib2 0.4.0-0ubuntu2
2009-10-28 21:02:24 configure python-pkg-resources 0.6c9-0ubuntu5 0.6c9-0ubuntu5
2009-10-28 21:02:24 status unpacked python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 21:02:24 status half-configured python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 21:02:24 status installed python-pkg-resources 0.6c9-0ubuntu5
2009-10-28 21:02:24 configure python-zope.interface 3.5.2-1 3.5.2-1
2009-10-28 21:02:24 status unpacked python-zope.interface 3.5.2-1
2009-10-28 21:02:24 status half-configured python-zope.interface 3.5.2-1
2009-10-28 21:02:24 status installed python-zope.interface 3.5.2-1
2009-10-28 21:02:24 configure python-lazr-restfulclient 0.9.3-0ubuntu3 0.9.3-0ubuntu3
2009-10-28 21:02:24 status unpacked python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 21:02:24 status half-configured python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 21:02:24 status installed python-lazr-restfulclient 0.9.3-0ubuntu3
2009-10-28 21:02:24 configure python-oauth 1.0a~svn1124-0ubuntu2 1.0a~svn1124-0ubuntu2
2009-10-28 21:02:24 status unpacked python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 21:02:24 status half-configured python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 21:02:25 status installed python-oauth 1.0a~svn1124-0ubuntu2
2009-10-28 21:02:25 configure python-launchpadlib 1.5.1-0ubuntu1 1.5.1-0ubuntu1
2009-10-28 21:02:25 status unpacked python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 21:02:25 status half-configured python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 21:02:25 status installed python-launchpadlib 1.5.1-0ubuntu1
2009-10-28 21:02:25 configure python-apport 1.9.3-0ubuntu4 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked python-apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked python-apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked python-apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status half-configured python-apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status installed python-apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 configure apport 1.9.3-0ubuntu4 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status unpacked apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status half-configured apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 status installed apport 1.9.3-0ubuntu4
2009-10-28 21:02:25 configure python-xdg 0.15-1.1ubuntu5 0.15-1.1ubuntu5
2009-10-28 21:02:25 status unpacked python-xdg 0.15-1.1ubuntu5
2009-10-28 21:02:25 status half-configured python-xdg 0.15-1.1ubuntu5
2009-10-28 21:02:26 status installed python-xdg 0.15-1.1ubuntu5
2009-10-28 21:02:26 configure apport-gtk 1.9.3-0ubuntu4 1.9.3-0ubuntu4
2009-10-28 21:02:26 status unpacked apport-gtk 1.9.3-0ubuntu4
2009-10-28 21:02:26 status half-configured apport-gtk 1.9.3-0ubuntu4
2009-10-28 21:02:26 status installed apport-gtk 1.9.3-0ubuntu4
2009-10-28 21:02:26 configure apport-symptoms 0.2 0.2
2009-10-28 21:02:26 status unpacked apport-symptoms 0.2
2009-10-28 21:02:26 status half-configured apport-symptoms 0.2
2009-10-28 21:02:26 status installed apport-symptoms 0.2
2009-10-28 21:02:26 configure python-xapian 1.0.14-1build1 1.0.14-1build1
2009-10-28 21:02:26 status unpacked python-xapian 1.0.14-1build1
2009-10-28 21:02:26 status half-configured python-xapian 1.0.14-1build1
2009-10-28 21:02:26 status installed python-xapian 1.0.14-1build1
2009-10-28 21:02:26 configure python-debian 0.1.14ubuntu1 0.1.14ubuntu1
2009-10-28 21:02:26 status unpacked python-debian 0.1.14ubuntu1
2009-10-28 21:02:26 status half-configured python-debian 0.1.14ubuntu1
2009-10-28 21:02:26 status installed python-debian 0.1.14ubuntu1
2009-10-28 21:02:26 configure apt-xapian-index 0.21ubuntu2 0.21ubuntu2
2009-10-28 21:02:26 status unpacked apt-xapian-index 0.21ubuntu2
2009-10-28 21:02:26 status unpacked apt-xapian-index 0.21ubuntu2
2009-10-28 21:02:26 status half-configured apt-xapian-index 0.21ubuntu2
2009-10-28 21:02:26 status installed apt-xapian-index 0.21ubuntu2
2009-10-28 21:02:26 configure apturl-common 0.4.1ubuntu2 0.4.1ubuntu2
2009-10-28 21:02:26 status unpacked apturl-common 0.4.1ubuntu2
2009-10-28 21:02:26 status unpacked apturl-common 0.4.1ubuntu2
2009-10-28 21:02:26 status half-configured apturl-common 0.4.1ubuntu2
2009-10-28 21:02:26 status installed apturl-common 0.4.1ubuntu2
2009-10-28 21:02:26 configure libgksu2-0 2.0.12-1ubuntu4 2.0.12-1ubuntu4
2009-10-28 21:02:26 status unpacked libgksu2-0 2.0.12-1ubuntu4
2009-10-28 21:02:26 status half-configured libgksu2-0 2.0.12-1ubuntu4
2009-10-28 21:02:26 update-alternatives: run with --install /usr/share/gconf/defaults/10_libgksu libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo 30
2009-10-28 21:02:26 update-alternatives: link group libgksu-gconf-defaults updated to point to /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo
2009-10-28 21:02:27 update-alternatives: run with --install /usr/share/gconf/defaults/10_libgksu libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-su 20
2009-10-28 21:02:27 status installed libgksu2-0 2.0.12-1ubuntu4
2009-10-28 21:02:27 configure libgp11-0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:27 status unpacked libgp11-0 2.28.1-0ubuntu1
2009-10-28 21:02:27 status half-configured libgp11-0 2.28.1-0ubuntu1
2009-10-28 21:02:27 status installed libgp11-0 2.28.1-0ubuntu1
2009-10-28 21:02:27 configure libgcr0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:27 status unpacked libgcr0 2.28.1-0ubuntu1
2009-10-28 21:02:27 status half-configured libgcr0 2.28.1-0ubuntu1
2009-10-28 21:02:27 status installed libgcr0 2.28.1-0ubuntu1
2009-10-28 21:02:27 configure gnome-keyring 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:27 status unpacked gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:02:27 status unpacked gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:02:27 status half-configured gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:02:27 status installed gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:02:27 configure gksu 2.0.2-2ubuntu1 2.0.2-2ubuntu1
2009-10-28 21:02:27 status unpacked gksu 2.0.2-2ubuntu1
2009-10-28 21:02:27 status half-configured gksu 2.0.2-2ubuntu1
2009-10-28 21:02:27 status installed gksu 2.0.2-2ubuntu1
2009-10-28 21:02:27 configure python-glade2 2.16.0-0ubuntu1 2.16.0-0ubuntu1
2009-10-28 21:02:27 status unpacked python-glade2 2.16.0-0ubuntu1
2009-10-28 21:02:27 status half-configured python-glade2 2.16.0-0ubuntu1
2009-10-28 21:02:27 status installed python-glade2 2.16.0-0ubuntu1
2009-10-28 21:02:27 configure libvte-common 1:0.22.2-0ubuntu2 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status unpacked libvte-common 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status half-configured libvte-common 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status installed libvte-common 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 configure libvte9 1:0.22.2-0ubuntu2 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status unpacked libvte9 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status half-configured libvte9 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status installed libvte9 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 configure python-vte 1:0.22.2-0ubuntu2 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status unpacked python-vte 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status half-configured python-vte 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 status installed python-vte 1:0.22.2-0ubuntu2
2009-10-28 21:02:27 configure synaptic 0.62.7ubuntu6 0.62.7ubuntu6
2009-10-28 21:02:27 status unpacked synaptic 0.62.7ubuntu6
2009-10-28 21:02:27 status half-configured synaptic 0.62.7ubuntu6
2009-10-28 21:02:28 status installed synaptic 0.62.7ubuntu6
2009-10-28 21:02:28 configure unattended-upgrades 0.52ubuntu1 0.52ubuntu1
2009-10-28 21:02:28 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status unpacked unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status half-configured unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 status installed unattended-upgrades 0.52ubuntu1
2009-10-28 21:02:28 configure python-software-properties 0.75.4 0.75.4
2009-10-28 21:02:28 status unpacked python-software-properties 0.75.4
2009-10-28 21:02:28 status half-configured python-software-properties 0.75.4
2009-10-28 21:02:28 status installed python-software-properties 0.75.4
2009-10-28 21:02:28 configure software-properties-gtk 0.75.4 0.75.4
2009-10-28 21:02:28 status unpacked software-properties-gtk 0.75.4
2009-10-28 21:02:28 status half-configured software-properties-gtk 0.75.4
2009-10-28 21:02:28 status installed software-properties-gtk 0.75.4
2009-10-28 21:02:28 configure apturl 0.4.1ubuntu2 0.4.1ubuntu2
2009-10-28 21:02:28 status unpacked apturl 0.4.1ubuntu2
2009-10-28 21:02:28 status half-configured apturl 0.4.1ubuntu2
2009-10-28 21:02:29 status installed apturl 0.4.1ubuntu2
2009-10-28 21:02:29 configure libaspell15 0.60.6-2 0.60.6-2
2009-10-28 21:02:29 status unpacked libaspell15 0.60.6-2
2009-10-28 21:02:29 status half-configured libaspell15 0.60.6-2
2009-10-28 21:02:29 status installed libaspell15 0.60.6-2
2009-10-28 21:02:29 configure dictionaries-common 1.2.1ubuntu1 1.2.1ubuntu1
2009-10-28 21:02:29 status unpacked dictionaries-common 1.2.1ubuntu1
2009-10-28 21:02:29 status unpacked dictionaries-common 1.2.1ubuntu1
2009-10-28 21:02:29 status half-configured dictionaries-common 1.2.1ubuntu1
2009-10-28 21:02:31 status installed dictionaries-common 1.2.1ubuntu1
2009-10-28 21:02:31 configure aspell 0.60.6-2 0.60.6-2
2009-10-28 21:02:31 status unpacked aspell 0.60.6-2
2009-10-28 21:02:31 status half-configured aspell 0.60.6-2
2009-10-28 21:02:31 status installed aspell 0.60.6-2
2009-10-28 21:02:31 configure aspell-en 6.0-0-5.1ubuntu3 6.0-0-5.1ubuntu3
2009-10-28 21:02:31 status unpacked aspell-en 6.0-0-5.1ubuntu3
2009-10-28 21:02:31 status half-configured aspell-en 6.0-0-5.1ubuntu3
2009-10-28 21:02:31 status installed aspell-en 6.0-0-5.1ubuntu3
2009-10-28 21:02:31 configure libatspi1.0-0 1.28.1-0ubuntu1 1.28.1-0ubuntu1
2009-10-28 21:02:31 status unpacked libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 21:02:31 status half-configured libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 21:02:31 status installed libatspi1.0-0 1.28.1-0ubuntu1
2009-10-28 21:02:31 configure at-spi 1.28.1-0ubuntu1 1.28.1-0ubuntu1
2009-10-28 21:02:31 status unpacked at-spi 1.28.1-0ubuntu1
2009-10-28 21:02:31 status unpacked at-spi 1.28.1-0ubuntu1
2009-10-28 21:02:31 status half-configured at-spi 1.28.1-0ubuntu1
2009-10-28 21:02:32 status installed at-spi 1.28.1-0ubuntu1
2009-10-28 21:02:32 configure libdaemon0 0.13-3 0.13-3
2009-10-28 21:02:32 status unpacked libdaemon0 0.13-3
2009-10-28 21:02:32 status half-configured libdaemon0 0.13-3
2009-10-28 21:02:32 status installed libdaemon0 0.13-3
2009-10-28 21:02:32 configure avahi-autoipd 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status half-configured avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 status installed avahi-autoipd 0.6.25-1ubuntu5
2009-10-28 21:02:32 configure libavahi-core6 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked libavahi-core6 0.6.25-1ubuntu5
2009-10-28 21:02:32 status half-configured libavahi-core6 0.6.25-1ubuntu5
2009-10-28 21:02:32 status installed libavahi-core6 0.6.25-1ubuntu5
2009-10-28 21:02:32 configure avahi-daemon 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status unpacked avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status half-configured avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 status installed avahi-daemon 0.6.25-1ubuntu5
2009-10-28 21:02:32 configure bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4 5.10.91.9+bdcom-0ubuntu4
2009-10-28 21:02:32 status unpacked bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 21:02:32 status half-configured bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 21:02:32 status installed bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4
2009-10-28 21:02:32 configure binfmt-support 1.2.14 1.2.14
2009-10-28 21:02:32 status unpacked binfmt-support 1.2.14
2009-10-28 21:02:32 status unpacked binfmt-support 1.2.14
2009-10-28 21:02:32 status half-configured binfmt-support 1.2.14
2009-10-28 21:02:33 status installed binfmt-support 1.2.14
2009-10-28 21:02:33 configure binutils 2.20-0ubuntu1 2.20-0ubuntu1
2009-10-28 21:02:33 status unpacked binutils 2.20-0ubuntu1
2009-10-28 21:02:33 status half-configured binutils 2.20-0ubuntu1
2009-10-28 21:02:33 status installed binutils 2.20-0ubuntu1
2009-10-28 21:02:33 configure libbluetooth3 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked libbluetooth3 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured libbluetooth3 4.51-0ubuntu2
2009-10-28 21:02:33 status installed libbluetooth3 4.51-0ubuntu2
2009-10-28 21:02:33 configure libnl1 1.1-5 1.1-5
2009-10-28 21:02:33 status unpacked libnl1 1.1-5
2009-10-28 21:02:33 status half-configured libnl1 1.1-5
2009-10-28 21:02:33 status installed libnl1 1.1-5
2009-10-28 21:02:33 configure bluez 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluez 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluez 4.51-0ubuntu2
2009-10-28 21:02:33 configure bluetooth 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluetooth 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluetooth 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluetooth 4.51-0ubuntu2
2009-10-28 21:02:33 configure bluez-alsa 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez-alsa 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluez-alsa 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluez-alsa 4.51-0ubuntu2
2009-10-28 21:02:33 configure bluez-cups 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez-cups 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluez-cups 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluez-cups 4.51-0ubuntu2
2009-10-28 21:02:33 configure bluez-gstreamer 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez-gstreamer 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluez-gstreamer 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluez-gstreamer 4.51-0ubuntu2
2009-10-28 21:02:33 configure bluez-utils 4.51-0ubuntu2 4.51-0ubuntu2
2009-10-28 21:02:33 status unpacked bluez-utils 4.51-0ubuntu2
2009-10-28 21:02:33 status half-configured bluez-utils 4.51-0ubuntu2
2009-10-28 21:02:33 status installed bluez-utils 4.51-0ubuntu2
2009-10-28 21:02:33 configure libgsl0ldbl 1.12+dfsg-1 1.12+dfsg-1
2009-10-28 21:02:33 status unpacked libgsl0ldbl 1.12+dfsg-1
2009-10-28 21:02:33 status half-configured libgsl0ldbl 1.12+dfsg-1
2009-10-28 21:02:33 status installed libgsl0ldbl 1.12+dfsg-1
2009-10-28 21:02:33 configure bogofilter-common 1.2.0-3ubuntu1 1.2.0-3ubuntu1
2009-10-28 21:02:33 status unpacked bogofilter-common 1.2.0-3ubuntu1
2009-10-28 21:02:33 status unpacked bogofilter-common 1.2.0-3ubuntu1
2009-10-28 21:02:33 status half-configured bogofilter-common 1.2.0-3ubuntu1
2009-10-28 21:02:33 status installed bogofilter-common 1.2.0-3ubuntu1
2009-10-28 21:02:33 configure bogofilter-bdb 1.2.0-3ubuntu1 1.2.0-3ubuntu1
2009-10-28 21:02:33 status unpacked bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 21:02:33 status half-configured bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 21:02:33 update-alternatives: run with --quiet --install /usr/bin/bogofilter bogofilter /usr/bin/bogofilter-bdb 20 --slave /usr/bin/bogoupgrade bogoupgrade /usr/bin/bogoupgrade-bdb --slave /usr/bin/bogotune bogotune /usr/bin/bogotune-bdb --slave /usr/bin/bf_copy bf_copy /usr/bin/bf_copy-bdb --slave /usr/bin/bogolexer bogolexer /usr/bin/bogolexer-bdb --slave /usr/bin/bogoutil bogoutil /usr/bin/bogoutil-bdb --slave /usr/bin/bf_compact bf_compact /usr/bin/bf_compact-bdb --slave /usr/bin/bf_tar bf_tar /usr/bin/bf_tar-bdb
2009-10-28 21:02:33 update-alternatives: link group bogofilter updated to point to /usr/bin/bogofilter-bdb
2009-10-28 21:02:33 status installed bogofilter-bdb 1.2.0-3ubuntu1
2009-10-28 21:02:33 configure bogofilter 1.2.0-3ubuntu1 1.2.0-3ubuntu1
2009-10-28 21:02:33 status unpacked bogofilter 1.2.0-3ubuntu1
2009-10-28 21:02:33 status half-configured bogofilter 1.2.0-3ubuntu1
2009-10-28 21:02:33 status installed bogofilter 1.2.0-3ubuntu1
2009-10-28 21:02:33 configure libbeagle1 0.3.9-1 0.3.9-1
2009-10-28 21:02:33 status unpacked libbeagle1 0.3.9-1
2009-10-28 21:02:33 status half-configured libbeagle1 0.3.9-1
2009-10-28 21:02:33 status installed libbeagle1 0.3.9-1
2009-10-28 21:02:33 configure libnautilus-extension1 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:02:33 status unpacked libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 21:02:33 status half-configured libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 21:02:33 status installed libnautilus-extension1 1:2.28.1-0ubuntu1
2009-10-28 21:02:33 configure libgmime-2.4-2 2.4.6-5 2.4.6-5
2009-10-28 21:02:33 status unpacked libgmime-2.4-2 2.4.6-5
2009-10-28 21:02:33 status half-configured libgmime-2.4-2 2.4.6-5
2009-10-28 21:02:33 status installed libgmime-2.4-2 2.4.6-5
2009-10-28 21:02:33 configure libtotem-plparser12 2.28.1-1 2.28.1-1
2009-10-28 21:02:33 status unpacked libtotem-plparser12 2.28.1-1
2009-10-28 21:02:33 status half-configured libtotem-plparser12 2.28.1-1
2009-10-28 21:02:33 status installed libtotem-plparser12 2.28.1-1
2009-10-28 21:02:33 configure libbrasero-media0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:33 status unpacked libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 21:02:33 status half-configured libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 21:02:33 status installed libbrasero-media0 2.28.1-0ubuntu1
2009-10-28 21:02:33 configure wodim 9:1.1.9-1ubuntu2 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status unpacked wodim 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status unpacked wodim 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status unpacked wodim 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status half-configured wodim 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status installed wodim 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 configure genisoimage 9:1.1.9-1ubuntu2 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status unpacked genisoimage 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status half-configured genisoimage 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 status installed genisoimage 9:1.1.9-1ubuntu2
2009-10-28 21:02:33 configure dvd+rw-tools 7.1-4 7.1-4
2009-10-28 21:02:33 status unpacked dvd+rw-tools 7.1-4
2009-10-28 21:02:33 status half-configured dvd+rw-tools 7.1-4
2009-10-28 21:02:33 status installed dvd+rw-tools 7.1-4
2009-10-28 21:02:33 configure libcdparanoia0 3.10.2+debian-5 3.10.2+debian-5
2009-10-28 21:02:33 status unpacked libcdparanoia0 3.10.2+debian-5
2009-10-28 21:02:33 status half-configured libcdparanoia0 3.10.2+debian-5
2009-10-28 21:02:33 status installed libcdparanoia0 3.10.2+debian-5
2009-10-28 21:02:33 configure liboil0.3 0.3.16-1ubuntu1 0.3.16-1ubuntu1
2009-10-28 21:02:33 status unpacked liboil0.3 0.3.16-1ubuntu1
2009-10-28 21:02:33 status half-configured liboil0.3 0.3.16-1ubuntu1
2009-10-28 21:02:33 status installed liboil0.3 0.3.16-1ubuntu1
2009-10-28 21:02:33 configure libtheora0 1.0-2.1build1 1.0-2.1build1
2009-10-28 21:02:33 status unpacked libtheora0 1.0-2.1build1
2009-10-28 21:02:33 status half-configured libtheora0 1.0-2.1build1
2009-10-28 21:02:33 status installed libtheora0 1.0-2.1build1
2009-10-28 21:02:33 configure libvisual-0.4-0 0.4.0-2.1+ubuntu1 0.4.0-2.1+ubuntu1
2009-10-28 21:02:33 status unpacked libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 21:02:33 status half-configured libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 21:02:34 status installed libvisual-0.4-0 0.4.0-2.1+ubuntu1
2009-10-28 21:02:34 configure gstreamer0.10-plugins-base 0.10.25-2ubuntu1 0.10.25-2ubuntu1
2009-10-28 21:02:34 status unpacked gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 21:02:34 status half-configured gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 21:02:34 status installed gstreamer0.10-plugins-base 0.10.25-2ubuntu1
2009-10-28 21:02:34 configure brasero 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:34 status unpacked brasero 2.28.1-0ubuntu1
2009-10-28 21:02:34 status half-configured brasero 2.28.1-0ubuntu1
2009-10-28 21:02:34 status installed brasero 2.28.1-0ubuntu1
2009-10-28 21:02:34 configure screen 4.0.3-13ubuntu4 4.0.3-13ubuntu4
2009-10-28 21:02:34 status unpacked screen 4.0.3-13ubuntu4
2009-10-28 21:02:34 status unpacked screen 4.0.3-13ubuntu4
2009-10-28 21:02:34 status unpacked screen 4.0.3-13ubuntu4
2009-10-28 21:02:34 status half-configured screen 4.0.3-13ubuntu4
2009-10-28 21:02:34 status installed screen 4.0.3-13ubuntu4
2009-10-28 21:02:34 configure python-newt 0.52.10-4ubuntu1 0.52.10-4ubuntu1
2009-10-28 21:02:34 status unpacked python-newt 0.52.10-4ubuntu1
2009-10-28 21:02:34 status half-configured python-newt 0.52.10-4ubuntu1
2009-10-28 21:02:34 status installed python-newt 0.52.10-4ubuntu1
2009-10-28 21:02:34 configure byobu 2.38-0ubuntu3 2.38-0ubuntu3
2009-10-28 21:02:34 status unpacked byobu 2.38-0ubuntu3
2009-10-28 21:02:34 status unpacked byobu 2.38-0ubuntu3
2009-10-28 21:02:34 status half-configured byobu 2.38-0ubuntu3
2009-10-28 21:02:34 status installed byobu 2.38-0ubuntu3
2009-10-28 21:02:34 configure cdparanoia 3.10.2+debian-5 3.10.2+debian-5
2009-10-28 21:02:34 status unpacked cdparanoia 3.10.2+debian-5
2009-10-28 21:02:34 status half-configured cdparanoia 3.10.2+debian-5
2009-10-28 21:02:34 status installed cdparanoia 3.10.2+debian-5
2009-10-28 21:02:34 configure checkbox 0.8.5 0.8.5
2009-10-28 21:02:34 status unpacked checkbox 0.8.5
2009-10-28 21:02:34 status unpacked checkbox 0.8.5
2009-10-28 21:02:34 status unpacked checkbox 0.8.5
2009-10-28 21:02:34 status unpacked checkbox 0.8.5
2009-10-28 21:02:34 status half-configured checkbox 0.8.5
2009-10-28 21:02:35 status installed checkbox 0.8.5
2009-10-28 21:02:35 configure checkbox-gtk 0.8.5 0.8.5
2009-10-28 21:02:35 status unpacked checkbox-gtk 0.8.5
2009-10-28 21:02:35 status half-configured checkbox-gtk 0.8.5
2009-10-28 21:02:36 status installed checkbox-gtk 0.8.5
2009-10-28 21:02:36 configure cli-common 0.7 0.7
2009-10-28 21:02:36 status unpacked cli-common 0.7
2009-10-28 21:02:36 status half-configured cli-common 0.7
2009-10-28 21:02:36 status installed cli-common 0.7
2009-10-28 21:02:36 configure mesa-utils 7.6.0-1ubuntu4 7.6.0-1ubuntu4
2009-10-28 21:02:36 status unpacked mesa-utils 7.6.0-1ubuntu4
2009-10-28 21:02:36 status half-configured mesa-utils 7.6.0-1ubuntu4
2009-10-28 21:02:36 status installed mesa-utils 7.6.0-1ubuntu4
2009-10-28 21:02:36 configure compiz-wrapper 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status half-configured compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status installed compiz-wrapper 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 configure compiz-core 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked compiz-core 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked compiz-core 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status half-configured compiz-core 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status installed compiz-core 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 configure libdecoration0 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status half-configured libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status installed libdecoration0 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 configure libglu1-mesa 7.6.0-1ubuntu4 7.6.0-1ubuntu4
2009-10-28 21:02:36 status unpacked libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 21:02:36 status half-configured libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 21:02:36 status installed libglu1-mesa 7.6.0-1ubuntu4
2009-10-28 21:02:36 configure compiz-plugins 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status half-configured compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status installed compiz-plugins 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 configure libprotobuf3 2.0.3-2.2ubuntu2 2.0.3-2.2ubuntu2
2009-10-28 21:02:36 status unpacked libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 21:02:36 status half-configured libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 21:02:36 status installed libprotobuf3 2.0.3-2.2ubuntu2
2009-10-28 21:02:36 configure libcompizconfig0 0.8.4-0ubuntu1 0.8.4-0ubuntu1
2009-10-28 21:02:36 status unpacked libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 21:02:36 status unpacked libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 21:02:36 status half-configured libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 21:02:36 status installed libcompizconfig0 0.8.4-0ubuntu1
2009-10-28 21:02:36 configure compizconfig-backend-gconf 0.8.4-0ubuntu1 0.8.4-0ubuntu1
2009-10-28 21:02:36 status unpacked compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 21:02:36 status half-configured compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 21:02:36 status installed compizconfig-backend-gconf 0.8.4-0ubuntu1
2009-10-28 21:02:36 configure compiz-gnome 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status unpacked compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 21:02:36 status half-configured compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 status installed compiz-gnome 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 configure compiz-fusion-plugins-main 0.8.4-0ubuntu1 0.8.4-0ubuntu1
2009-10-28 21:02:38 status unpacked compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 21:02:38 status half-configured compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 21:02:38 status installed compiz-fusion-plugins-main 0.8.4-0ubuntu1
2009-10-28 21:02:38 configure compiz-fusion-plugins-extra 0.8.4-0ubuntu2 0.8.4-0ubuntu2
2009-10-28 21:02:38 status unpacked compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 21:02:38 status half-configured compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 21:02:38 status installed compiz-fusion-plugins-extra 0.8.4-0ubuntu2
2009-10-28 21:02:38 configure compiz 1:0.8.4-0ubuntu2 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 status unpacked compiz 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 status half-configured compiz 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 status installed compiz 1:0.8.4-0ubuntu2
2009-10-28 21:02:38 configure python-fstab 1.4-0ubuntu1 1.4-0ubuntu1
2009-10-28 21:02:38 status unpacked python-fstab 1.4-0ubuntu1
2009-10-28 21:02:38 status half-configured python-fstab 1.4-0ubuntu1
2009-10-28 21:02:39 status installed python-fstab 1.4-0ubuntu1
2009-10-28 21:02:39 configure computer-janitor 1.13.3-0ubuntu2 1.13.3-0ubuntu2
2009-10-28 21:02:39 status unpacked computer-janitor 1.13.3-0ubuntu2
2009-10-28 21:02:39 status unpacked computer-janitor 1.13.3-0ubuntu2
2009-10-28 21:02:39 status half-configured computer-janitor 1.13.3-0ubuntu2
2009-10-28 21:02:39 status installed computer-janitor 1.13.3-0ubuntu2
2009-10-28 21:02:39 configure computer-janitor-gtk 1.13.3-0ubuntu2 1.13.3-0ubuntu2
2009-10-28 21:02:39 status unpacked computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 21:02:39 status half-configured computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 21:02:39 status installed computer-janitor-gtk 1.13.3-0ubuntu2
2009-10-28 21:02:39 configure libcurl3 7.19.5-1ubuntu2 7.19.5-1ubuntu2
2009-10-28 21:02:39 status unpacked libcurl3 7.19.5-1ubuntu2
2009-10-28 21:02:39 status half-configured libcurl3 7.19.5-1ubuntu2
2009-10-28 21:02:39 status installed libcurl3 7.19.5-1ubuntu2
2009-10-28 21:02:39 configure erlang-base 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-base 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-crypto 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-crypto 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-mnesia 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-mnesia 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-public-key 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-public-key 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-ssl 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-ssl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-inets 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-inets 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure erlang-xmerl 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status unpacked erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status half-configured erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 status installed erlang-xmerl 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:39 configure couchdb-bin 0.10.0-0ubuntu3 0.10.0-0ubuntu3
2009-10-28 21:02:39 status unpacked couchdb-bin 0.10.0-0ubuntu3
2009-10-28 21:02:39 status unpacked couchdb-bin 0.10.0-0ubuntu3
2009-10-28 21:02:39 status unpacked couchdb-bin 0.10.0-0ubuntu3
2009-10-28 21:02:39 status half-configured couchdb-bin 0.10.0-0ubuntu3
2009-10-28 21:02:40 status installed couchdb-bin 0.10.0-0ubuntu3
2009-10-28 21:02:40 configure libgutenprint2 5.2.4-0ubuntu2 5.2.4-0ubuntu2
2009-10-28 21:02:40 status unpacked libgutenprint2 5.2.4-0ubuntu2
2009-10-28 21:02:40 status half-configured libgutenprint2 5.2.4-0ubuntu2
2009-10-28 21:02:40 status installed libgutenprint2 5.2.4-0ubuntu2
2009-10-28 21:02:40 configure ghostscript-cups 8.70.dfsg.1-0ubuntu3 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:40 status unpacked ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:40 status half-configured ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:40 status installed ghostscript-cups 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:40 configure cups-driver-gutenprint 5.2.4-0ubuntu2 5.2.4-0ubuntu2
2009-10-28 21:02:40 status unpacked cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 21:02:40 status half-configured cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 21:02:40 status installed cups-driver-gutenprint 5.2.4-0ubuntu2
2009-10-28 21:02:40 configure dc 1.06.94-3.1ubuntu2 1.06.94-3.1ubuntu2
2009-10-28 21:02:40 status unpacked dc 1.06.94-3.1ubuntu2
2009-10-28 21:02:40 status half-configured dc 1.06.94-3.1ubuntu2
2009-10-28 21:02:40 status installed dc 1.06.94-3.1ubuntu2
2009-10-28 21:02:40 configure python-couchdb 0.6-1 0.6-1
2009-10-28 21:02:40 status unpacked python-couchdb 0.6-1
2009-10-28 21:02:40 status half-configured python-couchdb 0.6-1
2009-10-28 21:02:40 status installed python-couchdb 0.6-1
2009-10-28 21:02:40 configure python-twisted-bin 8.2.0-3 8.2.0-3
2009-10-28 21:02:40 status unpacked python-twisted-bin 8.2.0-3
2009-10-28 21:02:40 status half-configured python-twisted-bin 8.2.0-3
2009-10-28 21:02:40 status installed python-twisted-bin 8.2.0-3
2009-10-28 21:02:40 configure python-twisted-core 8.2.0-3 8.2.0-3
2009-10-28 21:02:40 status unpacked python-twisted-core 8.2.0-3
2009-10-28 21:02:40 status half-configured python-twisted-core 8.2.0-3
2009-10-28 21:02:42 status installed python-twisted-core 8.2.0-3
2009-10-28 21:02:42 configure python-avahi 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:02:42 status unpacked python-avahi 0.6.25-1ubuntu5
2009-10-28 21:02:42 status half-configured python-avahi 0.6.25-1ubuntu5
2009-10-28 21:02:42 status installed python-avahi 0.6.25-1ubuntu5
2009-10-28 21:02:42 configure python-gnomekeyring 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:02:42 status unpacked python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 21:02:42 status half-configured python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 21:02:42 status installed python-gnomekeyring 2.28.0-0ubuntu1
2009-10-28 21:02:42 configure libdevkit-power-gobject1 011-1ubuntu1 011-1ubuntu1
2009-10-28 21:02:42 status unpacked libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 21:02:42 status half-configured libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 21:02:42 status installed libdevkit-power-gobject1 011-1ubuntu1
2009-10-28 21:02:42 configure devicekit-power 011-1ubuntu1 011-1ubuntu1
2009-10-28 21:02:42 status unpacked devicekit-power 011-1ubuntu1
2009-10-28 21:02:42 status unpacked devicekit-power 011-1ubuntu1
2009-10-28 21:02:42 status half-configured devicekit-power 011-1ubuntu1
2009-10-28 21:02:42 status installed devicekit-power 011-1ubuntu1
2009-10-28 21:02:42 configure dmz-cursor-theme 0.4.1 0.4.1
2009-10-28 21:02:42 status unpacked dmz-cursor-theme 0.4.1
2009-10-28 21:02:42 status half-configured dmz-cursor-theme 0.4.1
2009-10-28 21:02:43 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/DMZ-White/cursor.theme 50
2009-10-28 21:02:43 update-alternatives: link group x-cursor-theme updated to point to /usr/share/icons/DMZ-White/cursor.theme
2009-10-28 21:02:43 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/DMZ-Black/cursor.theme 30
2009-10-28 21:02:43 status installed dmz-cursor-theme 0.4.1
2009-10-28 21:02:43 configure dnsmasq-base 2.50-1 2.50-1
2009-10-28 21:02:43 status unpacked dnsmasq-base 2.50-1
2009-10-28 21:02:43 status half-configured dnsmasq-base 2.50-1
2009-10-28 21:02:43 status installed dnsmasq-base 2.50-1
2009-10-28 21:02:43 configure libuuid-perl 0.02-3build1 0.02-3build1
2009-10-28 21:02:43 status unpacked libuuid-perl 0.02-3build1
2009-10-28 21:02:43 status half-configured libuuid-perl 0.02-3build1
2009-10-28 21:02:43 status installed libuuid-perl 0.02-3build1
2009-10-28 21:02:43 configure libmldbm-perl 2.01-2 2.01-2
2009-10-28 21:02:43 status unpacked libmldbm-perl 2.01-2
2009-10-28 21:02:43 status half-configured libmldbm-perl 2.01-2
2009-10-28 21:02:43 status installed libmldbm-perl 2.01-2
2009-10-28 21:02:43 configure doc-base 0.9.3 0.9.3
2009-10-28 21:02:43 status unpacked doc-base 0.9.3
2009-10-28 21:02:43 status unpacked doc-base 0.9.3
2009-10-28 21:02:43 status half-configured doc-base 0.9.3
2009-10-28 21:02:43 status installed doc-base 0.9.3
2009-10-28 21:02:43 configure libgssdp-1.0-1 0.6.4-2 0.6.4-2
2009-10-28 21:02:43 status unpacked libgssdp-1.0-1 0.6.4-2
2009-10-28 21:02:43 status half-configured libgssdp-1.0-1 0.6.4-2
2009-10-28 21:02:43 status installed libgssdp-1.0-1 0.6.4-2
2009-10-28 21:02:43 configure libgupnp-1.0-2 0.12.6-3.1 0.12.6-3.1
2009-10-28 21:02:43 status unpacked libgupnp-1.0-2 0.12.6-3.1
2009-10-28 21:02:43 status half-configured libgupnp-1.0-2 0.12.6-3.1
2009-10-28 21:02:43 status installed libgupnp-1.0-2 0.12.6-3.1
2009-10-28 21:02:43 configure libgupnp-igd-1.0-2 0.1.3-0ubuntu3 0.1.3-0ubuntu3
2009-10-28 21:02:43 status unpacked libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 21:02:43 status half-configured libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 21:02:43 status installed libgupnp-igd-1.0-2 0.1.3-0ubuntu3
2009-10-28 21:02:43 configure libnice0 0.0.9-2 0.0.9-2
2009-10-28 21:02:43 status unpacked libnice0 0.0.9-2
2009-10-28 21:02:43 status half-configured libnice0 0.0.9-2
2009-10-28 21:02:43 status installed libnice0 0.0.9-2
2009-10-28 21:02:43 configure libaa1 1.4p5-38 1.4p5-38
2009-10-28 21:02:43 status unpacked libaa1 1.4p5-38
2009-10-28 21:02:43 status half-configured libaa1 1.4p5-38
2009-10-28 21:02:43 status installed libaa1 1.4p5-38
2009-10-28 21:02:43 configure libraw1394-11 2.0.4-1ubuntu1 2.0.4-1ubuntu1
2009-10-28 21:02:43 status unpacked libraw1394-11 2.0.4-1ubuntu1
2009-10-28 21:02:43 status half-configured libraw1394-11 2.0.4-1ubuntu1
2009-10-28 21:02:43 status installed libraw1394-11 2.0.4-1ubuntu1
2009-10-28 21:02:43 configure libavc1394-0 0.5.3-1build3 0.5.3-1build3
2009-10-28 21:02:43 status unpacked libavc1394-0 0.5.3-1build3
2009-10-28 21:02:43 status half-configured libavc1394-0 0.5.3-1build3
2009-10-28 21:02:43 status installed libavc1394-0 0.5.3-1build3
2009-10-28 21:02:43 configure libcaca0 0.99.beta16-1 0.99.beta16-1
2009-10-28 21:02:43 status unpacked libcaca0 0.99.beta16-1
2009-10-28 21:02:43 status half-configured libcaca0 0.99.beta16-1
2009-10-28 21:02:43 status installed libcaca0 0.99.beta16-1
2009-10-28 21:02:43 configure libdv4 1.0.0-2ubuntu1 1.0.0-2ubuntu1
2009-10-28 21:02:43 status unpacked libdv4 1.0.0-2ubuntu1
2009-10-28 21:02:43 status half-configured libdv4 1.0.0-2ubuntu1
2009-10-28 21:02:43 status installed libdv4 1.0.0-2ubuntu1
2009-10-28 21:02:43 configure libiec61883-0 1.2.0-0.1 1.2.0-0.1
2009-10-28 21:02:43 status unpacked libiec61883-0 1.2.0-0.1
2009-10-28 21:02:43 status half-configured libiec61883-0 1.2.0-0.1
2009-10-28 21:02:43 status installed libiec61883-0 1.2.0-0.1
2009-10-28 21:02:43 configure libspeex1 1.2~rc1-1 1.2~rc1-1
2009-10-28 21:02:43 status unpacked libspeex1 1.2~rc1-1
2009-10-28 21:02:43 status half-configured libspeex1 1.2~rc1-1
2009-10-28 21:02:43 status installed libspeex1 1.2~rc1-1
2009-10-28 21:02:43 configure libshout3 2.2.2-5ubuntu1 2.2.2-5ubuntu1
2009-10-28 21:02:43 status unpacked libshout3 2.2.2-5ubuntu1
2009-10-28 21:02:43 status half-configured libshout3 2.2.2-5ubuntu1
2009-10-28 21:02:43 status installed libshout3 2.2.2-5ubuntu1
2009-10-28 21:02:43 configure libtag1-vanilla 1.6-2ubuntu2 1.6-2ubuntu2
2009-10-28 21:02:43 status unpacked libtag1-vanilla 1.6-2ubuntu2
2009-10-28 21:02:43 status half-configured libtag1-vanilla 1.6-2ubuntu2
2009-10-28 21:02:44 status installed libtag1-vanilla 1.6-2ubuntu2
2009-10-28 21:02:44 configure libtag1c2a 1.6-2ubuntu2 1.6-2ubuntu2
2009-10-28 21:02:44 status unpacked libtag1c2a 1.6-2ubuntu2
2009-10-28 21:02:44 status half-configured libtag1c2a 1.6-2ubuntu2
2009-10-28 21:02:44 status installed libtag1c2a 1.6-2ubuntu2
2009-10-28 21:02:44 configure libwavpack1 4.50.1-1 4.50.1-1
2009-10-28 21:02:44 status unpacked libwavpack1 4.50.1-1
2009-10-28 21:02:44 status half-configured libwavpack1 4.50.1-1
2009-10-28 21:02:44 status installed libwavpack1 4.50.1-1
2009-10-28 21:02:44 configure gstreamer0.10-plugins-good 0.10.16-1ubuntu3 0.10.16-1ubuntu3
2009-10-28 21:02:44 status unpacked gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 21:02:44 status half-configured gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 21:02:44 status installed gstreamer0.10-plugins-good 0.10.16-1ubuntu3
2009-10-28 21:02:44 configure gstreamer0.10-nice 0.0.9-2 0.0.9-2
2009-10-28 21:02:44 status unpacked gstreamer0.10-nice 0.0.9-2
2009-10-28 21:02:44 status half-configured gstreamer0.10-nice 0.0.9-2
2009-10-28 21:02:44 status installed gstreamer0.10-nice 0.0.9-2
2009-10-28 21:02:44 configure libgstfarsight0.10-0 0.0.15-1ubuntu1 0.0.15-1ubuntu1
2009-10-28 21:02:44 status unpacked libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 21:02:44 status half-configured libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 21:02:44 status installed libgstfarsight0.10-0 0.0.15-1ubuntu1
2009-10-28 21:02:44 configure libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status unpacked libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status half-configured libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status installed libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 configure libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status unpacked libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status half-configured libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 status installed libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:02:44 configure libtelepathy-glib0 0.9.0-1 0.9.0-1
2009-10-28 21:02:44 status unpacked libtelepathy-glib0 0.9.0-1
2009-10-28 21:02:44 status half-configured libtelepathy-glib0 0.9.0-1
2009-10-28 21:02:44 status installed libtelepathy-glib0 0.9.0-1
2009-10-28 21:02:44 configure libtelepathy-farsight0 0.0.11-2 0.0.11-2
2009-10-28 21:02:44 status unpacked libtelepathy-farsight0 0.0.11-2
2009-10-28 21:02:44 status half-configured libtelepathy-farsight0 0.0.11-2
2009-10-28 21:02:44 status installed libtelepathy-farsight0 0.0.11-2
2009-10-28 21:02:44 configure libempathy-common 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:44 status unpacked libempathy-common 2.28.1-1ubuntu1
2009-10-28 21:02:44 status half-configured libempathy-common 2.28.1-1ubuntu1
2009-10-28 21:02:44 status installed libempathy-common 2.28.1-1ubuntu1
2009-10-28 21:02:44 configure telepathy-mission-control-5 5.3.1-1 5.3.1-1
2009-10-28 21:02:44 status unpacked telepathy-mission-control-5 5.3.1-1
2009-10-28 21:02:44 status half-configured telepathy-mission-control-5 5.3.1-1
2009-10-28 21:02:44 status installed telepathy-mission-control-5 5.3.1-1
2009-10-28 21:02:44 configure libempathy30 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:44 status unpacked libempathy30 2.28.1-1ubuntu1
2009-10-28 21:02:44 status half-configured libempathy30 2.28.1-1ubuntu1
2009-10-28 21:02:44 status installed libempathy30 2.28.1-1ubuntu1
2009-10-28 21:02:44 configure libenchant1c2a 1.5.0-0ubuntu2 1.5.0-0ubuntu2
2009-10-28 21:02:44 status unpacked libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 21:02:44 status half-configured libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 21:02:44 status installed libenchant1c2a 1.5.0-0ubuntu2
2009-10-28 21:02:44 configure libwebkit-1.0-common 1.1.15.2-1 1.1.15.2-1
2009-10-28 21:02:44 status unpacked libwebkit-1.0-common 1.1.15.2-1
2009-10-28 21:02:44 status half-configured libwebkit-1.0-common 1.1.15.2-1
2009-10-28 21:02:44 status installed libwebkit-1.0-common 1.1.15.2-1
2009-10-28 21:02:44 configure libwebkit-1.0-2 1.1.15.2-1 1.1.15.2-1
2009-10-28 21:02:44 status unpacked libwebkit-1.0-2 1.1.15.2-1
2009-10-28 21:02:44 status half-configured libwebkit-1.0-2 1.1.15.2-1
2009-10-28 21:02:44 status installed libwebkit-1.0-2 1.1.15.2-1
2009-10-28 21:02:44 configure libempathy-gtk-common 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:44 status unpacked libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 21:02:44 status half-configured libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 21:02:45 status installed libempathy-gtk-common 2.28.1-1ubuntu1
2009-10-28 21:02:45 configure libempathy-gtk28 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:45 status unpacked libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 21:02:45 status half-configured libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 21:02:45 status installed libempathy-gtk28 2.28.1-1ubuntu1
2009-10-28 21:02:45 configure libindicate3 0.2.3-0ubuntu1 0.2.3-0ubuntu1
2009-10-28 21:02:45 status unpacked libindicate3 0.2.3-0ubuntu1
2009-10-28 21:02:45 status half-configured libindicate3 0.2.3-0ubuntu1
2009-10-28 21:02:45 status installed libindicate3 0.2.3-0ubuntu1
2009-10-28 21:02:45 configure libindicate-gtk1 0.2.3-0ubuntu1 0.2.3-0ubuntu1
2009-10-28 21:02:45 status unpacked libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 21:02:45 status half-configured libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 21:02:45 status installed libindicate-gtk1 0.2.3-0ubuntu1
2009-10-28 21:02:45 configure empathy-doc 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:45 status unpacked empathy-doc 2.28.1-1ubuntu1
2009-10-28 21:02:45 status half-configured empathy-doc 2.28.1-1ubuntu1
2009-10-28 21:02:45 status installed empathy-doc 2.28.1-1ubuntu1
2009-10-28 21:02:45 configure empathy 2.28.1-1ubuntu1 2.28.1-1ubuntu1
2009-10-28 21:02:45 status unpacked empathy 2.28.1-1ubuntu1
2009-10-28 21:02:45 status half-configured empathy 2.28.1-1ubuntu1
2009-10-28 21:02:45 status installed empathy 2.28.1-1ubuntu1
2009-10-28 21:02:45 configure libexempi3 2.1.1-1build1 2.1.1-1build1
2009-10-28 21:02:45 status unpacked libexempi3 2.1.1-1build1
2009-10-28 21:02:45 status half-configured libexempi3 2.1.1-1build1
2009-10-28 21:02:45 status installed libexempi3 2.1.1-1build1
2009-10-28 21:02:45 configure eog 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:45 status unpacked eog 2.28.1-0ubuntu1
2009-10-28 21:02:45 status half-configured eog 2.28.1-0ubuntu1
2009-10-28 21:02:45 status installed eog 2.28.1-0ubuntu1
2009-10-28 21:02:45 configure erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:45 status unpacked erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:45 status half-configured erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:45 status installed erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1
2009-10-28 21:02:45 configure esound-clients 0.2.41-5 0.2.41-5
2009-10-28 21:02:45 status unpacked esound-clients 0.2.41-5
2009-10-28 21:02:45 status half-configured esound-clients 0.2.41-5
2009-10-28 21:02:46 status installed esound-clients 0.2.41-5
2009-10-28 21:02:46 configure libportaudio2 19+svn20090620-0ubuntu1 19+svn20090620-0ubuntu1
2009-10-28 21:02:46 status unpacked libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 21:02:46 status half-configured libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 21:02:46 status installed libportaudio2 19+svn20090620-0ubuntu1
2009-10-28 21:02:46 configure espeak-data 1.41.01-0ubuntu1 1.41.01-0ubuntu1
2009-10-28 21:02:46 status unpacked espeak-data 1.41.01-0ubuntu1
2009-10-28 21:02:46 status half-configured espeak-data 1.41.01-0ubuntu1
2009-10-28 21:02:46 status installed espeak-data 1.41.01-0ubuntu1
2009-10-28 21:02:46 configure libespeak1 1.41.01-0ubuntu1 1.41.01-0ubuntu1
2009-10-28 21:02:46 status unpacked libespeak1 1.41.01-0ubuntu1
2009-10-28 21:02:46 status half-configured libespeak1 1.41.01-0ubuntu1
2009-10-28 21:02:46 status installed libespeak1 1.41.01-0ubuntu1
2009-10-28 21:02:46 configure espeak 1.41.01-0ubuntu1 1.41.01-0ubuntu1
2009-10-28 21:02:46 status unpacked espeak 1.41.01-0ubuntu1
2009-10-28 21:02:46 status half-configured espeak 1.41.01-0ubuntu1
2009-10-28 21:02:46 status installed espeak 1.41.01-0ubuntu1
2009-10-28 21:02:46 configure ethtool 6+20090307-1 6+20090307-1
2009-10-28 21:02:46 status unpacked ethtool 6+20090307-1
2009-10-28 21:02:46 status unpacked ethtool 6+20090307-1
2009-10-28 21:02:46 status unpacked ethtool 6+20090307-1
2009-10-28 21:02:46 status half-configured ethtool 6+20090307-1
2009-10-28 21:02:46 status installed ethtool 6+20090307-1
2009-10-28 21:02:46 configure libdjvulibre-text 3.5.22-1ubuntu2 3.5.22-1ubuntu2
2009-10-28 21:02:46 status unpacked libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 21:02:46 status half-configured libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 21:02:46 status installed libdjvulibre-text 3.5.22-1ubuntu2
2009-10-28 21:02:46 configure libdjvulibre21 3.5.22-1ubuntu2 3.5.22-1ubuntu2
2009-10-28 21:02:46 status unpacked libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 21:02:46 status half-configured libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 21:02:46 status installed libdjvulibre21 3.5.22-1ubuntu2
2009-10-28 21:02:46 configure libevdocument1 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked libevdocument1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status half-configured libevdocument1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status installed libevdocument1 2.28.1-0ubuntu1
2009-10-28 21:02:46 configure libevview1 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked libevview1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status half-configured libevview1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status installed libevview1 2.28.1-0ubuntu1
2009-10-28 21:02:46 configure libkpathsea4 2007.dfsg.2-7ubuntu1 2007.dfsg.2-7ubuntu1
2009-10-28 21:02:46 status unpacked libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 21:02:46 status half-configured libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 21:02:46 status installed libkpathsea4 2007.dfsg.2-7ubuntu1
2009-10-28 21:02:46 configure libpoppler-glib4 0.12.0-0ubuntu2 0.12.0-0ubuntu2
2009-10-28 21:02:46 status unpacked libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 21:02:46 status half-configured libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 21:02:46 status installed libpoppler-glib4 0.12.0-0ubuntu2
2009-10-28 21:02:46 configure libspectre1 0.2.2.ds-2 0.2.2.ds-2
2009-10-28 21:02:46 status unpacked libspectre1 0.2.2.ds-2
2009-10-28 21:02:46 status half-configured libspectre1 0.2.2.ds-2
2009-10-28 21:02:46 status installed libspectre1 0.2.2.ds-2
2009-10-28 21:02:46 configure evince 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked evince 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked evince 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked evince 2.28.1-0ubuntu1
2009-10-28 21:02:46 status half-configured evince 2.28.1-0ubuntu1
2009-10-28 21:02:46 status installed evince 2.28.1-0ubuntu1
2009-10-28 21:02:46 configure libebackend1.2-0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 21:02:46 status half-configured libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 21:02:46 status installed libebackend1.2-0 2.28.1-0ubuntu1
2009-10-28 21:02:46 configure libegroupwise1.2-13 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:46 status unpacked libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 21:02:46 status half-configured libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libegroupwise1.2-13 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libexchange-storage1.2-3 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libexchange-storage1.2-3 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libgdata1.2-1 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libgdata1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libgdata-google1.2-1 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libgdata-google1.2-1 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libpisock9 0.12.4-3ubuntu1 0.12.4-3ubuntu1
2009-10-28 21:02:47 status unpacked libpisock9 0.12.4-3ubuntu1
2009-10-28 21:02:47 status unpacked libpisock9 0.12.4-3ubuntu1
2009-10-28 21:02:47 status half-configured libpisock9 0.12.4-3ubuntu1
2009-10-28 21:02:47 status installed libpisock9 0.12.4-3ubuntu1
2009-10-28 21:02:47 configure libpisync1 0.12.4-3ubuntu1 0.12.4-3ubuntu1
2009-10-28 21:02:47 status unpacked libpisync1 0.12.4-3ubuntu1
2009-10-28 21:02:47 status half-configured libpisync1 0.12.4-3ubuntu1
2009-10-28 21:02:47 status installed libpisync1 0.12.4-3ubuntu1
2009-10-28 21:02:47 configure libgtkhtml3.14-19 1:3.28.1-0ubuntu1 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libgtkhtml3.14-19 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 configure libgtkhtml-editor-common 1:3.28.1-0ubuntu1 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libgtkhtml-editor-common 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 configure libgtkhtml-editor0 1:3.28.1-0ubuntu1 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libgtkhtml-editor0 1:3.28.1-0ubuntu1
2009-10-28 21:02:47 configure evolution-common 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked evolution-common 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured evolution-common 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed evolution-common 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libedata-book1.2-2 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libedata-book1.2-2 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libedata-cal1.2-6 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed libedata-cal1.2-6 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure evolution-data-server 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:47 status unpacked evolution-data-server 2.28.1-0ubuntu1
2009-10-28 21:02:47 status half-configured evolution-data-server 2.28.1-0ubuntu1
2009-10-28 21:02:47 status installed evolution-data-server 2.28.1-0ubuntu1
2009-10-28 21:02:47 configure libjson-glib-1.0-0 0.7.6-0ubuntu1 0.7.6-0ubuntu1
2009-10-28 21:02:47 status unpacked libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 21:02:47 status half-configured libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 21:02:47 status installed libjson-glib-1.0-0 0.7.6-0ubuntu1
2009-10-28 21:02:47 configure libcouchdb-glib-1.0-1 0.5.2-0ubuntu1 0.5.2-0ubuntu1
2009-10-28 21:02:47 status unpacked libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 21:02:47 status half-configured libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 21:02:47 status installed libcouchdb-glib-1.0-1 0.5.2-0ubuntu1
2009-10-28 21:02:47 configure libpst4 0.6.41-0ubuntu2 0.6.41-0ubuntu2
2009-10-28 21:02:47 status unpacked libpst4 0.6.41-0ubuntu2
2009-10-28 21:02:47 status half-configured libpst4 0.6.41-0ubuntu2
2009-10-28 21:02:47 status installed libpst4 0.6.41-0ubuntu2
2009-10-28 21:02:47 configure evolution-webcal 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:02:47 status unpacked evolution-webcal 2.28.0-0ubuntu1
2009-10-28 21:02:47 status half-configured evolution-webcal 2.28.0-0ubuntu1
2009-10-28 21:02:47 status installed evolution-webcal 2.28.0-0ubuntu1
2009-10-28 21:02:47 configure example-content 38 38
2009-10-28 21:02:47 status unpacked example-content 38
2009-10-28 21:02:47 status unpacked example-content 38
2009-10-28 21:02:47 status half-configured example-content 38
2009-10-28 21:02:47 status installed example-content 38
2009-10-28 21:02:47 configure libsqlite0 2.8.17-6build1 2.8.17-6build1
2009-10-28 21:02:47 status unpacked libsqlite0 2.8.17-6build1
2009-10-28 21:02:47 status half-configured libsqlite0 2.8.17-6build1
2009-10-28 21:02:47 status installed libsqlite0 2.8.17-6build1
2009-10-28 21:02:47 configure libgif4 4.1.6-6 4.1.6-6
2009-10-28 21:02:47 status unpacked libgif4 4.1.6-6
2009-10-28 21:02:47 status half-configured libgif4 4.1.6-6
2009-10-28 21:02:47 status installed libgif4 4.1.6-6
2009-10-28 21:02:47 configure libgdiplus 2.4.2-1 2.4.2-1
2009-10-28 21:02:47 status unpacked libgdiplus 2.4.2-1
2009-10-28 21:02:47 status half-configured libgdiplus 2.4.2-1
2009-10-28 21:02:48 status installed libgdiplus 2.4.2-1
2009-10-28 21:02:48 configure libglitz1 0.5.6-1 0.5.6-1
2009-10-28 21:02:48 status unpacked libglitz1 0.5.6-1
2009-10-28 21:02:48 status half-configured libglitz1 0.5.6-1
2009-10-28 21:02:48 status installed libglitz1 0.5.6-1
2009-10-28 21:02:48 configure libglitz-glx1 0.5.6-1 0.5.6-1
2009-10-28 21:02:48 status unpacked libglitz-glx1 0.5.6-1
2009-10-28 21:02:48 status half-configured libglitz-glx1 0.5.6-1
2009-10-28 21:02:48 status installed libglitz-glx1 0.5.6-1
2009-10-28 21:02:48 configure gvfs-bin 1.4.1-0ubuntu1 1.4.1-0ubuntu1
2009-10-28 21:02:48 status unpacked gvfs-bin 1.4.1-0ubuntu1
2009-10-28 21:02:48 status unpacked gvfs-bin 1.4.1-0ubuntu1
2009-10-28 21:02:48 status half-configured gvfs-bin 1.4.1-0ubuntu1
2009-10-28 21:02:48 status installed gvfs-bin 1.4.1-0ubuntu1
2009-10-28 21:02:48 configure unzip 6.0-1 6.0-1
2009-10-28 21:02:48 status unpacked unzip 6.0-1
2009-10-28 21:02:48 status half-configured unzip 6.0-1
2009-10-28 21:02:48 status installed unzip 6.0-1
2009-10-28 21:02:48 configure zip 3.0-1ubuntu1 3.0-1ubuntu1
2009-10-28 21:02:48 status unpacked zip 3.0-1ubuntu1
2009-10-28 21:02:48 status half-configured zip 3.0-1ubuntu1
2009-10-28 21:02:48 status installed zip 3.0-1ubuntu1
2009-10-28 21:02:48 configure file-roller 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:48 status unpacked file-roller 2.28.1-0ubuntu1
2009-10-28 21:02:48 status half-configured file-roller 2.28.1-0ubuntu1
2009-10-28 21:02:50 status installed file-roller 2.28.1-0ubuntu1
2009-10-28 21:02:50 configure mscompress 0.3-3 0.3-3
2009-10-28 21:02:50 status unpacked mscompress 0.3-3
2009-10-28 21:02:50 status half-configured mscompress 0.3-3
2009-10-28 21:02:50 status installed mscompress 0.3-3
2009-10-28 21:02:50 configure foo2zjs 20090623-0ubuntu5 20090623-0ubuntu5
2009-10-28 21:02:50 status unpacked foo2zjs 20090623-0ubuntu5
2009-10-28 21:02:50 status half-configured foo2zjs 20090623-0ubuntu5
2009-10-28 21:02:50 status installed foo2zjs 20090623-0ubuntu5
2009-10-28 21:02:50 configure gcalctool 5.28.1-0ubuntu1 5.28.1-0ubuntu1
2009-10-28 21:02:50 status unpacked gcalctool 5.28.1-0ubuntu1
2009-10-28 21:02:50 status half-configured gcalctool 5.28.1-0ubuntu1
2009-10-28 21:02:50 status installed gcalctool 5.28.1-0ubuntu1
2009-10-28 21:02:50 configure libgomp1 4.4.1-4ubuntu8 4.4.1-4ubuntu8
2009-10-28 21:02:50 status unpacked libgomp1 4.4.1-4ubuntu8
2009-10-28 21:02:50 status half-configured libgomp1 4.4.1-4ubuntu8
2009-10-28 21:02:50 status installed libgomp1 4.4.1-4ubuntu8
2009-10-28 21:02:50 configure gcc-4.4 4.4.1-4ubuntu8 4.4.1-4ubuntu8
2009-10-28 21:02:50 status unpacked gcc-4.4 4.4.1-4ubuntu8
2009-10-28 21:02:50 status half-configured gcc-4.4 4.4.1-4ubuntu8
2009-10-28 21:02:50 status installed gcc-4.4 4.4.1-4ubuntu8
2009-10-28 21:02:50 configure gcc 4:4.4.1-1ubuntu2 4:4.4.1-1ubuntu2
2009-10-28 21:02:50 status unpacked gcc 4:4.4.1-1ubuntu2
2009-10-28 21:02:50 status half-configured gcc 4:4.4.1-1ubuntu2
2009-10-28 21:02:50 update-alternatives: run with --quiet --install /usr/bin/cc cc /usr/bin/gcc 20 --slave /usr/share/man/man1/cc.1.gz cc.1.gz /usr/share/man/man1/gcc.1.gz
2009-10-28 21:02:50 update-alternatives: link group cc updated to point to /usr/bin/gcc
2009-10-28 21:02:50 update-alternatives: run with --quiet --install /usr/bin/c89 c89 /usr/bin/c89-gcc 20 --slave /usr/share/man/man1/c89.1.gz c89.1.gz /usr/share/man/man1/c89-gcc.1.gz
2009-10-28 21:02:50 update-alternatives: link group c89 updated to point to /usr/bin/c89-gcc
2009-10-28 21:02:50 update-alternatives: run with --quiet --install /usr/bin/c99 c99 /usr/bin/c99-gcc 20 --slave /usr/share/man/man1/c99.1.gz c99.1.gz /usr/share/man/man1/c99-gcc.1.gz
2009-10-28 21:02:50 update-alternatives: link group c99 updated to point to /usr/bin/c99-gcc
2009-10-28 21:02:50 status installed gcc 4:4.4.1-1ubuntu2
2009-10-28 21:02:50 configure gconf-defaults-service 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:02:50 status unpacked gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 21:02:50 status unpacked gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 21:02:51 status half-configured gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 21:02:51 status installed gconf-defaults-service 2.28.0-0ubuntu2
2009-10-28 21:02:51 configure gconf-editor 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:02:51 status unpacked gconf-editor 2.28.0-0ubuntu1
2009-10-28 21:02:51 status half-configured gconf-editor 2.28.0-0ubuntu1
2009-10-28 21:02:51 status installed gconf-editor 2.28.0-0ubuntu1
2009-10-28 21:02:51 configure gdb 7.0-0ubuntu1 7.0-0ubuntu1
2009-10-28 21:02:51 status unpacked gdb 7.0-0ubuntu1
2009-10-28 21:02:51 status unpacked gdb 7.0-0ubuntu1
2009-10-28 21:02:51 status half-configured gdb 7.0-0ubuntu1
2009-10-28 21:02:51 status installed gdb 7.0-0ubuntu1
2009-10-28 21:02:51 configure gdebi-core 0.5.9 0.5.9
2009-10-28 21:02:51 status unpacked gdebi-core 0.5.9
2009-10-28 21:02:51 status half-configured gdebi-core 0.5.9
2009-10-28 21:02:51 status installed gdebi-core 0.5.9
2009-10-28 21:02:51 configure gdebi 0.5.9 0.5.9
2009-10-28 21:02:51 status unpacked gdebi 0.5.9
2009-10-28 21:02:51 status half-configured gdebi 0.5.9
2009-10-28 21:02:51 status installed gdebi 0.5.9
2009-10-28 21:02:51 configure gnome-session-bin 2.28.0-0ubuntu5 2.28.0-0ubuntu5
2009-10-28 21:02:51 status unpacked gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 21:02:51 status half-configured gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 21:02:52 status installed gnome-session-bin 2.28.0-0ubuntu5
2009-10-28 21:02:52 configure hal-info 20090716-0ubuntu1 20090716-0ubuntu1
2009-10-28 21:02:52 status unpacked hal-info 20090716-0ubuntu1
2009-10-28 21:02:52 status half-configured hal-info 20090716-0ubuntu1
2009-10-28 21:02:52 status installed hal-info 20090716-0ubuntu1
2009-10-28 21:02:52 configure hal 0.5.13-1ubuntu8 0.5.13-1ubuntu8
2009-10-28 21:02:52 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 status unpacked hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 status half-configured hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 status installed hal 0.5.13-1ubuntu8
2009-10-28 21:02:52 configure libgtksourceview2.0-common 2.8.1-1 2.8.1-1
2009-10-28 21:02:52 status unpacked libgtksourceview2.0-common 2.8.1-1
2009-10-28 21:02:52 status half-configured libgtksourceview2.0-common 2.8.1-1
2009-10-28 21:02:52 status installed libgtksourceview2.0-common 2.8.1-1
2009-10-28 21:02:52 configure libgtksourceview2.0-0 2.8.1-1 2.8.1-1
2009-10-28 21:02:52 status unpacked libgtksourceview2.0-0 2.8.1-1
2009-10-28 21:02:52 status half-configured libgtksourceview2.0-0 2.8.1-1
2009-10-28 21:02:52 status installed libgtksourceview2.0-0 2.8.1-1
2009-10-28 21:02:52 configure gedit-common 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:02:52 status unpacked gedit-common 2.28.0-0ubuntu2
2009-10-28 21:02:52 status half-configured gedit-common 2.28.0-0ubuntu2
2009-10-28 21:02:52 status installed gedit-common 2.28.0-0ubuntu2
2009-10-28 21:02:52 configure python-gtksourceview2 2.8.0-1 2.8.0-1
2009-10-28 21:02:52 status unpacked python-gtksourceview2 2.8.0-1
2009-10-28 21:02:52 status half-configured python-gtksourceview2 2.8.0-1
2009-10-28 21:02:52 status installed python-gtksourceview2 2.8.0-1
2009-10-28 21:02:52 configure gedit 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:02:52 status unpacked gedit 2.28.0-0ubuntu2
2009-10-28 21:02:52 status half-configured gedit 2.28.0-0ubuntu2
2009-10-28 21:02:52 update-alternatives: run with --install /usr/bin/gnome-text-editor gnome-text-editor /usr/bin/gedit 50 --slave /usr/share/man/man1/gnome-text-editor.1.gz gnome-text-editor.1.gz /usr/share/man/man1/gedit.1.gz
2009-10-28 21:02:52 update-alternatives: link group gnome-text-editor updated to point to /usr/bin/gedit
2009-10-28 21:02:53 status installed gedit 2.28.0-0ubuntu2
2009-10-28 21:02:53 configure libggz2 0.0.14.1-1build1 0.0.14.1-1build1
2009-10-28 21:02:53 status unpacked libggz2 0.0.14.1-1build1
2009-10-28 21:02:53 status half-configured libggz2 0.0.14.1-1build1
2009-10-28 21:02:54 status installed libggz2 0.0.14.1-1build1
2009-10-28 21:02:54 configure libggzcore9 0.0.14.1-1ubuntu1 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status unpacked libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status half-configured libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status installed libggzcore9 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 configure libggzmod4 0.0.14.1-1ubuntu1 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status unpacked libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status half-configured libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status installed libggzmod4 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 configure ggzcore-bin 0.0.14.1-1ubuntu1 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status unpacked ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status unpacked ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status unpacked ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status half-configured ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 status installed ggzcore-bin 0.0.14.1-1ubuntu1
2009-10-28 21:02:54 configure ghostscript-x 8.70.dfsg.1-0ubuntu3 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:54 status unpacked ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:54 status half-configured ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:54 status installed ghostscript-x 8.70.dfsg.1-0ubuntu3
2009-10-28 21:02:54 configure libgimp2.0 2.6.7-1ubuntu1 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked libgimp2.0 2.6.7-1ubuntu1
2009-10-28 21:02:54 status half-configured libgimp2.0 2.6.7-1ubuntu1
2009-10-28 21:02:54 status installed libgimp2.0 2.6.7-1ubuntu1
2009-10-28 21:02:54 configure gimp-data 2.6.7-1ubuntu1 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status half-configured gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 status installed gimp-data 2.6.7-1ubuntu1
2009-10-28 21:02:54 configure libbabl-0.0-0 0.0.22-1 0.0.22-1
2009-10-28 21:02:54 status unpacked libbabl-0.0-0 0.0.22-1
2009-10-28 21:02:54 status half-configured libbabl-0.0-0 0.0.22-1
2009-10-28 21:02:54 status installed libbabl-0.0-0 0.0.22-1
2009-10-28 21:02:54 configure libilmbase6 1.0.1-3build1 1.0.1-3build1
2009-10-28 21:02:54 status unpacked libilmbase6 1.0.1-3build1
2009-10-28 21:02:54 status half-configured libilmbase6 1.0.1-3build1
2009-10-28 21:02:54 status installed libilmbase6 1.0.1-3build1
2009-10-28 21:02:54 configure libopenexr6 1.6.1-4ubuntu3 1.6.1-4ubuntu3
2009-10-28 21:02:54 status unpacked libopenexr6 1.6.1-4ubuntu3
2009-10-28 21:02:54 status half-configured libopenexr6 1.6.1-4ubuntu3
2009-10-28 21:02:54 status installed libopenexr6 1.6.1-4ubuntu3
2009-10-28 21:02:54 configure libsdl1.2debian-alsa 1.2.13-4ubuntu4 1.2.13-4ubuntu4
2009-10-28 21:02:54 status unpacked libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 21:02:54 status half-configured libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 21:02:54 status installed libsdl1.2debian-alsa 1.2.13-4ubuntu4
2009-10-28 21:02:54 configure libsdl1.2debian 1.2.13-4ubuntu4 1.2.13-4ubuntu4
2009-10-28 21:02:54 status unpacked libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 21:02:54 status half-configured libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 21:02:54 status installed libsdl1.2debian 1.2.13-4ubuntu4
2009-10-28 21:02:54 configure libgegl-0.0-0 0.0.22-0ubuntu3 0.0.22-0ubuntu3
2009-10-28 21:02:54 status unpacked libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 21:02:54 status half-configured libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 21:02:54 status installed libgegl-0.0-0 0.0.22-0ubuntu3
2009-10-28 21:02:54 configure libmng1 1.0.9-1build1 1.0.9-1build1
2009-10-28 21:02:54 status unpacked libmng1 1.0.9-1build1
2009-10-28 21:02:54 status half-configured libmng1 1.0.9-1build1
2009-10-28 21:02:54 status installed libmng1 1.0.9-1build1
2009-10-28 21:02:54 configure libwmf0.2-7 0.2.8.4-6.1ubuntu1 0.2.8.4-6.1ubuntu1
2009-10-28 21:02:54 status unpacked libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 21:02:54 status half-configured libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 21:02:54 status installed libwmf0.2-7 0.2.8.4-6.1ubuntu1
2009-10-28 21:02:54 configure gimp 2.6.7-1ubuntu1 2.6.7-1ubuntu1
2009-10-28 21:02:54 status unpacked gimp 2.6.7-1ubuntu1
2009-10-28 21:02:54 status half-configured gimp 2.6.7-1ubuntu1
2009-10-28 21:02:54 status installed gimp 2.6.7-1ubuntu1
2009-10-28 21:02:54 configure python-launchpad-integration 0.1.26 0.1.26
2009-10-28 21:02:54 status unpacked python-launchpad-integration 0.1.26
2009-10-28 21:02:54 status half-configured python-launchpad-integration 0.1.26
2009-10-28 21:02:54 status installed python-launchpad-integration 0.1.26
2009-10-28 21:02:54 configure glchess 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:54 status unpacked glchess 1:2.28.0-0ubuntu1
2009-10-28 21:02:54 status half-configured glchess 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status installed glchess 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 configure glines 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status unpacked glines 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status half-configured glines 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status installed glines 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 configure gnect 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status unpacked gnect 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status half-configured gnect 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status installed gnect 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 configure gnibbles 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status unpacked gnibbles 1:2.28.0-0ubuntu1
2009-10-28 21:02:55 status half-configured gnibbles 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status installed gnibbles 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 configure gnobots2 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status unpacked gnobots2 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status half-configured gnobots2 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status installed gnobots2 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 configure gtk2-engines 1:2.18.4-1ubuntu1 1:2.18.4-1ubuntu1
2009-10-28 21:02:56 status unpacked gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 21:02:56 status half-configured gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 21:02:56 status installed gtk2-engines 1:2.18.4-1ubuntu1
2009-10-28 21:02:56 configure gnome-accessibility-themes 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:02:56 status unpacked gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 21:02:56 status half-configured gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 21:02:56 status installed gnome-accessibility-themes 2.28.1-0ubuntu1
2009-10-28 21:02:56 configure gnome-blackjack 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status unpacked gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 21:02:56 status half-configured gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status installed gnome-blackjack 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 configure libgnome-bluetooth7 2.28.1-0ubuntu2 2.28.1-0ubuntu2
2009-10-28 21:02:57 status unpacked libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 21:02:57 status half-configured libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 21:02:57 status installed libgnome-bluetooth7 2.28.1-0ubuntu2
2009-10-28 21:02:57 configure libopenobex1 1.5-2 1.5-2
2009-10-28 21:02:57 status unpacked libopenobex1 1.5-2
2009-10-28 21:02:57 status half-configured libopenobex1 1.5-2
2009-10-28 21:02:57 status installed libopenobex1 1.5-2
2009-10-28 21:02:57 configure obexd-client 0.14-0ubuntu1 0.14-0ubuntu1
2009-10-28 21:02:57 status unpacked obexd-client 0.14-0ubuntu1
2009-10-28 21:02:57 status half-configured obexd-client 0.14-0ubuntu1
2009-10-28 21:02:57 status installed obexd-client 0.14-0ubuntu1
2009-10-28 21:02:57 configure gnome-bluetooth 2.28.1-0ubuntu2 2.28.1-0ubuntu2
2009-10-28 21:02:57 status unpacked gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 21:02:57 status unpacked gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 21:02:57 status half-configured gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 21:02:57 status installed gnome-bluetooth 2.28.1-0ubuntu2
2009-10-28 21:02:57 configure python-gst0.10 0.10.17-1 0.10.17-1
2009-10-28 21:02:57 status unpacked python-gst0.10 0.10.17-1
2009-10-28 21:02:57 status half-configured python-gst0.10 0.10.17-1
2009-10-28 21:02:57 status installed python-gst0.10 0.10.17-1
2009-10-28 21:02:57 configure gnome-codec-install 0.4.1ubuntu1 0.4.1ubuntu1
2009-10-28 21:02:57 status unpacked gnome-codec-install 0.4.1ubuntu1
2009-10-28 21:02:57 status half-configured gnome-codec-install 0.4.1ubuntu1
2009-10-28 21:02:57 update-alternatives: run with --install /usr/bin/gstreamer-codec-install gstreamer-codec-install /usr/bin/gnome-codec-install 85
2009-10-28 21:02:57 update-alternatives: link group gstreamer-codec-install updated to point to /usr/bin/gnome-codec-install
2009-10-28 21:02:57 status installed gnome-codec-install 0.4.1ubuntu1
2009-10-28 21:02:57 configure libgdu-gtk0 2.28.0+git20091012-0ubuntu1 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status unpacked libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status half-configured libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status installed libgdu-gtk0 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 configure gnome-disk-utility 2.28.0+git20091012-0ubuntu1 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status unpacked gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status unpacked gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status half-configured gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 status installed gnome-disk-utility 2.28.0+git20091012-0ubuntu1
2009-10-28 21:02:57 configure gnome-sudoku 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status unpacked gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status half-configured gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status installed gnome-sudoku 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 configure libclutter-1.0-0 1.0.6-0ubuntu1 1.0.6-0ubuntu1
2009-10-28 21:02:57 status unpacked libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 21:02:57 status half-configured libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 21:02:57 status installed libclutter-1.0-0 1.0.6-0ubuntu1
2009-10-28 21:02:57 configure libclutter-gtk-0.10-0 0.10.2-0ubuntu1 0.10.2-0ubuntu1
2009-10-28 21:02:57 status unpacked libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 21:02:57 status half-configured libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 21:02:57 status installed libclutter-gtk-0.10-0 0.10.2-0ubuntu1
2009-10-28 21:02:57 configure gnometris 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status unpacked gnometris 1:2.28.0-0ubuntu1
2009-10-28 21:02:57 status half-configured gnometris 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status installed gnometris 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 configure gnomine 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status unpacked gnomine 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status half-configured gnomine 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status installed gnomine 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 configure gnotravex 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status unpacked gnotravex 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status half-configured gnotravex 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status installed gnotravex 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 configure gnotski 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status unpacked gnotski 1:2.28.0-0ubuntu1
2009-10-28 21:02:58 status half-configured gnotski 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status installed gnotski 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 configure gtali 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status unpacked gtali 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status half-configured gtali 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status installed gtali 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 configure iagno 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status unpacked iagno 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status half-configured iagno 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status installed iagno 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 configure gnome-mahjongg 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status unpacked gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status half-configured gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status installed gnome-mahjongg 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 configure same-gnome 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status unpacked same-gnome 1:2.28.0-0ubuntu1
2009-10-28 21:02:59 status half-configured same-gnome 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 status installed same-gnome 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 configure gnome-games 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-games 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 status half-configured gnome-games 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 status installed gnome-games 1:2.28.0-0ubuntu1
2009-10-28 21:03:00 configure libgnome-mag2 1:0.15.9-0ubuntu1 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status unpacked libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status half-configured libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status installed libgnome-mag2 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 configure gnome-mag 1:0.15.9-0ubuntu1 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status half-configured gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 status installed gnome-mag 1:0.15.9-0ubuntu1
2009-10-28 21:03:00 configure gnome-media-common 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-media-common 2.28.1-0ubuntu1
2009-10-28 21:03:00 status half-configured gnome-media-common 2.28.1-0ubuntu1
2009-10-28 21:03:00 status installed gnome-media-common 2.28.1-0ubuntu1
2009-10-28 21:03:00 configure libgnome-media0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:00 status unpacked libgnome-media0 2.28.1-0ubuntu1
2009-10-28 21:03:00 status half-configured libgnome-media0 2.28.1-0ubuntu1
2009-10-28 21:03:00 status installed libgnome-media0 2.28.1-0ubuntu1
2009-10-28 21:03:00 configure gstreamer0.10-alsa 0.10.25-2ubuntu1 0.10.25-2ubuntu1
2009-10-28 21:03:00 status unpacked gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 21:03:00 status half-configured gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 21:03:00 status installed gstreamer0.10-alsa 0.10.25-2ubuntu1
2009-10-28 21:03:00 configure gstreamer0.10-pulseaudio 0.10.16-1ubuntu3 0.10.16-1ubuntu3
2009-10-28 21:03:00 status unpacked gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 21:03:00 status half-configured gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 21:03:00 status installed gstreamer0.10-pulseaudio 0.10.16-1ubuntu3
2009-10-28 21:03:00 configure gnome-media 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-media 2.28.1-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-media 2.28.1-0ubuntu1
2009-10-28 21:03:00 status half-configured gnome-media 2.28.1-0ubuntu1
2009-10-28 21:03:00 status installed gnome-media 2.28.1-0ubuntu1
2009-10-28 21:03:00 configure whois 4.7.34ubuntu2 4.7.34ubuntu2
2009-10-28 21:03:00 status unpacked whois 4.7.34ubuntu2
2009-10-28 21:03:00 status half-configured whois 4.7.34ubuntu2
2009-10-28 21:03:00 status installed whois 4.7.34ubuntu2
2009-10-28 21:03:00 configure gnome-nettool 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:03:00 status unpacked gnome-nettool 2.28.0-0ubuntu1
2009-10-28 21:03:00 status half-configured gnome-nettool 2.28.0-0ubuntu1
2009-10-28 21:03:00 status installed gnome-nettool 2.28.0-0ubuntu1
2009-10-28 21:03:00 configure libdotconf1.0 1.0.13-2ubuntu1 1.0.13-2ubuntu1
2009-10-28 21:03:00 status unpacked libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 21:03:00 status half-configured libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 21:03:00 status installed libdotconf1.0 1.0.13-2ubuntu1
2009-10-28 21:03:00 configure libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status half-configured libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status installed libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 configure speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status unpacked speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:00 status half-configured speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 status installed speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 configure python-speechd 0.6.7+git20090914~unofficial-0ubuntu4 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 status unpacked python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 status half-configured python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 status installed python-speechd 0.6.7+git20090914~unofficial-0ubuntu4
2009-10-28 21:03:01 configure libbrlapi0.5 4.0-7ubuntu2 4.0-7ubuntu2
2009-10-28 21:03:01 status unpacked libbrlapi0.5 4.0-7ubuntu2
2009-10-28 21:03:01 status half-configured libbrlapi0.5 4.0-7ubuntu2
2009-10-28 21:03:01 status installed libbrlapi0.5 4.0-7ubuntu2
2009-10-28 21:03:01 configure python-brlapi 4.0-7ubuntu2 4.0-7ubuntu2
2009-10-28 21:03:01 status unpacked python-brlapi 4.0-7ubuntu2
2009-10-28 21:03:01 status half-configured python-brlapi 4.0-7ubuntu2
2009-10-28 21:03:01 status installed python-brlapi 4.0-7ubuntu2
2009-10-28 21:03:01 configure notify-osd 0.9.24-0ubuntu1 0.9.24-0ubuntu1
2009-10-28 21:03:01 status unpacked notify-osd 0.9.24-0ubuntu1
2009-10-28 21:03:01 status half-configured notify-osd 0.9.24-0ubuntu1
2009-10-28 21:03:01 status installed notify-osd 0.9.24-0ubuntu1
2009-10-28 21:03:01 configure gnome-screensaver 2.28.0-0ubuntu3 2.28.0-0ubuntu3
2009-10-28 21:03:01 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:01 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:01 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:01 status unpacked gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:01 status half-configured gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:02 status installed gnome-screensaver 2.28.0-0ubuntu3
2009-10-28 21:03:02 configure nautilus-data 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:03:02 status unpacked nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 21:03:02 status half-configured nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 status installed nautilus-data 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 configure nautilus 1:2.28.1-0ubuntu1 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 status unpacked nautilus 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 status half-configured nautilus 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 status installed nautilus 1:2.28.1-0ubuntu1
2009-10-28 21:03:03 configure zenity 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:03:03 status unpacked zenity 2.28.0-0ubuntu2
2009-10-28 21:03:03 status half-configured zenity 2.28.0-0ubuntu2
2009-10-28 21:03:03 status installed zenity 2.28.0-0ubuntu2
2009-10-28 21:03:03 configure metacity 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:03:03 status unpacked metacity 1:2.28.0-0ubuntu1
2009-10-28 21:03:03 status half-configured metacity 1:2.28.0-0ubuntu1
2009-10-28 21:03:03 update-alternatives: run with --install /usr/bin/x-window-manager x-window-manager /usr/bin/metacity 60 --slave /usr/share/man/man1/x-window-manager.1.gz x-window-manager.1.gz /usr/share/man/man1/metacity.1.gz
2009-10-28 21:03:03 update-alternatives: link group x-window-manager updated to point to /usr/bin/metacity
2009-10-28 21:03:03 status installed metacity 1:2.28.0-0ubuntu1
2009-10-28 21:03:03 configure gnome-session-canberra 0.15-0ubuntu7 0.15-0ubuntu7
2009-10-28 21:03:03 status unpacked gnome-session-canberra 0.15-0ubuntu7
2009-10-28 21:03:03 status half-configured gnome-session-canberra 0.15-0ubuntu7
2009-10-28 21:03:03 status installed gnome-session-canberra 0.15-0ubuntu7
2009-10-28 21:03:03 configure libglibmm-2.4-1c2a 2.22.1-2 2.22.1-2
2009-10-28 21:03:03 status unpacked libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 21:03:03 status half-configured libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 21:03:03 status installed libglibmm-2.4-1c2a 2.22.1-2
2009-10-28 21:03:03 configure libcairomm-1.0-1 1.8.0-1build1 1.8.0-1build1
2009-10-28 21:03:03 status unpacked libcairomm-1.0-1 1.8.0-1build1
2009-10-28 21:03:03 status half-configured libcairomm-1.0-1 1.8.0-1build1
2009-10-28 21:03:03 status installed libcairomm-1.0-1 1.8.0-1build1
2009-10-28 21:03:03 configure libpangomm-1.4-1 2.26.0-0ubuntu2 2.26.0-0ubuntu2
2009-10-28 21:03:03 status unpacked libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 21:03:03 status half-configured libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 21:03:03 status installed libpangomm-1.4-1 2.26.0-0ubuntu2
2009-10-28 21:03:03 configure libgtkmm-2.4-1c2a 1:2.18.2-1 1:2.18.2-1
2009-10-28 21:03:03 status unpacked libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 21:03:03 status half-configured libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 21:03:03 status installed libgtkmm-2.4-1c2a 1:2.18.2-1
2009-10-28 21:03:03 configure gnome-system-monitor 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:03:03 status unpacked gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 21:03:03 status half-configured gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 21:03:04 status installed gnome-system-monitor 2.28.0-0ubuntu1
2009-10-28 21:03:04 configure gnome-terminal-data 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:04 status unpacked gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 21:03:04 status half-configured gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 21:03:05 status installed gnome-terminal-data 2.28.1-0ubuntu1
2009-10-28 21:03:05 configure gnome-terminal 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:05 status unpacked gnome-terminal 2.28.1-0ubuntu1
2009-10-28 21:03:05 status half-configured gnome-terminal 2.28.1-0ubuntu1
2009-10-28 21:03:05 update-alternatives: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/gnome-terminal.wrapper 40 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/gnome-terminal.1.gz
2009-10-28 21:03:05 update-alternatives: link group x-terminal-emulator updated to point to /usr/bin/gnome-terminal.wrapper
2009-10-28 21:03:05 status installed gnome-terminal 2.28.1-0ubuntu1
2009-10-28 21:03:05 configure gtk2-engines-pixbuf 2.18.3-1 2.18.3-1
2009-10-28 21:03:05 status unpacked gtk2-engines-pixbuf 2.18.3-1
2009-10-28 21:03:05 status half-configured gtk2-engines-pixbuf 2.18.3-1
2009-10-28 21:03:05 status installed gtk2-engines-pixbuf 2.18.3-1
2009-10-28 21:03:05 configure gnome-themes-selected 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:05 status unpacked gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 21:03:05 status half-configured gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 21:03:05 status installed gnome-themes-selected 2.28.1-0ubuntu1
2009-10-28 21:03:05 configure gtk2-engines-murrine 0.90.3-1ubuntu1 0.90.3-1ubuntu1
2009-10-28 21:03:05 status unpacked gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 21:03:05 status half-configured gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 21:03:05 status installed gtk2-engines-murrine 0.90.3-1ubuntu1
2009-10-28 21:03:05 configure humanity-icon-theme 0.4.1ubuntu5 0.4.1ubuntu5
2009-10-28 21:03:05 status unpacked humanity-icon-theme 0.4.1ubuntu5
2009-10-28 21:03:05 status half-configured humanity-icon-theme 0.4.1ubuntu5
2009-10-28 21:03:05 status installed humanity-icon-theme 0.4.1ubuntu5
2009-10-28 21:03:05 configure gnome-themes-ubuntu 0.5.1 0.5.1
2009-10-28 21:03:05 status unpacked gnome-themes-ubuntu 0.5.1
2009-10-28 21:03:05 status half-configured gnome-themes-ubuntu 0.5.1
2009-10-28 21:03:05 status installed gnome-themes-ubuntu 0.5.1
2009-10-28 21:03:05 configure libgdict-1.0-6 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:05 status unpacked libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 21:03:05 status half-configured libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 21:03:05 status installed libgdict-1.0-6 2.28.1-0ubuntu1
2009-10-28 21:03:05 configure grub-common 1.97~beta4-1ubuntu3 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status half-configured grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status installed grub-common 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 configure grub-pc 1.97~beta4-1ubuntu3 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-pc 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status unpacked grub-pc 1.97~beta4-1ubuntu3
2009-10-28 21:03:05 status half-configured grub-pc 1.97~beta4-1ubuntu3
2009-10-28 21:03:06 status installed grub-pc 1.97~beta4-1ubuntu3
2009-10-28 21:03:06 configure pkg-config 0.22-1build1 0.22-1build1
2009-10-28 21:03:06 status unpacked pkg-config 0.22-1build1
2009-10-28 21:03:06 status half-configured pkg-config 0.22-1build1
2009-10-28 21:03:06 status installed pkg-config 0.22-1build1
2009-10-28 21:03:06 configure gstreamer0.10-tools 0.10.25-2 0.10.25-2
2009-10-28 21:03:06 status unpacked gstreamer0.10-tools 0.10.25-2
2009-10-28 21:03:06 status half-configured gstreamer0.10-tools 0.10.25-2
2009-10-28 21:03:06 status installed gstreamer0.10-tools 0.10.25-2
2009-10-28 21:03:06 configure gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1 0.10.25-2ubuntu1
2009-10-28 21:03:06 status unpacked gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 21:03:06 status half-configured gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 21:03:06 status installed gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1
2009-10-28 21:03:06 configure gstreamer0.10-x 0.10.25-2ubuntu1 0.10.25-2ubuntu1
2009-10-28 21:03:06 status unpacked gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 21:03:06 status half-configured gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 21:03:06 status installed gstreamer0.10-x 0.10.25-2ubuntu1
2009-10-28 21:03:06 configure gucharmap 1:2.28.0-0ubuntu1 1:2.28.0-0ubuntu1
2009-10-28 21:03:06 status unpacked gucharmap 1:2.28.0-0ubuntu1
2009-10-28 21:03:06 status half-configured gucharmap 1:2.28.0-0ubuntu1
2009-10-28 21:03:07 status installed gucharmap 1:2.28.0-0ubuntu1
2009-10-28 21:03:07 configure libarchive1 2.6.2-1 2.6.2-1
2009-10-28 21:03:07 status unpacked libarchive1 2.6.2-1
2009-10-28 21:03:07 status half-configured libarchive1 2.6.2-1
2009-10-28 21:03:07 status installed libarchive1 2.6.2-1
2009-10-28 21:03:07 configure libcdio7 0.78.2+dfsg1-3 0.78.2+dfsg1-3
2009-10-28 21:03:07 status unpacked libcdio7 0.78.2+dfsg1-3
2009-10-28 21:03:07 status half-configured libcdio7 0.78.2+dfsg1-3
2009-10-28 21:03:07 status installed libcdio7 0.78.2+dfsg1-3
2009-10-28 21:03:07 configure libcdio-cdda0 0.78.2+dfsg1-3 0.78.2+dfsg1-3
2009-10-28 21:03:07 status unpacked libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 21:03:07 status half-configured libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 21:03:07 status installed libcdio-cdda0 0.78.2+dfsg1-3
2009-10-28 21:03:07 configure libcdio-paranoia0 0.78.2+dfsg1-3 0.78.2+dfsg1-3
2009-10-28 21:03:07 status unpacked libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 21:03:07 status half-configured libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 21:03:07 status installed libcdio-paranoia0 0.78.2+dfsg1-3
2009-10-28 21:03:07 configure libtalloc1 1.4.0~git20090718-1 1.4.0~git20090718-1
2009-10-28 21:03:07 status unpacked libtalloc1 1.4.0~git20090718-1
2009-10-28 21:03:07 status half-configured libtalloc1 1.4.0~git20090718-1
2009-10-28 21:03:07 status installed libtalloc1 1.4.0~git20090718-1
2009-10-28 21:03:07 configure libwbclient0 2:3.4.0-3ubuntu5 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status unpacked libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status half-configured libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status installed libwbclient0 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 configure libsmbclient 2:3.4.0-3ubuntu5 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status unpacked libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status half-configured libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 status installed libsmbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:07 configure gvfs-backends 1.4.1-0ubuntu1 1.4.1-0ubuntu1
2009-10-28 21:03:07 status unpacked gvfs-backends 1.4.1-0ubuntu1
2009-10-28 21:03:07 status half-configured gvfs-backends 1.4.1-0ubuntu1
2009-10-28 21:03:07 status installed gvfs-backends 1.4.1-0ubuntu1
2009-10-28 21:03:07 configure gvfs-fuse 1.4.1-0ubuntu1 1.4.1-0ubuntu1
2009-10-28 21:03:07 status unpacked gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 21:03:07 status half-configured gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 21:03:07 status installed gvfs-fuse 1.4.1-0ubuntu1
2009-10-28 21:03:07 configure hpijs 3.9.8-1ubuntu2 3.9.8-1ubuntu2
2009-10-28 21:03:07 status unpacked hpijs 3.9.8-1ubuntu2
2009-10-28 21:03:07 status half-configured hpijs 3.9.8-1ubuntu2
2009-10-28 21:03:07 status installed hpijs 3.9.8-1ubuntu2
2009-10-28 21:03:07 configure human-theme 0.37 0.37
2009-10-28 21:03:07 status unpacked human-theme 0.37
2009-10-28 21:03:07 status half-configured human-theme 0.37
2009-10-28 21:03:07 status installed human-theme 0.37
2009-10-28 21:03:07 configure hunspell-en-us 20070829-2ubuntu4 20070829-2ubuntu4
2009-10-28 21:03:07 status unpacked hunspell-en-us 20070829-2ubuntu4
2009-10-28 21:03:07 status half-configured hunspell-en-us 20070829-2ubuntu4
2009-10-28 21:03:07 status installed hunspell-en-us 20070829-2ubuntu4
2009-10-28 21:03:07 configure libibus1 1.2.0.20090927-2ubuntu1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status unpacked libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status half-configured libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status installed libibus1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 configure im-switch 1.16ubuntu1 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status unpacked im-switch 1.16ubuntu1
2009-10-28 21:03:07 status half-configured im-switch 1.16ubuntu1
2009-10-28 21:03:07 update-alternatives: run with --install /etc/X11/xinit/xinput.d/all_ALL xinput-all_ALL /etc/X11/xinit/xinput.d/default 10
2009-10-28 21:03:07 update-alternatives: link group xinput-all_ALL updated to point to /etc/X11/xinit/xinput.d/default
2009-10-28 21:03:07 update-alternatives: run with --install /etc/X11/xinit/xinput.d/all_ALL xinput-all_ALL /etc/X11/xinit/xinput.d/default-xim 0
2009-10-28 21:03:07 update-alternatives: run with --install /etc/X11/xinit/xinput.d/all_ALL xinput-all_ALL /etc/X11/xinit/xinput.d/none 0
2009-10-28 21:03:07 update-alternatives: run with --install /etc/X11/xinit/xinput.d/th_TH xinput-th_TH /etc/X11/xinit/xinput.d/th-xim 20
2009-10-28 21:03:07 update-alternatives: link group xinput-th_TH updated to point to /etc/X11/xinit/xinput.d/th-xim
2009-10-28 21:03:07 status installed im-switch 1.16ubuntu1
2009-10-28 21:03:07 configure python-ibus 1.2.0.20090927-2ubuntu1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status unpacked python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status half-configured python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status installed python-ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 configure python-rsvg 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:03:07 status unpacked python-rsvg 2.28.0-0ubuntu1
2009-10-28 21:03:07 status half-configured python-rsvg 2.28.0-0ubuntu1
2009-10-28 21:03:07 status installed python-rsvg 2.28.0-0ubuntu1
2009-10-28 21:03:07 configure ibus 1.2.0.20090927-2ubuntu1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status unpacked ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status unpacked ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 status half-configured ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:07 update-alternatives: run with --install /etc/X11/xinit/xinput.d/ja_JP xinput-ja_JP /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:07 update-alternatives: link group xinput-ja_JP updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:08 update-alternatives: run with --install /etc/X11/xinit/xinput.d/ko_KR xinput-ko_KR /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:08 update-alternatives: link group xinput-ko_KR updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:08 update-alternatives: run with --install /etc/X11/xinit/xinput.d/zh_CN xinput-zh_CN /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:08 update-alternatives: link group xinput-zh_CN updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:08 update-alternatives: run with --install /etc/X11/xinit/xinput.d/zh_TW xinput-zh_TW /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:08 update-alternatives: link group xinput-zh_TW updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:08 update-alternatives: run with --install /etc/X11/xinit/xinput.d/zh_HK xinput-zh_HK /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:08 update-alternatives: link group xinput-zh_HK updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:08 update-alternatives: run with --install /etc/X11/xinit/xinput.d/zh_SG xinput-zh_SG /etc/X11/xinit/xinput.d/ibus 60
2009-10-28 21:03:08 update-alternatives: link group xinput-zh_SG updated to point to /etc/X11/xinit/xinput.d/ibus
2009-10-28 21:03:09 status installed ibus 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:09 configure ibus-gtk 1.2.0.20090927-2ubuntu1 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:09 status unpacked ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:09 status half-configured ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:09 status installed ibus-gtk 1.2.0.20090927-2ubuntu1
2009-10-28 21:03:09 configure libanthy0 9100h-0ubuntu1 9100h-0ubuntu1
2009-10-28 21:03:09 status unpacked libanthy0 9100h-0ubuntu1
2009-10-28 21:03:09 status half-configured libanthy0 9100h-0ubuntu1
2009-10-28 21:03:09 status installed libanthy0 9100h-0ubuntu1
2009-10-28 21:03:09 configure libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 21:03:09 status unpacked libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 21:03:09 status half-configured libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 21:03:09 status installed libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1
2009-10-28 21:03:09 configure libotf0 0.9.9-1 0.9.9-1
2009-10-28 21:03:09 status unpacked libotf0 0.9.9-1
2009-10-28 21:03:09 status half-configured libotf0 0.9.9-1
2009-10-28 21:03:09 status installed libotf0 0.9.9-1
2009-10-28 21:03:09 configure libm17n-0 1.5.4-1ubuntu1 1.5.4-1ubuntu1
2009-10-28 21:03:09 status unpacked libm17n-0 1.5.4-1ubuntu1
2009-10-28 21:03:09 status half-configured libm17n-0 1.5.4-1ubuntu1
2009-10-28 21:03:09 status installed libm17n-0 1.5.4-1ubuntu1
2009-10-28 21:03:09 configure ibus-m17n 1.2.0.20090930-1 1.2.0.20090930-1
2009-10-28 21:03:09 status unpacked ibus-m17n 1.2.0.20090930-1
2009-10-28 21:03:09 status half-configured ibus-m17n 1.2.0.20090930-1
2009-10-28 21:03:09 status installed ibus-m17n 1.2.0.20090930-1
2009-10-28 21:03:09 configure ibus-table 1.2.0.20090625-1 1.2.0.20090625-1
2009-10-28 21:03:09 status unpacked ibus-table 1.2.0.20090625-1
2009-10-28 21:03:09 status half-configured ibus-table 1.2.0.20090625-1
2009-10-28 21:03:09 status installed ibus-table 1.2.0.20090625-1
2009-10-28 21:03:09 configure libdbusmenu-glib0 0.1.6-0ubuntu1 0.1.6-0ubuntu1
2009-10-28 21:03:09 status unpacked libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 21:03:09 status half-configured libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 21:03:09 status installed libdbusmenu-glib0 0.1.6-0ubuntu1
2009-10-28 21:03:09 configure libdbusmenu-gtk0 0.1.6-0ubuntu1 0.1.6-0ubuntu1
2009-10-28 21:03:09 status unpacked libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 21:03:09 status half-configured libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 21:03:09 status installed libdbusmenu-gtk0 0.1.6-0ubuntu1
2009-10-28 21:03:09 configure inputattach 1.23-0ubuntu3 1.23-0ubuntu3
2009-10-28 21:03:09 status unpacked inputattach 1.23-0ubuntu3
2009-10-28 21:03:09 status half-configured inputattach 1.23-0ubuntu3
2009-10-28 21:03:09 status installed inputattach 1.23-0ubuntu3
2009-10-28 21:03:09 configure python-xkit 0.4.2 0.4.2
2009-10-28 21:03:09 status unpacked python-xkit 0.4.2
2009-10-28 21:03:09 status half-configured python-xkit 0.4.2
2009-10-28 21:03:09 status installed python-xkit 0.4.2
2009-10-28 21:03:09 configure jockey-common 0.5.5-0ubuntu2 0.5.5-0ubuntu2
2009-10-28 21:03:09 status unpacked jockey-common 0.5.5-0ubuntu2
2009-10-28 21:03:09 status unpacked jockey-common 0.5.5-0ubuntu2
2009-10-28 21:03:09 status unpacked jockey-common 0.5.5-0ubuntu2
2009-10-28 21:03:09 status half-configured jockey-common 0.5.5-0ubuntu2
2009-10-28 21:03:09 status installed jockey-common 0.5.5-0ubuntu2
2009-10-28 21:03:09 configure python-notify 0.1.1-2build2 0.1.1-2build2
2009-10-28 21:03:09 status unpacked python-notify 0.1.1-2build2
2009-10-28 21:03:09 status half-configured python-notify 0.1.1-2build2
2009-10-28 21:03:10 status installed python-notify 0.1.1-2build2
2009-10-28 21:03:10 configure jockey-gtk 0.5.5-0ubuntu2 0.5.5-0ubuntu2
2009-10-28 21:03:10 status unpacked jockey-gtk 0.5.5-0ubuntu2
2009-10-28 21:03:10 status unpacked jockey-gtk 0.5.5-0ubuntu2
2009-10-28 21:03:10 status half-configured jockey-gtk 0.5.5-0ubuntu2
2009-10-28 21:03:10 status installed jockey-gtk 0.5.5-0ubuntu2
2009-10-28 21:03:10 configure kerneloops-daemon 0.12+git20090217-1ubuntu4 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 status unpacked kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 status unpacked kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 status unpacked kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 status half-configured kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 status installed kerneloops-daemon 0.12+git20090217-1ubuntu4
2009-10-28 21:03:10 configure language-selector-common 0.4.18 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status unpacked language-selector-common 0.4.18
2009-10-28 21:03:10 status half-configured language-selector-common 0.4.18
2009-10-28 21:03:11 status installed language-selector-common 0.4.18
2009-10-28 21:03:11 configure language-selector 0.4.18 0.4.18
2009-10-28 21:03:11 status unpacked language-selector 0.4.18
2009-10-28 21:03:11 status half-configured language-selector 0.4.18
2009-10-28 21:03:11 status installed language-selector 0.4.18
2009-10-28 21:03:11 configure launchpad-integration 0.1.26 0.1.26
2009-10-28 21:03:11 status unpacked launchpad-integration 0.1.26
2009-10-28 21:03:11 status half-configured launchpad-integration 0.1.26
2009-10-28 21:03:11 status installed launchpad-integration 0.1.26
2009-10-28 21:03:11 configure lftp 3.7.15-1ubuntu2 3.7.15-1ubuntu2
2009-10-28 21:03:11 status unpacked lftp 3.7.15-1ubuntu2
2009-10-28 21:03:11 status unpacked lftp 3.7.15-1ubuntu2
2009-10-28 21:03:11 status half-configured lftp 3.7.15-1ubuntu2
2009-10-28 21:03:11 status installed lftp 3.7.15-1ubuntu2
2009-10-28 21:03:11 configure libsamplerate0 0.1.7-2 0.1.7-2
2009-10-28 21:03:11 status unpacked libsamplerate0 0.1.7-2
2009-10-28 21:03:11 status half-configured libsamplerate0 0.1.7-2
2009-10-28 21:03:11 status installed libsamplerate0 0.1.7-2
2009-10-28 21:03:11 configure libasound2-plugins 1.0.20-1ubuntu8 1.0.20-1ubuntu8
2009-10-28 21:03:11 status unpacked libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 21:03:11 status half-configured libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 21:03:11 status installed libasound2-plugins 1.0.20-1ubuntu8
2009-10-28 21:03:11 configure libatk1.0-data 1.28.0-0ubuntu1 1.28.0-0ubuntu1
2009-10-28 21:03:11 status unpacked libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 21:03:11 status half-configured libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 21:03:11 status installed libatk1.0-data 1.28.0-0ubuntu1
2009-10-28 21:03:11 configure libavahi-gobject0 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:03:11 status unpacked libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 21:03:11 status half-configured libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 21:03:11 status installed libavahi-gobject0 0.6.25-1ubuntu5
2009-10-28 21:03:11 configure libavahi-ui0 0.6.25-1ubuntu5 0.6.25-1ubuntu5
2009-10-28 21:03:11 status unpacked libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 21:03:11 status half-configured libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 21:03:11 status installed libavahi-ui0 0.6.25-1ubuntu5
2009-10-28 21:03:11 configure libc-dev-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 21:03:11 status unpacked libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 21:03:11 status half-configured libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 21:03:11 status installed libc-dev-bin 2.10.1-0ubuntu15
2009-10-28 21:03:11 configure linux-libc-dev 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:03:11 status unpacked linux-libc-dev 2.6.31-14.48
2009-10-28 21:03:11 status half-configured linux-libc-dev 2.6.31-14.48
2009-10-28 21:03:11 status installed linux-libc-dev 2.6.31-14.48
2009-10-28 21:03:11 configure libc6-dev 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 21:03:11 status unpacked libc6-dev 2.10.1-0ubuntu15
2009-10-28 21:03:11 status half-configured libc6-dev 2.10.1-0ubuntu15
2009-10-28 21:03:11 status installed libc6-dev 2.10.1-0ubuntu15
2009-10-28 21:03:11 configure libcairo-perl 1.061-1 1.061-1
2009-10-28 21:03:11 status unpacked libcairo-perl 1.061-1
2009-10-28 21:03:11 status half-configured libcairo-perl 1.061-1
2009-10-28 21:03:11 status installed libcairo-perl 1.061-1
2009-10-28 21:03:11 configure libcanberra-gtk-module 0.15-0ubuntu7 0.15-0ubuntu7
2009-10-28 21:03:11 status unpacked libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 21:03:11 status unpacked libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 21:03:11 status half-configured libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 21:03:11 status installed libcanberra-gtk-module 0.15-0ubuntu7
2009-10-28 21:03:11 configure libspeexdsp1 1.2~rc1-1 1.2~rc1-1
2009-10-28 21:03:11 status unpacked libspeexdsp1 1.2~rc1-1
2009-10-28 21:03:11 status half-configured libspeexdsp1 1.2~rc1-1
2009-10-28 21:03:11 status installed libspeexdsp1 1.2~rc1-1
2009-10-28 21:03:11 configure libcolamd2.7.1 1:3.4.0-1ubuntu2 1:3.4.0-1ubuntu2
2009-10-28 21:03:11 status unpacked libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 21:03:11 status half-configured libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 21:03:11 status installed libcolamd2.7.1 1:3.4.0-1ubuntu2
2009-10-28 21:03:11 configure libcryptui0 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:11 status unpacked libcryptui0 2.28.1-0ubuntu1
2009-10-28 21:03:11 status half-configured libcryptui0 2.28.1-0ubuntu1
2009-10-28 21:03:11 status installed libcryptui0 2.28.1-0ubuntu1
2009-10-28 21:03:11 configure libdrm-intel1 2.4.14-1ubuntu1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status unpacked libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status half-configured libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status installed libdrm-intel1 2.4.14-1ubuntu1
2009-10-28 21:03:11 configure libdrm-radeon1 2.4.14-1ubuntu1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status unpacked libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status half-configured libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 21:03:11 status installed libdrm-radeon1 2.4.14-1ubuntu1
2009-10-28 21:03:11 configure libevent-1.4-2 1.4.11-stable-1 1.4.11-stable-1
2009-10-28 21:03:11 status unpacked libevent-1.4-2 1.4.11-stable-1
2009-10-28 21:03:11 status half-configured libevent-1.4-2 1.4.11-stable-1
2009-10-28 21:03:11 status installed libevent-1.4-2 1.4.11-stable-1
2009-10-28 21:03:11 configure libfreezethaw-perl 0.45-1 0.45-1
2009-10-28 21:03:11 status unpacked libfreezethaw-perl 0.45-1
2009-10-28 21:03:11 status half-configured libfreezethaw-perl 0.45-1
2009-10-28 21:03:11 status installed libfreezethaw-perl 0.45-1
2009-10-28 21:03:11 configure libgadu3 1:1.8.0+r592-3 1:1.8.0+r592-3
2009-10-28 21:03:11 status unpacked libgadu3 1:1.8.0+r592-3
2009-10-28 21:03:11 status half-configured libgadu3 1:1.8.0+r592-3
2009-10-28 21:03:11 status installed libgadu3 1:1.8.0+r592-3
2009-10-28 21:03:11 configure libgdata-common 0.4.0-1 0.4.0-1
2009-10-28 21:03:11 status unpacked libgdata-common 0.4.0-1
2009-10-28 21:03:11 status half-configured libgdata-common 0.4.0-1
2009-10-28 21:03:11 status installed libgdata-common 0.4.0-1
2009-10-28 21:03:11 configure libgdata5 0.4.0-1 0.4.0-1
2009-10-28 21:03:11 status unpacked libgdata5 0.4.0-1
2009-10-28 21:03:11 status half-configured libgdata5 0.4.0-1
2009-10-28 21:03:11 status installed libgdata5 0.4.0-1
2009-10-28 21:03:11 configure libglib-perl 1:1.221-1 1:1.221-1
2009-10-28 21:03:11 status unpacked libglib-perl 1:1.221-1
2009-10-28 21:03:11 status half-configured libglib-perl 1:1.221-1
2009-10-28 21:03:11 status installed libglib-perl 1:1.221-1
2009-10-28 21:03:11 configure libgmime-2.0-2a 2.2.22-4 2.2.22-4
2009-10-28 21:03:11 status unpacked libgmime-2.0-2a 2.2.22-4
2009-10-28 21:03:11 status half-configured libgmime-2.0-2a 2.2.22-4
2009-10-28 21:03:11 status installed libgmime-2.0-2a 2.2.22-4
2009-10-28 21:03:12 configure libpango-perl 1.220-1 1.220-1
2009-10-28 21:03:12 status unpacked libpango-perl 1.220-1
2009-10-28 21:03:12 status half-configured libpango-perl 1.220-1
2009-10-28 21:03:12 status installed libpango-perl 1.220-1
2009-10-28 21:03:12 configure libgtk2-perl 1:1.221-4 1:1.221-4
2009-10-28 21:03:12 status unpacked libgtk2-perl 1:1.221-4
2009-10-28 21:03:12 status half-configured libgtk2-perl 1:1.221-4
2009-10-28 21:03:12 status installed libgtk2-perl 1:1.221-4
2009-10-28 21:03:12 configure libgnome2-canvas-perl 1.002-2 1.002-2
2009-10-28 21:03:12 status unpacked libgnome2-canvas-perl 1.002-2
2009-10-28 21:03:12 status half-configured libgnome2-canvas-perl 1.002-2
2009-10-28 21:03:12 status installed libgnome2-canvas-perl 1.002-2
2009-10-28 21:03:12 configure libpth20 2.0.7-12 2.0.7-12
2009-10-28 21:03:12 status unpacked libpth20 2.0.7-12
2009-10-28 21:03:12 status half-configured libpth20 2.0.7-12
2009-10-28 21:03:12 status installed libpth20 2.0.7-12
2009-10-28 21:03:12 configure libgpgme11 1.1.8-2ubuntu3 1.1.8-2ubuntu3
2009-10-28 21:03:12 status unpacked libgpgme11 1.1.8-2ubuntu3
2009-10-28 21:03:12 status half-configured libgpgme11 1.1.8-2ubuntu3
2009-10-28 21:03:12 status installed libgpgme11 1.1.8-2ubuntu3
2009-10-28 21:03:12 configure libgpod4 0.7.2-1ubuntu1 0.7.2-1ubuntu1
2009-10-28 21:03:12 status unpacked libgpod4 0.7.2-1ubuntu1
2009-10-28 21:03:12 status half-configured libgpod4 0.7.2-1ubuntu1
2009-10-28 21:03:12 status installed libgpod4 0.7.2-1ubuntu1
2009-10-28 21:03:12 configure libgpod-common 0.7.2-1ubuntu1 0.7.2-1ubuntu1
2009-10-28 21:03:12 status unpacked libgpod-common 0.7.2-1ubuntu1
2009-10-28 21:03:12 status half-configured libgpod-common 0.7.2-1ubuntu1
2009-10-28 21:03:12 status installed libgpod-common 0.7.2-1ubuntu1
2009-10-28 21:03:12 configure libgraphviz4 2.20.2-3ubuntu5 2.20.2-3ubuntu5
2009-10-28 21:03:12 status unpacked libgraphviz4 2.20.2-3ubuntu5
2009-10-28 21:03:12 status half-configured libgraphviz4 2.20.2-3ubuntu5
2009-10-28 21:03:12 status installed libgraphviz4 2.20.2-3ubuntu5
2009-10-28 21:03:12 configure libgtk-vnc-1.0-0 0.3.9-1ubuntu2 0.3.9-1ubuntu2
2009-10-28 21:03:12 status unpacked libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 21:03:12 status half-configured libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 21:03:12 status installed libgtk-vnc-1.0-0 0.3.9-1ubuntu2
2009-10-28 21:03:12 configure libgtkhtml2-0 2.11.1-2ubuntu2 2.11.1-2ubuntu2
2009-10-28 21:03:12 status unpacked libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 21:03:12 status half-configured libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 21:03:12 status installed libgtkhtml2-0 2.11.1-2ubuntu2
2009-10-28 21:03:12 configure libgtkspell0 2.0.15-0ubuntu1 2.0.15-0ubuntu1
2009-10-28 21:03:12 status unpacked libgtkspell0 2.0.15-0ubuntu1
2009-10-28 21:03:12 status half-configured libgtkspell0 2.0.15-0ubuntu1
2009-10-28 21:03:12 status installed libgtkspell0 2.0.15-0ubuntu1
2009-10-28 21:03:12 configure libiw29 29-2ubuntu6 29-2ubuntu6
2009-10-28 21:03:12 status unpacked libiw29 29-2ubuntu6
2009-10-28 21:03:12 status half-configured libiw29 29-2ubuntu6
2009-10-28 21:03:12 status installed libiw29 29-2ubuntu6
2009-10-28 21:03:12 configure libloudmouth1-0 1.4.3-4 1.4.3-4
2009-10-28 21:03:12 status unpacked libloudmouth1-0 1.4.3-4
2009-10-28 21:03:12 status half-configured libloudmouth1-0 1.4.3-4
2009-10-28 21:03:12 status installed libloudmouth1-0 1.4.3-4
2009-10-28 21:03:12 configure libmeanwhile1 1.0.2-3build1 1.0.2-3build1
2009-10-28 21:03:12 status unpacked libmeanwhile1 1.0.2-3build1
2009-10-28 21:03:12 status half-configured libmeanwhile1 1.0.2-3build1
2009-10-28 21:03:12 status installed libmeanwhile1 1.0.2-3build1
2009-10-28 21:03:12 configure libmtp8 0.3.7-3ubuntu2 0.3.7-3ubuntu2
2009-10-28 21:03:12 status unpacked libmtp8 0.3.7-3ubuntu2
2009-10-28 21:03:12 status half-configured libmtp8 0.3.7-3ubuntu2
2009-10-28 21:03:12 status installed libmtp8 0.3.7-3ubuntu2
2009-10-28 21:03:12 configure libmusicbrainz4c2a 2.1.5-2ubuntu1 2.1.5-2ubuntu1
2009-10-28 21:03:12 status unpacked libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 21:03:12 status half-configured libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 21:03:12 status installed libmusicbrainz4c2a 2.1.5-2ubuntu1
2009-10-28 21:03:12 configure libxml-twig-perl 1:3.32-3ubuntu1 1:3.32-3ubuntu1
2009-10-28 21:03:12 status unpacked libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 21:03:12 status half-configured libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 21:03:12 status installed libxml-twig-perl 1:3.32-3ubuntu1
2009-10-28 21:03:12 configure libnet-dbus-perl 0.33.6-1build2 0.33.6-1build2
2009-10-28 21:03:12 status unpacked libnet-dbus-perl 0.33.6-1build2
2009-10-28 21:03:12 status half-configured libnet-dbus-perl 0.33.6-1build2
2009-10-28 21:03:12 status installed libnet-dbus-perl 0.33.6-1build2
2009-10-28 21:03:12 configure libnss-mdns 0.10-3ubuntu3 0.10-3ubuntu3
2009-10-28 21:03:12 status unpacked libnss-mdns 0.10-3ubuntu3
2009-10-28 21:03:12 status half-configured libnss-mdns 0.10-3ubuntu3
2009-10-28 21:03:12 status installed libnss-mdns 0.10-3ubuntu3
2009-10-28 21:03:12 configure system-tools-backends 2.8.2-1 2.8.2-1
2009-10-28 21:03:12 status unpacked system-tools-backends 2.8.2-1
2009-10-28 21:03:12 status unpacked system-tools-backends 2.8.2-1
2009-10-28 21:03:12 status half-configured system-tools-backends 2.8.2-1
2009-10-28 21:03:12 status installed system-tools-backends 2.8.2-1
2009-10-28 21:03:12 configure liboobs-1-4 2.22.2-0ubuntu1 2.22.2-0ubuntu1
2009-10-28 21:03:12 status unpacked liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 21:03:12 status half-configured liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 21:03:12 status installed liboobs-1-4 2.22.2-0ubuntu1
2009-10-28 21:03:12 configure libpam-ck-connector 0.3.1-0ubuntu2 0.3.1-0ubuntu2
2009-10-28 21:03:12 status unpacked libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 21:03:12 status half-configured libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 21:03:12 status installed libpam-ck-connector 0.3.1-0ubuntu2
2009-10-28 21:03:12 configure libpam-gnome-keyring 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:12 status unpacked libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:03:12 status half-configured libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:03:13 status installed libpam-gnome-keyring 2.28.1-0ubuntu1
2009-10-28 21:03:13 configure libpaper-utils 1.1.23+nmu1 1.1.23+nmu1
2009-10-28 21:03:13 status unpacked libpaper-utils 1.1.23+nmu1
2009-10-28 21:03:13 status half-configured libpaper-utils 1.1.23+nmu1
2009-10-28 21:03:13 status installed libpaper-utils 1.1.23+nmu1
2009-10-28 21:03:13 configure libpcsclite1 1.5.3-1ubuntu1 1.5.3-1ubuntu1
2009-10-28 21:03:13 status unpacked libpcsclite1 1.5.3-1ubuntu1
2009-10-28 21:03:13 status half-configured libpcsclite1 1.5.3-1ubuntu1
2009-10-28 21:03:13 status installed libpcsclite1 1.5.3-1ubuntu1
2009-10-28 21:03:13 configure libpolkit-gtk-1-0 0.94-1+1git.230873 0.94-1+1git.230873
2009-10-28 21:03:13 status unpacked libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 21:03:13 status half-configured libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 21:03:13 status installed libpolkit-gtk-1-0 0.94-1+1git.230873
2009-10-28 21:03:13 configure libpulse-browse0 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:03:13 status unpacked libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 21:03:13 status half-configured libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 21:03:13 status installed libpulse-browse0 1:0.9.19-0ubuntu4
2009-10-28 21:03:13 configure libpurple-bin 1:2.6.2-1ubuntu7 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status unpacked libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status half-configured libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status installed libpurple-bin 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 configure libsilc-1.1-2 1.1.10-2 1.1.10-2
2009-10-28 21:03:13 status unpacked libsilc-1.1-2 1.1.10-2
2009-10-28 21:03:13 status half-configured libsilc-1.1-2 1.1.10-2
2009-10-28 21:03:13 status installed libsilc-1.1-2 1.1.10-2
2009-10-28 21:03:13 configure libsilcclient-1.1-3 1.1.10-2 1.1.10-2
2009-10-28 21:03:13 status unpacked libsilcclient-1.1-3 1.1.10-2
2009-10-28 21:03:13 status half-configured libsilcclient-1.1-3 1.1.10-2
2009-10-28 21:03:13 status installed libsilcclient-1.1-3 1.1.10-2
2009-10-28 21:03:13 configure libzephyr4 3.0~rc.2544-1 3.0~rc.2544-1
2009-10-28 21:03:13 status unpacked libzephyr4 3.0~rc.2544-1
2009-10-28 21:03:13 status half-configured libzephyr4 3.0~rc.2544-1
2009-10-28 21:03:13 status installed libzephyr4 3.0~rc.2544-1
2009-10-28 21:03:13 configure libpurple0 1:2.6.2-1ubuntu7 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status unpacked libpurple0 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status half-configured libpurple0 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 status installed libpurple0 1:2.6.2-1ubuntu7
2009-10-28 21:03:13 configure libsctp1 1.0.10+dfsg-1 1.0.10+dfsg-1
2009-10-28 21:03:13 status unpacked libsctp1 1.0.10+dfsg-1
2009-10-28 21:03:13 status half-configured libsctp1 1.0.10+dfsg-1
2009-10-28 21:03:13 status installed libsctp1 1.0.10+dfsg-1
2009-10-28 21:03:13 configure libsexy2 0.1.11-2build1 0.1.11-2build1
2009-10-28 21:03:13 status unpacked libsexy2 0.1.11-2build1
2009-10-28 21:03:13 status half-configured libsexy2 0.1.11-2build1
2009-10-28 21:03:13 status installed libsexy2 0.1.11-2build1
2009-10-28 21:03:13 configure libtie-ixhash-perl 1.21-2 1.21-2
2009-10-28 21:03:13 status unpacked libtie-ixhash-perl 1.21-2
2009-10-28 21:03:13 status half-configured libtie-ixhash-perl 1.21-2
2009-10-28 21:03:13 status installed libtie-ixhash-perl 1.21-2
2009-10-28 21:03:13 configure libtrackerclient0 0.6.95-1ubuntu3 0.6.95-1ubuntu3
2009-10-28 21:03:13 status unpacked libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 21:03:13 status half-configured libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 21:03:13 status installed libtrackerclient0 0.6.95-1ubuntu3
2009-10-28 21:03:13 configure libx86-1 1.1+ds1-4 1.1+ds1-4
2009-10-28 21:03:13 status unpacked libx86-1 1.1+ds1-4
2009-10-28 21:03:13 status half-configured libx86-1 1.1+ds1-4
2009-10-28 21:03:13 status installed libx86-1 1.1+ds1-4
2009-10-28 21:03:13 configure libusplash0 0.5.49 0.5.49
2009-10-28 21:03:13 status unpacked libusplash0 0.5.49
2009-10-28 21:03:13 status half-configured libusplash0 0.5.49
2009-10-28 21:03:13 status installed libusplash0 0.5.49
2009-10-28 21:03:13 configure libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5 0.4.0.dfsg.1-2ubuntu5
2009-10-28 21:03:13 status unpacked libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 21:03:13 status half-configured libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 21:03:13 status installed libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5
2009-10-28 21:03:13 configure libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1 0.2.8.4-6.1ubuntu1
2009-10-28 21:03:13 status unpacked libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 21:03:13 status half-configured libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 21:03:13 status installed libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1
2009-10-28 21:03:13 configure libwpd8c2a 0.8.14-1 0.8.14-1
2009-10-28 21:03:13 status unpacked libwpd8c2a 0.8.14-1
2009-10-28 21:03:13 status half-configured libwpd8c2a 0.8.14-1
2009-10-28 21:03:13 status installed libwpd8c2a 0.8.14-1
2009-10-28 21:03:13 configure libwps-0.1-1 0.1.2-1 0.1.2-1
2009-10-28 21:03:13 status unpacked libwps-0.1-1 0.1.2-1
2009-10-28 21:03:13 status half-configured libwps-0.1-1 0.1.2-1
2009-10-28 21:03:13 status installed libwps-0.1-1 0.1.2-1
2009-10-28 21:03:13 configure libxfont1 1:1.4.0-1ubuntu1 1:1.4.0-1ubuntu1
2009-10-28 21:03:13 status unpacked libxfont1 1:1.4.0-1ubuntu1
2009-10-28 21:03:13 status half-configured libxfont1 1:1.4.0-1ubuntu1
2009-10-28 21:03:13 status installed libxfont1 1:1.4.0-1ubuntu1
2009-10-28 21:03:13 configure libxml-xpath-perl 1.13-6 1.13-6
2009-10-28 21:03:13 status unpacked libxml-xpath-perl 1.13-6
2009-10-28 21:03:13 status half-configured libxml-xpath-perl 1.13-6
2009-10-28 21:03:13 status installed libxml-xpath-perl 1.13-6
2009-10-28 21:03:13 configure libxp6 1:1.0.0.xsf1-2 1:1.0.0.xsf1-2
2009-10-28 21:03:13 status unpacked libxp6 1:1.0.0.xsf1-2
2009-10-28 21:03:13 status half-configured libxp6 1:1.0.0.xsf1-2
2009-10-28 21:03:13 status installed libxp6 1:1.0.0.xsf1-2
2009-10-28 21:03:13 configure libxvmc1 2:1.0.4-2ubuntu2 2:1.0.4-2ubuntu2
2009-10-28 21:03:13 status unpacked libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 21:03:13 status unpacked libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 21:03:13 status half-configured libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 21:03:13 status installed libxvmc1 2:1.0.4-2ubuntu2
2009-10-28 21:03:13 configure linux-firmware 1.24 1.24
2009-10-28 21:03:13 status unpacked linux-firmware 1.24
2009-10-28 21:03:13 status half-configured linux-firmware 1.24
2009-10-28 21:03:13 status installed linux-firmware 1.24
2009-10-28 21:03:13 configure linux-image-generic 2.6.31.14.27 2.6.31.14.27
2009-10-28 21:03:13 status unpacked linux-image-generic 2.6.31.14.27
2009-10-28 21:03:13 status half-configured linux-image-generic 2.6.31.14.27
2009-10-28 21:03:13 status installed linux-image-generic 2.6.31.14.27
2009-10-28 21:03:13 configure linux-generic 2.6.31.14.27 2.6.31.14.27
2009-10-28 21:03:13 status unpacked linux-generic 2.6.31.14.27
2009-10-28 21:03:13 status half-configured linux-generic 2.6.31.14.27
2009-10-28 21:03:13 status installed linux-generic 2.6.31.14.27
2009-10-28 21:03:13 configure linux-headers-2.6.31-14 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:03:13 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:03:13 status half-configured linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:03:13 status installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:03:13 configure linux-headers-2.6.31-14-generic 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:03:13 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:03:13 status half-configured linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:03:13 status installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:03:13 configure linux-headers-generic 2.6.31.14.27 2.6.31.14.27
2009-10-28 21:03:13 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:03:13 status half-configured linux-headers-generic 2.6.31.14.27
2009-10-28 21:03:13 status installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:03:13 configure lksctp-tools 1.0.10+dfsg-1 1.0.10+dfsg-1
2009-10-28 21:03:13 status unpacked lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:03:13 status half-configured lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:03:13 status installed lksctp-tools 1.0.10+dfsg-1
2009-10-28 21:03:13 configure lp-solve 5.5.0.13-6 5.5.0.13-6
2009-10-28 21:03:13 status unpacked lp-solve 5.5.0.13-6
2009-10-28 21:03:13 status half-configured lp-solve 5.5.0.13-6
2009-10-28 21:03:13 status installed lp-solve 5.5.0.13-6
2009-10-28 21:03:14 configure m17n-db 1.5.4-1 1.5.4-1
2009-10-28 21:03:14 status unpacked m17n-db 1.5.4-1
2009-10-28 21:03:14 status half-configured m17n-db 1.5.4-1
2009-10-28 21:03:14 status installed m17n-db 1.5.4-1
2009-10-28 21:03:14 configure m17n-contrib 1.1.9-1 1.1.9-1
2009-10-28 21:03:14 status unpacked m17n-contrib 1.1.9-1
2009-10-28 21:03:14 status half-configured m17n-contrib 1.1.9-1
2009-10-28 21:03:14 status installed m17n-contrib 1.1.9-1
2009-10-28 21:03:14 configure media-player-info 3-0ubuntu1 3-0ubuntu1
2009-10-28 21:03:14 status unpacked media-player-info 3-0ubuntu1
2009-10-28 21:03:14 status half-configured media-player-info 3-0ubuntu1
2009-10-28 21:03:14 status installed media-player-info 3-0ubuntu1
2009-10-28 21:03:14 configure min12xxw 0.0.9-3ubuntu1 0.0.9-3ubuntu1
2009-10-28 21:03:14 status unpacked min12xxw 0.0.9-3ubuntu1
2009-10-28 21:03:14 status half-configured min12xxw 0.0.9-3ubuntu1
2009-10-28 21:03:14 status installed min12xxw 0.0.9-3ubuntu1
2009-10-28 21:03:14 configure modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:03:14 status unpacked modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:03:14 status unpacked modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:03:14 status half-configured modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:03:14 status installed modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1
2009-10-28 21:03:14 configure mtools 4.0.10-1 4.0.10-1
2009-10-28 21:03:14 status unpacked mtools 4.0.10-1
2009-10-28 21:03:14 status unpacked mtools 4.0.10-1
2009-10-28 21:03:14 status half-configured mtools 4.0.10-1
2009-10-28 21:03:14 status installed mtools 4.0.10-1
2009-10-28 21:03:14 configure nautilus-sendto 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:03:14 status unpacked nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:03:14 status half-configured nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:03:14 status installed nautilus-sendto 2.28.0-0ubuntu1
2009-10-28 21:03:14 configure samba-common 2:3.4.0-3ubuntu5 2:3.4.0-3ubuntu5
2009-10-28 21:03:14 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:14 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:14 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:14 status unpacked samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:14 status half-configured samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 status installed samba-common 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 configure samba-common-bin 2:3.4.0-3ubuntu5 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 status unpacked samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 status half-configured samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 update-alternatives: run with --install /usr/bin/nmblookup nmblookup /usr/bin/nmblookup.samba3 0 --slave /usr/share/man/man1/nmblookup.1.gz nmblookup.1.gz /usr/share/man/man1/nmblookup.samba3.1.gz
2009-10-28 21:03:15 update-alternatives: link group nmblookup updated to point to /usr/bin/nmblookup.samba3
2009-10-28 21:03:15 update-alternatives: run with --install /usr/bin/net net /usr/bin/net.samba3 10 --slave /usr/share/man/man8/net.8.gz net.8.gz /usr/share/man/man8/net.samba3.8.gz
2009-10-28 21:03:15 update-alternatives: link group net updated to point to /usr/bin/net.samba3
2009-10-28 21:03:15 update-alternatives: run with --install /usr/bin/testparm testparm /usr/bin/testparm.samba3 10 --slave /usr/share/man/man1/testparm.1.gz testparm.1.gz /usr/share/man/man1/testparm.samba3.1.gz
2009-10-28 21:03:15 update-alternatives: link group testparm updated to point to /usr/bin/testparm.samba3
2009-10-28 21:03:15 status installed samba-common-bin 2:3.4.0-3ubuntu5
2009-10-28 21:03:15 configure wpasupplicant 0.6.9-3ubuntu1 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status unpacked wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status half-configured wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 status installed wpasupplicant 0.6.9-3ubuntu1
2009-10-28 21:03:15 configure update-notifier-common 0.90 0.90
2009-10-28 21:03:15 status unpacked update-notifier-common 0.90
2009-10-28 21:03:15 status unpacked update-notifier-common 0.90
2009-10-28 21:03:15 status unpacked update-notifier-common 0.90
2009-10-28 21:03:15 status unpacked update-notifier-common 0.90
2009-10-28 21:03:15 status unpacked update-notifier-common 0.90
2009-10-28 21:03:15 status half-configured update-notifier-common 0.90
2009-10-28 21:03:15 status installed update-notifier-common 0.90
2009-10-28 21:03:15 configure network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status half-configured network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 status installed network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
2009-10-28 21:03:15 configure mobile-broadband-provider-info 20091009-0ubuntu1 20091009-0ubuntu1
2009-10-28 21:03:15 status unpacked mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:03:15 status half-configured mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:03:15 status installed mobile-broadband-provider-info 20091009-0ubuntu1
2009-10-28 21:03:15 configure network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 status unpacked network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 status half-configured network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 status installed network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1
2009-10-28 21:03:15 configure notify-osd-icons 0.3 0.3
2009-10-28 21:03:15 status unpacked notify-osd-icons 0.3
2009-10-28 21:03:15 status half-configured notify-osd-icons 0.3
2009-10-28 21:03:15 status installed notify-osd-icons 0.3
2009-10-28 21:03:15 configure nvidia-173-modaliases 173.14.20-0ubuntu5 173.14.20-0ubuntu5
2009-10-28 21:03:15 status unpacked nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:03:15 status half-configured nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:03:15 status installed nvidia-173-modaliases 173.14.20-0ubuntu5
2009-10-28 21:03:15 configure nvidia-185-modaliases 185.18.36-0ubuntu9 185.18.36-0ubuntu9
2009-10-28 21:03:15 status unpacked nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:03:15 status half-configured nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:03:15 status installed nvidia-185-modaliases 185.18.36-0ubuntu9
2009-10-28 21:03:15 configure nvidia-96-modaliases 96.43.13-0ubuntu6 96.43.13-0ubuntu6
2009-10-28 21:03:15 status unpacked nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:03:15 status half-configured nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:03:15 status installed nvidia-96-modaliases 96.43.13-0ubuntu6
2009-10-28 21:03:15 configure nvidia-common 0.2.15 0.2.15
2009-10-28 21:03:15 status unpacked nvidia-common 0.2.15
2009-10-28 21:03:15 status unpacked nvidia-common 0.2.15
2009-10-28 21:03:16 status unpacked nvidia-common 0.2.15
2009-10-28 21:03:16 status half-configured nvidia-common 0.2.15
2009-10-28 21:03:16 status installed nvidia-common 0.2.15
2009-10-28 21:03:16 configure python-virtkey 0.50ubuntu2 0.50ubuntu2
2009-10-28 21:03:16 status unpacked python-virtkey 0.50ubuntu2
2009-10-28 21:03:16 status half-configured python-virtkey 0.50ubuntu2
2009-10-28 21:03:16 status installed python-virtkey 0.50ubuntu2
2009-10-28 21:03:16 configure onboard 0.92.0-0ubuntu3 0.92.0-0ubuntu3
2009-10-28 21:03:16 status unpacked onboard 0.92.0-0ubuntu3
2009-10-28 21:03:16 status half-configured onboard 0.92.0-0ubuntu3
2009-10-28 21:03:17 status installed onboard 0.92.0-0ubuntu3
2009-10-28 21:03:17 configure openoffice.org-base-core 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-base-core 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-calc 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-calc 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure libwpg-0.1-1 0.1.3-1 0.1.3-1
2009-10-28 21:03:17 status unpacked libwpg-0.1-1 0.1.3-1
2009-10-28 21:03:17 status half-configured libwpg-0.1-1 0.1.3-1
2009-10-28 21:03:17 status installed libwpg-0.1-1 0.1.3-1
2009-10-28 21:03:17 configure openoffice.org-draw 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-draw 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-gtk 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-gtk 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-gnome 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-gnome 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-writer 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-writer 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-help-en-us 1:3.1.1-4ubuntu1 1:3.1.1-4ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-help-en-us 1:3.1.1-4ubuntu1
2009-10-28 21:03:17 configure openoffice.org-impress 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-impress 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openoffice.org-math 1:3.1.1-5ubuntu1 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status unpacked openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status half-configured openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 status installed openoffice.org-math 1:3.1.1-5ubuntu1
2009-10-28 21:03:17 configure openprinting-ppds 20090825-0ubuntu4 20090825-0ubuntu4
2009-10-28 21:03:17 status unpacked openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:03:17 status half-configured openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:03:17 status installed openprinting-ppds 20090825-0ubuntu4
2009-10-28 21:03:17 configure os-prober 1.35 1.35
2009-10-28 21:03:17 status unpacked os-prober 1.35
2009-10-28 21:03:17 status half-configured os-prober 1.35
2009-10-28 21:03:17 status installed os-prober 1.35
2009-10-28 21:03:17 configure pcmciautils 014-4ubuntu3 014-4ubuntu3
2009-10-28 21:03:17 status unpacked pcmciautils 014-4ubuntu3
2009-10-28 21:03:17 status unpacked pcmciautils 014-4ubuntu3
2009-10-28 21:03:17 status half-configured pcmciautils 014-4ubuntu3
2009-10-28 21:03:17 status installed pcmciautils 014-4ubuntu3
2009-10-28 21:03:17 configure pnm2ppa 1.12-16.2ubuntu2 1.12-16.2ubuntu2
2009-10-28 21:03:17 status unpacked pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:03:17 status half-configured pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:03:18 status installed pnm2ppa 1.12-16.2ubuntu2
2009-10-28 21:03:18 configure psfontmgr 0.11.10-0.2ubuntu1 0.11.10-0.2ubuntu1
2009-10-28 21:03:18 status unpacked psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:03:18 status half-configured psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:03:18 status installed psfontmgr 0.11.10-0.2ubuntu1
2009-10-28 21:03:18 configure pulseaudio-utils 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:03:18 status unpacked pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:03:18 status half-configured pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:03:18 status installed pulseaudio-utils 1:0.9.19-0ubuntu4
2009-10-28 21:03:18 configure pxljr 1.1-0ubuntu7 1.1-0ubuntu7
2009-10-28 21:03:18 status unpacked pxljr 1.1-0ubuntu7
2009-10-28 21:03:18 status half-configured pxljr 1.1-0ubuntu7
2009-10-28 21:03:18 status installed pxljr 1.1-0ubuntu7
2009-10-28 21:03:18 configure python-configglue 0.2dev-0ubuntu2 0.2dev-0ubuntu2
2009-10-28 21:03:18 status unpacked python-configglue 0.2dev-0ubuntu2
2009-10-28 21:03:18 status half-configured python-configglue 0.2dev-0ubuntu2
2009-10-28 21:03:19 status installed python-configglue 0.2dev-0ubuntu2
2009-10-28 21:03:19 configure python-crypto 2.0.1+dfsg1-4ubuntu1 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:03:19 status unpacked python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:03:19 status half-configured python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:03:19 status installed python-crypto 2.0.1+dfsg1-4ubuntu1
2009-10-28 21:03:19 configure python-cups 1.9.46-0ubuntu2 1.9.46-0ubuntu2
2009-10-28 21:03:19 status unpacked python-cups 1.9.46-0ubuntu2
2009-10-28 21:03:19 status half-configured python-cups 1.9.46-0ubuntu2
2009-10-28 21:03:19 status installed python-cups 1.9.46-0ubuntu2
2009-10-28 21:03:19 configure python-cupshelpers 1.1.12+git20090826-0ubuntu8 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:19 status unpacked python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:19 status half-configured python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:19 status installed python-cupshelpers 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:19 configure python-gtkhtml2 2.25.3-3ubuntu1 2.25.3-3ubuntu1
2009-10-28 21:03:19 status unpacked python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:03:19 status half-configured python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:03:19 status installed python-gtkhtml2 2.25.3-3ubuntu1
2009-10-28 21:03:19 configure python-openssl 0.9-1 0.9-1
2009-10-28 21:03:19 status unpacked python-openssl 0.9-1
2009-10-28 21:03:19 status half-configured python-openssl 0.9-1
2009-10-28 21:03:19 status installed python-openssl 0.9-1
2009-10-28 21:03:19 configure python-pam 0.4.2-12ubuntu3 0.4.2-12ubuntu3
2009-10-28 21:03:19 status unpacked python-pam 0.4.2-12ubuntu3
2009-10-28 21:03:19 status half-configured python-pam 0.4.2-12ubuntu3
2009-10-28 21:03:19 status installed python-pam 0.4.2-12ubuntu3
2009-10-28 21:03:19 configure python-papyon 0.4.3-1ubuntu1 0.4.3-1ubuntu1
2009-10-28 21:03:19 status unpacked python-papyon 0.4.3-1ubuntu1
2009-10-28 21:03:19 status half-configured python-papyon 0.4.3-1ubuntu1
2009-10-28 21:03:19 status installed python-papyon 0.4.3-1ubuntu1
2009-10-28 21:03:19 configure python-pyinotify 0.8.6-2ubuntu2 0.8.6-2ubuntu2
2009-10-28 21:03:19 status unpacked python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:03:19 status half-configured python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:03:19 status installed python-pyinotify 0.8.6-2ubuntu2
2009-10-28 21:03:19 configure python-rdflib 2.4.0-5ubuntu1 2.4.0-5ubuntu1
2009-10-28 21:03:19 status unpacked python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:03:19 status half-configured python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:03:20 status installed python-rdflib 2.4.0-5ubuntu1
2009-10-28 21:03:20 configure python-serial 2.3-1 2.3-1
2009-10-28 21:03:20 status unpacked python-serial 2.3-1
2009-10-28 21:03:20 status half-configured python-serial 2.3-1
2009-10-28 21:03:20 status installed python-serial 2.3-1
2009-10-28 21:03:20 configure python-sexy 0.1.9-1ubuntu2 0.1.9-1ubuntu2
2009-10-28 21:03:20 status unpacked python-sexy 0.1.9-1ubuntu2
2009-10-28 21:03:20 status half-configured python-sexy 0.1.9-1ubuntu2
2009-10-28 21:03:20 status installed python-sexy 0.1.9-1ubuntu2
2009-10-28 21:03:20 configure python-smbc 1.0.6-0ubuntu2 1.0.6-0ubuntu2
2009-10-28 21:03:20 status unpacked python-smbc 1.0.6-0ubuntu2
2009-10-28 21:03:20 status half-configured python-smbc 1.0.6-0ubuntu2
2009-10-28 21:03:20 status installed python-smbc 1.0.6-0ubuntu2
2009-10-28 21:03:20 configure python-telepathy 0.15.11-1 0.15.11-1
2009-10-28 21:03:20 status unpacked python-telepathy 0.15.11-1
2009-10-28 21:03:20 status half-configured python-telepathy 0.15.11-1
2009-10-28 21:03:20 status installed python-telepathy 0.15.11-1
2009-10-28 21:03:20 configure python-twisted-names 8.2.0-1ubuntu2 8.2.0-1ubuntu2
2009-10-28 21:03:20 status unpacked python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:03:20 status half-configured python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:03:21 status installed python-twisted-names 8.2.0-1ubuntu2
2009-10-28 21:03:21 configure python-twisted-web 8.2.0-2ubuntu1 8.2.0-2ubuntu1
2009-10-28 21:03:21 status unpacked python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:03:21 status half-configured python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:03:22 status installed python-twisted-web 8.2.0-2ubuntu1
2009-10-28 21:03:22 configure python-protobuf 2.0.3-2.2ubuntu2 2.0.3-2.2ubuntu2
2009-10-28 21:03:22 status unpacked python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:03:22 status half-configured python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:03:22 status installed python-protobuf 2.0.3-2.2ubuntu2
2009-10-28 21:03:22 configure python-ubuntuone-storageprotocol 1.0.0-0ubuntu1 1.0.0-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:03:22 status half-configured python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:03:22 status installed python-ubuntuone-storageprotocol 1.0.0-0ubuntu1
2009-10-28 21:03:22 configure xdg-utils 1.0.2-6.1 1.0.2-6.1
2009-10-28 21:03:22 status unpacked xdg-utils 1.0.2-6.1
2009-10-28 21:03:22 status half-configured xdg-utils 1.0.2-6.1
2009-10-28 21:03:22 status installed xdg-utils 1.0.2-6.1
2009-10-28 21:03:22 configure python-ubuntuone-client 1.0.2-0ubuntu1 1.0.2-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status unpacked python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status half-configured python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 status installed python-ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:03:22 configure python-webkit 1.1.5-1 1.1.5-1
2009-10-28 21:03:22 status unpacked python-webkit 1.1.5-1
2009-10-28 21:03:22 status half-configured python-webkit 1.1.5-1
2009-10-28 21:03:23 status installed python-webkit 1.1.5-1
2009-10-28 21:03:23 configure libpciaccess0 0.10.6-2ubuntu1 0.10.6-2ubuntu1
2009-10-28 21:03:23 status unpacked libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:03:23 status half-configured libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:03:23 status installed libpciaccess0 0.10.6-2ubuntu1
2009-10-28 21:03:23 configure radeontool 1.5+git76606164-0ubuntu2 1.5+git76606164-0ubuntu2
2009-10-28 21:03:23 status unpacked radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:03:23 status half-configured radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:03:23 status installed radeontool 1.5+git76606164-0ubuntu2
2009-10-28 21:03:23 configure raptor-utils 1.4.19-1 1.4.19-1
2009-10-28 21:03:23 status unpacked raptor-utils 1.4.19-1
2009-10-28 21:03:23 status half-configured raptor-utils 1.4.19-1
2009-10-28 21:03:23 status installed raptor-utils 1.4.19-1
2009-10-28 21:03:23 configure rdesktop 1.6.0-2ubuntu2 1.6.0-2ubuntu2
2009-10-28 21:03:23 status unpacked rdesktop 1.6.0-2ubuntu2
2009-10-28 21:03:23 status half-configured rdesktop 1.6.0-2ubuntu2
2009-10-28 21:03:23 status installed rdesktop 1.6.0-2ubuntu2
2009-10-28 21:03:23 configure redland-utils 1.0.9-2 1.0.9-2
2009-10-28 21:03:23 status unpacked redland-utils 1.0.9-2
2009-10-28 21:03:23 status half-configured redland-utils 1.0.9-2
2009-10-28 21:03:23 status installed redland-utils 1.0.9-2
2009-10-28 21:03:23 configure liblircclient0 0.8.6-0ubuntu2 0.8.6-0ubuntu2
2009-10-28 21:03:23 status unpacked liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:03:23 status half-configured liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:03:23 status installed liblircclient0 0.8.6-0ubuntu2
2009-10-28 21:03:23 configure update-inetd 4.31 4.31
2009-10-28 21:03:23 status unpacked update-inetd 4.31
2009-10-28 21:03:23 status half-configured update-inetd 4.31
2009-10-28 21:03:23 status installed update-inetd 4.31
2009-10-28 21:03:23 configure sane-utils 1.0.20-4ubuntu3 1.0.20-4ubuntu3
2009-10-28 21:03:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:23 status unpacked sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:23 status half-configured sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:24 status installed sane-utils 1.0.20-4ubuntu3
2009-10-28 21:03:24 configure screen-resolution-extra 0.11 0.11
2009-10-28 21:03:24 status unpacked screen-resolution-extra 0.11
2009-10-28 21:03:24 status unpacked screen-resolution-extra 0.11
2009-10-28 21:03:24 status half-configured screen-resolution-extra 0.11
2009-10-28 21:03:24 status installed screen-resolution-extra 0.11
2009-10-28 21:03:24 configure xscreensaver-data 5.08-0ubuntu5 5.08-0ubuntu5
2009-10-28 21:03:24 status unpacked xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:03:24 status unpacked xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:03:24 status half-configured xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:03:24 status installed xscreensaver-data 5.08-0ubuntu5
2009-10-28 21:03:24 configure screensaver-default-images 0.2-1 0.2-1
2009-10-28 21:03:24 status unpacked screensaver-default-images 0.2-1
2009-10-28 21:03:24 status half-configured screensaver-default-images 0.2-1
2009-10-28 21:03:24 status installed screensaver-default-images 0.2-1
2009-10-28 21:03:24 configure seahorse 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:03:24 status unpacked seahorse 2.28.1-0ubuntu1
2009-10-28 21:03:24 status unpacked seahorse 2.28.1-0ubuntu1
2009-10-28 21:03:24 status half-configured seahorse 2.28.1-0ubuntu1
2009-10-28 21:03:24 status installed seahorse 2.28.1-0ubuntu1
2009-10-28 21:03:24 configure smartdimmer 0.8b4-1ubuntu2 0.8b4-1ubuntu2
2009-10-28 21:03:24 status unpacked smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:03:24 status half-configured smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:03:24 status installed smartdimmer 0.8b4-1ubuntu2
2009-10-28 21:03:24 configure smbclient 2:3.4.0-3ubuntu5 2:3.4.0-3ubuntu5
2009-10-28 21:03:24 status unpacked smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:24 status half-configured smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:24 status installed smbclient 2:3.4.0-3ubuntu5
2009-10-28 21:03:24 configure python-aptdaemon 0.10+bzr264-0ubuntu1 0.10+bzr264-0ubuntu1
2009-10-28 21:03:24 status unpacked python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:24 status half-configured python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:24 status installed python-aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 configure python-aptdaemon-gtk 0.10+bzr264-0ubuntu1 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status unpacked python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status half-configured python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status installed python-aptdaemon-gtk 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 configure aptdaemon 0.10+bzr264-0ubuntu1 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status unpacked aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status unpacked aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status unpacked aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status half-configured aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 status installed aptdaemon 0.10+bzr264-0ubuntu1
2009-10-28 21:03:25 configure software-center 1.0.2 1.0.2
2009-10-28 21:03:25 status unpacked software-center 1.0.2
2009-10-28 21:03:25 status unpacked software-center 1.0.2
2009-10-28 21:03:25 status half-configured software-center 1.0.2
2009-10-28 21:03:30 status installed software-center 1.0.2
2009-10-28 21:03:30 configure splix 2.0.0-2ubuntu2 2.0.0-2ubuntu2
2009-10-28 21:03:30 status unpacked splix 2.0.0-2ubuntu2
2009-10-28 21:03:30 status half-configured splix 2.0.0-2ubuntu2
2009-10-28 21:03:30 status installed splix 2.0.0-2ubuntu2
2009-10-28 21:03:30 configure sreadahead 1.0-5 1.0-5
2009-10-28 21:03:30 status unpacked sreadahead 1.0-5
2009-10-28 21:03:30 status unpacked sreadahead 1.0-5
2009-10-28 21:03:30 status unpacked sreadahead 1.0-5
2009-10-28 21:03:30 status half-configured sreadahead 1.0-5
2009-10-28 21:03:30 status installed sreadahead 1.0-5
2009-10-28 21:03:30 configure ssh-askpass-gnome 1:5.1p1-6ubuntu2 1:5.1p1-6ubuntu2
2009-10-28 21:03:30 status unpacked ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:03:30 status half-configured ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:03:30 update-alternatives: run with --quiet --install /usr/bin/ssh-askpass ssh-askpass /usr/lib/openssh/gnome-ssh-askpass 30 --slave /usr/share/man/man1/ssh-askpass.1.gz ssh-askpass.1.gz /usr/share/man/man1/gnome-ssh-askpass.1.gz
2009-10-28 21:03:30 update-alternatives: link group ssh-askpass updated to point to /usr/lib/openssh/gnome-ssh-askpass
2009-10-28 21:03:30 status installed ssh-askpass-gnome 1:5.1p1-6ubuntu2
2009-10-28 21:03:30 configure syslinux 2:3.63+dfsg-2ubuntu3 2:3.63+dfsg-2ubuntu3
2009-10-28 21:03:30 status unpacked syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:03:30 status half-configured syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:03:30 status installed syslinux 2:3.63+dfsg-2ubuntu3
2009-10-28 21:03:30 configure system-config-printer-common 1.1.12+git20090826-0ubuntu8 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status unpacked system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status unpacked system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status half-configured system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status installed system-config-printer-common 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 configure system-config-printer-udev 1.1.12+git20090826-0ubuntu8 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status unpacked system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status half-configured system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 status installed system-config-printer-udev 1.1.12+git20090826-0ubuntu8
2009-10-28 21:03:30 configure tcl8.4 8.4.19-3 8.4.19-3
2009-10-28 21:03:30 status unpacked tcl8.4 8.4.19-3
2009-10-28 21:03:30 status half-configured tcl8.4 8.4.19-3
2009-10-28 21:03:31 update-alternatives: run with --install /usr/bin/tclsh tclsh /usr/bin/tclsh8.4 841 --slave /usr/share/man/man1/tclsh.1.gz tclsh.1 /usr/share/man/man1/tclsh8.4.1.gz
2009-10-28 21:03:31 update-alternatives: link group tclsh updated to point to /usr/bin/tclsh8.4
2009-10-28 21:03:31 status installed tcl8.4 8.4.19-3
2009-10-28 21:03:31 configure tcpd 7.6.q-16 7.6.q-16
2009-10-28 21:03:31 status unpacked tcpd 7.6.q-16
2009-10-28 21:03:31 status half-configured tcpd 7.6.q-16
2009-10-28 21:03:31 status installed tcpd 7.6.q-16
2009-10-28 21:03:31 configure telepathy-butterfly 0.5.2-0ubuntu1 0.5.2-0ubuntu1
2009-10-28 21:03:31 status unpacked telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:03:31 status half-configured telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:03:31 status installed telepathy-butterfly 0.5.2-0ubuntu1
2009-10-28 21:03:31 configure telepathy-gabble 0.8.7-1 0.8.7-1
2009-10-28 21:03:31 status unpacked telepathy-gabble 0.8.7-1
2009-10-28 21:03:31 status half-configured telepathy-gabble 0.8.7-1
2009-10-28 21:03:31 status installed telepathy-gabble 0.8.7-1
2009-10-28 21:03:31 configure telepathy-haze 0.3.2-1 0.3.2-1
2009-10-28 21:03:31 status unpacked telepathy-haze 0.3.2-1
2009-10-28 21:03:31 status half-configured telepathy-haze 0.3.2-1
2009-10-28 21:03:31 status installed telepathy-haze 0.3.2-1
2009-10-28 21:03:31 configure telepathy-idle 0.1.5-1 0.1.5-1
2009-10-28 21:03:31 status unpacked telepathy-idle 0.1.5-1
2009-10-28 21:03:31 status half-configured telepathy-idle 0.1.5-1
2009-10-28 21:03:31 status installed telepathy-idle 0.1.5-1
2009-10-28 21:03:31 configure telepathy-salut 0.3.10-1 0.3.10-1
2009-10-28 21:03:31 status unpacked telepathy-salut 0.3.10-1
2009-10-28 21:03:31 status half-configured telepathy-salut 0.3.10-1
2009-10-28 21:03:31 status installed telepathy-salut 0.3.10-1
2009-10-28 21:03:31 configure tk8.4 8.4.19-3 8.4.19-3
2009-10-28 21:03:31 status unpacked tk8.4 8.4.19-3
2009-10-28 21:03:31 status half-configured tk8.4 8.4.19-3
2009-10-28 21:03:31 update-alternatives: run with --install /usr/bin/wish wish /usr/bin/wish8.4 841 --slave /usr/share/man/man1/wish.1.gz wish.1 /usr/share/man/man1/wish8.4.1.gz
2009-10-28 21:03:31 update-alternatives: link group wish updated to point to /usr/bin/wish8.4
2009-10-28 21:03:31 status installed tk8.4 8.4.19-3
2009-10-28 21:03:31 configure toshset 1.75-1 1.75-1
2009-10-28 21:03:31 status unpacked toshset 1.75-1
2009-10-28 21:03:31 status half-configured toshset 1.75-1
2009-10-28 21:03:32 status installed toshset 1.75-1
2009-10-28 21:03:32 configure totem-common 2.28.1-0ubuntu4 2.28.1-0ubuntu4
2009-10-28 21:03:32 status unpacked totem-common 2.28.1-0ubuntu4
2009-10-28 21:03:32 status half-configured totem-common 2.28.1-0ubuntu4
2009-10-28 21:03:33 status installed totem-common 2.28.1-0ubuntu4
2009-10-28 21:03:33 configure transmission-common 1.75-0ubuntu2 1.75-0ubuntu2
2009-10-28 21:03:33 status unpacked transmission-common 1.75-0ubuntu2
2009-10-28 21:03:33 status half-configured transmission-common 1.75-0ubuntu2
2009-10-28 21:03:33 status installed transmission-common 1.75-0ubuntu2
2009-10-28 21:03:33 configure transmission-gtk 1.75-0ubuntu2 1.75-0ubuntu2
2009-10-28 21:03:33 status unpacked transmission-gtk 1.75-0ubuntu2
2009-10-28 21:03:33 status half-configured transmission-gtk 1.75-0ubuntu2
2009-10-28 21:03:33 status installed transmission-gtk 1.75-0ubuntu2
2009-10-28 21:03:33 configure tsclient 0.150-2ubuntu2 0.150-2ubuntu2
2009-10-28 21:03:33 status unpacked tsclient 0.150-2ubuntu2
2009-10-28 21:03:33 status half-configured tsclient 0.150-2ubuntu2
2009-10-28 21:03:33 status installed tsclient 0.150-2ubuntu2
2009-10-28 21:03:33 configure ttf-dejavu-core 2.29-2 2.29-2
2009-10-28 21:03:33 status unpacked ttf-dejavu-core 2.29-2
2009-10-28 21:03:33 status unpacked ttf-dejavu-core 2.29-2
2009-10-28 21:03:33 status half-configured ttf-dejavu-core 2.29-2
2009-10-28 21:03:42 status installed ttf-dejavu-core 2.29-2
2009-10-28 21:03:42 configure ttf-indic-fonts-core 1:0.5.4ubuntu2 1:0.5.4ubuntu2
2009-10-28 21:03:42 status unpacked ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:03:42 status unpacked ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:03:42 status half-configured ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:03:55 status installed ttf-indic-fonts-core 1:0.5.4ubuntu2
2009-10-28 21:03:55 configure ttf-kacst 2.0+mry-1 2.0+mry-1
2009-10-28 21:03:55 status unpacked ttf-kacst 2.0+mry-1
2009-10-28 21:03:55 status unpacked ttf-kacst 2.0+mry-1
2009-10-28 21:03:55 status half-configured ttf-kacst 2.0+mry-1
2009-10-28 21:04:04 status installed ttf-kacst 2.0+mry-1
2009-10-28 21:04:04 configure ttf-lao 0.0.20060226-2 0.0.20060226-2
2009-10-28 21:04:04 status unpacked ttf-lao 0.0.20060226-2
2009-10-28 21:04:04 status unpacked ttf-lao 0.0.20060226-2
2009-10-28 21:04:04 status half-configured ttf-lao 0.0.20060226-2
2009-10-28 21:04:12 status installed ttf-lao 0.0.20060226-2
2009-10-28 21:04:12 configure xfonts-encodings 1:1.0.2-3 1:1.0.2-3
2009-10-28 21:04:12 status unpacked xfonts-encodings 1:1.0.2-3
2009-10-28 21:04:12 status half-configured xfonts-encodings 1:1.0.2-3
2009-10-28 21:04:12 status installed xfonts-encodings 1:1.0.2-3
2009-10-28 21:04:12 configure xfonts-utils 1:7.4+1ubuntu1 1:7.4+1ubuntu1
2009-10-28 21:04:12 status unpacked xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:04:12 status half-configured xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:04:12 status installed xfonts-utils 1:7.4+1ubuntu1
2009-10-28 21:04:12 configure x-ttcidfont-conf 32 32
2009-10-28 21:04:12 status unpacked x-ttcidfont-conf 32
2009-10-28 21:04:12 status unpacked x-ttcidfont-conf 32
2009-10-28 21:04:12 status half-configured x-ttcidfont-conf 32
2009-10-28 21:04:15 status installed x-ttcidfont-conf 32
2009-10-28 21:04:15 configure ttf-thai-tlwg 1:0.4.13-1ubuntu1 1:0.4.13-1ubuntu1
2009-10-28 21:04:15 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:15 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:15 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:15 status unpacked ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:15 status half-configured ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:27 status installed ttf-thai-tlwg 1:0.4.13-1ubuntu1
2009-10-28 21:04:27 configure ttf-unfonts-core 1.0.1-7ubuntu1 1.0.1-7ubuntu1
2009-10-28 21:04:27 status unpacked ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:04:27 status unpacked ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:04:27 status half-configured ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:04:36 status installed ttf-unfonts-core 1.0.1-7ubuntu1
2009-10-28 21:04:36 configure ttf-vlgothic 20090612-2 20090612-2
2009-10-28 21:04:36 status unpacked ttf-vlgothic 20090612-2
2009-10-28 21:04:36 status unpacked ttf-vlgothic 20090612-2
2009-10-28 21:04:36 status half-configured ttf-vlgothic 20090612-2
2009-10-28 21:04:36 update-alternatives: run with --install /usr/share/fonts/truetype/ttf-japanese-gothic.ttf ttf-japanese-gothic.ttf /usr/share/fonts/truetype/vlgothic/VL-Gothic-Regular.ttf 60
2009-10-28 21:04:36 update-alternatives: link group ttf-japanese-gothic.ttf updated to point to /usr/share/fonts/truetype/vlgothic/VL-Gothic-Regular.ttf
2009-10-28 21:04:45 status installed ttf-vlgothic 20090612-2
2009-10-28 21:04:45 configure ubuntu-wallpapers 0.30 0.30
2009-10-28 21:04:45 status unpacked ubuntu-wallpapers 0.30
2009-10-28 21:04:45 status half-configured ubuntu-wallpapers 0.30
2009-10-28 21:04:46 status installed ubuntu-wallpapers 0.30
2009-10-28 21:04:46 configure ubuntu-artwork 51 51
2009-10-28 21:04:46 status unpacked ubuntu-artwork 51
2009-10-28 21:04:46 status half-configured ubuntu-artwork 51
2009-10-28 21:04:46 status installed ubuntu-artwork 51
2009-10-28 21:04:46 configure cups-bsd 1.4.1-5ubuntu2 1.4.1-5ubuntu2
2009-10-28 21:04:46 status unpacked cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:04:46 status half-configured cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:04:46 status installed cups-bsd 1.4.1-5ubuntu2
2009-10-28 21:04:46 configure dcraw 8.86-1 8.86-1
2009-10-28 21:04:46 status unpacked dcraw 8.86-1
2009-10-28 21:04:46 status half-configured dcraw 8.86-1
2009-10-28 21:04:46 status installed dcraw 8.86-1
2009-10-28 21:04:46 configure gnome-system-tools 2.28.1-0ubuntu2 2.28.1-0ubuntu2
2009-10-28 21:04:46 status unpacked gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:04:46 status unpacked gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:04:46 status half-configured gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:04:46 status installed gnome-system-tools 2.28.1-0ubuntu2
2009-10-28 21:04:46 configure ubuntu-sounds 0.12 0.12
2009-10-28 21:04:46 status unpacked ubuntu-sounds 0.12
2009-10-28 21:04:46 status half-configured ubuntu-sounds 0.12
2009-10-28 21:04:46 status installed ubuntu-sounds 0.12
2009-10-28 21:04:46 configure update-manager 1:0.126.6 1:0.126.6
2009-10-28 21:04:46 status unpacked update-manager 1:0.126.6
2009-10-28 21:04:46 status half-configured update-manager 1:0.126.6
2009-10-28 21:04:47 status installed update-manager 1:0.126.6
2009-10-28 21:04:47 configure update-notifier 0.90 0.90
2009-10-28 21:04:47 status unpacked update-notifier 0.90
2009-10-28 21:04:47 status unpacked update-notifier 0.90
2009-10-28 21:04:47 status half-configured update-notifier 0.90
2009-10-28 21:04:48 status installed update-notifier 0.90
2009-10-28 21:04:48 configure usplash 0.5.49 0.5.49
2009-10-28 21:04:48 status unpacked usplash 0.5.49
2009-10-28 21:04:48 status unpacked usplash 0.5.49
2009-10-28 21:04:48 status unpacked usplash 0.5.49
2009-10-28 21:04:48 status unpacked usplash 0.5.49
2009-10-28 21:04:48 status half-configured usplash 0.5.49
2009-10-28 21:04:48 status installed usplash 0.5.49
2009-10-28 21:04:48 configure usplash-theme-ubuntu 0.27 0.27
2009-10-28 21:04:48 status unpacked usplash-theme-ubuntu 0.27
2009-10-28 21:04:48 status half-configured usplash-theme-ubuntu 0.27
2009-10-28 21:04:48 update-alternatives: run with --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu.so 10
2009-10-28 21:04:48 update-alternatives: link group usplash-artwork.so updated to point to /usr/lib/usplash/usplash-theme-ubuntu.so
2009-10-28 21:04:48 status installed usplash-theme-ubuntu 0.27
2009-10-28 21:04:48 configure wireless-tools 29-2ubuntu6 29-2ubuntu6
2009-10-28 21:04:48 status unpacked wireless-tools 29-2ubuntu6
2009-10-28 21:04:48 status unpacked wireless-tools 29-2ubuntu6
2009-10-28 21:04:48 status unpacked wireless-tools 29-2ubuntu6
2009-10-28 21:04:48 status half-configured wireless-tools 29-2ubuntu6
2009-10-28 21:04:48 status installed wireless-tools 29-2ubuntu6
2009-10-28 21:04:48 configure xdg-user-dirs 0.11-0ubuntu2 0.11-0ubuntu2
2009-10-28 21:04:48 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 status unpacked xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 status half-configured xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 status installed xdg-user-dirs 0.11-0ubuntu2
2009-10-28 21:04:48 configure xdg-user-dirs-gtk 0.8-1 0.8-1
2009-10-28 21:04:48 status unpacked xdg-user-dirs-gtk 0.8-1
2009-10-28 21:04:48 status unpacked xdg-user-dirs-gtk 0.8-1
2009-10-28 21:04:48 status half-configured xdg-user-dirs-gtk 0.8-1
2009-10-28 21:04:48 status installed xdg-user-dirs-gtk 0.8-1
2009-10-28 21:04:48 configure xserver-common 2:1.6.4-2ubuntu4 2:1.6.4-2ubuntu4
2009-10-28 21:04:48 status unpacked xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:04:48 status half-configured xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:04:48 status installed xserver-common 2:1.6.4-2ubuntu4
2009-10-28 21:04:48 configure libgl1-mesa-dri 7.6.0-1ubuntu4 7.6.0-1ubuntu4
2009-10-28 21:04:48 status unpacked libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:04:48 status half-configured libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:04:48 status installed libgl1-mesa-dri 7.6.0-1ubuntu4
2009-10-28 21:04:48 configure xfonts-base 1:1.0.0-6 1:1.0.0-6
2009-10-28 21:04:48 status unpacked xfonts-base 1:1.0.0-6
2009-10-28 21:04:48 status unpacked xfonts-base 1:1.0.0-6
2009-10-28 21:04:48 status half-configured xfonts-base 1:1.0.0-6
2009-10-28 21:04:48 status installed xfonts-base 1:1.0.0-6
2009-10-28 21:04:48 configure xfonts-100dpi 1:1.0.0-4build1 1:1.0.0-4build1
2009-10-28 21:04:48 status unpacked xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:04:48 status unpacked xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:04:48 status half-configured xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:04:48 status installed xfonts-100dpi 1:1.0.0-4build1
2009-10-28 21:04:48 configure xfonts-75dpi 1:1.0.0-4build1 1:1.0.0-4build1
2009-10-28 21:04:48 status unpacked xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:04:48 status unpacked xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:04:48 status half-configured xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:04:49 status installed xfonts-75dpi 1:1.0.0-4build1
2009-10-28 21:04:49 configure xinit 1.1.1-1 1.1.1-1
2009-10-28 21:04:49 status unpacked xinit 1.1.1-1
2009-10-28 21:04:49 status unpacked xinit 1.1.1-1
2009-10-28 21:04:49 status unpacked xinit 1.1.1-1
2009-10-28 21:04:49 status half-configured xinit 1.1.1-1
2009-10-28 21:04:49 status installed xinit 1.1.1-1
2009-10-28 21:04:49 configure xorg-docs-core 1:1.4-5 1:1.4-5
2009-10-28 21:04:49 status unpacked xorg-docs-core 1:1.4-5
2009-10-28 21:04:49 status half-configured xorg-docs-core 1:1.4-5
2009-10-28 21:04:49 status installed xorg-docs-core 1:1.4-5
2009-10-28 21:04:49 configure xterm 243-1ubuntu1 243-1ubuntu1
2009-10-28 21:04:49 status unpacked xterm 243-1ubuntu1
2009-10-28 21:04:49 status unpacked xterm 243-1ubuntu1
2009-10-28 21:04:49 status unpacked xterm 243-1ubuntu1
2009-10-28 21:04:49 status unpacked xterm 243-1ubuntu1
2009-10-28 21:04:49 status unpacked xterm 243-1ubuntu1
2009-10-28 21:04:49 status half-configured xterm 243-1ubuntu1
2009-10-28 21:04:49 update-alternatives: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/xterm 20 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/xterm.1.gz
2009-10-28 21:04:49 update-alternatives: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/uxterm 20 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/uxterm.1.gz
2009-10-28 21:04:49 update-alternatives: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/koi8rxterm 20 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/koi8rxterm.1.gz
2009-10-28 21:04:49 update-alternatives: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/lxterm 30 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/lxterm.1.gz
2009-10-28 21:04:49 status installed xterm 243-1ubuntu1
2009-10-28 21:04:49 configure xinput 1.4.2-1 1.4.2-1
2009-10-28 21:04:49 status unpacked xinput 1.4.2-1
2009-10-28 21:04:49 status half-configured xinput 1.4.2-1
2009-10-28 21:04:49 status installed xinput 1.4.2-1
2009-10-28 21:04:49 configure xscreensaver-gl 5.08-0ubuntu5 5.08-0ubuntu5
2009-10-28 21:04:49 status unpacked xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:04:49 status unpacked xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:04:49 status half-configured xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:04:49 status installed xscreensaver-gl 5.08-0ubuntu5
2009-10-28 21:04:49 configure ubuntu-xsplash-artwork 0.8.4-0ubuntu1 0.8.4-0ubuntu1
2009-10-28 21:04:49 status unpacked ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:04:49 status half-configured ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:04:49 status installed ubuntu-xsplash-artwork 0.8.4-0ubuntu1
2009-10-28 21:04:49 configure xsplash 0.8.4-0ubuntu1 0.8.4-0ubuntu1
2009-10-28 21:04:49 status unpacked xsplash 0.8.4-0ubuntu1
2009-10-28 21:04:49 status unpacked xsplash 0.8.4-0ubuntu1
2009-10-28 21:04:49 status half-configured xsplash 0.8.4-0ubuntu1
2009-10-28 21:04:49 status installed xsplash 0.8.4-0ubuntu1
2009-10-28 21:04:49 configure ubuntuone-client 1.0.2-0ubuntu1 1.0.2-0ubuntu1
2009-10-28 21:04:49 status unpacked ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:04:49 status half-configured ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:04:49 status installed ubuntuone-client 1.0.2-0ubuntu1
2009-10-28 21:04:49 configure ubuntuone-client-gnome 1.0.2-0ubuntu1 1.0.2-0ubuntu1
2009-10-28 21:04:49 status unpacked ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:04:49 status half-configured ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:04:49 status installed ubuntuone-client-gnome 1.0.2-0ubuntu1
2009-10-28 21:04:49 configure usb-creator-common 0.2.12 0.2.12
2009-10-28 21:04:49 status unpacked usb-creator-common 0.2.12
2009-10-28 21:04:49 status unpacked usb-creator-common 0.2.12
2009-10-28 21:04:49 status half-configured usb-creator-common 0.2.12
2009-10-28 21:04:49 status installed usb-creator-common 0.2.12
2009-10-28 21:04:49 configure vbetool 1.1-2 1.1-2
2009-10-28 21:04:49 status unpacked vbetool 1.1-2
2009-10-28 21:04:49 status half-configured vbetool 1.1-2
2009-10-28 21:04:49 status installed vbetool 1.1-2
2009-10-28 21:04:49 configure vino 2.28.1-0ubuntu2 2.28.1-0ubuntu2
2009-10-28 21:04:49 status unpacked vino 2.28.1-0ubuntu2
2009-10-28 21:04:49 status unpacked vino 2.28.1-0ubuntu2
2009-10-28 21:04:49 status half-configured vino 2.28.1-0ubuntu2
2009-10-28 21:04:49 status installed vino 2.28.1-0ubuntu2
2009-10-28 21:04:49 configure xcursor-themes 1.0.1-5ubuntu1 1.0.1-5ubuntu1
2009-10-28 21:04:49 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:49 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 status unpacked xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 status half-configured xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/core.theme 30
2009-10-28 21:04:50 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/redglass.theme 20
2009-10-28 21:04:50 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/whiteglass.theme 20
2009-10-28 21:04:50 update-alternatives: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/handhelds.theme 20
2009-10-28 21:04:50 status installed xcursor-themes 1.0.1-5ubuntu1
2009-10-28 21:04:50 configure xfonts-scalable 1:1.0.0-7 1:1.0.0-7
2009-10-28 21:04:50 status unpacked xfonts-scalable 1:1.0.0-7
2009-10-28 21:04:50 status unpacked xfonts-scalable 1:1.0.0-7
2009-10-28 21:04:50 status half-configured xfonts-scalable 1:1.0.0-7
2009-10-28 21:04:50 status installed xfonts-scalable 1:1.0.0-7
2009-10-28 21:04:50 configure xsane-common 0.996-2ubuntu1 0.996-2ubuntu1
2009-10-28 21:04:50 status unpacked xsane-common 0.996-2ubuntu1
2009-10-28 21:04:50 status half-configured xsane-common 0.996-2ubuntu1
2009-10-28 21:04:50 status installed xsane-common 0.996-2ubuntu1
2009-10-28 21:04:50 configure xsane 0.996-2ubuntu1 0.996-2ubuntu1
2009-10-28 21:04:50 status unpacked xsane 0.996-2ubuntu1
2009-10-28 21:04:50 status half-configured xsane 0.996-2ubuntu1
2009-10-28 21:04:50 status installed xsane 0.996-2ubuntu1
2009-10-28 21:04:50 configure brltty 4.0-7ubuntu2 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:50 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status half-configured brltty 4.0-7ubuntu2
2009-10-28 21:04:51 status installed brltty 4.0-7ubuntu2
2009-10-28 21:04:51 configure brltty-x11 4.0-7ubuntu2 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty-x11 4.0-7ubuntu2
2009-10-28 21:04:51 status unpacked brltty-x11 4.0-7ubuntu2
2009-10-28 21:04:51 status half-configured brltty-x11 4.0-7ubuntu2
2009-10-28 21:04:51 status installed brltty-x11 4.0-7ubuntu2
2009-10-28 21:04:51 configure evolution-documentation-en 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:04:51 status unpacked evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:04:51 status half-configured evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:04:51 status installed evolution-documentation-en 2.28.1-0ubuntu1
2009-10-28 21:04:51 configure fglrx-modaliases 2:8.660-0ubuntu4 2:8.660-0ubuntu4
2009-10-28 21:04:51 status unpacked fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:04:51 status half-configured fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:04:51 status installed fglrx-modaliases 2:8.660-0ubuntu4
2009-10-28 21:04:51 configure latex-xft-fonts 0.1-8 0.1-8
2009-10-28 21:04:51 status unpacked latex-xft-fonts 0.1-8
2009-10-28 21:04:51 status unpacked latex-xft-fonts 0.1-8
2009-10-28 21:04:51 status half-configured latex-xft-fonts 0.1-8
2009-10-28 21:05:02 status installed latex-xft-fonts 0.1-8
2009-10-28 21:05:02 configure liblouis-data 1.7.0-1ubuntu1 1.7.0-1ubuntu1
2009-10-28 21:05:02 status unpacked liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:05:02 status half-configured liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:05:02 status installed liblouis-data 1.7.0-1ubuntu1
2009-10-28 21:05:02 configure liblouis0 1.7.0-1ubuntu1 1.7.0-1ubuntu1
2009-10-28 21:05:02 status unpacked liblouis0 1.7.0-1ubuntu1
2009-10-28 21:05:02 status half-configured liblouis0 1.7.0-1ubuntu1
2009-10-28 21:05:02 status installed liblouis0 1.7.0-1ubuntu1
2009-10-28 21:05:02 configure protobuf-compiler 2.0.3-2.2ubuntu2 2.0.3-2.2ubuntu2
2009-10-28 21:05:02 status unpacked protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:05:02 status half-configured protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:05:02 status installed protobuf-compiler 2.0.3-2.2ubuntu2
2009-10-28 21:05:02 configure python-louis 1.7.0-1ubuntu1 1.7.0-1ubuntu1
2009-10-28 21:05:02 status unpacked python-louis 1.7.0-1ubuntu1
2009-10-28 21:05:02 status half-configured python-louis 1.7.0-1ubuntu1
2009-10-28 21:05:02 status installed python-louis 1.7.0-1ubuntu1
2009-10-28 21:05:02 configure xfonts-mathml 2 2
2009-10-28 21:05:02 status unpacked xfonts-mathml 2
2009-10-28 21:05:02 status unpacked xfonts-mathml 2
2009-10-28 21:05:02 status unpacked xfonts-mathml 2
2009-10-28 21:05:02 status half-configured xfonts-mathml 2
2009-10-28 21:05:11 status installed xfonts-mathml 2
2009-10-28 21:05:11 trigproc initramfs-tools 0.92bubuntu53 0.92bubuntu53
2009-10-28 21:05:11 status half-configured initramfs-tools 0.92bubuntu53
2009-10-28 21:05:11 status installed apparmor 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status installed initramfs-tools 0.92bubuntu53
2009-10-28 21:05:23 configure apparmor-utils 2.3.1+1403-0ubuntu27 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status unpacked apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status unpacked apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status unpacked apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status half-configured apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 status installed apparmor-utils 2.3.1+1403-0ubuntu27
2009-10-28 21:05:23 configure libmono-corlib2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status unpacked libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status half-configured libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status installed libmono-corlib2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 configure libmono-cairo2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status unpacked libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status half-configured libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status installed libmono-cairo2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 configure firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:23 status unpacked firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:23 status half-configured firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:23 status installed firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:23 configure indicator-messages 0.2.6-0ubuntu1 0.2.6-0ubuntu1
2009-10-28 21:05:23 status unpacked indicator-messages 0.2.6-0ubuntu1
2009-10-28 21:05:23 status half-configured indicator-messages 0.2.6-0ubuntu1
2009-10-28 21:05:23 status installed indicator-messages 0.2.6-0ubuntu1
2009-10-28 21:05:23 configure pulseaudio-module-udev 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:23 status unpacked pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 21:05:23 status half-configured pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 21:05:23 status installed pulseaudio-module-udev 1:0.9.19-0ubuntu4
2009-10-28 21:05:23 configure libmagickcore2 7:6.5.1.0-1.1ubuntu3 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status unpacked libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status half-configured libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status installed libmagickcore2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 configure libmagickwand2 7:6.5.1.0-1.1ubuntu3 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status unpacked libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status half-configured libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 status installed libmagickwand2 7:6.5.1.0-1.1ubuntu3
2009-10-28 21:05:23 configure libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status unpacked libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status half-configured libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 status installed libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:23 configure obex-data-server 0.4.4-2build1 0.4.4-2build1
2009-10-28 21:05:23 status unpacked obex-data-server 0.4.4-2build1
2009-10-28 21:05:23 status unpacked obex-data-server 0.4.4-2build1
2009-10-28 21:05:23 status unpacked obex-data-server 0.4.4-2build1
2009-10-28 21:05:23 status half-configured obex-data-server 0.4.4-2build1
2009-10-28 21:05:23 status installed obex-data-server 0.4.4-2build1
2009-10-28 21:05:23 configure totem 2.28.1-0ubuntu4 2.28.1-0ubuntu4
2009-10-28 21:05:23 status unpacked totem 2.28.1-0ubuntu4
2009-10-28 21:05:23 status half-configured totem 2.28.1-0ubuntu4
2009-10-28 21:05:23 status installed totem 2.28.1-0ubuntu4
2009-10-28 21:05:23 configure totem-plugins 2.28.1-0ubuntu4 2.28.1-0ubuntu4
2009-10-28 21:05:23 status unpacked totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:05:23 status half-configured totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:05:24 status installed totem-plugins 2.28.1-0ubuntu4
2009-10-28 21:05:24 configure totem-mozilla 2.28.1-0ubuntu4 2.28.1-0ubuntu4
2009-10-28 21:05:24 status unpacked totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:05:24 status half-configured totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:05:24 status installed totem-mozilla 2.28.1-0ubuntu4
2009-10-28 21:05:24 configure xserver-xorg-core 2:1.6.4-2ubuntu4 2:1.6.4-2ubuntu4
2009-10-28 21:05:24 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:05:24 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:05:24 status half-configured xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:05:24 status installed xserver-xorg-core 2:1.6.4-2ubuntu4
2009-10-28 21:05:24 configure foomatic-db 20090825-0ubuntu4 20090825-0ubuntu4
2009-10-28 21:05:24 status unpacked foomatic-db 20090825-0ubuntu4
2009-10-28 21:05:24 status half-configured foomatic-db 20090825-0ubuntu4
2009-10-28 21:05:24 status installed foomatic-db 20090825-0ubuntu4
2009-10-28 21:05:24 configure gamin 0.1.10-1ubuntu2 0.1.10-1ubuntu2
2009-10-28 21:05:24 status unpacked gamin 0.1.10-1ubuntu2
2009-10-28 21:05:24 status unpacked gamin 0.1.10-1ubuntu2
2009-10-28 21:05:24 status half-configured gamin 0.1.10-1ubuntu2
2009-10-28 21:05:24 status installed gamin 0.1.10-1ubuntu2
2009-10-28 21:05:24 configure desktopcouch 0.5-0ubuntu1 0.5-0ubuntu1
2009-10-28 21:05:24 status unpacked desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 status unpacked desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 status half-configured desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 status installed desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 configure python-desktopcouch 0.5-0ubuntu1 0.5-0ubuntu1
2009-10-28 21:05:24 status unpacked python-desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 status half-configured python-desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 status installed python-desktopcouch 0.5-0ubuntu1
2009-10-28 21:05:24 configure mono-2.0-gac 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:24 status unpacked mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:24 status half-configured mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:24 status installed mono-2.0-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:24 configure mono-gac 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:24 status unpacked mono-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:24 status half-configured mono-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:34 update-alternatives: run with --install /usr/bin/cli-gacutil global-assembly-cache-tool /usr/bin/gacutil 10 --slave /usr/share/man/man1/cli-gacutil.1.gz cli-gacutil.1.gz /usr/share/man/man1/gacutil.1.gz
2009-10-28 21:05:34 update-alternatives: link group global-assembly-cache-tool updated to point to /usr/bin/gacutil
2009-10-28 21:05:34 status installed mono-gac 2.4.2.3+dfsg-2
2009-10-28 21:05:34 configure mono-runtime 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status unpacked mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 status half-configured mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 update-alternatives: run with --install /usr/bin/cli cli /usr/bin/mono 10 --slave /usr/share/man/man1/cli.1.gz cli.1.gz /usr/share/man/man1/mono.1.gz
2009-10-28 21:05:34 update-alternatives: link group cli updated to point to /usr/bin/mono
2009-10-28 21:05:34 status installed mono-runtime 2.4.2.3+dfsg-2
2009-10-28 21:05:34 configure firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status half-configured firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox-3.5 40
2009-10-28 21:05:34 update-alternatives: link group x-www-browser updated to point to /usr/bin/firefox-3.5
2009-10-28 21:05:34 status installed firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 configure firefox 3.5.3+build1+nobinonly-0ubuntu6 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status unpacked firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status half-configured firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 status installed firefox 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:34 configure pulseaudio 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status unpacked pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:34 status half-configured pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status installed pulseaudio 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 configure libcanberra-pulse 0.15-0ubuntu7 0.15-0ubuntu7
2009-10-28 21:05:35 status unpacked libcanberra-pulse 0.15-0ubuntu7
2009-10-28 21:05:35 status half-configured libcanberra-pulse 0.15-0ubuntu7
2009-10-28 21:05:35 status installed libcanberra-pulse 0.15-0ubuntu7
2009-10-28 21:05:35 configure pulseaudio-esound-compat 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status unpacked pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status half-configured pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status installed pulseaudio-esound-compat 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 configure pulseaudio-module-gconf 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status unpacked pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status half-configured pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status installed pulseaudio-module-gconf 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 configure pulseaudio-module-x11 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status unpacked pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status half-configured pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 status installed pulseaudio-module-x11 1:0.9.19-0ubuntu4
2009-10-28 21:05:35 configure ubufox 0.8-0ubuntu1 0.8-0ubuntu1
2009-10-28 21:05:35 status unpacked ubufox 0.8-0ubuntu1
2009-10-28 21:05:35 status unpacked ubufox 0.8-0ubuntu1
2009-10-28 21:05:35 status half-configured ubufox 0.8-0ubuntu1
2009-10-28 21:05:35 status installed ubufox 0.8-0ubuntu1
2009-10-28 21:05:35 configure xserver-xorg-video-apm 1:1.2.1-2 1:1.2.1-2
2009-10-28 21:05:35 status unpacked xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:05:35 status half-configured xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:05:35 status installed xserver-xorg-video-apm 1:1.2.1-2
2009-10-28 21:05:35 configure xserver-xorg-video-ark 1:0.7.1-2 1:0.7.1-2
2009-10-28 21:05:35 status unpacked xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:05:35 status half-configured xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:05:35 status installed xserver-xorg-video-ark 1:0.7.1-2
2009-10-28 21:05:35 configure xserver-xorg-video-r128 6.8.1-1 6.8.1-1
2009-10-28 21:05:35 status unpacked xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:05:35 status half-configured xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:05:35 status installed xserver-xorg-video-r128 6.8.1-1
2009-10-28 21:05:35 configure xserver-xorg-video-mach64 6.8.2-1 6.8.2-1
2009-10-28 21:05:35 status unpacked xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:05:35 status half-configured xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:05:35 status installed xserver-xorg-video-mach64 6.8.2-1
2009-10-28 21:05:35 configure xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status unpacked xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status half-configured xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status installed xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 configure xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status unpacked xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status half-configured xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 status installed xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1
2009-10-28 21:05:35 configure xserver-xorg-video-chips 1:1.2.1-3 1:1.2.1-3
2009-10-28 21:05:35 status unpacked xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:05:35 status half-configured xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:05:35 status installed xserver-xorg-video-chips 1:1.2.1-3
2009-10-28 21:05:35 configure xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2 1:1.3.1-1ubuntu2
2009-10-28 21:05:35 status unpacked xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:05:35 status half-configured xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:05:35 status installed xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2
2009-10-28 21:05:35 configure xserver-xorg-video-fbdev 1:0.4.0-4 1:0.4.0-4
2009-10-28 21:05:35 status unpacked xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:05:35 status half-configured xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:05:35 status installed xserver-xorg-video-fbdev 1:0.4.0-4
2009-10-28 21:05:35 configure xserver-xorg-video-geode 2.11.6-1 2.11.6-1
2009-10-28 21:05:35 status unpacked xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:05:35 status half-configured xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:05:36 status installed xserver-xorg-video-geode 2.11.6-1
2009-10-28 21:05:36 configure xserver-xorg-video-i128 1:1.3.2-1 1:1.3.2-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:05:36 status installed xserver-xorg-video-i128 1:1.3.2-1
2009-10-28 21:05:36 configure xserver-xorg-video-i740 1:1.3.0-1 1:1.3.0-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:05:36 status installed xserver-xorg-video-i740 1:1.3.0-1
2009-10-28 21:05:36 configure xserver-xorg-video-intel 2:2.9.0-1ubuntu2 2:2.9.0-1ubuntu2
2009-10-28 21:05:36 status unpacked xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:05:36 status half-configured xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:05:36 status installed xserver-xorg-video-intel 2:2.9.0-1ubuntu2
2009-10-28 21:05:36 configure xserver-xorg-video-mga 1:1.4.11.dfsg-1 1:1.4.11.dfsg-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:05:36 status installed xserver-xorg-video-mga 1:1.4.11.dfsg-1
2009-10-28 21:05:36 configure xserver-xorg-video-neomagic 1:1.2.3-1 1:1.2.3-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:05:36 status installed xserver-xorg-video-neomagic 1:1.2.3-1
2009-10-28 21:05:36 configure xserver-xorg-video-nv 1:2.1.14-2ubuntu3 1:2.1.14-2ubuntu3
2009-10-28 21:05:36 status unpacked xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:05:36 status half-configured xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:05:36 status installed xserver-xorg-video-nv 1:2.1.14-2ubuntu3
2009-10-28 21:05:36 configure xserver-xorg-video-rendition 1:4.2.1-1 1:4.2.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-rendition 1:4.2.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-s3 1:0.6.2-1 1:0.6.2-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:05:36 status installed xserver-xorg-video-s3 1:0.6.2-1
2009-10-28 21:05:36 configure xserver-xorg-video-s3virge 1:1.10.2-2 1:1.10.2-2
2009-10-28 21:05:36 status unpacked xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:05:36 status half-configured xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:05:36 status installed xserver-xorg-video-s3virge 1:1.10.2-2
2009-10-28 21:05:36 configure xserver-xorg-video-savage 1:2.3.0-1ubuntu1 1:2.3.0-1ubuntu1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:05:36 status installed xserver-xorg-video-savage 1:2.3.0-1ubuntu1
2009-10-28 21:05:36 configure xserver-xorg-video-siliconmotion 1:1.7.2-1 1:1.7.2-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:05:36 status installed xserver-xorg-video-siliconmotion 1:1.7.2-1
2009-10-28 21:05:36 configure xserver-xorg-video-sis 1:0.10.1-2 1:0.10.1-2
2009-10-28 21:05:36 status unpacked xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:05:36 status half-configured xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:05:36 status installed xserver-xorg-video-sis 1:0.10.1-2
2009-10-28 21:05:36 configure xserver-xorg-video-sisusb 1:0.9.1-1 1:0.9.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-sisusb 1:0.9.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-tdfx 1:1.4.1-1 1:1.4.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-tdfx 1:1.4.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-trident 1:1.3.1-1 1:1.3.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-trident 1:1.3.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-tseng 1:1.2.1-1 1:1.2.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-tseng 1:1.2.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-vesa 1:2.2.1-1 1:2.2.1-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:05:36 status installed xserver-xorg-video-vesa 1:2.2.1-1
2009-10-28 21:05:36 configure xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:05:36 status installed xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1
2009-10-28 21:05:36 configure xserver-xorg-video-voodoo 1:1.2.2-1 1:1.2.2-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:05:36 status installed xserver-xorg-video-voodoo 1:1.2.2-1
2009-10-28 21:05:36 configure xserver-xorg-video-vmware 1:10.16.7-1 1:10.16.7-1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:05:36 status installed xserver-xorg-video-vmware 1:10.16.7-1
2009-10-28 21:05:36 configure xserver-xorg-video-v4l 1:0.2.0-3ubuntu1 1:0.2.0-3ubuntu1
2009-10-28 21:05:36 status unpacked xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:05:36 status half-configured xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:05:36 status installed xserver-xorg-video-v4l 1:0.2.0-3ubuntu1
2009-10-28 21:05:36 configure xserver-xorg-video-all 1:7.4+3ubuntu7 1:7.4+3ubuntu7
2009-10-28 21:05:36 status unpacked xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 status half-configured xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 status installed xserver-xorg-video-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 configure xserver-xorg-input-evdev 1:2.2.5-1ubuntu6 1:2.2.5-1ubuntu6
2009-10-28 21:05:36 status unpacked xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:05:36 status half-configured xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:05:36 status installed xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
2009-10-28 21:05:36 configure xserver-xorg-input-synaptics 1.1.2-1ubuntu7 1.1.2-1ubuntu7
2009-10-28 21:05:36 status unpacked xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:05:36 status half-configured xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:05:36 status installed xserver-xorg-input-synaptics 1.1.2-1ubuntu7
2009-10-28 21:05:36 configure xserver-xorg-input-mouse 1:1.4.0-2 1:1.4.0-2
2009-10-28 21:05:36 status unpacked xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:05:36 status half-configured xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:05:36 status installed xserver-xorg-input-mouse 1:1.4.0-2
2009-10-28 21:05:36 configure xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3 1:12.6.4-1ubuntu3
2009-10-28 21:05:36 status unpacked xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:05:36 status half-configured xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:05:36 status installed xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3
2009-10-28 21:05:36 configure xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4 1:0.8.4.1-0ubuntu4
2009-10-28 21:05:36 status unpacked xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:05:36 status half-configured xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:05:36 status installed xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4
2009-10-28 21:05:36 configure xserver-xorg-input-all 1:7.4+3ubuntu7 1:7.4+3ubuntu7
2009-10-28 21:05:36 status unpacked xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 status half-configured xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 status installed xserver-xorg-input-all 1:7.4+3ubuntu7
2009-10-28 21:05:36 configure xserver-xorg 1:7.4+3ubuntu7 1:7.4+3ubuntu7
2009-10-28 21:05:36 status unpacked xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 status half-configured xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 status installed xserver-xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 configure xorg 1:7.4+3ubuntu7 1:7.4+3ubuntu7
2009-10-28 21:05:36 status unpacked xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 status half-configured xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 status installed xorg 1:7.4+3ubuntu7
2009-10-28 21:05:36 configure pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4 1:0.9.19-0ubuntu4
2009-10-28 21:05:36 status unpacked pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:05:36 status half-configured pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:05:36 status installed pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4
2009-10-28 21:05:36 configure foomatic-db-engine 4.0.3-0ubuntu2 4.0.3-0ubuntu2
2009-10-28 21:05:36 status unpacked foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 21:05:36 status half-configured foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 21:05:36 status installed foomatic-db-engine 4.0.3-0ubuntu2
2009-10-28 21:05:36 configure libgamin0 0.1.10-1ubuntu2 0.1.10-1ubuntu2
2009-10-28 21:05:36 status unpacked libgamin0 0.1.10-1ubuntu2
2009-10-28 21:05:36 status half-configured libgamin0 0.1.10-1ubuntu2
2009-10-28 21:05:36 status installed libgamin0 0.1.10-1ubuntu2
2009-10-28 21:05:36 configure libgnomevfs2-0 1:2.24.2-1ubuntu1 1:2.24.2-1ubuntu1
2009-10-28 21:05:36 status unpacked libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 21:05:36 status half-configured libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 21:05:36 status installed libgnomevfs2-0 1:2.24.2-1ubuntu1
2009-10-28 21:05:36 configure libgnome2-0 2.28.0-0ubuntu3 2.28.0-0ubuntu3
2009-10-28 21:05:36 status unpacked libgnome2-0 2.28.0-0ubuntu3
2009-10-28 21:05:36 status half-configured libgnome2-0 2.28.0-0ubuntu3
2009-10-28 21:05:36 status installed libgnome2-0 2.28.0-0ubuntu3
2009-10-28 21:05:36 configure libbonoboui2-0 2.24.2-1ubuntu2 2.24.2-1ubuntu2
2009-10-28 21:05:36 status unpacked libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 21:05:36 status half-configured libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 21:05:36 status installed libbonoboui2-0 2.24.2-1ubuntu2
2009-10-28 21:05:36 configure libpanel-applet2-0 1:2.28.0-0ubuntu6 1:2.28.0-0ubuntu6
2009-10-28 21:05:36 status unpacked libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 21:05:36 status half-configured libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 status installed libpanel-applet2-0 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 configure libgnomeui-0 2.24.2-1 2.24.2-1
2009-10-28 21:05:37 status unpacked libgnomeui-0 2.24.2-1
2009-10-28 21:05:37 status half-configured libgnomeui-0 2.24.2-1
2009-10-28 21:05:37 status installed libgnomeui-0 2.24.2-1
2009-10-28 21:05:37 configure python-gnome2 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:05:37 status unpacked python-gnome2 2.28.0-0ubuntu1
2009-10-28 21:05:37 status half-configured python-gnome2 2.28.0-0ubuntu1
2009-10-28 21:05:37 status installed python-gnome2 2.28.0-0ubuntu1
2009-10-28 21:05:37 configure gnome-about 1:2.28.1-0ubuntu2 1:2.28.1-0ubuntu2
2009-10-28 21:05:37 status unpacked gnome-about 1:2.28.1-0ubuntu2
2009-10-28 21:05:37 status half-configured gnome-about 1:2.28.1-0ubuntu2
2009-10-28 21:05:37 status installed gnome-about 1:2.28.1-0ubuntu2
2009-10-28 21:05:37 configure gnome-panel 1:2.28.0-0ubuntu6 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 status unpacked gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 status unpacked gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 status half-configured gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 status installed gnome-panel 1:2.28.0-0ubuntu6
2009-10-28 21:05:37 configure gnome-applets 2.28.0-0ubuntu2 2.28.0-0ubuntu2
2009-10-28 21:05:37 status unpacked gnome-applets 2.28.0-0ubuntu2
2009-10-28 21:05:37 status half-configured gnome-applets 2.28.0-0ubuntu2
2009-10-28 21:05:37 status installed gnome-applets 2.28.0-0ubuntu2
2009-10-28 21:05:37 configure python-desktopcouch-records 0.5-0ubuntu1 0.5-0ubuntu1
2009-10-28 21:05:37 status unpacked python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 21:05:37 status half-configured python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 21:05:37 status installed python-desktopcouch-records 0.5-0ubuntu1
2009-10-28 21:05:37 configure libgnome-pilot2 2.0.17-0ubuntu2 2.0.17-0ubuntu2
2009-10-28 21:05:37 status unpacked libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 21:05:37 status half-configured libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 21:05:38 status installed libgnome-pilot2 2.0.17-0ubuntu2
2009-10-28 21:05:38 configure liblpint-bonobo0 0.1.26 0.1.26
2009-10-28 21:05:38 status unpacked liblpint-bonobo0 0.1.26
2009-10-28 21:05:38 status half-configured liblpint-bonobo0 0.1.26
2009-10-28 21:05:38 status installed liblpint-bonobo0 0.1.26
2009-10-28 21:05:38 configure evolution 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:38 status unpacked evolution 2.28.1-0ubuntu1
2009-10-28 21:05:38 status unpacked evolution 2.28.1-0ubuntu1
2009-10-28 21:05:38 status half-configured evolution 2.28.1-0ubuntu1
2009-10-28 21:05:38 status installed evolution 2.28.1-0ubuntu1
2009-10-28 21:05:38 configure evolution-couchdb 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-10-28 21:05:38 status unpacked evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 21:05:38 status half-configured evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 21:05:38 status installed evolution-couchdb 0.3.2-0ubuntu2
2009-10-28 21:05:38 configure evolution-exchange 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:38 status unpacked evolution-exchange 2.28.1-0ubuntu1
2009-10-28 21:05:38 status half-configured evolution-exchange 2.28.1-0ubuntu1
2009-10-28 21:05:39 status installed evolution-exchange 2.28.1-0ubuntu1
2009-10-28 21:05:39 configure evolution-plugins 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:39 status unpacked evolution-plugins 2.28.1-0ubuntu1
2009-10-28 21:05:39 status half-configured evolution-plugins 2.28.1-0ubuntu1
2009-10-28 21:05:39 status installed evolution-plugins 2.28.1-0ubuntu1
2009-10-28 21:05:39 configure libmono-system2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-system2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-security2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-security2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-data-tds2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-data-tds2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-system-data2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-system-data2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-sqlite2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-sqlite2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-posix2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-posix2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libmono2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status unpacked libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status half-configured libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 status installed libmono2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:39 configure libglib2.0-cil 2.12.9-1 2.12.9-1
2009-10-28 21:05:39 status unpacked libglib2.0-cil 2.12.9-1
2009-10-28 21:05:39 status half-configured libglib2.0-cil 2.12.9-1
2009-10-28 21:05:39 status installed libglib2.0-cil 2.12.9-1
2009-10-28 21:05:39 configure libgconf2.0-cil 2.24.1-4ubuntu1 2.24.1-4ubuntu1
2009-10-28 21:05:39 status unpacked libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:39 status half-configured libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:41 status installed libgconf2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:41 configure libgtk2.0-cil 2.12.9-1 2.12.9-1
2009-10-28 21:05:41 status unpacked libgtk2.0-cil 2.12.9-1
2009-10-28 21:05:41 status half-configured libgtk2.0-cil 2.12.9-1
2009-10-28 21:05:41 status installed libgtk2.0-cil 2.12.9-1
2009-10-28 21:05:41 configure libglade2.0-cil 2.12.9-1 2.12.9-1
2009-10-28 21:05:41 status unpacked libglade2.0-cil 2.12.9-1
2009-10-28 21:05:41 status half-configured libglade2.0-cil 2.12.9-1
2009-10-28 21:05:41 status installed libglade2.0-cil 2.12.9-1
2009-10-28 21:05:41 configure libndesk-dbus1.0-cil 0.6.0-3 0.6.0-3
2009-10-28 21:05:41 status unpacked libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 21:05:41 status half-configured libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 21:05:41 status installed libndesk-dbus1.0-cil 0.6.0-3
2009-10-28 21:05:41 configure libgnome-keyring1.0-cil 1.0.0-1 1.0.0-1
2009-10-28 21:05:41 status unpacked libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 21:05:41 status half-configured libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 21:05:42 status installed libgnome-keyring1.0-cil 1.0.0-1
2009-10-28 21:05:42 configure libgnome-vfs2.0-cil 2.24.1-4ubuntu1 2.24.1-4ubuntu1
2009-10-28 21:05:42 status unpacked libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:42 status half-configured libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:43 status installed libgnome-vfs2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:44 configure libart2.0-cil 2.24.1-4ubuntu1 2.24.1-4ubuntu1
2009-10-28 21:05:44 status unpacked libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:44 status half-configured libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:45 status installed libart2.0-cil 2.24.1-4ubuntu1
2009-10-28 21:05:45 configure libgnome2.24-cil 2.24.1-4ubuntu1 2.24.1-4ubuntu1
2009-10-28 21:05:45 status unpacked libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 21:05:45 status half-configured libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 21:05:46 status installed libgnome2.24-cil 2.24.1-4ubuntu1
2009-10-28 21:05:46 configure libmono-addins0.2-cil 0.4-5 0.4-5
2009-10-28 21:05:46 status unpacked libmono-addins0.2-cil 0.4-5
2009-10-28 21:05:46 status half-configured libmono-addins0.2-cil 0.4-5
2009-10-28 21:05:48 status installed libmono-addins0.2-cil 0.4-5
2009-10-28 21:05:48 configure libmono-addins-gui0.2-cil 0.4-5 0.4-5
2009-10-28 21:05:48 status unpacked libmono-addins-gui0.2-cil 0.4-5
2009-10-28 21:05:48 status half-configured libmono-addins-gui0.2-cil 0.4-5
2009-10-28 21:05:49 status installed libmono-addins-gui0.2-cil 0.4-5
2009-10-28 21:05:49 configure libndesk-dbus-glib1.0-cil 0.4.1-2 0.4.1-2
2009-10-28 21:05:49 status unpacked libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 21:05:49 status half-configured libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 21:05:49 status installed libndesk-dbus-glib1.0-cil 0.4.1-2
2009-10-28 21:05:50 configure xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status installed xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 configure firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status unpacked firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status half-configured firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status installed firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 configure firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status unpacked firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status half-configured firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 status installed firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6
2009-10-28 21:05:50 configure gdm 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status unpacked gdm 2.28.1-0ubuntu1
2009-10-28 21:05:50 status half-configured gdm 2.28.1-0ubuntu1
2009-10-28 21:05:51 status installed gdm 2.28.1-0ubuntu1
2009-10-28 21:05:51 configure gdm-guest-session 0.14 0.14
2009-10-28 21:05:51 status unpacked gdm-guest-session 0.14
2009-10-28 21:05:51 status unpacked gdm-guest-session 0.14
2009-10-28 21:05:51 status half-configured gdm-guest-session 0.14
2009-10-28 21:05:51 status installed gdm-guest-session 0.14
2009-10-28 21:05:51 configure libgail-gnome-module 1.20.1-1ubuntu1 1.20.1-1ubuntu1
2009-10-28 21:05:51 status unpacked libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 21:05:51 status half-configured libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 21:05:51 status installed libgail-gnome-module 1.20.1-1ubuntu1
2009-10-28 21:05:51 configure python-pyatspi 1.28.1-0ubuntu1 1.28.1-0ubuntu1
2009-10-28 21:05:51 status unpacked python-pyatspi 1.28.1-0ubuntu1
2009-10-28 21:05:51 status half-configured python-pyatspi 1.28.1-0ubuntu1
2009-10-28 21:05:51 status installed python-pyatspi 1.28.1-0ubuntu1
2009-10-28 21:05:51 configure gnome-orca 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:51 status unpacked gnome-orca 2.28.1-0ubuntu1
2009-10-28 21:05:51 status half-configured gnome-orca 2.28.1-0ubuntu1
2009-10-28 21:05:51 status installed gnome-orca 2.28.1-0ubuntu1
2009-10-28 21:05:51 configure gnome-power-manager 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:51 status unpacked gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 21:05:51 status unpacked gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 21:05:51 status half-configured gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 21:05:51 status installed gnome-power-manager 2.28.1-0ubuntu1
2009-10-28 21:05:51 configure gnome-session 2.28.0-0ubuntu5 2.28.0-0ubuntu5
2009-10-28 21:05:51 status unpacked gnome-session 2.28.0-0ubuntu5
2009-10-28 21:05:51 status unpacked gnome-session 2.28.0-0ubuntu5
2009-10-28 21:05:51 status unpacked gnome-session 2.28.0-0ubuntu5
2009-10-28 21:05:51 status half-configured gnome-session 2.28.0-0ubuntu5
2009-10-28 21:05:52 update-alternatives: run with --install /usr/bin/x-session-manager x-session-manager /usr/bin/gnome-session 50 --slave /usr/share/man/man1/x-session-manager.1.gz x-session-manager.1.gz /usr/share/man/man1/gnome-session.1.gz
2009-10-28 21:05:52 update-alternatives: link group x-session-manager updated to point to /usr/bin/gnome-session
2009-10-28 21:05:52 status installed gnome-session 2.28.0-0ubuntu5
2009-10-28 21:05:52 configure gnome-utils 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:52 status unpacked gnome-utils 2.28.1-0ubuntu1
2009-10-28 21:05:52 status half-configured gnome-utils 2.28.1-0ubuntu1
2009-10-28 21:05:52 status installed gnome-utils 2.28.1-0ubuntu1
2009-10-28 21:05:52 configure indicator-applet 0.2.0-0ubuntu2 0.2.0-0ubuntu2
2009-10-28 21:05:52 status unpacked indicator-applet 0.2.0-0ubuntu2
2009-10-28 21:05:52 status half-configured indicator-applet 0.2.0-0ubuntu2
2009-10-28 21:05:52 status installed indicator-applet 0.2.0-0ubuntu2
2009-10-28 21:05:52 configure indicator-session 0.1.7-0ubuntu3 0.1.7-0ubuntu3
2009-10-28 21:05:52 status unpacked indicator-session 0.1.7-0ubuntu3
2009-10-28 21:05:52 status half-configured indicator-session 0.1.7-0ubuntu3
2009-10-28 21:05:52 status installed indicator-session 0.1.7-0ubuntu3
2009-10-28 21:05:52 configure indicator-applet-session 0.2.0-0ubuntu2 0.2.0-0ubuntu2
2009-10-28 21:05:52 status unpacked indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 21:05:52 status half-configured indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 21:05:52 status installed indicator-applet-session 0.2.0-0ubuntu2
2009-10-28 21:05:52 configure libgmime2.2a-cil 2.2.22-4 2.2.22-4
2009-10-28 21:05:52 status unpacked libgmime2.2a-cil 2.2.22-4
2009-10-28 21:05:52 status half-configured libgmime2.2a-cil 2.2.22-4
2009-10-28 21:05:53 status installed libgmime2.2a-cil 2.2.22-4
2009-10-28 21:05:53 configure libgnome2-vfs-perl 1.081-1 1.081-1
2009-10-28 21:05:53 status unpacked libgnome2-vfs-perl 1.081-1
2009-10-28 21:05:53 status half-configured libgnome2-vfs-perl 1.081-1
2009-10-28 21:05:53 status installed libgnome2-vfs-perl 1.081-1
2009-10-28 21:05:53 configure libgnome2-perl 1.042-2 1.042-2
2009-10-28 21:05:53 status unpacked libgnome2-perl 1.042-2
2009-10-28 21:05:53 status half-configured libgnome2-perl 1.042-2
2009-10-28 21:05:53 status installed libgnome2-perl 1.042-2
2009-10-28 21:05:53 configure libgnomepanel2.24-cil 2.26.0-1 2.26.0-1
2009-10-28 21:05:53 status unpacked libgnomepanel2.24-cil 2.26.0-1
2009-10-28 21:05:53 status half-configured libgnomepanel2.24-cil 2.26.0-1
2009-10-28 21:05:53 status installed libgnomepanel2.24-cil 2.26.0-1
2009-10-28 21:05:53 configure libgnomevfs2-extra 1:2.24.2-1ubuntu1 1:2.24.2-1ubuntu1
2009-10-28 21:05:53 status unpacked libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 21:05:53 status unpacked libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 21:05:53 status half-configured libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 21:05:53 status installed libgnomevfs2-extra 1:2.24.2-1ubuntu1
2009-10-28 21:05:53 configure mousetweaks 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:53 status unpacked mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:05:53 status half-configured mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:05:54 status installed mousetweaks 2.28.1-0ubuntu1
2009-10-28 21:05:54 configure nautilus-share 0.7.2-12 0.7.2-12
2009-10-28 21:05:54 status unpacked nautilus-share 0.7.2-12
2009-10-28 21:05:54 status half-configured nautilus-share 0.7.2-12
2009-10-28 21:05:54 status installed nautilus-share 0.7.2-12
2009-10-28 21:05:54 configure python-gnomeapplet 2.28.0-0ubuntu1 2.28.0-0ubuntu1
2009-10-28 21:05:54 status unpacked python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:05:54 status half-configured python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:05:54 status installed python-gnomeapplet 2.28.0-0ubuntu1
2009-10-28 21:05:54 configure rhythmbox 0.12.5-0ubuntu4 0.12.5-0ubuntu4
2009-10-28 21:05:54 status unpacked rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:05:54 status half-configured rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:05:55 status installed rhythmbox 0.12.5-0ubuntu4
2009-10-28 21:05:55 configure system-config-printer-gnome 1.1.12+git20090826-0ubuntu8 1.1.12+git20090826-0ubuntu8
2009-10-28 21:05:55 status unpacked system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:05:55 status unpacked system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:05:55 status half-configured system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:05:55 status installed system-config-printer-gnome 1.1.12+git20090826-0ubuntu8
2009-10-28 21:05:55 configure tomboy 1.0.0-0ubuntu2 1.0.0-0ubuntu2
2009-10-28 21:05:55 status unpacked tomboy 1.0.0-0ubuntu2
2009-10-28 21:05:55 status half-configured tomboy 1.0.0-0ubuntu2
2009-10-28 21:05:57 status installed tomboy 1.0.0-0ubuntu2
2009-10-28 21:05:57 configure ubuntu-desktop 1.175 1.175
2009-10-28 21:05:57 status unpacked ubuntu-desktop 1.175
2009-10-28 21:05:57 status half-configured ubuntu-desktop 1.175
2009-10-28 21:05:57 status installed ubuntu-desktop 1.175
2009-10-28 21:05:57 configure usb-creator-gtk 0.2.12 0.2.12
2009-10-28 21:05:57 status unpacked usb-creator-gtk 0.2.12
2009-10-28 21:05:57 status half-configured usb-creator-gtk 0.2.12
2009-10-28 21:05:57 status installed usb-creator-gtk 0.2.12
2009-10-28 21:05:57 configure vinagre 2.28.1-0ubuntu1 2.28.1-0ubuntu1
2009-10-28 21:05:57 status unpacked vinagre 2.28.1-0ubuntu1
2009-10-28 21:05:57 status half-configured vinagre 2.28.1-0ubuntu1
2009-10-28 21:05:57 status installed vinagre 2.28.1-0ubuntu1
2009-10-28 21:05:57 configure evolution-indicator 0.2.4-0ubuntu2 0.2.4-0ubuntu2
2009-10-28 21:05:57 status unpacked evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:05:57 status half-configured evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:05:57 status installed evolution-indicator 0.2.4-0ubuntu2
2009-10-28 21:05:57 configure gnome-pilot 2.0.17-0ubuntu2 2.0.17-0ubuntu2
2009-10-28 21:05:57 status unpacked gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:05:57 status half-configured gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:05:58 status installed gnome-pilot 2.0.17-0ubuntu2
2009-10-28 21:05:58 configure gnome-pilot-conduits 2.0.15-1.2 2.0.15-1.2
2009-10-28 21:05:58 status unpacked gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:05:58 status half-configured gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:05:58 status installed gnome-pilot-conduits 2.0.15-1.2
2009-10-28 21:05:58 configure libmono-system-web2.0-cil 2.4.2.3+dfsg-2 2.4.2.3+dfsg-2
2009-10-28 21:05:58 status unpacked libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:58 status half-configured libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:58 status installed libmono-system-web2.0-cil 2.4.2.3+dfsg-2
2009-10-28 21:05:58 configure libflickrnet2.2-cil 1:2.2.0-1 1:2.2.0-1
2009-10-28 21:05:58 status unpacked libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 21:05:58 status half-configured libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 21:05:59 status installed libflickrnet2.2-cil 1:2.2.0-1
2009-10-28 21:05:59 configure f-spot 0.6.1.3-2 0.6.1.3-2
2009-10-28 21:05:59 status unpacked f-spot 0.6.1.3-2
2009-10-28 21:05:59 status half-configured f-spot 0.6.1.3-2
2009-10-28 21:05:59 status installed f-spot 0.6.1.3-2
2009-10-28 21:05:59 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 21:05:59 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 21:05:59 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 21:05:59 trigproc python-support 1.0.3ubuntu1 1.0.3ubuntu1
2009-10-28 21:05:59 status half-configured python-support 1.0.3ubuntu1
2009-10-28 21:05:59 status installed python-support 1.0.3ubuntu1
2009-10-28 21:06:00 startup packages purge
2009-10-28 21:06:00 status installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 remove linux-headers-generic 2.6.31.14.27 2.6.31.14.27
2009-10-28 21:06:00 status half-configured linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 status half-installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 status config-files linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 status config-files linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 status config-files linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:00 status not-installed linux-headers-generic <none>
2009-10-28 21:06:00 status installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:00 remove linux-headers-2.6.31-14-generic 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:06:00 status half-configured linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:00 status half-installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:01 status config-files linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:01 status config-files linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:01 status config-files linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:01 status not-installed linux-headers-2.6.31-14-generic <none>
2009-10-28 21:06:01 status installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:01 remove linux-headers-2.6.31-14 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:06:01 status half-configured linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:01 status half-installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:01 status config-files linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:02 status config-files linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:02 status config-files linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:02 status not-installed linux-headers-2.6.31-14 <none>
2009-10-28 21:06:02 startup archives unpack
2009-10-28 21:06:03 install linux-headers-2.6.31-14 <none> 2.6.31-14.48
2009-10-28 21:06:03 status half-installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:08 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:08 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:08 install linux-headers-2.6.31-14-generic <none> 2.6.31-14.48
2009-10-28 21:06:08 status half-installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:10 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:10 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:10 install linux-headers-generic <none> 2.6.31.14.27
2009-10-28 21:06:10 status half-installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:10 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:10 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:10 startup packages configure
2009-10-28 21:06:10 configure linux-headers-2.6.31-14 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:06:10 status unpacked linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:10 status half-configured linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:10 status installed linux-headers-2.6.31-14 2.6.31-14.48
2009-10-28 21:06:10 configure linux-headers-2.6.31-14-generic 2.6.31-14.48 2.6.31-14.48
2009-10-28 21:06:10 status unpacked linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:10 status half-configured linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:11 status installed linux-headers-2.6.31-14-generic 2.6.31-14.48
2009-10-28 21:06:11 configure linux-headers-generic 2.6.31.14.27 2.6.31.14.27
2009-10-28 21:06:11 status unpacked linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:11 status half-configured linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:11 status installed linux-headers-generic 2.6.31.14.27
2009-10-28 21:06:22 startup archives unpack
2009-10-28 21:06:22 install language-pack-bn-base <none> 1:9.10+20091022
2009-10-28 21:06:22 status half-installed language-pack-bn-base 1:9.10+20091022
2009-10-28 21:06:22 status triggers-pending software-center 1.0.2
2009-10-28 21:06:22 status half-installed language-pack-bn-base 1:9.10+20091022
2009-10-28 21:06:22 status unpacked language-pack-bn-base 1:9.10+20091022
2009-10-28 21:06:22 status unpacked language-pack-bn-base 1:9.10+20091022
2009-10-28 21:06:22 install language-pack-bn <none> 1:9.10+20091022
2009-10-28 21:06:22 status half-installed language-pack-bn 1:9.10+20091022
2009-10-28 21:06:22 status half-installed language-pack-bn 1:9.10+20091022
2009-10-28 21:06:22 status unpacked language-pack-bn 1:9.10+20091022
2009-10-28 21:06:22 status unpacked language-pack-bn 1:9.10+20091022
2009-10-28 21:06:22 install language-pack-de-base <none> 1:9.10+20091022
2009-10-28 21:06:22 status half-installed language-pack-de-base 1:9.10+20091022
2009-10-28 21:06:22 status half-installed language-pack-de-base 1:9.10+20091022
2009-10-28 21:06:24 status unpacked language-pack-de-base 1:9.10+20091022
2009-10-28 21:06:24 status unpacked language-pack-de-base 1:9.10+20091022
2009-10-28 21:06:24 install language-pack-de <none> 1:9.10+20091022
2009-10-28 21:06:24 status half-installed language-pack-de 1:9.10+20091022
2009-10-28 21:06:24 status half-installed language-pack-de 1:9.10+20091022
2009-10-28 21:06:24 status unpacked language-pack-de 1:9.10+20091022
2009-10-28 21:06:24 status unpacked language-pack-de 1:9.10+20091022
2009-10-28 21:06:24 install language-pack-en-base <none> 1:9.10+20091022
2009-10-28 21:06:24 status half-installed language-pack-en-base 1:9.10+20091022
2009-10-28 21:06:24 status half-installed language-pack-en-base 1:9.10+20091022
2009-10-28 21:06:25 status unpacked language-pack-en-base 1:9.10+20091022
2009-10-28 21:06:25 status unpacked language-pack-en-base 1:9.10+20091022
2009-10-28 21:06:25 install language-pack-en <none> 1:9.10+20091022
2009-10-28 21:06:25 status half-installed language-pack-en 1:9.10+20091022
2009-10-28 21:06:25 status half-installed language-pack-en 1:9.10+20091022
2009-10-28 21:06:25 status unpacked language-pack-en 1:9.10+20091022
2009-10-28 21:06:25 status unpacked language-pack-en 1:9.10+20091022
2009-10-28 21:06:25 install language-pack-es-base <none> 1:9.10+20091022
2009-10-28 21:06:25 status half-installed language-pack-es-base 1:9.10+20091022
2009-10-28 21:06:25 status half-installed language-pack-es-base 1:9.10+20091022
2009-10-28 21:06:27 status unpacked language-pack-es-base 1:9.10+20091022
2009-10-28 21:06:27 status unpacked language-pack-es-base 1:9.10+20091022
2009-10-28 21:06:27 install language-pack-es <none> 1:9.10+20091022
2009-10-28 21:06:27 status half-installed language-pack-es 1:9.10+20091022
2009-10-28 21:06:27 status half-installed language-pack-es 1:9.10+20091022
2009-10-28 21:06:27 status unpacked language-pack-es 1:9.10+20091022
2009-10-28 21:06:27 status unpacked language-pack-es 1:9.10+20091022
2009-10-28 21:06:27 install language-pack-fr-base <none> 1:9.10+20091022
2009-10-28 21:06:27 status half-installed language-pack-fr-base 1:9.10+20091022
2009-10-28 21:06:27 status half-installed language-pack-fr-base 1:9.10+20091022
2009-10-28 21:06:29 status unpacked language-pack-fr-base 1:9.10+20091022
2009-10-28 21:06:29 status unpacked language-pack-fr-base 1:9.10+20091022
2009-10-28 21:06:29 install language-pack-fr <none> 1:9.10+20091022
2009-10-28 21:06:29 status half-installed language-pack-fr 1:9.10+20091022
2009-10-28 21:06:29 status half-installed language-pack-fr 1:9.10+20091022
2009-10-28 21:06:29 status unpacked language-pack-fr 1:9.10+20091022
2009-10-28 21:06:29 status unpacked language-pack-fr 1:9.10+20091022
2009-10-28 21:06:29 install language-pack-gnome-bn-base <none> 1:9.10+20091022
2009-10-28 21:06:29 status half-installed language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:06:29 status half-installed language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:06:31 status unpacked language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:06:31 status unpacked language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:06:31 install language-pack-gnome-bn <none> 1:9.10+20091022
2009-10-28 21:06:31 status half-installed language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:06:31 status half-installed language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:06:31 status unpacked language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:06:31 status unpacked language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:06:31 install language-pack-gnome-de-base <none> 1:9.10+20091022
2009-10-28 21:06:31 status half-installed language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:06:31 status half-installed language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:06:35 status unpacked language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:06:35 status unpacked language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:06:35 install language-pack-gnome-de <none> 1:9.10+20091022
2009-10-28 21:06:35 status half-installed language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:06:35 status half-installed language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:06:35 status unpacked language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:06:35 status unpacked language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:06:35 install language-pack-gnome-en-base <none> 1:9.10+20091022
2009-10-28 21:06:35 status half-installed language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:06:35 status half-installed language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:06:37 status unpacked language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:06:38 status unpacked language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:06:38 install language-pack-gnome-en <none> 1:9.10+20091022
2009-10-28 21:06:38 status half-installed language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:06:38 status half-installed language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:06:38 status unpacked language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:06:38 status unpacked language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:06:38 install language-pack-gnome-es-base <none> 1:9.10+20091022
2009-10-28 21:06:38 status half-installed language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:06:38 status half-installed language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:06:41 status unpacked language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:06:41 status unpacked language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:06:41 install language-pack-gnome-es <none> 1:9.10+20091022
2009-10-28 21:06:41 status half-installed language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:06:41 status half-installed language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:06:41 status unpacked language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:06:41 status unpacked language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:06:41 install language-pack-gnome-fr-base <none> 1:9.10+20091022
2009-10-28 21:06:41 status half-installed language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:06:41 status half-installed language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:06:45 install language-pack-gnome-fr <none> 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:06:45 install language-pack-pt <none> 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-pt 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-pt 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-pt 1:9.10+20091022
2009-10-28 21:06:45 status unpacked language-pack-pt 1:9.10+20091022
2009-10-28 21:06:45 install language-pack-pt-base <none> 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-pt-base 1:9.10+20091022
2009-10-28 21:06:45 status half-installed language-pack-pt-base 1:9.10+20091022
2009-10-28 21:06:47 status unpacked language-pack-pt-base 1:9.10+20091022
2009-10-28 21:06:47 status unpacked language-pack-pt-base 1:9.10+20091022
2009-10-28 21:06:47 install language-pack-gnome-pt-base <none> 1:9.10+20091022
2009-10-28 21:06:47 status half-installed language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:06:47 status half-installed language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:06:51 install language-pack-gnome-pt <none> 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:06:51 install language-pack-xh <none> 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-xh 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-xh 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-xh 1:9.10+20091022
2009-10-28 21:06:51 status unpacked language-pack-xh 1:9.10+20091022
2009-10-28 21:06:51 install language-pack-xh-base <none> 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-xh-base 1:9.10+20091022
2009-10-28 21:06:51 status half-installed language-pack-xh-base 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-xh-base 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-xh-base 1:9.10+20091022
2009-10-28 21:06:52 install language-pack-gnome-xh-base <none> 1:9.10+20091022
2009-10-28 21:06:52 status half-installed language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:06:52 status half-installed language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:06:52 install language-pack-gnome-xh <none> 1:9.10+20091022
2009-10-28 21:06:52 status half-installed language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:06:52 status half-installed language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:06:52 status unpacked language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:06:52 install cryptsetup <none> 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 status half-installed cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 status triggers-pending sreadahead 1.0-5
2009-10-28 21:06:52 status half-installed cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 status triggers-pending sreadahead 1.0-5
2009-10-28 21:06:52 status triggers-pending man-db 2.5.6-2
2009-10-28 21:06:52 status half-installed cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:06:52 install libdmraid1.0.0.rc15 <none> 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status half-installed libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 install dmraid <none> 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status half-installed dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status half-installed dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:06:52 install libecryptfs0 <none> 81-0ubuntu3
2009-10-28 21:06:52 status half-installed libecryptfs0 81-0ubuntu3
2009-10-28 21:06:52 status unpacked libecryptfs0 81-0ubuntu3
2009-10-28 21:06:52 status unpacked libecryptfs0 81-0ubuntu3
2009-10-28 21:06:52 install keyutils <none> 1.2-10
2009-10-28 21:06:52 status half-installed keyutils 1.2-10
2009-10-28 21:06:52 status half-installed keyutils 1.2-10
2009-10-28 21:06:52 status unpacked keyutils 1.2-10
2009-10-28 21:06:52 status unpacked keyutils 1.2-10
2009-10-28 21:06:53 install ecryptfs-utils <none> 81-0ubuntu3
2009-10-28 21:06:53 status half-installed ecryptfs-utils 81-0ubuntu3
2009-10-28 21:06:53 status half-installed ecryptfs-utils 81-0ubuntu3
2009-10-28 21:06:53 status unpacked ecryptfs-utils 81-0ubuntu3
2009-10-28 21:06:53 status unpacked ecryptfs-utils 81-0ubuntu3
2009-10-28 21:06:53 install gparted <none> 0.4.5-2ubuntu1
2009-10-28 21:06:53 status half-installed gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 status triggers-pending hicolor-icon-theme 0.10-2
2009-10-28 21:06:53 status half-installed gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 status half-installed gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:06:53 status half-installed gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 status unpacked gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 status unpacked gparted 0.4.5-2ubuntu1
2009-10-28 21:06:53 install jfsutils <none> 1.1.12-2
2009-10-28 21:06:53 status half-installed jfsutils 1.1.12-2
2009-10-28 21:06:53 status half-installed jfsutils 1.1.12-2
2009-10-28 21:06:56 status unpacked jfsutils 1.1.12-2
2009-10-28 21:06:56 status unpacked jfsutils 1.1.12-2
2009-10-28 21:06:56 install myspell-en-au <none> 2.1-3.1
2009-10-28 21:06:56 status half-installed myspell-en-au 2.1-3.1
2009-10-28 21:06:56 status unpacked myspell-en-au 2.1-3.1
2009-10-28 21:06:56 status unpacked myspell-en-au 2.1-3.1
2009-10-28 21:06:56 install myspell-en-gb <none> 1:3.0.1-8ubuntu1
2009-10-28 21:06:56 status half-installed myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:06:56 status unpacked myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:06:56 status unpacked myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:06:56 install wamerican <none> 6-3
2009-10-28 21:06:56 status half-installed wamerican 6-3
2009-10-28 21:06:56 status half-installed wamerican 6-3
2009-10-28 21:06:56 status unpacked wamerican 6-3
2009-10-28 21:06:57 status unpacked wamerican 6-3
2009-10-28 21:06:57 install wbritish <none> 6-3
2009-10-28 21:06:57 status half-installed wbritish 6-3
2009-10-28 21:06:57 status half-installed wbritish 6-3
2009-10-28 21:06:57 status unpacked wbritish 6-3
2009-10-28 21:06:57 status unpacked wbritish 6-3
2009-10-28 21:06:57 install openoffice.org-thesaurus-en-us <none> 1:3.0.1-8ubuntu1
2009-10-28 21:06:57 status half-installed openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:06:59 status unpacked openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:06:59 status unpacked openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:07:00 install openoffice.org-thesaurus-en-au <none> 2.1-3.1
2009-10-28 21:07:00 status half-installed openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:01 status unpacked openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:01 status unpacked openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:01 install myspell-en-za <none> 1:3.0.1-8ubuntu1
2009-10-28 21:07:01 status half-installed myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:01 status unpacked myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:01 status unpacked myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:01 install openoffice.org-hyphenation <none> 0.3
2009-10-28 21:07:01 status half-installed openoffice.org-hyphenation 0.3
2009-10-28 21:07:01 status unpacked openoffice.org-hyphenation 0.3
2009-10-28 21:07:01 status unpacked openoffice.org-hyphenation 0.3
2009-10-28 21:07:01 install openoffice.org-hyphenation-en-us <none> 2.4-4
2009-10-28 21:07:01 status half-installed openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:01 status unpacked openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:01 status unpacked openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:01 install language-support-writing-en <none> 1:9.10+20090909
2009-10-28 21:07:01 status half-installed language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:01 status unpacked language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:01 status unpacked language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:01 install language-support-en <none> 1:9.10+20090909
2009-10-28 21:07:01 status half-installed language-support-en 1:9.10+20090909
2009-10-28 21:07:01 status unpacked language-support-en 1:9.10+20090909
2009-10-28 21:07:01 status unpacked language-support-en 1:9.10+20090909
2009-10-28 21:07:01 install libdebconfclient0 <none> 0.145
2009-10-28 21:07:01 status half-installed libdebconfclient0 0.145
2009-10-28 21:07:01 status unpacked libdebconfclient0 0.145
2009-10-28 21:07:01 status unpacked libdebconfclient0 0.145
2009-10-28 21:07:01 install libdebian-installer4 <none> 0.63ubuntu2
2009-10-28 21:07:01 status half-installed libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:01 status unpacked libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:01 status unpacked libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:01 install libntfs10 <none> 2.0.0-1ubuntu3
2009-10-28 21:07:01 status half-installed libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:01 status unpacked libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:01 status unpacked libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:01 install libreadline5 <none> 5.2-6
2009-10-28 21:07:01 status half-installed libreadline5 5.2-6
2009-10-28 21:07:02 status unpacked libreadline5 5.2-6
2009-10-28 21:07:02 status unpacked libreadline5 5.2-6
2009-10-28 21:07:02 install localechooser-data <none> 2.12ubuntu2
2009-10-28 21:07:02 status half-installed localechooser-data 2.12ubuntu2
2009-10-28 21:07:02 status unpacked localechooser-data 2.12ubuntu2
2009-10-28 21:07:02 status unpacked localechooser-data 2.12ubuntu2
2009-10-28 21:07:02 install ntfsprogs <none> 2.0.0-1ubuntu3
2009-10-28 21:07:02 status half-installed ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:02 status half-installed ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:02 status unpacked ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:02 status unpacked ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:02 install python-pyicu <none> 0.8.1-3ubuntu2
2009-10-28 21:07:02 status half-installed python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:02 status unpacked python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:02 status unpacked python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:02 install rdate <none> 1:1.2-1
2009-10-28 21:07:02 status half-installed rdate 1:1.2-1
2009-10-28 21:07:02 status half-installed rdate 1:1.2-1
2009-10-28 21:07:02 status unpacked rdate 1:1.2-1
2009-10-28 21:07:02 status unpacked rdate 1:1.2-1
2009-10-28 21:07:02 install reiserfsprogs <none> 1:3.6.21-1
2009-10-28 21:07:02 status half-installed reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:02 status half-installed reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:02 status unpacked reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:02 status unpacked reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:02 install ubiquity-frontend-gtk <none> 2.0.8
2009-10-28 21:07:02 status half-installed ubiquity-frontend-gtk 2.0.8
2009-10-28 21:07:02 status half-installed ubiquity-frontend-gtk 2.0.8
2009-10-28 21:07:02 status unpacked ubiquity-frontend-gtk 2.0.8
2009-10-28 21:07:02 status unpacked ubiquity-frontend-gtk 2.0.8
2009-10-28 21:07:02 install ubiquity-ubuntu-artwork <none> 2.0.8
2009-10-28 21:07:02 status half-installed ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:02 status unpacked ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:02 status unpacked ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:02 install ubiquity-casper <none> 1.206
2009-10-28 21:07:02 status half-installed ubiquity-casper 1.206
2009-10-28 21:07:02 status unpacked ubiquity-casper 1.206
2009-10-28 21:07:02 status unpacked ubiquity-casper 1.206
2009-10-28 21:07:03 install ubiquity <none> 2.0.8
2009-10-28 21:07:03 status half-installed ubiquity 2.0.8
2009-10-28 21:07:03 status half-installed ubiquity 2.0.8
2009-10-28 21:07:03 status half-installed ubiquity 2.0.8
2009-10-28 21:07:03 status half-installed ubiquity 2.0.8
2009-10-28 21:07:03 status unpacked ubiquity 2.0.8
2009-10-28 21:07:03 status unpacked ubiquity 2.0.8
2009-10-28 21:07:03 install ubiquity-slideshow-ubuntu <none> 10
2009-10-28 21:07:03 status half-installed ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:04 status unpacked ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:04 status unpacked ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:04 install xfsprogs <none> 3.0.2
2009-10-28 21:07:04 status half-installed xfsprogs 3.0.2
2009-10-28 21:07:04 status half-installed xfsprogs 3.0.2
2009-10-28 21:07:04 status unpacked xfsprogs 3.0.2
2009-10-28 21:07:04 status unpacked xfsprogs 3.0.2
2009-10-28 21:07:04 install user-setup <none> 1.27ubuntu11
2009-10-28 21:07:04 status half-installed user-setup 1.27ubuntu11
2009-10-28 21:07:04 status unpacked user-setup 1.27ubuntu11
2009-10-28 21:07:04 status unpacked user-setup 1.27ubuntu11
2009-10-28 21:07:04 install casper <none> 1.206
2009-10-28 21:07:04 status half-installed casper 1.206
2009-10-28 21:07:04 status half-installed casper 1.206
2009-10-28 21:07:04 status half-installed casper 1.206
2009-10-28 21:07:04 status unpacked casper 1.206
2009-10-28 21:07:04 status unpacked casper 1.206
2009-10-28 21:07:04 install kpartx <none> 0.4.8-14ubuntu2
2009-10-28 21:07:04 status half-installed kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:04 status half-installed kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:04 status unpacked kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:04 status unpacked kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:04 install lupin-casper <none> 0.27
2009-10-28 21:07:04 status half-installed lupin-casper 0.27
2009-10-28 21:07:04 status unpacked lupin-casper 0.27
2009-10-28 21:07:04 status unpacked lupin-casper 0.27
2009-10-28 21:07:04 trigproc software-center 1.0.2 1.0.2
2009-10-28 21:07:04 status half-configured software-center 1.0.2
2009-10-28 21:07:05 status installed software-center 1.0.2
2009-10-28 21:07:05 trigproc sreadahead 1.0-5 1.0-5
2009-10-28 21:07:05 status half-configured sreadahead 1.0-5
2009-10-28 21:07:05 status installed sreadahead 1.0-5
2009-10-28 21:07:05 trigproc man-db 2.5.6-2 2.5.6-2
2009-10-28 21:07:05 status half-configured man-db 2.5.6-2
2009-10-28 21:07:05 status installed man-db 2.5.6-2
2009-10-28 21:07:05 trigproc hicolor-icon-theme 0.10-2 0.10-2
2009-10-28 21:07:05 status half-configured hicolor-icon-theme 0.10-2
2009-10-28 21:07:06 status installed hicolor-icon-theme 0.10-2
2009-10-28 21:07:06 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2009-10-28 21:07:06 status half-configured desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:07:06 status installed desktop-file-utils 0.15-2ubuntu1
2009-10-28 21:07:06 startup packages configure
2009-10-28 21:07:06 configure cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status unpacked cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status half-configured cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status installed cryptsetup 2:1.0.6+20090405.svn49-1ubuntu7
2009-10-28 21:07:06 status triggers-pending initramfs-tools 0.92bubuntu53
2009-10-28 21:07:06 configure libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status unpacked libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status half-configured libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status installed libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-10-28 21:07:06 configure dmraid 1.0.0.rc15-11ubuntu3 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status unpacked dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status half-configured dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 status installed dmraid 1.0.0.rc15-11ubuntu3
2009-10-28 21:07:06 configure libecryptfs0 81-0ubuntu3 81-0ubuntu3
2009-10-28 21:07:06 status unpacked libecryptfs0 81-0ubuntu3
2009-10-28 21:07:06 status half-configured libecryptfs0 81-0ubuntu3
2009-10-28 21:07:06 status installed libecryptfs0 81-0ubuntu3
2009-10-28 21:07:06 configure keyutils 1.2-10 1.2-10
2009-10-28 21:07:06 status unpacked keyutils 1.2-10
2009-10-28 21:07:06 status unpacked keyutils 1.2-10
2009-10-28 21:07:06 status half-configured keyutils 1.2-10
2009-10-28 21:07:06 status installed keyutils 1.2-10
2009-10-28 21:07:06 configure ecryptfs-utils 81-0ubuntu3 81-0ubuntu3
2009-10-28 21:07:06 status unpacked ecryptfs-utils 81-0ubuntu3
2009-10-28 21:07:06 status half-configured ecryptfs-utils 81-0ubuntu3
2009-10-28 21:07:08 status installed ecryptfs-utils 81-0ubuntu3
2009-10-28 21:07:08 configure gparted 0.4.5-2ubuntu1 0.4.5-2ubuntu1
2009-10-28 21:07:08 status unpacked gparted 0.4.5-2ubuntu1
2009-10-28 21:07:08 status half-configured gparted 0.4.5-2ubuntu1
2009-10-28 21:07:08 status installed gparted 0.4.5-2ubuntu1
2009-10-28 21:07:08 configure jfsutils 1.1.12-2 1.1.12-2
2009-10-28 21:07:08 status unpacked jfsutils 1.1.12-2
2009-10-28 21:07:08 status half-configured jfsutils 1.1.12-2
2009-10-28 21:07:08 status installed jfsutils 1.1.12-2
2009-10-28 21:07:08 configure myspell-en-au 2.1-3.1 2.1-3.1
2009-10-28 21:07:08 status unpacked myspell-en-au 2.1-3.1
2009-10-28 21:07:08 status half-configured myspell-en-au 2.1-3.1
2009-10-28 21:07:08 status installed myspell-en-au 2.1-3.1
2009-10-28 21:07:08 configure myspell-en-gb 1:3.0.1-8ubuntu1 1:3.0.1-8ubuntu1
2009-10-28 21:07:08 status unpacked myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:07:08 status half-configured myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:07:08 status installed myspell-en-gb 1:3.0.1-8ubuntu1
2009-10-28 21:07:08 configure wamerican 6-3 6-3
2009-10-28 21:07:08 status unpacked wamerican 6-3
2009-10-28 21:07:08 status half-configured wamerican 6-3
2009-10-28 21:07:09 status installed wamerican 6-3
2009-10-28 21:07:09 configure wbritish 6-3 6-3
2009-10-28 21:07:09 status unpacked wbritish 6-3
2009-10-28 21:07:09 status half-configured wbritish 6-3
2009-10-28 21:07:11 status installed wbritish 6-3
2009-10-28 21:07:11 configure openoffice.org-thesaurus-en-au 2.1-3.1 2.1-3.1
2009-10-28 21:07:11 status unpacked openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:11 status half-configured openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:11 status installed openoffice.org-thesaurus-en-au 2.1-3.1
2009-10-28 21:07:11 configure myspell-en-za 1:3.0.1-8ubuntu1 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status unpacked myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status half-configured myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status installed myspell-en-za 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 configure openoffice.org-hyphenation 0.3 0.3
2009-10-28 21:07:11 status unpacked openoffice.org-hyphenation 0.3
2009-10-28 21:07:11 status half-configured openoffice.org-hyphenation 0.3
2009-10-28 21:07:11 status installed openoffice.org-hyphenation 0.3
2009-10-28 21:07:11 configure openoffice.org-hyphenation-en-us 2.4-4 2.4-4
2009-10-28 21:07:11 status unpacked openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:11 status half-configured openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:11 status installed openoffice.org-hyphenation-en-us 2.4-4
2009-10-28 21:07:11 configure openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status unpacked openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status half-configured openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 status installed openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1
2009-10-28 21:07:11 configure libdebconfclient0 0.145 0.145
2009-10-28 21:07:11 status unpacked libdebconfclient0 0.145
2009-10-28 21:07:11 status half-configured libdebconfclient0 0.145
2009-10-28 21:07:11 status installed libdebconfclient0 0.145
2009-10-28 21:07:11 configure libdebian-installer4 0.63ubuntu2 0.63ubuntu2
2009-10-28 21:07:11 status unpacked libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:11 status half-configured libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:11 status installed libdebian-installer4 0.63ubuntu2
2009-10-28 21:07:11 configure libntfs10 2.0.0-1ubuntu3 2.0.0-1ubuntu3
2009-10-28 21:07:11 status unpacked libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:11 status half-configured libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:11 status installed libntfs10 2.0.0-1ubuntu3
2009-10-28 21:07:11 configure libreadline5 5.2-6 5.2-6
2009-10-28 21:07:11 status unpacked libreadline5 5.2-6
2009-10-28 21:07:11 status half-configured libreadline5 5.2-6
2009-10-28 21:07:11 status installed libreadline5 5.2-6
2009-10-28 21:07:11 configure localechooser-data 2.12ubuntu2 2.12ubuntu2
2009-10-28 21:07:11 status unpacked localechooser-data 2.12ubuntu2
2009-10-28 21:07:11 status half-configured localechooser-data 2.12ubuntu2
2009-10-28 21:07:11 status installed localechooser-data 2.12ubuntu2
2009-10-28 21:07:11 configure ntfsprogs 2.0.0-1ubuntu3 2.0.0-1ubuntu3
2009-10-28 21:07:11 status unpacked ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:11 status half-configured ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:11 status installed ntfsprogs 2.0.0-1ubuntu3
2009-10-28 21:07:11 configure python-pyicu 0.8.1-3ubuntu2 0.8.1-3ubuntu2
2009-10-28 21:07:11 status unpacked python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:11 status half-configured python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:11 status installed python-pyicu 0.8.1-3ubuntu2
2009-10-28 21:07:11 status triggers-pending python-support 1.0.3ubuntu1
2009-10-28 21:07:11 configure rdate 1:1.2-1 1:1.2-1
2009-10-28 21:07:11 status unpacked rdate 1:1.2-1
2009-10-28 21:07:11 status half-configured rdate 1:1.2-1
2009-10-28 21:07:11 status installed rdate 1:1.2-1
2009-10-28 21:07:11 configure reiserfsprogs 1:3.6.21-1 1:3.6.21-1
2009-10-28 21:07:11 status unpacked reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:11 status half-configured reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:11 status installed reiserfsprogs 1:3.6.21-1
2009-10-28 21:07:11 configure ubiquity-ubuntu-artwork 2.0.8 2.0.8
2009-10-28 21:07:11 status unpacked ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:11 status half-configured ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:11 status installed ubiquity-ubuntu-artwork 2.0.8
2009-10-28 21:07:11 configure ubiquity-casper 1.206 1.206
2009-10-28 21:07:11 status unpacked ubiquity-casper 1.206
2009-10-28 21:07:11 status half-configured ubiquity-casper 1.206
2009-10-28 21:07:11 status installed ubiquity-casper 1.206
2009-10-28 21:07:11 configure ubiquity-slideshow-ubuntu 10 10
2009-10-28 21:07:11 status unpacked ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:11 status half-configured ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:11 status installed ubiquity-slideshow-ubuntu 10
2009-10-28 21:07:11 configure xfsprogs 3.0.2 3.0.2
2009-10-28 21:07:11 status unpacked xfsprogs 3.0.2
2009-10-28 21:07:11 status half-configured xfsprogs 3.0.2
2009-10-28 21:07:11 status installed xfsprogs 3.0.2
2009-10-28 21:07:11 configure user-setup 1.27ubuntu11 1.27ubuntu11
2009-10-28 21:07:11 status unpacked user-setup 1.27ubuntu11
2009-10-28 21:07:11 status half-configured user-setup 1.27ubuntu11
2009-10-28 21:07:13 status installed user-setup 1.27ubuntu11
2009-10-28 21:07:13 configure casper 1.206 1.206
2009-10-28 21:07:13 status unpacked casper 1.206
2009-10-28 21:07:13 status unpacked casper 1.206
2009-10-28 21:07:13 status unpacked casper 1.206
2009-10-28 21:07:13 status half-configured casper 1.206
2009-10-28 21:07:13 status installed casper 1.206
2009-10-28 21:07:13 configure kpartx 0.4.8-14ubuntu2 0.4.8-14ubuntu2
2009-10-28 21:07:13 status unpacked kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:13 status half-configured kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:13 status installed kpartx 0.4.8-14ubuntu2
2009-10-28 21:07:13 configure lupin-casper 0.27 0.27
2009-10-28 21:07:13 status unpacked lupin-casper 0.27
2009-10-28 21:07:13 status half-configured lupin-casper 0.27
2009-10-28 21:07:13 status installed lupin-casper 0.27
2009-10-28 21:07:13 configure language-support-writing-en 1:9.10+20090909 1:9.10+20090909
2009-10-28 21:07:13 status unpacked language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:13 status half-configured language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:39 status installed language-support-writing-en 1:9.10+20090909
2009-10-28 21:07:39 configure language-support-en 1:9.10+20090909 1:9.10+20090909
2009-10-28 21:07:39 status unpacked language-support-en 1:9.10+20090909
2009-10-28 21:07:39 status half-configured language-support-en 1:9.10+20090909
2009-10-28 21:07:39 status installed language-support-en 1:9.10+20090909
2009-10-28 21:07:39 configure language-pack-pt 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:39 status unpacked language-pack-pt 1:9.10+20091022
2009-10-28 21:07:39 status half-configured language-pack-pt 1:9.10+20091022
2009-10-28 21:07:39 status installed language-pack-pt 1:9.10+20091022
2009-10-28 21:07:39 configure language-pack-xh 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:39 status unpacked language-pack-xh 1:9.10+20091022
2009-10-28 21:07:39 status half-configured language-pack-xh 1:9.10+20091022
2009-10-28 21:07:39 status installed language-pack-xh 1:9.10+20091022
2009-10-28 21:07:39 configure language-pack-bn 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:39 status unpacked language-pack-bn 1:9.10+20091022
2009-10-28 21:07:39 status half-configured language-pack-bn 1:9.10+20091022
2009-10-28 21:07:39 status installed language-pack-bn 1:9.10+20091022
2009-10-28 21:07:39 configure language-pack-bn-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:39 status unpacked language-pack-bn-base 1:9.10+20091022
2009-10-28 21:07:39 status half-configured language-pack-bn-base 1:9.10+20091022
2009-10-28 21:07:42 status installed language-pack-bn-base 1:9.10+20091022
2009-10-28 21:07:42 configure language-pack-de 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:42 status unpacked language-pack-de 1:9.10+20091022
2009-10-28 21:07:42 status half-configured language-pack-de 1:9.10+20091022
2009-10-28 21:07:42 status installed language-pack-de 1:9.10+20091022
2009-10-28 21:07:42 configure language-pack-de-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:42 status unpacked language-pack-de-base 1:9.10+20091022
2009-10-28 21:07:42 status half-configured language-pack-de-base 1:9.10+20091022
2009-10-28 21:07:52 status installed language-pack-de-base 1:9.10+20091022
2009-10-28 21:07:52 configure language-pack-en 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:52 status unpacked language-pack-en 1:9.10+20091022
2009-10-28 21:07:52 status half-configured language-pack-en 1:9.10+20091022
2009-10-28 21:07:52 status installed language-pack-en 1:9.10+20091022
2009-10-28 21:07:52 configure language-pack-en-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:07:52 status unpacked language-pack-en-base 1:9.10+20091022
2009-10-28 21:07:52 status half-configured language-pack-en-base 1:9.10+20091022
2009-10-28 21:08:20 status installed language-pack-en-base 1:9.10+20091022
2009-10-28 21:08:20 configure language-pack-es 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:08:20 status unpacked language-pack-es 1:9.10+20091022
2009-10-28 21:08:20 status half-configured language-pack-es 1:9.10+20091022
2009-10-28 21:08:20 status installed language-pack-es 1:9.10+20091022
2009-10-28 21:08:20 configure language-pack-es-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:08:20 status unpacked language-pack-es-base 1:9.10+20091022
2009-10-28 21:08:20 status half-configured language-pack-es-base 1:9.10+20091022
2009-10-28 21:08:53 status installed language-pack-es-base 1:9.10+20091022
2009-10-28 21:08:53 configure language-pack-fr 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:08:53 status unpacked language-pack-fr 1:9.10+20091022
2009-10-28 21:08:53 status half-configured language-pack-fr 1:9.10+20091022
2009-10-28 21:08:53 status installed language-pack-fr 1:9.10+20091022
2009-10-28 21:08:53 configure language-pack-fr-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:08:53 status unpacked language-pack-fr-base 1:9.10+20091022
2009-10-28 21:08:53 status half-configured language-pack-fr-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-fr-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-bn 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-bn 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-bn-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-bn-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-de 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-de 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-de-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-de-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-en 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-en 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-en-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-en-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-es 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-es 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-es-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-es-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-fr 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-fr 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-gnome-fr-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:09:02 status installed language-pack-gnome-fr-base 1:9.10+20091022
2009-10-28 21:09:02 configure language-pack-pt-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:02 status unpacked language-pack-pt-base 1:9.10+20091022
2009-10-28 21:09:02 status half-configured language-pack-pt-base 1:9.10+20091022
2009-10-28 21:09:05 status installed language-pack-pt-base 1:9.10+20091022
2009-10-28 21:09:05 configure language-pack-gnome-pt 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:05 status unpacked language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:09:05 status half-configured language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:09:05 status installed language-pack-gnome-pt 1:9.10+20091022
2009-10-28 21:09:05 configure language-pack-gnome-pt-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:05 status unpacked language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:09:05 status half-configured language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:09:05 status installed language-pack-gnome-pt-base 1:9.10+20091022
2009-10-28 21:09:05 configure language-pack-xh-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:05 status unpacked language-pack-xh-base 1:9.10+20091022
2009-10-28 21:09:05 status half-configured language-pack-xh-base 1:9.10+20091022
2009-10-28 21:09:07 status installed language-pack-xh-base 1:9.10+20091022
2009-10-28 21:09:07 configure language-pack-gnome-xh 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:07 status unpacked language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:09:07 status half-configured language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:09:07 status installed language-pack-gnome-xh 1:9.10+20091022
2009-10-28 21:09:07 configure language-pack-gnome-xh-base 1:9.10+20091022 1:9.10+20091022
2009-10-28 21:09:07 status unpacked language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:09:07 status half-configured language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:09:07 status installed language-pack-gnome-xh-base 1:9.10+20091022
2009-10-28 21:09:07 configure ubiquity 2.0.8 2.0.8
2009-10-28 21:09:07 status unpacked ubiquity 2.0.8
2009-10-28 21:09:07 status unpacked ubiquity 2.0.8
2009-10-28 21:09:07 status half-configured ubiquity 2.0.8
2009-10-28 21:09:12 status installed ubiquity 2.0.8
2009-10-28 21:09:12 configure ubiquity-frontend-gtk 2.0.8 2.0.8
2009-10-28 21:09:12 status unpacked ubiquity-frontend-gtk 2.0.8
2009-10-28 21:09:12 status half-configured ubiquity-frontend-gtk 2.0.8
2009-10-28 21:09:13 status installed ubiquity-frontend-gtk 2.0.8
2009-10-28 21:09:13 trigproc initramfs-tools 0.92bubuntu53 0.92bubuntu53
2009-10-28 21:09:13 status half-configured initramfs-tools 0.92bubuntu53
2009-10-28 21:09:27 status installed initramfs-tools 0.92bubuntu53
2009-10-28 21:09:27 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-10-28 21:09:27 status half-configured libc-bin 2.10.1-0ubuntu15
2009-10-28 21:09:28 status installed libc-bin 2.10.1-0ubuntu15
2009-10-28 21:09:28 trigproc python-support 1.0.3ubuntu1 1.0.3ubuntu1
2009-10-28 21:09:28 status half-configured python-support 1.0.3ubuntu1
2009-10-28 21:09:28 status installed python-support 1.0.3ubuntu1
2010-01-12 00:00:10 update-alternatives: run with --set libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo
2010-01-12 00:00:10 update-alternatives: status of link group libgksu-gconf-defaults set to manual
2010-01-12 00:05:46 startup packages purge
2010-01-12 00:12:06 update-alternatives: run with --install /usr/bin/js js /usr/bin/rhino 100 --slave /usr/share/man/man1/js.1.gz js.1.gz /usr/share/man/man1/rhino.1.gz
2010-01-12 00:12:06 update-alternatives: link group js updated to point to /usr/bin/rhino
2010-01-12 00:12:07 update-alternatives: run with --install /usr/bin/java java /usr/lib/jvm/java-6-openjdk/jre/bin/java 1061 --slave /usr/share/man/man1/java.1.gz java.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
2010-01-12 00:12:07 update-alternatives: link group java updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/java
2010-01-12 00:12:08 update-alternatives: run with --install /usr/bin/keytool keytool /usr/lib/jvm/java-6-openjdk/jre/bin/keytool 1061 --slave /usr/share/man/man1/keytool.1.gz keytool.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/keytool.1.gz
2010-01-12 00:12:08 update-alternatives: link group keytool updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/keytool
2010-01-12 00:12:08 update-alternatives: run with --install /usr/bin/pack200 pack200 /usr/lib/jvm/java-6-openjdk/jre/bin/pack200 1061 --slave /usr/share/man/man1/pack200.1.gz pack200.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/pack200.1.gz
2010-01-12 00:12:08 update-alternatives: link group pack200 updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/pack200
2010-01-12 00:12:08 update-alternatives: run with --install /usr/bin/rmid rmid /usr/lib/jvm/java-6-openjdk/jre/bin/rmid 1061 --slave /usr/share/man/man1/rmid.1.gz rmid.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/rmid.1.gz
2010-01-12 00:12:08 update-alternatives: link group rmid updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/rmid
2010-01-12 00:12:08 update-alternatives: run with --install /usr/bin/rmiregistry rmiregistry /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry 1061 --slave /usr/share/man/man1/rmiregistry.1.gz rmiregistry.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/rmiregistry.1.gz
2010-01-12 00:12:08 update-alternatives: link group rmiregistry updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
2010-01-12 00:12:08 update-alternatives: run with --install /usr/bin/unpack200 unpack200 /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200 1061 --slave /usr/share/man/man1/unpack200.1.gz unpack200.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/unpack200.1.gz
2010-01-12 00:12:08 update-alternatives: link group unpack200 updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
2010-01-12 00:12:09 update-alternatives: run with --install /usr/bin/orbd orbd /usr/lib/jvm/java-6-openjdk/jre/bin/orbd 1061 --slave /usr/share/man/man1/orbd.1.gz orbd.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/orbd.1.gz
2010-01-12 00:12:09 update-alternatives: link group orbd updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/orbd
2010-01-12 00:12:09 update-alternatives: run with --install /usr/bin/servertool servertool /usr/lib/jvm/java-6-openjdk/jre/bin/servertool 1061 --slave /usr/share/man/man1/servertool.1.gz servertool.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/servertool.1.gz
2010-01-12 00:12:09 update-alternatives: link group servertool updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/servertool
2010-01-12 00:12:09 update-alternatives: run with --install /usr/bin/tnameserv tnameserv /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv 1061 --slave /usr/share/man/man1/tnameserv.1.gz tnameserv.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/tnameserv.1.gz
2010-01-12 00:12:09 update-alternatives: link group tnameserv updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
2010-01-12 00:12:09 update-alternatives: run with --install /usr/bin/jexec jexec /usr/lib/jvm/java-6-openjdk/jre/lib/jexec 1061 --slave /usr/share/binfmts/jar jexec-binfmt /usr/lib/jvm/java-6-openjdk/jre/lib/jar.binfmt
2010-01-12 00:12:09 update-alternatives: link group jexec updated to point to /usr/lib/jvm/java-6-openjdk/jre/lib/jexec
2010-01-12 00:12:17 update-alternatives: run with --install /usr/bin/javaws javaws /usr/lib/jvm/java-6-openjdk/jre/bin/javaws 1061 --slave /usr/share/man/man1/javaws.1.gz javaws.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/javaws.1.gz
2010-01-12 00:12:17 update-alternatives: link group javaws updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/javaws
2010-01-12 00:12:17 update-alternatives: run with --install /usr/bin/pluginappletviewer pluginappletviewer /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer 1061
2010-01-12 00:12:17 update-alternatives: link group pluginappletviewer updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer
2010-01-12 00:12:17 update-alternatives: run with --install /usr/bin/policytool policytool /usr/lib/jvm/java-6-openjdk/jre/bin/policytool 1061 --slave /usr/share/man/man1/policytool.1.gz policytool.1.gz /usr/lib/jvm/java-6-openjdk/jre/man/man1/policytool.1.gz
2010-01-12 00:12:17 update-alternatives: link group policytool updated to point to /usr/lib/jvm/java-6-openjdk/jre/bin/policytool
2010-01-12 00:12:18 update-alternatives: run with --quiet --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so 1061
2010-01-12 00:12:18 update-alternatives: link group mozilla-javaplugin.so updated to point to /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

```

---

### Post by 7o7YlUcb on 2010-01-12
I deleted ubuntu 9.10 and installed 9.04 instead (below 137GB - thanks for that tip). It works perfectly. I then used the upgrade thing from within 9.04 to upgrade to 9.10 and it still works. I guess there are differences between an upgrade and a clean install of 9.10. For instance Grub is still at version 0.97. So I'm going to blame Grub 2 for most of my problems. 
Thanks to everybody for looking into this.
Cheers.

---

### Post by meierfra. on 2010-01-12
> This time I did get a grub menu but with two different memtest options and windows XP 

Very weird.  But since you reinstalled, we won't be able to figure out the cause. I doubt it had anything to do with the 137GB limit (that only effects the booting)


> So I'm going to blame Grub 2 for most of my problems. 
Legacy Grub is also effected by the 137GB limit. The most blame goes to your bios. But  I read  the Grub 2 developers are trying to find a way around that problem.


> and it still works. 
Glad you could it resolved.

---

