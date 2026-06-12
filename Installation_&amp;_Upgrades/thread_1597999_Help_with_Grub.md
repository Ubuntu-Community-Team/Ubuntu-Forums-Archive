---
title: "Help with Grub"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by konang on 2010-10-16
So I installed ubuntu desktop edition to a external hard drive, and it worked perfectly but there is only one annoying detail, which is that I installed the Grub 1.98 on the sdb instead of the sda and now when I boot I need to have my external hard drive pluged in, but I still have windows 7 installed in the sda, Can someone tell me if there is a way to move the Grub 1.98 from sdb to sda without having to do format windows or loosing data?

---

### Post by garvinrick4 on 2010-10-16
Make sda bootable again with windows on it. 
Unplug your external drive sdb;
Put in your Ubuntu install CD and choose Try Ubuntu;
When it boots up. open a terminal Applications/Asseccories/terminal
and copy and paste:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will get a few error messages ignore. only need MBR.
Now restart take Cd out and will boot into Windows.
If in your BIOS you have HDD to boot first Windows will boot.
If you have USB to boot first and you have your external in will have choice
of Ubuntu or Windows.
Also you can select through BIOS to choose which one you boot from be it CD, USB, HDD
on every boot instance. 
Every make or model a little different some hit F10 others F2 mine a HP I hit escape then F9 and I can choose at every boot.
Look around your BIOS and see how yours works. Is real nice to know.
Need to update grub to probe for all Operating Systems:
```
sudo update-grub
```Here is some links:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by konang on 2010-10-16
> **garvinrick4 said:**
> Make sda bootable again with windows on it. 
Unplug your external drive sdb;
Put in your Ubuntu install CD and choose Try Ubuntu;
When it boots up. open a terminal Applications/Asseccories/terminal
and copy and paste:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will get a few error messages ignore. only need MBR.
Now restart take Cd out and will boot into Windows.
If in your BIOS you have HDD to boot first Windows will boot.
If you have USB to boot first and you have your external in will have choice
of Ubuntu or Windows.
Also you can select through BIOS to choose which one you boot from be it CD, USB, HDD
on every boot instance. 
Every make or model a little different some hit F10 others F2 mine a HP I hit escape then F9 and I can choose at every boot.
Look around your BIOS and see how yours works. Is real nice to know.
Need to update grub to probe for all Operating Systems:
```
sudo update-grub
```Here is some links:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

So I did what you told me, I restored W7 mbr, then with the liveCd installed lilo ran the sudo apt-get install lilo, accepted the installation, then it told me to run liloconfig, I ran it, the ran sudo lilo -M /dev/sda mbr, and told me that the master boot recorder in dev/sda was updated. So I exit ubuntu liveCD and tried to boot ubunt 10.10 from the bootload menu and it just stays like waiting for something to load but it doesnt loads nothing, what am I missing here?

---

### Post by garvinrick4 on 2010-10-16
Goint to have to run this script to DESKTOP and then run this code and will put a text file on desktop post it to this thread takes about 15 seconds.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 ```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by garvinrick4 on 2010-10-16
> **konang said:**
> So I did what you told me, I restored W7 mbr, then with the liveCd installed lilo ran the sudo apt-get install lilo, accepted the installation, then it told me to run liloconfig, I ran it, the ran sudo lilo -M /dev/sda mbr, and told me that the master boot recorder in dev/sda was updated. So I exit ubuntu liveCD and tried to boot ubunt 10.10 from the bootload menu and it just stays like waiting for something to load but it doesnt loads nothing, what am I missing here? That was to boot Windows.
in sda you were not even suppose to have sdb drive plugged in as stated previously. sdb should have been fine. We will see. Could be no bootloader
in sdb should be if you installed in sdb at install. Bootscript with sdb plugged in will tell.

---

### Post by konang on 2010-10-16
> **garvinrick4 said:**
> Goint to have to run this script to DESKTOP and then run this code and will put a text file on desktop post it to this thread takes about 15 seconds.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 ```
sudo bash ~/Desktop/boot_info_script*.sh 
```
  
Here are my results, just to remember I installed Ubuntu 10.10 on an external hard drive that is in the sdb, still, it isnt plugged in right now


         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
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

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   941,082,623   940,673,024   7 HPFS/NTFS
/dev/sda3         941,328,384   976,560,127    35,231,744   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D06E26C96E26A864                       ntfs       SYSTEM                        
/dev/sda2        34A43672A4363728                       ntfs                                     
/dev/sda3        C8D6F481D6F47154                       ntfs       RECOVERY                      
/dev/sda4        66BE-8D79                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/34A43672A4363728  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)



All this partitions were default within the laptop

---

### Post by garvinrick4 on 2010-10-16
rerun script with sdb your ubuntu drive plugged in also. Do not have to download just
run the piece of code again with script on desktop. Does Windows boot without sdb plugged in?
 If you copy and paste whole text file and then highlight it and then click the # sign in upper right of the message box it will put it in a nice little box I can scroll thru.

---

### Post by konang on 2010-10-16
> **garvinrick4 said:**
> rerun script with sdb your ubuntu drive plugged in also. Do not have to download just
run the piece of code again with script on desktop. Does Windows boot without sdb plugged in?
 If you copy and paste whole text file and then highlight it and then click the # sign in upper right of the message box it will put it in a nice little box I can scroll thru.


Here it is, sorry i fell asleep, yes windows does boot without sdb plugged in, I restored de MBR from a Windows7 recovery disk, but I cant get Ubuntu to boot from the hard drive, and its either I restore grub to sdb and only be able to boot from the external hard drive, or boot form windows and wont be able to boot Ubutnu in the external hard drive.
```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   941,082,623   940,673,024   7 HPFS/NTFS
/dev/sda3         941,328,384   976,560,127    35,231,744   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   468,520,959   468,518,912  83 Linux
/dev/sdb2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdb5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D06E26C96E26A864                       ntfs       SYSTEM                        
/dev/sda2        34A43672A4363728                       ntfs                                     
/dev/sda3        C8D6F481D6F47154                       ntfs       RECOVERY                      
/dev/sda4        66BE-8D79                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c4b18296-0401-45fd-a336-4b08cc410c9d   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        77b33152-1124-4e45-a480-fdca7de3403f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/c4b18296-0401-45fd-a336-4b08cc410c9d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/34A43672A4363728  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c4b18296-0401-45fd-a336-4b08cc410c9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c4b18296-0401-45fd-a336-4b08cc410c9d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4b18296-0401-45fd-a336-4b08cc410c9d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=77b33152-1124-4e45-a480-fdca7de3403f none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 189.1GB: boot/grub/core.img
 189.1GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic-pae
 189.1GB: boot/vmlinuz-2.6.35-22-generic-pae
   1.0GB: initrd.img
 189.1GB: vmlinuz
```

---

### Post by garvinrick4 on 2010-10-16
Put in Live Cd and open a terminal and:
```
sudo mkdir /media/root
``````
sudo mount /dev/sdb1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/root
``` (not a typo)
You have made a directory (folder)
you have mounted partition sdb1 (linux install)
you have installed grub2 in sdb looking in sdb1 for grub2
you have unmounted and it is umount.
Now you can boot into Ubuntu with USB first in BIOS order and then
```
sudo update-grub
```will probe for all other Operating Systems to put in grub-config and grub menu.(above)
```
grep menuentry /boot/grub/grub.cfg
```to see grub menu(above)

Now you have to learn to use BIOS. If USB first in order will have Windows and UBUNTU
as choice. If use sda as boot drive will only get Windows. Do not have a Linux entry on drive to look for grub2. Looks for Window entry because that is what is installed on that drive. If had both Ubuntu and Windows on same drive can Use grub2
Can use BIOS to choose to BOOT from either CD,HDD,USB drives at each boot.
Some are F10 some are F2 mine is a HP and is esc and then F9 and choose to take choice to boot from. Remember can change Bios to boot USB first all the time and when external plugged in will always get both choices. If a USB not plugged in will go to next choice. IF CD will Pass if no Cd and next if HDD will go to that one and boot Windows. You will now have a working system.

---

### Post by konang on 2010-10-16
> **garvinrick4 said:**
> Put in Live Cd and open a terminal and:
```
sudo mkdir /media/root
``````
sudo mount /dev/sdb1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/root
``` (not a typo)
You have made a directory (folder)
you have mounted partition sdb1 (linux install)
you have installed grub2 in sdb looking in sdb1 for grub2
you have unmounted and it is umount.
Now you can boot into Ubuntu with USB first in BIOS order and then
```
sudo update-grub
```will probe for all other Operating Systems to put in grub-config and grub menu.(above)
```
grep menuentry /boot/grub/grub.cfg
```to see grub menu(above)

Now you have to learn to use BIOS. If USB first in order will have Windows and UBUNTU
as choice. If use sda as boot drive will only get Windows. Do not have a Linux entry on drive to look for grub2. Looks for Window entry because that is what is installed on that drive. If had both Ubuntu and Windows on same drive can Use grub2
Can use BIOS to choose to BOOT from either CD,HDD,USB drives at each boot.
Some are F10 some are F2 mine is a HP and is esc and then F9 and choose to take choice to boot from. Remember can change Bios to boot USB first all the time and when external plugged in will always get both choices. If a USB not plugged in will go to next choice. IF CD will Pass if no Cd and next if HDD will go to that one and boot Windows.


Thank you for you asistance you really where helpful throughout the process everything works fine now Thank You Very Much :)

---

### Post by garvinrick4 on 2010-10-16
My pleasure happy you are off and running, enjoy your Ubuntu.

---

