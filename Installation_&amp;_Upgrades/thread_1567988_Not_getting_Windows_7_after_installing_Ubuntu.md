---
title: "Not getting Windows 7 after installing Ubuntu"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by krishnandu.sarkar on 2010-09-04
Hey friends, I installed Win 7 then Arch and then Ubuntu. Now I'm not getting only Arch and Ubuntu not Win 7. What to do..??

---

### Post by Rubi1200 on 2010-09-04
> **krishnandu.sarkar said:**
> Hey friends, I installed Win 7 then Arch and then Ubuntu. Now I'm not getting only Arch and Ubuntu not Win 7. What to do..??
Not sure I understand; can you boot into Ubuntu?

If you installed Ubuntu last, go to the terminal and run
```
sudo update-grub
```
If that does not pick up Windows then use a LiveCD to boot the computer and post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by krishnandu.sarkar on 2010-09-04
Ya I can boot Ubuntu. Actually I had Win 7 and Ubuntu before also and that time it detected WIn 7 automatically. Afterwards I installed Arch and everything got messed up. I was getting neither Ubuntu nor Windows, only Arch. 

So I decided to delete both and install Arch and then Ubuntu so that it detects everything. But now it's only detecting Arch and Ubuntu. I can boot into both but the problem is Win 7 is not there.

I already tried sudo update-grub but it shows
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
Found Arch on /dev/sda5
done                      

Here is the output of the script(I mean result.txt)
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   104,859,647   104,652,800   7 HPFS/NTFS
/dev/sda3         104,859,648   251,660,287   146,800,640   7 HPFS/NTFS
/dev/sda4         251,660,349   312,580,095    60,919,747   5 Extended
/dev/sda5         251,660,351   279,661,582    28,001,232  83 Linux
/dev/sda6         279,661,646   281,653,642     1,991,997  82 Linux swap / Solaris
/dev/sda7         281,655,296   312,580,095    30,924,800  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2083 MB, 2083258368 bytes
255 heads, 63 sectors/track, 253 cylinders, total 4068864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 128     4,065,407     4,065,280   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        96E0E85CE0E84459                       ntfs       System Reserved               
/dev/sda2        44DCF390DCF37B0E                       ntfs                                     
/dev/sda3        E2CE162FCE15FC8B                       ntfs       New Volume                    
/dev/sda4: PTTYPE="dos" 
/dev/sda5        64c7857b-3740-4754-91e7-2aa53124bbdc   ext4                                     
/dev/sda6        9880b453-7205-4595-bcd9-3cd60612508d   swap                                     
/dev/sda7        612f6efb-4959-468d-9358-0403ae672b6e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D693-EE63                              vfat       PMP                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PMP               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sda5/boot/grub/menu.lst: ===========================

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
#  [http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution](http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution) 

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
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/sda5 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/sda5 ro
initrd /boot/kernel26-fallback.img

# (2) Windows
title Windows
rootnoverify (hd0,0)
makeactive
#chainloader +1

=============================== sda5/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda5 / ext4 defaults 0 1
/dev/sda6 swap swap defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


 131.1GB: boot/grub/menu.lst
 137.6GB: boot/grub/stage2
 128.9GB: boot/kernel26-fallback.img
 128.9GB: boot/kernel26.img
 137.5GB: boot/vmlinuz26

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=612f6efb-4959-468d-9358-0403ae672b6e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=612f6efb-4959-468d-9358-0403ae672b6e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 612f6efb-4959-468d-9358-0403ae672b6e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 64c7857b-3740-4754-91e7-2aa53124bbdc
    linux /boot/vmlinuz26 root=/dev/sda5 ro
    initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 64c7857b-3740-4754-91e7-2aa53124bbdc
    linux /boot/vmlinuz26 root=/dev/sda5 ro
    initrd /boot/kernel26-fallback.img
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=612f6efb-4959-468d-9358-0403ae672b6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9880b453-7205-4595-bcd9-3cd60612508d none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 146.6GB: boot/grub/core.img
 148.7GB: boot/grub/grub.cfg
 146.7GB: boot/initrd.img-2.6.32-21-generic
 146.7GB: boot/vmlinuz-2.6.32-21-generic
 146.7GB: initrd.img
 146.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  73 63 3d 22 44 61 74 75  61 6b 20 67 72 61 66 69  |sc="Datuak grafi|
00000010  6b 6f 61 6e 20 6c 65 75  6e 64 75 20 62 65 68 61  |koan leundu beha|
00000020  72 20 64 69 72 65 6e 20  65 64 6f 20 65 7a 22 3e  |r diren edo ez">|
00000030  0a 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |.               |
00000040  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000060  20 20 20 20 20 20 20 20  20 3c 6c 6f 6e 67 64 65  |         <longde|
00000070  73 63 3e 44 61 74 75 61  6b 20 67 72 61 66 69 6b  |sc>Datuak grafik|
00000080  6f 61 6e 20 6c 65 75 6e  64 75 20 62 65 68 61 72  |oan leundu behar|
00000090  20 64 69 72 65 6e 20 65  64 6f 20 65 7a 2e 3c 2f  | diren edo ez.</|
000000a0  6c 6f 6e 67 64 65 73 63  3e 0a 20 20 20 20 20 20  |longdesc>.      |
000000b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000000d0  20 20 20 20 20 20 20 20  20 20 3c 2f 6c 6f 63 61  |          </loca|
000000e0  6c 5f 73 63 68 65 6d 61  3e 0a 20 20 20 20 20 20  |l_schema>.      |
000000f0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000110  20 20 3c 2f 65 6e 74 72  79 3e 0a 20 20 20 20 20  |  </entry>.     |
00000120  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000140  20 20 20 3c 65 6e 74 72  79 20 6e 61 6d 65 3d 22  |   <entry name="|
00000150  73 68 6f 77 5f 65 76 65  6e 74 73 22 3e 0a 20 20  |show_events">.  |
00000160  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000180  20 20 20 20 20 20 20 20  20 20 20 20 20 20 3c 6c  |              <l|
00000190  6f 63 61 6c 5f 73 63 68  65 6d 61 20 73 68 6f 72  |ocal_schema shor|
000001a0  74 5f 64 65 73 63 3d 22  47 65 72 74 61 65 72 61  |t_desc="Gertaera|
000001b0  6b 20 65 72 61 6b 75 74  73 69 20 62 65 68 00 fe  |k erakutsi beh..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 d0 43 ab 01 00 fe  |...........C....|
000001d0  ff ff 05 fe ff ff d2 43  ab 01 7c 65 1e 00 00 00  |.......C..|e....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by krishnandu.sarkar on 2010-09-04
Got this : [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Problem Solved.

---

