---
title: "HELP Installing Solaris deleted ubuntu boot loader"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by drdigital on 2011-01-10
Hello Every one,
I have a serious problem , pls help me to overcome.

I had a good working installation of Ubuntu 10.10 after I installed Sun SOlaris 11 Express, I lost the boot options for Ubuntu and I can not boot it.

After some trials, I reached the mnu.lst file and I can edit it , I can now see the Boot splash screen menu of solaris 11 showing 

Solaris 11 Express 
Windows
Windows

and when I click one of these windows I got error and CTRL+ALT+DEL to restart.

Can any one help me in this ??

Thanks

---

### Post by ajgreeny on 2011-01-10
It sounds as if you need to reinstall grub to the MBR of the machine using a live Ubuntu CD
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The one thing I don't know anything about is solaris and which bootloader that uses, but if it already uses grub2 you may be able to run the equivalent of sudo update-grub from solaris to get ubuntu added to the solaris grub menu.

I am also assuming that if you restore grub2 to the MBR it will find and be able to boot solaris even when using ubuntu as the source of grub.

You could run the boot-info-script from my signature which will no doubt assist other people who understand solaris and how it boots to help you more.

EDIT:
A quick search shows that solaris uses grub2 so my first suggestion of running update-grub may be all you need.  Do a search of solaris commands and you may solve all your problems.

---

### Post by drdigital on 2011-01-10
I made the first step, it returned back but I lost Solaris :D

I made sudo -update from ubuntu , solaris did not appear.

by the way solaris does not use grub 2 !!

---

### Post by kansasnoob on 2011-01-10
We really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by drdigital on 2011-01-10
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 58605170 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1    *             63    58,605,119    58,605,057  83 Linux
/dev/sda2          58,605,120   159,734,294   101,129,175  bf Solaris
/dev/sda3         159,741,950   610,299,903   450,557,954   5 Extended
/dev/sda5         159,741,952   262,141,951   102,400,000  83 Linux
/dev/sda6         262,144,000   405,503,999   143,360,000   7 HPFS/NTFS
/dev/sda7         405,506,048   528,386,047   122,880,000   7 HPFS/NTFS
/dev/sda8         528,388,096   566,886,399    38,498,304  83 Linux
/dev/sda9         566,888,448   610,299,903    43,411,456  83 Linux
/dev/sda4         610,299,904   625,141,759    14,841,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10                                              zfs                                      
/dev/sda1        893cfc85-f296-47e7-929a-ce25900ae05f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda4        276e362a-7aa9-4033-8b9e-336df713ae66   swap                                     
/dev/sda5        58b5bdf8-0d18-462e-a9c5-718c012819b2   ext4       UbuntuPart                    
/dev/sda6        1C99DE8B011A0F40                       ntfs       Common                        
/dev/sda7        6AF988BA3E2B0671                       ntfs       WindowsPart                   
/dev/sda8        56836023-0b58-4db1-9f3d-1799b1719778   ext2       TPD                           
/dev/sda9        cbbd41c0-4cf1-41d2-a142-a28e03a72857   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Common            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/UbuntuPart        ext4       (rw,commit=0)
/dev/sda7        /media/WindowsPart       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/TPD               ext2       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=893cfc85-f296-47e7-929a-ce25900ae05f /               ext4    errors=remount-ro 0       1
UUID=276e362a-7aa9-4033-8b9e-336df713ae66 none            swap    sw              0       0

/dev/sda6 /media/Common ntfs defaults 0 0
/dev/sda5 /media/UbuntuPart ext4 defaults 0 0
/dev/sda7 /media/WindowsPart ntfs defaults 0 0
/dev/sda8 /media/TPD ext2 defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  21.6GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
   1.2GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old

```

---

### Post by drdigital on 2011-01-10
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 58605170 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1    *             63    58,605,119    58,605,057  83 Linux
/dev/sda2          58,605,120   159,734,294   101,129,175  bf Solaris
/dev/sda3         159,741,950   610,299,903   450,557,954   5 Extended
/dev/sda5         159,741,952   262,141,951   102,400,000  83 Linux
/dev/sda6         262,144,000   405,503,999   143,360,000   7 HPFS/NTFS
/dev/sda7         405,506,048   528,386,047   122,880,000   7 HPFS/NTFS
/dev/sda8         528,388,096   566,886,399    38,498,304  83 Linux
/dev/sda9         566,888,448   610,299,903    43,411,456  83 Linux
/dev/sda4         610,299,904   625,141,759    14,841,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10                                              zfs                                      
/dev/sda1        893cfc85-f296-47e7-929a-ce25900ae05f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda4        276e362a-7aa9-4033-8b9e-336df713ae66   swap                                     
/dev/sda5        58b5bdf8-0d18-462e-a9c5-718c012819b2   ext4       UbuntuPart                    
/dev/sda6        1C99DE8B011A0F40                       ntfs       Common                        
/dev/sda7        6AF988BA3E2B0671                       ntfs       WindowsPart                   
/dev/sda8        56836023-0b58-4db1-9f3d-1799b1719778   ext2       TPD                           
/dev/sda9        cbbd41c0-4cf1-41d2-a142-a28e03a72857   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Common            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/UbuntuPart        ext4       (rw,commit=0)
/dev/sda7        /media/WindowsPart       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/TPD               ext2       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=893cfc85-f296-47e7-929a-ce25900ae05f /               ext4    errors=remount-ro 0       1
UUID=276e362a-7aa9-4033-8b9e-336df713ae66 none            swap    sw              0       0

/dev/sda6 /media/Common ntfs defaults 0 0
/dev/sda5 /media/UbuntuPart ext4 defaults 0 0
/dev/sda7 /media/WindowsPart ntfs defaults 0 0
/dev/sda8 /media/TPD ext2 defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  21.6GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
   1.2GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old

```

---

### Post by drdigital on 2011-01-10
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 58605170 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1    *             63    58,605,119    58,605,057  83 Linux
/dev/sda2          58,605,120   159,734,294   101,129,175  bf Solaris
/dev/sda3         159,741,950   610,299,903   450,557,954   5 Extended
/dev/sda5         159,741,952   262,141,951   102,400,000  83 Linux
/dev/sda6         262,144,000   405,503,999   143,360,000   7 HPFS/NTFS
/dev/sda7         405,506,048   528,386,047   122,880,000   7 HPFS/NTFS
/dev/sda8         528,388,096   566,886,399    38,498,304  83 Linux
/dev/sda9         566,888,448   610,299,903    43,411,456  83 Linux
/dev/sda4         610,299,904   625,141,759    14,841,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10                                              zfs                                      
/dev/sda1        893cfc85-f296-47e7-929a-ce25900ae05f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda4        276e362a-7aa9-4033-8b9e-336df713ae66   swap                                     
/dev/sda5        58b5bdf8-0d18-462e-a9c5-718c012819b2   ext4       UbuntuPart                    
/dev/sda6        1C99DE8B011A0F40                       ntfs       Common                        
/dev/sda7        6AF988BA3E2B0671                       ntfs       WindowsPart                   
/dev/sda8        56836023-0b58-4db1-9f3d-1799b1719778   ext2       TPD                           
/dev/sda9        cbbd41c0-4cf1-41d2-a142-a28e03a72857   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Common            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/UbuntuPart        ext4       (rw,commit=0)
/dev/sda7        /media/WindowsPart       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/TPD               ext2       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=893cfc85-f296-47e7-929a-ce25900ae05f /               ext4    errors=remount-ro 0       1
UUID=276e362a-7aa9-4033-8b9e-336df713ae66 none            swap    sw              0       0

/dev/sda6 /media/Common ntfs defaults 0 0
/dev/sda5 /media/UbuntuPart ext4 defaults 0 0
/dev/sda7 /media/WindowsPart ntfs defaults 0 0
/dev/sda8 /media/TPD ext2 defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  21.6GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
   1.2GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old

```

---

### Post by drdigital on 2011-01-10
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 58605170 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1    *             63    58,605,119    58,605,057  83 Linux
/dev/sda2          58,605,120   159,734,294   101,129,175  bf Solaris
/dev/sda3         159,741,950   610,299,903   450,557,954   5 Extended
/dev/sda5         159,741,952   262,141,951   102,400,000  83 Linux
/dev/sda6         262,144,000   405,503,999   143,360,000   7 HPFS/NTFS
/dev/sda7         405,506,048   528,386,047   122,880,000   7 HPFS/NTFS
/dev/sda8         528,388,096   566,886,399    38,498,304  83 Linux
/dev/sda9         566,888,448   610,299,903    43,411,456  83 Linux
/dev/sda4         610,299,904   625,141,759    14,841,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10                                              zfs                                      
/dev/sda1        893cfc85-f296-47e7-929a-ce25900ae05f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda4        276e362a-7aa9-4033-8b9e-336df713ae66   swap                                     
/dev/sda5        58b5bdf8-0d18-462e-a9c5-718c012819b2   ext4       UbuntuPart                    
/dev/sda6        1C99DE8B011A0F40                       ntfs       Common                        
/dev/sda7        6AF988BA3E2B0671                       ntfs       WindowsPart                   
/dev/sda8        56836023-0b58-4db1-9f3d-1799b1719778   ext2       TPD                           
/dev/sda9        cbbd41c0-4cf1-41d2-a142-a28e03a72857   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Common            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/UbuntuPart        ext4       (rw,commit=0)
/dev/sda7        /media/WindowsPart       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/TPD               ext2       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=893cfc85-f296-47e7-929a-ce25900ae05f ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 893cfc85-f296-47e7-929a-ce25900ae05f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=893cfc85-f296-47e7-929a-ce25900ae05f /               ext4    errors=remount-ro 0       1
UUID=276e362a-7aa9-4033-8b9e-336df713ae66 none            swap    sw              0       0

/dev/sda6 /media/Common ntfs defaults 0 0
/dev/sda5 /media/UbuntuPart ext4 defaults 0 0
/dev/sda7 /media/WindowsPart ntfs defaults 0 0
/dev/sda8 /media/TPD ext2 defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-24-generic
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  21.6GB: boot/vmlinuz-2.6.35-24-generic
    .8GB: initrd.img
   1.2GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old

```

---

### Post by drdigital on 2011-01-10
Sorry for all those duplications, I did not mean it.

---

### Post by drdigital on 2011-01-11
can some one help me before i format ?

---

### Post by kansasnoob on 2011-01-11
> **drdigital said:**
> can some one help me before i format ?

Just now looking. Snow had it's way with me.

I'm going to have to do some testing myself because of this:

> sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 58605170 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

Basically it's time for me to give do a "test-drive" but this will undoubtedly take quite a while.

---

### Post by kansasnoob on 2011-01-11
I'm downloading 'sol-11-exp-201011-live-x86.iso' now, sheesh - what a complicated registration process :(

Anyway, assuming you're still booting Ubuntu with grub2, try this first (please copy-n-paste commands and post the full terminal output here regardless of outcome):

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo apt-get install --reinstall os-prober
```

```
sudo os-prober
```

```
sudo update-grub
```

If Solaris is found great :)

If not I'll be having a closer look at the Solaris file structure but if this is correct:

[http://docs.sun.com/app/docs/doc/820-7799/grubmultiboot?a=view](http://docs.sun.com/app/docs/doc/820-7799/grubmultiboot?a=view)

You may be able to help by poking around using Nautilus and trying to find the Solaris menu.lst. If you find it please copy-n-paste the full text here. DO NOT edit that menu.lst!

NOTE: Due to snow I may be out for quite some time! Please be patient :)

---

### Post by kansasnoob on 2011-01-12
Just in case others hit this thread during a search I'll report my own results.

Installing Solaris was a real challenge. It took forever to figure out that I needed to turn off the hyper-thread option in BIOS before I could install.

That was the tough one but many more problems dogged me! Long story made short:

Ubuntu's grub2 does find Solaris' grub and make it boot if Ubuntu is installed last!

And the commands I provided earlier do work!

Oh, and why would anyone want to run Solaris? SO MANY COMPLICATIONS!

Don't ask for details! I like Ubuntu and Debian. I will not waste any time trying to explain why, it's just my preference!

---

### Post by foxmulder881 on 2011-01-12
> **kansasnoob said:**
> I'm downloading 'sol-11-exp-201011-live-x86.iso' now, sheesh - what a complicated registration process :(


That's what I thought too, but I refused to register and sourced it from the torrent networks instead. ;-)

---

### Post by kansasnoob on 2011-01-13
> **foxmulder881 said:**
> That's what I thought too, but I refused to register and sourced it from the torrent networks instead. ;-)

The installation was a nightmare! After spinning it up in VirtualBox everything I'd try resulted in an I/O error.

Trying a "hard install" I'd get no keyboard input with either a USB or PS/2 keyboard. I finally figured out that I needed to turn off the hyperthreading in my BIOS.

Like the newest Solaris is equal to Dapper :(

But I'm biased! IMHO if it's not Debian based I don't like it :D

---

### Post by foxmulder881 on 2011-01-13
Yeah I didn't really try running it in a VB session, but rather just run the LiveCD.

Personally, I reckon they've got a lot of work to do to grab a more  mainstream user-base. But then again, perhaps that's not what they're trying to do.

---

### Post by foxmulder881 on 2011-01-13
For those who want an easier download solution, here's the torrent file.

[http://ul.to/9b7dgz](http://ul.to/9b7dgz)

---

### Post by kholis on 2011-01-28
hi, i have same problem as you too. solaris 11 express grub installation simply override my ubuntu grub. and only detect ms windows partition. but not ubuntu partition. because of that i can't boot to ubuntu anymore.

according to [http://blogs.sun.com/tonyb/entry/dual_boot_soalris_and_ubuntu](http://blogs.sun.com/tonyb/entry/dual_boot_soalris_and_ubuntu). you have to reinstall ubuntu grub with ubuntu live CD. "update-grub" command will not automatically add "Solaris" entry in grub, because ubuntu dont know ZFS filesystem used in Solaris. You must add the following line manually entry in /boot/grub/grub.cfg

```
menuentry "Solaris 11 Express" {
        set root='(hd0,msdos9)'
        chainloader +1
        makeactive
        boot
}

```  

be sure to add write permission to grub.cfg. change hd0 to your HD and msdos9 to partition on where solaris installed. use "fdisk -l" to know your partition number.

if you select "Solaris 11 Express" while booting, it will load original solaris grub.

it works in my laptop. you can see my grub.cfg in [https://gist.github.com/799979/5822f7c6dbf461dfbde376f11d319317a1165055](https://gist.github.com/799979/5822f7c6dbf461dfbde376f11d319317a1165055)

---

### Post by mayotte on 2011-06-19
[QUOTE=kholis;10404979] 
```
menuentry "Solaris 11 Express" {
        set root='(hd0,msdos9)'
        chainloader +1
        makeactive
        boot
}

```  That didn't work for me. I banged on it until I got the following to work: 
```
menuentry "Solaris 11 Express" {
        set root='(hd0,7)'
        chainloader +1
        boot
}

``` makeactive was apparently replaced by parttool in grub2, but I couldn't figure it out. Omitting it still seems to work. And the msdos thing threw an unknown disk error at me. 
So now I have a triple boot: Win7, Ubuntu 11.04, and Solaris 11. WooHoo!

---

