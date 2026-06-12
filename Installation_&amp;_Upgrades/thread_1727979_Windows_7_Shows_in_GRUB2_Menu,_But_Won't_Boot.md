---
title: "Windows 7 Shows in GRUB2 Menu, But Won't Boot"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by qsczse25 on 2011-04-13
Hello,
I have two hard drives - (1) 80GB (2) 500GB:

[LIST]
[*]the 1st HD has 3 partitions (in that order) - Windows 7, Ubuntu 10.10 & Swap.
[*]the 2nd HD is for storage only, and has 2 partitions.
[/LIST]

I did the following - I installed Windows 7 on the first partition of the 1st HD, it booted just fine. Then I installed Ubuntu 10.10 on the second partition of the 1st HD.

Windows 7 shows in the GRUB menu alongside with Ubuntu. Ubuntu boots just fine, but when I select Windows it simply restarts the computer and the GRUB menu shows again.

**_RESULTS.txt of Boot Info Script_:**

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   106,498,047   106,291,200   7 HPFS/NTFS
/dev/sda3         106,498,048   151,963,647    45,465,600  83 Linux
/dev/sda4         151,963,648   156,366,847     4,403,200  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   129,419,639   129,419,577   7 HPFS/NTFS
/dev/sdb2         129,419,640   976,768,064   847,348,425   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2A0001010000D62B                       ntfs       System Reserved               
/dev/sda2        E84412FA4412CAE8                       ntfs                                     
/dev/sda3        26cb1013-70cb-4d79-9bea-570acb1877cc   ext4                                     
/dev/sda4        d423fbe6-927c-4ec0-ac5e-3785d54ce367   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0214E4AC14E4A3BF                       ntfs       Stuff                         
/dev/sdb2        B820891A2088E12C                       ntfs       Archive                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
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
	search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=26cb1013-70cb-4d79-9bea-570acb1877cc ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=26cb1013-70cb-4d79-9bea-570acb1877cc ro single 
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
	search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 26cb1013-70cb-4d79-9bea-570acb1877cc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2a0001010000d62b
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
UUID=26cb1013-70cb-4d79-9bea-570acb1877cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=d423fbe6-927c-4ec0-ac5e-3785d54ce367 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  74.1GB: boot/grub/core.img
  74.1GB: boot/grub/grub.cfg
  55.4GB: boot/initrd.img-2.6.35-22-generic
  54.8GB: boot/vmlinuz-2.6.35-22-generic
  55.4GB: initrd.img
  54.8GB: vmlinuz
```

I'd really appreciate any help solving this.
Thanks in advance.

---

### Post by Dutch70 on 2011-04-13
Hi and welcome to UF

Did you choose the "install side by side" option in 10.10? 

It will mess up windows. To install 10.10, you should partition your disk ahead of time, then just choose the partition to install it on. 
I'm not sure if you can recover it, or if you'll have to reinstall. There should be someone on here soon that knows more about it.

---

### Post by qsczse25 on 2011-04-13
> **Dutch70 said:**
> Hi and welcome to UF

Did you choose the "install side by side" option in 10.10? 

It will mess up windows. To install 10.10, you should partition your disk ahead of time, then just choose the partition to install it on. 
I'm not sure if you can recover it, or if you'll have to reinstall. There should be someone on here soon that knows more about it.
Indeed, I chose "install side by side".

I actually simplified things - here's the complete process, just for the record:
(1) Partitioned everything manually
(2) Installed Ubuntu on its dedicated partition
(3) Installed Windows on its dedicated partition
(4) Booted a Live CD to recover GRUB - but after that Windows 7 wasn't in the GRUB Menu, so...
(5) Install Ubuntu (again) with the side-by-side option, on its dedicated partition

...and that's where I'm standing right now.

---

### Post by Dutch70 on 2011-04-13
So, you're saying you partitioned manually & installed. 
Then went back and chose the "install alongside windows" option?

I have no idea how that would work out. Please post the current output of...
```
sudo fdisk -l
```
That's a lower case "L"

For future reference, you should always install windows first.

---

### Post by coffeecat on 2011-04-13
> **Dutch70 said:**
> Please post the current output of...
```
sudo fdisk -l
```That's a lower case "L"

No need. That information is in the boot script output.

@qsczse25, I can see nothing in your boot script output that would prevent Windows from booting. The grub.cfg entry for Windows is OK and you have the correct Windows boot files in the Windows partitions' boot sectors. By the way, you have two Windows partitions, not one. That's normal for Windows 7 - the first partition is a small boot partition.

Question: did you resize the Windows partition in Ubuntu's Gparted after you installed Windows? I know that's unlikely from what you posted, but we need to be sure.

Did you install Windows 7 from a retail DVD? Or, if not, do you have a Windows 7 repair disc? If so, I suggest running some of the utilities from the repair console of the DVD/CD - also chkdsk from the command prompt. There may be a filesystem irregularity that needs correcting. By the way, don't run 'bootrec /FixMbr'. You'll have to reinstall grub if you do.

---

### Post by Hedgehog1 on 2011-04-13
Lets have you repair the Windows boot partition 1st.  Once windows boots correctly without grub, then you can load grub again from the LiveCD/LiveUSB.

To make a Windows 7 / Vista emergency repair disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]

**Please run the Startup Repair Once or Twice**

Then reboot to get windows to boot up.

**_Once Windows is booting directly_**:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

```
sudo mount /dev/sda3 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```


***The Hedge***

:KS

EDIT: Removed the '/FixMbr' pictures - got a little over-zealous.  Thanks Coffeecat!

---

### Post by coffeecat on 2011-04-13
@Hedgehog1, all those screenshots and links are very useful - thanks - but one of your suggestions  to the OP is that they run 'bootrec /FixMbr' which is not a good idea. All that will do is to write Windows boot code to the mbr and that will mean that the OP will be able to boot neither operating system. Not until they reinstall grub to get back to the situation as it is now.

'bootrec FixBoot' might be useful, even though the Windows boot files seem to be OK. It won't hurt to reinstall them. But I strongly discourage the OP from running /bootrec /FixMbr'. It's irrelevant and a waste of time.

---

### Post by oldfred on 2011-04-13
I generally suggest not to run the auto repairs even though that is easier as that usually does the fixMBR as part of it. I also like coffeecat suggest to run all the other windows repairs and usually that works. But sometimes more to show that it is just a windows issue, suggest running the fixMBR command to directly boot windows. Then that shows is not related to grub or Ubuntu. 

As i understand it grub just hands off booting to the windows partition just like the windows MBR does, so grub should never by itself be a cause of boot issues if configured to boot the correct working windows partition. I think grub2 does a little more checking that the NTFS partition is valid, so system does not crash. Old grub legacy just jumped to the windows partition and if not correct then system crashed.

---

