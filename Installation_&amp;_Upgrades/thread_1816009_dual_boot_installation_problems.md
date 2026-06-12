---
title: "dual boot installation problems"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by Rezenebe on 2011-08-01
My computer runs Windows XP from a SATA disk and Ubuntu for an IDE disk. I had a dual boot setup. I tried to upgrade to 11.04, but after a number of attempts I managed to get a Classic Mode version of 11.04. However, in the process I lost the GRUB. My machine was set to boot from the SATA disk first, but now I get this message:

GRUB loading
error: no such disk
grub rescue> _

If I set the IDE disk as the first drive to boot from Ubuntu 11.04 (in Classic Mode) is launched successfully.

As most of my work is done in Windows, I need to get my Windows back.

Can anyone help me with this. I am not very familiar with Ubuntu.

---

### Post by Frogs Hair on 2011-08-01
Hello and Welcome 

You can try running the following in the terminal ```
sudo update-grub
``` 
To run Unity in 11.04 you may need to install a proprietary graphics driver if one is offered from additional drivers.

---

### Post by Rezenebe on 2011-08-01
Thank you for your reply

I ran the command  sudo update-grub.
When I rebooted the menu appeared giving the various oprtions of Ubuntu, Mem test and my copy of Windows. I chose Windows, the screen went blank and then nothing further happened.

What should I do next?

---

### Post by oldfred on 2011-08-01
Lets see where everything is installed. Which drive do you boot from?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Rezenebe on 2011-08-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=cf3cc437-9f88-448b-8fe8-25d43445c1ed)/boot/grub on this 
    drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   157,466,623   157,464,576  83 Linux
/dev/sda2         157,468,670   160,086,015     2,617,346   5 Extended
/dev/sda5         157,468,672   160,086,015     2,617,344  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   163,846,934   163,846,872   7 NTFS / exFAT / HPFS
/dev/sdb2         163,846,935   488,392,064   324,545,130   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        773cdc68-4c77-49e8-9587-a8dbcce2d62c   ext4       
/dev/sda5        489690cf-41ff-44f2-ba25-c28b5b9b4809   swap       
/dev/sdb1        04043D75043D6B36                       ntfs       
/dev/sdb2        5030B9F930B9E65E                       ntfs       PHOTOS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=773cdc68-4c77-49e8-9587-a8dbcce2d62c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=773cdc68-4c77-49e8-9587-a8dbcce2d62c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 773cdc68-4c77-49e8-9587-a8dbcce2d62c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 04043D75043D6B36
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=773cdc68-4c77-49e8-9587-a8dbcce2d62c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=489690cf-41ff-44f2-ba25-c28b5b9b4809 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.137042999 = 43.096821760   boot/grub/core.img                             1
  38.171165466 = 40.985976832   boot/grub/grub.cfg                             1
   0.762428284 = 0.818651136    boot/initrd.img-2.6.38-8-generic               2
  40.135314941 = 43.094966272   boot/vmlinuz-2.6.38-8-generic                  1
   0.762428284 = 0.818651136    initrd.img                                     2
  40.135314941 = 43.094966272   vmlinuz                                        1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  c1 01 84 05 c3 01 80 05  cc 01 81 05 c5 01 83 05  |................|
00000010  c6 01 83 05 c5 01 7d 05  c6 01 7f 05 c9 01 87 05  |......}.........|
00000020  c7 01 83 05 cb 01 81 05  c9 01 83 05 c5 01 80 05  |................|
00000030  c8 01 83 05 c3 01 7a 05  c6 01 81 05 c4 01 7f 05  |......z.........|
00000040  c7 01 81 05 c9 01 7f 05  c6 01 7d 05 c0 01 82 05  |..........}.....|
00000050  ca 01 83 05 cc 01 83 05  c9 01 82 05 c9 01 85 05  |................|
00000060  c7 01 84 05 cb 01 85 05  ca 01 7f 05 c8 01 84 05  |................|
00000070  cb 01 83 05 c6 01 7f 05  c4 01 84 05 c3 01 81 05  |................|
00000080  c9 01 83 05 cd 01 84 05  c4 01 81 05 c8 01 81 05  |................|
00000090  ca 01 83 05 c8 01 84 05  cb 01 83 05 cc 01 86 05  |................|
000000a0  c8 01 81 05 c7 01 80 05  c7 01 82 05 c6 01 82 05  |................|
000000b0  c8 01 80 05 c4 01 81 05  be 01 80 05 c2 01 7d 05  |..............}.|
000000c0  bf 01 7d 05 c2 01 7f 05  c4 01 82 05 c4 01 84 05  |..}.............|
000000d0  c4 01 83 05 c7 01 81 05  c4 01 84 05 c4 01 81 05  |................|
000000e0  c4 01 80 05 c5 01 7e 05  c9 01 83 05 c6 01 84 05  |......~.........|
000000f0  c0 01 84 05 c4 01 80 05  c3 01 7e 05 c5 01 82 05  |..........~.....|
00000100  c4 01 80 05 c3 01 80 05  c3 01 87 05 c3 01 80 05  |................|
00000110  c0 01 7e 05 c2 01 81 05  c4 01 82 05 c4 01 7e 05  |..~...........~.|
00000120  c0 01 7d 05 c0 01 80 05  bf 01 80 05 bf 01 82 05  |..}.............|
00000130  c3 01 7f 05 c5 01 7e 05  c3 01 7e 05 c5 01 7f 05  |......~...~.....|
00000140  c7 01 83 05 c6 01 82 05  c1 01 84 05 c4 01 86 05  |................|
00000150  c4 01 87 05 c1 01 81 05  c0 01 7a 05 bd 01 7d 05  |..........z...}.|
00000160  c3 01 7d 05 c0 01 7b 05  c1 01 7e 05 c2 01 7f 05  |..}...{...~.....|
00000170  c1 01 83 05 c3 01 81 05  c4 01 7e 05 c5 01 7e 05  |..........~...~.|
00000180  c4 01 80 05 c2 01 80 05  c3 01 82 05 c1 01 7f 05  |................|
00000190  c5 01 7c 05 c4 01 7c 05  c3 01 80 05 c7 01 80 05  |..|...|.........|
000001a0  c2 01 7e 05 be 01 7c 05  c1 01 83 05 be 01 80 05  |..~...|.........|
000001b0  c2 01 80 05 c1 01 84 05  c3 01 80 05 c3 01 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 27 00 00 00  |............'...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by YesWeCan on 2011-08-01
Hi there. I'm sure oldfred will advice on the reason Grub is not booting Windows. Meanwhile, for some reason you have Grub installed to both disks MBRs. This rather defeats the benefits of having dual booting on separate disks. I think it would be better to have a standard Windows MBR on your Windows disk and Grub on your Ubuntu disk. This would enable you to independently boot into Windows if you need to (like you do now) without having to use Grub at all.

Preferably, you can do this using your Windows install CD to do a repair/fixmbr. If you don't have a Windows disk you can use a linux program called lilo to install a Windows-compatible MBR code.
Boot from live CD
[COLOR="Navy"]sudo fdisk -l[/COLOR]  to double-check the disk name of your Windows disk.
[COLOR="Navy"]sudo apt-get install lilo[/COLOR]
[COLOR="Navy"]sudo lilo -M /dev/sdb mbr[/COLOR]  assuming your Windows disk is sdb

---

### Post by oldfred on 2011-08-01
It looks like you changed drives around. Windows thinks it is in sda rdisk(0) per boot.ini and Ubuntu says it is in sdb, but looks for UUID and should boot if you boot from sda or the 82GB drive.

I agree with YesWeCan on installing a windows boot loader, but would suggest swapping drive order, if thats what you changed. Then run windows fixes to reinstall windows boot loader. My drive order is controlled by SATA port order on motherboard, not BIOS or any software. Not sure if some BIOS can change order, but with SATA you can change boot order.

---

### Post by surajrajpurohit on 2011-08-01
my friend,
you hve win xp in ur IDE drive and Ubuntu in ur SATA drive...
the problem occured when u updated ur ubuntu...it has updated the grub n saved in IDE which is not it's correct place.

u can do 1 thing.....
open ur ubuntu..den search the gnome file in IDE which got saved...and remove those file.....it might work...

---

### Post by Rezenebe on 2011-08-02
Thank you for your help.
I tried using a Windows CD to repair the Windows MBR but this did not work. So I set the SATA drive (the one with Windows XP) to boot before the IDE drive (the one with Ubuntu). I followed the instructions that YesWeCan gave me making use of lilo and now my computer boots into Windows. I am so pleased!

If I set the IDE drive to boot before the SATA Ubuntu does not load. I get the message: ```
Error loading operating system
```
Can I get the computer to return to be able to dual boot?

---

### Post by oldfred on 2011-08-02
Have you tried reinstalling grub to sda. Was lilo installed to sdb. And is sda still the 80GB drive?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Also to confirm which drive grub will reinstall to on updates:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Other alternative to try:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by YesWeCan on 2011-08-02
> **Rezenebe said:**
> If I set the IDE drive to boot before the SATA Ubuntu does not load. I get the message: ```
Error loading operating system
```Can I get the computer to return to be able to dual boot?
That sounds like a non-linux error message. It is odd that you were able to boot the IDE drive into Ubuntu before you used your Windows CD to fix the mbr. Maybe you now have a Windows mbr on your IDE disk.

One way to avoid this mix up while installing things is to disconnect the other disk (pull out the power plug).

As oldfred explained, you should be able to reinstall Grub to the IDE mbr and it will boot Ubuntu again. An update-grub after that will add Windows to the Grub menu.

Be careful to choose the disk names correctly or you'll end up with Grub on the SATA mbr again.

---

### Post by Rezenebe on 2011-08-06
Thank you all for your help.
I tried to reinstall Ubuntu on the IDE drive only to find that the drive is no longer functioning. Neither Windows nor the Ubuntu Live CD recognise it. I do not want to install Ubuntu on the same disc as Windows, so I am unable to proceed until I buy a new disc. And as my PC is nine years old I am reluctant to add anything further on this machine.

I am going to save a copy of this thread for future reference.

Thank you all, once again.

---

