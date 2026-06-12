---
title: "Minor Inconvenience in GRUB 2"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by creative4reel on 2010-05-20
Sorry if I don't do this well, but it is my first time posting this sort of stuff on a forum. New to Ubuntu & Linux. The last Ubuntu 10.04 64-bit update left double posts in GRUB 2 menu.  What do I do to remove duplicate?[IMG]http://hotimg23.fotki.com/a/72_220/253_6/DSC01442-vi869.jpg[/IMG]

Here's Boot Info Script Results:
```
                                                  [FONT=FreeMono, monospace][SIZE=1]Boot Info Script 0.55    dated February 15th, 2010                    [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]============================= Boot Info Summary: ============================== [/SIZE][/FONT] 
 

  [FONT=FreeMono, monospace][SIZE=1]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]partition #3 for /boot/grub. [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda1: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       ntfs [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  Windows Vista/7 [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  No errors found in the Boot Parameter Block. [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Operating System:  Windows XP [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda2: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       ntfs [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  Windows Vista/7 [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  No errors found in the Boot Parameter Block. [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Operating System:  Windows 7 [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot files/dirs:   /Windows/System32/winload.exe [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda3: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       ext3 [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Operating System:  Ubuntu 10.04 LTS [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda4: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       Extended Partition [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda5: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       swap [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]sda6: _________________________________________________________________________ [/SIZE][/FONT] 
 

     [FONT=FreeMono, monospace][SIZE=1]File system:       ext3 [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector type:  - [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot sector info:  [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Operating System:  [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]Boot files/dirs:   [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]=========================== Drive/Partition Info: ============================= [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]Drive: sda ___________________ _____________________________________________________ [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]Disk /dev/sda: 500.1 GB, 500107862016 bytes [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]Units = sectors of 1 * 512 = 512 bytes [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]Partition  Boot         Start           End          Size  Id System [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda2          40,966,144   208,738,303   167,772,160   7 HPFS/NTFS [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda3         208,738,304   218,738,687    10,000,384  83 Linux [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda4         218,740,734   269,676,543    50,935,810   5 Extended [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda5         218,740,736   230,809,599    12,068,864  82 Linux swap / Solaris [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda6         230,811,648   269,676,543    38,864,896  83 Linux [/SIZE][/FONT] 
 

 

 [FONT=FreeMono, monospace][SIZE=1]blkid -c /dev/null: ____________________________________________________________ [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]Device           UUID                                   TYPE       LABEL                         [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]/dev/sda1        AED07BB7D07B847D                       ntfs                                     [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda2        1C901CD1901CB2EE                       ntfs                                     [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda3        a5f4e57e-1bad-4b65-9ab5-0ffd030ef089   ext3                                     [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda4: PTTYPE="dos" [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda5        6c712ca4-f57a-4282-9ebc-9b04070fec97   swap                                     [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda6        311d727a-e251-4b78-9203-6d8353cf4655   ext3                                     [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda: PTTYPE="dos" [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]============================ "mount | grep ^/dev  output: =========================== [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]Device           Mount_Point              Type       Options [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]/dev/sda3        /                        ext3       (rw,errors=remount-ro) [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/sda6        /home                    ext3       (rw) [/SIZE][/FONT] 
 

 

 [FONT=FreeMono, monospace][SIZE=1]================================ sda1/boot.ini: ================================ [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]; [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1];Warning: Boot.ini is used on Windows XP and earlier operating systems. [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1];Warning: Use BCDEDIT.exe to modify Windows Vista boot options. [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]; [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1][boot loader] [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]timeout=30 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1][operating systems] [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]=========================== sda3/boot/grub/grub.cfg: =========================== [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]# [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# DO NOT EDIT THIS FILE [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# It is automatically generated by /usr/sbin/grub-mkconfig using templates [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# from /etc/grub.d and settings from /etc/default/grub [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/00_header ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]if [ -s $prefix/grubenv ]; then [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]load_env [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set default="0" [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]if [ ${prev_saved_entry} ]; then [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set saved_entry=${prev_saved_entry} [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]save_env saved_entry [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set prev_saved_entry= [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]save_env prev_saved_entry [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set boot_once=true [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]function savedefault { [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]if [ -z ${boot_once} ]; then [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]saved_entry=${chosen} [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]save_env saved_entry [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]function recordfail { [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set recordfail=1 [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]if loadfont /usr/share/grub/unicode.pf2 ; then [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set gfxmode=640x480 [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]insmod gfxterm [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]insmod vbe [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]if terminal_output gfxterm ; then true ; else [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]# For backward compatibility with versions of terminal.mod that don't [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]# understand terminal_output [/SIZE][/FONT] 
     [FONT=FreeMono, monospace][SIZE=1]terminal gfxterm [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set locale_dir=($root)/boot/grub/locale [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set lang=en [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]insmod gettext [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]if [ ${recordfail} = 1 ]; then [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set timeout=-1 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]else [/SIZE][/FONT] 
   [FONT=FreeMono, monospace][SIZE=1]set timeout=10 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]fi [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/00_header ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/05_debian_theme ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set menu_color_normal=white/black [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]set menu_color_highlight=black/light-gray [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/05_debian_theme ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/10_linux ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    recordfail [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 ro   quiet splash [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    initrd    /boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    recordfail [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    echo    'Loading Linux 2.6.32-22-generic ...' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 ro single [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    echo    'Loading initial ramdisk ...' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    initrd    /boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    recordfail [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 ro   quiet splash [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    initrd    /boot/initrd.img-2.6.32-21-generic [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    recordfail [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    echo    'Loading Linux 2.6.32-21-generic ...' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 ro single [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    echo    'Loading initial ramdisk ...' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    initrd    /boot/initrd.img-2.6.32-21-generic [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/10_linux ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/20_memtest86+ ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry "Memory test (memtest86+)" { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux16    /boot/memtest86+.bin [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry "Memory test (memtest86+, serial console 115200)" { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ext2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,3)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    linux16    /boot/memtest86+.bin console=ttyS0,115200n8 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/20_memtest86+ ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/30_os-prober ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]menuentry "Windows 7 (loader) (on /dev/sda1)" { [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    insmod ntfs [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    set root='(hd0,1)' [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    search --no-floppy --fs-uuid --set aed07bb7d07b847d [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]    chainloader +1 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]} [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/30_os-prober ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]### BEGIN /etc/grub.d/40_custom ### [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# This file provides an easy way to add custom menu entries.  Simply type the [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# menu entries you want to add after this comment.  Be careful not to change [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# the 'exec tail' line above. [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]### END /etc/grub.d/40_custom ### [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]=============================== sda3/etc/fstab: =============================== [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]# /etc/fstab: static file system information. [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# Use 'blkid -o value -s UUID' to print the universally unique identifier [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# for a device; this may be used with UUID= as a more robust way to name [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# devices that works even if disks are added and removed. See fstab(5). [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# <file system> <mount point>   <type>  <options>       <dump>  <pass> [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]proc            /proc           proc    nodev,noexec,nosuid 0       0 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# / was on /dev/sda3 during installation [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]UUID=a5f4e57e-1bad-4b65-9ab5-0ffd030ef089 /               ext3    errors=remount-ro 0       1 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# /home was on /dev/sda6 during installation [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]UUID=311d727a-e251-4b78-9203-6d8353cf4655 /home           ext3    defaults        0       2 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]# swap was on /dev/sda5 during installation [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]UUID=6c712ca4-f57a-4282-9ebc-9b04070fec97 none            swap    sw              0       0 [/SIZE][/FONT] 
 [FONT=FreeMono, monospace][SIZE=1]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 [/SIZE][/FONT] 
 

 [FONT=FreeMono, monospace][SIZE=1]=================== sda3: Location of files loaded by Grub: =================== [/SIZE][/FONT] 
 

 

  [FONT=FreeMono, monospace][SIZE=1]110.1GB: boot/grub/core.img [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.1GB: boot/grub/grub.cfg [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.2GB: boot/initrd.img-2.6.32-21-generic [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.4GB: boot/initrd.img-2.6.32-22-generic [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.1GB: boot/vmlinuz-2.6.32-21-generic [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.1GB: boot/vmlinuz-2.6.32-22-generic [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.4GB: initrd.img [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.2GB: initrd.img.old [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.1GB: vmlinuz [/SIZE][/FONT] 
  [FONT=FreeMono, monospace][SIZE=1]110.1GB: vmlinuz.old[/SIZE][/FONT]
 
```

---

### Post by darkod on 2010-05-20
There are no double entries. You have two kernels, 2.6.32-22 and 2.6.32-21 and both have a normal mode and recovery mode entry.

Keeping the recovery mode entry is recommended because it allows to boot sometimes if the normal mode can't, so you can repair things.

Also, keeping at least one older kernel, except the latest one, is recommended because after an update installs a new kernel it can sometimes make issues. Then you can just boot the older kernel.

So, you can remove the 2.6.32-21 but there is no need.

The only thing you might do is disable the memory test from showing up, because you won't be testing the memory on every boot. :)

If you want to do this, boot ubuntu and just disable the execute bit from the memtest file with:

sudo chmod -x /etc/grub.d/20_memtest86+

After that update grub.cfg with:

sudo update-grub

That should remove both memtest entries. You can always bring them back by running the first command again with +x instead of the -x, and running update-grub again.

---

### Post by uRock on 2010-05-20
You can easily remove the older kernel option by going to System> Administration> Synaptic Package Manager and clicking Installed in the left column, then entering 2.6.32-21 in the search field. Select each entry for the -21 kernel and select "Mark for Complete Removal." Once you click for the action to complete you will no longer have multiple kernel entries in the grub menu.

---

### Post by creative4reel on 2010-05-21
I'll remove MemTest86+ from menu and leave old kernel.  I also like knowing how to remove it, if I want to, in the future.  Thanks for speedy replies.  I'm amazed that the install and experience are going so well.

---

### Post by kansasnoob on 2010-05-21
> **uRock said:**
> You can easily remove the older kernel option by going to System> Administration> Synaptic Package Manager and clicking Installed in the left column, then entering 2.6.32-21 in the search field. Select each entry for the -21 kernel and select "Mark for Complete Removal." Once you click for the action to complete you will no longer have multiple kernel entries in the grub menu.

Must run "sudo update-grub" afterward :)

---

### Post by uRock on 2010-05-21
> **kansasnoob said:**
> Must run "sudo update-grub" afterward :)

The uninstall process runs grub.cfg, but it doesn't hurt to double check.

---

