---
title: "Removing dual-boot involving two hard drives"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by PatrickD-52761 on 2011-09-04
Hi everyone,

Here's my setup. I have two 80GB drives in my desktop, one (sda) with Windows 7 installed, and one (sdb) with Mythbuntu 11.04 installed.  IIRC, when I installed GRUB, I either had it placed on just sda, or on both drives (I honestly don't remember which way I went).  Now, I want to eliminate the Windows 7 boot, and use that drive as extra data (with the intention of eventually replacing both drives with one larger drive).

So my questions are

1. How do I determine where the GRUB loader is installed (if it's on both drives or just the one)?
2. Is this a simple case of reformatting the Windows 7 drive and then updating GRUB, or is there more to it?
3. If there's more to this, what exactly will I have to do?

I should note that this probably won't happen for a week or two. I need to sift through the Windows 7 partition and determine exactly what I may use out of it. Then, I'll have to find applications to meet the same functionality (or install them via WINE).  Also, I chose "All variants" because this could equally apply to someone who has Kubuntu, Lubuntu, Edubuntu, or even Ubuntu installed alongside Windows.

Have a great weekend, and thanks for any help :)
Patrick.

---

### Post by Hakunka-Matata on 2011-09-04
Welcome to the forums Patrick;

Download boot_info_script, install and run it.  It will generate a file named RESULTS.txt, Read through it and you'll see all pertinent information about where Grub is installed.  You can run it again after changes to compare.

---

### Post by PatrickD-52761 on 2011-09-04
> **Hakunka-Matata said:**
> Welcome to the forums Patrick;

Download boot_info_script, install and run it.  It will generate a file named RESULTS.txt, Read through it and you'll see all pertinent information about where Grub is installed.  You can run it again after changes to compare.

Thanks for the quick reply.

I pasted the results into a pastebin file [http://pastebin.ubuntu.com/681720/]("http://pastebin.ubuntu.com/681720/")

So, essentially I'll be wiping off sda (which is the Windows drive), and re-updating GRUB. So, will it move the GRUB (or even need to move it)? And more importantly, will it require two hard drives to be installed in the computer in the future?

Finally, I have no clue about the sdb2 portion (especially the "Unknown bootloader" message. It could be from when I upgraded Mythbuntu to 11.04, as I ran into issues there.  So, I could probably wipe that partition out too.


Thanks again, and have a great weekend:)
Patrick.

---

### Post by Hakunka-Matata on 2011-09-04
**EDIT:  I tried to copy past and format the RESULTS.txt but it **didn't work right.  Please try this, 
# open your RESULTS.txt file with```
 
gedit RESULTS.txt
```copy the entire text, Ctrl-A
paste the entire text into a new reply
highlight the entire text
click on # icon (code tags)
preview it,
post it.
thanks

---

### Post by Hakunka-Matata on 2011-09-04
> **PatrickD-52761 said:**
> Hi everyone,

Here's my setup. I have two 80GB drives in my desktop, one (sda) with Windows 7 installed, and one (sdb) with Mythbuntu 11.04 installed.  IIRC, when I installed GRUB, I either had it placed on just sda, or on both drives (I honestly don't remember which way I went).  Now, I want to eliminate the Windows 7 boot, and use that drive as extra data (with the intention of eventually replacing both drives with one larger drive).

So my questions are

1. How do I determine where the GRUB loader is installed (if it's on both drives or just the one)?
2. Is this a simple case of reformatting the Windows 7 drive and then updating GRUB, or is there more to it?
3. If there's more to this, what exactly will I have to do?

I should note that this probably won't happen for a week or two. I need to sift through the Windows 7 partition and determine exactly what I may use out of it. Then, I'll have to find applications to meet the same functionality (or install them via WINE).  Also, I chose "All variants" because this could equally apply to someone who has Kubuntu, Lubuntu, Edubuntu, or even Ubuntu installed alongside Windows.

Have a great weekend, and thanks for any help :)
Patrick.
Reply to questions

[LIST=1]
[*]run boot_info_script && sure there is a command to show that..........
[*]ya, sort of.
[LIST=1]
[*]You can delete the Windows 7 partition
[*]create a new partition in the newly visible unallocated space
[*]format it ntfs - it'll be read and writable by both Linux & Windows
[/LIST]
 
[*]decide on boot scheme - Grub or each drive bootable by switching "first boot drive" in BIOS
[/LIST]

---

### Post by oldfred on 2011-09-04
Are these IDE/PATA drives or SATA? Some systems with IDE drives will only boot from sda or older system determine boot as primary master with jumpers or location on cable.

If you cannot select in BIOS, I would install grub2's boot loader to sdb, just so if sda ever fails you can replug sdb in as primary and directly boot it.

When in Ubuntu all you have to do is this.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Only if you can reset BIOS to boot sdb then you may want to also change the default reinstall on grub updates to sdb.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by PatrickD-52761 on 2011-09-04
> **Hakunka-Matata said:**
> **EDIT:  I tried to copy past and format the RESULTS.txt but it **didn't work right.  Please try this, 
# open your RESULTS.txt file with```
 
gedit RESULTS.txt
```copy the entire text, Ctrl-A
paste the entire text into a new reply
highlight the entire text
click on # icon (code tags)
preview it,
post it.
thanks

Here it is. I put it in the pastebin because it's pretty long.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 843b55f6-5ed7-450e-9e43-935e230f3a71 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   156,297,215   156,295,168   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   150,300,671   150,298,624  83 Linux
/dev/sdb2         150,302,718   156,301,311     5,998,594   5 Extended
/dev/sdb5         150,302,720   156,301,311     5,998,592  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048    77,830,143    77,828,096   7 NTFS / exFAT / HPFS
/dev/sdc2          77,830,144   625,141,759   547,311,616  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1AA83EA3A83E7CF7                       ntfs       DCKY-7-MC
/dev/sdb1        843b55f6-5ed7-450e-9e43-935e230f3a71   ext4       
/dev/sdb5        01611613-0a18-4ec0-b8d6-816382a96561   swap       
/dev/sdc1        59D234A620BCBCFB                       ntfs       
/dev/sdc2        790f256c-9315-4e05-bbc5-44c4026aa27f   ext4       recordings

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sdc1        /media/59D234A620BCBCFB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/recordings        ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.35-29-generic ...'
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro   quiet splash vmalloc=192MB vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 843b55f6-5ed7-450e-9e43-935e230f3a71
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1AA83EA3A83E7CF7
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=843b55f6-5ed7-450e-9e43-935e230f3a71 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sdb5 during installation
UUID=01611613-0a18-4ec0-b8d6-816382a96561 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.2.254/Videos /mnt/Videos cifs auto,iocharset=utf8,uid=mythtv,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
UUID=d8419d48-5863-4abe-ab35-5937d162f412 / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.243556976 = 17.441386496   boot/grub/core.img                             1
  16.342197418 = 17.547300864   boot/grub/grub.cfg                             1
   0.774414062 = 0.831520768    boot/initrd.img-2.6.35-22-generic              2
  69.792255402 = 74.938863616   boot/initrd.img-2.6.35-28-generic              1
  22.308933258 = 23.954034688   boot/initrd.img-2.6.35-29-generic              2
  22.482471466 = 24.140369920   boot/initrd.img-2.6.38-10-generic              2
  65.591068268 = 70.427873280   boot/initrd.img-2.6.38-11-generic              2
  11.255130768 = 12.085104640   boot/initrd.img-2.6.38-8-generic               2
  16.264137268 = 17.463484416   boot/vmlinuz-2.6.35-22-generic                 1
  16.321834564 = 17.525436416   boot/vmlinuz-2.6.35-28-generic                 1
  16.953456879 = 18.203635712   boot/vmlinuz-2.6.35-29-generic                 1
  17.606754303 = 18.905108480   boot/vmlinuz-2.6.38-10-generic                 2
  52.337223053 = 56.196665344   boot/vmlinuz-2.6.38-11-generic                 2
  16.243457794 = 17.441280000   boot/vmlinuz-2.6.38-8-generic                  1
  65.591068268 = 70.427873280   initrd.img                                     2
  22.482471466 = 24.140369920   initrd.img.old                                 2
  52.337223053 = 56.196665344   vmlinuz                                        2
  17.606754303 = 18.905108480   vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  e4 6b 5e d6 9b 0c 44 b0  94 8b da b3 65 88 9a 12  |.k^...D.....e...|
00000010  c5 7b 54 6d bd 12 c2 5e  af 6a 49 b4 a3 48 16 8c  |.{Tm...^.jI..H..|
00000020  1f 89 1a 42 54 59 cd 05  0e d7 90 b2 67 89 cd 93  |...BTY......g...|
00000030  c3 56 5d 25 fa ef bf 79  51 26 64 a2 51 cd ba d1  |.V]%...yQ&d.Q...|
00000040  ce 4b 92 7a 51 08 a1 99  7e e7 7d 45 58 9a 81 39  |.K.zQ...~.}EX..9|
00000050  89 5e c6 24 66 42 47 e3  4c af 32 94 42 9e 02 d3  |.^.$fBG.L.2.B...|
00000060  38 b9 79 81 b7 a5 4d d4  3a d7 d4 d4 4b 8e d1 24  |8.y...M.:...K..$|
00000070  9a 86 1e 9d 5f 5c a8 b4  4a b1 ff 94 f8 e9 26 e2  |...._\..J.....&.|
00000080  bb 95 a1 8b 8b 5c 5e dc  f6 d3 74 6d 3c 37 37 f3  |.....\^...tm<77.|
00000090  d2 ea 50 36 1e ad 7f 5a  00 00 11 98 f1 fc 2c 7a  |..P6...Z......,z|
000000a0  da 50 11 92 00 03 35 d5  1d 43 81 c0 bb 2e 31 82  |.P....5..C....1.|
000000b0  88 2c b4 8c 97 c0 8f 20  ad e3 ec e9 9e 92 0e e3  |.,..... ........|
000000c0  e7 42 db ce 36 09 b8 5b  f3 2a 87 db 9f 72 72 de  |.B..6..[.*...rr.|
000000d0  db 13 ba a4 a6 7b e2 7e  9d 76 5f fb 33 12 9a b6  |.....{.~.v_.3...|
000000e0  66 4c b4 ba 67 1c a5 d1  cc 38 33 c3 b8 76 1d 99  |fL..g....83..v..|
000000f0  47 b1 4d 9a 1f 3e d6 f5  07 f7 c8 f2 12 22 68 fe  |G.M..>......."h.|
00000100  df 9d 89 cf 52 c8 bc b4  df 33 26 0e 6c e4 51 7c  |....R....3&.l.Q||
00000110  8c 8d 4d a7 2a de 83 13  3a 46 8a 00 28 32 98 04  |..M.*...:F..(2..|
00000120  cd 41 07 28 7c c8 51 48  00 00 1a 98 d7 c7 10 0d  |.A.(|.QH........|
00000130  62 cd 20 a8 68 2a 0e 1c  74 d0 ec 67 08 b5 30 c4  |b. .h*..t..g..0.|
00000140  8d c1 8d a2 13 7c 8d cd  0c 65 79 34 0c a6 8c 41  |.....|...ey4...A|
00000150  fa fd 54 85 bf 27 ca f7  ae 8c c4 ea 4e ce c9 99  |..T..'......N...|
00000160  f4 a6 9b 2b eb b6 48 19  13 75 4c 75 44 16 4a ee  |...+..H..uLuD.J.|
00000170  89 32 4e 0f aa ae 14 43  81 f4 38 43 4e 5c 16 8b  |.2N....C..8CN\..|
00000180  c4 07 76 3f ac a4 6f b5  a9 6f 1a 7b 4d 2f de 82  |..v?..o..o.{M/..|
00000190  a6 35 a3 cc b7 c7 24 18  91 ca d6 86 70 94 88 f2  |.5....$.....p...|
000001a0  e3 e9 cb 86 9e a1 7b ae  2e ad a3 49 59 f1 2d 68  |......{....IY.-h|
000001b0  36 a7 a4 39 a8 f1 24 7a  94 89 47 b5 c1 40 00 fe  |6..9..$z..G..@..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Thanks, and have a great day:)
Patrick.

---

### Post by YesWeCan on 2011-09-04
The Grub MBR code is on your Windows drive. It wants to be on your Ubuntu drive.

Boot your Ubuntu as normal.
[COLOR="Navy"]sudo fdisk -l[/COLOR]
to check the drive letter. I'll assume it is sdb but check it.
[COLOR="navy"]sudo grub-install /dev/sdb[/COLOR]

Shutdwn, disconnect your Windows drive and verify you can boot Ubuntu.

---

### Post by YannBuntu on 2011-09-05
> **PatrickD-52761 said:**
> I want to eliminate the Windows 7 boot, and use that drive as extra data

Hello Patrick, you can do this in 1 click by uninstalling Windows via OS-Uninstaller: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1313035409.png[/IMG]

it will format your Windows partition in NTFS (you can also choose EXT in the Advanced Options) and automatically reinstall GRUB so that you will still have access to Ubuntu.

---

