---
title: "Boot MGR missing Ubuntu"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by elzipa on 2011-11-03
[FONT=Courier New][/FONT]
[FONT=Courier New]Hello,[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]I recently reinstalled Ubuntu 11.10 in my Macbook Pro. I used to have 3 systems working OS X, Win 7 and Ubuntu 11.10 however I started having booting issues so I decided to fix Win MBR and then could not get Ubuntu to boot so I reinstalled after different attemps to reinstall and fix grub.[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Bootom line I reinstalled UBuntu 11.10 and does not boot and get the message Boot MGR missing.[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]I would appreciate if anybody can help solve this problem. The partition report is bellow[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]SDA1 is OS X[/FONT]
[FONT=Courier New]SDA2 is shared NTFS partition[/FONT]
[FONT=Courier New]SDA3 is Win7 [/FONT]
[FONT=Courier New]SDA4 is Ubuntu system[/FONT]
[FONT=Courier New]SDA5 is SWAP [/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]*** Report for internal hard disk ***[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Current GPT partition table:[/FONT]
[FONT=Courier New] #      Start LBA      End LBA  Type[/FONT]
[FONT=Courier New] 1         409640    136405135  Mac OS X HFS+[/FONT]
[FONT=Courier New] 2      136669184    800729087  Basic Data[/FONT]
[FONT=Courier New] 3      800729088    898383871  Basic Data[/FONT]
[FONT=Courier New] 4      898383872    964204543  Basic Data[/FONT]
[FONT=Courier New] 5      964204544    976773119  Linux Swap[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Current MBR partition table:[/FONT]
[FONT=Courier New] # A    Start LBA      End LBA  Type[/FONT]
[FONT=Courier New] 1              1       409639  ee  EFI Protective[/FONT]
[FONT=Courier New] 2         409640    136405135  af  Mac OS X HFS+[/FONT]
[FONT=Courier New] 3      136669184    800729087  07  NTFS/HPFS[/FONT]
[FONT=Courier New] 4 *    800729088    898383871  07  NTFS/HPFS[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]MBR contents:[/FONT]
[FONT=Courier New] Boot Code: Unknown, but bootable[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Partition at LBA 409640:[/FONT]
[FONT=Courier New] Boot Code: None[/FONT]
[FONT=Courier New] File System: HFS Extended (HFS+)[/FONT]
[FONT=Courier New] Listed in GPT as partition 1, type Mac OS X HFS+  Listed in MBR as partition 2, type af  Mac OS X HFS+[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Partition at LBA 136669184:[/FONT]
[FONT=Courier New] Boot Code: Windows BOOTMGR (Vista)[/FONT]
[FONT=Courier New] File System: NTFS[/FONT]
[FONT=Courier New] Listed in GPT as partition 2, type Basic Data  Listed in MBR as partition 3, type 07  NTFS/HPFS[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Partition at LBA 800729088:[/FONT]
[FONT=Courier New] Boot Code: Windows BOOTMGR (Vista)[/FONT]
[FONT=Courier New] File System: NTFS[/FONT]
[FONT=Courier New] Listed in GPT as partition 3, type Basic Data  Listed in MBR as partition 4, type 07  NTFS/HPFS, active[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Partition at LBA 898383872:[/FONT]
[FONT=Courier New] Boot Code: GRUB[/FONT]
[FONT=Courier New] File System: ext4[/FONT]
[FONT=Courier New] Listed in GPT as partition 4, type Basic Data[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]Partition at LBA 964204544:[/FONT]
[FONT=Courier New] Boot Code: None[/FONT]
[FONT=Courier New] File System: Unknown[/FONT]
[FONT=Courier New] Listed in GPT as partition 5, type Linux Swap[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Arial] [/FONT]

---

### Post by darkod on 2011-11-03
bootmgr is part of windows booting, not ubuntu. Does this message appear when selecting to boot ubuntu?

For more detailed info, run the bootinfoscript as explained here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Attach the resulting results.txt file (or if you are pasting the content include it in code tags for easier reading.

---

### Post by elzipa on 2011-11-03
Yes, that is correct; I try starting Ubuntu the the linux logo shows up for a few seconds and after I get that Boot MGR missing then it asks you to restart.

---

### Post by elzipa on 2011-11-03
Here is the result of boot_info_script.sh:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda4 
                       and looks at sector 940765912 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   136,405,135   135,995,496  af HFS / HFS+
/dev/sda3         136,669,184   800,729,087   664,059,904   7 NTFS / exFAT / HPFS
/dev/sda4    *    800,729,088   898,383,871    97,654,784   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1         409,640   136,405,135   135,995,496 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda2     136,669,184   800,729,087   664,059,904 Data partition (Windows/Linux)
/dev/sda3     800,729,088   898,383,871    97,654,784 Data partition (Windows/Linux)
/dev/sda4     898,383,872   964,204,543    65,820,672 Data partition (Windows/Linux)
/dev/sda5     964,204,544   976,773,119    12,568,576 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        709efb54-f38b-3de9-84bb-2f9259087a42   hfsplus    Macintosh HD
/dev/sda2        0E4E1AF64E1AD675                       ntfs       SHARE
/dev/sda3        B0BCF402BCF3C140                       ntfs       WINDOWS
/dev/sda4        232874d0-f867-4b0b-aa0a-87309c69d066   ext4       
/dev/sda5        6f962f51-c325-4e33-a07e-9039737dd04c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt4)'
  search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=232874d0-f867-4b0b-aa0a-87309c69d066 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=232874d0-f867-4b0b-aa0a-87309c69d066 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 232874d0-f867-4b0b-aa0a-87309c69d066
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda1)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root b8fa4390806fa1f6
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b8fa4390806fa1f6 uuid
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
menuentry "Mac OS X (64-bit) (on /dev/sda1)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root b8fa4390806fa1f6
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b8fa4390806fa1f6 uuid
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
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root B0BCF402BCF3C140
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=232874d0-f867-4b0b-aa0a-87309c69d066 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f962f51-c325-4e33-a07e-9039737dd04c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


---

### Post by darkod on 2011-11-04
In the original installation which bootloader were you using?

The script might be wrong, but it says you have windows bootloader on the MBR of the disk. I wonder if that can boot your OS X at all. And since the disk is GPT it might not be relevant anyway, I have no experience with GPT disks.

The grub2 is installed onto the ubuntu root partition, don't know if you planned it this way.

So what was the original setup and how were you booting the operating systems?

---

### Post by elzipa on 2011-11-04
Thanks for your response...
 
I can now boot in both OS X and Wind 7 wiith out a problem... I am using rEFIt
 
yes, I wanted to have the Grub2 in the same Ubunto system sda4.
 
All happened because I wanted windows to boot without going trough Ubunto Grub... so I decided to repair boot for win 7 using Windows disk and then after that I could not boot Ubuntu... Even after reinstalling it a couple of times 
 
Any way I can fix that...

---

### Post by darkod on 2011-11-04
Under the assumption that grub2 is correctly installed onto the sda4 partition and can boot ubuntu, you need to configure your bootloader (refit) to "call" grub2 from sda4 when ever you select to boot ubuntu. Popularly called chainloading.

That's the missing step, that refit calls grub2. At least it seems like that.

---

### Post by elzipa on 2011-11-05
Thanks Darkod!
How do I go about it pl... where do I do it and how
Much appreciated

---

### Post by darkod on 2011-11-05
Sorry, but I have no idea how that goes. I never chainload, but in this case your have OS X too so I don't know if there is a different way apart from refit.

Try googling around for refit procedures, visit some of their (is it Macs) forums, etc. If you keep using this type of boot, you need to investigate and learn how it goes.

---

### Post by elzipa on 2011-11-06
All right... I re-installed Ubuntu 11.10 and set Grub in sda. Bottom line software started well.

OS X is booting well with the rEFIt boot-loader icon
Windows booting through rEFIt however it has to boot trough GRUB all the time
Ubuntu is booting well

Only situation I do not like much is booting Windows through GRUB and rEFIt

---

