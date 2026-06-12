---
title: "Grub won't load my windows partition"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by t3ddyg on 2010-09-08
I was running windows XP, and decided to give kubuntu a shot after seeing KDE 4.5 on a youtube video. I resized my 160 gb drive using norton partition magic down to 100gb.  Then, i installed kubuntu in the free space I created.  Kubuntu works great, but whenever I try to launch my windows XP partition from grub, it goes to a black screen - and that is it.  Nothing happens at all, just a black screen.  Grub correctly identifies it as Windows XP on sda1.  
I tried reinstalling grub from the live cd using the instructions in the grub wiki.  The same issue persists.  Can someone please point me in the right direction?  This is irritating, and I have no clue how to fix it.

---

### Post by mohansathish on 2010-09-08
When grub detects your Windows partition, then its not an issue with grub or Kubuntu. 

I have a question for you. After partitioning the HDD and before installing Kubuntu, did your machine booted?

If no for the the above question, then its some other problem.

---

### Post by lechien73 on 2010-09-08
Many people report similar problems after installation. Please could you download and run the Boot Info Script from here: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

When you have generated the results.txt file, please post the contents here. If you're copying and pasting the text in, then please wrap it in [CODE] tags using the # button on the toolbar.

---

### Post by mohansathish on 2010-09-08
I don't know whether the MBR of Win X is being not detected clearly of it is a problem of Windows boot itself

---

### Post by Mark Phelps on 2010-09-09
```
I don't know whether the MBR of Win X is being not detected clearly of it is a problem of Windows boot itself
```

The fact that the machine boots to GRUB indicates that GRUB is already installed in the MBR.

To check the Windows boot, the OP would have to reinstall the XP MBR, which could be done using an XP CD, booting to a command line, and running the commands fixboot and fixmbr.  But that will remove GRUB from the MBR and create a different problem.

---

### Post by t3ddyg on 2010-09-09
> **lechien73 said:**
> Please could you download and run the Boot Info Script

I've run the boot info script, and here is the output.  Thanks for the quick replies guys!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 211382296 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             19   194,337,471   194,337,453   7 HPFS/NTFS
/dev/sda2         194,338,814   320,172,031   125,833,218   5 Extended
/dev/sda5         194,338,816   314,945,535   120,606,720  83 Linux
/dev/sda6         314,947,584   320,172,031     5,224,448  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A0A8EFABA8EF7E62                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        eb46d6a4-cbde-4a91-a38e-332998a08945   ext4                                     
/dev/sda6        2cd85021-7c2a-4f75-8f9d-bd8705230571   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D8DC4027DC4001EC                       ntfs       Dante                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
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
search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
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
search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=eb46d6a4-cbde-4a91-a38e-332998a08945 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=eb46d6a4-cbde-4a91-a38e-332998a08945 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set eb46d6a4-cbde-4a91-a38e-332998a08945
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a0a8efaba8ef7e62
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
UUID=eb46d6a4-cbde-4a91-a38e-332998a08945 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2cd85021-7c2a-4f75-8f9d-bd8705230571 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 108.2GB: boot/grub/core.img
 155.5GB: boot/grub/grub.cfg
 108.3GB: boot/initrd.img-2.6.32-24-generic
 108.2GB: boot/vmlinuz-2.6.32-24-generic
 108.3GB: initrd.img
 108.2GB: vmlinuz

```

---

### Post by Hobgoblin on 2010-09-09
> **t3ddyg said:**
> I was running windows XP, and decided to give kubuntu a shot after seeing KDE 4.5 on a youtube video. I resized my 160 gb drive using norton partition magic down to 100gb.

Did you boot into XP after resizing the partition? (just to make sure it had worked).

If not then it's most likely that something went wrong there and no amount of meddling with Grub will fix it.

The fact that it does not come up with a message such as missing operating system suggests to me that it is trying to boot from the correct partition but something on there is broken.

Can you mount the Windows partition from Kubuntu?  Can you read files from it?

---

### Post by oldfred on 2010-09-09
Windows generally wants to run chkdsk after a resize, Have you run that. If you find any errors you have to rerun until you have no errrors as it does not fix everything on one pass.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

