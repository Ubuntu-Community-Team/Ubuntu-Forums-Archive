---
title: "Grub2 can not load SuSe10"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by aixilin on 2011-06-23
I installed the Ubuntu 11 alongside of the SUSE10. Now I can get into the Ubuntu, but the suse10 is failed to loaded. 
The boot infor script file shows:


[COLOR="DarkSlateGray"]```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:   Welcome to SUSE LINUX 10.0 
                       (i586) - Kernel ().
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.96) is installed in the boot sector 
                       of sda3 and looks at sector 23085406 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /boot/grub/stage2.
    Operating System:   Welcome to SUSE LINUX 10.0 
                       (i586) - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     2,104,514     2,104,452  82 Linux swap / Solaris
/dev/sda2           2,104,515    23,085,404    20,980,890  83 Linux
/dev/sda3    *     23,085,405    84,527,103    61,441,699  83 Linux
/dev/sda4          84,529,150   156,301,311    71,772,162   5 Extended
/dev/sda5          84,529,152   154,204,159    69,675,008  83 Linux
/dev/sda6         154,206,208   156,301,311     2,095,104  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1                                               swap       
/dev/sda2        f1d92cf2-4c02-40ac-a0e8-25891fa18edc   reiserfs   
/dev/sda3        e63908da-ef76-4c96-8820-8975eeeaf7e4   reiserfs   
/dev/sda5        ebe56bd7-ff91-4ec5-8c2c-1d2330db3337   ext4       
/dev/sda6        5bf81900-1e0a-4020-8fd3-3c9a49c6dcb1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sda2            /                    reiserfs   acl,user_xattr        1 1
/dev/sda3            /home                ext2       acl,user_xattr        1 2
/dev/sda1            swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
/dev/dvdram          /media/dvdram        subfs      noauto,fs=cdfss,ro,procuid,nosuid,nodev,exec,iocharset=utf8 0 0
/dev/fd0             /media/floppy        subfs      noauto,fs=floppyfss,procuid,nodev,nosuid,sync 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Wed Jun  7 20:43:01 UTC 2006

color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,2)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE LINUX 10.0
    root (hd0,2)
    kernel /boot/vmlinuz root=/dev/sda3 vga=0x31a selinux=0    resume=/dev/sda1  splash=silent showopts
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE LINUX 10.0
    root (hd0,2)
    kernel /boot/vmlinuz root=/dev/sda3 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sda3            /                    reiserfs   acl,user_xattr        1 1
/dev/sda1            swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
/dev/sda2            /data1               auto       noauto,user           0 0
/dev/dvdram          /media/dvdram        subfs      noauto,fs=cdfss,ro,procuid,nosuid,nodev,exec,iocharset=utf8 0 0
/dev/fd0             /media/floppy        subfs      noauto,fs=floppyfss,procuid,nodev,nosuid,sync 0 0
none                 /subdomain       subdomainfs noauto         0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst                             0
            ?? = ??             boot/grub/stage2                               1
            ?? = ??             boot/initrd                                    3
            ?? = ??             boot/initrd-2.6.13-15-smp                      3
            ?? = ??             boot/vmlinuz                                   1
            ?? = ??             boot/vmlinuz-2.6.13-15-smp                     1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ebe56bd7-ff91-4ec5-8c2c-1d2330db3337 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ebe56bd7-ff91-4ec5-8c2c-1d2330db3337 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ebe56bd7-ff91-4ec5-8c2c-1d2330db3337
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "SUSE LINUX 10.0 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod reiserfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root e63908da-ef76-4c96-8820-8975eeeaf7e4
	linux /boot/vmlinuz root=/dev/sda3 vga=0x31a selinux=0 resume=/dev/sda1 splash=silent showopts
	initrd /boot/initrd
}
menuentry "Failsafe -- SUSE LINUX 10.0 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod reiserfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root e63908da-ef76-4c96-8820-8975eeeaf7e4
	linux /boot/vmlinuz root=/dev/sda3 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3
	initrd /boot/initrd
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ebe56bd7-ff91-4ec5-8c2c-1d2330db3337 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5bf81900-1e0a-4020-8fd3-3c9a49c6dcb1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  49.050613403 = 52.667695104   boot/grub/core.img                             1
  44.643005371 = 47.935062016   boot/grub/grub.cfg                             1
  45.572265625 = 48.932847616   boot/initrd.img-2.6.38-8-generic               2
  49.049942017 = 52.666974208   boot/vmlinuz-2.6.38-8-generic                  1
  45.572265625 = 48.932847616   initrd.img                                     2
  49.049942017 = 52.666974208   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```[/COLOR]

Anyone knows: what's wrong with these settings??

---

### Post by Rubi1200 on 2011-06-23
Have you tried running ```
sudo update-grub
``` in Ubuntu?

---

### Post by aixilin on 2011-06-24
> **Rubi1200 said:**
> Have you tried running ```
sudo update-grub
``` in Ubuntu?

Yes, I tried, it shows:
```
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found SUSE LINUX 10.0 (i586) OSS on /dev/sda2
Found SUSE LINUX 10.0 (i586) on /dev/sda3
done

```

---

### Post by Rubi1200 on 2011-06-24
Which partition are you trying to boot, sda2 or sda3? Which one fails to load? Try them both.

---

### Post by aixilin on 2011-06-24
> **Rubi1200 said:**
> Which partition are you trying to boot, sda2 or sda3? Which one fails to load? Try them both.

sda2 is the suse safe mode; sda3 is the suse10 boot drive. 
I have tried both, neither are working. 
There were only black screen, then afterwards, it went back to the grub 
window. 

Because the Suse10 uses the Grub legacy, whereas the Ubuntu11 uses the Grub 2. Is that a problem? 
In the end of the boot info file, it shows one error:"unlzma: Decoder error". What does that mean?

---

### Post by Rubi1200 on 2011-06-24
The decoder error is nothing to worry about; it has something to do with the way the script parses information.

I see that legacy-GRUB is installed to the PBR of sda2 whereas GRUB2 is in the MBR of sda.

Try reinstalling GRUB and see if that helps:

from within the Ubuntu install, run these commands:

```
sudo grub-install --recheck /dev/sda
```

```
sudo update-grub
```

Then try to boot again.

---

### Post by oldfred on 2011-06-24
I am not familiar with SuSe, but it looks like the os-prober fixed the boot partition number to boot from sda3 but not the root partition number in the linux line. Old grub is one number different from grub2. And SuSe has sda1 as swap.

```
menuentry "SUSE LINUX 10.0 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root e63908da-ef76-4c96-8820-8975eeeaf7e4
    linux /boot/vmlinuz root=[COLOR=Blue]/dev/sda3[/COLOR] vga=0x31a selinux=0 resume=[COLOR=Red]/dev/sda1[/COLOR] splash=silent showopts
    initrd /boot/initrd
}
```When you have a boot partition separate from the root partition, the set root line ( and search)refers to the boot, but the linux line should refer to root. But root is sda2? 

I would copy above to 40_custom after experimenting in booting. YOu can at grub menu use e for edit and change sda3/sda1 - both to sda2 or try others if that does not work. Once you find the correct combination then copy above and permantently edit it in 40_custom.

gksudo gedit /etc/grub.d/40_custom
#Then do:
sudo update-grub

---

### Post by aixilin on 2011-06-24
Thanks for your help, but it is still not working. The grub.cfg file is same as before. 

From Ubuntu, the grub2 can find the bootable files in sda2 (suse root), but failed to boot in. 

> **Rubi1200 said:**
> The decoder error is nothing to worry about; it has something to do with the way the script parses information.

I see that legacy-GRUB is installed to the PBR of sda2 whereas GRUB2 is in the MBR of sda.

Try reinstalling GRUB and see if that helps:

from within the Ubuntu install, run these commands:

```
sudo grub-install --recheck /dev/sda
```

```
sudo update-grub
```

Then try to boot again.

---

### Post by aixilin on 2011-06-24
Thanks for your suggestion. The root of SuSe is in sda3. The sda1 is the swap, sda 2 is the fail safe part. I replace [COLOR=Red]resume=/dev/sda1[/COLOR] with [COLOR=Red]resume=/dev/sda3[/COLOR] and reboot, then it failed again. I also tried use sda2 here, but failed.

> **oldfred said:**
> I am not familiar with SuSe, but it looks like the os-prober fixed the boot partition number to boot from sda3 but not the root partition number in the linux line. Old grub is one number different from grub2. And SuSe has sda1 as swap.

```
menuentry "SUSE LINUX 10.0 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root e63908da-ef76-4c96-8820-8975eeeaf7e4
    linux /boot/vmlinuz root=[COLOR=Blue]/dev/sda3[/COLOR] vga=0x31a selinux=0 resume=[COLOR=Red]/dev/sda1[/COLOR] splash=silent showopts
    initrd /boot/initrd
}
```When you have a boot partition separate from the root partition, the set root line ( and search)refers to the boot, but the linux line should refer to root. But root is sda2? 

I would copy above to 40_custom after experimenting in booting. YOu can at grub menu use e for edit and change sda3/sda1 - both to sda2 or try others if that does not work. Once you find the correct combination then copy above and permantently edit it in 40_custom.

gksudo gedit /etc/grub.d/40_custom
#Then do:
sudo update-grub

---

### Post by oldfred on 2011-06-24
You also installed grub legacy to the partition boot sector of sda3. We can try chainloading.

Copy this into 40_custom.

```
menuentry "Chainload Other Systems Grub Menu on sda3" {
set root=(hd0,3)
chainloader +1
}

```

sudo update-grub


If it works then you can update descriptions to whatever you want.

---

