---
title: "won't boot"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by catlover2 on 2010-09-10
hi,

i installed an update and it told me i needed to reboot.
i said yes and and it shut down and did not reboot, it said something  about 
"Assuming drive cache write through"
and the screen went black.

i'm posting this from a livecd.

thanks,
catlover

---

### Post by Rubi1200 on 2010-09-10
Do you remember which update?

Is there anything else associated with the error message like a drive letter such as sda etc.?

---

### Post by catlover2 on 2010-09-10
> **Rubi1200 said:**
> Do you remember which update?

Is there anything else associated with the error message like a drive letter such as sda etc.?


i hadn't updated in a while so there were lots and lots of 
updates.

here's the error:    
```
[6.844525] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
[6.847754] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
[6.851763] sd 2:0:0:0: [sdb] Assuming drive cache: write through

_
```


after the error it says "UBUNTU 10.04"  and then goes blank.
                         

disconnecting all hardware attached to the comp has no effect.

---

### Post by wilee-nilee on 2010-09-10
Is this a wubi install? it is important to be as specific as you can, not always easy I know.

Post the boot script in rubi1200 signature, or mine in code tags. Code tags=paste text to reply and click on the # in the reply panel.

---

### Post by catlover2 on 2010-09-10
> **wilee-nilee said:**
> Is this a wubi install? it is important to be as specific as you can, not always easy I know.

Post the boot script in rubi1200 signature, or mine in code tags. Code tags=paste text to reply and click on the # in the reply panel.

not a wubi, straight from a livecd.

there's the boot script.

```
                Boot Info Script 0.55    dated September 10th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1352319 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1370815 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,360,914    75,360,852  83 Linux
/dev/sda2          75,360,915    78,140,159     2,779,245   5 Extended
/dev/sda5          75,360,978    78,140,159     2,779,182  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        0290abc9-47ad-4799-ab27-6f7cfc416d7d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6ad945df-5edd-4c43-abb9-be9f4b99552d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8070E81170E81028                       ntfs       Reeds Pics 2                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/apt               iso9660    (ro,relatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6ad945df-5edd-4c43-abb9-be9f4b99552d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
  13.8GB: boot/initrd.img-2.6.31-20-generic
  14.3GB: boot/initrd.img-2.6.32-17-generic
  10.7GB: boot/vmlinuz-2.6.31-20-generic
  13.6GB: boot/vmlinuz-2.6.32-17-generic
  14.3GB: initrd.img
  13.8GB: initrd.img.old
  13.6GB: vmlinuz
  10.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by JBAlaska on 2010-09-10
That is not usually a error message, I'm guessing that's just all you can see before the boot stops.

Can you boot in recovery mode or to a prior kernel?

Let us know if the upgrade included a kernel update, and what graphics card you have.

---

### Post by wilee-nilee on 2010-09-10
I suspect somewhere in that update was a grub update and it may be just reloading grub to the mbr and mounting the Ubuntu partition will get you going.

Here is a link to the grub2 wiki that defaults to the methods of loading grub from a live cd, I will give you the commands to be run from a live cd of karmic or beyond.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

```
sudo mount /dev/sda1 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to the Ubuntu install hopefully and then run in the terminal.
```
sudo update-grub
```

As it is grub is looking at the correct partition, but something is not working.

I would also answer JBAlaska's questions as well

---

### Post by catlover2 on 2010-09-10
> **JBAlaska said:**
> That is not usually a error message, I'm guessing that's just all you can see before the boot stops.

Can you boot in recovery mode or to a prior kernel?

Let us know if the upgrade included a kernel update, and what graphics card you have.


i don't know what was in the update, didn't think to look!:redface:

i'm not sure about my graphics card, all i know is that it's some pathetic integrated card. :biggrin:

---

### Post by catlover2 on 2010-09-10
> **wilee-nilee said:**
> I suspect somewhere in that update was a grub update and it may be just reloading grub to the mbr and mounting the Ubuntu partition will get you going.

Here is a link to the grub2 wiki that defaults to the methods of loading grub from a live cd, I will give you the commands to be run from a live cd of karmic or beyond.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

```
sudo mount /dev/sda1 /mnt
```Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot to the Ubuntu install hopefully and then run in the terminal.
```
sudo update-grub
```As it is grub is looking at the correct partition, but something is not working.

I would also answer JBAlaska's questions as well

so you're saying to run these?

---

### Post by wilee-nilee on 2010-09-10
> **catlover2 said:**
> so you're saying to run these?

Yes from a live cd then the update grub from the rebooted installed OS.

You also have the grub bootloader files in sda1 which is okay but these are for the mbr, generally. This partition has a boot flag on it this combination may be the problem, even though it shouldn't. 

You can remove the boot flag from gparted on the live cd right click the unmounted sda1 then manage flags and untick the boot flag.

---

### Post by catlover2 on 2010-09-10
i did all that,
still no difference.

something i just remembered,
i think i still have the beta version of 10.04.

---

### Post by wilee-nilee on 2010-09-10
Have you made sure that sda is first in bios to be read?

Generally the bios is accessed with f2, but some computers may use another f-key or esc.

Since you have reloaded the mbr run the script again to have the latest info for others to look over for help.

---

### Post by catlover2 on 2010-09-11
yes,
its first in boot order,

and here it is.

```

                Boot Info Script 0.55    dated September 10th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1352319 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1370815 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    75,360,914    75,360,852  83 Linux
/dev/sda2          75,360,915    78,140,159     2,779,245   5 Extended
/dev/sda5          75,360,978    78,140,159     2,779,182  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        0290abc9-47ad-4799-ab27-6f7cfc416d7d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6ad945df-5edd-4c43-abb9-be9f4b99552d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8070E81170E81028                       ntfs       Reeds Pics 2                  
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/apt               iso9660    (ro,relatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6ad945df-5edd-4c43-abb9-be9f4b99552d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
  13.8GB: boot/initrd.img-2.6.31-20-generic
  14.3GB: boot/initrd.img-2.6.32-17-generic
  10.7GB: boot/vmlinuz-2.6.31-20-generic
  13.6GB: boot/vmlinuz-2.6.32-17-generic
  14.3GB: initrd.img
  13.8GB: initrd.img.old
  13.6GB: vmlinuz
  10.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Jeepman on 2010-09-11
I hope I have the right thread for this issue. I just installed Ubuntu on my Mother-in-law's computer, after she seen how well my computer ran with it for years now. And I did a new update for her and now it tells me that it cannot find the root sys mount files, so I booted into the live disk and try to mount the hard disk and it tells me that it (error mounting: wrong fs type, bad option, bad superblock on /dev/sda1,  missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | tail or so)

I know the file system is the ext4 and it was working until the last update, can anyone help I don't want to reinstall the OS

---

### Post by wilee-nilee on 2010-09-11
> **Jeepman said:**
> I hope I have the right thread for this issue. I just installed Ubuntu on my Mother-in-law's computer, after she seen how well my computer ran with it for years now. And I did a new update for her and now it tells me that it cannot find the root sys mount files, so I booted into the live disk and try to mount the hard disk and it tells me that it (error mounting: wrong fs type, bad option, bad superblock on /dev/sda1,  missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | tail or so)

I know the file system is the ext4 and it was working until the last update, can anyone help I don't want to reinstall the OS

Your going to want to start your own thread, with your description, and post the bootscript in my signature.

We try to keep threads separate as they are different and things can get confusing. ;)

---

### Post by Rubi1200 on 2010-09-11
What do you have installed on sdb? The file system is NTFS but there don't appear to be any boot files there:
> sdb1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Grub 2     Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and                         looks at sector 1370815 of the same hard drive for                         core.img, but core.img can not be found at this                         location. No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   And why is GRUB saying it is installed there when there is nothing there?

I also don't see a boot flag on the drives (indicated by an asterisk next to the relevant partition *)

Is sdb an external drive?

Perhaps try removing it and then follow the instructions previously provided by wilee-nilee for reinstalling GRUB and then boot and see what happens?

---

### Post by catlover2 on 2010-09-11
> **Rubi1200 said:**
> 
What do you have installed on sdb? The file system is NTFS but there don't appear to be any boot files there:
And why is GRUB saying it is installed there when there is nothing there?

I also don't see a boot flag on the drives (indicated by an asterisk next to the relevant partition *)

Is sdb an external drive?

Perhaps try removing it and then follow the instructions previously provided by wilee-nilee for reinstalling GRUB and then boot and see what happens?
nothing installed on it that i know of..

don't know why GRUB thinks there's something there.

sdb is external.

I'll try it!

---

### Post by catlover2 on 2010-09-11
now there's no "assuming drive cache: write through"

just the "UBUNTU 10.04" and then a blank screen with no HD activity.

---

### Post by Rubi1200 on 2010-09-12
Could you run and post the results from the bootscript again please?

Thanks.

---

### Post by catlover2 on 2010-09-12
lol,

here it is again!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1352319 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    75,360,914    75,360,852  83 Linux
/dev/sda2          75,360,915    78,140,159     2,779,245   5 Extended
/dev/sda5          75,360,978    78,140,159     2,779,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        0290abc9-47ad-4799-ab27-6f7cfc416d7d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6ad945df-5edd-4c43-abb9-be9f4b99552d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/apt               iso9660    (ro,relatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0290abc9-47ad-4799-ab27-6f7cfc416d7d
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0290abc9-47ad-4799-ab27-6f7cfc416d7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6ad945df-5edd-4c43-abb9-be9f4b99552d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
  13.8GB: boot/initrd.img-2.6.31-20-generic
  14.3GB: boot/initrd.img-2.6.32-17-generic
  10.7GB: boot/vmlinuz-2.6.31-20-generic
  13.6GB: boot/vmlinuz-2.6.32-17-generic
  14.3GB: initrd.img
  13.8GB: initrd.img.old
  13.6GB: vmlinuz
  10.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by Rubi1200 on 2010-09-13
Hi catlover2,
please use a LiveCD and try reinstalling GRUB to the MBR:

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

If there are no errors, reboot the computer and run ```
sudo update-grub
```

---

### Post by catlover2 on 2010-09-13
i got this:

```
root@PartedMagic:~# grub-install --root-directory=/mnt/ /dev/sda
cp: `/mnt//boot/grub/locale/en_AU.mo' and `/mnt//boot/grub/locale/en_AU.mo' are the same file
cp: `/mnt//boot/grub/locale/en_GB.mo' and `/mnt//boot/grub/locale/en_GB.mo' are the same file
Installation finished. No error reported.
root@PartedMagic:~# 
```
are you saying to reboot the comp to the livecd or the HD??


thanks for all the help!!

catlover

---

### Post by Rubi1200 on 2010-09-13
> **catlover2 said:**
> i got this:

```
root@PartedMagic:~# grub-install --root-directory=/mnt/ /dev/sda
cp: `/mnt//boot/grub/locale/en_AU.mo' and `/mnt//boot/grub/locale/en_AU.mo' are the same file
cp: `/mnt//boot/grub/locale/en_GB.mo' and `/mnt//boot/grub/locale/en_GB.mo' are the same file
Installation finished. No error reported.
root@PartedMagic:~# 
```
are you saying to reboot the comp to the livecd or the HD??


thanks for all the help!!

catlover

Reboot to the HD; I am hoping you can get into Ubuntu and then run the final command to update grub.

---

### Post by catlover2 on 2010-09-13
:shock::shock::frown::confused:?!?

it still wont boot into ubuntu!!!!!!!!!

a little history,

now before i installed xfce desktop manager (3-4 months ago)
it saying "UBUNTU 10.04" was normal.

but after installing xfce it'd just say "XUBUNTU".

NOW, it says "UBUNTU 10.04", and doesn't boot.

---

### Post by Rubi1200 on 2010-09-13
I don't get it either!?!

I have the feeling I/we are missing something with all of this.

I am going to ask one of the more experienced forum members to take a look and see if he can help because, unfortunately, I am out of ideas: unless you are willing to do a fresh install.

---

### Post by catlover2 on 2010-09-13
i'd much rather not do a fresh install. 

thanks for all your help!

catlover

---

### Post by catlover2 on 2010-09-13
i just checked the ram by using one stick at a time,
STILL no dif,
just the same old 
"Grub loading
Welcome to Grub"

"ubuntu 10.04"

then blank screen.

---

### Post by Rubi1200 on 2010-09-13
Have you made any changes to BIOS recently; changed a setting perhaps?

---

### Post by oldfred on 2010-09-13
I did not see anything in boot script that looked like a problem. Once the catlover2 got to booting then it should not be a boot issue unless some setting in the kernel like nomodeset or acpi=off type settings on the kernel line. Once grub gets past menu a reinstall to the MBR should not add anything. 

The write cache thru may not be the error but just the last process run as part of the boot. My messages log shows write cache: enabled. It looked like that message was related to sdb and now the boot script does not show sdb. 

catlover2, you mention two externals, did you switch and they somehow are enough different to cause issues?

Now that we do not get menu, we need to reinstall and when the quick reinstall does not work lets try the full chroot with some updates.

chroot:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
kansasnoob's change sda1 to correct partition
```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Then once chrooted lets update & totally reinstall grub2.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by catlover2 on 2010-09-14
please give me slightly more info on what to do, 
as what you posted is a bit unclear to me. :redface:

---

### Post by catlover2 on 2010-09-14
> **Rubi1200 said:**
> Have you made any changes to BIOS recently; changed a setting perhaps?

no

---

### Post by oldfred on 2010-09-14
Chrooting is using the liveCD to boot and then CHanging ROOT to run your hard drive install to repair it.

You have to mount a bunch of things and kanasnoob use && to make them all one line, so you can copy and paste his command & be chrooted into your non-working install.

then from your non-working system we can do anything we could do from within it. That way we can update & repair it.

After chrooted into your system run each of the command I gave. If you get any error messages that would be very important.

---

### Post by catlover2 on 2010-09-14
so sorry, i'm just not quite linux savvy enough to make that make sense!

---

### Post by Rubi1200 on 2010-09-14
Ok, let me help a little bit here:

oldfred wants you to boot the LiveCD again and then go to the terminal to run some commands.

I will set them up in order:

1. 
```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```2. ```
apt-get autoclean
```3. ```
apt-get clean
```4. ```
apt-get update
```5.```
 apt-get upgrade
```6.```
 apt-get dist-upgrade
```7.```
 apt-get -f install
```8. ```
dpkg --configure -a
```Once all of this has been done, and assuming there are no errors, you can continue with the next steps:

```
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc
```Run these commands one at a time.

Hopefully, you can then reboot, removing the LiveCD and you will be back into Ubuntu.

If there are errors, let us know.

By the way, the first part could take some time so don't be alarmed.

---

### Post by catlover2 on 2010-09-14
ok, so i did this: ```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```




then i tried to run this:```
 apt-get autoclean 
```



then it told me to run this:
```
 sudo dpkg --configure -a
```and i ran it and it said "configuring wine" and every other package on my [COLOR=Red]*Hard drive installation!!!!*[/COLOR] :o:confused:


then gave me this: (screenshot included)



thanks,

catlover.

---

### Post by oldfred on 2010-09-14
You just want to click ok. The first screen is just asking if you need any special parameters like nomodeset or others. For now the only thing we want is to confirm the install of grub to the MBR which is the last screen. Do not choose partitions. When it says all it just means drives sda, sdb, not partitions sda1, sda2.

---

### Post by catlover2 on 2010-09-14
> **Rubi1200 said:**
> 
...If there are errors, let us know....



LOL!!:o:o

every command that had anything to do with installation or upgrades ended like this!!
```
Errors were encountered while processing:
 dbus
 gconf2-common
 rhythmbox
 packagekit
 hal
 gnome-control-center
 udisks
 kpackagekit
 xubuntu-desktop
 dbus-x11
 ubuntu-desktop
 network-manager
 evolution
 gnome-screensaver
 f-spot
 gconf2
 gnibbles
 light-themes
 gnome-applets
 evolution-couchdb
 totem-common
 onboard
 gstreamer0.10-plugins-good
 compiz-gnome
 update-manager
 rhythmbox-plugin-cdrecorder
 network-manager-gnome
 nautilus-sendto
 evolution-indicator
 gnome-session-bin
 swell-foop
 aisleriot
 policykit-1
 gnotski
 gconf-defaults-service
 gnome-power-manager
 empathy-common
 pitivi
 python-aptdaemon
 empathy
 gdm
 glines
 libgstfarsight0.10-0
 lightsoff
 eog
 gconf-editor
 gnome-settings-daemon
 compiz
 gtali
 openoffice.org-gnome
 capplets-data
Processing was halted because there were too many errors.
root@ubuntu:/# 

```

---

### Post by Rubi1200 on 2010-09-14
I don't know whether to laugh or cry! 

I hope oldfred has some more suggestions.

By the way, thanks for being so understanding through all of this!

:)

---

### Post by oldfred on 2010-09-14
Was there an error on connecting to the internet? That might explain so many errors, otherwise the quickest solution is backup using liveCD and reinstall. Or I am out of ideas. Maybe someone else knows more.

---

### Post by catlover2 on 2010-09-14
maybe backup and reinstall is what i'll do!

thanks!!

---

### Post by catlover2 on 2010-09-14
:o:oeek!!

i just thought i'd see what'd happen if i tried to boot again,

and i got a distorted, oversized xubuntu logo, then that black screen!!:shock:8-[

and, would it be any use to run that command even though there were a bunch of errors??

---

### Post by oldfred on 2010-09-14
If you are just about to reinstall it will not hurt to chroot into system again. Make sure you have Internet connection and run them in the order I gave you.

---

### Post by catlover2 on 2010-09-15
ok, quick everybody, give me another idea before i shoot my 
operating system dead:biggrin::biggrin:!!

---

