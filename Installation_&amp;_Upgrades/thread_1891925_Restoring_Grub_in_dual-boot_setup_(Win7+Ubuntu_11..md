---
title: "Restoring Grub in dual-boot setup (Win7+Ubuntu 11.10)"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by Halibutt on 2011-12-06
Hello there. I recently tried to update my Ubuntu to 11.10 in a dual-boot setup. The upgrade partially failed ([detailed description here]("http://ubuntuforums.org/showthread.php?t=1891079")) but in the end I reinstalled the system from a CD and all is fine. 

Somewhere in the process the grub loader got duplicated. First I saw the grub menu (black background). In order to get to ubuntu I had to chose Windows 7 option, then another Grub window appeared, where I had to chose Ubuntu - and it worked. 

However, some nasty devil forced me to try to fix that. I tried [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") (here's the [log file pastebin]("http://paste.ubuntu.com/762133/")) and all went fine. Only one grub menu now when I start my computer and ubuntu loads just fine. However, I can't boot to Windows 7 now, the option is there, but hitting enter does nothing. 

Any ideas?
Cheers and thanks in advance for any help.

---

### Post by MAFoElffen on 2011-12-06
> **Halibutt said:**
> Hello there. I recently tried to update my Ubuntu to 11.10 in a dual-boot setup. The upgrade partially failed ([detailed description here]("http://ubuntuforums.org/showthread.php?t=1891079")) but in the end I reinstalled the system from a CD and all is fine. 

Somewhere in the process the grub loader got duplicated. First I saw the grub menu (black background). In order to get to ubuntu I had to chose Windows 7 option, then another Grub window appeared, where I had to chose Ubuntu - and it worked. 

However, some nasty devil forced me to try to fix that. I tried [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") (here's the [log file pastebin]("http://paste.ubuntu.com/762133/")) and all went fine. Only one grub menu now when I start my computer and ubuntu loads just fine. However, I can't boot to Windows 7 now, the option is there, but hitting enter does nothing. 

Any ideas?
Cheers and thanks in advance for any help.
If you went to a terminal session and rean the grub updater, it will restart OS Probe and rebuild the menu tree:
```

sudo update-grub

```

---

### Post by Halibutt on 2011-12-06
Nope, no success. The command runs just fine (report below), but after a restart when I choose Windows 7 the screen goes blank for a couple of seconds (white cursor blinking) and then goes back to main grub screen. Trying the same command from recovery console's command line gives me some access violation error.

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

---

### Post by kio_http on 2011-12-07
If you have a Windows 7 Retail disk, boot it and launch start up repair it recovery options.

---

### Post by Halibutt on 2011-12-07
> **kio_http said:**
> If you have a Windows 7 Retail disk, boot it and launch start up repair it recovery options.Did that, but no success either. The recovery disk sees my Windows @ drive C and does some magic, but when I restart I am back to square one, no changes. 

Any ideas? I usually solve most of my problems with Ubuntu by reinstalling, but reinstalling Windows is out of the question in this case and I would really, really like to avoid that...
Cheers

---

### Post by darkod on 2011-12-07
Run the boot info script from the link in my signature. It will show more details. Post the results included in code tags (the button # above).

---

### Post by Halibutt on 2011-12-07
> **darkod said:**
> Run the boot info script from the link in my signature. It will show more details. Post the results included in code tags (the button # above).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 9 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 214778552 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 205071486 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 205068540 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 38913, w sumie sektorów: 625142448
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda2         204,797,950   625,137,344   420,339,395   f W95 Extended (LBA)
/dev/sda5         255,722,731   625,137,344   369,414,614   7 NTFS / exFAT / HPFS
/dev/sda6         204,797,952   205,299,711       501,760  83 Linux
/dev/sda7         205,301,760   209,205,247     3,903,488  82 Linux swap / Solaris
/dev/sda8         228,739,072   255,721,471    26,982,400  83 Linux
/dev/sda9         209,207,296   220,348,415    11,141,120  83 Linux
/dev/sda10        220,350,464   228,732,927     8,382,464  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953525168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        06A02B74A02B68FF                       ntfs       
/dev/sda10       d433a374-d15b-4d74-995d-10afb9ee092e   swap       
/dev/sda5        C0682A67682A5D02                       ntfs       
/dev/sda6        44c7c16a-033b-4f15-991e-b81ad0a267e9   ext2       
/dev/sda7        f59a054e-d2e4-4fc6-8c24-ddaa8fd9b06e   swap       
/dev/sda8        562bb0c6-4298-4da6-b745-3f06ac3efb8c   ext4       
/dev/sda9        a16c7e61-37c4-4804-85b2-c3f5d553f9fc   ext4       
/dev/sdb1        A870F12D70F1033C                       ntfs       tera

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda6/grub/grub.cfg: ==============================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 1c99e419-2bff-48dd-9190-744ade09d21a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
  set locale_dir=($root)/grub/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	linux	/vmlinuz-3.0.0-14-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/vmlinuz-3.0.0-14-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	linux	/vmlinuz-3.0.0-12-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/vmlinuz-3.0.0-12-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	linux	/vmlinuz-2.6.38-11-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/vmlinuz-2.6.38-11-generic root=UUID=1c99e419-2bff-48dd-9190-744ade09d21a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 44c7c16a-033b-4f15-991e-b81ad0a267e9
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 06A02B74A02B68FF
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

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  97.785248756 = 104.996111360  grub/core.img                                  2
  97.780926704 = 104.991470592  grub/grub.cfg                                  2
  97.740103722 = 104.947637248  initrd.img-2.6.38-11-generic                  62
  97.685144424 = 104.888625152  initrd.img-3.0.0-12-generic                   58
  97.802756310 = 105.014909952  initrd.img-3.0.0-14-generic                   57
  97.728507996 = 104.935186432  vmlinuz-2.6.38-11-generic                     20
  97.668485641 = 104.870737920  vmlinuz-3.0.0-12-generic                      19
  97.705822945 = 104.910828544  vmlinuz-3.0.0-14-generic                      22

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
  set locale_dir=($root)/boot/grub/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=a16c7e61-37c4-4804-85b2-c3f5d553f9fc ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-13-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	echo	'Wczytywanie systemu Linux 3.0.0-13-generic...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=a16c7e61-37c4-4804-85b2-c3f5d553f9fc ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a16c7e61-37c4-4804-85b2-c3f5d553f9fc ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.0.0-12-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	echo	'Wczytywanie systemu Linux 3.0.0-12-generic...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a16c7e61-37c4-4804-85b2-c3f5d553f9fc ro recovery nomodeset 
	echo	'Wczytywanie pocz&#261;tkowego dysku RAM...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root a16c7e61-37c4-4804-85b2-c3f5d553f9fc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 06A02B74A02B68FF
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=a16c7e61-37c4-4804-85b2-c3f5d553f9fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=d433a374-d15b-4d74-995d-10afb9ee092e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.461429596 = 107.869638656  boot/grub/core.img                             1
 104.246574402 = 111.933906944  boot/grub/grub.cfg                             1
 103.012794495 = 110.609145856  boot/initrd.img-3.0.0-12-generic               2
 104.424049377 = 112.124469248  boot/initrd.img-3.0.0-13-generic               2
 102.414035797 = 109.966233600  boot/vmlinuz-3.0.0-12-generic                  1
 103.398872375 = 111.023693824  boot/vmlinuz-3.0.0-13-generic                  1
 104.424049377 = 112.124469248  initrd.img                                     2
 103.012794495 = 110.609145856  initrd.img.old                                 2
 103.398872375 = 111.023693824  vmlinuz                                        1
 102.414035797 = 109.966233600  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  0a 73 c7 23 72 ea 10 bd  4c 32 ad 56 b6 ff 00 ec  |.s.#r...L2.V....|
00000010  9c bd 9d 66 db 6e 21 d6  d2 2c d1 24 4e 6a 12 2a  |...f.n!..,.$Nj.*|
00000020  b7 5d b9 bc 84 c6 61 6a  4a 45 02 23 b4 b5 11 9d  |.]....ajJE.#....|
00000030  4b 8a 14 e1 81 8e 62 e2  00 43 23 1b 1b 49 27 72  |K.....b..C#..I'r|
00000040  6b db 3f 84 ab 96 e1 66  cd ba 7b 9d 2d b5 5f 2d  |k.?....f..{.-._-|
00000050  68 69 d6 18 71 1d 56 e3  06 dc 51 01 c3 a8 05 1d  |hi..q.V...Q.....|
00000060  0a a5 39 13 8e 91 ba 51  23 17 50 ae 06 e3 9d d8  |..9....Q#.P.....|
00000070  1e e1 14 79 9a 07 b4 4d  07 a7 a5 13 6f 2f 84 ce  |...y...M....o/..|
00000080  cd 0b 2c e8 db 7a 03 71  6f 12 1e f7 88 b7 17 01  |..,..z.qo.......|
00000090  71 49 78 83 5a 05 93 44  28 9c c0 e5 8b ac d2 1a  |qIx.Z..D(.......|
000000a0  ec 37 ae 7a e3 9f 24 63  c1 03 d4 de 37 95 bf 67  |.7.z..$c....7..g|
000000b0  36 ce ef ec de c2 77 65  5c ee 28 7c 41 b8 49 95  |6.....we\.(|A.I.|
000000c0  6a 31 96 b2 94 c7 79 41  c4 a1 5a 80 ce a4 e5 c3  |j1....yA..Z.....|
000000d0  1b 3a 3d 83 a3 65 1f 43  8a e5 39 b7 5b 8e f2 e4  |.:=..e.C..9.[...|
000000e0  4b 0e 66 e0 2b 5e 21 13  6e 9b a4 cd c9 b7 ad 2b  |K.f.+^!.n......+|
000000f0  6e 25 1c 32 a4 a9 2d b5  a9 ca a8 00 48 ce b4 26  |n%.2..-.....H..&|
00000100  a4 d3 c3 1b b0 30 31 ee  c7 70 5c fd c4 85 f1 b4  |.....01..p\.....|
00000110  53 79 fa 15 61 76 b9 40  e8 c9 6e e7 04 ba b4 3a  |Sy..av.@..n....:|
00000120  94 24 17 96 c3 80 1c 88  40 1c c1 15 ae 34 32 9c  |.$......@....42.|
00000130  28 51 d9 45 43 8e d5 0b  74 ba d9 e2 da 5b b7 5a  |(Q.EC...t....[.Z|
00000140  19 79 b2 fb c1 d7 4b ee  a5 c5 9a 24 80 91 a4 0c  |.y....K....$....|
00000150  b3 e2 70 05 ae 26 a5 6b  44 09 72 0d 94 d1 53 e1  |..p..&.kD.r...S.|
00000160  48 05 2b 3a 89 4f e0 a5  70 db 96 98 7e 09 87 dd  |H.+:.O..p...~...|
00000170  df be fa 7a be 5c 57 aa  b5 e6 9e c4 11 6a f7 b7  |...z.\W......j..|
00000180  a1 38 59 d2 5b 61 b5 38  a7 9d 50 42 12 07 22 b5  |.8Y.[a.8..PB..".|
00000190  10 2b e8 ad 71 e4 c2 00  bd b6 4d 49 e7 8a 86 b9  |.+..q.....MI....|
000001a0  6e 8b 6c 50 4b 9a a7 3e  4f d0 3a 1a 49 f4 9e 2a  |n.lPK..>O.:.I..*|
000001b0  1e aa 60 da 28 80 e6 72  8b 8f ba 67 4a 98 00 fe  |..`.(..r...gJ...|
000001c0  ff ff 07 fe ff ff ed 0c  09 03 d6 d1 04 16 00 fe  |................|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 a8 07 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error

```

Is it any different from the pastebin version I linked in my first post?
Cheers

---

### Post by darkod on 2011-12-07
Sorry, I didn't notice that link.
You have grub2 all around the place, on partitions /dev/sda1 and /dev/sda6. And just for the record, your ubuntu 11.10 is installed on /dev/sda9.

While /dev/sda6 is linux partition and it doesn't mind having grub2 installed onto the Partition Boot Record (PBR), you also have grub2 on the PBR of /dev/sda1 which is the win7 partition and it does mind having it there.
You also have some boot file in /dev/sda1 and my assumption is you earlier tried to somehow chainload grub2 to the windows bootloader.

Lesson for the future: Don't listen to various blogs and people telling you it's better to let windows bootloader chainload to grub2. There is nothing to be afraid of installing grub2 to your MBR. It makes things much simpler in the future, as you now witnessed. That's just my personal opinion. I have no intention making windows bootloader recognize an OS it can't by default. So I just use grub2. Also if you insist on chainlaoding, you have to be aware of that fact and when repairing grub2 in the future the standard commands would not apply to your system. 

From here onwards, two options:
1. You can continue trying to use windows bootloader on the MBR. In that case I can't help further, I am not familiar with the process.
2. You can remove grub2 from the PBR of /dev/sda1 and let grub2 which is already installed on your MBR run the show. I think as soon as you repair the /dev/sda1 PBR the computer will start booting because grub2 from the MBR is pointing to the right place. What you have in that place is messing things up.

You can use testdisk to remove grub2 from a PBR. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Basically I think you use the Backup BS command on /dev/sda1 to repair it to standard PBR. I had a link with more details if you need it, but it's in my home computer and can't post it until later.

---

### Post by kio_http on 2011-12-07
> **darkod said:**
> Sorry, I didn't notice that link.
You have grub2 all around the place, on partitions /dev/sda1 and /dev/sda6. And just for the record, your ubuntu 11.10 is installed on /dev/sda9.

While /dev/sda6 is linux partition and it doesn't mind having grub2 installed onto the Partition Boot Record (PBR), you also have grub2 on the PBR of /dev/sda1 which is the win7 partition and it does mind having it there.
You also have some boot file in /dev/sda1 and my assumption is you earlier tried to somehow chainload grub2 to the windows bootloader.

Lesson for the future: Don't listen to various blogs and people telling you it's better to let windows bootloader chainload to grub2. There is nothing to be afraid of installing grub2 to your MBR. It makes things much simpler in the future, as you now witnessed. That's just my personal opinion. I have no intention making windows bootloader recognize an OS it can't by default. So I just use grub2. Also if you insist on chainlaoding, you have to be aware of that fact and when repairing grub2 in the future the standard commands would not apply to your system. 

From here onwards, two options:
1. You can continue trying to use windows bootloader on the MBR. In that case I can't help further, I am not familiar with the process.
2. You can remove grub2 from the PBR of /dev/sda1 and let grub2 which is already installed on your MBR run the show. I think as soon as you repair the /dev/sda1 PBR the computer will start booting because grub2 from the MBR is pointing to the right place. What you have in that place is messing things up.

You can use testdisk to remove grub2 from a PBR. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Basically I think you use the Backup BS command on /dev/sda1 to repair it to standard PBR. I had a link with more details if you need it, but it's in my home computer and can't post it until later.

While I prefer having grub on mbr, sometimes you have to set the windows loader back to the mbr. E.g I was unable to install Vista SP1 with grub on mbr.

---

### Post by Halibutt on 2011-12-07
> **darkod said:**
> Lesson for the future: Don't listen to various blogs and people telling you it's better to let windows bootloader chainload to grub2. There is nothing to be afraid of installing grub2 to your MBR. It makes things much simpler in the future, as you now witnessed. That's just my personal opinion. I have no intention making windows bootloader recognize an OS it can't by default. So I just use grub2. Also if you insist on chainlaoding, you have to be aware of that fact and when repairing grub2 in the future the standard commands would not apply to your system. 
Well, AAMoF I had no idea what was going on, I didn't **try to** mess with Grub. All the problems stem from the fact that update to 11.10 failed. Then I tried to update from the cd (which also failed) and finally started ubuntu by installing it over the previous installation. Which most likely means that Grub was installed all over the place for no apparent reason. 

I'm a consumer, you know. Fairly advanced (I kind of understand your last post), but my sole intention is to have two working systems side by side, I don't need any optimisation or Windows loaders handling Ubuntu or whatnot. :)

> From here onwards, two options:
2. You can remove grub2 from the PBR of /dev/sda1 and let grub2 which is already installed on your MBR run the show. I think as soon as you repair the /dev/sda1 PBR the computer will start booting because grub2 from the MBR is pointing to the right place. What you have in that place is messing things up.

You can use testdisk to remove grub2 from a PBR. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Basically I think you use the Backup BS command on /dev/sda1 to repair it to standard PBR. I had a link with more details if you need it, but it's in my home computer and can't post it until later.Okay, I will try to fix this by using TestDisk after I get back from work, thanks for the suggestion, will let you know if it helped. 
Cheers

EDIT/ Any instructions on how to use this tool to achieve what you suggest will be highly appreciated.

---

### Post by darkod on 2011-12-07
:)
I didn't want to sound rude or blaming you. I was just covering all options in one post. I am aware lots of people are asking to keep windows bootloader literary saying they are afraid to put grub on the MBR. Personally I think they are asking for trouble especially if they don't have experience with that sort of thing. By having a non-standard setup you are much more open to some update messing something up, or some tool because the setup is not standard it would expect.

It's probably not your fault, I'm just stating that that grub2 had to be installed somehow. Maybe the Boot Repair process did that. Because even if you did select grub2 to be installed onto any partition, and not the MBR, it only installs one copy. Not 3.

Anyway, lets see how testdisk goes, and I will try to find that link later on.

---

### Post by Halibutt on 2011-12-07
I'm not defending myself either, just pointing out that you're talking to a complete moron who is happy he knows what Grub is at all and understands what you say but not necessarily knows how to get around. :)

Anyway, I ran the TestDisk 6.11 (installed from within Ubuntu, hence 6.11 and not 6.13) as root, but already have a problem. 

On the first screen it lists two disks and I obviously need to alter something in the first one 
```
Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 320 GB / 298 GiB - ATA WDC WD3200AAJS-0
Disk /dev/sdb - 1000 GB / 931 GiB - ATA ST31000528AS

[Proceed ]  [  Quit  ]

```

But then it asks me what partition table type I need to chose. Well, I have no idea and this sounds dangerous (considering I don't want to format the disk with all my data or anything). 

```
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

```

What exactly am I doing again? :)
Cheers

---

### Post by darkod on 2011-12-07
First option, Intel partition table.
You have screenshots from their website here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Be careful, the beginning of the procedure is to recover deleted partition, skip over that. In fact, the part interesting for you is almost at the end, the title that says NTFS Boot Sector Recovery.
After the first few screens to select the disk, the partition table, the partition, you can jump to the end as soon as you are into partition #1. And do the Backup BS command.

If it can't find valid backup to restore it from there, some people have reported success using the Rebuild BS command next to it. In theory it should build a new standard ntfs boot sector.

---

### Post by Halibutt on 2011-12-07
> **darkod said:**
> First option, Intel partition table.
You have screenshots from their website here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Be careful, the beginning of the procedure is to recover deleted partition, skip over that. In fact, the part interesting for you is almost at the end, the title that says NTFS Boot Sector Recovery.
After the first few screens to select the disk, the partition table, the partition, you can jump to the end as soon as you are into partition #1. And do the Backup BS command.

If it can't find valid backup to restore it from there, some people have reported success using the Rebuild BS command next to it. In theory it should build a new standard ntfs boot sector.Yeah, just found that how-to, following it now. (performing deeper search right now). Thanks. Will keep you posted, unless I fry my computer of course. 

EDIT/ Cancelled that, but apparently no BackupBS option there. Will perform a deeper search, perhaps the BackupBS will show up then,.

EDIT 2/ 67% and counting...
Cheers

---

### Post by oldfred on 2011-12-07
It may tell you that the boot sector is ok as grub in it is not wrong unless it is a NTFS partition. What is important is if the backup is valid and can be restored and is the Windows version.

If the backup is bad, you to have to rebuild the bootsector. That is often just a basic NTFS Boot sector and then the windows repair may work. Usually with grub in the PBR, Windows does not even correctly see & repair a NTFS partition.

---

### Post by Halibutt on 2011-12-07
Weird, it found all the linux partitions (apparently when installing Ubuntu over Ubuntu, the Ubuntu installer just creates three partitions out of the main one, rather than using the partitions that are already there. Anyway, it found all the partitions, but the option to backupBS is not there at all.

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 12747 254 63  204796557
D HPFS - NTFS          12748   1  1 38912 254 63  420340662
D Linux                12748  21  8 12779  80 35     501760
D Linux                12748  21 10 12779  80 37     501760
D Linux Swap           12779 113  7 13022 107 61    3903472
D Linux                13022 140 47 13716  13 57   11141120
D Linux                13306 180 59 14000  54  6   11141120
D Linux                13312 146 19 14006  19 29   11141120
D Linux                13312 178 51 14006  51 61   11141120
D Linux                13313 118 54 14006 247  1   11141120
D Linux                13313 248 56 14007 122  3   11141120
D Linux                13314 123 58 14007 252  5   11141120
D Linux Swap           13716  46 27 14237 246  9    8382448
D Linux                14238  88 59 15917 235 62   26982400
D Linux                15046  19 14 16725 166 17   26982400
D Linux                15047 121 51 16727  13 54   26982400
D Linux                15049 164 28 16729  56 31   26982400
D Linux                15050  39 30 16729 186 33   26982400
D Linux                15051 207  5 16731  99  8   26982400
D Linux                15052 179 40 16732  71 43   26982400
D Linux                15053  54 42 16732 201 45   26982400
D Linux                15053 184 44 16733  76 47   26982400
D HPFS - NTFS          15918   0 62 38912 254 63  369414614




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue


```

---

### Post by oldfred on 2011-12-07
That is to bring back deleted partitions. You want to be at this screen. since you have reformated many times you have many versions of partitions on drive.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by Halibutt on 2011-12-07
> **oldfred said:**
> You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

I know, I just don't know how to get to that screen...I keep trying though.

EDIT/ I found it!
It's called Boot in my version of the program, but the explanation is "Boot sector recovery". Apparently the step by step was made with a different version.
Cheers

---

### Post by darkod on 2011-12-07
> (apparently when installing Ubuntu over Ubuntu, the Ubuntu installer  just creates three partitions out of the main one, rather than using the  partitions that are already there.Actually this is what I love about linux. It never assumes you want to overwrite your partitions. Unless you literary tell it to use an existing one (manual partitioning during the install, now called Something Else in the latest 11.10), it will NEVER use existing partitions, never mind if it's windows or linux partition.

You seem to be on the way to repair the boot sector, hope it works.

---

### Post by Halibutt on 2011-12-07
Well, as long as both systems boot just fine I'm fine with it and don't plan to meddle with it any more. At least until I run out of space because Ubuntu decided to create a new swap and forget about the older one - or until another "update" comes out and forces me to reinstall... 

Thanks for your help, I wouldn't have made it without you. 
Cheers

---

