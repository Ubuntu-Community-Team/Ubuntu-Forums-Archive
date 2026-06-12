---
title: "Grub Problem on 10.10 -&gt;11.04 Upgrade"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by kmand on 2011-05-03
I just upgraded from 10.10 to 11.04. On reboot grub2 had issues. The arrow keys didn't work, and various grub symbols were not found.

So I booted off a grub2 cd and manually booted into 11.04. I went ahead and did an apt-get purge and add on the grub2 packages. It did a reinstall and update-grub.

This grub2 boots with out the key or symbol problems. However, the generated grub.cfg is wrong. I should say my 11.04 is on /dev/sda2 and there is a copy of 10.10 on /dev/sda6.

The grub.cfg is wierd. It has /dev/sda's where there should be hd0's. It has "search's" which give "error file not found, you need to load the kernel first". It has a mixup between 11.04 kernels and root= on the 10.10 partition. It lists the generic-pae and not the straight generic.

Again, I can type a set root/linux/initrd sequence manually, as I could from the grub2 cd, but the grub.cfg is just not right for automated booting.

Any ideas? Is the old 10.10 partition confusing update-grub?

---

### Post by Quackers on 2011-05-03
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kmand on 2011-05-04
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,610,014    77,609,952   7 HPFS/NTFS
/dev/sda2          77,610,015   261,923,759   184,313,745  83 Linux
/dev/sda4         261,923,760   488,392,064   226,468,305   5 Extended
/dev/sda5         261,923,823   282,406,634    20,482,812  82 Linux swap / Solaris
/dev/sda6         282,406,636   466,720,380   184,313,745  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80C4F861C4F85ABC                       ntfs                                     
/dev/sda2        7e620b67-4a1c-40b9-a09b-ac51b03b1910   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c7f7f494-2353-43e8-b216-55cb42f04961   swap                                     
/dev/sda6        7e620b67-4a1c-40b9-a09b-ac51b03b1910   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,commit=0)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
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
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-9-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
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
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35.4-km (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35.4-km
}
menuentry "Ubuntu, with Linux 2.6.35.4-km (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35.4-km
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-29-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-29-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
#UUID=C0FC203AFC202D5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=f682dedc-3532-4783-9f19-d3c952862f11 none            swap    sw              0       0
/dev/sda5  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda4	/swap	ext3	defaults,relatime	0	1

=================== sda2: Location of files loaded by Grub: ===================


  51.4GB: boot/grub/core.img
  42.2GB: boot/grub/grub.cfg
  78.9GB: boot/initrd.img-2.6.24-21-xen
 101.2GB: boot/initrd.img-2.6.38-8-generic
  91.8GB: boot/initrd.img-2.6.38-8-generic-pae
  86.2GB: boot/initrd.img-2.6.38-9-generic
  93.3GB: boot/initrd.img-2.6.38-9-generic-pae
  82.2GB: boot/vmlinuz-2.6.38-8-generic
  82.3GB: boot/vmlinuz-2.6.38-8-generic-pae
  85.5GB: boot/vmlinuz-2.6.38-9-generic
  85.7GB: boot/vmlinuz-2.6.38-9-generic-pae
  93.3GB: initrd.img
  86.2GB: initrd.img.old
  85.7GB: vmlinuz
  85.5GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
root		(hd0,1)
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Xen 3.3 / Ubuntu 10.10, kernel 2.6.24-21-xen
root		(hd0,1)
kernel		/boot/xen-3.3.gz
module		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro console=tty0
module		/boot/initrd.img-2.6.24-21-xen
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic-pae
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.35-22-generic-pae
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic-pae (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.35-22-generic-pae

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.24-21-xen
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-xen
quiet

title		Ubuntu 10.10, kernel 2.6.24-21-xen (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.24-21-xen

title		Ubuntu 10.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 10.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu, with Linux 2.6.35-22-generic"
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
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
menuentry 'Ubuntu, with Linux 2.6.35.4-km' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35.4-km
}
menuentry 'Ubuntu, with Linux 2.6.35.4-km (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35.4-km ...'
	linux	/boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35.4-km
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-29-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-29-generic ...'
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 80C4F861C4F85ABC
	chainloader +1
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-25-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=/dev/sda2 ro quiet splash nomodeset
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/memtest86+.bin 
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
#UUID=C0FC203AFC202D5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=f682dedc-3532-4783-9f19-d3c952862f11 none            swap    sw              0       0
/dev/sda5  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda4	/swap	ext3	defaults,relatime	0	1

=================== sda6: Location of files loaded by Grub: ===================


 156.2GB: boot/grub/core.img
 146.2GB: boot/grub/grub.cfg
 159.5GB: boot/grub/menu.lst
 156.3GB: boot/initrd.img-2.6.31-21-generic
 178.2GB: boot/initrd.img-2.6.32-25-generic
 181.4GB: boot/initrd.img-2.6.35-22-generic
 181.4GB: boot/initrd.img-2.6.35-22-generic-pae
 207.6GB: boot/initrd.img-2.6.35-23-generic
 207.6GB: boot/initrd.img-2.6.35-23-generic-pae
 212.3GB: boot/initrd.img-2.6.35-24-generic
 212.3GB: boot/initrd.img-2.6.35-24-generic-pae
 225.2GB: boot/initrd.img-2.6.35-25-generic
 225.3GB: boot/initrd.img-2.6.35-25-generic-pae
 185.6GB: boot/initrd.img-2.6.35-26-generic
 198.1GB: boot/initrd.img-2.6.35-26-generic-pae
 190.6GB: boot/initrd.img-2.6.35-27-generic
 190.6GB: boot/initrd.img-2.6.35-27-generic-pae
 186.0GB: boot/initrd.img-2.6.35-28-generic
 186.0GB: boot/initrd.img-2.6.35-28-generic-pae
 198.9GB: boot/initrd.img-2.6.35-29-generic
 199.0GB: boot/initrd.img-2.6.35-29-generic-pae
 187.3GB: boot/initrd.img-2.6.35.4-km
 156.4GB: boot/vmlinuz-2.6.31-21-generic
 238.2GB: boot/vmlinuz-2.6.32-25-generic
 174.4GB: boot/vmlinuz-2.6.35-22-generic
 174.4GB: boot/vmlinuz-2.6.35-22-generic-pae
 195.8GB: boot/vmlinuz-2.6.35-23-generic
 192.2GB: boot/vmlinuz-2.6.35-23-generic-pae
 181.1GB: boot/vmlinuz-2.6.35-24-generic
 181.1GB: boot/vmlinuz-2.6.35-24-generic-pae
 183.9GB: boot/vmlinuz-2.6.35-25-generic
 183.9GB: boot/vmlinuz-2.6.35-25-generic-pae
 184.3GB: boot/vmlinuz-2.6.35-26-generic
 184.4GB: boot/vmlinuz-2.6.35-26-generic-pae
 187.0GB: boot/vmlinuz-2.6.35-27-generic
 187.0GB: boot/vmlinuz-2.6.35-27-generic-pae
 185.0GB: boot/vmlinuz-2.6.35-28-generic
 185.0GB: boot/vmlinuz-2.6.35-28-generic-pae
 186.7GB: boot/vmlinuz-2.6.35-29-generic
 187.9GB: boot/vmlinuz-2.6.35-29-generic-pae
 191.7GB: boot/vmlinuz-2.6.35.4-km
 199.0GB: initrd.img
 198.9GB: initrd.img.old
 187.9GB: vmlinuz
 174.4GB: vmlinuz.off
 186.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 

```

---

### Post by Quackers on 2011-05-04
I can give you a couple of pointers, but I'm not exactly sure on how to fix it.

Firstly in sda1 you have the normal Windows boot files PLUS /boot/grub/core.img
That shouldn't be in there. Does Windows boot ok from grub?
Secondly your 10.10 installation in sda6 has a /boot/grub/menu.lst in with the grub boot files. This would suggest that grub (legacy) has been installed at some time rather than grub2, which would be the default bootloader for 10.10 (unless the 10.10 installation was an upgrade from 9.04 or before).

Lastly, and most peculiarly, according to blkid your sda2 and sda6 partitions have the same UUID, which is 7e620b67-4a1c-40b9-a09b-ac51b03b1910
As far as I'm aware this is very odd, if not impossible, unless one is a clone of the other, then installed over (if you see what I mean).

---

### Post by kmand on 2011-05-04
Quakers

Thanks for the pointers, it helped a lot!

Specifically

1) As far as Windows on sda1, I made a typo on one of the installs that stuck in the not needed grub directory. I've deleted it, and the windows boot is fine.

2) The big thing was that the 10.10 sda6 directory was a dd clone of sda2 prior to 11.04 upgrade, which is why it had the same UUID.

I've since given sda6 a different UUID and rerun update-grub.The result is a lot better but not perfect.

The grub.cfg puts up a default of the 11.04 generic-pae correctly rooted correctly at the sda2 UUID. It boot fine, though I really want the non-pae generic to be the default. The non-pae does not even appear on the first page. I have to select OLD Linux to choose it.

What does appear on first page are the 10.10/sda6 kernels. These entries are not correct. Their search line has the correct UUID for sda6, but the linux root= line has the sda2 UUID.

As to the origin of the 10.10 partition as you suspected it was updated from a 9.04 with grub legacy (and several updates before that).

Any ideas on how to get the sda2 entries on the first page, and corrected sda6 entries on the OLD page? 



> **Quackers said:**
> I can give you a couple of pointers, but I'm not exactly sure on how to fix it.

Firstly in sda1 you have the normal Windows boot files PLUS /boot/grub/core.img
That shouldn't be in there. Does Windows boot ok from grub?
Secondly your 10.10 installation in sda6 has a /boot/grub/menu.lst in with the grub boot files. This would suggest that grub (legacy) has been installed at some time rather than grub2, which would be the default bootloader for 10.10 (unless the 10.10 installation was an upgrade from 9.04 or before).

Lastly, and most peculiarly, according to blkid your sda2 and sda6 partitions have the same UUID, which is 7e620b67-4a1c-40b9-a09b-ac51b03b1910
As far as I'm aware this is very odd, if not impossible, unless one is a clone of the other, then installed over (if you see what I mean).

---

### Post by oldfred on 2011-05-04
The old version of boot info script does not parse the MBR with grub2 1.99 from Natty well. So you must have Natty's grub in the MBR.

There is a testing version of boot info script that parses MBR better but it has not been finalized.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

You have a lot of kernels and grub finds all of them. You may want to houseclean older one. We normally suggest you keep the working one and one older one, just in case. Since you have pae also I do not know for sure what versions you may want to keep.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Whichever system you boot is determined by which partition's grub2 boot loader is in the MBR. That will be the first lines in the grub menu.

You can boot into a working Ubuntu and install grub2's boot loader to the MBR to make it the primary boot system. Only one line is required:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by kansasnoob on 2011-05-04
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Hello good friend ):P

We kind of need to start using the development version of BIS as I explained here:

[http://ubuntuforums.org/showpost.php?p=10756222&postcount=2](http://ubuntuforums.org/showpost.php?p=10756222&postcount=2)

I'm holding off a bit about contacting Gert because of the content of the last private message to me, it's called being polite :)

We can live with this method for now.

---

### Post by kansasnoob on 2011-05-04
> **oldfred said:**
> The old version of boot info script does not parse the MBR with grub2 1.99 from Natty well. So you must have Natty's grub in the MBR.

There is a testing version of boot info script that parses MBR better but it has not been finalized.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

You have a lot of kernels and grub finds all of them. You may want to houseclean older one. We normally suggest you keep the working one and one older one, just in case. Since you have pae also I do not know for sure what versions you may want to keep.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Whichever system you boot is determined by which partition's grub2 boot loader is in the MBR. That will be the first lines in the grub menu.

You can boot into a working Ubuntu and install grub2's boot loader to the MBR to make it the primary boot system. Only one line is required:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

Good to see you around oldfred :)

I got sidetracked while searching for my last post regarding the status of BIS, stumbled upon a few posts I hadn't replied to :(

I was going to suggest either step #2 or step #3 of this post to the OP:

[http://ubuntuforums.org/showpost.php?p=10764475&postcount=12](http://ubuntuforums.org/showpost.php?p=10764475&postcount=12)

I'm seeing somewhat of a pattern with grub failure in Natty but I've not been able to duplicate it on my own box so I can't be sure what the problem is :(

I have repeated both of those processes several times so I'm sure they will work, but I had a thought earlier today :rolleyes:

I haven't bothered to figure out how to revert "echo <packagename> hold | sudo dpkg --set-selections". I just never gave it any thought :oops:

I'm sure a bit of Googling will get me straightened out.

---

### Post by kansasnoob on 2011-05-04
In regards to this:

> I haven't bothered to figure out how to revert "echo <packagename> hold | sudo dpkg --set-selections".

It's easy:

```
echo <packagename> install | sudo dpkg --set-selections
```

Just change "hold" to "install" :)

---

### Post by kmand on 2011-05-05
> **oldfred said:**
> The old version of boot info script does not parse the MBR with grub2 1.99 from Natty well. So you must have Natty's grub in the MBR.

There is a testing version of boot info script that parses MBR better but it has not been finalized.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'



Are you suggesting I run the newer boot_info_script so I can post more informative diagnostic info?

> 

You have a lot of kernels and grub finds all of them. You may want to houseclean older one.


The old kernels are on sda6 the pre-update clone. As you can see from the earlier posting I had deleted them all on the updated sda2. The clone is meant mostly to reflect history so I left those alone.

> 

You can boot into a working Ubuntu and install grub2's boot loader to the MBR to make it the primary boot system. Only one line is required:

[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]


Of course this is what I did do from sda2 to start with after being sure with apt-get that I had the latest Naty grub packages.

---

### Post by oldfred on 2011-05-05
Did you change the UUIDs as Quackers originally suggested? You cannot have two partitions with the same UUID.

---

### Post by kmand on 2011-05-05
> **oldfred said:**
> Did you change the UUIDs as Quackers originally suggested? You cannot have two partitions with the same UUID.

Yes, that was the first thing I did, and as I replied that did solve the most important issues. The sda2/11.04 entries are correct.

The remaining issues are that the default (and only sda2) entries on the main boot page is for generic-pae. The rest (and more relevant) sda2 entries only show by selecting OLD LINUX.

In addition the sda6 entries that DO show on the main page have correct search UUID's, but incorrect root= UUIDs.

I'll include the current output from the development boot_info_script for clarity.

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    77,610,014    77,609,952   7 NTFS / exFAT / HPFS
/dev/sda2          77,610,015   261,923,759   184,313,745  83 Linux
/dev/sda4         261,923,760   488,392,064   226,468,305   5 Extended
/dev/sda5         261,923,823   282,406,634    20,482,812  82 Linux swap / Solaris
/dev/sda6         282,406,636   466,720,380   184,313,745  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        80C4F861C4F85ABC                       ntfs       
/dev/sda2        7e620b67-4a1c-40b9-a09b-ac51b03b1910   ext4       
/dev/sda5        c7f7f494-2353-43e8-b216-55cb42f04961   swap       
/dev/sda6        84d1c493-2f49-43e7-a4da-901333ca6f09   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
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
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-9-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
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
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 80C4F861C4F85ABC
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35.4-km (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35.4-km
}
menuentry "Ubuntu, with Linux 2.6.35.4-km (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35.4-km
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-29-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-29-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu, with Linux 2.6.35-29-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 84d1c493-2f49-43e7-a4da-901333ca6f09
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
#UUID=C0FC203AFC202D5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=f682dedc-3532-4783-9f19-d3c952862f11 none            swap    sw              0       0
/dev/sda5  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda4	/swap	ext3	defaults,relatime	0	1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  47.922282696 = 51.456159232   boot/grub/core.img                             1
  59.081752300 = 63.438548480   boot/grub/grub.cfg                             1
  73.559699535 = 78.984125952   boot/initrd.img-2.6.24-21-xen                  1
  94.295093060 = 101.248585216  boot/initrd.img-2.6.38-8-generic               2
  85.542701244 = 91.850776064   boot/initrd.img-2.6.38-8-generic-pae           2
  80.285464764 = 86.205861376   boot/initrd.img-2.6.38-9-generic               2
  86.904983044 = 93.313515008   boot/initrd.img-2.6.38-9-generic-pae           2
  76.585769176 = 82.233343488   boot/vmlinuz-2.6.38-8-generic                  2
  76.652297497 = 82.304777728   boot/vmlinuz-2.6.38-8-generic-pae              1
  79.667800426 = 85.542649344   boot/vmlinuz-2.6.38-9-generic                  2
  79.851520061 = 85.739916800   boot/vmlinuz-2.6.38-9-generic-pae              2
  86.904983044 = 93.313515008   initrd.img                                     2
  80.285464764 = 86.205861376   initrd.img.old                                 2
  79.851520061 = 85.739916800   vmlinuz                                        2
  79.667800426 = 85.542649344   vmlinuz.old                                    2

=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
root		(hd0,1)
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Xen 3.3 / Ubuntu 10.10, kernel 2.6.24-21-xen
root		(hd0,1)
kernel		/boot/xen-3.3.gz
module		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro console=tty0
module		/boot/initrd.img-2.6.24-21-xen
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic-pae
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.35-22-generic-pae
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic-pae (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.35-22-generic-pae

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.24-21-xen
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-xen
quiet

title		Ubuntu 10.10, kernel 2.6.24-21-xen (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-xen root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.24-21-xen

title		Ubuntu 10.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 10.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu, with Linux 2.6.35-22-generic"
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
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
menuentry 'Ubuntu, with Linux 2.6.35.4-km' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35.4-km
}
menuentry 'Ubuntu, with Linux 2.6.35.4-km (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35.4-km ...'
	linux	/boot/vmlinuz-2.6.35.4-km root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35.4-km
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-29-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-29-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-29-generic ...'
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-26-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-26-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=7e620b67-4a1c-40b9-a09b-ac51b03b1910 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e620b67-4a1c-40b9-a09b-ac51b03b1910
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 80C4F861C4F85ABC
	chainloader +1
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-25-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=/dev/sda2 ro quiet splash nomodeset
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=7b393dc4-9e6e-4a0a-9d50-f435e32440e2 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7b393dc4-9e6e-4a0a-9d50-f435e32440e2
	linux /boot/memtest86+.bin 
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=84d1c493-2f49-43e7-a4da-901333ca6f09  /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
#UUID=C0FC203AFC202D5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=f682dedc-3532-4783-9f19-d3c952862f11 none            swap    sw              0       0
/dev/sda5  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda4	/swap	ext3	defaults,relatime	0	1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 145.560831070 = 156.294752256  boot/grub/core.img                             1
 167.617021561 = 179.977406464  boot/grub/grub.cfg                             3
 148.578908920 = 159.535388672  boot/grub/menu.lst                             1
 145.627378464 = 156.366206976  boot/initrd.img-2.6.31-21-generic             27
 166.060415268 = 178.306013184  boot/initrd.img-2.6.32-25-generic              2
 168.974477768 = 181.434963968  boot/initrd.img-2.6.35-22-generic              2
 168.982290268 = 181.443352576  boot/initrd.img-2.6.35-22-generic-pae          2
 193.345335007 = 207.602972672  boot/initrd.img-2.6.35-23-generic              2
 193.435319901 = 207.699593216  boot/initrd.img-2.6.35-23-generic-pae          2
 197.755727768 = 212.338595840  boot/initrd.img-2.6.35-24-generic              2
 197.766073227 = 212.349704192  boot/initrd.img-2.6.35-24-generic-pae          1
 209.791479111 = 225.261885440  boot/initrd.img-2.6.35-25-generic              2
 209.832918167 = 225.306380288  boot/initrd.img-2.6.35-25-generic-pae          2
 172.934778214 = 185.687304192  boot/initrd.img-2.6.35-26-generic              2
 184.543310165 = 198.151870464  boot/initrd.img-2.6.35-26-generic-pae          2
 177.594224930 = 190.690347008  boot/initrd.img-2.6.35-27-generic              1
 177.607290268 = 190.704375808  boot/initrd.img-2.6.35-27-generic-pae          2
 173.292695999 = 186.071615488  boot/initrd.img-2.6.35-28-generic              2
 173.299276352 = 186.078681088  boot/initrd.img-2.6.35-28-generic-pae          2
 185.318227768 = 198.983931904  boot/initrd.img-2.6.35-29-generic              2
 185.375455856 = 199.045380096  boot/initrd.img-2.6.35-29-generic-pae          1
 174.476964951 = 187.343214592  boot/initrd.img-2.6.35.4-km                    2
 145.703207016 = 156.447627264  boot/vmlinuz-2.6.31-21-generic                33
 221.853445053 = 238.213322752  boot/vmlinuz-2.6.32-25-generic                 3
 162.446641922 = 174.425753600  boot/vmlinuz-2.6.35-22-generic                 1
 162.456819534 = 174.436681728  boot/vmlinuz-2.6.35-22-generic-pae             1
 182.447462082 = 195.901470720  boot/vmlinuz-2.6.35-23-generic                 1
 179.043054581 = 192.246016000  boot/vmlinuz-2.6.35-23-generic-pae             1
 168.705041885 = 181.145659392  boot/vmlinuz-2.6.35-24-generic                 1
 168.728601456 = 181.170956288  boot/vmlinuz-2.6.35-24-generic-pae             1
 171.322710037 = 183.956359168  boot/vmlinuz-2.6.35-25-generic                 1
 171.306726456 = 183.939196928  boot/vmlinuz-2.6.35-25-generic-pae             1
 171.728487015 = 184.392058880  boot/vmlinuz-2.6.35-26-generic                 1
 171.759851456 = 184.425736192  boot/vmlinuz-2.6.35-26-generic-pae             1
 174.219160080 = 187.066398720  boot/vmlinuz-2.6.35-27-generic                 1
 174.223283768 = 187.070826496  boot/vmlinuz-2.6.35-27-generic-pae             1
 172.331155777 = 185.039169536  boot/vmlinuz-2.6.35-28-generic                 1
 172.307535172 = 185.013807104  boot/vmlinuz-2.6.35-28-generic-pae             1
 173.905000687 = 186.729072640  boot/vmlinuz-2.6.35-29-generic                 1
 175.056734085 = 187.965736960  boot/vmlinuz-2.6.35-29-generic-pae             1
 178.542901993 = 191.708981248  boot/vmlinuz-2.6.35.4-km                       1
 185.375455856 = 199.045380096  initrd.img                                     1
 185.318227768 = 198.983931904  initrd.img.old                                 2
 175.056734085 = 187.965736960  vmlinuz                                        1
 162.456819534 = 174.436681728  vmlinuz.off                                    1
 173.905000687 = 186.729072640  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by oldfred on 2011-05-05
You could manually edit the grub.cfg on sda6, but they intentionally make it difficult as it is read only also.

It may just be easier to manually edit one boot stanza as you are booting in the grub menu  with the correct UUID or even just root=/dev/sda6 to get to boot the install in sda6. Then run the update-grub from there.

At grub menu for boot into sda6, select e for manual edit. Correct boot stanza to correct UUID or change from UUID to root=/dev/sda6. 

Then once booted into sda6:
sudo update-grub

---

### Post by kmand on 2011-05-06
> **oldfred said:**
> You could manually edit the grub.cfg on sda6, but they intentionally make it difficult as it is read only also.

It may just be easier to manually edit one boot stanza as you are booting in the grub menu  with the correct UUID or even just root=/dev/sda6 to get to boot the install in sda6. Then run the update-grub from there.

At grub menu for boot into sda6, select e for manual edit. Correct boot stanza to correct UUID or change from UUID to root=/dev/sda6. 

Then once booted into sda6:
sudo update-grub

Yes, I'm quite adept at editing the stanza's on the fly, or even typing from scratch from the grub command prompt. Still I would like it to at least auto boot to the right 11.04 entry.

I guess I will submit a bug.


I guess I

---

### Post by oldfred on 2011-05-06
If you boot into your install in sda6 does not update-grub fix it? An update grub from your install in sda2 will not update the grub menu in sda6. And the os-prober in sda2 finds its info for sda2's grub.cfg from the grub.cfg in sda6. So sda6 has to be correct before sda2 can be corrected. So actually you have to update-grub in sda6 then update-grub in sda2.

Rather than having to always update both, I find it easier to just boot the partition. Ranch hand posted this which he uses for his alpha/beta version as the kernel often changes. Just add this to 40_custom and run update-grub. You then will always boot the newest kernel in the other partition.

gksudo gedit /etc/grub.d/40_custom

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

