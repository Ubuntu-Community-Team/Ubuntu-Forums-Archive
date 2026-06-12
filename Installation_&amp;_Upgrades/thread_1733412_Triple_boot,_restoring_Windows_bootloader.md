---
title: "Triple boot, restoring Windows bootloader?"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by anlag on 2011-04-19
So I've been helping a friend install a triple boot on her system: Windows XP, Windows 7 and Ubuntu 10.10. All systems work fine, the problem is that she's got the annoying two-level boot menus, where the GRUB menu lists one Windows option which then leads into the Windows boot menu. The aim is to get them into a single menu with all three alternatives.

Now, having done my homework before starting, I found in [this thread]("http://http://ubuntuforums.org/showpost.php?p=8357272&postcount=18") instructions to first install XP, then remove its boot flag, and then proceed in turn with Windows 7 and Ubuntu installations, which should mean both Windows installations think they're alone so to speak, and each get their own bootloader installed. Unfortunately it turned out when the process was done (I've been guiding this over the Internet as my friend is half a world away) that that boot flag possibly was never removed. In any case, we've got the double boot menus, and the Windows 7 installation doesn't have any boot files in its root but simply refers on to the XP partition.

First thing, tried to simply create a new custom GRUB entry to point to the Windows 7 partition. Unsurprisingly this didn't help, it gave some erratic behavuour and then showed the Windows boot menu anyway. Second thing, we tried copying over the Boot directory, bootmgr, boot.ini and boot.bak from the XP root to the Windows 7 root, as sort of suggested [here]("http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing") although under slightly different circumstances. After running an update-grub this did yield another Windows entry in the GRUB menu, but again somewhat unsurprisingly this leads just go the same old Windows boot menu.

So, what I suppose needs doing is to properly configure the Windows boot loaders on both the XP and Win 7 partitions, so that they will independently load the system stored on their own partitions, rather than go to this joint Windows bootloader bollocks. Whether it's sufficient to somehow (how?) edit the existing files (that we copied over) on each system, or whether we have to install something else, also considering one system is Windows 7, I'm rather clueless about. Is this reasonably doable, or might it be preferable to use some tool to (re)build the Windows boot configurations from scratch? 

Any help or pointers would be appreciated at this point. Oh yeah, for completion I'll enclose the output of the boot_info_script, just in case it helps, noting that the script was ran before any files were copied from the XP installation (which is on sda1) to the Windows 7 installation (which is on sda5) which is why they don't show up on the latter drive here.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdj

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   409,593,239   409,593,177   7 HPFS/NTFS
/dev/sda2         409,593,301   976,771,071   567,177,771   f W95 Ext d (LBA)
/dev/sda5         409,593,303   819,186,479   409,593,177   7 HPFS/NTFS
/dev/sda6         819,187,712   819,576,831       389,120  83 Linux
/dev/sda7         819,578,880   823,771,135     4,192,256  82 Linux swap / Solaris
/dev/sda8         823,773,184   865,724,415    41,951,232  83 Linux
/dev/sda9         865,726,464   976,771,071   111,044,608  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdj1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00DCE03BDCE02C9A                       ntfs       XP                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3AAAC996AAC94F57                       ntfs       WIN-7                         
/dev/sda6        dfba7429-a524-4494-922a-aae5e6eda5a3   ext3                                     
/dev/sda7        1f8c1f2d-04d1-4621-98de-9fbcc8fd97b1   swap                                     
/dev/sda8        913d21a0-c2bc-4b2b-8948-507f1be27d6f   ext4                                     
/dev/sda9        d1c42fdf-8754-4bdc-9981-6de1a100812a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        88248D4E248D4064                       ntfs       Local                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2C482E09482DD27E                       ntfs       O1a.1Tb.black.s               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        A2A4530CA452E279                       ntfs       O1b.1Tb.black.wd              
/dev/sdd: PTTYPE="dos" 
/dev/sde1        324848AF4848741F                       ntfs       Movies01b.1Tb                 
/dev/sde: PTTYPE="dos" 
/dev/sdj1        607AAD5D7AAD30A8                       ntfs       Portable 500                  
/dev/sdj: PTTYPE="dos" 
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /boot                    ext3       (rw,commit=0)
/dev/sda9        /home                    ext4       (rw,commit=0)
/dev/sdj1        /media/Portable 500      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/Movies01b.1Tb     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/O1a.1Tb.black.s   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/O1b.1Tb.black.wd  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


============================= sda6/grub/grub.cfg: =============================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 913d21a0-c2bc-4b2b-8948-507f1be27d6f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	linux	/vmlinuz-2.6.35-28-generic root=UUID=913d21a0-c2bc-4b2b-8948-507f1be27d6f ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=913d21a0-c2bc-4b2b-8948-507f1be27d6f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	linux	/vmlinuz-2.6.35-22-generic root=UUID=913d21a0-c2bc-4b2b-8948-507f1be27d6f ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=913d21a0-c2bc-4b2b-8948-507f1be27d6f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set dfba7429-a524-4494-922a-aae5e6eda5a3
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 00dce03bdce02c9a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows lucky dip (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
#	search --no-floppy --fs-uuid --set 00dce03bdce02c9a
	chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda6: Location of files loaded by Grub: ===================


 419.5GB: grub/core.img
 419.5GB: grub/grub.cfg
 419.4GB: initrd.img-2.6.35-22-generic
 419.4GB: initrd.img-2.6.35-28-generic
 419.4GB: vmlinuz-2.6.35-22-generic
 419.4GB: vmlinuz-2.6.35-28-generic

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=913d21a0-c2bc-4b2b-8948-507f1be27d6f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=dfba7429-a524-4494-922a-aae5e6eda5a3 /boot           ext3    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=d1c42fdf-8754-4bdc-9981-6de1a100812a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=1f8c1f2d-04d1-4621-98de-9fbcc8fd97b1 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 421.8GB: initrd.img
 421.7GB: initrd.img.old
 421.7GB: vmlinuz
 421.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi 
```

---

### Post by oldfred on 2011-04-19
I cannot follow link to the instructions you found (double HTTP), but I have posted instructions several times that I found from others. You really should have win7 in a primary partition. Windows will not install to a logical unless the boot is from a primary.

To get each MS to have its own boot loader make a second[COLOR=Red] primary [/COLOR]partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

I have seen instructions to get XP to directly boot from a logical, but not Win7. But best to have all windows installs in primary partitions.

---

### Post by anlag on 2011-04-19
Thanks, and yes, I saw at least a couple of those threads before. The plan was definitely to install Windows 7 to a primary partition, in fact before she installed Windows XP she already partitioned the drive into three partitions. XP went into the first primary, and Windows 7 supposedly went in the second one, or at least it was intended to. The bizarre thing there is that when we were doing the manual partitioning as part of the Ubuntu install, after Windows 7 had been installed, the W7 partition first showed as /dev/sda2 and then after creating and removing some partitions (without applying changes) and backing up a step, and entering the partitioning tool again, it was showing as /dev/sda5. I'd have assumed she read it wrong but she pasted the actual text into a chat window so we could go back and check.... very odd indeed. I read later that if Windows 7 is installed and it notices an existing Windows installation, it gets slotted into a logical partition rather than a primary one. So perhaps that's what happened, not that I sew how it explains the changing device names... but there you go.

OK I'm ranting, not very relevant. So, we'll need to get rid of the Windows 7 partition and use that space as a primary partition (if it isn't) and then reinstall W7? Are you saying we should manually set the boot flag on that new partition before beginning the Windows 7 installation? If so that's news to me, I had previously thought it would be enough to have the boot flag on the XP partition switched off.

But we can try that of course. I take it that will run over GRUB, but that should be easily fixable with update-grub from the live cd...

---

### Post by Mark Phelps on 2011-04-19
> **anlag said:**
>  I read later that if Windows 7 is installed and it notices an existing Windows installation, it gets slotted into a logical partition rather than a primary one. So perhaps that's what happened, not that I sew how it explains the changing device names... but there you go.

Actually, when you already have XP installed, Win 7 installs its boot loader files to the XP partition, and its other files to the new  partition.  This can confuse the OS_Prober in GRUB later when it sees Win7 stuff in two different partitions.

---

