---
title: "Lost boot record Ubuntu 9.10"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by olimb on 2010-11-11
Was dual booting winXP and Ubuntu9.10 ok
I added a third partition and tried to clone my winXP using XXClone
The clone job failed and now I can only boot into winXP.
Ubuntu is still there but the boot reference is lost.
Any suggestions appreciated

---

### Post by wilee-nilee on 2010-11-11
A good start would be to click the bootscript link in my signature, download it run the command on the link page. From the generated file copy the text then open a reply click on the # you will see code tags, put the text between them.

---

### Post by olimb on 2010-11-11
I accessed Ubuntu from a live CD and ran the Boot Info Script 
Here are the results
 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => GAG is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d2c59

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sda2         245,762,370   420,340,724   174,578,355   5 Extended
/dev/sda5         245,762,433   404,870,129   159,107,697  83 Linux
/dev/sda6         404,870,193   420,340,724    15,470,532  82 Linux swap / Solaris
/dev/sda3         420,340,725   625,137,344   204,796,620   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 63 sectors/track, 497 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5547c0e2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63       500,975       500,913   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        67FFEDE071B2192E                       ntfs                                     
/dev/sda3        5D2DB92711608C02                       ntfs                                     
/dev/sda5        bc284619-a2a2-46f2-8fd8-56466a62a1cb   ext4                                     
/dev/sda6        873f80b7-eb19-465d-bf01-4c2bce564fcf   swap                                     
/dev/sdc1        CCDF-F105                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/67FFEDE071B2192E  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/bc284619-a2a2-46f2-8fd8-56466a62a1cb ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda3        /media/5D2DB92711608C02  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/CCDF-F105         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="XXCLONE: (Cloned Volume) [d:0,p:3] \WINDOWS" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 67ffede071b2192e
	drivemap -s (hd0) ${root}
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
UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a65fcf80-1f4c-4b6e-abdf-61cd998c715e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.1GB: boot/grub/core.img
 142.1GB: boot/grub/grub.cfg
 126.4GB: boot/initrd.img-2.6.31-14-generic
 126.6GB: boot/initrd.img-2.6.31-22-generic
 126.3GB: boot/vmlinuz-2.6.31-14-generic
 126.2GB: boot/vmlinuz-2.6.31-22-generic
 126.6GB: initrd.img
 126.4GB: initrd.img.old
 126.2GB: vmlinuz
 126.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by wilee-nilee on 2010-11-11
**GAG **is installed in the MBR of /dev/sda

So this was a custom install of this bootloader or whats going on? here is a link to a good page on this.
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

I just want to figure out here what do you want to be the bootloader, personally I don't care which but grub2 would really be the only one I could possibly help with.

---

### Post by oldfred on 2010-11-11
In your partition editing you must have deleted & recreated swap as the UUID's are different. You will have to edit fstab.

# swap was on /dev/sda6 during installation
UUID=[COLOR=Red]a65fcf80-1f4c-4b6e-abdf-61cd998c715e[/COLOR] none            swap    sw              0       0

/dev/sda6        [COLOR=Red]873f80b7-eb19-465d-bf01-4c2bce564fcf[/COLOR]   swap  


Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by wilee-nilee on 2010-11-11
> **oldfred said:**
> In your partition editing you must have deleted & recreated swap as the UUID's are different. You will have to edit fstab.

# swap was on /dev/sda6 during installation
UUID=[COLOR=Red]a65fcf80-1f4c-4b6e-abdf-61cd998c715e[/COLOR] none            swap    sw              0       0

/dev/sda6        [COLOR=Red]873f80b7-eb19-465d-bf01-4c2bce564fcf[/COLOR]   swap  


Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

+1 thanks oldfred I saw that, but with many afraid of the bootloaders whatever they may be, I was just trying to get to the heart of the matter.

OP follow this users advice.

---

### Post by oldfred on 2010-11-11
wilee-nilee, I do not know gag either. Just suggesting to use grub2 as we like it and it works for many without issue. A few have issues, but most issues are solvable.

---

### Post by wilee-nilee on 2010-11-11
> **oldfred said:**
> wilee-nilee, I do not know gag either. Just suggesting to use grub2 as we like it and it works for many without issue. A few have issues, but most issues are solvable.

Hey, like you have said, (any input is good), for me even if I look the fool I actually am in real life.

Viva grub2;)

---

### Post by olimb on 2010-11-11
I used Gparted since the original install and I see you picked up on that from the boot record.
The GAG Graphical Boot Manager is not a true boot manager it is more like a skin with icons that point to drives that are already working correctly.
I installed it in the hopes of it booting linux but it didn’t so I uninstalled it, I see it has left a trail, also there is reference to win7 which I thought was completely removed from the system.

I followed these instructions 
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
All appeared to install without errors, but upon reboot I get an error
“ cannot mount sda5 start in recovery mode”
 When I try
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
upon reboot I get a black dos type screen referencing grub legacy
It appears my Ubuntu 9.10 install has grub legacy not grub2 
Do I need to use different commands for the grub reinstall or should I get grub2 and install that?

---

### Post by wilee-nilee on 2010-11-11
I think I know what to do here, but I suspect oldfred will stop by for a look so along with them and a lot of others who are really pretty good at this stuff, lets get a consensus or a for sure thing.

Your getting the grub-legacy, but you also have grub2 installed, it looks like a upgrade to grub2 that was not finished which would have purged the grub-legacy files possibly.

Here is a link for wiping out all things grub in general and reinstalls grub2 take a look if you try it do the Chroot method.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I have a terrible headache right now and so I want you up and running.;)

---

### Post by olimb on 2010-11-12
I booted into recovery mode so I had to do the whole Chroot method
Did all the steps 
Everything seemed to go well except I still get the mount error and have to boot into recovery mode.
wilee-nilee if your headache’s bothering you get some rest, I can wait.

In the mean time I’ll do another Boot Info Script and if the results look different I’ll post them.

---

### Post by olimb on 2010-11-12
Latest boot info script results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d2c59

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sda2         245,762,370   420,340,724   174,578,355   5 Extended
/dev/sda5         245,762,433   404,870,129   159,107,697  83 Linux
/dev/sda6         404,870,193   420,340,724    15,470,532  82 Linux swap / Solaris
/dev/sda3         420,340,725   625,137,344   204,796,620   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 63 sectors/track, 497 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5547c0e2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63       500,975       500,913   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        67FFEDE071B2192E                       ntfs                                     
/dev/sda3        5D2DB92711608C02                       ntfs                                     
/dev/sda5        bc284619-a2a2-46f2-8fd8-56466a62a1cb   ext4                                     
/dev/sda6        873f80b7-eb19-465d-bf01-4c2bce564fcf   swap                                     
/dev/sdc1        CCDF-F105                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="XXCLONE: (Cloned Volume) [d:0,p:3] \WINDOWS" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set bc284619-a2a2-46f2-8fd8-56466a62a1cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 67ffede071b2192e
	drivemap -s (hd0) ${root}
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
UUID=bc284619-a2a2-46f2-8fd8-56466a62a1cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a65fcf80-1f4c-4b6e-abdf-61cd998c715e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 127.0GB: boot/grub/core.img
 142.1GB: boot/grub/grub.cfg
 126.4GB: boot/initrd.img-2.6.31-14-generic
 126.6GB: boot/initrd.img-2.6.31-22-generic
 126.3GB: boot/vmlinuz-2.6.31-14-generic
 126.2GB: boot/vmlinuz-2.6.31-22-generic
 126.6GB: initrd.img
 126.4GB: initrd.img.old
 126.2GB: vmlinuz
 126.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by wilee-nilee on 2010-11-12
I have seen where the swap can cause problems similar to this. The swap UUID still doesn't read the same, the sda5 UUID is okay, but not the swap. I would boot the live cd, open gparted and turn off the swap delete it and replace it with one in it's place. I would then go to the link old fred gave for reloading grub2 to the mbr and run those two commands as you know sda5 is where we are trying to get. Here the link I use for grub2 I think it is the same one.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I think, just a hypothesis that something isn't getting cleared out of the swap with all of this. Otherwise I might be missing something here that is always possible, except for the swap uuid it all looks good. If a new swap doesn't work then just delete it from the live cd run the two commands again and from the live cd and build the swap from a live cd if everything gets up and running.

So I think you realize that the grub2 load commands are always follwed with a reboot to Ubuntu and a 
```
sudo update-grub
```

So if the swap rebuild doesn't work after rebooting do the same process by booting the cd to just remove it and see if that works.

Always turn the swap off when you do anything with it and in general while doing any partitioning. 

My headache is slowly going away so thanks for your patince

---

### Post by olimb on 2010-11-12
I couldn’t figure out how to switch off the swap partition
but after deleting it and adding it again made no change, 
I deleted it entirely leaving it listed as unused space

Then I purged and reinstalled grub with
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-common grub-pc
reboot
sudo update-grub

Now I still have the error message 
“Cannot mount swap press escape to boot into recovery mode” 
and now I can’t mount the cdrom either.
Unable to mount cdrom0
mount: special device /dev/scd0 does not exist

---

### Post by oldfred on 2010-11-12
From LiveCD you should change UUID of swap to the currrent UUID of your new swap partition in your fstab.

You can always list your UUID's
sudo blkid

Or you can boot without swap by putting a # in front of the UUID entry to make it a comment. Then you should be able to edit once booted.

Not sure about CD issue.

---

### Post by olimb on 2010-11-15
Thanks wilee-nilee and oldfred for your help.
I have decided to format and reinstall this time but I appreciate the help you gave trying to get it repaired.

---

