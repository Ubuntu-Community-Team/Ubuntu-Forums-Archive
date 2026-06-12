---
title: "GRUB2 + Windows 7"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by MadRyNe on 2011-01-12
Hello there!
I am newbie in Linux and Ubuntu. Need qualified help :)  I've installed Ubuntu on my first drive. And I have Windows 7 on second drive. At the begining the problem was that GRUB2 didn't see Win7 loader. I red GRUB2 manual and find solution which says to add some text to the file /etc/grub.d/40_custom. So I did this and here is my 40_custom content:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[B]menuentry "Win 7" {
insmod chain
set root=(hd1,1)
drivemap -s hd0 hd1
chainloader +1
}[/B]

```(bold text is which I added to this file)

Next, I perform **sudo update-grub** and reboot. Here I've got second problem: when my comp loads, grub2 loader doesn't show even if I push SHIFT button. So what should I do now? :) Please help!
P.S.: here is RESULTS.txt after running **boot_info_script055.sh** script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

&#1044;&#1080;&#1089;&#1082; /dev/sda: 320.1 &#1043;&#1041;, 320072933376 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 38913 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 625142448 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sda2          39,063,552    44,922,879     5,859,328  82 Linux swap / Solaris
/dev/sda3          44,922,880    83,984,383    39,061,504  83 Linux
/dev/sda4          83,984,384   625,141,759   541,157,376  83 Linux


Drive: sdb ___________________ _____________________________________________________

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 1000.2 &#1043;&#1041;, 1000204886016 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 121601 cylinders, &#1074;&#1089;&#1077;&#1075;&#1086; 1953525168 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0a000778-7b6c-4c7a-9bb9-6089f33ff2e2   ext4                                     
/dev/sda2        e58e15f0-4c61-46e6-8b2a-138510df22aa   swap                                     
/dev/sda3        a31adc34-f2e6-40c9-91ad-d971bdcfaec5   ext4                                     
/dev/sda4        94825e03-4d14-4190-9068-c8c50a19942e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C02CB7302CB71FF8                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /home                    ext4       (rw,commit=0)
/dev/sda3        /var                     ext4       (rw,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
set locale_dir=($root)/boot/grub/locale
set lang=ru
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0a000778-7b6c-4c7a-9bb9-6089f33ff2e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0a000778-7b6c-4c7a-9bb9-6089f33ff2e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0a000778-7b6c-4c7a-9bb9-6089f33ff2e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0a000778-7b6c-4c7a-9bb9-6089f33ff2e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0a000778-7b6c-4c7a-9bb9-6089f33ff2e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Win 7" {
insmod chain
set root=(hd1,1)
drivemap -s hd0 hd1
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0a000778-7b6c-4c7a-9bb9-6089f33ff2e2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=94825e03-4d14-4190-9068-c8c50a19942e /home           ext4    defaults        0       2
# /var was on /dev/sda3 during installation
UUID=a31adc34-f2e6-40c9-91ad-d971bdcfaec5 /var            ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=e58e15f0-4c61-46e6-8b2a-138510df22aa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.1GB: boot/grub/core.img
  15.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
    .7GB: boot/initrd.img-2.6.35-24-generic
  13.1GB: boot/vmlinuz-2.6.35-22-generic
  13.4GB: boot/vmlinuz-2.6.35-24-generic
    .7GB: initrd.img
    .7GB: initrd.img.old
  13.4GB: vmlinuz
  13.1GB: vmlinuz.old

```

---

### Post by Quackers on 2011-01-12
Welcome to UF :-)
Firstly, I would have thought that sdb1 should have a boot flag attached.
Secondly, 2 of Win 7's boot files are missing from sdb1. To repair Win 7 I would set a boot flag (with gparted) on sdb1, then run Startup repair (from the Win 7 repair disc) up to 3 times - after setting the bios to boot from the Windows drive.

---

### Post by dino99 on 2011-01-12
to see the grub menu, you need to hold "shift" key down at end of bios process. But you should see it by default as its a dual boot system. So try with something else than (hd1,1)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

(look at "creating the custom menu")

---

### Post by MadRyNe on 2011-01-14
> **Quackers said:**
> Welcome to UF :-)
Firstly, I would have thought that sdb1 should have a boot flag attached.
Secondly, 2 of Win 7's boot files are missing from sdb1. To repair Win 7 I would set a boot flag (with gparted) on sdb1, then run Startup repair (from the Win 7 repair disc) up to 3 times - after setting the bios to boot from the Windows drive.

Thank you for advice. After setting the 'boot' flag on sdb1, GRUB2 has launched normally with WIN7 menu entry.
And, as you've told me, I've some problem with Win7's boot files. So I tried to fix it with Win7 Repair CD. I ran "StartUp Repair" up to 5 times, every time it found different kinds of errors on windows partition. At 4th time this utility performed system recover from last point, then after reload thinked a lot and said "Windows can't automatically repair this error.". Though a run "Startup repair" again and utility start checking filesystem. As it seems very boring to me I decided to continue repair another time :) 
P.S.: Ubuntu Disk Utility says that sdb1 has crushed cluster, so it seems I need fix it. Any advice? It will be normal if I'll do it from Recovery CD? :)

---

### Post by oldfred on 2011-01-14
One disadvantage of large system (or any partition) is that the system check can take forever. But too small partitions can make for difficulty on full partitions and having to reorganize too often. Its a trade-ff. Some use LVM - logical volume, but that adds complexity.

You have to run chkdsk from a windows Cd and have to run chkdsk until there are no errors as it does not fix everything on one pass.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by MadRyNe on 2011-01-14
> **oldfred said:**
> One disadvantage of large system (or any partition) is that the system check can take forever. But too small partitions can make for difficulty on full partitions and having to reorganize too often. Its a trade-ff. Some use LVM - logical volume, but that adds complexity.

You have to run chkdsk from a windows Cd and have to run chkdsk until there are no errors as it does not fix everything on one pass.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


Thank you for useful information.:) I hope chkdsk will solve my problem.

---

### Post by MadRyNe on 2011-01-24
It seems that my second drive (1TB sdb) have too many crushed clusters. I think that is the only problem now, so it seems that the trouble with GRUB2 + Win7 **is solved**. The solution is: just using "sudo update-grub". In case if grub2 doesn't see win7 loader maybe is useful adding manually menuenty to the "40_custom" file and then doing "sudo update-grub" again.

But here is still another question: how could Ubuntu Installer damage my hard drive? (before installing Ubuntu Win7 worked perfectly). I thought before that it could only kill MBR or delete 'boot' flag from Windows partition or something in that way.
After this case I've decided not to connect (physically) hardrive with installed another OS on it to my PC (or not to mount partition with OS due Ubuntu install if OS is installed on the same harddrive) and then manually add OS's loader to grub2. I think this is the most rational way if I want to guarantee succesfull run all operating systems.

If there isn't any advices, I'll set 'solved' flag on this thread.
Thanks to everybody!

---

