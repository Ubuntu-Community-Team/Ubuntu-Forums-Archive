---
title: "Can I add ubuntu to my setup?"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by jogonjr on 2011-02-15
Hi all. I just want to know if it is still possible to add ubuntu 10.04 to my setup. i have three primary partitions in one drive installed with mac os x,xp,and 7.linux mndriva is on an extended partition. Id appreciate any input.

---

### Post by presence1960 on 2011-02-15
You can add ubuntu to the extended partition provided you have free space there or can create some space for ubuntu inside the extended partition. You will need to create a logical partition inside the extended to house ubuntu.

---

### Post by jogonjr on 2011-02-16
Thank you, however i  have created a logical partition from the extended partition already which is for the Linux Swap. ?

---

### Post by jogonjr on 2011-02-16
not possible anymore?

---

### Post by jogonjr on 2011-02-16
no can do?

---

### Post by coffeecat on 2011-02-16
You can have as many logical partitions as you want in an extended partition, free contiguous space on the drive being the only limiting factor. presence1960 has already said as much as can be said with the limited information you have posted. If you need detailed help you need to post more details of your partition layout. The output of:

```
sudo fdisk -lu
```

... would help.

Your Mandriva swap partition can be used by Ubuntu. There is no point in having more than one swap partition.

---

### Post by jogonjr on 2011-02-17
Thank you for your help coffeecat.
This is the output

```
[COLOR="Navy"]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d249d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    44302398    22151168   af  HFS / HFS+
/dev/sda2   *    44302419    86243410    20970496    7  HPFS/NTFS
/dev/sda3        86247424   583192575   248472576    7  HPFS/NTFS
/dev/sda4       583196670   625139711    20971521    f  W95 Ext'd (LBA)
/dev/sda5       583196672   623091711    19947520   83  Linux
/dev/sda6       623093760   625139711     1022976   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03999d69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976767451   488383694+   7  HPFS/NTFS[/COLOR]
```

The 500 GB is my external HDD but I don't want to touch that.
How do I create another logical partition from the extended partition? I tried within Windows but it wont let me. It says the drive has reached the limit. Thanks again. :D

---

### Post by coffeecat on 2011-02-17
First, when you post output like that, please always wrap it in BBCode [noparse]```
 and 
```[/noparse] tags. You can use the # icon in the message toolbar for this. Do it now. Make a fresh post with your 'sudo fdisk -lu ' output in code tags and compare it with how it appears in your post #7, which is very difficult to read.

For more on BBCode, see:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

But to your problem. Your fdisk output gives these partition sizes:

sda1 - presumably your MacOS partition - 22.7GB
sda2 - presumably XP - 21.5GB
sda3 - presumably Windows 7 - 254GB
sda4 - your extended partition - 21.5GB, which contains these logical partitions:
sda5 - presumably Mandriva root - 20.4GB
sda6 - swap partition - 1.05GB

And you have no unallocated space - or nothing significant

You have two options:

1 - shrink sda5 to make room for another Linux partition for Ubuntu. 20GB is not much to play with. This is probably not a very good idea.

2 - shrink your sda3 Win7 C: partition to allow you to enlarge the extended partition so that you can create a partition for Ubuntu.

Personally, I would choose option 2 and this is what I would do:

1 - Boot into Windows 7 and use the Disk Management utility to shrink the Windows 7 partition by the size you want the Ubuntu partition to be. 20GB would be a good size. Windows 7 is plenty big enough at 254GB, and it would run quite  happily  234GB.

**Do not use Windows 7 Disk management to try to create partitions for Ubuntu.** This is most important.

2 - Backup anything important from Mandriva. The extended partition will be enlarged next and if something goes wrong, you may lose Mandriva. In fact be aware that if you are very unlucky, editing partitions can sometimes, but mercifully rarely, end in disaster. Backup everything.

3 - Boot up with the live Ubuntu CD. Choose 'try Ubuntu', not the installer. From the desktop open System > Administration > Gparted. Right-click on the swap partition sda6 and click on 'swapoff'. Now highlight sda4 and from the Partition menu > Resize/Move. Enlarge it backwards to take over the 20GB vacated by Windows 7. Now click on 'Apply' (the green tick icon). This might take some time. Now click on the 20GB unallocated space that should have appeared just below the sda4 line. From the Partition menu > New, and create a logical partition with an ext4 filesystem. Click on Apply. Make a note of the partition number of the new ext4 partition. It may be sda7 with your original sda5 and sda6 unchanged, or all the logical numbers may have shifted around.

4 - Now close Gparted and start the installer. When you get to the partitioning stage, choose manual/advanced and tell the installer to use the new partition you've made for the Ubuntu root partition (/). It will detect the swap partition automatically - no need to do anything.

The Ubuntu installer will automatically detect Mandriva and the two installations of Windows and set up a grub boot menu for them as well as Ubuntu. What it will do about MacOS, I have no idea, and I cannot help you with that.

Now here's one for your bookmarks. Most of what you need to know about partitioning:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by jogonjr on 2011-02-19
Thank you for your help.
I was able to install ubuntu and all work fine except Mandriva.
This is what I get when booting to Mandriva

  [[IMG]http://img198.imagevenue.com/loc174/th_22092_19022011115_122_174lo.jpg[/IMG]](http://img198.imagevenue.com/img.php?image=22092_19022011115_122_174lo.jpg)

---

### Post by coffeecat on 2011-02-19
The important error in that screenshot seems to be 'Cannot open root device "UUID=....'. The UUID of the Mandriva partition should not have changed when you enlarged the extended partition and added a Ubuntu one, so I'm not sure what's going on. Let's see what the situation is now. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of results.txt here. Use code tags as before. The results.txt file will contain details of your revised partition layout and configuration files from both Ubuntu and Mandriva so, hopefully, we can see what is going wrong.

---

### Post by jogonjr on 2011-02-19
The UIID probably changed because I reinstalled Mandriva. Then reinstalled Ubuntu then the extended partition got messed up so I reinstalled Mandriva then Ubuntu again but the error the first time is the same as the error I posted. I'm sorry I did things on my own. It wont happen again though.  ](*,)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.2 
                       (Official) for i586 Kernel 2.6.33.7-desktop586-2mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    44,302,398    44,302,336  af HFS
/dev/sda2          44,302,419    86,243,410    41,940,992   7 HPFS/NTFS
/dev/sda3    *     86,247,424   541,249,535   455,002,112   7 HPFS/NTFS
/dev/sda4         541,251,582   625,137,344    83,885,763   5 Extended
/dev/sda5         541,251,584   582,172,671    40,921,088  83 Linux
/dev/sda6         582,174,720   584,126,463     1,951,744  82 Linux swap / Solaris
/dev/sda7         584,139,528   625,137,344    40,997,817  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        94ab8c37-27cb-3c54-b971-c8d04b48f746   hfsplus    Mac                           
/dev/sda2        3C7CD1F77CD1ABC0                       ntfs                                     
/dev/sda3        40A8E043A8E038D4                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        caed8f6c-5315-4050-bdd7-6e8a010543c7   ext4                                     
/dev/sda6        4d2a4e07-3925-4001-a2ae-87b0a32cf1db   swap                                     
/dev/sda7        30b0c3f3-f03e-4311-83a3-297d7b17f650   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=caed8f6c-5315-4050-bdd7-6e8a010543c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=caed8f6c-5315-4050-bdd7-6e8a010543c7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set caed8f6c-5315-4050-bdd7-6e8a010543c7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda1)" {
    insmod hfsplus
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 27c69ff83bb5407f
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 27c69ff83bb5407f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda1)" {
    insmod hfsplus
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 27c69ff83bb5407f
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 27c69ff83bb5407f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3c7cd1f77cd1abc0
    chainloader +1
}
menuentry "linux (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
    initrd (hd0,6)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db
    initrd (hd0,6)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 failsafe
    initrd (hd0,6)/boot/initrd.img
}
menuentry "desktop586 2.6.33.5-2 (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz-2.6.33.5-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.33.5-2 root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
    initrd (hd0,6)/boot/initrd-2.6.33.5-desktop586-2mnb.img
}
menuentry "desktop586 2.6.33.7-2 (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz-2.6.33.7-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.33.7-2 root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
    initrd (hd0,6)/boot/initrd-2.6.33.7-desktop586-2mnb.img
}
menuentry "linux-0 (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz-2.6.33.7-desktop586-2mnb BOOT_IMAGE=linux-0 root=UUID=4823b7b5-3df1-4e0f-ab11-cdf3929e88fb
    initrd (hd0,6)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=caed8f6c-5315-4050-bdd7-6e8a010543c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 292.5GB: boot/grub/core.img
 294.6GB: boot/grub/grub.cfg
 292.5GB: boot/initrd.img-2.6.32-24-generic
 292.5GB: boot/vmlinuz-2.6.32-24-generic
 292.5GB: initrd.img
 292.5GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

timeout 20
color black/cyan yellow/cyan
gfxmenu (hd0,6)/boot/gfxmenu
default 0

title linux
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
initrd (hd0,6)/boot/initrd.img

title linux-nonfb
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db
initrd (hd0,6)/boot/initrd.img

title failsafe
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 failsafe
initrd (hd0,6)/boot/initrd.img

title windows
root (hd0,2)
makeactive
chainloader +1

title Mac
root (hd0,0)
chainloader +1

title windows-0
root (hd0,4)
chainloader +1

title desktop586 2.6.33.5-2
kernel (hd0,6)/boot/vmlinuz-2.6.33.5-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.33.5-2 root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
initrd (hd0,6)/boot/initrd-2.6.33.5-desktop586-2mnb.img

title desktop586 2.6.33.7-2
kernel (hd0,6)/boot/vmlinuz-2.6.33.7-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.33.7-2 root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
initrd (hd0,6)/boot/initrd-2.6.33.7-desktop586-2mnb.img

title linux-0
kernel (hd0,6)/boot/vmlinuz-2.6.33.7-desktop586-2mnb BOOT_IMAGE=linux-0 root=UUID=4823b7b5-3df1-4e0f-ab11-cdf3929e88fb 
initrd (hd0,6)/boot/initrd.img

=============================== sda7/etc/fstab: ===============================

# Entry for /dev/sda7 :
UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 / ext3 acl,noatime 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db swap swap defaults 0 0

=================== sda7: Location of files loaded by Grub: ===================


 318.6GB: boot/grub/menu.lst
 318.6GB: boot/grub/stage2
 318.5GB: boot/initrd-2.6.33.5-desktop586-2mnb.img
 318.6GB: boot/initrd-2.6.33.7-desktop586-2mnb.img
 318.6GB: boot/initrd-desktop586.img
 318.6GB: boot/initrd.img
 318.6GB: boot/vmlinuz
 318.6GB: boot/vmlinuz-2.6.33.5-desktop586-2mnb
 318.6GB: boot/vmlinuz-2.6.33.7-desktop586-2mnb
 318.6GB: boot/vmlinuz-desktop586
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf ed  e1 e8 6a 00 8a 16 04 e6  |.|h.N.....j.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5b 00 f4 eb fd 66 60  |.... ....[....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 52 31 d2 66 c1 ea 04  |.fa.f`...R1.f...|
000000f0  8e c2 5b 1e 1e 66 03 0e  00 e6 66 51 06 53 30 e4  |..[..f....fQ.S0.|
00000100  50 68 10 00 8a 16 04 e6  89 e6 b4 42 cd 13 72 a5  |Ph.........B..r.|
00000110  89 ec 07 66 61 c3 66 60  57 be dd e3 e8 07 00 5e  |...fa.f`W......^|
00000120  e8 03 00 66 61 c3 bb 01  00 ac 3c 00 74 06 b4 0e  |...fa.....<.t...|
00000130  cd 10 eb f5 c3 66 60 ad  86 e0 ab 3c 00 74 23 89  |.....f`....<.t#.|
00000140  c1 ad 86 e0 80 3e 01 e4  58 74 14 09 c0 75 01 48  |.....>..Xt...u.H|
00000150  80 fc 00 77 0a 3c 41 72  06 3c 5a 77 02 04 20 ab  |...w.<Ar.<Zw.. .|
00000160  e2 df 66 61 c3 66 60 b2  00 66 8b 44 02 66 3b 45  |..fa.f`..f.D.f;E|
00000170  02 75 0f 80 3c 00 75 0a  66 8b 44 06 66 3b 45 06  |.u..<.u.f.D.f;E.|
00000180  74 48 77 44 72 3d 66 60  31 d2 87 f7 66 ad 66 89  |tHwDr=f`1...f.f.|
00000190  c1 87 f7 66 ad 66 39 c8  77 2e 72 27 87 f7 ad 89  |...f.f9.w.r'....|
000001a0  c1 87 f7 ad 80 f9 00 74  1f 39 c8 74 0b 77 07 fe  |.......t.9.t.w..|
000001b0  ce 89 c1 e9 02 00 fe c6  f3 a7 77 0c 72 05 88 f2  |..........w.r...|
000001c0  e9 07 00 fe ca e9 02 00  fe c2 88 96 14 00 80 fa  |................|
000001d0  00 66 61 c3 50 57 8b 3e  0a e6 57 47 47 49 49 b0  |.fa.PW.>..WGGII.|
000001e0  00 f3 aa 89 3e 0a e6 5d  89 2d 5f 58 c3 2f 62 6f  |....>..].-_X./bo|
000001f0  6f 74 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |ot............U.|
00000200

Unknown BootLoader  on sda4

00000000  1e b8 00 00 01 0c 3b 54  06 74 06 62 28 21 a4 02  |......;T.t.b(!..|
00000010  6c c7 f8 06 00 55 21 21  82 ae d1 d7 45 12 ca b0  |l....U!!....E...|
00000020  c6 51 48 80 40 05 43 3a  7b c4 a5 86 22 28 86 a4  |.QH.@.C:{..."(..|
00000030  49 fa 25 9d 45 10 b2 e4  0d 30 db d5 ea ee 30 b1  |I.%.E....0....0.|
00000040  56 74 89 bc a8 7d c4 94  6a b5 c3 12 2a 02 bb 86  |Vt...}..j...*...|
00000050  24 54 1b 71 a5 88 1d 1c  ef 10 db 3d fd 0f ba 26  |$T.q.......=...&|
00000060  7a 0b 12 2d 09 c3 00 fc  58 d3 19 57 d3 f9 91 e3  |z..-....X..W....|
00000070  e0 63 ff fb 94 8d ee e8  9a 0c 3b 04 2d b1 f2 59  |.c........;.-..Y|
00000080  d1 47 57 a2 a9 40 40 67  8e 79 c0 69 66 cf 57 71  |.GW..@@g.y.if.Wq|
00000090  02 0f c4 91 57 54 4d 06  1a 85 c7 5c f6 e4 84 d2  |....WTM....\....|
000000a0  72 43 03 1e 44 18 f0 03  60 13 86 27 f0 e9 3e 8c  |rC..D...`..'..>.|
000000b0  ac c0 05 00 21 df c0 80  06 c1 a5 26 04 00 2d 2c  |....!......&..-,|
000000c0  84 5e 4c 08 00 64 97 d0  0e d0 98 03 20 dd 59 80  |.^L..d...... .Y.|
000000d0  80 06 cf 02 00 1f 13 60  40 03 72 d3 fc 08 00 88  |.......`@.r.....|
000000e0  5e e6 c0 17 ef 00 34 6b  a5 a1 a1 80 1a e2 86 1d  |^.....4k........|
000000f0  00 6b 00 85 05 64 68 04  2d af fa d4 50 ed a1 84  |.k...dh.-...P...|
00000100  29 32 e5 cb d6 cc 2e 0c  2d 2b a1 a1 40 0e 74 00  |)2......-+..@.t.|
00000110  c6 00 72 88 01 7f ab 65  45 e5 c2 03 1d 42 a0 13  |..r....eE....B..|
00000120  94 05 40 a2 30 47 ff 8a  47 22 c0 3b 0c 26 86 06  |..@.0G..G".;.&..|
00000130  77 0d 4a be 3b 1f 00 66  43 01 39 31 95 89 ab 34  |w.J.;..fC.91...4|
00000140  0b 49 ab af 27 86 00 6a  4d 00 7e 4c 48 22 00 20  |.I..'..jM.~LH". |
00000150  25 7f e8 1c 88 60 64 a2  c5 44 b2 18 62 52 fb 76  |%....`d..D..bR.v|
00000160  17 4e 8f a2 66 89 bf 5d  b1 41 64 a6 9a d8 5d ef  |.N..f..].Ad...].|
00000170  23 7b 43 ea a1 f5 59 80  19 65 32 a0 2a 05 30 d6  |#{C...Y..e2.*.0.|
00000180  03 a4 4d 58 84 2a 26 a3  7d f3 03 38 00 d7 97 75  |..MX.*&.}..8...u|
00000190  6d 61 84 3e 51 29 49 25  87 2e 21 95 91 95 b7 c2  |ma.>Q)I%..!.....|
000001a0  fa a2 1a 40 6c 18 91 88  26 7f c4 e8 86 4b 47 3c  |...@l...&....KG<|
000001b0  0b 61 30 44 5a 1b dc 9a  98 00 46 4c db 3c 00 fe  |.a0DZ.....FL.<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 70 02 00 fe  |...........hp...|
000001d0  ff ff 05 fe ff ff 02 68  70 02 00 d0 1d 00 00 00  |.......hp.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by coffeecat on 2011-02-19
Although it certainly helps if you were to divulge everything you have done, :wink: I don't think your re-installs have caused this problem. I think you've uncovered an obscure bug in grub. First of all, the UUID that Mandriva seems to be having trouble with; Mandriva is on sda7:

```
 sda7: _______________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.2 
                       (Official) for i586 Kernel 2.6.33.7-desktop586-2mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
```The UUID of sda7 is:

```
/dev/sda7        30b0c3f3-f03e-4311-83a3-297d7b17f650   ext3
```Mandriva /etc/fstab:

```
=============================== sda7/etc/fstab: ===============================

# Entry for /dev/sda7 :
UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 / ext3 acl,noatime 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db swap swap defaults 0 0
```OK, so far. But this from your Ubuntu grub.cfg:

```
menuentry "linux (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 30b0c3f3-f03e-4311-83a3-297d7b17f650
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=30b0c3f3-f03e-4311-83a3-297d7b17f650 resume=UUID=4d2a4e07-3925-4001-a2ae-87b0a32cf1db splash=silent vga=788
    initrd [COLOR=Red](hd0,6)[/COLOR]/boot/initrd.img
}
```The UUID of sda7 is OK, but look where it thinks Mandriva's initrd.img is - on sda6. Which is wrong. I've never seen such an error before and I don't know why it should do this. In theory, you could edit grub.cfg (you're not meant to) but that is only a temporary fix because grub.cfg gets regenerated every time there is another kernel upgrade and the error will creep in again. I think the problem might be (this is only a theory) that Ubuntu's grub 2 has parsed your Mandriva's legacy grub menu.lst and has got confused. Legacy grub-speak for sda7 is (hd0,6) whereas (hd0,6) in grub 2 means sda6. Have a look at Mandriva's menu.lst in your boot script output to see what I mean.

Here is what I suggest you do. I cannot guarantee that it will work. If it doesn't, we'll try something else.

Boot into Ubuntu. Open a terminal and mount the Mandriva partition:

```
sudo mount /dev/sda7 /mnt
```Now rename Mandriva's menu.lst:

```
sudo mv /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst.backup
```**EDIT**: that, by the way, will disable Mandriva's grub, but as you are using Ubuntu's grub it shouldn't matter.

Be very careful to avoid typos. That's MENU.LST but in lower-case - L not figure 1. Now regenerate Ubuntu's grub.cfg:

```
sudo update-grub
```Now reboot and see if you can boot into Mandriva. Post back to let us know what happens, and if that doesn't work, we'll try something else.

---

### Post by jogonjr on 2011-02-19
So, when I renamed the menu.lst of mandriva and rebuilt the ubuntu grub, it seemed to have gone well since it was able to read all the operating systems even mandriva but when I tried to boot to mandriva, I got this error. 

  [[IMG]http://img279.imagevenue.com/loc475/th_60798_20022011117_122_475lo.jpg[/IMG]](http://img279.imagevenue.com/img.php?image=60798_20022011117_122_475lo.jpg)

---

### Post by jogonjr on 2011-02-20
[B]Now I went to /etc/grub.d/40_custom and added this

[/B]```

menuentry "Mandriva-Gnome 2010" { 

 	insmod ext2 

 	set root=(hd0,7) 

 	linux (hd0,7)/boot/vmlinuz 

 	initrd (hd0,7)/boot/initrd.img

 }
```


and I can now boot into Mandriva. Thank you so much cofee cat. You led me to the right path. :P

---

### Post by coffeecat on 2011-02-20
Yes, 40_custom was one of the things to try next. I'm glad you discovered it.

Presumably, grub was still generating a bad sda7 entry even after renaming the Mandriva menu.lst, so I don't know what was going on there - except that the Mandriva bootup errors were  different from before. If you want to investigate it further, have a look in your Ubuntu's /boot/grub/grub.cfg and see if the Mandriva entries under "30_os-prober" still have the bad (hd0,6) initrd lines.

---

### Post by jogonjr on 2011-02-26
Yes, it was still there. It ws so annoying because the boot entry comes up everytime you update grub. I had to reinstall ubuntu eventually since I had other problems. They're all working now except the wifi connection. I'll create another thread fot that. THanks again.

---

