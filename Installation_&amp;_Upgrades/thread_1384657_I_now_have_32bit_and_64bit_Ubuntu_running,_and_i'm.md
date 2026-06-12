---
title: "I now have 32bit and 64bit Ubuntu running, and i'm wanting to get rid of 32bit."
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Dixi1801 on 2010-01-18
How would i go about this?

When my computer starts up I have a lot of loaders in my grub and i want to get rid of some!

Could I do this with GParted or would I be best just doing a fresh install of Windows and Ubuntu?

Thanks in advance :)

---

### Post by presence1960 on 2010-01-18
What version of Ubuntu are you running and what GRUB do you use?

Do the following to give all info needed: Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Dixi1801 on 2010-01-19
> **presence1960 said:**
> What version of Ubuntu are you running and what GRUB do you use?

Do the following to give all info needed: Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Did exactly as you said and here is the result:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.
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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x133cae7e

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176   327,249,919   297,887,744   7 HPFS/NTFS
/dev/sda3         327,249,920   333,542,407     6,292,488   7 HPFS/NTFS
/dev/sda4         333,557,595   625,137,344   291,579,750   5 Extended
/dev/sda5         333,557,658   395,439,974    61,882,317  83 Linux
/dev/sda6         613,217,178   625,137,344    11,920,167  82 Linux swap / Solaris
/dev/sda7         395,440,038   604,268,909   208,828,872  83 Linux
/dev/sda8         604,268,973   613,217,114     8,948,142  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4E08AABD08AAA385" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="8CBC2F60BC2F4454" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="E886633486630304" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="11a85435-3cc6-45e1-bc7e-87e0dd9fc077" TYPE="ext4" 
/dev/sda6: UUID="916dd6f3-ee3f-4466-b469-0bbcfb51dc7e" TYPE="swap" 
/dev/sda7: UUID="29006757-d5bc-4f42-be75-e380b2dbe835" TYPE="ext4" 
/dev/sda8: UUID="e5a24908-34fd-4479-884d-874ca06b625d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dixi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dixi)


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
search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro single 
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
    search --no-floppy --fs-uuid --set 4e08aabd08aaa385
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8cbc2f60bc2f4454
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
UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=916dd6f3-ee3f-4466-b469-0bbcfb51dc7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 170.7GB: boot/grub/core.img
 170.7GB: boot/grub/grub.cfg
 170.7GB: boot/initrd.img-2.6.31-14-generic
 170.7GB: boot/initrd.img-2.6.31-17-generic
 170.7GB: boot/vmlinuz-2.6.31-14-generic
 170.7GB: boot/vmlinuz-2.6.31-17-generic
 170.7GB: initrd.img
 170.7GB: initrd.img.old
 170.7GB: vmlinuz
 170.7GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 29006757-d5bc-4f42-be75-e380b2dbe835
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 29006757-d5bc-4f42-be75-e380b2dbe835
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=29006757-d5bc-4f42-be75-e380b2dbe835 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 29006757-d5bc-4f42-be75-e380b2dbe835
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=29006757-d5bc-4f42-be75-e380b2dbe835 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 29006757-d5bc-4f42-be75-e380b2dbe835
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=29006757-d5bc-4f42-be75-e380b2dbe835 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 29006757-d5bc-4f42-be75-e380b2dbe835
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=29006757-d5bc-4f42-be75-e380b2dbe835 ro single 
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
    search --no-floppy --fs-uuid --set 4e08aabd08aaa385
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8cbc2f60bc2f4454
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 11a85435-3cc6-45e1-bc7e-87e0dd9fc077
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=11a85435-3cc6-45e1-bc7e-87e0dd9fc077 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=29006757-d5bc-4f42-be75-e380b2dbe835 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e5a24908-34fd-4479-884d-874ca06b625d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 202.4GB: boot/grub/core.img
 202.4GB: boot/grub/grub.cfg
 202.4GB: boot/initrd.img-2.6.31-14-generic
 202.4GB: boot/initrd.img-2.6.31-17-generic
 202.4GB: boot/vmlinuz-2.6.31-14-generic
 202.4GB: boot/vmlinuz-2.6.31-17-generic
 202.4GB: initrd.img
 202.4GB: initrd.img.old
 202.4GB: vmlinuz
 202.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 

:) many thanks for your help again

---

### Post by presence1960 on 2010-01-19
Now the million $$ question. Which is the 32 bit? 

If it is sda5 you can use gparted from the 64 bit ubuntu to remove or format that partition (sda5).

But if 32 bit ubuntu is sda7 you can boot into 64 bit ubuntu (sda5) and remove or format sda7 with gparted. But immediately after doing this open a terminal and run ```
sudo grub-install /dev/sda
```
Reboot & see if Ubuntu boots.

Just in case you get a GRUB error or it won't boot do this:

Boot from the Live CD & choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```
This will mount your ubuntu partition. Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB on MBR and pointing to sda5

---

