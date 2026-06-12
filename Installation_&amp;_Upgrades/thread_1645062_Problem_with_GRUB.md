---
title: "Problem with GRUB?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by davidbilla on 2010-12-14
I've come upon a system which dual boots Ubuntu 10.04 and Windows 7, and it uses GRUB2. Linux was installed first and after sometime Windows 7 was installed on it, the GRUB reinstalled so that it recognizes both Linux and Windows and all was well.

Now, when the system is started up, it presents the GRUB menu from which you can boot into windows but not into ubuntu; it just presents a blank screen. As I understand, no upgrades to linux or windows had been done and people had been using it only with Windows for a few months, so no one recognized this problem with linux until now.

I don't know whether the problem is with GRUB since one can and does boot into windows everyday from the same GRUB menu. Any ideas?

---

### Post by davidbilla on 2010-12-14
I found that in the menu entries for the linux kernels, the set root parameter value is '(hd0,1)' while it's actually supposed to be (hd0,0).

I have now booted from a live CD. Is it ok to mount the 'boot' partition of my linux installation and edit grub/grub.cfg?

This is the file 'RESULTS.txt' obtained by running bootinfoscript.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /grub/core.img 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2    *        499,712   100,499,455    99,999,744   7 HPFS/NTFS
/dev/sda3         100,501,502   976,773,119   876,271,618   5 Extended
/dev/sda5         100,501,504   108,451,839     7,950,336  82 Linux swap / Solaris
/dev/sda6         108,453,888   140,451,839    31,997,952  83 Linux
/dev/sda7         140,453,888   240,451,583    99,997,696  83 Linux
/dev/sda8         240,453,632   640,452,607   399,998,976  83 Linux
/dev/sda9         640,454,656   976,773,119   336,318,464  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4b6ee817-2479-49d3-9c57-e2f696a191f8   ext4                                     
/dev/sda2        4E42B63042B61CA1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7c9e3a59-d10a-45e5-8890-7555f815f80f   swap                                     
/dev/sda6        3b94e11d-7c25-4417-98a7-cc68fa00f705   ext4                                     
/dev/sda7        4f235f0e-d532-4ba1-bd8a-7564d24ec286   ext4                                     
/dev/sda8        0aa2b979-5427-4bcc-b753-b88e8fb1a6c4   ext4                                     
/dev/sda9        8b56e20b-4baf-4d89-8720-8a47f3160736   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/3b94e11d-7c25-4417-98a7-cc68fa00f705 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/4b6ee817-2479-49d3-9c57-e2f696a191f8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/apt               iso9660    (ro)


============================= sda1/grub/grub.cfg: =============================

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
set default="8"
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3b94e11d-7c25-4417-98a7-cc68fa00f705
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-25-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro  splash vga=795  quiet splash
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /vmlinuz-2.6.32-25-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-24-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro  splash vga=795  quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-23-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro  splash vga=795  quiet splash
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /vmlinuz-2.6.32-23-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro  splash vga=795  quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4e42b63042b61ca1
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3b94e11d-7c25-4417-98a7-cc68fa00f705
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
set locale_dir=($root)/grub/locale
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-24-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-23-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro   quiet splash
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /vmlinuz-2.6.32-23-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4b6ee817-2479-49d3-9c57-e2f696a191f8
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
menuentry "Microsoft Windows Seven Retail (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4E42B63042B61CA1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: initrd.img-2.6.32-23-generic
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: initrd.img-2.6.32-25-generic
    .0GB: vmlinuz-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-23-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-25-generic

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
UUID=3b94e11d-7c25-4417-98a7-cc68fa00f705 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=4b6ee817-2479-49d3-9c57-e2f696a191f8 /boot           ext4    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=8b56e20b-4baf-4d89-8720-8a47f3160736 /home           ext4    defaults        0       2
# /usr/local was on /dev/sda7 during installation
UUID=4f235f0e-d532-4ba1-bd8a-7564d24ec286 /usr/local      ext4    defaults        0       2
# /vmware was on /dev/sda8 during installation
UUID=0aa2b979-5427-4bcc-b753-b88e8fb1a6c4 /vmware         ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=3715-D6DE  /windows        vfat    defaults,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=7c9e3a59-d10a-45e5-8890-7555f815f80f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by ajgreeny on 2010-12-14
I am not an expert but the main thing I note is that there are two grub.cfg files, one on **sda1/grub/grub.cfg** and the second in **sda1/boot/grub/grub.cfg**.  I think this is unusual, and may be confusing the system, though it is true to say that the one which should be read by grub itself, which appears to be in the right place (dev/sda) seems to be incorrect, with the confusion in the set root=, where both HD0,1 and HD0,6 are showing, though their positions seem to be reversed in the two files.  Study the two carefully and you may see what I mean.

I will have to leave this to others to help more with this, I'm afraid, but don't despair, I think there must be a way round the problem.

---

### Post by dandnsmith on 2010-12-14
I think you must have been reading grub1 info -
grub2 has changed the way partitions are numbered (to help people?) and now starts from 1 **not** 0

Since you have grub2, changing to 0 would be a big mistake.

HTH

---

### Post by ajgreeny on 2010-12-14
> **dandnsmith said:**
> I think you must have been reading grub1 info -
grub2 has changed the way partitions are numbered (to help people?) and now starts from 1 **not** 0

Since you have grub2, changing to 0 would be a big mistake.

HTH
This, however, does not sort out the two grub.cfg files both of which are wrong, as far as I can see.

---

### Post by Rubi1200 on 2010-12-14
Bit of an odd setup there...hmm?

You have a /boot partition, which is a bit outdated but fine.

But I am not sure why you have a separate /usr/local partition or a /vmware partition?

I also recommend deleting the /grldr on sda2.
Anyway, as ajgreeny already pointed out, having 2 grub.cfg and 2 core.img files is quite likely to cause problems.

I suggest trying to reinstall GRUB, but using the method outlined here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

You need to use the 3rd method, chroot.

Read the instructions carefully; it tells you how to deal with a separate /boot partition, which is what you have.

If the install runs successfully, you should be able to boot Ubuntu again.

If so, run ```
sudo update-grub
``` back in Ubuntu to pick up the Windows installation.

Let us know how it goes or if you need assistance with the instructions.

---

