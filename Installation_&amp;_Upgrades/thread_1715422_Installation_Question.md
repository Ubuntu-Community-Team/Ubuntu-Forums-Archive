---
title: "Installation Question"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by acmariner99 on 2011-03-26
I am installing version 10.10. Does it matter where I install the bootloader? There are selections for the entire device and each partition. I have Windows 7 on /dev/sda1 and Ubuntu on /dev/sda3. The last time I tried this I couldn't go back to Windows 7 even after using the grub-update commands.

---

### Post by dacoolio on 2011-03-26
I'd say go for the entire device. If I remember correctly, doesn't a bootloader install in the first part of the drive? So in that case I wouldn't think it can be installed for individual partitions. I would wait for more advice though, since I'm not 100% sure.

---

### Post by Hedgehog1 on 2011-03-26
Please install the boot loader on **/dev/sda**, not the sda1 or sda4.

dacoolio - you have good instincts!  In nearly all cases you do want the whole device. :D

***The Hedge***

:KS

---

### Post by acmariner99 on 2011-03-27
I jumped the gun. I installed grub to /dev/sda1 (Windows 7) -- and now when I boot Windows 7 it just goes back to the grub screen. How do I fix this? I tried doing

sudo grub-install /dev/sda and
sudo update-grub

but it didn't fix the problem. How do I reconfigure the mbr? Noob mistake and I should have noticed it.

---

### Post by acmariner99 on 2011-03-27
sudo fdisk -l prints this:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27991   224830432+   7  HPFS/NTFS
/dev/sda2           38189       38912     5808128    7  HPFS/NTFS
/dev/sda3           27991       37946    79967232   83  Linux
/dev/sda4           37946       38189     1951744   82  Linux swap / Solaris

---

### Post by Hedgehog1 on 2011-03-27
Reinstall Grub on Hard Drive from Live CD

Please boot off your LiveCD/LiveUSB, select TRY

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a3** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

This should fix you right up!

***The Hedge***

:KS

---

### Post by acmariner99 on 2011-03-27
I followed your instructions. I can boot into Ubuntu, but now when I boot into Windows 7 I just get a blank screen with a flashing _ at the top left corner of the screen. Will a grub-update fix this or is my Windows 7 bootloader trashed? Any other suggestions on how to fix this?

---

### Post by acmariner99 on 2011-03-27
I used the bootscript to get an idea of what is going on, here it is:[HTML]                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 550595408 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   449,660,927   449,660,865   7 HPFS/NTFS
/dev/sda2         613,500,928   625,117,183    11,616,256   7 HPFS/NTFS
/dev/sda3         449,660,928   609,595,391   159,934,464  83 Linux
/dev/sda4         609,595,392   613,498,879     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        76C87503C874C343                       ntfs                                     
/dev/sda2        2EA877A2A877676D                       ntfs       PRESARIO_RP                   
/dev/sda3        74d11b5a-e0a0-4230-9b56-f9b4e30b4865   ext4                                     
/dev/sda4        37a45ebd-6b13-4428-9e0f-b9259f6f9a87   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/76C87503C874C343  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=74d11b5a-e0a0-4230-9b56-f9b4e30b4865 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=74d11b5a-e0a0-4230-9b56-f9b4e30b4865 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 74d11b5a-e0a0-4230-9b56-f9b4e30b4865
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 76c87503c874c343
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2ea877a2a877676d
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=74d11b5a-e0a0-4230-9b56-f9b4e30b4865 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=37a45ebd-6b13-4428-9e0f-b9259f6f9a87 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 281.9GB: boot/grub/core.img
 281.9GB: boot/grub/grub.cfg
 310.4GB: boot/initrd.img-2.6.35-22-generic
 230.6GB: boot/vmlinuz-2.6.35-22-generic
 310.4GB: initrd.img
 230.6GB: vmlinuz[/HTML]

---

### Post by Hedgehog1 on 2011-03-27
> **acmariner99 said:**
> I followed your instructions. I can boot into Ubuntu, but now when I boot into Windows 7 I just get a blank screen with a flashing _ at the top left corner of the screen. Will a grub-update fix this or is my Windows 7 bootloader trashed? Any other suggestions on how to fix this?

Hello again.

Because you loaded into sda1 - That hammers the Windows BOOT.

It means you have two steps: FIXMBR, and then repeat the grub-install.

To get your PC to boot directly into Windows again:

You need a Windows 7 / Vista emergency repair disk.  If you don't have a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

To Reinstall Grub on Hard Drive from Live CD

Please boot off your LiveCD/LiveUSB, select TRY

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a3** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

This should fix **both** boots this time!

***The Hedge***

:KS

---

### Post by acmariner99 on 2011-03-27
Success! I found this thread that said the same thing: [http://ubuntuforums.org/showthread.php?t=1423998]("http://ubuntuforums.org/showthread.php?t=1423998") The BootRec.exe /FixMbr fixed the Windows 7 boot problem and the instructions posted for loading grub into /dev/sda allowed Ubuntu and Win 7 to work. 

This thread is SOLVED. Thanks for the help!

---

### Post by Hedgehog1 on 2011-03-27
Glad you are operational again!

Hey - don't forget to update your profile!  You are running 10.10 now!

***The Hedge***

:KS

---

