---
title: "unable to boot, Error in booting"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by bedamoni on 2010-12-09
Hello,
      I have problem with booting in Ubuntu10..4. It shows an error:
       	 	 	 	 	 	  init: Failed to spawn plymouth main process: unable to execute: No such file or directory




I had installed lots of softwares, programs in the above mentioned OS. So, please help me to solve this problem.  I am new to Ubuntu and dont know how to upgrade to a new version saving all the files in the earlier OS.




With regards, 

Bedamoni

---

### Post by wilee-nilee on 2010-12-09
> **bedamoni said:**
> Hello,
      I have problem with booting in Ubuntu10..4. It shows an error:
       	 	 	 	 	 	  init: Failed to spawn plymouth main process: unable to execute: No such file or directory

I had installed lots of softwares, programs in the above mentioned OS. So, please help me to solve this problem.  I am new to Ubuntu and dont know how to upgrade to a new version saving all the files in the earlier OS.

With regards, 

Bedamoni

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

This will let us see what is where.

---

### Post by bedamoni on 2010-12-09
Hello,
      I have problem with booting in Ubuntu10..4. It shows an error:
       	 	 	 	 	 	  init: Failed to spawn plymouth main process: unable to execute: No such file or directory




I had installed lots of softwares, programs in the above mentioned OS. So, please help me to solve this problem.  I am new to Ubuntu and dont know how to upgrade to a new version saving all the files in the earlier OS.




With regards, 

Bedamoni

---

### Post by bedamoni on 2010-12-09
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

This will let us see what is where.



should I take "boot_info_script055.sh" in a CD and then this CD should I put tn the the computer which has the boot problem? Or I can download it in a linux machine which is working properly and follow the step given in the sourceforge site? 

I even could not start the machine (ie the user name option things should come, but not).

best 
bedamoni

---

### Post by bedamoni on 2010-12-09
the result text shows like:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   110,635,636   110,633,589   7 HPFS/NTFS
/dev/sda2         110,637,054   488,396,799   377,759,746   f W95 Ext d (LBA)
/dev/sda5         191,542,995   293,941,304   102,398,310  83 Linux
/dev/sda6         396,339,678   406,573,019    10,233,342  82 Linux swap / Solaris
/dev/sda7         406,573,056   484,947,967    78,374,912  83 Linux
/dev/sda8         484,950,016   488,396,799     3,446,784  82 Linux swap / Solaris
/dev/sda9         293,941,368   396,339,614   102,398,247  83 Linux
/dev/sda10        293,941,306   293,941,366            61  83 Linux
/dev/sda11        110,637,056   188,131,327    77,494,272  83 Linux
/dev/sda12        188,133,376   191,526,911     3,393,536  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4009 MB, 4009754624 bytes
5 heads, 32 sectors/track, 48947 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda11       2f4ec1ee-35c1-4181-91b6-4791a2d067cd   ext4                                     
/dev/sda12       a16f4595-3b4d-4c93-81e4-320a6ec3dcdf   swap                                     
/dev/sda1        B404340D0433D15A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bd828511-d146-4fbb-92f2-ec632d845004   ext3       /                             
/dev/sda6        6cae4b81-f158-477d-9a10-ba77d14e25ae   swap       SWAP-sda7                     
/dev/sda7        d0639455-ec49-48a6-baf5-d4499df0a655   ext4                                     
/dev/sda8        4582e3f7-9852-4e55-abdb-638052218c58   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        51A1-86CF                              vfat       BEDA                          
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro)
/dev/sdf1        /media/BEDA              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b404340d0433d15a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d0639455-ec49-48a6-baf5-d4499df0a655 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=4582e3f7-9852-4e55-abdb-638052218c58 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 244.8GB: boot/grub/core.img
 240.5GB: boot/grub/grub.cfg
 244.8GB: boot/initrd.img-2.6.32-21-generic
 244.8GB: boot/vmlinuz-2.6.32-21-generic
 244.8GB: initrd.img
 244.8GB: vmlinuz

========================== sda11/boot/grub/grub.cfg: ==========================

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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b404340d0433d15a
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=a16f4595-3b4d-4c93-81e4-320a6ec3dcdf none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


  58.9GB: boot/grub/core.img
  58.9GB: boot/grub/grub.cfg
  58.9GB: boot/initrd.img-2.6.32-21-generic
  58.9GB: boot/vmlinuz-2.6.32-21-generic
  58.9GB: initrd.img
  58.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 


..........................................................................................................................................................................

---

### Post by sikander3786 on 2010-12-09
First of all, edit your above post, highlight the text from boot script and click # icon in post menu to wrap it with code tags. Or simply, just type [/code] at the end of that text and ```
 at the beginning of it. That would make it easier to read ;-)

From that output, what I see, Grub seems pretty ok so that shouldn't be causing any problems here.

The issue seems to lie with plymouth. I would suggest to try to boot the recovery mode and perform some commands. From Grub menu, choose Recovery, 2nd option on the list, then drop to root shell and:

Connect to the internet,

[code]dhclient eth0
```

Where eth0 is your network interface.

Try to configure any broken packages.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

Update and upgrade your system,

```
sudo apt-get update && sudo apt-get upgrade
```

Reboot and try to boot to Desktop.

```
sudo shutdown -r now
```

If any errors are reported, please post them.

---

### Post by s.fox on 2010-12-09
Please do not create duplicate threads.  Thank you.

Threads merged.

---

### Post by bedamoni on 2010-12-10
I have installed two ubuntu10.4 and a windows vista. One of the ubuntu and windows is working properly, but the problem ls in the another ubuntu. I have also tried the recovery mode, the same problem persist i.e. the screen gives an error massage like:

  	 	 	 	 	 	  init: Failed to spawn mountall main process: unable to execute: No such file or directory


init: Failed to spawn mountall post-stop process: unable to execute: No such file or directory


.............................................................................................        ........................................................................


I am sending the previous post by editing 


                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   110,635,636   110,633,589   7 HPFS/NTFS
/dev/sda2         110,637,054   488,396,799   377,759,746   f W95 Ext d (LBA)
/dev/sda5         191,542,995   293,941,304   102,398,310  83 Linux
/dev/sda6         396,339,678   406,573,019    10,233,342  82 Linux swap / Solaris
/dev/sda7         406,573,056   484,947,967    78,374,912  83 Linux
/dev/sda8         484,950,016   488,396,799     3,446,784  82 Linux swap / Solaris
/dev/sda9         293,941,368   396,339,614   102,398,247  83 Linux
/dev/sda10        293,941,306   293,941,366            61  83 Linux
/dev/sda11        110,637,056   188,131,327    77,494,272  83 Linux
/dev/sda12        188,133,376   191,526,911     3,393,536  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4009 MB, 4009754624 bytes
5 heads, 32 sectors/track, 48947 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda11       2f4ec1ee-35c1-4181-91b6-4791a2d067cd   ext4                                     
/dev/sda12       a16f4595-3b4d-4c93-81e4-320a6ec3dcdf   swap                                     
/dev/sda1        B404340D0433D15A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bd828511-d146-4fbb-92f2-ec632d845004   ext3       /                             
/dev/sda6        6cae4b81-f158-477d-9a10-ba77d14e25ae   swap       SWAP-sda7                     
/dev/sda7        d0639455-ec49-48a6-baf5-d4499df0a655   ext4                                     
/dev/sda8        4582e3f7-9852-4e55-abdb-638052218c58   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        51A1-86CF                              vfat       BEDA                          
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro)
/dev/sdf1        /media/BEDA              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b404340d0433d15a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d0639455-ec49-48a6-baf5-d4499df0a655 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=4582e3f7-9852-4e55-abdb-638052218c58 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 244.8GB: boot/grub/core.img
 240.5GB: boot/grub/grub.cfg
 244.8GB: boot/initrd.img-2.6.32-21-generic
 244.8GB: boot/vmlinuz-2.6.32-21-generic
 244.8GB: initrd.img
 244.8GB: vmlinuz

========================== sda11/boot/grub/grub.cfg: ==========================

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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 2f4ec1ee-35c1-4181-91b6-4791a2d067cd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b404340d0433d15a
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set d0639455-ec49-48a6-baf5-d4499df0a655
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0639455-ec49-48a6-baf5-d4499df0a655 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=2f4ec1ee-35c1-4181-91b6-4791a2d067cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=a16f4595-3b4d-4c93-81e4-320a6ec3dcdf none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


  58.9GB: boot/grub/core.img
  58.9GB: boot/grub/grub.cfg
  58.9GB: boot/initrd.img-2.6.32-21-generic
  58.9GB: boot/vmlinuz-2.6.32-21-generic
  58.9GB: initrd.img
  58.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde ```

```

---

