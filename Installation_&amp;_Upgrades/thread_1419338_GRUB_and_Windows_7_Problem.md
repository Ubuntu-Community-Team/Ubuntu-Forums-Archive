---
title: "GRUB and Windows 7 Problem"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by gingivere on 2010-03-01
I've been using Ubuntu for a couple of months and yesterday I got a new laptop which came pre-installed with Windows 7.  Upon getting Windows 7 up and running, I immediately installed Ubuntu 9.10 Karmic.  After getting Ubuntu running, I am now no longer able see Windows 7 in GRUB2, though I can still access the files through nautilus.  Also, GRUB2 shows that I have 4 different Linux installations; "Ubuntu, Linux, 2.6.31-19"; "Ubuntu, Linux, 2.6.31-19 recovery mode" (I'm not sure of the exact notation, but its just a recovery mode for -19); "Ubuntu, Linux, 2.6.31-14"; "Ubuntu, Linux, 2.6.31-14", and "Ubuntu, Linux, 2.6.31-14 recovery mode (again, not exact but you get the picture).  After these there are 2 memtest options and a Windows Vista Loader that is meant to recover the Windows 7 system, but since the computer can't get to these files, it's useless.  Sorry for being so wordy, but is there anyway that I can make Windows 7 boot from GRUB2 because everything that I've searched hasn't helped any. 

Thank you for reading and for commenting!

---

### Post by darkod on 2010-03-01
Follow these instructions and post the content of the results file, it will show more details:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Ubuntu looks for boot files and I guess it can't see the win7 boot files out of what ever reason. Maybe if you didn't shrink the win7 partition first using windows Disk Management but instead used the side-by-side option in the ubuntu installer, that can sometimes corrupt the win7 partition.

---

### Post by gingivere on 2010-03-01
Thanks for the speedy reply!  Here is the info from the script you told me to run.  Also I did shrink the Windows 7 partition from inside Windows 7.





```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1013cbb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845  82 Linux swap / Solaris
/dev/sda3    *     25,382,700   277,538,939   252,156,240   7 HPFS/NTFS
/dev/sda4         429,786,945   488,392,064    58,605,120   5 Extended
/dev/sda5         429,803,010   488,392,064    58,589,055  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70C40E55C40E1E4A                       ntfs       PQSERVICE                     
/dev/sda2        3a8b374a-5b41-4443-bbb7-bfb342f533d3   swap                                     
/dev/sda3        54000FC7000FAED4                       ntfs       eMachines                     
/dev/sda5        fbf9272a-5b13-437e-867d-6a09b0c7bd85   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sda3        /dos                     fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

# This entry automatically added by the Ubuntu installer for a non-linux OS
# on /dev/sdb1
title Windows 7
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set fbf9272a-5b13-437e-867d-6a09b0c7bd85
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fbf9272a-5b13-437e-867d-6a09b0c7bd85
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=fbf9272a-5b13-437e-867d-6a09b0c7bd85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fbf9272a-5b13-437e-867d-6a09b0c7bd85
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=fbf9272a-5b13-437e-867d-6a09b0c7bd85 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fbf9272a-5b13-437e-867d-6a09b0c7bd85
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fbf9272a-5b13-437e-867d-6a09b0c7bd85 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fbf9272a-5b13-437e-867d-6a09b0c7bd85
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fbf9272a-5b13-437e-867d-6a09b0c7bd85 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd2,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 70c40e55c40e1e4a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom_backup ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom_backup ###

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
UUID=fbf9272a-5b13-437e-867d-6a09b0c7bd85 /               ext3    errors=remount-ro 0       1
# /dos was on /dev/sda3 during installation
UUID=54000FC7000FAED4 /dos            ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
UUID=3a8b374a-5b41-4443-bbb7-bfb342f533d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 232.3GB: boot/grub/core.img
 232.3GB: boot/grub/grub.cfg
 232.3GB: boot/grub/menu.lst
 232.4GB: boot/initrd.img-2.6.31-14-generic
 232.3GB: boot/initrd.img-2.6.31-19-generic
 232.3GB: boot/vmlinuz-2.6.31-14-generic
 232.3GB: boot/vmlinuz-2.6.31-19-generic
 232.3GB: initrd.img
 232.4GB: initrd.img.old
 232.3GB: vmlinuz
 232.3GB: vmlinuz.old
```

---

### Post by darkod on 2010-03-01
Before we start: What is /dev/sda1, a recovery partition? You didn't by any chance cut your win7 partition in two by inserting a swap partition right?

1. This looks like clean install of 9.10, why do you have menu.lst in /boot/grub? It doesn't use it any more in grub2.
If you created it manually, move it from /boot/grub into your home folder for example. It doesn't need to be there.

2. Your manual 11_windows file is wrong, it needs to be:
set root=(hd0,3)

if your win7 system partition is /dev/sda3 and the boot files need to be there.
You have only one hdd, where did you come up with hd2?

3. As I said, you seem to be missing win7 boot files, only winload.exe is on /dev/sda3. There needs to be /bootmgr and /boot/BCD. Files with those names exist in /dev/sda1 but I guess that's recovery partition, right?

4. Boot the ubuntu live desktop (Try Ubuntu option from the cd, not the hdd) and in Gparted remove the boot flag from the swap partition /dev/sda2. Leave the boot flag on /dev/sda3. You might need to right-click /dev/sda2 and do Swapoff before you can remove the boot flag.

5. Repair the win7 boot process using the manual commands as explained here (not the automatic mode):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have win7 install dvd to use get a repair cd here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

This procedure will overwrite grub2 from the MBR. After you make sure your win7 can boot properly, continue with restoring grub2 to the MBR.

6. Boot again in ubuntu live desktop and to restore grub2 execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

I hope I didn't miss anything. So much things to repair. :) It might sound scary but it's not.

---

### Post by oldfred on 2010-03-01
Somehow you have two boot flags. You can only have one and windows needs that on the boot partition whether sda1 or sda3? You can use gparted to turn off the extra boot flag or you can use this in ubuntu:

set boot flag on for sda[COLOR=Red]2[/COLOR] (off on others)
sudo sfdisk -A[COLOR=Red]2[/COLOR] /dev/sda

---

### Post by gingivere on 2010-03-01
I followed all of your directions but after step 4, my grub doesnt have any options, and i dont know how to fix what i did from live cd because i get a permissions error

---

### Post by meierfra. on 2010-03-01
> 5. Repair the win7 boot process using the manual commands as explained here (not the automatic mode):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have win7 install dvd to use get a repair cd here:
[http://neosmart.net/blog/2009/window...-repair-discs/](http://neosmart.net/blog/2009/window...-repair-discs/)

This procedure will overwrite grub2 from the MBR. After you make sure your win7 can boot properly, continue with restoring grub2 to the MBR.

Please do **not** follow that  procedure. It will not restore the file "bootmgr".

Instead  just run "startup repair" on the Windows 7 DVD.  It will restore all the boot  files and you won't have to reinstall Grub.


> sudo sfdisk -A2 /dev/sda 


The boot flag needs to be set  to /dev/sda3. So you need to use

```
sudo sfdisk -A3 /dev/sda 
```



> I followed all of your directions but after step 4, my grub doesnt have any options, and i dont know how to fix what i did from live cd because i get a permissions error

What kind of permission error? How are your trying to fix the problem?

Please run the boot info script from the LiveCD and post the new RESULTS.txt?

---

### Post by gingivere on 2010-03-01
I dont have windows 7 install dvd, and when i try to run the recover cd, grub says file not found.  And forget the permission error thing, i worked around it and what i was doing did nothing anyway.   Ill post that boot info in a sec

---

### Post by gingivere on 2010-03-01
On second thought, I dont have internet on my live cd, and i cant access the boot script.  I have no clue what to do :(((

---

### Post by meierfra. on 2010-03-01
> Then i try to run the recover cd, grub says file not found.  
Did you set the bios to boot from the CD drive? You might download the recovery CD from darkrod's link again and burn the CD at  the slowest speed (4x)
 (but we'll worry about this later. First we have to get Ubuntu to boot again)


> I dont have internet on my live cd, 
OK. Lets see whether we can boot Ubuntu without the LiveCD.

What exactly happens when you try to boot into Ubuntu. Do you get the Grub Menu?  Or a "grub:sh> " prompt?  Or a "grub:rescue>"  prompt.

---

### Post by gingivere on 2010-03-01
bios can boot from cd, because i can use an ubuntu live cd.  When i try to boot from hdd it says
"GRUB loading.
 error: file not found
 grub rescue>

---

### Post by meierfra. on 2010-03-01
Strange.  

Try this at the "grub rescue>" prompt

```

set root=(hd0,5)
set prefix=(hd0,5)/boot/grub
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

```

---

### Post by gingivere on 2010-03-01
it says it doesnt recognize the filesystems ext2 and linux

---

### Post by gingivere on 2010-03-01
oh, wait.  I did some that i found on another thread and it came up with a different grub version.  Now it says 
"GNU GRUB  version 1.97~beta4
[   Minimal BASH--like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions.  ]
 
sh:grub>"

---

### Post by meierfra. on 2010-03-01
Try the set of commands from my last post at the "sh>grub" prompt.

---

### Post by gingivere on 2010-03-01
Works fine until i type "insmod ext2", there it says "error: unknown filesystem".  BTW that partition is ext3, not ext2 ( idk if the two are related at all, just tryin to recognize a pattern) but "insmod ext3" gives the same result.  "insmond linux" does the same as set root and set prefix commands do.  The 5th line gives me "error:  unknown filesystem". "initrd /initrd.img" says "error:  you need to load the kernel first.".  and "boot" says "error: no loaded kernel"

---

### Post by meierfra. on 2010-03-01
> BTW that partition is ext3, not ext2
Grub uses the "ext2" module for ext2, ext3 and ext4. So "insmod ext2" is the correct command.


> error: unknown filesystem".

Strange.

Try this: Download the boot info script on a different computer. Put it on a flash drive. Boot from the LiveCD, move the script from the flash drive  to  the desktop and then run the script as before.

---

### Post by gingivere on 2010-03-01
i'm just going to reformat the ubuntu part of the partition, do you think this will work?  I just installed ubuntu yesterday, so i wont lose any info.

---

### Post by meierfra. on 2010-03-01
It should.
Post a new RESULTS.txt after reinstalling, so I can give you detailed instruction how to fix Windows 7.

---

### Post by darkod on 2010-03-02
Sorry for the bad advice earlier, I thought the manual procedure also recovers /bootmgr. Haven't used windows tools too much.

If you decide to reinstall, it would be good to reconsider your hdd layout too.
The first strange fact is how did swap end up between sda1 and sda3, your windows install.
Also, I just noticed in your original results file, you have a big gap of unallocated space between sda3 and sda4, at least according to the start/end data. And because you already have 4 partitions created you can't just create a new one there, so it will sit wasted. Maybe you could create a logical partition and that should merge it into sda4 I guess.

Any way you decide, you should use whole of your hdd space.

---

### Post by gingivere on 2010-03-02
Ok, I reinstalled ubuntu using the same layout as before.  It reset my grub to exactly how it was whenever I first posted.  Here is the RESULTS.txt after the install. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1013cbb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2          25,173,855    25,382,699       208,845  82 Linux swap / Solaris
/dev/sda3    *     25,382,700   277,538,939   252,156,240   7 HPFS/NTFS
/dev/sda4         312,592,770   488,392,064   175,799,295   5 Extended
/dev/sda5         312,608,835   488,392,064   175,783,230  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70C40E55C40E1E4A                       ntfs       PQSERVICE                     
/dev/sda2        3a8b374a-5b41-4443-bbb7-bfb342f533d3   swap                                     
/dev/sda3        54000FC7000FAED4                       ntfs       eMachines                     
/dev/sda5        94ce527b-e893-4dcf-aac7-fc9d0f847a80   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=seth)


=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 94ce527b-e893-4dcf-aac7-fc9d0f847a80
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 94ce527b-e893-4dcf-aac7-fc9d0f847a80
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=94ce527b-e893-4dcf-aac7-fc9d0f847a80 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 94ce527b-e893-4dcf-aac7-fc9d0f847a80
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=94ce527b-e893-4dcf-aac7-fc9d0f847a80 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 94ce527b-e893-4dcf-aac7-fc9d0f847a80
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=94ce527b-e893-4dcf-aac7-fc9d0f847a80 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 94ce527b-e893-4dcf-aac7-fc9d0f847a80
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=94ce527b-e893-4dcf-aac7-fc9d0f847a80 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 70c40e55c40e1e4a
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
UUID=94ce527b-e893-4dcf-aac7-fc9d0f847a80 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=3a8b374a-5b41-4443-bbb7-bfb342f533d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 222.5GB: boot/grub/core.img
 222.5GB: boot/grub/grub.cfg
 222.5GB: boot/initrd.img-2.6.31-14-generic
 222.4GB: boot/initrd.img-2.6.31-19-generic
 222.5GB: boot/vmlinuz-2.6.31-14-generic
 222.4GB: boot/vmlinuz-2.6.31-19-generic
 222.4GB: initrd.img
 222.5GB: initrd.img.old
 222.4GB: vmlinuz
 222.5GB: vmlinuz.old
```

---

### Post by gingivere on 2010-03-02
ps. sorry for the late reply, it was late last night when the thing finished installing and downloading needed updates and I had school today so this is the earliest i could post :)

---

### Post by darkod on 2010-03-02
The win7 boot files are still missing on /dev/sda3. Use your win7 install dvd, boot with it, and after the language selection screen you should see Repair This Computer option at the bottom. Use that to try repair your win7 boot process.

If you don't have install dvd get a repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by meierfra. on 2010-03-02
> Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img


Just to make life more interesting,  you somehow managed to create a Grub folder on the Window 7 partition. No a big deal, but it needs to be deleted to avoid confusions:

```
sudo mount /dev/sda3 /mnt
sudo   rm -r /mnt/boot
```


The boot flag is on the correct partition by now.  So that's one thing we don't have to worry about any more.


Are you able to boot from the Window Recovery CD?

If yes. Boot from the CD.

At the first screen select your favorite language.
At the second screen choose "Repair your Computer".

If a pop up  appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".

Otherwise, on the  next screen select "Use recovery tools ..."  and click on "Next".
Choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

After running startup repair, boot into Ubuntu and run

```
sudo update-grub
```

That should be all.

---

### Post by gingivere on 2010-03-02
I'm burning the iso right now. Thank you for all the help :D

---

### Post by gingivere on 2010-03-02
Yes! It worked!!!  I am now able to boot to both Ubuntu and Windows 7 from GRUB!!!
Now you said earlier that I should make Ubuntu use the rest of my hard drive.  I'm fine with increasing its partition size, as I'm not planning on using this for anything else.  How can I increase the partition size of Ubuntu without messing up anything else? 
Again, Thank you soooooooo much!! :D:D:D:D:D

---

### Post by meierfra. on 2010-03-02
> How can I increase the partition size of Ubuntu without messing up anything else? 
You have about 22GB of unallocated space. A few  options:

[list=1]
[*]  Expand  the extended partition /dev/sda4. Then use the unallocated space to  create a new Data partition (either ntfs or ext4)

[*] Expand  the extended partition /dev/sda4. Then use the unallocated space to expand your ubuntu partition  /dev/sda5.

[*] Use the unallocated space  to expand your Window 7 partition /dev/sda3.

[*]  Delete your Ubuntu partition /dev/sda5 and the swap partition /dev/sda2.  Expand the  extended  partition and reinstall Ubuntu (mabye creating Data and/or Home partitions. If you  have Home or Data partition you Ubuntu partition only needs to be about 20GB) Create a new Swap partition inside the extended partition. 

[*] Leave it as is and wait  until you find a good use for the unallocated space.
[/list]

I don't like option 2. Moving  the start point  of Ubuntu partition  will take quite a while, so you might as well reinstall.

Option 5 certainly is a decent choice. 

 Although you should do something about your swap partition.  Sitting between Win 7 and the recovery partition is not a problem.  but its only 100MB.  A  swap partition should be larger to be useful. (I guess the 100MB partition used to be your  Win 7 boot partition )

The 100 MB partition is even to small for Ubuntu boot partition (unless you keep deleting kernels).  So I would just leave it unallocated (adding it to the recovery partitions makes no sense, and moving the start point of the Win 7 partition will lead to booting problems)

So my vote is for Option 4.

---

### Post by gingivere on 2010-03-02
Sorry, but what is a home partition?

---

### Post by gingivere on 2010-03-02
Couldn't i just delete the ubuntu partition and then install it to use the entire free space?

---

### Post by meierfra. on 2010-03-03
> Couldn't i just delete the ubuntu partition and then install it to use the entire free space? 
No, if you only delete the ubuntu partition,  the largest available free space will be confined to  your extended partition /dev/sda4.  So the unallocated space between /dev/sda3 and /dev/sda4 will not be used.  Also Ubuntu will use your current swap partition /dev/sda2 as the swap partition. 

So you need to delete the ubuntu partition, the extended partition and the swap partition.  After that installing to the largest available free space will give you a decent setup.


But you might consider a [home partition]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by gingivere on 2010-03-03
Ok, what I did was delete the ubuntu partition and the reinstall it to make it take up the extra 20 gig.  Then i deleted the 100mb swap and moved it behind the windows partition and increased the size to 5gb. I'm happy with it like it is now, because im using up my complete hard drive and the swap partition is more appropriately sized :)  Thank you SOOO much for all the help!! :D

---

### Post by meierfra. on 2010-03-03
> Then i deleted the 100mb swap and moved it behind the windows partition and increased the size to 5gb. 


There is some chance  that you are not using the swap partition. Run

```
free
```

If it shows  your "total" swap as "0", please run the boot info script again and  post the RESULTS.txt.

---

### Post by gingivere on 2010-03-04
It does show I'm using my swap :)  It says swap: 5807424 used.   Thank you :)

---

### Post by meierfra. on 2010-03-04
> 5807424 used. 
I hope it says "5807424  total"and not "5807424 used"  If your were using 5GB of swap, your computer would run really slow.  More likely you are not actually  using any of the swap.

---

### Post by gingivere on 2010-03-05
Oh, yeah my fault.  It does say that much total, not used :p

---

