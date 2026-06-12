---
title: "Ubuntu not booting"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by troysos on 2011-02-08
Hello everyone! This is my first post and I just got though trying to install Ubuntu along side windows 7 and Linux Mint. Linux Mint was my first try with Linux and I like it so far. I wanted to try out Ubuntu (I know they are very similar). I made an install disc (64amd desktop) and went though the entire process of installing. The insulation looked like everything went right and when I restarted my computer just like the installation said to do. I cannot get into Ubuntu or Mint now, Windows 7 boots fine. When I try and boot into Ubuntu my computer just goes into a sleep mode. When I try and boot into Mint my computer just sits in the boot mode with a bunch of letter and numbers.
Is the problem that I cant triple boot my computer? 
I'm running a Dell desktop, AMD 64 dual core, 500HD 300gigs to widows and Ubuntu and Mint splitting the rest. Thank you for your help!

---

### Post by drs305 on 2011-02-08
troysos,

Welcome to the Ubuntu forums. For us to understand what is wrong, please go to the following site. Download and run the boot info script, then post the contents of RESULTS.txt here.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

We will probably be able to tell from RESULTS.txt, but were Ubuntu and Mint separate installations or did you try the Wubi (within Windows) version?  If both were Wubi, I recommend visiting this site:
[Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by troysos on 2011-02-08
Thank you for helping me. I installed Mint months ago and it was a separate install dual booted with windows. I tried installing Ubuntu the same way. The results were
```
[IMG]file:///tmp/moz-screenshot.png[/IMG]   	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }                  Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in      partition #7 for (,msdos7)/boot/grub.  sda1: _________________________________________________________________________      File system:       vfat     Boot sector type:  Dell Utility: Fat16     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /COMMAND.COM  sda2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /bootmgr /Boot/BCD  sda3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /Windows/System32/winload.exe  sda4: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sda5: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Linux Mint 10 Julia     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda6: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda7: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 10.10     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda8: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1                  63       112,454       112,392  de Dell Utility /dev/sda2    *        112,640    17,762,303    17,649,664   7 HPFS/NTFS /dev/sda3          17,762,304   642,612,209   624,849,906   7 HPFS/NTFS /dev/sda4         642,613,246   976,771,071   334,157,826   5 Extended /dev/sda5         642,613,248   814,486,087   171,872,840  83 Linux /dev/sda6         963,131,392   976,771,071    13,639,680  82 Linux swap / Solaris /dev/sda7         814,487,552   956,981,247   142,493,696  83 Linux /dev/sda8         956,983,296   963,129,343     6,146,048  82 Linux swap / Solaris   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/sda1        07D9-0C1F                              vfat       DellUtility                    /dev/sda2        5400E17000E1598E                       ntfs       RECOVERY                       /dev/sda3        760AE5540AE511C3                       ntfs       OS                             /dev/sda4: PTTYPE="dos"  /dev/sda5        ad03dd5a-e6a0-4c01-8272-387da2cbfb86   ext4                                      /dev/sda6        43155547-35f9-4c7a-9e47-b797879e1a2f   swap                                      /dev/sda7        109f8cbb-e58d-412b-b852-7a76251f5dd0   ext4                                      /dev/sda8        27e3fde9-6b80-4dc4-93a0-0f602c00080d   swap                                      /dev/sda: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sr0         /cdrom                   iso9660    (ro,noatime) /dev/loop0       /rofs                    squashfs   (ro,noatime)   =========================== sda5/boot/grub/grub.cfg: ===========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub # sudo bash ~/Desktop/boot_info_script*.sh   ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ext2 set root='(hd0,msdos5)' search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(hd0,msdos5)' search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/06_mint_theme ### insmod part_msdos insmod ext2 set root='(hd0,msdos5)' search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 insmod png if background_image /boot/grub/linuxmint.png ; then   set color_normal=white/black   set color_highlight=white/light-gray else   set menu_color_normal=white/black   set menu_color_highlight=white/light-gray fi ### END /etc/grub.d/06_mint_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-22-generic } menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	echo	'Loading Linux 2.6.35-22-generic ...' 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-22-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/10_lupin ### ### END /etc/grub.d/10_lupin ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows 7 (loader) (on /dev/sda2)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd0,msdos2)' 	search --no-floppy --fs-uuid --set 5400e17000e1598e 	chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  =============================== sda5/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda5 during installation UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda6 during installation UUID=43155547-35f9-4c7a-9e47-b797879e1a2f none            swap    sw              0       0  =================== sda5: Location of files loaded by Grub: ===================    357.0GB: boot/grub/core.img  386.8GB: boot/grub/grub.cfg  380.8GB: boot/initrd.img-2.6.35-22-generic  357.0GB: boot/vmlinuz-2.6.35-22-generic  380.8GB: initrd.img  357.0GB: vmlinuz  =========================== sda7/boot/grub/grub.cfg: ===========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ext2 set root='(hd0,msdos7)' search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(hd0,msdos7)' search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos7)' 	search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-22-generic } menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos7)' 	search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 	echo	'Loading Linux 2.6.35-22-generic ...' 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-22-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos7)' 	search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos7)' 	search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows 7 (loader) (on /dev/sda2)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd0,msdos2)' 	search --no-floppy --fs-uuid --set 5400e17000e1598e 	chainloader +1 } menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) (on /dev/sda5)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro quiet splash 	initrd /boot/initrd.img-2.6.35-22-generic } menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) -- recovery mode (on /dev/sda5)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86 	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro single 	initrd /boot/initrd.img-2.6.35-22-generic } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  =============================== sda7/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda7 during installation UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda8 during installation UUID=27e3fde9-6b80-4dc4-93a0-0f602c00080d none            swap    sw              0       0  =================== sda7: Location of files loaded by Grub: ===================    440.7GB: boot/grub/core.img  430.0GB: boot/grub/grub.cfg  417.9GB: boot/initrd.img-2.6.35-22-generic  440.7GB: boot/vmlinuz-2.6.35-22-generic  417.9GB: initrd.img  440.7GB: vmlinuz 
```

---

### Post by troysos on 2011-02-08
Maybe I didn't do that right.

---

### Post by drs305 on 2011-02-08
> **troysos said:**
> Maybe I didn't do that right.

It's the correct contents.  :-)

Try opening the RESULTS.txt with Gedit (Applications, Accessories, Text Editor), then CTRL-A to highlight, CTRL-c to copy, then CTRL-v to paste into a new post.

You can press the "Preview Post" button at the bottom of the post to see what it's going to look like before you "Submit Reply". Don't use any type of formatting, although pasting within "code" tags is preferred (with the # icon).

---

### Post by softappstudio on 2011-02-08
I have tried 7 times to install Ubuntu Lucid from LiveCD and a USB-HDD image of that, onto a new PC with 2.5" m-SATA HDD. Installation proceeds smoothly, but it will not boot. Early messages (too quick to follow) suggest failure to mount /dev (?). This system will support WinXP (which I don't want) do no hardware problem. The actual LiveCD was used to install Ubuntu on another PC, OK. Ubuntu runus in "trial" mode on this new PC. I have checked       fdisk -l     and that indicates that the HDD is bootable. [I am a newbie].  I have tried to use grub-install but that fails, and its man pages seem to be written for a different OS, so no luck there.
 
This is madness! What is wrong? What can I do? Would this "RESULTS.txt" be of help, if so where is it please?

Thanks for any suggestions!
--Grahame

---

### Post by drs305 on 2011-02-08
softappstudio,

Please open your own thread, as it can get confusing to discuss different issues within the same thread. You can just copy your entry from this post, and you can post the RESULTS.txt, which you get by running the boot info script from here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by troysos on 2011-02-08
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

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
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,640    17,762,303    17,649,664   7 HPFS/NTFS
/dev/sda3          17,762,304   642,612,209   624,849,906   7 HPFS/NTFS
/dev/sda4         642,613,246   976,771,071   334,157,826   5 Extended
/dev/sda5         642,613,248   814,486,087   171,872,840  83 Linux
/dev/sda6         963,131,392   976,771,071    13,639,680  82 Linux swap / Solaris
/dev/sda7         814,487,552   956,981,247   142,493,696  83 Linux
/dev/sda8         956,983,296   963,129,343     6,146,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D9-0C1F                              vfat       DellUtility                   
/dev/sda2        5400E17000E1598E                       ntfs       RECOVERY                      
/dev/sda3        760AE5540AE511C3                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ad03dd5a-e6a0-4c01-8272-387da2cbfb86   ext4                                     
/dev/sda6        43155547-35f9-4c7a-9e47-b797879e1a2f   swap                                     
/dev/sda7        109f8cbb-e58d-412b-b852-7a76251f5dd0   ext4                                     
/dev/sda8        27e3fde9-6b80-4dc4-93a0-0f602c00080d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 5400e17000e1598e
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
UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=43155547-35f9-4c7a-9e47-b797879e1a2f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 357.0GB: boot/grub/core.img
 386.8GB: boot/grub/grub.cfg
 380.8GB: boot/initrd.img-2.6.35-22-generic
 357.0GB: boot/vmlinuz-2.6.35-22-generic
 380.8GB: initrd.img
 357.0GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 109f8cbb-e58d-412b-b852-7a76251f5dd0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 5400e17000e1598e
    chainloader +1
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda5) -- recovery mode (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ad03dd5a-e6a0-4c01-8272-387da2cbfb86
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad03dd5a-e6a0-4c01-8272-387da2cbfb86 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=109f8cbb-e58d-412b-b852-7a76251f5dd0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=27e3fde9-6b80-4dc4-93a0-0f602c00080d none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 440.7GB: boot/grub/core.img
 430.0GB: boot/grub/grub.cfg
 417.9GB: boot/initrd.img-2.6.35-22-generic
 440.7GB: boot/vmlinuz-2.6.35-22-generic
 417.9GB: initrd.img
 440.7GB: vmlinuz

```

---

### Post by drs305 on 2011-02-08
Since Mint was working and now you can't get into it, let's get it working again by pointing Grub2 to your Mint installation. From a LiveCD:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

If Mint boot,s run:
```
sudo update-grub
```

I don't know specifically why Ubuntu isn't working for you, but this should at least get Mint back and allow you to pick which OS you want to use.

---

### Post by softappstudio on 2011-02-08
Thank you Master Roaster. Sorry I placed this is the wrong thread, it looked perfect for my problem, but I have now posted  <along with my RESULTS.txt> in my  very own thread. 
--Grahame


Edit: Here is *softappstudio's* new thread for those who would like to help him:
[http://ubuntuforums.org/showthread.php?t=1684152]("http://ubuntuforums.org/showthread.php?t=1684152")

---

