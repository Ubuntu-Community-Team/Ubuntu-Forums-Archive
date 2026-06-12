---
title: "Base OS installation problems"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by msantarc on 2010-09-28
Let me start by saying that I'm semi new to the UNIX world. I've been a windows semi literate person for as long as it's been out, so I know my way around a computer, but I'm stuck.
I have an AMD chiped PC that has Windows XP on it. When I installed it I left room for and later added a UNIX partition (PCLinux) everything worked fine. (I have my monitor and, keyboard and mouse on a CablesToGo KVM switch). I could boot to windows or UNIX. no problems.
Then a friend suggested that I try UBUNTU Studio (ubuntu 10.04 LTS) for some recording that I'm doing. I installed it, but there was limited space available on my drive. It installed ok, (My KVM switch worked) but occasionally my monitor would say that it was no longer receiveing input so it went to sleep, and noting I did could wake it. (had to reboot.
Ok that's all the set up for my real problem.
I decided that my problems might be related to the fact that UBUNTU Studio didn't have sufficient disk space to do it's thing, so I decided to delete the old PCLinux partition, the new UBUNTU partition and start over. 
Now:
- I can't boot to Windows (The system just hangs part of the way through. (But I CAN access the Windows partition and files from within un\buntu).
- Within UBUNTU I can no longer use any USB devices (I'm using a hard wired keyboard and mouse right now (UGH!)
- ANd I still have my original problem where the monitor can no longer see anything from the PC and basically shuts down.

Do you have any suggestions?
My priorities are:
1) Get Windows working again
2) Get the USB ports working
3) Fix the monitor problem. (this may actually be  issue #2, but I cant decide)

Thanks for anything you can provide.
Mike

---

### Post by oldfred on 2010-09-28
To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Your KVM may contribute to issues.

Unix is not Linux. Linux is a work alike, but they are not totally compatible.

---

### Post by msantarc on 2010-09-28
Here's teh info I got when I ran the boot_info_script055.sh file:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,974   320,172,031    51,757,058   5 Extended
/dev/sda5         268,414,976   317,939,711    49,524,736  83 Linux
/dev/sda6         317,941,760   320,172,031     2,230,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2E8C47348C46F63D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cead5024-3263-48e5-b843-73df538d3b15   ext4                                     
/dev/sda6        b7c58cb4-00f8-421c-8834-1701f059093d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/2E8C47348C46F63D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
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
search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cead5024-3263-48e5-b843-73df538d3b15 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cead5024-3263-48e5-b843-73df538d3b15 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cead5024-3263-48e5-b843-73df538d3b15
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2e8c47348c46f63d
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=cead5024-3263-48e5-b843-73df538d3b15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b7c58cb4-00f8-421c-8834-1701f059093d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 161.2GB: boot/grub/grub.cfg
 146.2GB: boot/initrd.img-2.6.32-21-generic
 146.2GB: boot/vmlinuz-2.6.32-21-generic
 146.2GB: initrd.img
 146.2GB: vmlinuz

---

### Post by oldfred on 2010-09-28
If grub is transferring to the windows boot loader it has done its job and windows then has an issue. Often after resizing a NTFS partition windows will want to do a chkdsk.

You can reinstall the windows boot loader to test that by running fixboot from a windows repair cd or ::
Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you do install a windows boot loader you will have to reinstall grub2 to the MBR to boot Ubuntu:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

What video card do you have. My monitor would go to sleep until I made some adjustments.
I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

