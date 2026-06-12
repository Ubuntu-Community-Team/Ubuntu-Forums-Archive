---
title: "Grub2 reinstall clobbered Windows 7 boot in a curious way"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by BlueXIV on 2010-05-20
So, I got a new rig recently, and I was waiting for my Windows 7 order to process. I wanted to mess around with the machine, so I just installed Ubuntu first, even though my past experiences dictated that it was a bad idea.

Anyways, I installed my copy of windows as I got it, used it for a few days, everything was fine. Then I decided I needed to boot Ubuntu up again to make use of it's superior developer environment. So I booted up from my live-cd, reinstalled grub2, and booted into ubuntu. Used it for a while, then was going to switch back to windows for some games.

So, a bit of background. I have two HDDs in my computer, one 1TB drive with my current installations, and a 180GB one with my old windows 7 installation. The old one doesn't boot anymore because of a weird hard drive dependency error, which didn't matter too much. But apparently grub made it so that BOTH windows7 booters (on /dev/sda1 and /dev/sda2) pointed to my OLD installation of Windows (on sda1), which booted up fine. However, I have no way of getting to my current Windows installation now.

Any tips? I don't really want to just let Windows "autofix", which will probably just overwrite the MBR again and make me go through the whole process.

Thanks in advance

---

### Post by wilee-nilee on 2010-05-20
If you can post this script in code tags it would be helpful.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by BlueXIV on 2010-05-21
> **wilee-nilee said:**
> If you can post this script in code tags it would be helpful.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    63,999,999    63,997,952  83 Linux
/dev/sdb2    *     64,000,000    64,204,799       204,800   7 HPFS/NTFS
/dev/sdb3          64,204,800   483,430,399   419,225,600   7 HPFS/NTFS
/dev/sdb4       1,949,528,064 1,953,523,711     3,995,648  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CB8B1F1B8B1B9A2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d667c5fb-19dc-4807-bb69-03cfc56919c8   ext4                                     
/dev/sdb2        203C8A683C8A3934                       ntfs       System Reserved               
/dev/sdb3        6C04D0AC04D07B12                       ntfs                                     
/dev/sdb4        80718071-0456-410c-9c65-115a1a064275   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    63,999,999    63,997,952  83 Linux
/dev/sdb2    *     64,000,000    64,204,799       204,800   7 HPFS/NTFS
/dev/sdb3          64,204,800   483,430,399   419,225,600   7 HPFS/NTFS
/dev/sdb4       1,949,528,064 1,953,523,711     3,995,648  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CB8B1F1B8B1B9A2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d667c5fb-19dc-4807-bb69-03cfc56919c8   ext4                                     
/dev/sdb2        203C8A683C8A3934                       ntfs       System Reserved               
/dev/sdb3        6C04D0AC04D07B12                       ntfs                                     
/dev/sdb4        80718071-0456-410c-9c65-115a1a064275   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2cb8b1f1b8b1b9a2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 261c421d1c41e7ff
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=80718071-0456-410c-9c65-115a1a064275 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.5GB: boot/initrd.img-2.6.32-22-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
    .4GB: boot/vmlinuz-2.6.32-22-generic
  17.5GB: initrd.img
  17.3GB: initrd.img.old
    .4GB: vmlinuz
  17.3GB: vmlinuz.old
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set d667c5fb-19dc-4807-bb69-03cfc56919c8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2cb8b1f1b8b1b9a2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 261c421d1c41e7ff
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=80718071-0456-410c-9c65-115a1a064275 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.5GB: boot/initrd.img-2.6.32-22-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
    .4GB: boot/vmlinuz-2.6.32-22-generic
  17.5GB: initrd.img
  17.3GB: initrd.img.old
    .4GB: vmlinuz
  17.3GB: vmlinuz.old

```


Edit: kinda off topic, but I kind of realized too late windows creates a system partition as well, eating up my 4 primary partition limit. Could I just remove the linux swap partition and replace it with a swap file? Is there anything special I need to do when removing it? Or would creating a swap then deleting the partition be good enough? Thanks

---

### Post by frantid on 2010-05-21
have you tried, in your ubuntu install:

```
sudo update-grub
```

It looks like some of the partition uuid's have changed since grub was installed.  update-grub should work it out.

---

### Post by darkod on 2010-05-21
# / was on [COLOR=Red]/dev/sdc1[/COLOR] during installation
UUID=d667c5fb-19dc-4807-bb69-03cfc56919c8 /               ext4    errors=remount-ro 0       1
# swap was on [COLOR=Red]/dev/sdc2[/COLOR] during installation
UUID=80718071-0456-410c-9c65-115a1a064275 none            swap    sw              0       0

Did you have another disk plugged in or usb stick? No wonder grub2 is confused, it was initially installed as third drive, and now there are only two.

At the top it says /dev/sdb1 is the root partition but during install it was /dev/sdc1.

If you can boot ubuntu, and it seems you can, boot it and recreate the device.map and update the grub.cfg with:

sudo grub-mkdevicemap
sudo update-grub

See if that helps sort out the boot process. We'll worry about swap later.

---

### Post by BlueXIV on 2010-05-21
Ahh right, I forgot! I took out a harddrive recently, it totally slipped my mind. I gotta go to work now, but I'll update this when I get home today. Thanks!

---

### Post by darkod on 2010-05-21
> **BlueXIV said:**
> Ahh right, I forgot! I took out a harddrive recently, it totally slipped my mind. I gotta go to work now, but I'll update this when I get home today. Thanks!

Yeah, you forgot you took out a hdd, but you were quick to blame ubuntu in your title. ;-)

---

### Post by BlueXIV on 2010-05-21
pfff I couldn't find a good tag for it :P

---

