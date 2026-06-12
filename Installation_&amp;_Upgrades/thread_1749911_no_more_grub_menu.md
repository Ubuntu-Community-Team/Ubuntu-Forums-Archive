---
title: "no more grub menu"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by itfool on 2011-05-05
Hello all,
i installed ubuntu 10.10 to my external HDD and it works. Recently, i reinstalled windows therefore, there is no more grub menu when my computer boots. I tried to reinstall grub to my external HDD but it doesn't work. Any suggestion or help would be much appreciated.

---

### Post by tommcd on 2011-05-05
How did you try to reinstall grub2? Are you sure you tried to reinstall grub2 to the MBR of the external drive?
Here is a tutorial on reinstalling grub2 from the Ubuntu live CD: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Since you are installing grub2 to the external drive, that would probably be */dev/sdb*, and not */dev/sda* as it says in that tutorial.
It would be useful if you could run the bootinfo script from the live CD and post the results here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by itfool on 2011-05-05
how could i run the bootinfo script ? can you tell me.

---

### Post by lechien73 on 2011-05-05
The procedure is documented at the link in Tom's response. Briefly, though:

[LIST=1]
[*]Boot into Ubuntu from a LiveCD
[*]Go to [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
[*]Follow the instructions there for downloading and running the script.
[*]Copy the contents of the RESULTS.TXT file.
[*]Create a new reply here, click the **#** button on the toolbar, and paste the RESULTS.TXT between the [CODE] tags
[/LIST]

---

### Post by itfool on 2011-05-09
Here is my code.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   205,301,759   205,094,912   7 HPFS/NTFS
/dev/sda3         205,301,760   625,139,711   419,837,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,768,064   976,766,017   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       8d2a8bb9-90de-4349-baae-be0c0f793818   ext4                                     
/dev/sda1        16767E8E767E6E7D                       ntfs       System Reserved               
/dev/sda2        E8A48C5EA48C315C                       ntfs                                     
/dev/sda3        A40A5F690A5F380E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38A8C7D6A8C790B4                       ntfs       Gyi Hein                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/Gyi Hein          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A40A5F690A5F380E loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A40A5F690A5F380E loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 16767E8E767E6E7D
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


  17.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.38-8-generic
  13.1GB: boot/vmlinuz-2.6.38-8-generic
    .7GB: initrd.img
  13.1GB: vmlinuz

======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A40A5F690A5F380E loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root A40A5F690A5F380E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A40A5F690A5F380E loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 16767E8E767E6E7D
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

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


  17.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.38-8-generic
  13.1GB: boot/vmlinuz-2.6.38-8-generic
    .7GB: initrd.img
  13.1GB: vmlinuz
```

---

### Post by ThatCoolGuy220 on 2011-05-09
@itfool

you mean it boots automatically on any O.S

or when you boot all you see is a black screen?

---

### Post by wilee-nilee on 2011-05-09
> **ThatCoolGuy220 said:**
> @itfool

you mean it boots automatically on any O.S

or when you boot all you see is a black screen?

Unless you are a wubi guru I would let them deal with this it is a bit complicated, just saying.;)

---

### Post by garvinrick4 on 2011-05-09
Your installs are of WUBI Ubuntu which is a folder inside of Windows. So go into
your windows install and go to Add and remove programs and remove Ubuntu from
there: You have on both internal and external drives a wubi install.
##Get your Windows boot back in order and start over in other words.
 
Link is here to install your windows boot loader only two commands quite simple.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
 
##There is a Wubi install and a partition install of Ubuntu, Wubi is a folder right next to
Users in C: Drive can also open that folder and have a uninstall there.
 
#Here is a Wubi thread if you want to try to straighten out installs.
Rubi1200 is only user I know would take a shot at your Wubi installs. Always use Wubi in your Title so Wubi users can see your thread.
[[wubi] Wubi megathread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by ThatCoolGuy220 on 2011-05-09
@wilee-nilee


You are right bro better not get my hands on the fire....

---

### Post by wilee-nilee on 2011-05-09
> **ThatCoolGuy220 said:**
> @wilee-nilee


You are right bro better not get my hands on the fire....

That is one messed up wubi, I wouldn't touch that and I'm slightly familiar with it. garvinrick4 is correct for removal I think, but the ms bootloader is in the mbr, they should be able to boot the windows. You just never know though without confirmation, I have seen scripts that showed none of the relative files and the user had a working setup.

You never know though the wubi may be recoverable but  needs the right forum helper.

---

### Post by itfool on 2011-05-09
hello all,
all I just want to do is to get back my ubuntu 10.10 installed by using wubi in external HDD. Before I reinstalled my windows, it's ok and no problem using/boot from external one. Yup, I installed 11.04 a few days ago with wubi again coz it's new released and I wanna try. But I don't like 11.04's features and cannot use it well. Moreover, the one in external HDD is already done many installed packages of my likes and customized. So so, I seriously want to get it back. :(

---

### Post by bcbc on 2011-05-10
Both wubi installs shown in the bootinfoscript are fresh 11.04 installs. If you have the backup root.disk from your 10.10 install it's possible to get it booting again... but it's not shown anywhere in those results.

In fact it looks like the wubi on /dev/sdb1 was copied from the one on /dev/sda3 - so they appear identical (as far as I can tell from the bootinfoscript).

---

### Post by tommcd on 2011-05-11
> **itfool said:**
> hello all,
all I just want to do is to get back my ubuntu 10.10 installed by using wubi ...
Wubi is only meant to try out Ubuntu. It was never intended for long term installations. See this interview with the Wubi developer for some background: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
If you have been using Ubuntu for a while, and want to continue using it, then you would be better off just doing a real install to a dedicated linux partition on your hard drive. You can install Ubuntu to the external drive if you wish.

---

