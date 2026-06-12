---
title: "Dual Boot Problems with x2 sata drives"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by storm_808 on 2011-04-14
[LEFT]Hi 

I have recently built a new system which has two internal sata drives. The plan was to install windows 7 one drive and ubuntu 10.10 on the second drive for KVM hosts. 

I started with the windows install which completed, then I went forward and installed ubuntu 10.10 64bit to my second drive (sdb). During the installation I chose to manually partition my drive. i partitoned the drive (sdb) as follows

/boot - 1gb
/ 40gb
swap 16gb
extended partion of 400gb

I then selected sdb to hold the boot record, as it was set by default to sda (my windows drive). The OS installed fine. I then went to reboot my system so go back into windows, by selecting the first drive in the bios.  Once selected the  system keeps booting into Ubuntu, no matter which drive I select. Now I checked the grub.cfg file and i see all references to hd1 there is no reference for windows found. I then proceeded to do 'sudo update grub2' this did not pickup any reference to my windows droive to add to the grub menu. 

When i select the ubuntu drive to boot fom my bios, i get no grub menu appaer it just boots quite happily into ubuntu. Can anyone please provide any resoloution to this, I can provide additonal outputs regarding my partion tables etc. later this evening when I get back from work.

Any help would be much appraciated.



 
[/LEFT]

---

### Post by Quackers on 2011-04-14
Welcome to UF.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-04-14
> **storm_808 said:**
> [LEFT]...I then proceeded to do 'sudo update grub2' this did not pickup any reference to my windows droive to add to the grub menu.

The command is "sudo update-grub" -- different spelling than what you used. Try this command, instead.  Should work.

---

### Post by storm_808 on 2011-04-14
> **Quackers said:**
> Welcome to UF.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks for this, I will get it done as soon as I get back home today, and post my results

---

### Post by storm_808 on 2011-04-14
> **Mark Phelps said:**
> The command is "sudo update-grub" -- different spelling than what you used. Try this command, instead.  Should work.

Hi Mark 

What you have stated is what I typed in, I made the mistake in my post. Like I said there was no reference to my windows environment when I ran the command.

---

### Post by storm_808 on 2011-04-14
Hi 
See below  the output from the boot script
         ```

         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   485,378,047   485,376,000   7 HPFS/NTFS
/dev/sda2         485,378,048   976,769,023   491,390,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     2,000,895     1,998,848  83 Linux
/dev/sdb2           2,000,896    82,001,919    80,001,024  83 Linux
/dev/sdb3          82,001,920   114,001,919    32,000,000  82 Linux swap / Solaris
/dev/sdb4         114,003,966   976,771,071   862,767,106   5 Extended
/dev/sdb5         114,013,305   323,725,814   209,712,510  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9E48D9D748D9AE71                       ntfs                                     
/dev/sda2        5224A011249FF667                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        873a609f-080f-4b00-b339-3bc6bbc5347f   ext3                                     
/dev/sdb2        0c2e3485-2fc1-4e2b-91f7-05a314f3aa86   ext3                                     
/dev/sdb3        21554e4d-8946-407e-95a2-5e18f2dcfbaa   swap                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        75b887c1-3615-4256-a3b2-1644531c56eb   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /boot                    ext3       (rw,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 0c2e3485-2fc1-4e2b-91f7-05a314f3aa86
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 873a609f-080f-4b00-b339-3bc6bbc5347f
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 873a609f-080f-4b00-b339-3bc6bbc5347f
    linux    /vmlinuz-2.6.35-22-generic root=UUID=0c2e3485-2fc1-4e2b-91f7-05a314f3aa86 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 873a609f-080f-4b00-b339-3bc6bbc5347f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=0c2e3485-2fc1-4e2b-91f7-05a314f3aa86 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 873a609f-080f-4b00-b339-3bc6bbc5347f
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 873a609f-080f-4b00-b339-3bc6bbc5347f
    linux16    /memtest86+.bin console=ttyS0,115200n8
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .8GB: grub/core.img
    .8GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=0c2e3485-2fc1-4e2b-91f7-05a314f3aa86 /               ext3    errors=remount-ro 0       1
/dev/sdb1       /boot           ext3    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=21554e4d-8946-407e-95a2-5e18f2dcfbaa none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


   1.0GB: initrd.img
   1.0GB: vmlinuz



```

---

### Post by storm_808 on 2011-04-14
Hi 

Ok from the boot info script i noticed that the boot flag was missing from sda1, so i applied it via gparted. Now the system boots but stops at bootmgr missing, i think i may of lost my windows install

---

### Post by storm_808 on 2011-04-14
> **storm_808 said:**
> Hi 

Ok from the boot info script i noticed that the boot flag was missing from sda1, so i applied it via gparted. Now the system boots but stops at bootmgr missing, i think i may of lost my windows install

Ok just another update, I managed to fix the problem by booting of a win cd and doing a fix on the mbr. Everything now works:P , but..... I would like to know for future reference what would be the best approach to do this type of install. Maybe disconnecting the windows drive from the system???. I still mythed how this happened, I specifically stated in the partitoner not to make any boot changes to sda. :confused:

My only other minor issue is, I have to go into my bios each time to change the boot order to decide which OS i boot into, my grub menu when i boot into ubuntu is still not displaying. It would be ideal to place the ubuntu drive as the primary boot drive and then have grub to provide me with the option to which OS to launch. Any ideas??:?:

---

### Post by storm_808 on 2011-04-14
Final Update.... I fixed it ran the grub2 update and my windows drive was picked up. Changed the boot order in bios,, and voila!!! grub menu appears with both my ubuntu/windows OS's.. Great learning curve on grub2 :)... now onto to KVM stuff. Thanks again

---

### Post by oldfred on 2011-04-14
You may have had drive order different. Windows 7 normally installs to two partitions. A small boot/recovery of 100MB that in windows is hidden. But since your main install was sda1 the boot partition was probably on the other drive. 

Your moving boot flag to main partition and running win repairs was exactly the correct solution as it moves the missing boot files to the main install. The main reason windows has a separate /boot was so you could encrypt the main install. Perhaps also when main install is corrupted you can still get to the repair functions in the boot/recovery partition.

---

