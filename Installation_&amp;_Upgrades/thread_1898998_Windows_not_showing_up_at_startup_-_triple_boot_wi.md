---
title: "Windows not showing up at startup - triple boot with arch and ubuntu"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by Vanatiq on 2011-12-22
Hi,

I'm a complete newbie when it comes to Linux. During the last weeks, I've installed some Linux distroes alongside Windows 7 to simply check them out. Started with Ubuntu and Windows 7,  and the boot loader worked fine with those. However, now I have Windows 7, Arch Linux and a fresh install of Ubuntu, and Windows 7 aren't showing up in the boot loader.

I have two HDDs, both of them are 250GB. SDA has a partition for Windows 7 (200 GB) and another for Arch Linux (50 GB). SDB has a partition for Ubuntu (50GB) and a second partition of 200 GB for storage of pictures, videos, documents etc.

I decided to reinstall Windows 7 today, as well as installing Ubuntu. Seeing that I wanted Ubuntu's boot loader, I reinstalled Windows first and logged in to check that everything went fine. Then I installed Ubuntu. When the installation was finished, only Ubuntu and Arch showed up in the boot loader.

Here's the output from fdisk -l:
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005eaaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19685   158014464    7  HPFS/NTFS
/dev/sda3           19685       23510    30718976    7  HPFS/NTFS
/dev/sda4           23510       30402    55361505+   5  Extended
/dev/sda5           23510       26552    24434833+  83  Linux
/dev/sda6           26552       26675      987966   83  Linux
/dev/sda7           26675       27040     2931831   83  Linux
/dev/sda8           27040       27648     4883728+  83  Linux
/dev/sda9           27648       29715    16603146   83  Linux
/dev/sda10          29715       29884     1360353   82  Linux swap / Solaris
/dev/sda11          29884       30402     4159488   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000988b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24322   195364864    7  HPFS/NTFS
/dev/sdb2           24323       30402    48831489    5  Extended
/dev/sdb5           24323       24687     2928640   83  Linux
/dev/sdb6           26755       26876      975872   82  Linux swap / Solaris
/dev/sdb7           26876       30402    28319744   83  Linux
/dev/sdb8           26268       26754     3905536   83  Linux
/dev/sdb9           25903       26268     2929664   83  Linux
/dev/sdb10          24687       25902     9760768   83  Linux


Tried to search for a tutorial on solving this, but the best guide I found told me to create a thread with the results of fdisk -l and [COLOR=navy]**cat /boot/grub/menu.lst**[/COLOR] (the last one didn't work, only got errors in the terminal :s) Here's the guide: [http://forums.opensuse.org/english/information-new-users/unreviewed-how-faq/448769-edit-grub-menu-add-windows-entries.html#post2243266](http://forums.opensuse.org/english/information-new-users/unreviewed-how-faq/448769-edit-grub-menu-add-windows-entries.html#post2243266)

Thanks in advance!

---

### Post by darkod on 2011-12-22
menu.lst was used with grub1, ubuntu comes with grub2 since 9.10. That's why it reported an error.

To get more details about your setup follow the link in my signature and run the boot info script. Post the results as explained there.

It looks fine from the fdisk results but the script offers more details to know if something is wrong.

---

### Post by Vanatiq on 2011-12-22
Thanks for the quick reply! Followed the guide in the link, and here's the output I got:
```

  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 661b60c6-1e50-4c20-b182-51a191cd229d root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Arch Linux () ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   316,235,775   316,028,928   7 NTFS / exFAT / HPFS
/dev/sda3         316,235,776   377,673,727    61,437,952   7 NTFS / exFAT / HPFS
/dev/sda4         377,673,789   488,396,799   110,723,011   5 Extended
/dev/sda5         377,673,791   426,543,457    48,869,667  83 Linux
/dev/sda6         426,543,521   428,519,452     1,975,932  83 Linux
/dev/sda7         428,519,516   434,383,177     5,863,662  83 Linux
/dev/sda8         434,383,241   444,150,697     9,767,457  83 Linux
/dev/sda9         444,150,761   477,357,052    33,206,292  83 Linux
/dev/sda10        477,357,116   480,077,821     2,720,706  82 Linux swap / Solaris
/dev/sda11        480,077,824   488,396,799     8,318,976  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   390,731,775   390,729,728   7 NTFS / exFAT / HPFS
/dev/sdb2         390,733,822   488,396,799    97,662,978   5 Extended
/dev/sdb5         390,733,824   396,591,103     5,857,280  83 Linux
/dev/sdb6         429,803,520   431,755,263     1,951,744  82 Linux swap / Solaris
/dev/sdb7         431,757,312   488,396,799    56,639,488  83 Linux
/dev/sdb8         421,990,400   429,801,471     7,811,072  83 Linux
/dev/sdb9         416,120,832   421,980,159     5,859,328  83 Linux
/dev/sdb10        396,593,152   416,114,687    19,521,536  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5E02A19E02A17C21                       ntfs       System Reserved
/dev/sda10       7d0398aa-4afa-43b2-9f77-ec8fb3fcf6cc   swap       
/dev/sda2        74508E44508E0D54                       ntfs       New Volume
/dev/sda3        F8AA1745AA170034                       ntfs       
/dev/sda5        a5e4ab2e-0382-4bc1-8995-8b0f9f5cf070   ext4       
/dev/sda6        49a6ce51-6f2a-42f7-95e1-096464dd64da   ext4       
/dev/sda7        63e0e6c9-2ad2-49dc-a05a-94a1d825cb08   ext4       
/dev/sda8        b1d1bc0e-6487-4d6b-8ec9-10764dfa4286   ext4       
/dev/sda9        136030f6-4dbf-4d75-87fc-db9692a86031   ext4       
/dev/sdb1        B2D85C51D85C15C7                       ntfs       
/dev/sdb10       87292135-cc05-4b89-a80e-219c7bf555d0   ext4       
/dev/sdb5        661b60c6-1e50-4c20-b182-51a191cd229d   ext4       
/dev/sdb6        0872071c-49d8-4658-b0d5-527a6999b669   swap       
/dev/sdb7        2dc059b8-5a8d-4158-b513-45b0394c6a22   ext4       
/dev/sdb8        7909a6b6-f5b6-4f17-9dec-857e9ecda9a2   ext4       
/dev/sdb9        fd8b5fc3-2a22-4ea3-aff3-13a8125e164a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/a5e4ab2e-0382-4bc1-8995-8b0f9f5cf070 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb10       /usr                     ext4       (rw,commit=0)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,commit=0)
/dev/sdb8        /tmp                     ext4       (rw,commit=0)
/dev/sdb9        /var                     ext4       (rw,commit=0)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
/dev/sda10 swap swap defaults 0 0
/dev/sda5 / ext4 defaults 0 1
/dev/sda6 /boot ext4 defaults 0 1
/dev/sda7 /tmp ext4 defaults 0 1
/dev/sda8 /var ext4 defaults 0 1
/dev/sda9 /home ext4 defaults 0 1
--------------------------------------------------------------------------------

============================= sda6/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,5)
kernel /vmlinuz-linux root=/dev/sda5 ro
initrd /initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,5)
kernel /vmlinuz-linux root=/dev/sda5 ro
initrd /initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

# (3) Linux Mint
#title Linux Mint
#rootnoverify (hd1,1)
#makeactive
#chainloader +2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 203.520710468 = 218.528698880  grub/menu.lst                                  1
 203.550201893 = 218.560365056  grub/stage2                                    1
 203.550053120 = 218.560205312  initramfs-linux-fallback.img                   1
 203.534580708 = 218.543591936  initramfs-linux.img                            1
 203.519932270 = 218.527863296  vmlinuz-linux                                  1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sdb,msdos10)'
search --no-floppy --fs-uuid --set=root 87292135-cc05-4b89-a80e-219c7bf555d0
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=661b60c6-1e50-4c20-b182-51a191cd229d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=661b60c6-1e50-4c20-b182-51a191cd229d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=661b60c6-1e50-4c20-b182-51a191cd229d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=661b60c6-1e50-4c20-b182-51a191cd229d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 661b60c6-1e50-4c20-b182-51a191cd229d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 49a6ce51-6f2a-42f7-95e1-096464dd64da
    linux /vmlinuz-linux root=/dev/sda5 ro
    initrd /initramfs-linux.img
}
menuentry "Arch Linux Fallback (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 49a6ce51-6f2a-42f7-95e1-096464dd64da
    linux /vmlinuz-linux root=/dev/sda5 ro
    initrd /initramfs-linux-fallback.img
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=661b60c6-1e50-4c20-b182-51a191cd229d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=2dc059b8-5a8d-4158-b513-45b0394c6a22 /home           ext4    defaults        0       2
# /tmp was on /dev/sdb8 during installation
UUID=7909a6b6-f5b6-4f17-9dec-857e9ecda9a2 /tmp            ext4    defaults        0       2
# /usr was on /dev/sdb10 during installation
UUID=87292135-cc05-4b89-a80e-219c7bf555d0 /usr            ext4    defaults        0       2
# /var was on /dev/sdb9 during installation
UUID=fd8b5fc3-2a22-4ea3-aff3-13a8125e164a /var            ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=7d0398aa-4afa-43b2-9f77-ec8fb3fcf6cc none            swap    sw              0       0
/dev/sdb6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 186.653911591 = 200.418111488  boot/grub/core.img                             1
 186.781078339 = 200.554655744  boot/grub/grub.cfg                             1
 186.951034546 = 200.737144832  boot/initrd.img-2.6.38-13-generic              2
 186.709110260 = 200.477380608  boot/initrd.img-2.6.38-8-generic               2
 186.832344055 = 200.609701888  boot/vmlinuz-2.6.38-13-generic                 1
 186.696308136 = 200.463634432  boot/vmlinuz-2.6.38-8-generic                  1
 186.951034546 = 200.737144832  initrd.img                                     2
 186.709110260 = 200.477380608  initrd.img.old                                 2
 186.832344055 = 200.609701888  vmlinuz                                        1
 186.696308136 = 200.463634432  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  89 b7 9a 14 c7 39 df 69  52 f7 56 9e 37 b2 75 f8  |.....9.iR.V.7.u.|
00000010  fe c2 a4 7f bd 59 b4 fd  9c a8 17 9a 96 bc 43 2a  |.....Y........C*|
00000020  b2 b4 c4 9c be fd e7 c4  39 e7 a0 46 3a 74 ed 68  |........9..F:t.h|
00000030  88 72 f8 86 6b d1 3c 49  40 f1 55 20 39 fd ce 08  |.r..k.<I@.U 9...|
00000040  b1 a9 fb 83 c9 ed 04 7c  bf b6 cd c3 d3 06 fb c4  |.......|........|
00000050  c6 e1 0d 8a c5 51 b6 6d  2b 6d 54 02 8a bd 29 ca  |.....Q.m+mT...).|
00000060  ff 6d 79 7b 44 62 d0 96  43 68 45 f6 33 a6 15 73  |.my{Db..ChE.3..s|
00000070  7b 72 c8 b5 6b bc cd 52  66 b5 0e 9a cd 96 0d 65  |{r..k..Rf......e|
00000080  26 3c 7e 46 da a2 3b b6  e5 29 02 3f fd 41 35 0e  |&<~F..;..).?.A5.|
00000090  3a 65 32 b2 49 97 49 93  ac 73 e1 54 2a c8 3c da  |:e2.I.I..s.T*.<.|
000000a0  4e 6d 31 12 80 9e 5d 07  e5 b0 29 88 7a 1c f6 db  |Nm1...]...).z...|
000000b0  6c af 97 cf 0a 1c 96 c7  ad 2e f7 45 a0 88 cc 1d  |l..........E....|
000000c0  fd 7f 0f 86 6f 60 9f 7c  ec 4d bd d9 c1 d9 4d f5  |....o`.|.M....M.|
000000d0  62 3b f2 55 d4 1c 15 07  a2 1c 47 51 4b bf 86 b2  |b;.U......GQK...|
000000e0  e5 ff b7 4e 66 be 34 e9  69 33 f4 fb 27 91 d5 94  |...Nf.4.i3..'...|
000000f0  24 09 d7 c9 bf 0c 93 d1  2d 9b b3 f8 28 24 a0 06  |$.......-...($..|
00000100  41 9a 87 52 23 97 e7 1b  8e 38 31 84 d1 fa bb 15  |A..R#....81.....|
00000110  e3 8a d1 92 e9 68 64 82  7e 10 0f 6c fd 1c f7 5b  |.....hd.~..l...[|
00000120  64 82 78 47 9f b3 b6 22  dd 1d 3a e7 80 44 ca 24  |d.xG..."..:..D.$|
00000130  31 6c 94 29 4e dd da ed  b5 ea 6e ff c9 8b b0 39  |1l.)N.....n....9|
00000140  32 0b 18 89 81 ba 91 6c  db f3 24 be 1e 04 17 73  |2......l..$....s|
00000150  40 bc 29 ca 36 36 06 f9  91 e5 8c fa 7a 65 26 c3  |@.).66......ze&.|
00000160  75 10 52 7f ed 7f 67 17  07 e5 96 39 77 5c 04 3c  |u.R...g....9w\.<|
00000170  f6 5d ff 7b 27 97 61 97  41 dd ad 88 9f 8f a3 08  |.].{'.a.A.......|
00000180  d2 37 1d 94 d5 7c 95 7b  fd b2 bf 1f 98 3c 30 35  |.7...|.{.....<05|
00000190  ea a7 5c 60 bd 9f 30 ac  2d 57 70 25 0b da 55 e7  |..\`..0.-Wp%..U.|
000001a0  79 7c 8c ff 8f 57 e2 52  f8 d3 cc b5 f8 9a 23 5c  |y|...W.R......#\|
000001b0  36 fb 34 12 e7 f1 24 f5  f4 23 c2 a4 2f e1 00 fe  |6.4...$..#../...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 23 b1 e9 02 00 fe  |..........#.....|
000001d0  ff ff 05 fe ff ff 25 b1  e9 02 bb 26 1e 00 00 00  |......%....&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  c0 f7 24 e2 3e 80 a9 2d  24 a0 1c 96 92 b9 87 84  |..$.>..-$.......|
00000010  80 0a 6e 85 10 cf 8e 7e  a5 9e 3e 38 09 f8 ad b3  |..n....~..>8....|
00000020  8f d9 a6 48 b0 ea e2 0c  21 d9 3a f1 84 5f e0 eb  |...H....!.:.._..|
00000030  ba 14 4f c9 e1 cb 0b 8e  02 33 01 f0 e9 eb 9b 52  |..O......3.....R|
00000040  93 c7 2b 41 d1 f4 51 02  89 09 22 41 69 c9 1d f0  |..+A..Q..."Ai...|
00000050  b6 56 96 65 f2 d2 51 78  0a 62 69 60 15 74 92 c0  |.V.e..Qx.bi`.t..|
00000060  cf c0 13 fe 7b 9e c2 a0  c2 19 0c 9a 1a 80 42 00  |....{.........B.|
00000070  7f 90 5f 1a 05 cb 29 45  0c 24 38 0a ee f0 39 6e  |.._...)E.$8...9n|
00000080  f3 05 1e 65 af 9b 25 86  74 20 35 28 c5 a4 30 0c  |...e..%.t 5(..0.|
00000090  9a cc 24 e7 92 07 b7 33  f6 c2 fd de 24 85 a6 2d  |..$....3....$..-|
000000a0  34 f5 c1 56 4b e1 80 5d  06 05 53 88 7a c7 4c 3a  |4..VK..]..S.z.L:|
000000b0  0d 21 8c 03 2f 94 34 27  31 19 ad 46 75 d0 e2 50  |.!../.4'1..Fu..P|
000000c0  40 7b e2 b9 8c 91 fa e8  71 08 da 42 26 86 64 8c  |@{......q..B&.d.|
000000d0  2f 7e 4b 2b 84 73 58 70  88 84 51 0c 6f 6f be ee  |/~K+.sXp..Q.oo..|
000000e0  d8 71 63 d8 54 68 71 3a  9c 61 83 4e bb a7 10 41  |.qc.Thq:.a.N...A|
000000f0  61 55 c6 27 76 22 9c 61  86 74 e7 81 75 5c e7 9b  |aU.'v".a.t..u\..|
00000100  d7 38 87 47 57 13 42 e4  06 23 23 31 48 c5 0a c0  |.8.GW.B..##1H...|
00000110  35 94 38 75 24 96 ca eb  22 57 1b 62 5f ba e6 c1  |5.8u$..."W.b_...|
00000120  dc c1 60 2d b3 14 6e 27  c0 75 42 2f 05 12 ae 85  |..`-..n'.uB/....|
00000130  03 ce 6f 27 1e 4b 03 f8  e8 79 f7 77 81 61 be 2c  |..o'.K...y.w.a.,|
00000140  92 d2 1a 92 f9 79 24 af  fb fe 82 34 90 ce 01 51  |.....y$....4...Q|
00000150  64 30 d2 90 81 a0 3b 28  94 1b fe 71 a8 80 85 e3  |d0....;(...q....|
00000160  34 60 40 29 88 44 32 b2  0b 02 81 a3 09 a1 89 26  |4`@).D2........&|
00000170  12 89 6b 46 28 33 92 22  69 7c 10 bf e8 9a 03 10  |..kF(3."i|......|
00000180  cc 80 0a cb 2c 68 17 ce  51 65 a7 37 7c 04 9e ec  |....,h..Qe.7|...|
00000190  f0 17 73 f4 01 ce bc 28  88 cb 13 3c 7f 58 1f 38  |..s....(...<.X.8|
000001a0  38 c8 d7 1c 3e 48 7c 59  88 10 e1 73 5d 57 e7 e0  |8...>H|Y...s]W..|
000001b0  0c a8 71 39 9e 3e cf 70  eb c6 88 55 ed c2 00 fe  |..q9.>.p...U....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 59 00 00 fe  |...........`Y...|
000001d0  ff ff 05 fe ff ff 04 26  54 02 fe c9 1d 00 00 00  |.......&T.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by darkod on 2011-12-22
Wow, why do you have so many partitions? You don't need to mount everything in its own partition. :)

Anyway, lets try one thing first. You have no bootloader on sdb, where win7 and ubuntu are. Even though you said you have win7 and arch on sda and ubuntu on sdb, the script reports arch on sda5, win7 on sdb1 and ubuntu on sdb5. The win7 boot files are actually on sda1 but the OS on sdb1.

First thing first. You can boot ubuntu right now, yes? If yes, boot ubuntu and in terminal execute:
sudo grub-install /dev/sdb

That will install grub2 from uubntu on the MBR of sdb. Reboot, enter bios and switch the boot order of your HDDs, to boot from sdb not sda.
Check that ubuntu and arch boot fine.
Report here if it does, to proceed with the next step.

---

### Post by oldfred on 2011-12-22
I may be jumping ahead, as I know Darko will give good advice.

But you have This issue in sda1 and that is probably why Windows does not work as it cannot read two /boot partitions as it sees /Boot as the same as /boot:
> /bootmgr /Boot/BCD /boot/grub/core.img

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Herman made comments on separate system partitions. I think he does not even use a separate partition for swap now, just a swap file.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by darkod on 2011-12-22
That was the second step. :)
I think it's better to ensure it boots fine from sdb first, especially since grub2 on sda says it's using embedded config file (what ever that is).
It's easy to delete the core.img from sda1, it even might have something to do with the message about embedded config file.

---

### Post by oldfred on 2011-12-22
@Darko

The embedded config is how the script shows that it is booting from the core.img on one drive but searching for a UUID on another drive. I think the embedded file is just the core.img?

Kansasnoob is working with  Gert on improvements to boot script which you can test:
[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

---

### Post by darkod on 2011-12-22
> **oldfred said:**
> @Darko

The embedded config is how the script shows that it is booting from the core.img on one drive but searching for a UUID on another drive. I think the embedded file is just the core.img?

Kansasnoob is working with  Gert on improvements to boot script which you can test:
[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

It sounds OK then, if that's what it means. Probably just deleting core.img from sda1 will sort it out. I would still feel more comfortable if booting from sdb works before trying that, just to make sure the system will not end up unbootable.

---

