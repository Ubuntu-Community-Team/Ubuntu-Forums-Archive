---
title: "GRUB and UUID Startup problems"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by jmartinosky on 2011-09-09
Ok, I'm about to explode. Here's the situation. I am trying to bring up an atom mobo to be embedded in a final product. I have no CDROM drive, but have a plethora of USB ports, as well as one SATA hard drive. I'm attempting to install Ubuntu 11.04 onto a 4GB SATA DOM, from a running installation of 11.04, which is installed on the hard drive. Installation was made from a flash drive.
 
I need a UUID agnostic boot. I'm attempting to set this up so we can make (hopefully) thousands of systems, which will all have different IDs. Unfortunately, when I remove the original boot hard drive I end up just after the BIOS message "Verifying DMI Pool Data" with the message "error: no such device:" and then the UUID of the old hard drive.
 
Try as I might, having spent 2+ days tripping down endless posts, and trying anything that looked remotely promising, I cannot get rid of this dependence on the original hard drive.
 
What am I missing? I don't see the magic of the new GRUB's dependence on UUIDs.
 
Thanks

---

### Post by YesWeCan on 2011-09-09
How are you making the copies? Are you copying the Ubuntu partition contents on to the DOM (what does the 'D' in DOM stand for?)? How are you installing Grub on the DOM? Do you need each Ubuntu to have a unique UUID or is it ok for all DOMs to be identical.

---

### Post by jmartinosky on 2011-09-09
The DOM is short for Disk on Module.  It's a tiny SSD that plugs directly into the SATA port.
 
I'm working from instructions generated from an Ubuntu 7.10 version of the product.  The DOM is partitioned, and then mkfs is used to set up the drive.  Then, GRUB is installed to it from the running system using grub-install /dev/sda.  After that, the grub.cfg and vmlinuz are copied over to their proper locations.

---

### Post by oldfred on 2011-09-09
You can use UUIDs, device like /dev/sda1 or labels. I think you might need to use labels and just label every system the same?

[http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dinstall)

[LIST]
[*]Drive ordering in your operating system may not be the same as the boot drive ordering used by your firmware.  Do not assume that your first hard drive (e.g. ‘/dev/sda’) is the one that your firmware will boot from.  device.map (see [Device map]("http://www.gnu.org/software/grub/manual/grub.html#Device-map")) can be used to override this, but it is usually better to use UUIDs or file system labels and avoid depending on drive ordering entirely.
[/LIST]
Re: GRUB2 booting with labels (no UUID) MountainX
[http://ubuntuforums.org/showpost.php?p=9585951&postcount=19](http://ubuntuforums.org/showpost.php?p=9585951&postcount=19)

---

### Post by YesWeCan on 2011-09-09
When you do a grub-install the boot-loader code that is put at the start of your DOM is told the UUID of the root partition on your HD and this is where it looks for /boot/grub files. So when you remove the HD it cannot find the partition.

So what you need to do is create a partition on the DOM that contains /grub/* files (or it can be /boot/grub/*) and tell grub install to use this as the target when installing. It has to be mounted first.

Eg:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That will solve the immediate problem and at worst the DOM will boot to a grub> prompt.

If you want 11.04 to boot up on the DOM you'll need to copy more than vmlinuz across. You'll need to copy the whole root partition, won't you? The other boot issue will arise with /etc/fstab. As a minimum this file sets the partition to mount to be root. Since the UUID of the new DOM partition will be different from that of your HD this will need to be changed. You can change the fstab entry to use /dev/sdaN instead of UUID=... if you are sure that the DOM device will always be sda. The reason UUIDs are used is because different bioses give different names to devices and the names can change when new devices are connected.

---

### Post by YesWeCan on 2011-09-09
oldfred's "by label" is better than using device names. :)
The only gotcha with either is that two DOMs must not be connected to the same PC at the same time or the boot and mounting process will get really screwed up.

If DOMs have unique device IDs then you are in business. fstab can use this, for example:
```
/dev/disk/by-id/ata-WDC_WD1002FAEX-00Z3A0_WD-WCATR3387738-part1 / ext4 defaults 0 1
```

(I think that's the correct syntax, anyway)

To automate this you'll need a shell script or something.

---

### Post by jmartinosky on 2011-09-12
Thanks for all the advice.  I'm attempting to implement the changes this morning.
 
As for the system, I can guarantee that only one drive will be installed, and it will be sda.  The DOMs are gang programmed and we want to avoid having to set up UUIDs for individual systems.
 
I am looking into the question about the rest of the root file system.  I didn't set up the initial system.  I've only been brought in to make this new aspect work, so there is a great deal that is out of my control.  As is typical of a project like this, I have to learn why choices were made with the initial system, so some of your questions drive me to find out just why the heck I have the instructions I do have!
 
Thanks

---

### Post by jmartinosky on 2011-09-12
Ok,
Only half-luck.  I've ended up at the  BusyBox (initramfs) prompt.
 
On the plus side, there was no longer a complaint about the hard drive's UUID, so I'm happy there.  
 
Is there a step-by-step listing, somewhere, of the complete boot process, from MBR through GRUB?  I suspect there's a detail I've missed somewhere, and I'd be able to understand the boot process and the problems if I could see the entire thing.
 
Thanks for all the help!

---

### Post by oldfred on 2011-09-12
If you want to see what is installed where in detail including grub in the MBR this tool lists it all. I use it just to document my system as well.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.


This is more for Windows and multibooting but it is MBR computers boot. Grub does not use PBR, but puts some code just after the MBR to allow enough code to find files by name in the partition.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by jmartinosky on 2011-09-12
```
                  Boot Info Script 0.60    from 17 May 2011

============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
sda1: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab
sda2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda3 and looks at sector 205343328 on boot 
                       drive #1 for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #3 for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf
sda4: __________________________________________________________________________
    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img
vg_sbc2dev1-lv_swap': __________________________________________________________
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
vg_sbc2dev1-lv_home': __________________________________________________________
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
vg_sbc2dev1-lv_root': __________________________________________________________
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
sdc: ___________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 8018 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   204,802,047   204,800,000  83 Linux
/dev/sda2         972,601,342   976,771,071     4,169,730   5 Extended
/dev/sda5         972,601,344   976,771,071     4,169,728  82 Linux swap / Solaris
/dev/sda3         204,802,048   205,826,047     1,024,000  83 Linux
/dev/sda4         205,826,048   972,599,295   766,773,248  8e Linux LVM

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 8012 MB, 8012390400 bytes
24 heads, 9 sectors/track, 72450 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1               2,048    15,648,767    15,646,720  83 Linux

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/mapper/vg_sbc2dev1-lv_home 198a7145-b837-4587-b4e4-6ab26e55e1a3   ext4       
/dev/mapper/vg_sbc2dev1-lv_root e1213ab3-d0e7-4fcb-a9bd-70e1729cb04d   ext4       _Fedora-15-i686-
/dev/mapper/vg_sbc2dev1-lv_swap 3dda812b-9bd5-4fb6-965a-6c9e773196c1   swap       
/dev/sda1        ada400d3-6ca6-4b34-bf49-8686ae2231da   ext4       
/dev/sda3        28365794-2002-4e58-aefa-0ba306b8c022   ext4       
/dev/sda4        4ZICmX-8y1b-5bmV-0000-jIRj-vJMj-6W2mG5 LVM2_member 
/dev/sda5        9f93b9c0-e6b3-4dca-823b-4b4974741286   swap       
/dev/sdb1        d8d79929-455d-4f56-b107-d6eea7c560a7   ext4       
/dev/sdc         1416-1144                              vfat       PENDRIVE
========================= "ls -R /dev/mapper/" output: =========================
/dev/mapper:
control
vg_sbc2dev1-lv_home
vg_sbc2dev1-lv_root
vg_sbc2dev1-lv_swap
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc         /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

=========================== sda1/boot/grub/grub.cfg: ===========================
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
set root='(/dev/sda,msdos1)'
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
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
 set root=(hd0,msdos1)
 linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod part_msdos
 insmod ext2
 set root=(hd0,msdos1)
 echo 'Loading Linux 2.6.38-8-generic ...'
 linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sda,msdos1)'
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sda,msdos1)'
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora (2.6.38.6-26.rc1.fc15.i686) (on /dev/mapper/vg_sbc2dev1-lv_root)" --class gnu-linux --class gnu --class os {
 insmod part_msdos
 insmod ext2
 set root=(hd0,msdos3)
 linux /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_sbc2dev1-lv_root rd_LVM_LV=vg_sbc2dev1/lv_root rd_LVM_LV=vg_sbc2dev1/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
 initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
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
=============================== sda1/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=ada400d3-6ca6-4b34-bf49-8686ae2231da /               ext4    errors=remount-ro 0       1
/dev/sda1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=9f93b9c0-e6b3-4dca-823b-4b4974741286 none            swap    sw              0       0
/dev/sda5 none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sda1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
  12.237480164 = 13.139894272   boot/grub/grub.cfg                             1
   2.405509949 = 2.582896640    boot/initrd.img-2.6.38-8-generic               2
   0.668861389 = 0.718184448    boot/vmlinuz-2.6.38-8-generic                  1
   2.405509949 = 2.582896640    initrd.img                                     2
   0.668861389 = 0.718184448    vmlinuz                                        1
============================= sda3/grub/grub.conf: =============================
--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_sbc2dev1-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda3
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.i686)
 root (hd0,2)
 kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_sbc2dev1-lv_root rd_LVM_LV=vg_sbc2dev1/lv_root rd_LVM_LV=vg_sbc2dev1/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
 initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------
=================== sda3: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
  97.915327072 = 105.135781888  grub/grub.conf                                 1
  97.915327072 = 105.135781888  grub/menu.lst                                  1
  97.915444374 = 105.135907840  grub/stage2                                    1
  97.687784195 = 104.891459584  initramfs-2.6.38.6-26.rc1.fc15.i686.img        4
  97.676396370 = 104.879232000  vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
================= sda3: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
  97.665584564 = 104.867622912  extlinux/cat.c32                               1
  97.665656090 = 104.867699712  extlinux/chain.c32                             1
  97.670896530 = 104.873326592  extlinux/cmd.c32                               1
  97.665577888 = 104.867615744  extlinux/config.c32                            1
  97.666419029 = 104.868518912  extlinux/cpuid.c32                             1
  97.670682907 = 104.873097216  extlinux/cpuidtest.c32                         1
  97.665695190 = 104.867741696  extlinux/disk.c32                              1
  97.666396141 = 104.868494336  extlinux/dmitest.c32                           1
  97.665980339 = 104.868047872  extlinux/elf.c32                               1
  97.666460037 = 104.868562944  extlinux/ethersel.c32                          1
  97.666029930 = 104.868101120  extlinux/gfxboot.c32                           1
  97.666282654 = 104.868372480  extlinux/gpxecmd.c32                           1
  97.665952682 = 104.868018176  extlinux/hdt.c32                               1
  97.665596962 = 104.867636224  extlinux/host.c32                              1
  97.670685768 = 104.873100288  extlinux/ifcpu64.c32                           1
  97.666277885 = 104.868367360  extlinux/ifcpu.c32                             1
  97.666431427 = 104.868532224  extlinux/ifplop.c32                            1
  97.665988922 = 104.868057088  extlinux/kbdmap.c32                            1
  97.666413307 = 104.868512768  extlinux/linux.c32                             1
  97.666428566 = 104.868529152  extlinux/ls.c32                                1
  97.666255951 = 104.868343808  extlinux/lua.c32                               1
  97.665689468 = 104.867735552  extlinux/mboot.c32                             1
  97.666261673 = 104.868349952  extlinux/meminfo.c32                           1
  97.666345596 = 104.868440064  extlinux/menu.c32                              1
  97.670742989 = 104.873161728  extlinux/pcitest.c32                           1
  97.666361809 = 104.868457472  extlinux/pmload.c32                            1
  97.666348457 = 104.868443136  extlinux/pwd.c32                               1
  97.666279793 = 104.868369408  extlinux/reboot.c32                            1
  97.666008949 = 104.868078592  extlinux/rosh.c32                              1
  97.665983200 = 104.868050944  extlinux/sanboot.c32                           1
  97.670711517 = 104.873127936  extlinux/sdi.c32                               1
  97.665637016 = 104.867679232  extlinux/sysdump.c32                           1
  97.665572166 = 104.867609600  extlinux/vesainfo.c32                          1
  97.670895576 = 104.873325568  extlinux/vesamenu.c32                          1
  97.665591240 = 104.867630080  extlinux/vpdtest.c32                           1
  97.670899391 = 104.873329664  extlinux/whichsys.c32                          1
============== sda3: Version of COM32(R) files used by Syslinux: ===============
 extlinux/cat.c32                   :  COM32R module (v4.xx)
 extlinux/chain.c32                 :  COM32R module (v4.xx)
 extlinux/cmd.c32                   :  COM32R module (v4.xx)
 extlinux/config.c32                :  COM32R module (v4.xx)
 extlinux/cpuid.c32                 :  COM32R module (v4.xx)
 extlinux/cpuidtest.c32             :  COM32R module (v4.xx)
 extlinux/disk.c32                  :  COM32R module (v4.xx)
 extlinux/dmitest.c32               :  COM32R module (v4.xx)
 extlinux/elf.c32                   :  COM32R module (v4.xx)
 extlinux/ethersel.c32              :  COM32R module (v4.xx)
 extlinux/gfxboot.c32               :  COM32R module (v4.xx)
 extlinux/gpxecmd.c32               :  COM32R module (v4.xx)
 extlinux/hdt.c32                   :  COM32R module (v4.xx)
 extlinux/host.c32                  :  COM32R module (v4.xx)
 extlinux/ifcpu64.c32               :  COM32R module (v4.xx)
 extlinux/ifcpu.c32                 :  COM32R module (v4.xx)
 extlinux/ifplop.c32                :  COM32R module (v4.xx)
 extlinux/kbdmap.c32                :  COM32R module (v4.xx)
 extlinux/linux.c32                 :  COM32R module (v4.xx)
 extlinux/ls.c32                    :  COM32R module (v4.xx)
 extlinux/lua.c32                   :  COM32R module (v4.xx)
 extlinux/mboot.c32                 :  COM32R module (v4.xx)
 extlinux/meminfo.c32               :  COM32R module (v4.xx)
 extlinux/menu.c32                  :  COM32R module (v4.xx)
 extlinux/pcitest.c32               :  COM32R module (v4.xx)
 extlinux/pmload.c32                :  COM32R module (v4.xx)
 extlinux/pwd.c32                   :  COM32R module (v4.xx)
 extlinux/reboot.c32                :  COM32R module (v4.xx)
 extlinux/rosh.c32                  :  COM32R module (v4.xx)
 extlinux/sanboot.c32               :  COM32R module (v4.xx)
 extlinux/sdi.c32                   :  COM32R module (v4.xx)
 extlinux/sysdump.c32               :  COM32R module (v4.xx)
 extlinux/vesainfo.c32              :  COM32R module (v4.xx)
 extlinux/vesamenu.c32              :  COM32R module (v4.xx)
 extlinux/vpdtest.c32               :  COM32R module (v4.xx)
 extlinux/whichsys.c32              :  COM32R module (v4.xx)
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='(/dev/sda,msdos1)'
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
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
 set root=(hd0,msdos1)
 linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro   quiet splash vt.handoff=7
 initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod part_msdos
 insmod ext2
 set root=(hd0,msdos1)
 echo 'Loading Linux 2.6.38-8-generic ...'
 linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sda,msdos1)'
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sda,msdos1)'
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora (2.6.38.6-26.rc1.fc15.i686) (on /dev/mapper/vg_sbc2dev1-lv_root)" --class gnu-linux --class gnu --class os {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sda,msdos3)'
 linux /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_sbc2dev1-lv_root rd_LVM_LV=vg_sbc2dev1/lv_root rd_LVM_LV=vg_sbc2dev1/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
 initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
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
=================== sdb1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
   2.255947113 = 2.422304768    boot/grub/core.img                             1
   2.258811951 = 2.425380864    boot/grub/grub.cfg                             1
   0.141601562 = 0.152043520    boot/initrd.img-2.6.38-8-generic               2
   2.255187988 = 2.421489664    boot/vmlinuz-2.6.38-8-generic                  1
========================== sdc/syslinux/syslinux.cfg: ==========================
--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------
================== sdc: Location of files loaded by Syslinux: ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1
=============== sdc: Version of COM32(R) files used by Syslinux: ===============
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on vg_sbc2dev1-lv_swap'

Unknown BootLoader on vg_sbc2dev1-lv_home'

Unknown BootLoader on vg_sbc2dev1-lv_root'
 
=============================== StdErr Messages: ===============================
unlzma: Decoder error
unlzma: Decoder error
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_sbc2dev1-lv_swap': No such file or directory
hexdump: /dev/mapper/vg_sbc2dev1-lv_swap': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_sbc2dev1-lv_home': No such file or directory
hexdump: /dev/mapper/vg_sbc2dev1-lv_home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_sbc2dev1-lv_root': No such file or directory
hexdump: /dev/mapper/vg_sbc2dev1-lv_root': No such file or directory
/media/PENDRIVE/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-09-12
I do not see anything major wrong. It looks like it installed grub2's boot loader to the MBR & core.img to the first sector & it is correctly looking into sda1.

But sda1 looks like it is missing core.img.

My entry:
```
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

It also looks like the os-prober found your Fedora install and added it to the boot menu.

You could try just copying core.img, but I think it may be better just to purge & reinstall grub2.
HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jmartinosky on 2011-09-13
Thank you all for your help.  I can't say exactly which thing got me over the hump, but it's working now.  It's very much appreciated.

---

### Post by YesWeCan on 2011-09-13
This may be moot but there are some things that are confusing me.
> I'm attempting to install Ubuntu 11.04 onto a 4GB SATA DOM, from a  running installation of 11.04, which is installed on the hard drive.  Installation was made from a flash drive.
According to bootinfoscript your DOM is 8GB and is sdb. But this is when you are booting from the 500GB drive, I assume. When you boot from the DOM it will be sda. According to bootinfoscript the DOM has Grub files but is missing the OS files. Just thought I'd point that out.

---

