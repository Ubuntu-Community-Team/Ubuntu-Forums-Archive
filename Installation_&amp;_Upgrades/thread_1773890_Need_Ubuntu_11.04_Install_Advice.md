---
title: "Need Ubuntu 11.04 Install Advice"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Awes0meSauce on 2011-06-02
A while back I attempted to install Ubuntu 11.04, but the install did not go well. Since then I have installed Fedora 15. I am now dual booting Windows 7 Professional and Fedora. My computer has three hard drives. 

HDD 1 - Windows 7 
HDD 2 - Fedora 15

I want to install Ubuntu 11.04 on the third HDD. The problem is, after unsuccessfully trying to install Ubuntu last time, I installed lilo so that I could at least get back into Windows 7. A few weeks later I installed Fedora 15 and it's GRUB on HDD 2, and changed my boot order to boot from HDD 2. Since Fedora 15 uses GRUB legacy, my question is whether installing Ubuntu 11.04 which uses Grub2, will cause any problems? If you need more information on my system, I can provide the results of the boot info script that I ran in Fedora a few weeks back. Thank you for your time.

---

### Post by Hedgehog1 on 2011-06-02
> **Awes0meSauce said:**
> A while back I attempted to install Ubuntu 11.04, but the install did not go well. Since then I have installed Fedora 15. I am now dual booting Windows 7 Professional and Fedora. My computer has three hard drives. 

HDD 1 - Windows 7 
HDD 2 - Fedora 15

I want to install Ubuntu 11.04 on the third HDD. The problem is, after unsuccessfully trying to install Ubuntu last time, I installed lilo so that I could at least get back into Windows 7. A few weeks later I installed Fedora 15 and it's GRUB on HDD 2, and changed my boot order to boot from HDD 2. Since Fedora 15 uses GRUB legacy, my question is whether installing Ubuntu 11.04 which uses Grub2, will cause any problems? If you need more information on my system, I can provide the results of the boot info script that I ran in Fedora a few weeks back. Thank you for your time.

If you install Ubuntu on the 3rd hard drive, install grub2 on the third hard drive, and the change your boot order to start with the 3rd hard drive, this will keep the Ubuntu install from changing anything on the first 2 hard drives, and grub2 on the 3rd hard drive should see the other two OSes.

Alternately, some folks who prefer 'absolute separation' of their OSes use the BIOS boot selector and choose the hard drive at boot time.

***The Hedge***

:KS

---

### Post by Awes0meSauce on 2011-06-04
> **Hedgehog1 said:**
> If you install Ubuntu on the 3rd hard drive, install grub2 on the third hard drive, and the change your boot order to start with the 3rd hard drive, this will keep the Ubuntu install from changing anything on the first 2 hard drives, and grub2 on the 3rd hard drive should see the other two OSes.

Alternately, some folks who prefer 'absolute separation' of their OSes use the BIOS boot selector and choose the hard drive at boot time.

***The Hedge***

:KS
Thanks for reply. That makes sense, and it's actually very simple when I think about it. I was looking too much into it. Fingers crossed for the install though.

---

### Post by Awes0meSauce on 2011-06-04
Well the install went great! Only problem now is that Ubuntu 11.04 can't see Fedora 15. I ran the boot info script, here are my results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub Legacy0.97-71.fc15 is installed in the MBR of /dev/sdb and looks at 
    sector 30242 on boot drive #1 for the stage2 file.  A stage2 file is at 
    this location on /dev/sdb.  Stage2 looks on partition #1 for 
    /grub/grub.conf..
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sdb2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sdb2           1,026,048   488,396,799   487,370,752  8e Linux LVM


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   593,531,893   593,531,831   b W95 FAT32
/dev/sdc2         593,532,926   976,771,071   383,238,146   5 Extended
/dev/sdc5         593,532,928   968,386,559   374,853,632  83 Linux
/dev/sdc6         968,388,608   976,771,071     8,382,464  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CA447E3E447E2CF7                       ntfs       
/dev/sdb1        3597766a-2dd5-4748-be9c-63f39caedfad   ext4       
/dev/sdb2        Z1nte4-wgOh-OCyp-LbWM-11Qa-wck9-4BcHEL LVM2_member 
/dev/sdc1        190B-2494                              vfat       STORAGE
/dev/sdc5        8a321aa5-74ef-478e-bc17-4221c7e041fe   ext4       
/dev/sdc6        c0c69589-cd3c-4bc6-9f70-316d5035568c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sdb1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_blackmesa-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sdb
default=0
timeout=-1
splashimage=(hd0,0)/grub/splash.xpm.gz
#hiddenmenu
title Fedora (2.6.38.6-27.fc15.i686)
    root (hd0,0)
    kernel /vmlinuz-2.6.38.6-27.fc15.i686 ro root=/dev/mapper/vg_blackmesa-lv_root rd_LVM_LV=vg_blackmesa/lv_root rd_LVM_LV=vg_blackmesa/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-27.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,0)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_blackmesa-lv_root rd_LVM_LV=vg_blackmesa/lv_root rd_LVM_LV=vg_blackmesa/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
title Windows 7
    rootnoverify (hd1,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.040530205 = 0.043518976    grub/grub.conf                                 1
   0.040530205 = 0.043518976    grub/menu.lst                                  1
   0.014535904 = 0.015607808    grub/stage2                                    1
   0.031785011 = 0.034128896    initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
   0.051069260 = 0.054835200    initramfs-2.6.38.6-27.fc15.i686.img            2
   0.012580872 = 0.013508608    vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
   0.035771370 = 0.038409216    vmlinuz-2.6.38.6-27.fc15.i686                  1

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdd,msdos5)'
search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos5)'
search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos5)'
    search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8a321aa5-74ef-478e-bc17-4221c7e041fe ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos5)'
    search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8a321aa5-74ef-478e-bc17-4221c7e041fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos5)'
    search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos5)'
    search --no-floppy --fs-uuid --set=root 8a321aa5-74ef-478e-bc17-4221c7e041fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root CA447E3E447E2CF7
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
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=8a321aa5-74ef-478e-bc17-4221c7e041fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=c0c69589-cd3c-4bc6-9f70-316d5035568c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 373.165225983 = 400.683110400  boot/grub/core.img                             1
 443.159240723 = 475.838611456  boot/grub/grub.cfg                             1
 284.562038422 = 305.546162176  boot/initrd.img-2.6.38-8-generic               1
 373.163497925 = 400.681254912  boot/vmlinuz-2.6.38-8-generic                  1
 284.562038422 = 305.546162176  initrd.img                                     1
 373.163497925 = 400.681254912  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  0a 02 dc 02 f1 f1 d3 bc  bc bc f1 f1 d3 d3 bc bc  |................|
00000010  bc d3 d3 b2 bc bc f1 0d  0d 0d 0d e2 0d 0d f1 f1  |................|
00000020  dc dc dc dc dc dc dc dc  dc dc f1 f1 dc bc dc f1  |................|
00000030  f1 dc dc f1 dc dc dc 02  02 02 dc f1 02 02 02 a9  |................|
00000040  0a dc dc 02 f1 dc f1 f1  dc de dc dc dc 02 dc bc  |................|
00000050  bc f1 bc bc bc dc 02 02  0a 0a 02 dc f8 c0 dc 02  |................|
00000060  02 02 02 dc 02 02 02 02  02 dc dc dc dc dc f1 f1  |................|
00000070  dc dc 0d 0d 0d f1 0d bc  0d b2 b2 b2 b2 b2 33 c7  |..............3.|
00000080  c7 b2 b2 21 01 b2 c7 c7  c7 c7 0d bc c7 c7 b2 b2  |...!............|
00000090  f8 b2 c7 c7 b2 b2 21 21  21 21 21 21 b2 c7 01 c7  |......!!!!!!....|
000000a0  c7 c7 21 b2 21 09 09 09  21 21 21 21 21 21 21 09  |..!.!...!!!!!!!.|
000000b0  09 09 09 09 db 09 09 db  b6 c0 c8 db db db db db  |................|
000000c0  b9 b6 b9 db db 09 db db  b6 c8 bf c1 bf b9 b6 db  |................|
000000d0  fd fd b9 15 15 fd b6 09  fc 9f 21 21 09 01 21 09  |..........!!..!.|
000000e0  09 09 09 db 09 f8 db db  db db 09 db db db db 09  |................|
000000f0  09 09 db db db db 09 09  09 21 21 b2 21 21 21 21  |.........!!.!!!!|
00000100  21 b2 21 f8 f8 b2 b2 09  21 b2 21 f8 09 eb eb da  |!.!.....!.!.....|
00000110  ee da ec ec c0 eb eb f8  f8 f8 eb f8 eb da da da  |................|
00000120  ee ee c0 ec ec da db eb  f8 21 21 b2 b2 f8 f8 f8  |.........!!.....|
00000130  f8 f8 f8 f8 f8 21 21 b2  21 f8 f8 09 f8 eb da ec  |.....!!.!.......|
00000140  ec da ec ec ec ec 03 ec  ec ec ec cb a3 f7 a3 a3  |................|
00000150  a3 a3 f7 a3 aa a3 f7 f7  a3 a8 a3 a3 df f7 f7 f7  |................|
00000160  e9 f7 df 04 04 08 04 04  04 04 04 04 f7 04 df 04  |................|
00000170  04 04 04 f9 f7 df 04 04  04 04 04 04 04 04 04 0c  |................|
00000180  0c 0c 0e 0c 0c 0e 0e 0c  0e 0e 04 0c 04 04 f7 a8  |................|
00000190  a8 a8 a8 a8 a3 a3 a2 cc  eb c0 cb a3 e5 e5 e5 df  |................|
000001a0  f7 a3 69 ec db 21 c7 bc  dc 0d 21 01 c3 a1 f2 53  |..i..!....!....S|
000001b0  c6 31 57 c6 f2 34 c3 4d  c6 31 53 53 cf cf 00 fe  |.1W..4.M.1SS....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 57 16 00 fe  |............W...|
000001d0  ff ff 05 fe ff ff 02 d0  57 16 00 f0 7f 00 00 00  |........W.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

Any ideas?

---

### Post by Awes0meSauce on 2011-06-06
Here is my Grub file as well. Is there anything that I need to change to be able to see Fedora 15 when Grub loads up?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by jramshu on 2011-06-06
Did you run
```
sudo update-grub
```

---

### Post by Awes0meSauce on 2011-06-06
> **jramshu said:**
> Did you run
```
sudo update-grub
```
Yeah, and after I restarted it still only showed Ubuntu and Windows. So weird how it won't recognise another linux OS.

---

### Post by jramshu on 2011-06-07
That is weird.  
I had that with F15 too, but it showed up after running the update-grub command. 
I only have one drive though.

EDIT: May want to look at this, not sure if will help but it's "similar."
[http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/](http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/)

---

