---
title: "Grub choices are messed up"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by frito on 2011-04-30
Hi I just installed ubuntu and I was planning to dual-boot into another distro (which i've been doing for a long time with many flavors of linux). 
However somehow the ubuntu grub choices result in some sort of kernel panic with my other distros.

Also if i rewrite grub using my other distro, the ubuntu grub screen still comes up, like its over riding anything else i do.

I have no idea what to post but I'll take any guidance.

Help please and thankyou

---

### Post by Hedgehog1 on 2011-04-30
We need to get a look at what shape your PC is in.

Please boot off the LiveCD/LiveUSB, select 'TRY' OR boot from another of your Linux Distros, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by MAFoElffen on 2011-04-30
> **frito said:**
> Hi I just installed ubuntu and I was planning to dual-boot into another distro (which i've been doing for a long time with many flavors of linux). 
However somehow the ubuntu grub choices result in some sort of kernel panic with my other distros.

Also if i rewrite grub using my other distro, the ubuntu grub screen still comes up, like its over riding anything else i do.

I have no idea what to post but I'll take any guidance.

Help please and thankyou
It sounds like you are editing the /boot/grub/grub.cfg file, then running update-grub and overwriting your changes?

IMHO- This is what I do... I embrace GNU Grub as my primary choice. I chainload from Grub2 to legacy grub (and others). 

Use this for refrence for the current version:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

These 2 come in handy for refrence
[https://help.ubuntu.com/community/Grub2:](https://help.ubuntu.com/community/Grub2:)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

Use this as reference to dev notes from Meerkat for the geek in us:
[http://ubuntuforums.org/showthread.php?t=1590501](http://ubuntuforums.org/showthread.php?t=1590501)

I go to /etc/grub.d and I edit those files how it suit's me. my configs and installs, using the 40_custom for distro's it doesn't pick up. Then I do a update-grub to pick up the changes...

You could do some tweaks to the os-prober to fine tune, such as hiding an item from becoming an entry during an update-grub, but if you don't know what you're doing, it could just as fast, bury you!!!  

Then I make backup copies of those files and keep them in my home directory-- Because later updates tend to overwrite them.  Be prepared that this is going to be a given --> GNU Grub release 1.99~rc1 is just that, a release candidate for a proposed version that will someday go to "release" status.

---

### Post by wilee-nilee on 2011-04-30
> **Hedgehog1 said:**
> We need to get a look at what shape your PC is in.

Please boot off the LiveCD/LiveUSB, select 'TRY' OR boot from another of your Linux Distros, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***
:KS
Big, big, big +1

---

### Post by frito on 2011-05-01
When i try to load my other distro I see something come up after the "VGA= something  " line that says partition doesnt exist.

Note: While i was trying to fix this i accidentally installed grub to sda but my computer boots from sdb
Note: AS a note im actually triple booting not dual booting.

Also i have figured out an ugly way to fix this but it requires me to chain load ubuntu. However the ubuntu grub install wont let me install grub to ubuntus partition. how do you override it?


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cah.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.38.2-pclos1.a64 on a 
                       3-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    29,339,647    29,337,600  83 Linux
/dev/sdb2          29,341,694   976,768,064   947,426,371   5 Extended
/dev/sdb5         102,398,373   106,478,819     4,080,447  82 Linux swap / Solaris
/dev/sdb6         106,478,883   126,945,629    20,466,747  83 Linux
/dev/sdb7         126,945,693   208,861,064    81,915,372  83 Linux
/dev/sdb8         208,861,128   976,768,064   767,906,937   7 HPFS/NTFS
/dev/sdb9          29,341,696   102,397,951    73,056,256  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F444ADB644AD7C4C                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ab13103d-5341-4f7c-89dd-d6e83fb411b3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2559f0ce-29b7-4602-a19c-db880c48b2ca   swap                                     
/dev/sdb6        98f8de46-61b9-4b53-882f-d43998659a45   ext4                                     
/dev/sdb7        dfe51e78-c49e-46ee-b46b-d3531dc87083   ext4                                     
/dev/sdb8        746E909D6E905A26                       ntfs       Win7                          
/dev/sdb9        2d552f44-9416-4bbf-948a-c55aa90848da   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb9        /home                    ext4       (rw,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root F444ADB644AD7C4C
	chainloader +1
}
menuentry "linux (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=98f8de46-61b9-4b53-882f-d43998659a45
	initrd (hd0,5)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 failsafe
	initrd (hd0,5)/boot/initrd.img
}
menuentry "2.6.32.11-pclos2.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.32.11-pclos2.bfs BOOT_IMAGE=2.6.32.11-pclos2.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.32.11-pclos2.bfs.img
}
menuentry "2.6.33.5-pclos1.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.33.5-pclos1.bfs BOOT_IMAGE=2.6.33.5-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.33.5-pclos1.bfs.img
}
menuentry "2.6.38.2-pclos1.pae.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.pae.bfs BOOT_IMAGE=2.6.38.2-pclos1.pae.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.pae.bfs.img
}
menuentry "2.6.38.2-pclos1.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.bfs BOOT_IMAGE=2.6.38.2-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.bfs.img
}
menuentry "2.6.38.2-pclos1.a64 (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.a64 BOOT_IMAGE=2.6.38.2-pclos1.a64 root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.a64.img
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb9 during installation
UUID=2d552f44-9416-4bbf-948a-c55aa90848da /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  13.3GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.38-8-generic-pae
   1.2GB: boot/vmlinuz-2.6.38-8-generic-pae
   1.7GB: initrd.img
   1.2GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

timeout 3
color black/cyan yellow/cyan
gfxmenu (hd0,5)/boot/gfxmenu
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title Windows7
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title WindowsXP
root (hd0,0)
makeactive
chainloader +1

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 failsafe
initrd (hd0,5)/boot/initrd.img

title 2.6.32.11-pclos2.bfs
kernel (hd0,5)/boot/vmlinuz-2.6.32.11-pclos2.bfs BOOT_IMAGE=2.6.32.11-pclos2.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.32.11-pclos2.bfs.img

title 2.6.33.5-pclos1.bfs
kernel (hd0,5)/boot/vmlinuz-2.6.33.5-pclos1.bfs BOOT_IMAGE=2.6.33.5-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.33.5-pclos1.bfs.img

title 2.6.38.2-pclos1.pae.bfs
kernel (hd0,5)/boot/vmlinuz-2.6.38.2-pclos1.pae.bfs BOOT_IMAGE=2.6.38.2-pclos1.pae.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.pae.bfs.img

title 2.6.38.2-pclos1.bfs
kernel (hd0,5)/boot/vmlinuz-2.6.38.2-pclos1.bfs BOOT_IMAGE=2.6.38.2-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.bfs.img

title 2.6.38.2-pclos1.a64
kernel (hd0,5)/boot/vmlinuz-2.6.38.2-pclos1.a64 BOOT_IMAGE=2.6.38.2-pclos1.a64 root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.a64.img

=============================== sdb6/etc/fstab: ===============================

# Entry for /dev/sdb6 :
UUID=98f8de46-61b9-4b53-882f-d43998659a45 / ext4 relatime 1 1
none /dev/pts devpts defaults 0 0
tmpfs /dev/shm tmpfs defaults 0 0
# Entry for /dev/sdb7 :
UUID=dfe51e78-c49e-46ee-b46b-d3531dc87083 /home ext4 relatime 1 2
# Entry for /dev/sda1 :
#UUID=F444ADB644AD7C4C /mnt/windows ntfs-3g defaults,umask=000 0 0
#none /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca swap swap defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


  61.0GB: boot/grub/menu.lst
  61.4GB: boot/grub/stage2
  62.7GB: boot/initrd-2.6.32.11-pclos2.bfs.img
  62.7GB: boot/initrd-2.6.33.5-pclos1.bfs.img
  63.5GB: boot/initrd-2.6.38.2-pclos1.a64.img
  63.0GB: boot/initrd-2.6.38.2-pclos1.bfs.img
  63.0GB: boot/initrd-2.6.38.2-pclos1.pae.bfs.img
  63.5GB: boot/initrd.img
  62.7GB: boot/initrd.img.old
  62.3GB: boot/vmlinuz
  61.1GB: boot/vmlinuz-2.6.32.11-pclos2.bfs
  62.1GB: boot/vmlinuz-2.6.33.5-pclos1.bfs
  62.3GB: boot/vmlinuz-2.6.38.2-pclos1.a64
  62.3GB: boot/vmlinuz-2.6.38.2-pclos1.bfs
  62.3GB: boot/vmlinuz-2.6.38.2-pclos1.pae.bfs
```

---

