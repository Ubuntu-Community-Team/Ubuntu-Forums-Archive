---
title: "Ubuntu won't login from cloned HDD."
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2010-06-06
Hi all,

I had cloned my 250 GB HD to a new 1 TB HD using 'dd'. After that Ubuntu does not login. The MBR [Grub] and Windows 7 do start without any problem and all the programs are working perfect under it. When I boot to Ubuntu, the login screen just keeps displaying 'Automatically logging in...'. On the first boot from the cloned HD, Ubuntu displayed that the /home is not found and offered Check/Skip/Ignore and I selected Check. After that the message is not shown. Another weird thing is that at logon, the system does a log off and display a warning that the Power Manager Applet is not responding and asks for Log off anyway.

Is it possible to correct this? I have the old HDD intact with me. 

Thanks in advance.

---

### Post by hariks0 on 2010-06-07
Bump.

---

### Post by wilee-nilee on 2010-06-07
Cloning probably changed something in the boot, post the boot script in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by hariks0 on 2010-06-07
But where is the boot script? You mean GRUB.cfg?

---

### Post by wilee-nilee on 2010-06-07
> **hariks0 said:**
> But where is the boot script? You mean GRUB.cfg?

It is a link in my last post just boot a live cd download it drag it to your desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 
then paste into a reply with the code tags or just highlight the text and click on the # in the reply panel.

---

### Post by hariks0 on 2010-06-07
This is the Results.txt

sda is the new HD and sdb id the old one. sdb8 has Ubuntu 10.4 whereas sda8 says something wrong.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,397,951   102,191,104   7 HPFS/NTFS
/dev/sda3         102,398,371   488,394,751   385,996,381   f W95 Ext d (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sda6         204,796,683   266,229,179    61,432,497   7 HPFS/NTFS
/dev/sda7         266,229,243   365,510,879    99,281,637   7 HPFS/NTFS
/dev/sda8         365,512,704   400,504,831    34,992,128  83 Linux
/dev/sda9         400,506,880   478,629,887    78,123,008  83 Linux
Invalid MBR Signature found
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   102,397,951   102,191,104   7 HPFS/NTFS
/dev/sdb3         102,398,371   488,394,751   385,996,381   f W95 Ext d (LBA)
/dev/sdb5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sdb6         204,796,683   266,229,179    61,432,497   7 HPFS/NTFS
/dev/sdb7         266,229,243   365,510,879    99,281,637   7 HPFS/NTFS
/dev/sdb8         365,512,704   400,504,831    34,992,128  83 Linux
/dev/sdb9         400,506,880   478,629,887    78,123,008  83 Linux
/dev/sdb10        478,631,936   488,394,751     9,762,816  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        80B456ECB456E466                       ntfs       System Reserved               
/dev/sda2        0C66650C6664F83A                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4024497624497048                       ntfs       DDrive                        
/dev/sda6        46400AAF400AA631                       ntfs       EDrive                        
/dev/sda7        03AB01E67E33EB5F                       ntfs       MM                            
/dev/sda8        13ec6024-74bc-4f42-91de-0ce793f547da   ext4                                     
/dev/sda9        7aa4012c-45a9-495b-832c-92c904fae0e5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       6bdf1f48-539b-44e6-b5a4-3e967366cc7b   swap                                     
/dev/sdb1        80B456ECB456E466                       ntfs       System Reserved               
/dev/sdb2        0C66650C6664F83A                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        4024497624497048                       ntfs       DDrive                        
/dev/sdb6        46400AAF400AA631                       ntfs       EDrive                        
/dev/sdb7        03AB01E67E33EB5F                       ntfs       MM                            
/dev/sdb8        13ec6024-74bc-4f42-91de-0ce793f547da   ext4                                     
/dev/sdb9        7aa4012c-45a9-495b-832c-92c904fae0e5   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="6"
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
search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
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
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 80b456ecb456e466
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=13ec6024-74bc-4f42-91de-0ce793f547da /               ext4    errors=remount-ro 0       1
# /CDrive was on /dev/sda2 during installation
UUID=0C66650C6664F83A /CDrive         ntfs    defaults,umask=007,gid=46 0       0
# /DDrive was on /dev/sda5 during installation
UUID=4024497624497048 /DDrive         ntfs    defaults,umask=007,gid=46 0       0
# /EDrive was on /dev/sda6 during installation
UUID=46400AAF400AA631 /EDrive         ntfs    defaults,umask=007,gid=46 0       0
# /FDrive was on /dev/sda7 during installation
UUID=03AB01E67E33EB5F /FDrive         ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sda9 during installation
UUID=7aa4012c-45a9-495b-832c-92c904fae0e5 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=6bdf1f48-539b-44e6-b5a4-3e967366cc7b none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 196.0GB: boot/grub/core.img
 193.9GB: boot/grub/grub.cfg
 196.0GB: boot/initrd.img-2.6.32-21-generic
 196.1GB: boot/initrd.img-2.6.32-22-generic
 196.0GB: boot/vmlinuz-2.6.32-21-generic
 196.1GB: boot/vmlinuz-2.6.32-22-generic
 196.1GB: initrd.img
 196.0GB: initrd.img.old
 196.1GB: vmlinuz
 196.0GB: vmlinuz.old

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set default="6"
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
search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
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
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13ec6024-74bc-4f42-91de-0ce793f547da ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13ec6024-74bc-4f42-91de-0ce793f547da
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 80b456ecb456e466
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=13ec6024-74bc-4f42-91de-0ce793f547da /               ext4    errors=remount-ro 0       1
# /CDrive was on /dev/sda2 during installation
UUID=0C66650C6664F83A /CDrive         ntfs    defaults,umask=007,gid=46 0       0
# /DDrive was on /dev/sda5 during installation
UUID=4024497624497048 /DDrive         ntfs    defaults,umask=007,gid=46 0       0
# /EDrive was on /dev/sda6 during installation
UUID=46400AAF400AA631 /EDrive         ntfs    defaults,umask=007,gid=46 0       0
# /FDrive was on /dev/sda7 during installation
UUID=03AB01E67E33EB5F /FDrive         ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sda9 during installation
UUID=7aa4012c-45a9-495b-832c-92c904fae0e5 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=6bdf1f48-539b-44e6-b5a4-3e967366cc7b none            swap    sw              0       0

=================== sdb8: Location of files loaded by Grub: ===================


 196.0GB: boot/grub/core.img
 193.9GB: boot/grub/grub.cfg
 196.0GB: boot/initrd.img-2.6.32-21-generic
 196.1GB: boot/initrd.img-2.6.32-22-generic
 196.0GB: boot/vmlinuz-2.6.32-21-generic
 196.1GB: boot/vmlinuz-2.6.32-22-generic
 196.1GB: initrd.img
 196.0GB: initrd.img.old
 196.1GB: vmlinuz
 196.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ab 02 95 cf 2f 2f ff fb  94 64 ac 00 04 13 5b 56  |....//...d....[V|
00000010  4b 38 43 6a 38 c5 ba c6  31 47 5b 10 01 6d 5d 4c  |K8Cj8...1G[..m]L|
00000020  3c cd a8 cb 8a ab a8 94  8c e0 00 58 1c df 4e 95  |<..........X..N.|
00000030  9e 8a e8 39 f6 ac 6b 16  14 ef ff ff fa e8 57 e9  |...9..k.......W.|
00000040  80 e0 aa ae 38 44 df 18  52 6a de 76 10 86 31 12  |....8D..Rj.v..1.|
00000050  00 07 09 f4 6d 82 a3 40  9c 11 44 ca a7 d9 2b 1c  |....m..@..D...+.|
00000060  4e b7 df 25 d4 88 c5 a2  41 59 90 d6 9a 6e a6 4d  |N..%....AY...n.M|
00000070  79 45 20 e9 f8 55 d9 f7  67 63 d8 b2 64 f5 ae 3b  |yE ..U..gc..d..;|
00000080  aa f5 0f d3 db 43 b4 44  37 20 4f e9 5b 6c ff a6  |.....C.D7 O.[l..|
00000090  d8 f9 98 f1 fe 63 ec e7  7f a5 ef 6d 7f fb 3d bd  |.....c.....m..=.|
000000a0  5e e7 62 b3 fd e5 21 fc  4b f7 fa f6 f1 eb eb ff  |^.b...!.K.......|
000000b0  2b f7 72 48 1e c7 80 30  55 56 e2 a2 06 10 e3 a0  |+.rH...0UV......|
000000c0  d0 42 33 3d 58 1a 39 c6  7a 7b bd e8 a8 81 39 04  |.B3=X.9.z{....9.|
000000d0  3f 73 b9 18 e6 50 00 45  34 44 77 53 73 2a e1 c0  |?s...P.E4DwSs*..|
000000e0  c0 cd 2f d5 7f fa ee 20  b0 84 9a 04 17 bc ef e5  |../.... ........|
000000f0  a1 69 cc b8 85 4d 0b bf  bb fd f3 45 77 82 cd d8  |.i...M.....Ew...|
00000100  79 47 0a 4e 49 c0 08 0e  42 69 26 a4 0e 2c 84 ec  |yG.NI...Bi&..,..|
00000110  59 f8 37 25 ff 4e f4 8f  1a 8e f3 02 d4 0e 11 71  |Y.7%.N.........q|
00000120  79 31 99 07 56 a5 4c 57  64 11 59 29 8f 06 97 bb  |y1..V.LWd.Y)....|
00000130  52 6d d0 56 a3 78 9a 15  a3 9b 4c ca a9 42 4d 78  |Rm.V.x....L..BMx|
00000140  3d 41 ba 1a 2e 36 aa 92  12 f4 0e 83 d0 03 08 0e  |=A...6..........|
00000150  02 a1 e0 d6 c6 33 33 44  9d a3 c7 a3 f2 2a b4 e3  |.....33D.....*..|
00000160  8f 95 95 10 6a aa ef ac  47 2d be 2f f7 ae da 03  |....j...G-./....|
00000170  a9 6e a4 99 94 69 af a5  f4 e9 2f 9b ae d0 b8 91  |.n...i..../.....|
00000180  00 00 3d 2a aa f9 ff fb  94 64 a3 00 03 b1 5a 57  |..=*.....d....ZW|
00000190  b3 12 33 6a 4f 09 2a f6  24 a3 6d 0f 5d 79 65 4c  |..3jO.*.$.m.]yeL|
000001a0  35 0d a1 70 28 ac a4 63  a1 b4 a2 93 ce dd c9 d5  |5..p(..c........|
000001b0  2f d8 55 6e df 67 35 77  bb e5 33 fb 4e 6d 00 01  |/.Un.g5w..3.Nm..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff 29 79  1a 06 f0 62 a9 03 00 00  |......)y...b....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb3

00000000  ab 02 95 cf 2f 2f ff fb  94 64 ac 00 04 13 5b 56  |....//...d....[V|
00000010  4b 38 43 6a 38 c5 ba c6  31 47 5b 10 01 6d 5d 4c  |K8Cj8...1G[..m]L|
00000020  3c cd a8 cb 8a ab a8 94  8c e0 00 58 1c df 4e 95  |<..........X..N.|
00000030  9e 8a e8 39 f6 ac 6b 16  14 ef ff ff fa e8 57 e9  |...9..k.......W.|
00000040  80 e0 aa ae 38 44 df 18  52 6a de 76 10 86 31 12  |....8D..Rj.v..1.|
00000050  00 07 09 f4 6d 82 a3 40  9c 11 44 ca a7 d9 2b 1c  |....m..@..D...+.|
00000060  4e b7 df 25 d4 88 c5 a2  41 59 90 d6 9a 6e a6 4d  |N..%....AY...n.M|
00000070  79 45 20 e9 f8 55 d9 f7  67 63 d8 b2 64 f5 ae 3b  |yE ..U..gc..d..;|
00000080  aa f5 0f d3 db 43 b4 44  37 20 4f e9 5b 6c ff a6  |.....C.D7 O.[l..|
00000090  d8 f9 98 f1 fe 63 ec e7  7f a5 ef 6d 7f fb 3d bd  |.....c.....m..=.|
000000a0  5e e7 62 b3 fd e5 21 fc  4b f7 fa f6 f1 eb eb ff  |^.b...!.K.......|
000000b0  2b f7 72 48 1e c7 80 30  55 56 e2 a2 06 10 e3 a0  |+.rH...0UV......|
000000c0  d0 42 33 3d 58 1a 39 c6  7a 7b bd e8 a8 81 39 04  |.B3=X.9.z{....9.|
000000d0  3f 73 b9 18 e6 50 00 45  34 44 77 53 73 2a e1 c0  |?s...P.E4DwSs*..|
000000e0  c0 cd 2f d5 7f fa ee 20  b0 84 9a 04 17 bc ef e5  |../.... ........|
000000f0  a1 69 cc b8 85 4d 0b bf  bb fd f3 45 77 82 cd d8  |.i...M.....Ew...|
00000100  79 47 0a 4e 49 c0 08 0e  42 69 26 a4 0e 2c 84 ec  |yG.NI...Bi&..,..|
00000110  59 f8 37 25 ff 4e f4 8f  1a 8e f3 02 d4 0e 11 71  |Y.7%.N.........q|
00000120  79 31 99 07 56 a5 4c 57  64 11 59 29 8f 06 97 bb  |y1..V.LWd.Y)....|
00000130  52 6d d0 56 a3 78 9a 15  a3 9b 4c ca a9 42 4d 78  |Rm.V.x....L..BMx|
00000140  3d 41 ba 1a 2e 36 aa 92  12 f4 0e 83 d0 03 08 0e  |=A...6..........|
00000150  02 a1 e0 d6 c6 33 33 44  9d a3 c7 a3 f2 2a b4 e3  |.....33D.....*..|
00000160  8f 95 95 10 6a aa ef ac  47 2d be 2f f7 ae da 03  |....j...G-./....|
00000170  a9 6e a4 99 94 69 af a5  f4 e9 2f 9b ae d0 b8 91  |.n...i..../.....|
00000180  00 00 3d 2a aa f9 ff fb  94 64 a3 00 03 b1 5a 57  |..=*.....d....ZW|
00000190  b3 12 33 6a 4f 09 2a f6  24 a3 6d 0f 5d 79 65 4c  |..3jO.*.$.m.]yeL|
000001a0  35 0d a1 70 28 ac a4 63  a1 b4 a2 93 ce dd c9 d5  |5..p(..c........|
000001b0  2f d8 55 6e df 67 35 77  bb e5 33 fb 4e 6d 00 01  |/.Un.g5w..3.Nm..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff 29 79  1a 06 f0 62 a9 03 00 00  |......)y...b....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-06-07
So your script was on at the right time of day for the people who might have the answers would have seen it. What I see myself are a lot of extras in boot files in partitions that are probably only share or data related. I am not sure but this may be throwing a wrench or wrenches into getting Ubuntu to boot. I guess having the original HD and the new cloned as part of the script is helpful, but it makes it a long hard read even for people who are able to decipher this script.

You might confirm exactly what your OS are, I see a mixture of XP, Vista,and W7 boot types mixed through several partitions. I would say though if your not using any more the W7 and Ubuntu you probably have more partitions then you need and some of them have boot files in them. Not sure of any fix at this time.

---

### Post by hariks0 on 2010-06-07
Let me sa three things:-

1. There is no XP in the PC. However, these partitions were created with XP.
2. There is no swap partition in the new HD /dev/sda10 whereas it is there in the old one as /dev/sdb10
3. At the end of drive/partition info, the script says that there is invalid MBR Signature.

Creating a swap partition will help? Is it possible to copy the MBR from the old HD to the new one? But it already boots grub properly.:confused:

---

### Post by wilee-nilee on 2010-06-07
I wish I had a answer to this but I don't. The script if it is correct gives the most information in one fell swoop.

I would bump it until you get an answer, or try other forums whatever you think is appropriate. Personally I would have just installed in the new HD and transfered what ever you needed, it might have been the quickest answer rather then where your at now. I'm not all that patient when something doesn't work I just reinstall. But I have all the pertinent stuff off my computer so that method works for me.

You have the original stuff and the clone so nothing is lost. It just has to be approached in a manner that gets what you want in the end.

---

### Post by bcbc on 2010-06-08
Are you trying to boot with both these drives in the computer? The reason I ask is that they have the same UUIDs, which grub2 uses to identify the partition. Also these are used in /etc/fstab as they are preferred over the old /dev/sdXY designation.
So this is going to cause you problems.

i don' have much experience with cloning, but you'll need to change the uuid's for sure, also /etc/fstab on the cloned drive, and regenerate the grub menu.

Otherwise, try booting with only the cloned disk - that should give you a better result.

---

### Post by hariks0 on 2010-06-10
I tried booting from each of the HD individually. The Ubuntu and /home in the old HD works normal. I booted from Live CD and manually copied the contents of my /home from old to new. Now the error messages are gone, only that there are no Desktop, gnome panel, my settings are gone etc. But the Cairo-dock is still there and I can do almost all things from that. I also tried the terminal by Ctrl+Alt+F1 and I was able to login successfully.

When i do ```
sudo dd if=/dev/sdv9 of=/dev/sda9
```

an I/O error is returned.

I will reinstall Ubuntu if the cloning could not be completed successfully as a last resort.

---

### Post by bcbc on 2010-06-10
> **hariks0 said:**
> I tried booting from each of the HD individually. The Ubuntu and /home in the old HD works normal. I booted from Live CD and manually copied the contents of my /home from old to new. Now the error messages are gone, only that there are no Desktop, gnome panel, my settings are gone etc. But the Cairo-dock is still there and I can do almost all things from that. I also tried the terminal by Ctrl+Alt+F1 and I was able to login successfully.

When i do ```
sudo dd if=/dev/sdv9 of=/dev/sda9
```

an I/O error is returned.

I will reinstall Ubuntu if the cloning could not be completed successfully as a last resort.

how did you copy home? rsync -av? You'll need to keep your permissions intact.Assuming you have the same userid (number) under both computers.
I'm a little confused as on the one hand you used dd to take a direct image, and on the other you 'manually copied'.

Anyway - as I said before I've little experience with cloning, but I'm sure someone out there has written a howto.

---

### Post by hariks0 on 2010-06-12
Hellow bcbc,

I first tried the 'dd' command and later - due to the I/O error message - manually copied the contents of my /home from the old HD to the new HD. Both by booting from a live CD.

I do nt know anything about 'rync -av'. Can you please elaborate a bit ?

Thank you.

---

### Post by bcbc on 2010-06-13
> rsync is a file transfer program capable of efficient remote update via a fast differencing algorithm.

-a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)


r - recursive
l - links (symlinks)
p - preserve permissions
t - preserve modification times
g - preserve group
o - preserve owner
D - preserve device files and special files

v is just verbose (no big deal).

If you are trying to make a straight copy especially to a cloned machine with the same userids etc., you want all your ownership/permissions etc to be preserved. So that's how I'd do it.

---

