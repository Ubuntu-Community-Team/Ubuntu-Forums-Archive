---
title: "No boot after install of 10.04 to IDE hdd"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by cL0h on 2011-07-05
Hi everyone,
I've been trying to put 10.04 on a 160GB IDE hard disk that I formatted for that purpose with 3 partitions 1 for Ubuntu, 1 for SWAP and 1 FAT for storing files I may copy from a Windows system.

After rebooting after install from USB using unetbootin I get "Reboot and select proper boot device or insert boot media"

:confused:

My boot script RESULTS.TXT is:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1075696 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005536d

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   160,835,583   160,833,536  83 Linux
/dev/sda2         313,632,768   321,671,167     8,038,400  82 Linux swap / Solaris
/dev/sda3         160,835,584   313,632,767   152,797,184   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          1,128     7,831,551     7,830,424   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        c8e0d997-1bca-41f3-9257-03a1dd3363ba   ext4       
/dev/sda2        0b4b9075-7746-48f7-9438-26d122813d62   swap       
/dev/sda3        804D-2C14                              vfat       
/dev/sdb1        10EF-CA8D                              vfat       USB Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/sdb1        /media/USB Drive         vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash -- persistent

label ubnentry2
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys
            ?? = ??             menu.c32
            ?? = ??             syslinux.cfg

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

Can anyone help me troubleshoot?

Much thanks 
Colm

---

### Post by cL0h on 2011-07-06
OK so I've learned that the Mint 6 Live CD I used doesn't recognise ext4. I'll run the boot script again when I get home.
C.

---

### Post by mastablasta on 2011-07-06
why you had to mkae one for swap? it's made automaticly. it would be mroe logical to make one for /home. 
 
also why FAT parittion? if windows is on same disk or same computer then it's better to use NTFS (FAT won't be able to read files larger than 4 GB i think). Also if windows is not on same ocmputer then there is no reason for windows file system.

---

### Post by cL0h on 2011-07-06
> **mastablasta said:**
> why you had to mkae one for swap? it's made automaticly. it would be mroe logical to make one for /home. 
 
also why FAT parittion? if windows is on same disk or same computer then it's better to use NTFS (FAT won't be able to read files larger than 4 GB i think). Also if windows is not on same ocmputer then there is no reason for windows file system.

Is this what is causing my PC to not boot?

Also what do you mean by "it's made automatically". Do you mean the partitioner makes it at install time or that I don't need one?

---

### Post by cL0h on 2011-07-07
OK so here it is again:
This time I used a XUbuntu Live CD and copied the RESULTS.TXT to a USB key
Can anyone help me out? IS it the FAT partition. Should I have SWAP before the FAT?
I can't imagine this is causing the error of "Insert boot disk... etc ..."

Any tips would be much appreciated.

PS. Just so people don't get confused the USB key also had a copy of  XUbuntu on it too but I couldn't get the PC to boot from it so I burned a LiveCD


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1075696 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   160,835,583   160,833,536  83 Linux
/dev/sda2         313,632,768   321,671,167     8,038,400  82 Linux swap / Solaris
/dev/sda3         160,835,584   313,632,767   152,797,184   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          1,128     7,831,551     7,830,424   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        c8e0d997-1bca-41f3-9257-03a1dd3363ba   ext4       
/dev/sda2        0b4b9075-7746-48f7-9438-26d122813d62   swap       
/dev/sda3        804D-2C14                              vfat       
/dev/sdb1        10EF-CA8D                              vfat       USB Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/USB Drive         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set c8e0d997-1bca-41f3-9257-03a1dd3363ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
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
search --no-floppy --fs-uuid --set c8e0d997-1bca-41f3-9257-03a1dd3363ba
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=800x600
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c8e0d997-1bca-41f3-9257-03a1dd3363ba
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c8e0d997-1bca-41f3-9257-03a1dd3363ba ro   quiet splash xbmc=autostart,nodiskmount loglevel=0 video=vesafb
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=800x600
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c8e0d997-1bca-41f3-9257-03a1dd3363ba
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c8e0d997-1bca-41f3-9257-03a1dd3363ba ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8e0d997-1bca-41f3-9257-03a1dd3363ba /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
UUID=804D-2C14  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda2 during installation
UUID=0b4b9075-7746-48f7-9438-26d122813d62 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  44.128646851 = 47.382773760   boot/grub/core.img                             1
  14.132316589 = 15.174459392   boot/grub/grub.cfg                             1
  44.202228546 = 47.461781504   boot/initrd.img-2.6.32-29-generic              1
  44.145511627 = 47.400882176   boot/vmlinuz-2.6.32-29-generic                 1
  44.202228546 = 47.461781504   initrd.img                                     1
  44.145511627 = 47.400882176   vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash -- persistent

label ubnentry2
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by YesWeCan on 2011-07-07
The bootinfoscript output looks ok to me. The error you report sounds like the bios is unable to find the disk you asked it to boot. Could this be related to your IDE arrangement? Some more info about your hardware might reveal something.

---

### Post by cL0h on 2011-07-07
> **YesWeCan said:**
> The bootinfoscript output looks ok to me. The error you report sounds like the bios is unable to find the disk you asked it to boot. Could this be related to your IDE arrangement? Some more info about your hardware might reveal something.

OK so I changed the drive jumpers from master to cable select and I also reset the bios to defaults (on the Asus asus p541c-mlx mobo). I had ide/pata turned off at one point due to having no ide devices. 
One of those changes has resolved the issue.
Sorry I realise I could have checked this without bootscript knowledge and in hindsight it seems obvious I should have reset the BIOS to factory default but big thanks for taking a look at my boot script YesWeCan. I really do appreciate it.

---

### Post by YesWeCan on 2011-07-07
You are welcome. Glad it works.

---

