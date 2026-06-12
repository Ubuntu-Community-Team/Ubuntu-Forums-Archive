---
title: "Restoring W7 Boot Loader"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Shane-C on 2010-11-17
Hey all,

I've spent the better part of two days googling and trying out fixes. I've done quite a bit but still have the same issue.

I want Ubuntu to be my secondary operating system. As such I'd like Ubuntu to be on the W7 bootloader, not W7 on Grub. This is, mainly, so that I can press power and not sit at the computer to manually select W7.

I've tried EasyBCD, many times, but when I select both Grub (legacy) and Grub 2, add it, overwrite the MBR, and reboot, it wipes out the bootloader entirely, and Windows 7 boots up.

I'm all out of ideas. Any help you can offer would be VERY appreciated.

Ubuntu v10.10
Windows 7 Home Premium

Here is a partial FDISK
```

/dev/sda1     Dell Utility
/dev/sda2     HPFS/NFTS [BOOT]
/dev/sda3     HPFS/NFTS
/dev/sda4     Extended
/dev/sda5     Linux
/dev/sda6     Linux swap / Solaris

```

---

### Post by Quackers on 2010-11-17
Welcome to UF.
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Shane-C on 2010-11-17
Thank you for the reply!

Here is the information you requested:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   527,485,110   496,683,191   7 HPFS/NTFS
/dev/sda4         527,486,974   625,141,759    97,654,786   5 Extended
/dev/sda5         527,486,976   621,053,951    93,566,976  83 Linux
/dev/sda6         621,056,000   625,141,759     4,085,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        C82E2C1F2E2C08D0                       ntfs       RECOVERY                      
/dev/sda3        24022EB7022E8DBC                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        77728a21-c45b-44b1-9ff1-fe5de7c93e3c   ext4                                     
/dev/sda6        ea75a37e-b6b2-40ac-8fa8-695437ede4c0   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=77728a21-c45b-44b1-9ff1-fe5de7c93e3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=77728a21-c45b-44b1-9ff1-fe5de7c93e3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 77728a21-c45b-44b1-9ff1-fe5de7c93e3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c82e2c1f2e2c08d0
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=77728a21-c45b-44b1-9ff1-fe5de7c93e3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ea75a37e-b6b2-40ac-8fa8-695437ede4c0 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 308.8GB: boot/grub/core.img
 274.6GB: boot/grub/grub.cfg
 271.0GB: boot/initrd.img-2.6.35-22-generic
 308.8GB: boot/vmlinuz-2.6.35-22-generic
 271.0GB: initrd.img
 308.8GB: vmlinuz

```

---

### Post by Quackers on 2010-11-17
Can I take it that when either OS is chosen from the grub menu the chosen OS boots ok?
As for making W7 the default OS you can install Startup Manager from Synaptic Package Manager and change the default OS to Windows. Or alternately you can change the GRUB_DEFAULT=0 parameter to GRUB_DEFAULT=1 (probably) in /etc/default/grub. Details here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Shane-C on 2010-11-17
> **Quackers said:**
> Can I take it that when either OS is chosen from the grub menu the chosen OS boots ok?
As for making W7 the default OS you can install Startup Manager from Synaptic Package Manager and change the default OS to Windows. Or alternately you can change the GRUB_DEFAULT=0 parameter to GRUB_DEFAULT=1 (probably) in /etc/default/grub. Details here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Installed the Startup Manager and it worked like a charm! While not the preferred option it certainly did the trick.

While I'm comfortable stopping at that point, I am wondering, though, why EasyBCD didn't work in restoring the W7 Bootloader. Any ideas?

At any rate thank you for your help!

---

### Post by Quackers on 2010-11-17
You're welcome.
Whilst I have used EasyBCD to boot Mac OS X from the Windows bootloader I have not used it to boot Ubuntu. although I seem to remember it was a fairly straightforward process. Maybe something went wrong in your case.
I have never tried restoring a bootloader with it and was unaware that it could do that.

---

### Post by Mark Phelps on 2010-11-18
> **Shane-C said:**
> While I'm comfortable stopping at that point, I am wondering, though, why EasyBCD didn't work in restoring the W7 Bootloader. Any ideas?

Yeah ... go ask the Experts -- at the NeoSmart Technology EasyBCD Support forum -- not here.

---

