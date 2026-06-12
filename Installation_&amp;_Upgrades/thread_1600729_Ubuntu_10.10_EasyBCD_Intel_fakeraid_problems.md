---
title: "Ubuntu 10.10 EasyBCD Intel fakeraid problems"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by protivakid on 2010-10-19
I am having a problem getting Ubuntu 10.10's Grub 2 to work with EasyBCD  using an Intel Motherboard Fakeraid. I start by installing 7 then  install ubuntu which works fine. I then boot back into Windows 7 through  grub and use easybcd to write the Windows 7 bootlaoder to the mbr and  add the Grub 2 entry to the boot list. Upon rebooting and selecting  linux all I see is a text screen that says "grub4dos" "Minimal  bash-like..." and then it just sits there waiting for input. 

I tried the whole process using only a single hard drive and it worked  100% fine. How do I get this to work using an intel fakeraid? When  ubuntu gives the option for the boot loader's location what should I  be selecting?

---

### Post by protivakid on 2010-10-19
Bump. No one out there is using the Intel Raid found on motherboards with Ubuntu, Win 7, & EasyBCD?

---

### Post by protivakid on 2010-10-19
Bump. I really figured there would be others out there with this same issue solved!

---

### Post by acatak on 2010-10-19
ima bump for you!

i posted a very similar question 4 hours ago:
[http://ubuntuforums.org/showthread.php?t=1600991](http://ubuntuforums.org/showthread.php?t=1600991)


I too have the option of fakeraid, but its not supported
check out: 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I wanna know how i can raid ubuntu and windows 7 while dual booting harmony.

Another possible option i think is get 4 disks. 2 raid with ubuntu and 2 raid with windows 7.

Whats your setup?

---

### Post by protivakid on 2010-10-20
> **acatak said:**
> ima bump for you!

i posted a very similar question 4 hours ago:
[http://ubuntuforums.org/showthread.php?t=1600991](http://ubuntuforums.org/showthread.php?t=1600991)


I too have the option of fakeraid, but its not supported
check out: 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I wanna know how i can raid ubuntu and windows 7 while dual booting harmony.

Another possible option i think is get 4 disks. 2 raid with ubuntu and 2 raid with windows 7.

Whats your setup?

Bump again! And my setup is 2 drives in Raid 0 that I want to boot 7 and Ubuntu on using EasyBCD instead of grub.

---

### Post by protivakid on 2010-10-21
Bump

---

### Post by kansasnoob on 2010-10-21
I'm a complete dummy when it comes to RAID but regarding Easy-BCD it must be version 2.0.2:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

And Ubuntu's grub must be installed to the Ubuntu partition containing "/boot". So we'd need to know what Ubuntu's partitioning arrangement is.

The easiest way to gather the needed info would be to post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by protivakid on 2010-10-22
> **kansasnoob said:**
> I'm a complete dummy when it comes to RAID but regarding Easy-BCD it must be version 2.0.2:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

And Ubuntu's grub must be installed to the Ubuntu partition containing "/boot". So we'd need to know what Ubuntu's partitioning arrangement is.

The easiest way to gather the needed info would be to post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Still haven't gotten this solved! I am using the latest version of EasyBCD and grub is installed to /boot. 

Here is my bootinfoscript: I put it in a PHP box to make it easier to read :). 

Please note that I was experimenting and added WindowsXP to grub 2 though it does not currently work I just haven't removed it yet in the hopes I can use EasyBCD instead.

[PHP]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of 
    /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bgeadggheg_WD750GBx2Stripe1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

isw_bgeadggheg_WD750GBx2Stripe2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /ntldr /NTDETECT.COM

isw_bgeadggheg_WD750GBx2Stripe3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

isw_bgeadggheg_WD750GBx2Stripe4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bgeadggheg_WD750GBx2Stripe5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_bgeadggheg_WD750GBx2Stripe6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 2,765,780,991 2,765,574,144   7 HPFS/NTFS
/dev/sda3       2,765,780,992 2,807,724,031    41,943,040   7 HPFS/NTFS
/dev/sda4       2,807,724,542 2,930,288,127   122,563,586   5 Extended
Invalid MBR Signature found
/dev/sda5     ? 2,807,724,542 2,807,724,541                   Unknown
/dev/sda6     ? 2,807,724,542 2,807,724,541                   Unknown

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4

Drive: isw_bgeadggheg_WD750GBx2Stripe ___________________ _____________________________________________________

Disk /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe2            206,848 2,765,780,991 2,765,574,144   7 HPFS/NTFS
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe3      2,765,780,992 2,807,724,031    41,943,040   7 HPFS/NTFS
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe4      2,807,724,542 2,930,288,127   122,563,586   5 Extended
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe5      2,807,724,544 2,824,417,279    16,692,736  82 Linux swap / Solaris
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe6      2,824,417,792 2,930,288,127   105,870,336  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe1 3AB81597B81552AD                       ntfs       System Reserved               
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe2 B486227786223A6E                       ntfs                                     
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe3 D4CC4C0CCC4BE778                       ntfs                                     
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe5 29decfc6-ba73-417a-b616-f1b97b855077   swap                                     
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe6 a2e8a6fb-cc85-4a93-aef0-a0f665d1685e   ext4                                     
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe4: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bgeadggheg_WD750GBx2Stripe
isw_bgeadggheg_WD750GBx2Stripe1
isw_bgeadggheg_WD750GBx2Stripe2
isw_bgeadggheg_WD750GBx2Stripe3
isw_bgeadggheg_WD750GBx2Stripe5
isw_bgeadggheg_WD750GBx2Stripe6

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe6 /                        ext4       (rw,errors=remount-ro,commit=0)


================== isw_bgeadggheg_WD750GBx2Stripe1/boot.ini: ==================

; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe 
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader 
 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows XP on D:\" /fastdetect 

============= isw_bgeadggheg_WD750GBx2Stripe6/boot/grub/grub.cfg: =============

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
set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
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
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
    search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a2e8a6fb-cc85-4a93-aef0-a0f665d1685e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
    search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a2e8a6fb-cc85-4a93-aef0-a0f665d1685e ro single 
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
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
    search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos6)'
    search --no-floppy --fs-uuid --set a2e8a6fb-cc85-4a93-aef0-a0f665d1685e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe1)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos1)'
    search --no-floppy --fs-uuid --set 3ab81597b81552ad
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe2)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe,msdos2)'
    search --no-floppy --fs-uuid --set b486227786223a6e
    drivemap -s (hd0) ${root}
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

================== isw_bgeadggheg_WD750GBx2Stripe6/etc/fstab: ==================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe6 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bgeadggheg_WD750GBx2Stripe5 none            swap    sw              0       0

====== isw_bgeadggheg_WD750GBx2Stripe6: Location of files loaded by Grub: ======


1454.8GB: boot/grub/core.img
1461.2GB: boot/grub/grub.cfg
1446.7GB: boot/initrd.img-2.6.35-22-generic
1454.8GB: boot/vmlinuz-2.6.35-22-generic
1446.7GB: initrd.img
1454.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on isw_bgeadggheg_WD750GBx2Stripe4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe4: No such file or directory
hexdump: /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe4: No such file or directory
[/PHP]

---

### Post by protivakid on 2010-10-25
bump

---

### Post by ronparent on 2010-10-25
In a raid 0 setup where the boot is on the raid, the boot loader has to be also on the raid. At this point you should try a grub reinstall to set it up per this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

For your case as shown in 'results' and using a live cd you would first open a terminal and mount the partition you installed to:
> sudo mount /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe6 /mnt
Then you run the install:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_bgeadggheg_WD750GBx2Stripe
This works most of the time. If not you will probably have to resort to one of the chroot methods also outlined in the above reference. Post how you make out. Good luck.

---

### Post by psusi on 2010-10-25
It looks like EasyBCD is replacing grub with grub4dos, and doing so wrongly.  The solution is simple: don't use EasyBCD.  Why do you want to complicate things with a third boot loader to boot two operating systems anyhow?  Just stick with the standard grub2 install and chain load windows.

---

### Post by protivakid on 2010-11-02
I just wanted to add that I never got this working with EasyBCD. I ended up just  using all primary partitions for each os (7 XP Ubuntu) and grub2 because  grub2 wasn't working when Ubuntu was on an extended partition on the 2  raid0 drives. Also I had to hide each windows drive from the other while  installing each os or ortherwise grub2 would throw an error when trying  to boot the last installed ntfs os.

Also I am using Ubuntu 10.04.1 64 because on my Asus P6T Deluxe V2 1366 i7 board Ubuntu 10.10 would freeze every 20 minutes or so including during the install requiring a hard reboot. 10.04.1 has given me no such problem and has been running well for a week now.

---

