---
title: "Dualboot with Fedora"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by vikdak on 2011-07-31
I have Ubuntu 11.04. I wanted to try Fedora since it seems to have better support for Sandybridge. I installed it using liveusb, making sure that the boot loader was installed into Fedora's boot rather than the MBR. Then I booted back into Ubuntu, did update-grub but it does not seem to detect Fedora.

What do I do?

---

### Post by Quackers on 2011-07-31
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by vikdak on 2011-07-31
Here's the output


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 1322639360.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda3 and looks at sector 909418018 on boot 
                       drive #1 for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #3 for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   909,389,823   909,387,776  83 Linux
/dev/sda2       1,322,639,360 1,465,147,391   142,508,032   b W95 FAT32
/dev/sda3         909,389,824   910,413,823     1,024,000  83 Linux
/dev/sda4         910,413,824 1,322,639,359   412,225,536   5 Extended
/dev/sda5         910,415,872 1,322,639,359   412,223,488  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd   ext4       
/dev/sda2        7A82-D1E1                              vfat       
/dev/sda3        5cea4c53-6ea1-4bda-9983-857d52846238   ext4       
/dev/sda5        83I6wU-QN1N-WRDM-kzmN-dXrt-fIhE-da2jKv LVM2_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/5cea4c53-6ea1-4bda-9983-857d52846238 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 738c9b8f-3424-4fcf-8bd7-f0feaa4f80bd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 160.136745453 = 171.945521152  boot/grub/core.img                             1
 160.133300781 = 171.941822464  boot/grub/grub.cfg                             1
  32.524414062 = 34.922823680   boot/initrd.img-2.6.38-10-generic              7
   4.880100250 = 5.239967744    boot/initrd.img-2.6.38-8-generic               2
   0.704410553 = 0.756355072    boot/vmlinuz-2.6.38-10-generic                 1
 160.133281708 = 171.941801984  boot/vmlinuz-2.6.38-8-generic                  1
  32.524414062 = 34.922823680   initrd.img                                     7
   4.880100250 = 5.239967744    initrd.img.old                                 2
   0.704410553 = 0.756355072    vmlinuz                                        1
 160.133281708 = 171.941801984  vmlinuz.old                                    1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_fedora-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda3
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_fedora-lv_root rd_LVM_LV=vg_fedora/lv_root rd_LVM_LV=vg_fedora/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 433.644928932 = 465.622696960  grub/grub.conf                                 1
 433.644928932 = 465.622696960  grub/menu.lst                                  1
 433.644418716 = 465.622149120  grub/stage2                                    1
 433.661667824 = 465.640670208  initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
 433.642463684 = 465.620049920  vmlinuz-2.6.38.6-26.rc1.fc15.i686              1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-07-31
There appear to be some curious issues with your installation.
Your Fedora system is presumably in sda3 and grub legacy is installed to that partition, which is fine. However in the sda3 output of the boot script no operating system is shown - that field is blank
```
sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda3 and looks at sector 909418018 on boot 
                       drive #1 for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #3 for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf
```
I would expect Fedora to show up there. Maybe something went wrong with the installation?
Also your grub/grub.conf file (which is what grub legacy uses to boot) seems to be looking for 
root=/dev/mapper/vg_fedora-lv_root
although sda3 doesn't appear to be a LVM2 member (but it has a raid/LVM type name).
Curious to me, unless I'm missing something.

---

### Post by vikdak on 2011-07-31
When I installed using liveUSB, I selected the option of shrinking my Ubuntu parition and install on the remaining space. So it installed using whatever defaults it uses. I believe sda3 was /boot for Fedora and sda4 is where it installed the operating system. 

Does that clear anything up?

---

