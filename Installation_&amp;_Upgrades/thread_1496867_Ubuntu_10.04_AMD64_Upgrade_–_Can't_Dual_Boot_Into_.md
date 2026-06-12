---
title: "Ubuntu 10.04 AMD64 Upgrade – Can't Dual Boot Into Windows Vista"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by KNC on 2010-05-29
Hello,
 

 I have a dual hard-drive system with Windows Vista on the first hard drive and Ubuntu on the second.   There was a clean install of Ubuntu 9.10 AMD64 on the second hard drive for a number of months and dual-booting worked just fine.  Yesterday I did an upgrade of Ubuntu to 10.04 AMD64 and now the system can not boot into Vista.  Boot into Ubuntu works fine.
 

 It is possible to mount and access the first hard drive from within Ubuntu so data loss is not an issue.
 

 Here is the symptom scenario:
 

 Power-on and grub menu displays.  Scroll down to the selection for Windows Vista, hit <Enter> and the screen goes black with the cursor blinking in the top left corner.  No hard drive activity at all.  I have left the system in that state for 5 minutes to remove any impatience on my part from influencing the observations.
 

 Below is the output of boot_info_script*.sh
 

 

 

 

                 [FONT=Courier New, monospace][SIZE=2]Boot Info Script 0.55    dated February 15th, 2010                    [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]============================= Boot Info Summary: ============================== [/SIZE][/FONT] 
 

  [FONT=Courier New, monospace][SIZE=2]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in[/SIZE][/FONT]
     [FONT=Courier New, monospace][SIZE=2]partition #1 for /boot/grub. [/SIZE][/FONT] 
  [FONT=Courier New, monospace][SIZE=2]=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]partition #1 for /boot/grub. [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sda1: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=Courier New, monospace][SIZE=2]File system:       ntfs [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector type:  Grub 2 [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector info:  Grub 2 is installed in the boot sector of sda1 and [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]looks at sector 275031 of the same hard drive for [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]core.img, but core.img can not be found at this [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]location. No errors found in the Boot Parameter Block. [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Operating System:  Windows Vista [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sda3: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=Courier New, monospace][SIZE=2]File system:       ntfs [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector type:  Grub 2 [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector info:  Grub 2 is installed in the boot sector of sda3 and [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]looks at sector 275031 of the same hard drive for [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]core.img, but core.img can not be found at this [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]location. No errors found in the Boot Parameter Block. [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Operating System:  [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot files/dirs:   /bootmgr /boot/bcd [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sdb1: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=Courier New, monospace][SIZE=2]File system:       ext4 [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector type:  Grub 2 [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]looks at sector 275031 of the same hard drive for [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]core.img, but core.img can not be found at this [/SIZE][/FONT] 
                        [FONT=Courier New, monospace][SIZE=2]location. [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Operating System:  Ubuntu 10.04 LTS [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sdb2: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=Courier New, monospace][SIZE=2]File system:       Extended Partition [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector info:  [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sdb5: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=Courier New, monospace][SIZE=2]File system:       swap [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]Boot sector info:  [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]=========================== Drive/Partition Info: ============================= [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Drive: sda ___________________ _____________________________________________________ [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Disk /dev/sda: 750.2 GB, 750156374016 bytes [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]Units = sectors of 1 * 512 = 512 bytes [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Partition  Boot         Start           End          Size  Id System [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]/dev/sda1    *             63 1,439,150,894 1,439,150,832   7 HPFS/NTFS [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sda3       1,439,150,895 1,465,144,064    25,993,170   7 HPFS/NTFS [/SIZE][/FONT] 
 

 

 [FONT=Courier New, monospace][SIZE=2]Drive: sdb ___________________ _____________________________________________________ [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]Units = sectors of 1 * 512 = 512 bytes [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Partition  Boot         Start           End          Size  Id System [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]/dev/sdb1                  63 1,905,501,779 1,905,501,717  83 Linux [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb2       1,905,501,780 1,953,520,064    48,018,285   5 Extended [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb5       1,905,501,843 1,953,520,064    48,018,222  82 Linux swap / Solaris [/SIZE][/FONT] 
 

 

 [FONT=Courier New, monospace][SIZE=2]blkid -c /dev/null: ____________________________________________________________ [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Device           UUID                                   TYPE       LABEL                         [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]/dev/sda1        327CAEDC7CAE9A5D                       ntfs       HP                            [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sda: PTTYPE="dos" [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb1        300287b9-0224-4c97-85d2-f4e509527005   ext4                                     [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb2: PTTYPE="dos" [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb5        b1527b9e-073b-42fd-841c-95b91fb7d085   swap                                     [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/sdb: PTTYPE="dos" [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]error: /dev/sdc: No medium found [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]error: /dev/sdd: No medium found [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]error: /dev/sde: No medium found [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]error: /dev/sdf: No medium found [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]============================ "mount | grep ^/dev  output: =========================== [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]Device           Mount_Point              Type       Options [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]/dev/sdb1        /                        ext4       (rw,errors=remount-ro) [/SIZE][/FONT] 
 

 

 [FONT=Courier New, monospace][SIZE=2]=========================== sdb1/boot/grub/grub.cfg: =========================== [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]# [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# DO NOT EDIT THIS FILE [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# It is automatically generated by /usr/sbin/grub-mkconfig using templates [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# from /etc/grub.d and settings from /etc/default/grub [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/00_header ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]if [ -s $prefix/grubenv ]; then [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]load_env [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set default="0" [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]if [ ${prev_saved_entry} ]; then [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set saved_entry=${prev_saved_entry} [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]save_env saved_entry [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set prev_saved_entry= [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]save_env prev_saved_entry [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set boot_once=true [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]function savedefault { [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]if [ -z ${boot_once} ]; then [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]saved_entry=${chosen} [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]save_env saved_entry [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]function recordfail { [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set recordfail=1 [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]if loadfont /usr/share/grub/unicode.pf2 ; then [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set gfxmode=640x480 [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]insmod gfxterm [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]insmod vbe [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]if terminal_output gfxterm ; then true ; else [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]# For backward compatibility with versions of terminal.mod that don't [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]# understand terminal_output [/SIZE][/FONT] 
     [FONT=Courier New, monospace][SIZE=2]terminal gfxterm [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set locale_dir=($root)/boot/grub/locale [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set lang=en [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]insmod gettext [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]if [ ${recordfail} = 1 ]; then [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set timeout=-1 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]else [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set timeout=10 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/00_header ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/05_debian_theme ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]insmod tga [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set color_normal=black/black [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set color_highlight=magenta/black [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]else [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set menu_color_normal=white/black [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]set menu_color_highlight=magenta/black [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]fi [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/05_debian_theme ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/10_linux ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	recordfail [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=300287b9-0224-4c97-85d2-f4e509527005 ro   quiet splash [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	initrd	/boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	recordfail [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	echo	'Loading Linux 2.6.32-22-generic ...' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=300287b9-0224-4c97-85d2-f4e509527005 ro single [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	echo	'Loading initial ramdisk ...' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	initrd	/boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	recordfail [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=300287b9-0224-4c97-85d2-f4e509527005 ro   quiet splash [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	initrd	/boot/initrd.img-2.6.31-21-generic [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	recordfail [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	echo	'Loading Linux 2.6.31-21-generic ...' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=300287b9-0224-4c97-85d2-f4e509527005 ro single [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	echo	'Loading initial ramdisk ...' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	initrd	/boot/initrd.img-2.6.31-21-generic [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/10_linux ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/20_memtest86+ ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry "Memory test (memtest86+)" { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux16	/boot/memtest86+.bin [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry "Memory test (memtest86+, serial console 115200)" { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ext2 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd1,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 300287b9-0224-4c97-85d2-f4e509527005 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/20_memtest86+ ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/30_os-prober ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry "Windows Vista (loader) (on /dev/sda1)" { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ntfs [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd0,1)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 327caedc7cae9a5d [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	chainloader +1 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]menuentry "Windows Vista (loader) (on /dev/sda3)" { [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	insmod ntfs [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	search --no-floppy --fs-uuid --set 949ca48c9ca46a86 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	chainloader +1 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]} [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/30_os-prober ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]### BEGIN /etc/grub.d/40_custom ### [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# This file provides an easy way to add custom menu entries.  Simply type the [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# menu entries you want to add after this comment.  Be careful not to change [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# the 'exec tail' line above. [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]### END /etc/grub.d/40_custom ### [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]=============================== sdb1/etc/fstab: =============================== [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]# /etc/fstab: static file system information. [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# Use 'blkid -o value -s UUID' to print the universally unique identifier [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# for a device; this may be used with UUID= as a more robust way to name [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# devices that works even if disks are added and removed. See fstab(5). [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# <file system> <mount point>   <type>  <options>       <dump>  <pass> [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]proc            /proc           proc    defaults        0       0 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# / was on /dev/sdb1 during installation [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]UUID=300287b9-0224-4c97-85d2-f4e509527005 /               ext4    errors=remount-ro 0       1 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]# swap was on /dev/sdb5 during installation [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]UUID=b1527b9e-073b-42fd-841c-95b91fb7d085 none            swap    sw              0       0 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]=================== sdb1: Location of files loaded by Grub: =================== [/SIZE][/FONT] 
 

 

     [FONT=Courier New, monospace][SIZE=2].1GB: boot/grub/core.img [/SIZE][/FONT] 
    [FONT=Courier New, monospace][SIZE=2]2.4GB: boot/grub/grub.cfg [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]12.9GB: boot/initrd.img-2.6.31-21-generic [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]12.9GB: boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
    [FONT=Courier New, monospace][SIZE=2]2.2GB: boot/vmlinuz-2.6.31-21-generic [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]13.6GB: boot/vmlinuz-2.6.32-22-generic [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]12.9GB: initrd.img [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]12.9GB: initrd.img.old [/SIZE][/FONT] 
   [FONT=Courier New, monospace][SIZE=2]13.6GB: vmlinuz [/SIZE][/FONT] 
    [FONT=Courier New, monospace][SIZE=2]2.2GB: vmlinuz.old [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]=======Devices which don't seem to have a corresponding hard drive============== [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]sdc sdd sde sdf [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]=============================== StdErr Messages: =============================== [/SIZE][/FONT] 
 

 [FONT=Courier New, monospace][SIZE=2]umount: /tmp/BootInfo0/sda1: device is busy. [/SIZE][/FONT] 
         [FONT=Courier New, monospace][SIZE=2](In some cases useful info about processes that use [/SIZE][/FONT] 
          [FONT=Courier New, monospace][SIZE=2]the device is found by lsof(8) or fuser(1))[/SIZE][/FONT]
 

 Any help beyond this point is appreciated.
 

 [SIZE=3]Thanks[/SIZE]

---

### Post by drs305 on 2010-05-29
You have grub installed on the Windows partition (sda1). Normally grub should be installed on the drive but not on a specific partition (and certainly not on the Windows partition).

Take a look at this link for the likely solution:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

Note: Grub2 will boot faster if you go into BIOS and select sdb as the drive your system boots first (with G2 installed on sdb).

---

### Post by darkod on 2010-05-29
sda1:  __________________________________________________   _______________________  
 

     File system:        ntfs  
     Boot sector  type:  Grub 2  
     Boot sector  info: [COLOR=Red] Grub 2 is installed in the boot sector of sda1[/COLOR] and   
                        looks at sector 275031 of the same hard drive for   
                        core.img, but core.img can not be found at this  
                        location. No errors found in the Boot Parameter Block.   
     Operating  System:  Windows Vista  
     Boot files/dirs:    /bootmgr /Boot/BCD /Windows/System32/winload.exe

You have installed grub2 to the vista partition. Use these instructions to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to apply the fix on partition #1 on disk /dev/sda.

That should sort it out.

You have the same on /dev/sda3 which looks like your restore partition, so if you want to access it from the grub2 menu, you need to do the same for /dev/sda3 too.

---

### Post by Norwal on 2010-05-29
I hope this help. I had the same issue after I decided to upgrade to Win7.  I did a complete install of Win7 followed by a new install of Ubuntu 9.10 64 bit(separate drives). All was fine until I did a update on Ubuntu. After much searching on the forums, I discovered that Grub2 doesn't play nice in the park anymore and the upgrade I did included Grub2. 

[http://ubuntuforums.org/showthread.php?t=1328983](http://ubuntuforums.org/showthread.php?t=1328983)

To fix this annoying little step backwards by Grub, you can follow all the complex fixes on the forums or do what I did.  I reformatted my Ubuntu drive and start over.  This time I tried 10.04. I did all the updates, minus the Grub2 "upgrade" and everything still works.  :P

---

### Post by KNC on 2010-05-29
Thank you folks. The website that drs305 directed me to had the answer.  I had a slightly different third screen come up, but it worked!

Thanks!

---

### Post by darkod on 2010-05-29
> **Norwal said:**
> I hope this help. I had the same issue after I decided to upgrade to Win7.  I did a complete install of Win7 followed by a new install of Ubuntu 9.10 64 bit(separate drives). All was fine until I did a update on Ubuntu. After much searching on the forums, I discovered that Grub2 doesn't play nice in the park anymore and the upgrade I did included Grub2. 

[http://ubuntuforums.org/showthread.php?t=1328983](http://ubuntuforums.org/showthread.php?t=1328983)

To fix this annoying little step backwards by Grub, you can follow all the complex fixes on the forums or do what I did.  I reformatted my Ubuntu drive and start over.  This time I tried 10.04. I did all the updates, minus the Grub2 "upgrade" and everything still works.  :P

Please don't confuse the OP. This has nothing to do with grub2 directly.

It has to do with installing grub2 onto the windows partition. And even if ubuntu is reinstalled now, grub2 will still remain on the windows partition and grub1 nor grub2 can boot windows in that situation.

When asked by the upgrade process where to install grub2, the OP checked all partitions. You can see it on all partitions in the results file.

Only disk(s) need to be selected, not partitions, when asked where you want grub2 by the upgrade process.

---

### Post by darkod on 2010-05-29
> **KNC said:**
> Thank you folks. The website that drs305 directed me to had the answer.  I had a slightly different third screen come up, but it worked!

Thanks!

Great. :) Good job.

---

### Post by Norwal on 2010-05-29
> **darkod said:**
> When asked by the upgrade process where to install grub2, the OP checked all partitions. You can see it on all partitions in the results file.

Only disk(s) need to be selected, not partitions, when asked where you want grub2 by the upgrade process.

Thanks for the reply darkod.  I guess I don't understand the process well enough. When I did the update that last time, I used Synaptic and don't recall being prompted. I guess now that all other updates are completed, I could try again. The worse thing that could happen is another reinstall. :)

The point I was making was this; If you don't update to Grub2, then the dual boot still works from a clean install. ie: if it ain't broke don't fix it.  But then again where is the fun and learning in that?

Cheers

---

### Post by darkod on 2010-05-30
> **Norwal said:**
> 

The point I was making was this; If you don't update to Grub2, then the dual boot still works from a clean install.


I'm not sure I can follow you on this. A clean install, according to me at least, is when you install ubuntu without previously having one, or over your existing install formatting the old root partition, which wipes everything from it.

Either way, if you don't install grub2 (the bootloader) during the clean install, what are you going to boot ubuntu with?

This can only work if you also have another linux distro with its grub/grub2 already installed, and want to use that one to boot your new ubuntu.

Otherwise, for a windows/ubuntu dual boot, not installing a bootloader during clean install will definitely not make it work, because the grub2 that remains on the MBR will have his files wiped from the old root partition by the clean install. That is a very good recipe how to break your dual boot.

---

### Post by s2f on 2010-06-26
> **drs305 said:**
> You have grub installed on the Windows partition (sda1). Normally grub should be installed on the drive but not on a specific partition (and certainly not on the Windows partition).

Take a look at this link for the likely solution:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Note: Grub2 will boot faster if you go into BIOS and select sdb as the drive your system boots first (with G2 installed on sdb).

wow this saved me from going completely grey haired. everything was working fine until i upgraded to lucid lynx. thanks a lot to you and the original poster

---

### Post by darkod on 2010-06-27
> **s2f said:**
> wow this saved me from going completely grey haired. everything was working fine until i upgraded to lucid lynx. thanks a lot to you and the original poster

Just a quick reminder, everything was working fine until you selected to install grub2 on the windows partition. This "problem" has nothing to do with the upgrade itself. As long as you don't install grub2 on the windows partition, it will be fine.
You made it sound like the upgrade itself will make windows unbootable.

---

