---
title: "Lucid Lynx 10.04 Dual Boot, Lost Windows Vista"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by pgs3223 on 2010-06-23
I have a Dell Inspiron that came delivered with an 80GB hard disk running Windows Vista.
 

 I had been dual booting with Ubuntu successfully until I upgraded to 10.04 Lucid Lynx.
 

 On upgrading, when I rebooted the machine I saw an option to boot into Linux (Ubuntu) BUT NOT  Windows Vista as expected.
 

 When I chose Linux the computer boot to Linux as expected.
 

 But no option to boot into Windows Vista!
 

 I suspect this is a GRUB problem.
 

 Can anybody tell me how to edit the Grub menu so that I can boot into Vista as well please?
 

 Below is a summary of the disc partitions
 

 			Label			Size		Used		Unused	Flags
 /dev/sda1	fat16	Dell Utility		86.26 MB	7.06MB	79.20MB
 /dev/sda2	ntfs	Recovery		10GB		3.22GB	6.78GB
 /dev/sda3	ntfs	OS			46,27GB					Boot
 /dev/sda4	extended
 /dev/sda6	ext4				15.45GB	14.01GB	1.44GB	“Ubuntu”
 

 And a copy of the boot script
 

                 Boot Info Script 0.55    dated February 15th, 2010                     
 

 ============================= Boot Info Summary: =========================
 

  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  
 

     partition #6 for /boot/grub.
 

 

 

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
 

     Boot files/dirs:    
 

 

 

 sda3: _________________________________________________________________________
 

 

 

     File system:       ntfs
 

     Boot sector type:  Windows Vista/7
 

     Boot sector info:  No errors found in the Boot Parameter Block.
 

     Operating System:  Windows Vista
 

     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
 

 

 

 sda4: _________________________________________________________________________
 

 

 

     File system:       Extended Partition
 

     Boot sector type:  -
 

     Boot sector info:   
 

 

 

 sda5: _________________________________________________________________________
 

 

 

     File system:       vfat
 

     Boot sector type:  Vista: Fat 32
 

     Boot sector info:  No errors found in the Boot Parameter Block.
 

     Operating System:  Windows XP
 

     Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM
 

 

 

 sda6: _________________________________________________________________________
 

 

 

     File system:       ext4
 

     Boot sector type:  -
 

     Boot sector info:   
 

     Operating System:  Ubuntu 10.04 LTS
 

     Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab  
 

                        /boot/grub/core.img
 

 

 

 sda7: _________________________________________________________________________
 

 

 

     File system:       swap
 

     Boot sector type:  -
 

     Boot sector info:   
 

 

 

 =========================== Drive/Partition Info: =============================
 

 

 

 Drive: sda ___________________ _____________________________________________________
 

 

 

 Disk /dev/sda: 80.0 GB, 80026361856 bytes
 

 255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
 

 Units = sectors of 1 * 512 = 512 bytes
 

 Sector size (logical/physical): 512 bytes / 512 bytes
 

 

 

 Partition  Boot         Start           End          Size  Id System
 

 

 

 /dev/sda1                  63       176,714       176,652  de Dell Utility
 

 /dev/sda2             178,176    21,149,695    20,971,520   7 HPFS/NTFS
 

 /dev/sda3    *     21,149,696   118,180,063    97,030,368   7 HPFS/NTFS
 

 /dev/sda4         118,190,266   156,299,263    38,108,998   f W95 Ext d (LBA)
 

 /dev/sda5         152,107,008   156,299,263     4,192,256  dd Dell Media Direct
 

 /dev/sda6         118,190,268   150,593,309    32,403,042  83 Linux
 

 /dev/sda7         150,593,373   152,103,419     1,510,047  82 Linux swap / Solaris
 

 

 

 

 

 blkid -c /dev/null: ____________________________________________________________
 

 

 

 Device           UUID                                   TYPE       LABEL                          
 

 

 

 /dev/sda1        07D7-031B                              vfat       DellUtility                    
 

 /dev/sda2        6AE687FFE687CA31                       ntfs       RECOVERY                       
 

 /dev/sda3        50EA8B50EA8B3170                       ntfs       OS                             
 

 /dev/sda4: PTTYPE="dos"  
 

 /dev/sda5        1C8F-AF23                              vfat       MEDIADIRECT                    
 

 /dev/sda6        ffb33961-3fdd-4ee4-b36a-e3933a8758df   ext4                                      
 

 /dev/sda7        2a7b911f-ab7c-4a27-81cf-39c3dc67a59f   swap                                      
 

 /dev/sda: PTTYPE="dos"  
 

 

 

 ============================ "mount | grep ^/dev  output: ===========================
 

 

 

 Device           Mount_Point              Type       Options
 

 

 

 /dev/sda6        /                        ext4       (rw,errors=remount-ro)
 

 

 

 

 

 ================================ sda5/boot.ini: ================================
 

 

 

 [boot loader]
 

 timeout=0
 

 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 

 [operating systems]
 

 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
 

 

 

 ============================= sda6/grub/grub.cfg: =============================
 

 

 

 #
 

 # DO NOT EDIT THIS FILE
 

 #
 

 # It is automatically generated by /usr/sbin/grub-mkconfig using templates
 

 # from /etc/grub.d and settings from /etc/default/grub
 

 #
 

 

 

 ### BEGIN /etc/grub.d/00_header ###
 

 if [ -s $prefix/grubenv ]; then
 

   load_env
 

 fi
 

 set default="0"
 

 if [ ${prev_saved_entry} ]; then
 

   set saved_entry=${prev_saved_entry}
 

   save_env saved_entry
 

   set prev_saved_entry=
 

   save_env prev_saved_entry
 

   set boot_once=true
 

 fi
 

 

 

 function savedefault {
 

   if [ -z ${boot_once} ]; then
 

     saved_entry=${chosen}
 

     save_env saved_entry
 

   fi
 

 }
 

 

 

 function recordfail {
 

   set recordfail=1
 

   if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
 

 }
 

 if [ ${recordfail} = 1 ]; then
 

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
 

 ### END /etc/grub.d/10_linux ###
 

 

 

 ### BEGIN /etc/grub.d/20_memtest86+ ###
 

 ### END /etc/grub.d/20_memtest86+ ###
 

 

 

 ### BEGIN /etc/grub.d/30_os-prober ###
 

 ### END /etc/grub.d/30_os-prober ###
 

 

 

 ### BEGIN /etc/grub.d/40_custom ###
 

 # This file provides an easy way to add custom menu entries.  Simply type the
 

 # menu entries you want to add after this comment.  Be careful not to change
 

 # the 'exec tail' line above.
 

 ### END /etc/grub.d/40_custom ###
 

 

 

 =========================== sda6/boot/grub/grub.cfg: ===========================
 

 

 

 #
 

 # DO NOT EDIT THIS FILE
 

 #
 

 # It is automatically generated by /usr/sbin/grub-mkconfig using templates
 

 # from /etc/grub.d and settings from /etc/default/grub
 

 #
 

 

 

 ### BEGIN /etc/grub.d/00_header ###
 

 if [ -s $prefix/grubenv ]; then
 

   load_env
 

 fi
 

 set default="0"
 

 if [ ${prev_saved_entry} ]; then
 

   set saved_entry=${prev_saved_entry}
 

   save_env saved_entry
 

   set prev_saved_entry=
 

   save_env prev_saved_entry
 

   set boot_once=true
 

 fi
 

 

 

 function savedefault {
 

   if [ -z ${boot_once} ]; then
 

     saved_entry=${chosen}
 

     save_env saved_entry
 

   fi
 

 }
 

 

 

 function recordfail {
 

   set recordfail=1
 

   if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
 

 }
 

 insmod ext2
 

 set root='(hd0,6)'
 

 search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 if loadfont /usr/share/grub/unicode.pf2 ; then
 

   set gfxmode=640x480
 

   insmod gfxterm
 

   insmod vbe
 

   if terminal_output gfxterm ; then true ; else
 

     # For backward compatibility with versions of terminal.mod that don't
 

     # understand terminal_output
 

     terminal gfxterm
 

   fi
 

 fi
 

 insmod ext2
 

 set root='(hd0,6)'
 

 search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 set locale_dir=($root)/boot/grub/locale
 

 set lang=en
 

 insmod gettext
 

 if [ ${recordfail} = 1 ]; then
 

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
 

 menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.32-21-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.32-21-generic ...'
 

 	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.32-21-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-20-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-20-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-20-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-19-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-19-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-19-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-17-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-17-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-17-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-16-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-16-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-16-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-15-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-15-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-15-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro   quiet splash
 

 	initrd	/boot/initrd.img-2.6.31-14-generic
 

 }
 

 menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 

 	recordfail
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	echo	'Loading Linux 2.6.31-14-generic ...'
 

 	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df ro single  
 

 	echo	'Loading initial ramdisk ...'
 

 	initrd	/boot/initrd.img-2.6.31-14-generic
 

 }
 

 ### END /etc/grub.d/10_linux ###
 

 

 

 ### BEGIN /etc/grub.d/20_memtest86+ ###
 

 menuentry "Memory test (memtest86+)" {
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux16	/boot/memtest86+.bin
 

 }
 

 menuentry "Memory test (memtest86+, serial console 115200)" {
 

 	insmod ext2
 

 	set root='(hd0,6)'
 

 	search --no-floppy --fs-uuid --set ffb33961-3fdd-4ee4-b36a-e3933a8758df
 

 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
 

 }
 

 ### END /etc/grub.d/20_memtest86+ ###
 

 

 

 ### BEGIN /etc/grub.d/30_os-prober ###
 

 menuentry "Dell Utility Partition (on /dev/sda1)" {
 

 	insmod fat
 

 	set root='(hd0,1)'
 

 	search --no-floppy --fs-uuid --set 07d7-031b
 

 	drivemap -s (hd0) ${root}
 

 	chainloader +1
 

 }
 

 menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
 

 	insmod ntfs
 

 	set root='(hd0,3)'
 

 	search --no-floppy --fs-uuid --set 50ea8b50ea8b3170
 

 	drivemap -s (hd0) ${root}
 

 	chainloader +1
 

 }
 

 menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
 

 	insmod fat
 

 	set root='(hd0,5)'
 

 	search --no-floppy --fs-uuid --set 1c8f-af23
 

 	drivemap -s (hd0) ${root}
 

 	chainloader +1
 

 }
 

 ### END /etc/grub.d/30_os-prober ###
 

 

 

 ### BEGIN /etc/grub.d/40_custom ###
 

 # This file provides an easy way to add custom menu entries.  Simply type the
 

 # menu entries you want to add after this comment.  Be careful not to change
 

 # the 'exec tail' line above.
 

 ### END /etc/grub.d/40_custom ###
 

 

 

 =============================== sda6/etc/fstab: ===============================
 

 

 

 # /etc/fstab: static file system information.
 

 #
 

 # Use 'blkid -o value -s UUID' to print the universally unique identifier
 

 # for a device; this may be used with UUID= as a more robust way to name
 

 # devices that works even if disks are added and removed. See fstab(5).
 

 #
 

 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 

 proc            /proc           proc    defaults        0       0
 

 # / was on /dev/sda6 during installation
 

 UUID=ffb33961-3fdd-4ee4-b36a-e3933a8758df /               ext4    errors=remount-ro 0       1
 

 # swap was on /dev/sda7 during installation
 

 UUID=2a7b911f-ab7c-4a27-81cf-39c3dc67a59f none            swap    sw              0       0
 

 

 

 =================== sda6: Location of files loaded by Grub: ===================
 

 

 

 

 

   60.9GB: boot/grub/core.img
 

   63.7GB: boot/grub/grub.cfg
 

   70.7GB: boot/initrd.img-2.6.31-14-generic
 

   70.9GB: boot/initrd.img-2.6.31-15-generic
 

   62.7GB: boot/initrd.img-2.6.31-16-generic
 

   70.1GB: boot/initrd.img-2.6.31-17-generic
 

   73.1GB: boot/initrd.img-2.6.31-19-generic
 

   64.8GB: boot/initrd.img-2.6.31-20-generic
 

   61.0GB: boot/initrd.img-2.6.32-21-generic
 

   62.6GB: boot/vmlinuz-2.6.31-14-generic
 

   71.5GB: boot/vmlinuz-2.6.31-15-generic
 

   68.7GB: boot/vmlinuz-2.6.31-16-generic
 

   61.2GB: boot/vmlinuz-2.6.31-17-generic
 

   73.1GB: boot/vmlinuz-2.6.31-19-generic
 

   66.9GB: boot/vmlinuz-2.6.31-20-generic
 

   65.9GB: boot/vmlinuz-2.6.32-21-generic
 

   76.7GB: grub/grub.cfg
 

   61.0GB: initrd.img
 

   64.8GB: initrd.img.old
 

   65.9GB: vmlinuz
 

   66.9GB: vmlinuz.old

---

### Post by darkod on 2010-06-23
It's just a confusion by the type of boot files detected by grub2. I don't know why, but it happens sometimes.

Your Vista is on /dev/sda3 so that's it, even if the grub menu is calling it Recovery Environment.

If you select that it should boot your vista.

---

### Post by pgs3223 on 2010-06-23
Brilliant, problem solved, thank you very much!

PS Do you have any further thoughts or suggestions on my "other" GRUB problem

[http://ubuntuforums.org/showthread.php?p=9490199](http://ubuntuforums.org/showthread.php?p=9490199)

Getting desperate with this one:confused:

---

