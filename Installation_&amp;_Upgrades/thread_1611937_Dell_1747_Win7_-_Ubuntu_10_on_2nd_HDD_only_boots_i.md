---
title: "Dell 1747 Win7 - Ubuntu 10 on 2nd HDD only boots into Win7 ?"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by beltonwith on 2010-11-02
[FONT=Arial]Been using Ubuntu on a Dell 6000 for some time and have just purchased a Dell 1747 with Win 7 on a 500gb SATA HDD. Installed a 2nd 120gb SATA hdd with Ubuntu 10 and changed Boot sequence in F12 to load Ubuntu..........

Problem is ....it always boots into Win 7 ???.. Can anyone Help ?.

Looked through all threads and google it but can't find a solution. Any help would be appreciated. Would like to keep separate HDD and load into OS via F12 boot sequence or if possible, on start up menu.

Attached Results.txt:[/FONT]```

```
  	 	 	 	p { margin-bottom: 0.21cm; }                 Boot Info Script 0.55    dated February 15th, 2010                     
 

 ============================= Boot Info Summary: ==============================  
 

  => Windows is installed in the MBR of /dev/sda  
  => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in  
     partition #2 for (,msdos2)/boot/grub.  
 

 sda1: _________________________________________________________________________ 
 

     File system:       vfat  
     Boot sector type:  Dell Utility: Fat16  
     Boot sector info:  According to the info in the boot sector, sda1 has  
                        4193697 sectors.. But according to the info from the  
                        partition table , it has 4208966 sectors.  
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
 

 sdb1: _________________________________________________________________________ 
 

     File system:       Extended Partition  
     Boot sector type:  -  
     Boot sector info:   
 

 sdb5: _________________________________________________________________________ 
 

     File system:       swap  
     Boot sector type:  -  
     Boot sector info:   
 

 sdb2: _________________________________________________________________________ 
 

     File system:       ext4  
     Boot sector type:  -  
     Boot sector info:   
     Operating System:  Ubuntu 10.10  
     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  
 

 =========================== Drive/Partition Info: =============================  
 

 Drive: sda ___________________ _____________________________________________________  
 

 Disk /dev/sda: 500.1 GB, 500107862016 bytes  
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 

 Partition  Boot         Start           End          Size  Id System  
 

 /dev/sda1                  63     4,209,029     4,208,967  de Dell Utility  
 /dev/sda2    *      4,210,688    21,860,351    17,649,664   7 HPFS/NTFS  
 /dev/sda3          21,860,352   976,771,071   954,910,720   7 HPFS/NTFS  
 

 

 Drive: sdb ___________________ _____________________________________________________  
 

 Disk /dev/sdb: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 

 Partition  Boot         Start           End          Size  Id System  
 

 /dev/sdb1               2,046    11,798,527    11,796,482   5 Extended  
 /dev/sdb5               2,048    11,798,527    11,796,480  82 Linux swap / Solaris  
 /dev/sdb2    *     11,798,528   312,580,095   300,781,568  83 Linux  
 

 

 blkid -c /dev/null: ____________________________________________________________  
 

 Device           UUID                                   TYPE       LABEL                          
 

 /dev/loop0                                              squashfs                                  
 /dev/sda1        3030-3030                              vfat       DellUtility                    
 /dev/sda2        423A2F143A2F048F                       ntfs       RECOVERY                       
 /dev/sda3        9AF833E0F833B8F9                       ntfs       OS                             
 /dev/sda: PTTYPE="dos" 
 /dev/sdb1: PTTYPE="dos" 
 /dev/sdb2        3ac60636-9831-465b-bc08-58e4a998d869   ext4                                      
 /dev/sdb5        c8ebd77e-9426-422e-a6df-6d8d55b3e48c   swap                                      
 /dev/sdb: PTTYPE="dos" 
 

 ============================ "mount | grep ^/dev  output: ===========================  
   
 Device           Mount_Point              Type       Options  
 

 aufs             /                        aufs       (rw)  
 /dev/sr0         /cdrom                   iso9660    (ro,noatime)  
 /dev/loop0       /rofs                    squashfs   (ro,noatime)  
 /dev/sr0         /media/apt               iso9660    (ro)  
 

 

 =========================== sdb2/boot/grub/grub.cfg: ===========================  
 

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
 set root='(hd1,msdos2)' 
 search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
 if loadfont /usr/share/grub/unicode.pf2 ; then  
   set gfxmode=640x480  
   load_video  
   insmod gfxterm  
 fi  
 terminal_output gfxterm 
 insmod part_msdos  
 insmod ext2  
 set root='(hd1,msdos2)' 
 search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
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
 menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {  
 	recordfail  
 	insmod part_msdos  
 	insmod ext2  
 	set root='(hd1,msdos2)'  
 	search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
 	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=3ac60636-9831-465b-bc08-58e4a998d869 ro   quiet splash  
 	initrd	/boot/initrd.img-2.6.35-22-generic-pae 
 }  
 menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {  
 	recordfail  
 	insmod part_msdos  
 	insmod ext2  
 	set root='(hd1,msdos2)'  
 	search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
 	echo	'Loading Linux 2.6.35-22-generic-pae ...'  
 	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=3ac60636-9831-465b-bc08-58e4a998d869 ro single  
 	echo	'Loading initial ramdisk ...'  
 	initrd	/boot/initrd.img-2.6.35-22-generic-pae 
 }  
 ### END /etc/grub.d/10_linux ###  
 

 ### BEGIN /etc/grub.d/20_linux_xen ###  
 ### END /etc/grub.d/20_linux_xen ###  
 

 ### BEGIN /etc/grub.d/20_memtest86+ ###  
 menuentry "Memory test (memtest86+)" {  
 	insmod part_msdos  
 	insmod ext2  
 	set root='(hd1,msdos2)'  
 	search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
 	linux16	/boot/memtest86+.bin 
 }  
 menuentry "Memory test (memtest86+, serial console 115200)" {  
 	insmod part_msdos  
 	insmod ext2  
 	set root='(hd1,msdos2)'  
 	search --no-floppy --fs-uuid --set 3ac60636-9831-465b-bc08-58e4a998d869  
 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8  
 }  
 ### END /etc/grub.d/20_memtest86+ ###  
 

 ### BEGIN /etc/grub.d/30_os-prober ###  
 menuentry "Windows 7 (loader) (on /dev/sda2)" {  
 	insmod part_msdos  
 	insmod ntfs  
 	set root='(hd0,msdos2)'  
 	search --no-floppy --fs-uuid --set 423a2f143a2f048f  
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
 

 =============================== sdb2/etc/fstab: ===============================  
 

 # /etc/fstab: static file system information.  
 #  
 # Use 'blkid -o value -s UUID' to print the universally unique identifier  
 # for a device; this may be used with UUID= as a more robust way to name  
 # devices that works even if disks are added and removed. See fstab(5).  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    nodev,noexec,nosuid 0       0  
 # / was on /dev/sdb2 during installation  
 UUID=3ac60636-9831-465b-bc08-58e4a998d869 /               ext4    errors=remount-ro 0       1  
 # swap was on /dev/sdb5 during installation  
 UUID=c8ebd77e-9426-422e-a6df-6d8d55b3e48c none            swap    sw              0       0  
 

 =================== sdb2: Location of files loaded by Grub: ===================  
 

 

   74.9GB: boot/grub/core.img  
   79.2GB: boot/grub/grub.cfg  
    6.9GB: boot/initrd.img-2.6.35-22-generic-pae  
   74.8GB: boot/vmlinuz-2.6.35-22-generic-pae  
    6.9GB: initrd.img  
   74.8GB: vmlinuz
 

Hope this loads Ok.

---

