---
title: "Windows wont boot.. :("
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by francobrotto on 2012-05-19
Hello everyone!
I'm new here and new to Ubuntu.
 

 I'm here to ask for your help to solve this apparently small issue that is taking me a lot of time. Basically what happens is that Windows wont boot. And nothing that I tried so far got me any step closer to fixing this issue... I'll give you all the details you need
 

 Im using a Dell Studio 1555 Intel Core 2 Duo T6400 @ 2.00ghz and I had (have, actually) Windows 7 64bits installed. The other day I wanted to try Linux so I downloaded and installed in a different partition Debian. Alright, no problems so far.  
 

 The problem started when I tried to uninstall Debian. I didnt know how to do it so I followed a tutorial that told me to use EasyBCD to repair GRUB/MBR (not sure what needed to be fixed) and restart. When I restarted Windows didnt load and this message was showing up:
 

 "Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert the Windows installation disk and restart your computer.
2. Choose your language settings, and click 'Next'
3. Click 'Repair your computer'
 

 I looked over dozens of pages to solve this issue, I burnt a Disc Repair, a Installation Disc, set the boot order to boot from CD/DVD, but nothing happened. I gave up this option and tried another one, using Ubuntu from a Pen Drive (LiveCD) running Boot-Repair. Didnt work too, I was able to restore the GRUB and boot Debian (that I didnt have time to delete) but when I chose Windows, same problem as I mentioned. Tried rewriting windows MBR and nothing!!!
 

 I already got my documents but I also wanted to get my emails from Outlook, and I think the only way to do it is using Windows...
 Also, I want Windows back because I need it to use Adobe's Programs...
 

 Can anyone help me on this? Below I'll post the results I've got from Boot-Repair..
 

 Big thanks,
 

 francobrotto
 
```

 ---------------------------BOOT-REPAIR RESULTS-----------------------------
 

                 Boot Info Script 0.61-git      [12 April 2012] 
  
  
 ============================= Boot Info Summary: =============================== 
  
  => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda. 
  => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb. 
  
 sda1: __________________________________________________________________________ 
  
     File system:       vfat 
     Boot sector type:  Dell Utility: FAT16 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM 
  
 sda2: __________________________________________________________________________ 
  
     File system:       ntfs 
     Boot sector type:  Windows Vista/7: NTFS 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:  Windows Vista 
     Boot files:        /bootmgr /BOOT/BCD /Windows/System32/winload.exe 
  
 sda3: __________________________________________________________________________ 
  
     File system:       ntfs 
     Boot sector type:  Windows Vista/7: NTFS 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:  Windows 7 
     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
  
 sda4: __________________________________________________________________________ 
  
     File system:       Extended Partition 
     Boot sector type:  Unknown 
     Boot sector info:  
  
 sda5: __________________________________________________________________________ 
  
     File system:       ext3 
     Boot sector type:  - 
     Boot sector info:  
     Operating System:  Debian GNU/Linux 6.0 
     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
  
 sda6: __________________________________________________________________________ 
  
     File system:       swap 
     Boot sector type:  - 
     Boot sector info:  
  
 sdb1: __________________________________________________________________________ 
  
     File system:       vfat 
     Boot sector type:  SYSLINUX 4.04 2011-04-18 
     Boot sector info:  Syslinux looks at sector 2961800 of /dev/sdb1 for its  
                        second stage. SYSLINUX is installed in the  directory.  
                        No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files:        /syslinux/syslinux.cfg /ldlinux.sys 
  
 ============================ Drive/Partition Info: ============================= 
  
 Drive: sda _____________________________________________________________________ 
  
 Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
  
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
  
 /dev/sda1                  63        80,324        80,262  de Dell Utility 
 /dev/sda2              80,325    30,800,324    30,720,000   7 NTFS / exFAT / HPFS 
 /dev/sda3    *     30,800,325   858,431,535   827,631,211   7 NTFS / exFAT / HPFS 
 /dev/sda4         858,433,534   976,771,071   118,337,538   5 Extended 
 /dev/sda5         858,433,536   971,880,447   113,446,912  83 Linux 
 /dev/sda6         971,882,496   976,771,071     4,888,576  82 Linux swap / Solaris 
  
  
 Drive: sdb _____________________________________________________________________ 
  
 Disk /dev/sdb: 2034 MB, 2034237440 bytes 
 23 heads, 55 sectors/track, 3140 cylinders, total 3973120 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
  
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System 
  
 /dev/sdb1    *         40,480     3,973,119     3,932,640   b W95 FAT32 
  
  
 "blkid" output: ________________________________________________________________ 
  
 Device           UUID                                   TYPE       LABEL 
  
 /dev/loop0                                              squashfs    
 /dev/loop1       53938097-35f7-424f-8e1c-f946b706de98   ext2        
 /dev/sda1        3030-3030                              vfat       DellUtility 
 /dev/sda2        58B27D48B27D2C1E                       ntfs       RECOVERY 
 /dev/sda3        30667F93667F5914                       ntfs       Windows 
 /dev/sda5        a875526f-e580-4982-9a4d-82aecab45cfd   ext3        
 /dev/sda6        196236eb-8744-45d1-9a4d-133b81baaf26   swap        
 /dev/sdb1        74CE-9447                              vfat       AMO VOCE S2 
  
 ================================ Mount points: ================================= 
  
 Device           Mount_Point              Type       Options 
  
 /dev/loop0       /rofs                    squashfs   (ro,noatime) 
 /dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) 
  
  
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
  
 function load_video { 
   insmod vbe 
   insmod vga 
   insmod video_bochs 
   insmod video_cirrus 
 } 
  
 insmod part_msdos 
 insmod ext2 
 set root='(hd0,msdos5)' 
 search --no-floppy --fs-uuid --set a875526f-e580-4982-9a4d-82aecab45cfd 
 if loadfont /usr/share/grub/unicode.pf2 ; then 
   set gfxmode=640x480 
   load_video 
   insmod gfxterm 
 fi 
 terminal_output gfxterm 
 insmod part_msdos 
 insmod ext2 
 set root='(hd0,msdos5)' 
 search --no-floppy --fs-uuid --set a875526f-e580-4982-9a4d-82aecab45cfd 
 set locale_dir=($root)/boot/grub/locale 
 set lang=en 
 insmod gettext 
 set timeout=10 
 ### END /etc/grub.d/00_header ### 
  
 ### BEGIN /etc/grub.d/05_debian_theme ### 
 insmod part_msdos 
 insmod ext2 
 set root='(hd0,msdos5)' 
 search --no-floppy --fs-uuid --set a875526f-e580-4982-9a4d-82aecab45cfd 
 insmod png 
 if background_image /usr/share/images/desktop-base/spacefun-grub.png; then 
   set color_normal=light-gray/black 
   set color_highlight=white/black 
 else 
   set menu_color_normal=cyan/blue 
   set menu_color_highlight=white/blue 
 fi 
 ### END /etc/grub.d/05_debian_theme ### 
  
 ### BEGIN /etc/grub.d/10_linux ### 
 menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os { 
     insmod part_msdos 
     insmod ext2 
     set root='(hd0,msdos5)' 
     search --no-floppy --fs-uuid --set a875526f-e580-4982-9a4d-82aecab45cfd 
     echo    'Loading Linux 2.6.32-5-686 ...' 
     linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=a875526f-e580-4982-9a4d-82aecab45cfd ro  quiet 
     echo    'Loading initial ramdisk ...' 
     initrd    /boot/initrd.img-2.6.32-5-686 
 } 
 menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os { 
     insmod part_msdos 
     insmod ext2 
     set root='(hd0,msdos5)' 
     search --no-floppy --fs-uuid --set a875526f-e580-4982-9a4d-82aecab45cfd 
     echo    'Loading Linux 2.6.32-5-686 ...' 
     linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=a875526f-e580-4982-9a4d-82aecab45cfd ro single  
     echo    'Loading initial ramdisk ...' 
     initrd    /boot/initrd.img-2.6.32-5-686 
 } 
 ### END /etc/grub.d/10_linux ### 
  
 ### BEGIN /etc/grub.d/20_linux_xen ### 
 ### END /etc/grub.d/20_linux_xen ### 
  
 ### BEGIN /etc/grub.d/30_os-prober ### 
 ### END /etc/grub.d/30_os-prober ### 
  
 ### BEGIN /etc/grub.d/30_otheros ### 
  
 # This entry automatically added by the Debian installer for a non-linux OS 
 # on /dev/sda3 
 menuentry "Windows Vista (loader)" { 
     set root=(hd0,msdos3) 
     search --no-floppy --fs-uuid --set 30667f93667f5914 
     chainloader +1 
 } 
 ### END /etc/grub.d/30_otheros ### 
  
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
  
 =============================== sda5/etc/fstab: ================================ 
  
 -------------------------------------------------------------------------------- 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda5 during installation 
 UUID=a875526f-e580-4982-9a4d-82aecab45cfd /               ext3    errors=remount-ro 0       1 
 # swap was on /dev/sda6 during installation 
 UUID=196236eb-8744-45d1-9a4d-133b81baaf26 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0 
 /dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0 
 -------------------------------------------------------------------------------- 
  
 =================== sda5: Location of files loaded by Grub: ==================== 
  
            GiB - GB             File                                 Fragment(s) 
  
  445.981468201 = 478.868955136  boot/grub/core.img                             1 
  446.036136627 = 478.927654912  boot/grub/grub.cfg                             1 
  444.785171509 = 477.584441344  boot/initrd.img-2.6.32-5-686                   4 
  444.750541687 = 477.547257856  boot/vmlinuz-2.6.32-5-686                      2 
  444.785171509 = 477.584441344  initrd.img                                     4 
  444.750541687 = 477.547257856  vmlinuz                                        2 
  
 ========================= sdb1/syslinux/syslinux.cfg: ========================== 
  
 -------------------------------------------------------------------------------- 
 # D-I config version 2.0 
 include menu.cfg 
 default vesamenu.c32 
 prompt 0 
 timeout 50 
 ui gfxboot bootlogo 
 -------------------------------------------------------------------------------- 
  
 ================= sdb1: Location of files loaded by Syslinux: ================== 
  
            GiB - GB             File                                 Fragment(s) 
  
             ?? = ??             ldlinux.sys                                    1 
             ?? = ??             syslinux/chain.c32                             1 
             ?? = ??             syslinux/gfxboot.c32                           1 
             ?? = ??             syslinux/syslinux.cfg                          1 
             ?? = ??             syslinux/vesamenu.c32                          1 
  
 ============== sdb1: Version of COM32(R) files used by Syslinux: =============== 
  
  syslinux/chain.c32                 :  COM32R module (v4.xx) 
  syslinux/gfxboot.c32               :  COM32R module (v4.xx) 
  syslinux/vesamenu.c32              :  COM32R module (v4.xx) 
  
 ======================== Unknown MBRs/Boot Sectors/etc: ======================== 
  
 Unknown BootLoader on sda4 
  
 00000000  1d fc 0a fc 0d fc 27 fc  55 fc 96 fc eb fc 53 fd  |......'.U.....S.| 
 00000010  c9 fd 48 fe cd fe 54 ff  dc ff 5e 00 da 00 4e 01  |..H...T...^...N.| 
 00000020  b6 01 0c 02 4f 02 7c 02  8d 02 84 02 5f 02 23 02  |....O.|....._.#.| 
 00000030  d1 01 6e 01 fa 00 7a 00  f6 ff 6c ff de fe 56 fe  |..n...z...l...V.| 
 00000040  d6 fd 5e fd f0 fc 90 fc  3f fc fc fb c7 fb a2 fb  |..^.....?.......| 
 00000050  8c fb 86 fb 8f fb ad fb  dc fb 1d fc 6a fc c1 fc  |............j...| 
 00000060  1c fd 7a fd db fd 43 fe  b7 fe 36 ff be ff 50 00  |..z...C...6...P.| 
 00000070  e6 00 7b 01 0e 02 9d 02  28 03 b2 03 3b 04 c7 04  |..{.....(...;...| 
 00000080  53 05 d7 05 4f 06 b8 06  0c 07 48 07 6a 07 75 07  |S...O.....H.j.u.| 
 00000090  6e 07 55 07 2e 07 fe 06  c2 06 7d 06 2b 06 cd 05  |n.U.......}.+...| 
 000000a0  5f 05 e1 04 53 04 b7 03  11 03 65 02 b1 01 fd 00  |_...S.....e.....| 
 000000b0  4b 00 9b ff eb fe 3a fe  8b fd de fc 38 fc 9b fb  |K.....:.....8...| 
 000000c0  09 fb 83 fa 0a fa a2 f9  49 f9 fc f8 bf f8 8f f8  |........I.......| 
 000000d0  70 f8 60 f8 61 f8 7a f8  a7 f8 ec f8 43 f9 aa f9  |p.`.a.z.....C...| 
 000000e0  20 fa 9d fa 1f fb a3 fb  26 fc a7 fc 21 fd 98 fd  | .......&...!...| 
 000000f0  0c fe 7d fe e6 fe 4d ff  b0 ff 0d 00 5f 00 aa 00  |..}...M....._...| 
 00000100  ec 00 24 01 54 01 80 01  ab 01 d2 01 f4 01 0f 02  |..$.T...........| 
 00000110  28 02 3a 02 45 02 4c 02  56 02 63 02 6f 02 7b 02  |(.:.E.L.V.c.o.{.| 
 00000120  87 02 91 02 97 02 97 02  93 02 8e 02 82 02 69 02  |..............i.| 
 00000130  46 02 18 02 de 01 9b 01  50 01 01 01 aa 00 50 00  |F.......P.....P.| 
 00000140  f3 ff 97 ff 3d ff eb fe  a0 fe 64 fe 37 fe 1a fe  |....=.....d.7...| 
 00000150  0d fe 12 fe 25 fe 49 fe  7f fe cc fe 2e ff a1 ff  |....%.I.........| 
 00000160  22 00 ab 00 34 01 b9 01  35 02 a9 02 17 03 7b 03  |"...4...5.....{.| 
 00000170  d7 03 2c 04 79 04 bf 04  fb 04 28 05 46 05 58 05  |..,.y.....(.F.X.| 
 00000180  5b 05 50 05 37 05 13 05  e2 04 a5 04 58 04 fe 03  |[.P.7.......X...| 
 00000190  8f 03 10 03 81 02 e5 01  41 01 99 00 f1 ff 4f ff  |........A.....O.| 
 000001a0  b4 fe 20 fe 91 fd 08 fd  88 fc 11 fc a2 fb 3f fb  |.. ...........?.| 
 000001b0  e7 fa a0 fa 69 fa 47 fa  39 fa 3e fa 54 fa 00 fe  |....i.G.9.>.T...| 
 000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 c3 06 00 fe  |................| 
 000001d0  ff ff 05 fe ff ff 02 10  c3 06 00 a0 4a 00 00 00  |............J...| 
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 
 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 
 00000200 
  
  
  
 ADDITIONAL INFORMATION : 
 =================== log of boot-repair 2012-05-19__14h57 =================== 
 boot-repair version : 3.18-0ppa16~precise 
 boot-sav version : 3.18-0ppa44~precise 
 glade2script version : 0.3.2.1-0ppa7~precise 
 boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686) 
  
 =================== OSPROBER: 
 /dev/sda2:Windows Vista (loader):Windows:chain 
 /dev/sda3:Windows Vista (loader):Windows1:chain 
 /dev/sda5:Debian GNU/Linux (6.0.5):Debian:linux 
  
 =================== BLKID: 
 /dev/loop0: TYPE="squashfs" 
 /dev/loop1: UUID="53938097-35f7-424f-8e1c-f946b706de98" TYPE="ext2" 
 /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
 /dev/sda2: LABEL="RECOVERY" UUID="58B27D48B27D2C1E" TYPE="ntfs" 
 /dev/sda3: LABEL="Windows" UUID="30667F93667F5914" TYPE="ntfs" 
 /dev/sda5: UUID="a875526f-e580-4982-9a4d-82aecab45cfd" SEC_TYPE="ext2" TYPE="ext3" 
 /dev/sda6: UUID="196236eb-8744-45d1-9a4d-133b81baaf26" TYPE="swap" 
 /dev/sdb1: LABEL="AMO VOCE S2" UUID="74CE-9447" TYPE="vfat" 
  
  
 1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS. 
  
 Warning: extended partition does not start at a cylinder boundary. 
 DOS and Linux will interpret the contents differently. 
  
  
 =================== /mnt/boot-sav/sda5/etc/default/grub : 
  
 # If you change this file, run 'update-grub' afterwards to update 
 # /boot/grub/grub.cfg. 
  
 GRUB_DEFAULT=0 
 GRUB_TIMEOUT=10 
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
 GRUB_CMDLINE_LINUX_DEFAULT="quiet" 
 GRUB_CMDLINE_LINUX="" 
  
 # Uncomment to enable BadRAM filtering, modify to suit your needs 
 # This works with Linux (no patch required) and with any kernel that obtains 
 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 
  
 # Uncomment to disable graphical terminal (grub-pc only) 
 #GRUB_TERMINAL=console 
  
 # The resolution used on graphical terminal 
 # note that you can use only modes which your graphic card supports via VBE 
 # you can see them in real GRUB with the command `vbeinfo' 
 #GRUB_GFXMODE=640x480 
  
 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
 #GRUB_DISABLE_LINUX_UUID=true 
  
 # Uncomment to disable generation of recovery mode menu entries 
 #GRUB_DISABLE_LINUX_RECOVERY="true" 
  
 # Uncomment to get a beep at grub start 
 #GRUB_INIT_TUNE="480 440 1" 
  
  
  
  
 =================== PARTITIONS & DISKS: 
 sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda1. 
 sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    BOOT/BCD,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda2. 
 sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda3. 
 sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not-on-gpt-disk,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    /mnt/boot-sav/sda5. 
  
 sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     63 sectors * 512 bytes 
  
 =================== PARTED: 
  
 Model: ATA WDC WD5000BEVT-7 (scsi) 
 Disk /dev/sda: 500GB 
 Sector size (logical/physical): 512B/512B 
 Partition Table: msdos 
  
 Number  Start   End     Size    Type      File system     Flags 
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag 
 2      41.1MB  15.8GB  15.7GB  primary   ntfs 
 3      15.8GB  440GB   424GB   primary   ntfs            boot 
 4      440GB   500GB   60.6GB  extended 
 5      440GB   498GB   58.1GB  logical   ext3 
 6      498GB   500GB   2503MB  logical   linux-swap(v1) 
  
  
 Model: Kingston DataTraveler 2.0 (scsi) 
 Disk /dev/sdb: 2034MB 
 Sector size (logical/physical): 512B/512B 
 Partition Table: msdos 
  
 Number  Start   End     Size    Type     File system  Flags 
 1      20.7MB  2034MB  2014MB  primary  fat32        boot 
  
  
 =================== MOUNT: 
 /cow on / type overlayfs (rw) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 /dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) 
 /dev/loop0 on /rofs type squashfs (ro,noatime) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 tmpfs on /tmp type tmpfs (rw,nosuid,nodev) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu) 
 /dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw) 
 /dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) 
 /dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) 
 /dev/sda5 on /mnt/boot-sav/sda5 type ext3 (rw) 
  
  
 /sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent 
 /sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent 
 /sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent 
 /dev:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 usbmon8 v4l vga_arbiter video0 zero 
 /dev/mapper:  control 
  
 =================== DF: 
  
 Filesystem     Type       Size  Used Avail Use% Mounted on 
 /cow           overlayfs  775M  260M  476M  36% / 
 udev           devtmpfs   2.0G   12K  2.0G   1% /dev 
 tmpfs          tmpfs      805M  884K  804M   1% /run 
 /dev/sdb1      vfat       1.9G  1.7G  270M  86% /cdrom 
 /dev/loop0     squashfs   673M  673M     0 100% /rofs 
 tmpfs          tmpfs      2.0G   25M  2.0G   2% /tmp 
 none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock 
 none           tmpfs      2.0G  980K  2.0G   1% /run/shm 
 /dev/sda1      vfat        40M  8.7M   31M  23% /mnt/boot-sav/sda1 
 /dev/sda2      fuseblk     15G  7.6G  7.2G  52% /mnt/boot-sav/sda2 
 /dev/sda3      fuseblk    395G   51G  345G  13% /mnt/boot-sav/sda3 
 /dev/sda5      ext3        54G  1.5G   50G   3% /mnt/boot-sav/sda5 
  
 =================== FDISK: 
  
 Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x6f191570 
  
 Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1              63       80324       40131   de  Dell Utility 
 /dev/sda2           80325    30800324    15360000    7  HPFS/NTFS/exFAT 
 /dev/sda3   *    30800325   858431535   413815605+   7  HPFS/NTFS/exFAT 
 /dev/sda4       858433534   976771071    59168769    5  Extended 
 /dev/sda5       858433536   971880447    56723456   83  Linux 
 /dev/sda6       971882496   976771071     2444288   82  Linux swap / Solaris 
  
 Disk /dev/sdb: 2034 MB, 2034237440 bytes 
 23 heads, 55 sectors/track, 3140 cylinders, total 3973120 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x04030201 
  
 Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   *       40480     3973119     1966320    b  W95 FAT32 
  
  
  
 =================== Default settings 
 recommendedrepair 
 This setting would reinstall the grub2 of sda5 into the MBR of sda. 
 Additional repair would be performed: unhide-bootmenu 
  
 =================== Settings chosen by the user 
 customrepair 
 This setting will restore the sda (mbr) (sda3) MBR on sda. 
 Additional repair will be performed: unhide-bootmenu repair-filesystems 
  
  
 Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var 
 fsck from util-linux 2.20.1 
 Refusing to operate on read-write mounted device /dev/sda2. 
 Refusing to operate on read-write mounted device /dev/sda3. 
 fsck from util-linux 2.20.1 
 Will restore the MBR_TO_RESTORE : sda (mbr) into sda 
 dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 
 0+1 records in 
 0+1 records out 
 parted /dev/sda set 3 boot on 
  
                                                                            
 Information: You may need to update /etc/fstab. 
  
 Boot successfully repaired. 
  
 You can now reboot your computer.
```

---

### Post by wilee-nilee on 2012-05-19
So you still have debian, and the ms-sys boot put in by the boot-reoair is not working. This is to get the boot back straight to windows, you can remove the debian partitions from the partitioner in windows.

Since you have a Windows recovery or install disc it seems try this boot to the recovery terminal with that windows disc and run this command to reload the mbr.

```
bootrec.exe /fixmbr
```

Here is a link on getting to that terminal.

  	 	 	 	 	 	   [FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html [/SIZE][/FONT] 
  
There are others commands that can be tried if this does not work. Let us know how tis goes.

---

### Post by francobrotto on 2012-05-19
Hey, thanks for you help wilee-nilee!!

But I dont know why, when I restart with the Repair Disc, absolutely nothing happens, it goes straight to the same screen reporting Windows error, so I cant fix it!!

Im pretty sure I burnt the DVD as I was supposed to, but nothing happens!!! Thats why Im now trying to do it through Ubuntu...

---

### Post by wilee-nilee on 2012-05-19
> **francobrotto said:**
> Hey, thanks for you help wilee-nilee!!

But I dont know why, when I restart with the Repair Disc, absolutely nothing happens, it goes straight to the same screen reporting Windows error, so I cant fix it!!

Im pretty sure I burnt the DVD as I was supposed to, but nothing happens!!! Thats why Im now trying to do it through Ubuntu...

There is a bootloader that can be installed from a ubuntu live cd, here are the instructions.

Make sure the universe repo is ticked and untick the cd, in software sources, found in the ubuntu software center-edit-software sources, then in the terminal.

```
sudo apt-get update
```Then run this command set and notice the error reference.

                                  [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR 
[/SIZE][/FONT]
[FONT=Verdana, sans-serif][SIZE=1]You should boot straight to the windows setup.[/SIZE][/FONT]
[SIZE=1][FONT=Verdana, sans-serif]
Did you notice as well that my first post only mentioned the boot-repair, not any instructions on using it. I suggested using a windows recovery or install disc to run the [/FONT][/SIZE]bootrec.exe /fixmbr command.

If you have the windows disc try that first, personally I would want an actual MS bootloader in place if I had a disc to install it.

---

### Post by francobrotto on 2012-05-19
Hello wilee-nilee

Thanks again, I tried doing this lilo thing and it didnt work. I restarted and got the same error. This is the output from the terminal if it matters:

sudo lilo -M /dev/sda mbr
/boot/boot.0800 exists - no /dev/sda backup copy made.
The Master Boot Record of  /dev/sda  has been updated.

Also, I downloaded from torrent Windows 7, made a DVD and again, it seems my computer doesnt even read it (even thought I set BIOS to read DVD firstly)

I dont know what else to do!!!

Gawd!

ps. thank you coffeecat for adding code tags!

---

### Post by wilee-nilee on 2012-05-19
> **francobrotto said:**
> Hello wilee-nilee

Thanks again, I tried doing this lilo thing and it didnt work. I restarted and got the same error. This is the output from the terminal if it matters:

sudo lilo -M /dev/sda mbr
/boot/boot.0800 exists - no /dev/sda backup copy made.
The Master Boot Record of  /dev/sda  has been updated.

Also, I downloaded from torrent Windows 7, made a DVD and again, it seems my computer doesnt even read it (even thought I set BIOS to read DVD firstly)

I dont know what else to do!!!

Gawd!

ps. thank you coffeecat for adding code tags!

So there is another part of the windows boot called the pbr, if it has been changed this can be a problem.

I believe a W7 disc will possibly fix this, I would not use a torrent disc, but it may be that you just need to use the per session boot menu rather then the bios setting.

On the bios screen, not the actual bios at powering on it should tell you the boot from key prompts. A common key used is f12 you can look on the web for more info per your computer manufacturer, and or model.

I don't think the one command I have posted is going to fix this as the pbr needs rebuilding.

Can you get a legit recovery disc or install disc from a friend, has to be the same bit I believe. You can buy a recovery disc for 9.75$ on the web.

[http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery](http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery)

It may be that from looking at the boot-script and not seeing windows mentioned that it looks like it never was accessed after the debian install, meaning a chkdsk was not run, which is a automatic function if you have changed the Windows partition size.

Can you get to a f8 prompt at the booting of windows and get a terminal, if so try chkdsk /r and see if it gives the option to do this on a reboot.

---

### Post by bodhi.zazen on 2012-05-20
> **francobrotto said:**
> Also, I downloaded from torrent Windows 7, made a DVD and again, it seems my computer doesnt even read it (even thought I set BIOS to read DVD firstly)

We do not support pirated software here. I am closing this thread now.

---

