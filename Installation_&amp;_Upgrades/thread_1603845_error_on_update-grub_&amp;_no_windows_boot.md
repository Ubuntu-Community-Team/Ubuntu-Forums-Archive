---
title: "error on update-grub &amp; no windows boot"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by viodelin on 2010-10-23
With a bit of help from this forum I managed to install 10.04. The solution was to add i915.modeset=1 to the options when booting up from CD.
Now I need to do the same in order to boot up from HD. I've opened /etc/default/grub and changed the relevant line to include the above option. But I need to run "update-grub" and it comes back with an error to the effect that it 'can't find a device for / (is /dev mounted?)
Any suggestions?

Also, the boot menu only has ubuntu - no sign of windows in my intended dual-boot. What can I do?

I've got a supergrub disk somewhere. Shall I run this and see where it gets me?

Thanks in advance.

---

### Post by kansasnoob on 2010-10-23
Please use a Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by viodelin on 2010-10-23
Thank you. Below is the entire contents of the file:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97-os.1 is installed in the MBR of /dev/sda and looks on the same 
    drive in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,531,069    20,531,007   7 HPFS/NTFS
/dev/sda2          20,531,194   117,201,785    96,670,592   f W95 Ext d (LBA)
/dev/sda5          59,617,278    86,252,984    26,635,707   7 HPFS/NTFS
/dev/sda6          20,531,196    42,829,289    22,298,094  83 Linux
/dev/sda7          42,829,353    44,917,739     2,088,387  82 Linux swap / Solaris
/dev/sda8          44,917,803    59,617,214    14,699,412  83 Linux
/dev/sda9          86,253,048    90,799,379     4,546,332   7 HPFS/NTFS
/dev/sda10         90,799,443   117,201,785    26,402,343   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       25D8-6A04                              vfat       WIN98PROGS                    
/dev/sda1        7230C41D30C3E667                       ntfs       Local Disk                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        F6845C55845C1B07                       ntfs       elotrolado                    
/dev/sda6        5f2bc5f7-d4ab-4343-a57f-beb34ded17f0   ext4                                     
/dev/sda7        caa8b486-39ce-453f-96f3-2ae7ce49c0f1   swap                                     
/dev/sda8        78e3a025-36d2-4430-b8cc-7d1e6f75c8b5   ext4                                     
/dev/sda9        F66C24FD6C24BA6F                       ntfs       PagefileXP                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f2bc5f7-d4ab-4343-a57f-beb34ded17f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f2bc5f7-d4ab-4343-a57f-beb34ded17f0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# /fat32tripas was on /dev/sda10 during installation
UUID=25D8-6A04  /fat32tripas    vfat    utf8,umask=007,gid=46 0       1
/dev/sda8       /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=caa8b486-39ce-453f-96f3-2ae7ce49c0f1 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  12.8GB: boot/grub/core.img
  13.6GB: boot/grub/grub.cfg
  13.7GB: boot/initrd.img-2.6.32-21-generic
  11.7GB: boot/vmlinuz-2.6.32-21-generic
  13.7GB: initrd.img
  11.7GB: vmlinuz

========================== sda10/boot/grub/menu.lst: ==========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sda10: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2

---

### Post by kansasnoob on 2010-10-23
This is a bit of an oddity, you have a separate grub partition created by SGD:

> sda10: __________________________________________________ _______________________

File system: vfat
Boot sector type: MSWIN4.1: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot/grub/menu.lst

And the MBR is assigned to it:

> => Grub 0.97-os.1 is installed in the MBR of /dev/sda and looks on the same
drive in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

Making matters even odder is that it shows up in Ubuntu's fstab:

> =============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda6 / ext4 errors=remount-ro 0 1
[COLOR="Red"][B]# /fat32tripas was on /dev/sda10 during installation
UUID=25D8-6A04 /fat32tripas vfat utf8,umask=007,gid=46 0 1[/B][/COLOR]
/dev/sda8 /home ext4 defaults 0 2
# swap was on /dev/sda7 during installation
UUID=caa8b486-39ce-453f-96f3-2ae7ce49c0f1 none swap sw 0 0

**Please read this all before beginning!** If any of it is unclear please ask for additional instructions :)

So I'd begin by assigning the mbr to Ubuntu's grub2 by booting a Live CD and running from terminal (please copy-n-paste):

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

Note: If that returns any errors also run:

```
grub-install --recheck /dev/sda
```

Then:

```
sudo update-grub
```

Wait for it to say done then just exit the chroot, unmount, and reboot:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

On reboot the grub menu may still be hidden, if so immediately after the System/BIOS screen passes press the Shift key, that should display the menu.

Once at the grub menu Ubuntu should be selected by default so just press 'e' to edit, then add "i915.modeset=1" after "quiet splash". Then press Ctrl+x to boot. 

Hopefully that will let you boot. If so make the "i915.modeset=1" edit permanent by running these commands from terminal:

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf

```

```
sudo update-initramfs -u
```

The third thing is dealing with that entry for sda10 in fstab. **It could slow, or even prevent, boot!** I think you'll need to comment out one line in fstab  so run:

```
sudo gedit /etc/fstab
```

Then edit as indicated in red below:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda6 / ext4 errors=remount-ro 0 1
# /fat32tripas was on /dev/sda10 during installation
**[COLOR="Red"]#[/COLOR]**UUID=25D8-6A04 /fat32tripas vfat utf8,umask=007,gid=46 0 1
/dev/sda8 /home ext4 defaults 0 2
# swap was on /dev/sda7 during installation
UUID=caa8b486-39ce-453f-96f3-2ae7ce49c0f1 none swap sw 0 0

Hopefully this helps :)

---

### Post by viodelin on 2010-10-23
It did indeed help! Now I can boot into ubuntu just fine, but still no sign of windows.
:confused:
Can I ask for a bit more help?
Thanks!

---

### Post by efflandt on 2010-10-23
What do you have in sda9?  The boot sector of sda9 thinks it begins at sector 63 (it does not, and conflicts with sda1). That might be the reason grub2 does not want to deal with either.

> sda9:

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

---

### Post by viodelin on 2010-10-23
sda9 contains my pagefile, ie Windows swap

---

### Post by kansasnoob on 2010-10-23
> **viodelin said:**
> It did indeed help! Now I can boot into ubuntu just fine, but still no sign of windows.
:confused:
Can I ask for a bit more help?
Thanks!

Absolutely :)

Give me a few moments.

---

### Post by kansasnoob on 2010-10-23
I guess I should first ask a question. Will Ubuntu now boot with no fiddling around? I mean you no longer have to edit the boot parameters from the grub menu?

I guess beyond that I need to know if Windows booted OK when it was booting from that SGD grub menu? Or when did it last boot?

If Ubuntu is now booting OK then I'd like to see a new output from the Boot Info Script, but first of all boot into Ubuntu and run:

```
sudo update-grub
```

Then try to boot Windows again, if it even shows up in the boot menu, then let me know if it shows up in the menu and what, if any, errors are displayed while trying to boot Windows.

The answers to those questions and a fresh output from the Boot Info Script will help me a lot :)

BTW: I may be out for a few hours, sorry.

---

### Post by viodelin on 2010-10-23
Ah, so that's what it was - just needed that update-grub, which worked ever so well this time... as do both Ubuntu and Windows! thank you very much for all your help. Just followed your instructions and no more fiddling around.

However... I think the installation got a bit mixed up with my partitions. I just tried to add sda10 (the fat32 partition where I keep my thunderbird profile) to fstab and what do you know, no sign of sda10, but it mounted my XP pagefile instead, and now i can't even find the fat 32 partition to mount it!
:guitar:          
No rush!




```


      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,531,069    20,531,007   7 HPFS/NTFS
/dev/sda2          20,531,194   117,201,785    96,670,592   f W95 Ext d (LBA)
/dev/sda5          59,617,278    86,252,984    26,635,707   7 HPFS/NTFS
/dev/sda6          20,531,196    42,829,289    22,298,094  83 Linux
/dev/sda7          42,829,353    44,917,739     2,088,387  82 Linux swap / Solaris
/dev/sda8          44,917,803    59,617,214    14,699,412  83 Linux
/dev/sda9          86,253,048    90,799,379     4,546,332   7 HPFS/NTFS
/dev/sda10         90,799,443   117,201,785    26,402,343   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda10       25D8-6A04                              vfat       WIN98PROGS                    
/dev/sda1        7230C41D30C3E667                       ntfs       Local Disk                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        F6845C55845C1B07                       ntfs       elotrolado                    
/dev/sda6        5f2bc5f7-d4ab-4343-a57f-beb34ded17f0   ext4                                     
/dev/sda7        caa8b486-39ce-453f-96f3-2ae7ce49c0f1   swap                                     
/dev/sda8        78e3a025-36d2-4430-b8cc-7d1e6f75c8b5   ext4                                     
/dev/sda9        F66C24FD6C24BA6F                       ntfs       PagefileXP                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /home                    ext4       (rw)
/dev/sda10       /fat32tripas             vfat       (rw,uid=1001,gid=1001,iocharset=iso8859-1)
/dev/sda9        /media/PagefileXP        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda10       /media                   vfat       (rw)
/dev/sda5        /media/elotrolado        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f2bc5f7-d4ab-4343-a57f-beb34ded17f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f2bc5f7-d4ab-4343-a57f-beb34ded17f0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5f2bc5f7-d4ab-4343-a57f-beb34ded17f0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7230c41d30c3e667
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# /fat32tripas was on /dev/sda10 during installation
#UUID=25D8-6A04  /fat32tripas    vfat    utf8,umask=007,gid=46 0       1
/dev/sda8       /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=caa8b486-39ce-453f-96f3-2ae7ce49c0f1 none            swap    sw              0       0
/dev/sda10     /fat32tripas    vfat    auto,rw,uid=1001,gid=1001,iocharset=iso8859-1   1   0

=================== sda6: Location of files loaded by Grub: ===================


  12.7GB: boot/grub/core.img
  13.4GB: boot/grub/grub.cfg
  13.7GB: boot/initrd.img-2.6.32-21-generic
  11.7GB: boot/vmlinuz-2.6.32-21-generic
  13.7GB: initrd.img
  11.7GB: vmlinuz

========================== sda10/boot/grub/menu.lst: ==========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sda10: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
=============================== StdErr Messages: ===============================

/home/maria/Desktop/boot_info_script055.sh: line 1266: cd: /media/PagefileXP/: No such file or directory


```

---

### Post by kansasnoob on 2010-10-23
> Ah, so that's what it was - just needed that update-grub, which worked ever so well this time... as do both Ubuntu and Windows! thank you very much for all your help. Just followed your instructions and no more fiddling around.

Great!

> However... I think the installation got a bit mixed up with my partitions. I just tried to add sda10 (the fat32 partition where I keep my thunderbird profile) to fstab and what do you know, no sign of sda10, but it mounted my XP pagefile instead, and now i can't even find the fat 32 partition to mount it!

I didn't know you had anything but the SGD grub there, we can fix that. Just give me a little time to parse everything in that new output. We're almost there.

SGD is great to boot with but it can actually create problems if used to install or reinstall grub.

My son's supposed to be stopping by so i may be out for a while, sorry you have to temporarily live without Thunderbird until I return :(

---

### Post by kansasnoob on 2010-10-23
I'm rushing but it can't do any harm to remove that comment (#) I had you add to fstab, then remove the line you added to fstab. Bassically go back to the fstab you showed in post #3.

If that messes up booting or tries to "mount your XP page file" we'll likely have to pick around in sda10 and find those SGD files so we can rename and/or trash them.

Would you please post the output of:

```
sudo parted /dev/sda print
```

Because I'm too lazy to do math :redface:

---

### Post by viodelin on 2010-10-23
Hello again,
I removed my crappy line from fstab and was able to mount sda10, so thunderbird is fine. All I need now is to add the *correct* line to fstab so that this partition is mounted on startup. I would like to understand how it's done so that I can do my own fiddling about, like hiding that silly pagefile from my ubuntu file system. But none of this is very important or urgent!


This is the result of parted:

Model: ATA Hitachi HTE54166 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.5GB  10.5GB  primary   ntfs            boot
 2      10.5GB  60.0GB  49.5GB  extended                  lba
 6      10.5GB  21.9GB  11.4GB  logical   ext4
 7      21.9GB  23.0GB  1069MB  logical   linux-swap(v1)
 8      23.0GB  30.5GB  7526MB  logical   ext4
 5      30.5GB  44.2GB  13.6GB  logical   ntfs
 9      44.2GB  46.5GB  2328MB  logical   ntfs
10      46.5GB  60.0GB  13.5GB  logical   fat32


A million thanks for all your help.

---

### Post by viodelin on 2010-10-23
PS I had to put the # back into the line, as per your first suggestion. Otherwise the partition doesn't even show in Places.
good night

---

### Post by kansasnoob on 2010-10-24
**Please consider this just thinking out loud at the moment.** I'm just reviewing things this AM while sipping my first cups of coffee :)

I do wonder if you're still able to boot both Ubuntu and XP because I noticed this in the second Boot Info output:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

Nothing in Boot files/dirs, but they were there in the first output:

> sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: **[COLOR="Red"]/boot.ini /ntldr /NTDETECT.COM[/COLOR]**

Odd to say the least :confused:

I'm thinking efflandt may have been onto something in post #6:

> What do you have in sda9? The boot sector of sda9 thinks it begins at sector 63 (it does not, and conflicts with sda1). That might be the reason grub2 does not want to deal with either.

I know you answered that, but I see both sda5 and sda9 show that they begin at sector 63 which neither actually do.

And both the old and new outputs show this:

> =================== sda10: Location of files loaded by Grub: ===================


**[COLOR="Red"]??[/COLOR]**GB: boot/grub/menu.lst
**[COLOR="Red"]??[/COLOR]**GB: boot/grub/stage2

I'm curious when you began booting XP with SGD?

Also the new output showed this:

> =============================== StdErr Messages: ===============================

/home/maria/Desktop/boot_info_script055.sh: line 1266: cd: /media/PagefileXP/: No such file or directory

All quite puzzling to me. I've never worked with an XP that had so many separate partitions.

I also notice that Ubuntu's /home is quite small:

> 8 23.0GB 30.5GB **[COLOR="Red"]7526MB[/COLOR]** logical ext4

That's not a problem now, but 7.5 GB will generally fill up pretty fast.

Ultimately I think you're going to need some help from someone that knows Windows XP much better than I do. I know Ubuntu/Debian grub and grub2 pretty well, but I'm far from knowledgeable regarding Windows :(

I hope oldfred pops in today. He knows much more than I do.

---

### Post by viodelin on 2010-10-25
Yes, it all seems quite peculiar but hey, it works!
I don't think SGD actually worked on this occasion. I have used it in the past, so maybe there is some trace of it somewhere.
I consider my problem solved
:)

---

