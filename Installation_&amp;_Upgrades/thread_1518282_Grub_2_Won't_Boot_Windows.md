---
title: "Grub 2 Won't Boot Windows"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Yombute on 2010-06-26
I really hate to post this - I'd much rather read and figure it out for meself but I'm afraid I'm going to make a bigger mess than I already have.
Had a fine dual boot install of Win 7 and Ubuntu and decided to do the 10.04 upgrade.  I knew I was in trouble when the grub install came up and gave me options I didn't understand but I went ahead.  (I also have a startup manager installed through Ubuntu that I have pointing to the Win 7 OS for default.)
Anyway, post upgrade I don't get a "grub loading" msg and when it gets to my boot options there's Win 7 but if I go ahead and try to boot into that all I get is a blinking cursor.  Thank goodness I can still get into Ubuntu or I'd be up sheet's creek.
Here is my boot info if anyone can offer some clear assistance.  I tried going through what has been posted previously and it didn't change anything.  PS:  The LAST two lines are what I tried to do to get GRUB to point to the correct place.
```

```Boot Info Script 0.55    dated February 15th, 2010                    

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 158588710 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 159304342 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 159307286 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda8 and 
                       looks at sector 159310214 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda8 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 159318982 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb6 and 
                       looks at sector 159321902 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb6 starts at sector 1472. But according to the info 
                       from fdisk, sdb6 starts at sector 485353472.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb7 and 
                       looks at sector 159308438 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sda5              16,128   514,144,259   514,128,132   b W95 FAT32
/dev/sda6         514,144,323   738,459,854   224,315,532   7 HPFS/NTFS
/dev/sda7         738,459,918   912,524,129   174,064,212   7 HPFS/NTFS
/dev/sda8         912,524,193   976,768,064    64,243,872   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
240 heads, 63 sectors/track, 82689 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *        206,848   156,772,351   156,565,504   7 HPFS/NTFS
/dev/sdb2         156,779,280 1,245,026,159 1,088,246,880   f W95 Ext d (LBA)
/dev/sdb5         278,792,073   485,351,999   206,559,927   7 HPFS/NTFS
/dev/sdb6         485,353,472   589,801,471   104,448,000   7 HPFS/NTFS
/dev/sdb7         699,775,398 1,245,024,943   545,249,546   7 HPFS/NTFS
/dev/sdb8         156,779,406   273,717,359   116,937,954  83 Linux
/dev/sdb9         273,717,423   278,782,559     5,065,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda5        CD9C-74F2                              vfat       Recorded St                   
/dev/sda6        8AAF825AC85F460E                       ntfs       Data                          
/dev/sda7        C6AFFCBF6F31FBB1                       ntfs       MiscellaneousCrap             
/dev/sda8        6E1AB50D728D7E85                       ntfs       Music                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A403E38403E2B39                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        E04BAF71D75FFE78                       ntfs       Recorded TV                   
/dev/sdb6        822A952D2A951F6B                       ntfs       New Volume                    
/dev/sdb7        D410BCFCD5A4DE44                       ntfs       Edits                         
/dev/sdb8        428b9a7f-4219-4265-bb93-defe6d9ccac6   ext4                                     
/dev/sdb9        de883377-0a93-4ec6-bd3c-ee84291fce83   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb8        /                        ext4       (rw,errors=remount-ro)


=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
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
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=428b9a7f-4219-4265-bb93-defe6d9ccac6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=428b9a7f-4219-4265-bb93-defe6d9ccac6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=428b9a7f-4219-4265-bb93-defe6d9ccac6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	echo	'Loading Linux 2.6.31-15-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=428b9a7f-4219-4265-bb93-defe6d9ccac6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 428b9a7f-4219-4265-bb93-defe6d9ccac6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 0a403e38403e2b39
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=428b9a7f-4219-4265-bb93-defe6d9ccac6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=de883377-0a93-4ec6-bd3c-ee84291fce83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


  83.2GB: boot/grub/core.img
  80.7GB: boot/grub/grub.cfg
  81.5GB: boot/initrd.img-2.6.31-15-generic-pae
  81.5GB: boot/initrd.img-2.6.32-22-generic-pae
  80.5GB: boot/vmlinuz-2.6.31-15-generic-pae
  81.1GB: boot/vmlinuz-2.6.32-22-generic-pae
  81.5GB: initrd.img
  81.5GB: initrd.img.old
  81.1GB: vmlinuz
  80.5GB: vmlinuz.old

```

sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

---

### Post by Yombute on 2010-06-26
By the way...should GRUB have installed on each partition???

---

### Post by drs305 on 2010-06-26
Post(s) moved to new thread.

---

### Post by darkod on 2010-06-26
> **Yombute said:**
> By the way...should GRUB have installed on each partition???

It shouldn't, only to a disk MBR which doesn't have a number in its device name, like /dev/sda, /dev/sdb, etc.

However, usually installing grub2 to the windows partition would block windows loading, but if we can trust the script results you don't have it installed in the win7 partition. So it should still load fine.

Also, grub2 is installed to the other disk, not the disk with win7 and ubuntu.

Boot into ubuntu, and to install grub2 to the MBR of sdb do:

sudo grub-install /dev/sdb

After that restart and make sdb first hdd to boot from in BIOS.

Then again load ubuntu and try:

sudo grub-mkdevicemap
sudo update-grub

to clear out any confusion. See if that helped.

---

### Post by Yombute on 2010-06-26
You guys are amazing.  No, it's still not working but I am incredibly impressed with the responses and helpfulness.  Thanks to drs305 for kindly moving my post and to Darko for his suggestions.

You know, it's odd I think, but it doesn't matter which HDD I boot from, I still get my boot options and can get into Ubuntu.  (Getting Win 7 to work will be a necessary plus for now)  I'm still puzzled as to why I don't get the "Grub loading" prompt now.

I'm considering trying to get rid of the grub and doing a MBR repair with Win7, then going back and reinstalling Ubuntu but I tried the MBR repair last night following instructions from an MS document and that didn't work either.  I'm a bit afraid of getting this to the point where I can't get into either OS.

Any other suggestions would be appreciated.

---

### Post by drs305 on 2010-06-26
Have you tried the solutions offered in this thread by *talsemgeest* on restoring Windows after installing Ubuntu:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")
Note it should work for 10.04 as well.

In response to your question, no - grub 2 should not be installed to each partition; I am not enough of a Windows guy to know how it's being there is going to affect your Windows operation, but try the above procedure as long as you are ending up at a blinking cursor when you select Windows. (If it returns to the Grub menu it's a different solution).

Off to work.

PS - Glad you found the relocated post.  ;-)

Also I saw you attempted to use the code tags. If you click on the # icon it will put them in for you. Your attempt didn't work because the "code" and "/code" must be enclosed in brackets [ ]. I"ve cleaned it up - hope you don't mind.

---

### Post by oldfred on 2010-06-26
I have not had to repair Vista or & but have saved these instructions for those who do. After fixing windows you just need to rerun Darko's instructions or drs305 linked instructions to reinstall grub. You do not have to reinstall Ubuntu.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Yombute on 2010-06-26
Thanks folks.  I've got Windows 7 booting up again.  I had read (and thought I) followed the MS support document for fixboot-fixmbr last night but it didn't do anything.  Could it really be that one needs to UNselect the OS when it's found with the repair option?  MS might want to mention that.

Anyway, I enjoy chaos and frustration so I'm off to reinstall Grub now.  I'm sure I'll be speaking with you all in a bit.
I am VERY appreciative of the help.
Yom

---

### Post by Yombute on 2010-06-26
Well that part went smoothly.  All is now right with the world - inside my small little home office.  Thanks to you folks I am once again able to boot into either OS.
I appreciate the help!
Now, has anyone found a way to separate out and turn OFF the vuvuzela drone from the TV watching the world cup?  Man, that is obnoxious!

---

