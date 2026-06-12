---
title: "Getting Windows Back After Installing Ubuntu"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by daquietmonkey on 2010-10-07
Greetings Everyone

I hope everyone is doing great. I recently installed Ubuntu on my laptop which came with Windows 7 preloaded. How I did it is that I created a new parition for Ubuntu on the same harddisk which had windows installed on a separate parition and installed Ubuntu on the new parition and made it the primary partition. The windows is still lying on its own partition.

I would like to get some advice on how to get windows working as well without loosing the Ubuntu installation.  

Would be great if I can get both working aside.

Thank you 
Imran

---

### Post by andrewthomas on 2010-10-07
Open a terminal, enter (alt + F2 then check run in terminal) 

```
sudo update-grub
```

does it pick up your windows?

Post the output of the above command

---

### Post by daquietmonkey on 2010-10-08
Greetings Andrew

Hope you are doing great and I really appreciate your assistance. May  Allah enlighten us. Alrite this is the output I am getting:

imran@imranlaptop:~$ sudo update-grub
[sudo] password for imran: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Piece of the puzzle?

---

### Post by sikander3786 on 2010-10-08
Assalam O Alaikum Imran. Welcome to the forums :popcorn:

Can you please post the output of bootinfo script as per instructions from the following page. You'll need to boot into a Live CD to do that. That will give us a better idea of your partitioning setup thus helping us to diagnose the problem.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by daquietmonkey on 2010-10-08
Aoa Sikander
Hope you are doing great. Really appreciate your assistance. Allah kamyaab karin. Alrite buddy this is the output from the script:

[COLOR=Navy]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       465827839 sectors, but according to the info from 
                       fdisk, it has 506128431 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
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

/dev/sda1    *             63         2,047         1,985   0 Empty
/dev/sda2               4,094       407,551       403,458   5 Extended
/dev/sda5               4,096       407,551       403,456  82 Linux swap / Solaris
/dev/sda3             409,600   470,642,687   470,233,088  83 Linux
/dev/sda4         470,642,688   976,771,119   506,128,432  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32    15,625,215    15,625,184   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda3        c6030e3d-2825-42d5-929a-32a50d2b63d8   ext4                                     
/dev/sda4        7C960B04960ABF20                       ntfs                                     
/dev/sda5        21203e43-aa28-45e2-8787-bf7dd6ed9c6d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        801D-797C                              vfat       e('new'); }                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/c6030e3d-2825-42d5-929a-32a50d2b63d8 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c6030e3d-2825-42d5-929a-32a50d2b63d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=c6030e3d-2825-42d5-929a-32a50d2b63d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c6030e3d-2825-42d5-929a-32a50d2b63d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=c6030e3d-2825-42d5-929a-32a50d2b63d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set c6030e3d-2825-42d5-929a-32a50d2b63d8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=c6030e3d-2825-42d5-929a-32a50d2b63d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=21203e43-aa28-45e2-8787-bf7dd6ed9c6d none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 148.5GB: boot/grub/core.img
 103.6GB: boot/grub/grub.cfg
 148.6GB: boot/initrd.img-2.6.32-24-generic
 148.7GB: boot/initrd.img-2.6.32-25-generic
 148.6GB: boot/vmlinuz-2.6.32-24-generic
 148.7GB: boot/vmlinuz-2.6.32-25-generic
 148.7GB: initrd.img
 148.6GB: initrd.img.old
 148.7GB: vmlinuz
 148.6GB: vmlinuz.old[/COLOR]

JazakAllah for your assistance.

Imran

---

### Post by Rubi1200 on 2010-10-08
For future reference, please wrap the text with the # tag; it makes for easier reading.

Well, I hope you have your Windows installation/recovery disc because it looks as if you may have wiped it out somehow.

> [COLOR=Navy]/dev/sda1    *             63         2,047         1,985   0 _Empty_[/COLOR]Also, I am not sure why you have this file system on sda4; did you set it up this way?

> [COLOR=Navy]/dev/sda4         470,642,688   976,771,119   506,128,432  _42 SFS_[/COLOR]Take a look at sda1 and sda4; no file system and no Wndows boot files.

You can try, _first_, to recover the Windows installation using Testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If that does not work, you will have little choice but to reinstall Windows and then Ubuntu.

If that is the case, ask here first and we can advise you on the best way to go about it.

Good luck and keep us informed.

---

### Post by sikander3786 on 2010-10-08
Hi Imran.

I had asked Rubi to take a look at your thread as he is lot more experienced with bootinfoscript than me.

As Rubi mentioned, we can't see any Windows boot files on sda4 which were supposed to be there.

[COLOR="Blue"]@Rubi[/COLOR]

If he has a Windows 7 disc, booting off it and selecting to Repair Startup (or something like that, I don't remember the exact phrase) would help? And later Grub can be re-installed. What do you think?

---

### Post by Rubi1200 on 2010-10-08
> **sikander3786 said:**
> [COLOR=Blue]@Rubi[/COLOR]

If he has a Windows 7 disc, booting off it and selecting to Repair Startup (or something like that, I don't remember the exact phrase) would help? And later Grub can be re-installed. What do you think?

Hi sikander, I have never used Windows 7, but I believe that is definitely an option worth trying.

If it works, then yes we can reinstall GRUB and everything should be back to normal. Of course, if it doesn't then I still think Testdisk is the next best option to try and recover whatever was lost.

---

### Post by Mark Phelps on 2010-10-09
If looks like Win7 got trashed -- completely.  That script usually lists Windows OS files, and in this case, for sda4, it lists nothing.

Also, there's no listing for any Recovery partition which, unless the Recovery disk is a DVD, is necessary in order to restore Win7.

And finally, the standard Win7 Repair disk will look for a Win7 installation when you launch Startup Repair. If it finds no installation, there is nothing (in it's view) for it to repair -- so it won't do anything.

---

### Post by Rubi1200 on 2010-10-09
> **Mark Phelps said:**
> If looks like Win7 got trashed -- completely.  That script usually lists Windows OS files, and in this case, for sda4, it lists nothing.

Also, there's no listing for any Recovery partition which, unless the Recovery disk is a DVD, is necessary in order to restore Win7.

And finally, the standard Win7 Repair disk will look for a Win7 installation when you launch Startup Repair. If it finds no installation, there is nothing (in it's view) for it to repair -- so it won't do anything.
Thanks for the additional information Mark.

Just to confirm some things with you please:

1. I assume the Recovery Partition was probably on sda1?

2. The file system on sda4 suggests some form of encryption?

3. In your opinion, would Testdisk help here as I have already suggested?

---

### Post by Mark Phelps on 2010-10-10
From the little I've read, SFS is how other filesystems interpret MS Windows Dynamic Disks (which are actually formatted NTFS).

I've read you CAN convert dynamic to simple, but I believe that is a destructive process.

Regardless, I don't believe you can access SFS stuff from Linux at all ... but I don't use that and could be wrong.

---

