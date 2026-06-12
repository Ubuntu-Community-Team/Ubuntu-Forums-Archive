---
title: "Grub doesn't show up at startup"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Voidzm on 2011-05-07
Hi,

I have a dual-boot setup with Windows 7 and Ubuntu 11.04. Each OS is installed on a separate partition of one hard drive. I read that installing Windows after installing Ubuntu wipes out Grub, so I made sure to install Windows first. Unfortunately, after completing the Ubuntu install and rebooting, I see no sign of the Grub menu. I followed several sets of instructions for reinstalling Grub, and after running grub-update, it appears that Windows 7 was added to Grub, and after examining the grub.cfg file, it appeared that that was the case. Despite appearing to be installed perfectly once inside Ubuntu, Grub doesn't show anything at startup.

No matter what I try, I can't seem to make Grub appear, and now I can't get back to Windows 7. Am I missing something, or should I try a different bootloader?

---

### Post by drs305 on 2011-05-07
Voidzm,

Welcome to Ubuntu and the Ubuntu forums.

Have you tried holding down the SHIFT key during boot to see if the menu appears?

If you run the boot info script found at the following link and post the contents of RESULTS.txt we can take a look at your boot file status.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Voidzm on 2011-05-07
I did try pressing Shift during startup, and it simply said "Grub is loading..." for about a second, and then went to a black screen and from there to Ubuntu.

I'll run that script as soon as I can and get back to you ;)

---

### Post by drs305 on 2011-05-07
> **Voidzm said:**
> I did try pressing Shift during startup, and it simply said "Grub is loading..." for about a second, and then went to a black screen and from there to Ubuntu.

I'll run that script as soon as I can and get back to you ;)

One thing you could try is to wait until you think the system is starting to boot and then press CTRL-ALT-DEL. This should interrupt the boot and induce a 'recordfail' event. That normally would make Grub 2 display the menu on the next boot and await user input. 

The RESULTS.txt will still be good to see.

---

### Post by MAFoElffen on 2011-05-07
> **Voidzm said:**
> I did try pressing Shift during startup, and it simply said "Grub is loading..." for about a second, and then went to a black screen and from there to Ubuntu.

I'll run that script as soon as I can and get back to you ;)
Like "drs305" said then... If you can edit "files" via a LiveCD,,,
  Commenting out /etc/default/grub/ line  
      ```

         # GRUB_HIDDEN_TIMEOUT=00

```

sometimes helps with that...

---

### Post by Voidzm on 2011-05-08
I tried pressing CTRL-ALT-DEL at startup, and that seemed to immediately restart the boot. Even after changing the timeout_hidden line and running update-grub, I still see no change during boot. Pressing Shift shows the loading message for a second, and then in either case Ubuntu loads.

Here is the boot_info_script output:
```
***************Boot Info Script 0.55 ***dated February 15th, 2010 *******************

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

***File system: ******ntfs
***Boot sector type: *Windows Vista/7
***Boot sector info: *No errors found in the Boot Parameter Block.
***Operating System: *
***Boot files/dirs: **/bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

***File system: ******ntfs
***Boot sector type: *Windows Vista/7
***Boot sector info: *No errors found in the Boot Parameter Block.
***Operating System: *Windows 7
***Boot files/dirs: **/Windows/System32/winload.exe

sda3: _________________________________________________________________________

***File system: ******Extended Partition
***Boot sector type: *-
***Boot sector info: *

sda5: _________________________________________________________________________

***File system: ******ext4
***Boot sector type: *-
***Boot sector info: *
***Operating System: *Ubuntu 11.04
***Boot files/dirs: **/boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

***File system: ******swap
***Boot sector type: *-
***Boot sector info: *

sda4: _________________________________________________________________________

***File system: ******ntfs
***Boot sector type: *Windows Vista/7
***Boot sector info: *No errors found in the Boot Parameter Block.
***Operating System: *
***Boot files/dirs: **

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition *Boot ********Start **********End *********Size *Id System

/dev/sda1 **** *********2,048 ******206,847 ******204,800 **7 HPFS/NTFS
/dev/sda2 ************206,848 ***58,593,279 ***58,386,432 **7 HPFS/NTFS
/dev/sda3 *********58,595,326 ***97,654,783 ***39,059,458 **5 Extended
/dev/sda5 *********58,595,328 ***96,606,207 ***38,010,880 *83 Linux
/dev/sda6 *********96,608,256 ***97,654,783 ****1,046,528 *82 Linux swap / Solaris
/dev/sda4 *********97,654,784 **234,491,903 **136,837,120 **7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device **********UUID **********************************TYPE ******LABEL ************************

/dev/sda1 *******3E88879A88874EF9 **********************ntfs ******System Reserved **************
/dev/sda2 *******2C3C910B3C90D166 **********************ntfs ************************************
/dev/sda3: PTTYPE="dos" 
/dev/sda4 *******75E1F45F20454C57 **********************ntfs ******Storage **********************
/dev/sda5 *******c7a39c33-2b34-4195-bcc5-fa3e5ee1090b **ext4 ************************************
/dev/sda6 *******9dda919b-c7ff-4813-88a8-f171ec5585a6 **swap ************************************
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev *output: ===========================

Device **********Mount_Point *************Type ******Options

/dev/sda5 *******/ ***********************ext4 ******(rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
*set have_grubenv=true
*load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
*set saved_entry="${prev_saved_entry}"
*save_env saved_entry
*set prev_saved_entry=
*save_env prev_saved_entry
*set boot_once=true
fi

function savedefault {
*if [ -z "${boot_once}" ]; then
***saved_entry="${chosen}"
***save_env saved_entry
*fi
}

function recordfail {
*set recordfail=1
*if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
*insmod vbe
*insmod vga
*insmod video_bochs
*insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
if loadfont /usr/share/grub/unicode.pf2 ; then
*set gfxmode=auto
*load_video
*insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
*set timeout=-1
else
*set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
*clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
*if [ -e ${prefix}/gfxblacklist.txt ]; then
***if hwmatch ${prefix}/gfxblacklist.txt 3; then
*****if [ ${match} = 0 ]; then
*******set linux_gfx_mode=keep
*****else
*******set linux_gfx_mode=text
*****fi
***else
*****set linux_gfx_mode=text
***fi
*else
***set linux_gfx_mode=keep
*fi
else
*set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
* *recordfail
* *set gfxpayload=$linux_gfx_mode
* *insmod part_msdos
* *insmod ext2
* *set root='(/dev/sda,msdos5)'
* *search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
* *linux * */boot/vmlinuz-2.6.38-8-generic root=UUID=c7a39c33-2b34-4195-bcc5-fa3e5ee1090b ro **quiet splash vt.handoff=7
* *initrd * */boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
* *recordfail
* *set gfxpayload=$linux_gfx_mode
* *insmod part_msdos
* *insmod ext2
* *set root='(/dev/sda,msdos5)'
* *search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
* *echo * *'Loading Linux 2.6.38-8-generic ...'
* *linux * */boot/vmlinuz-2.6.38-8-generic root=UUID=c7a39c33-2b34-4195-bcc5-fa3e5ee1090b ro single 
* *echo * *'Loading initial ramdisk ...'
* *initrd * */boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
* *insmod part_msdos
* *insmod ext2
* *set root='(/dev/sda,msdos5)'
* *search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
* *linux16 * */boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
* *insmod part_msdos
* *insmod ext2
* *set root='(/dev/sda,msdos5)'
* *search --no-floppy --fs-uuid --set=root c7a39c33-2b34-4195-bcc5-fa3e5ee1090b
* *linux16 * */boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
* *insmod part_msdos
* *insmod ntfs
* *set root='(/dev/sda,msdos1)'
* *search --no-floppy --fs-uuid --set=root 3E88879A88874EF9
* *chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. *Simply type the
# menu entries you want to add after this comment. *Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f *$prefix/custom.cfg ]; then
*source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> **<type> *<options> ******<dump> *<pass>
proc ***********/proc **********proc ***nodev,noexec,nosuid 0 ******0
# / was on /dev/sda5 during installation
UUID=c7a39c33-2b34-4195-bcc5-fa3e5ee1090b / **************ext4 ***errors=remount-ro 0 ******1
# swap was on /dev/sda6 during installation
UUID=9dda919b-c7ff-4813-88a8-f171ec5585a6 none ***********swap ***sw *************0 ******0
/dev/fd0 *******/media/floppy0 *auto ***rw,user,noauto,exec,utf8 0 ******0

=================== sda5: Location of files loaded by Grub: ===================


*47.6GB: boot/grub/core.img
*47.6GB: boot/grub/grub.cfg
*31.0GB: boot/initrd.img-2.6.38-8-generic
*47.6GB: boot/vmlinuz-2.6.38-8-generic
*31.0GB: initrd.img
*47.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by kansasnoob on 2011-05-08
Please look at this post:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Note: ignore the rest of the thread! I only used that thread as a place-holder for that post so I wouldn't have to retype everything every time.

Also, if you can boot Ubuntu now there's no real need to create the SGD2 disc as described in step #1 (although it's a great tool to have around), and your problem is different than that described in step #6.

I'm not real sure what's going on yet but there seem to be three somewhat different problems with Natty's grub2:

1: Won't boot anything.
2: Produces an out-of-range monitor error during boot.
3: Refuses to display the grub menu at all.

I don't know if the three are related or not :confused:

---

### Post by Voidzm on 2011-05-08
Kansasnoob,

I was able to get Grub working properly thanks to that guide of yours. Thanks a lot to all of you for your help!

---

### Post by chrismonster13 on 2011-05-13
> **kansasnoob said:**
> Please look at this post:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Note: ignore the rest of the thread! I only used that thread as a place-holder for that post so I wouldn't have to retype everything every time.

Also, if you can boot Ubuntu now there's no real need to create the SGD2 disc as described in step #1 (although it's a great tool to have around), and your problem is different than that described in step #6.

I'm not real sure what's going on yet but there seem to be three somewhat different problems with Natty's grub2:

1: Won't boot anything.
2: Produces an out-of-range monitor error during boot.
3: Refuses to display the grub menu at all.

I don't know if the three are related or not :confused:
Just wanted to say THANK YOU for that great thread. Now I can use all of the OS's installed on my system. I'm still having problems with my splash screen being all ugly though :P

---

