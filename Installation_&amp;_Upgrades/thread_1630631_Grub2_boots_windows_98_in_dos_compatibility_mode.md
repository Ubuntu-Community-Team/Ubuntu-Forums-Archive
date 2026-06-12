---
title: "Grub2 boots windows 98 in dos compatibility mode"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by n.hinton on 2010-11-25
Have win98se on secondary master as it fully supports some devices Ubuntu doesn't (Aries scan it pro, pci smart modem, Lexmark printer/scanner x2250), Lucid is on primary master. Grub seamlessly booted windows using menu.lst entry:

```
title		Windows 95/98/Me
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
map (hd0) (hd1)
map (hd1) (hd0)
```

Have updated grub to grub2 and cannot get it to boot windows without dos compatibility mode (which is no good for 2 of the above devices), it is not overwriting the secondary master's mbr, it just appears that way when booting from grub2 menu. Disabling primary master in CMOS setup, has windows boot normally.

The 30_os-prober generates:

```
### BEGIN /etc/grub.d/30_os-prober ###
Found Windows 95/98/Me on /dev/sdb1
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2d27-07ee
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Which fails as above (dos compatibility mode), as does 40_custom, with all the permutations I've tried so far, like:

```
### BEGIN /etc/grub.d/40_custom ###
menuentry "Microsoft Windows" {
	insmod fat
	set root=(hd1,1)
	chainloader +1
	drivemap -s hd0 hd1
}
### END /etc/grub.d/40_custom ###
```
and
```
menuentry "Microsoft Windows" {
	drivemap -s hd0 hd1
	chainloader (hd1,1)+1
}
```

and have experimented with parttool and load_env/save_env, without success and am wondering if the problem is rootnoverify not being supported.

Would be grateful if anyone knows a configuration that works, as using CMOS/BIOS setup to boot windows is a pain.

---

### Post by Mark Phelps on 2010-11-25
As you will see in the link below, rootnoverify is NOT supported in GRUB2:

[http://grub.enbug.org/CommandList]("http://grub.enbug.org/CommandList")

---

### Post by n.hinton on 2010-11-25
Yes Mark, I'd just said that. But is that the problem?

---

### Post by oldfred on 2010-11-26
So we can see what is where. I think meierfra. modified script to include win98 partitions.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by jocko on 2010-11-26
If you can't find how to make grub2 re-map the drives properly for windows, another option is to swap the drives around (either in the boot order or physically), then install grub2 to the mbr of the drive containing the windows install. This would of course overwrite the windows boot loader in the mbr of the drive, but that would only be a problem if you disconnect your ubuntu drive (or delete the partition containing /boot).

But, of course grub2 should be able to boot your windows 98, so keep trying to find help on grub2 before you try my idea...

---

### Post by n.hinton on 2010-11-26
Hi oldfred & jocko

Thanks jocko, and it would only require fdisk/mbr to rebuild secondary master mbr, that's where grub2 needs to point.

@ oldfred, results text as requested:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   234,436,544   234,436,482   5 Extended
/dev/sda5                 126   226,002,419   226,002,294  83 Linux
/dev/sda6         226,050,678   234,436,544     8,385,867  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda5        ef051c9e-179a-4158-af23-0332c223a49f   ext3                                     
/dev/sda6        0c9b4203-ebec-4747-a879-3150c279a385   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2D27-07EE                              vfat       &#8364;ê&#339;8                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/disk-1            vfat       (rw,iocharset=utf8,umask=000)


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
search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
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
search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=ef051c9e-179a-4158-af23-0332c223a49f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=ef051c9e-179a-4158-af23-0332c223a49f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ef051c9e-179a-4158-af23-0332c223a49f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2d27-07ee
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
menuentry "Microsoft Windows" {
#	insmod chain
#	insmod fat
	set root=(hd1)
	drivemap -s hd0 hd1
#	search --fs-uuid --set 2D27-07EE
	chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ef051c9e-179a-4158-af23-0332c223a49f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0c9b4203-ebec-4747-a879-3150c279a385 none            swap    sw              0       0
#/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sdb1 /media/disk-1 vfat iocharset=utf8,umask=000 0
UUID=2D27-07EE /media/disk-1 vfat iocharset=utf8,umask=000 0

=================== sda5: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.32-26-generic
   3.0GB: boot/vmlinuz-2.6.32-26-generic
   3.0GB: initrd.img
   3.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by dino99 on 2010-11-26
The other solution is to kick w98 off :)

wine (winehq) is able to run most of the exe progs. (i dont need Ms os since 2005)

---

### Post by klytu on 2010-11-26
> **jocko said:**
> If you can't find how to make grub2 re-map the drives properly for windows, another option is to swap the drives around (either in the boot order or physically), then install grub2 to the mbr of the drive containing the windows install. This would of course overwrite the windows boot loader in the mbr of the drive, but that would only be a problem if you disconnect your ubuntu drive (or delete the partition containing /boot).

But, of course grub2 should be able to boot your windows 98, so keep trying to find help on grub2 before you try my idea...

+1 I second this idea! Dual-booting Windows 98 gave me all sorts of weird problems if Windows 98 wasn't installed on the physically first drive seen by the BIOS. For me these problems disappeared when Windows 98 was installed to the first physical drive (not just by swapping the boot order in the BIOS) and then installing GRUB to the mbr of the Windows 98 drive. Maybe this will work with GRUB2 as well. If you're worried about overwriting the Win98 boot loader on that drive, you could back it up first; or just reinstall it if you have a Win98 CD.

---

### Post by oldfred on 2010-11-26
I do not see anything out of place in the boot script. It looks like you boot entries should work, but I am sure win98 was not one the main things that was tested.

All the above suggestions are good possiblities.

I might try chainloading to the MBR of the second drive (first drive is drive 0).

# Chainload another bootloader
menuentry "Chainload Drive 1" {
set root=(hd1)
chainloader +1
}

---

### Post by n.hinton on 2010-11-26
Hi oldfred,

Now thinking set root=(hd1) should use secondary masters mbr but does not. Is this a grub2 bug?

without drivemap -s hd0 hd1
```
# Chainload another bootloader
menuentry "Chainload Drive 1" {
set root=(hd1)
chainloader +1
}
``` boots Lucid on hd0,1. And with, dos compatibility mode again

---

### Post by oldfred on 2010-11-26
Perhaps something about your drives. I have all SATA and which ever drive I boot is drive0. I have chainloaded to all my other drives but normally boot sdc. Then sda is hd1 and sdb is hd2. If I boot sda they are in order. If I boot sdb it is hd0, sda is then hd1 again. I found this only by editing (using e on grub menu) until I found which drive number worked on the chainboot. 

When I boot my flash drive it it hd0 but Ubuntu sees it as sde or sdf. It skips some drives but I have not tried to chainboot the flash drive to see what number grub thinks it is?

---

### Post by n.hinton on 2010-11-26
Hi oldfred,

This one's hd's are on eide's and the designations remain fixed regardless of grub2 boot drive selection, thanks though.

PS Grub indirectly booted secondary master via the mbr, I suspect Grub2 is pointing at the vbr, thus causing win98 to think the mbr has been modified and go to dos compatibility mode.

---

### Post by oldfred on 2010-11-26
Even though the boot script showed windows as sdb and linux as sda, does BIOS have it the other way around? Did you try editing grub menu with e and change entries to boot hd0 instead of hd1?

---

### Post by n.hinton on 2010-11-26
No, correct in BIOS, and yes, it then boots Lucid.

---

### Post by oldfred on 2010-11-26
So using either of these in the chainboot entry, both boot Ubuntu?

set root=(hd1)
set root=(hd0)

---

### Post by n.hinton on 2010-11-26
Correct, if we exclude the drivemap -s hdx hdx line

PS The problem in not booting win98 its booting it from its mbr on secondary master to avoid the issue with dos compatibility mode.

---

### Post by oldfred on 2010-11-26
I guess I do not understand the issue with DOS compatibility mode. What I read was that was just the area after the MBR that grub legacy ( and new grub) use for additional parts of grub.

Is not win98 built on DOS, so it actually runs as DOS.

---

### Post by n.hinton on 2010-11-26
No it doesn't need dos, but dos compatibility disables protected mode drivers along with any devices/software that depend on them, so is no good to me for the devices I use it for. It would of course be nice just to buy new stuff.

---

### Post by n.hinton on 2010-12-02
Nothing I've tried so far works, every permutation has booted into dos compatibility mode.

Does anyone know the difference between the way grub and grub2 handle int13 hooking?

---

### Post by oldfred on 2010-12-02
I found this on grub2.

[http://kubuntuforums.net/forums/index.php?topic=3106368.15;wap2](http://kubuntuforums.net/forums/index.php?topic=3106368.15;wap2)

The drivemap command kicks in, it takes over the Int13 role, performing  the drive mapping and switching, returns control to the BIOS Int13  handler, and then the OS sees the drives as they have been  mapped/switched by drivemap.
Important:  drivemap does not change the  real (live) drive mapping as seen by GRUB 2; the changes performed by  drivemap only affect the booted OS.

[http://gnu.gds.tuwien.ac.at/software/grub/grub-legacy-faq.en.html](http://gnu.gds.tuwien.ac.at/software/grub/grub-legacy-faq.en.html)

 Check if you have turned on the support for INT 13 extension (LBA). If so, disable the support and see if GRUB can now access your SCSI disk. This will make it clear that your SCSI BIOS sucks.

---

### Post by n.hinton on 2010-12-02
Hi oldfred,

Again thanks for the links, but had already read through those.

Logical Block Addressing is what allows the fat32 partition to be larger than 4gb and since its nearly 80gb I can't change it, well not without being destructive.

Thing is, for last 2 years grub has worked perfectly booting the win98 normal protected mode.

I'm reluctant to regress back to legacy, as I keep reading grub2 is the way forward and it wouldn't come as a big surprise, if a future distro broke legacy anyway.

---

### Post by n.hinton on 2010-12-02
Hi again oldfred,

Win98 thinks grub2 maybe a virus, not really, just thinks the mbr been altered, it **hasn't**, boots just fine if hd0 is disabled in CMOS/BIOS setup, of if booted from Smart Boot Manager or Grub legacy. Have attached its error message and system properties status.

---

### Post by oldfred on 2010-12-02
Since it is important to run your old programs I would go back to grub legacy. While I like grub2 and it is the future, if you have an old system and it works, you do not have to upgrade.

This can work both ways.
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by n.hinton on 2010-12-04
Update:

There was an update to grub2 last night, and whilst the update alone, didn't solve the issue, changing the boot order in CMOS/BIOS setup to 'first boot device = IDE1'(hd1) did. Previously the same setting booted into dos compatibility mode, now it works (odd because drive designations remain unchanged) but now seeing hd1's mbr first solves the issue.

Had to have grub2 setup write to hd1 again though as had to fdisk/mbr hd1 after experiments to boot it with hd0 disabled.

---

### Post by goodbill on 2011-10-18
Thanks you all, booted successfully DR DOS 7.02 installed
in primary partition of the same drive (250GB) that uses Linux (Ubuntu Lucida Lynx)

menuentry "test" {
set root=(hd0,3)
chainloader +1
}

tried (hd0,1)  (hd0,2) etc until booted
now should try OpenDOS 7.01 to make a proper partition of the disk, but all works anyway

---

