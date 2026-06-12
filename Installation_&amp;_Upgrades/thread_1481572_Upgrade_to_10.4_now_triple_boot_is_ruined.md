---
title: "Upgrade to 10.4 now triple boot is ruined"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Ceejay34 on 2010-05-12
I just upgraded to lucid lynx from karmic koala 64 bit. During the upgrade it complained about grub not working. It said if i didnt know what drive to mount i had to select all of them, which i did. Did i now damage my triple boot ? i had also win7/ winxp on my hd, but altho it says windows 7 in the grub menu if i select it nothing happens just a cursor blinking. I can get into Ubuntu okay.

I looked at the forum here and saw someone being advised to get Bootinfo script.
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 595718 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2  and 
                       looks at sector 594998 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda6:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168  sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     24,226,020   988,865,009   964,638,990   7 HPFS/NTFS
/dev/sda2         988,865,010 1,953,520,064   964,655,055   7 HPFS/NTFS
/dev/sda3                  63    24,226,019    24,225,957   5 Extended
/dev/sda5                 126    23,101,469    23,101,344  83 Linux
/dev/sda6          23,101,533    24,226,019     1,124,487  82 Linux swap  / Solaris


Drive: sdf ___________________  _____________________________________________________

Schijf /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 koppen, 63 sectoren/spoor, 182401 cilinders, totaal 2930277168  sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


Drive: sdg ___________________  _____________________________________________________

Schijf /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168  sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdh ___________________  _____________________________________________________

Schijf /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168  sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE        LABEL                         

/dev/sda1        B45A63F35A63B0B2                       ntfs        Windows                       
/dev/sda2        16A4667AA4665BED                       ntfs        Data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f1cfad06-dec8-4656-a75b-c74a0f98b495    ext4                                     
/dev/sda6        7004358b-74ff-464e-9732-d054fc382a0d    swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        40E42EFCE42EF3B6                       ntfs        Elements 3                    
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        CA728A5F728A4FDD                       ntfs        Elements 2                    
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        C088818C88818220                       ntfs        Elements 1                    
/dev/sdh: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4        (rw,errors=remount-ro)
/dev/sdg1        /media/Elements 2_       fuseblk     (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdh1        /media/Elements 1_       fuseblk     (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdf1        /media/Elements 3_       fuseblk     (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini:  ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP  Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda5/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="14"
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, met Linux 2.6.32-22-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-22-generic (herstelmodus)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    echo    'Linux 2.6.32-22-generic laden ...'
    linux    /boot/vmlinuz-2.6.32-22-generic  root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, met Linux 2.6.31-20-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux    /boot/vmlinuz-2.6.31-20-generic  root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, met Linux 2.6.31-20-generic (herstelmodus)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    echo    'Linux 2.6.31-20-generic laden ...'
    linux    /boot/vmlinuz-2.6.31-20-generic  root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set  f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b45a63f35a63b0b2
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7004358b-74ff-464e-9732-d054fc382a0d none            swap     sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8  0       0

=================== sda5: Location of files loaded by Grub:  ===================


    .3GB: boot/grub/core.img
    .9GB: boot/grub/grub.cfg
  10.7GB: boot/initrd.img-2.6.31-20-generic
  11.0GB: boot/initrd.img-2.6.32-22-generic
   4.3GB: boot/vmlinuz-2.6.31-20-generic
   9.8GB: boot/vmlinuz-2.6.32-22-generic
  11.0GB: initrd.img
  10.7GB: initrd.img.old
   9.8GB: vmlinuz
   4.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard  drive==============

sdb sdc sdd sde 
```

---

### Post by wilee-nilee on 2010-05-12
Please edit the boot script by putting it in code tags. This may mean a new paste in a response that you highlight then click # in the reply gui. This will make it into a scrolling text much easier to read. If you do this then delete the original bootscript and we will read the new post.

---

### Post by kansasnoob on 2010-05-12
> It said if i didnt know what drive to mount i had to select all of them,

And drive designations end with letters like sda, sdb, sdc, etc.

Partition designations end with numbers like sda1, sda2, sdb1, etc.

It's almost never a good idea to install grub to a partition. That said I've filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

That said we can fix this, just give me time to parse all of the info, and in the meanwhile leave a comment on my bug report and mark it "effects me too". Just be nice :) Code of conduct and all that.

I'll go thru this all and get back here ASAP.

---

### Post by kansasnoob on 2010-05-12
OK, this should be simple. You have grub installed in both Windows OS's:

```
sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 595718 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda2  and 
                       looks at sector 594998 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter  Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
```

Since both OS's are on /dev/sda you should be able to run this fix only once:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Just be sure you select drive sda!

---

### Post by Ceejay34 on 2010-05-12
Thanks for your swift reply. I wasn aware this was a bug. I feel like adding i did use a beta of grub because i was scared to change it when i upgraded to koala last year.

What i had was grub booting, then id get in the windows 7 bootmanager if i selected the windows 7 option, where i could choose between windows 7 and windows xp. I didnt do any fancy boot or grub editing, i just installed xp first then windows 7 and finally ubuntu to get the triple boot. I figured i could install lucid lynx because it would pick up on the options it found in grub.

Edit

That was quick you were faster than me replying. Thanks i will try this right away and get back to you

---

### Post by wilee-nilee on 2010-05-12
> **kansasnoob said:**
> ok, this should be simple. You have grub installed in both windows os's:

```
sda1:  _________________________________________________________________________

    file system:       Ntfs
    boot sector type:  **[color="red"]grub 2[/color]**
    boot sector info:  [b][color="red"]grub 2 is installed in the boot sector of sda1  and 
                       looks at sector 595718 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location.[/color][/b] no errors found in the boot parameter  block.
    Operating system:  Windows xp
    boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /ntdetect.com

sda2:  _________________________________________________________________________

    file system:       Ntfs
    boot sector type:  **[color="red"]grub 2[/color]**
    boot sector info:  [b][color="red"]grub 2 is installed in the boot sector of sda2  and 
                       looks at sector 594998 of the same hard drive for  
                       core.img, but core.img can not be found at this 
                       location.[/color][/b] no errors found in the boot parameter  block.
    Operating system:  Windows 7
    boot files/dirs:   /windows/system32/winload.exe
```

since both os's are on /dev/sda you should be able to run this fix only once:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=boot_problems:boot_sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=boot_problems:boot_sector)

just be sure you select drive sda!

+1

---

### Post by darkod on 2010-05-12
Kansas, don't those instructions say:

Fifth   screen:  Select the Windows system partition  and choose "boot"

So you would need to run it for each partition right? In this case twice not once. Or I've missed the point of the fix?

---

### Post by kansasnoob on 2010-05-12
> **darkod said:**
> Kansas, don't those instructions say:

Fifth   screen:  Select the Windows system partition  and choose "boot"

So you would need to run it for each partition right? In this case twice not once. Or I've missed the point of the fix?

Yes, you're right. It's been a long day.

---

### Post by Ceejay34 on 2010-05-12
That didnt work. Still a - .You said do it once right. So i took the windows 7 disk... should i have done the windows xp disk? Im not sure which i should have done. Should i do them both?

I will do them both and get back to you

---

### Post by Ceejay34 on 2010-05-12
Both windows partitions have backup and regular bootsectors identical now.
I did set it back from the backup for the windows 7 bootsector. The windows xp bootsector was identical it said, so i didnt do anything

It still gives a cursor only

```

 menuentry "Windows 7 (loader) (on /dev/sda1)" {    
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set b45a63f35a63b0b2
 chainloader +1 ]
```Would it help if i removed the search line in grub?

---

### Post by wilee-nilee on 2010-05-12
Since you now have a slightly different setup run the bootscript again and post it.

---

### Post by oldfred on 2010-05-12
the boot sectors should not be identical for sda1. Your win7 boots thru the XP partition. the backup should be a windows boot sector and you have grub in it.

The next choice is to run fixboot. I do not know if you have to run XP's fixboot since it is originally an XP install or run the win7 fixboot since 7 combined its boots into the XP partition.

Based on what I see here I think you need to run the win7 repair on the XP partition since 7 puts its boot sector in:
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

These are all the commands but only run the fixboot and see it it works on the first windows install. If not then you may have to run them all and get windows booting on its own. Then reinstall grub.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by Ceejay34 on 2010-05-12
```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     24,226,020   988,865,009   964,638,990   7 HPFS/NTFS
/dev/sda2         988,865,010 1,953,520,064   964,655,055   7 HPFS/NTFS
/dev/sda3                  63    24,226,019    24,225,957   5 Extended
/dev/sda5                 126    23,101,469    23,101,344  83 Linux
/dev/sda6          23,101,533    24,226,019     1,124,487  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Schijf /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Schijf /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Schijf /dev/sdh: 1500.3 GB, 1500301910016 bytes
255 koppen, 63 sectoren/spoor, 182401 cilinders, totaal 2930277168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B45A63F35A63B0B2                       ntfs       Windows                       
/dev/sda2        16A4667AA4665BED                       ntfs       Data                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f1cfad06-dec8-4656-a75b-c74a0f98b495   ext4                                     
/dev/sda6        7004358b-74ff-464e-9732-d054fc382a0d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        CA728A5F728A4FDD                       ntfs       Elements 2                    
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        C088818C88818220                       ntfs       Elements 1                    
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        40E42EFCE42EF3B6                       ntfs       Elements 3                    
/dev/sdh: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdh1        /media/Elements 3_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdg1        /media/Elements 1_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdf1        /media/Elements 2_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

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
set default="14"
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
search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
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
search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, met Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-22-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    echo    'Linux 2.6.32-22-generic laden ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, met Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, met Linux 2.6.31-20-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    echo    'Linux 2.6.31-20-generic laden ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f1cfad06-dec8-4656-a75b-c74a0f98b495
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b45a63f35a63b0b2
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f1cfad06-dec8-4656-a75b-c74a0f98b495 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7004358b-74ff-464e-9732-d054fc382a0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
  10.7GB: boot/initrd.img-2.6.31-20-generic
  11.0GB: boot/initrd.img-2.6.32-22-generic
   4.3GB: boot/vmlinuz-2.6.31-20-generic
   9.8GB: boot/vmlinuz-2.6.32-22-generic
  11.0GB: initrd.img
  10.7GB: initrd.img.old
   9.8GB: vmlinuz
   4.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Now i have both the sda drives as windows7/vista. altho windows xp has different boot files. i dont get it. Still no boot. I will try testdisk once more then i will pull out the windows 7 disc

---

### Post by darkod on 2010-05-12
There is an easy way to test if your win7/winxp boot process is fine as you think it is now.

Since it's easy to reinstall grub2 to /dev/sda, put a generic mbr on it, and that should give you the windows bootloader on boot. Check if both win7 and winxp boot fine. If not, there is a problem booting windows alone.

You can set the generic mbr in ubuntu live mode with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you.

IMPORTANT NOTE: That will overwrite grub2 on the MBR and if the windows boot process is not fine you won't be able to boot any of the 3 OSs. But you can install grub2 back very easy from ubuntu live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by Ceejay34 on 2010-05-12
Thanks Darko, Kansasnoob and all you guys helping out. I am now on the dark side (Windows XP).

I had a flash of inspiration and saw that grub was also checking the external HD's i got. I have had trouble before with usb drives being checked for non existent boot sectors... And yes there they were in the boot sequence in my BIOS i turned off all USB drives in there, and i had my windows 7 boot menu back, instead of a cursor. 

So Kansasnoobs fix did the trick afterall. What i now need to do is get grub to stop checking for my usb drives and then no more probs i hope. Thanks again the Ubuntu Community ROCKS

---

### Post by kansasnoob on 2010-05-13
> **Ceejay34 said:**
> Thanks Darko, Kansasnoob and all you guys helping out. I am now on the dark side (Windows XP).

I had a flash of inspiration and saw that grub was also checking the external HD's i got. I have had trouble before with usb drives being checked for non existent boot sectors... And yes there they were in the boot sequence in my BIOS i turned off all USB drives in there, and i had my windows 7 boot menu back, instead of a cursor. 

So Kansasnoobs fix did the trick afterall. What i now need to do is get grub to stop checking for my usb drives and then no more probs i hope. Thanks again the Ubuntu Community ROCKS

As long as the external drives are plugged in when "update-grub" is run (either manually or automatically when required by updates) grub2 will search all drives. Normally that shouldn't be a problem.

---

### Post by oldfred on 2010-05-13
Just for curosity what does you device.map look like.

Typical:
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

If it has all the external you may want to update it with all the USBs unplugged.
You can edit it or:
sudo grub-mkdevicemap
sudo update-grub

---

