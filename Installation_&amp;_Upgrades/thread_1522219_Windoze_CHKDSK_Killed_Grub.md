---
title: "Windoze CHKDSK Killed Grub"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by dankdave on 2010-07-01
Hi,

I've been running this Dell Studio for a while on dual boot.  I have the 64-bit 10.04 Ubuntu with Windows 7 installed on the other partition.

Today when I booted into Windows it wanted to run CHKDSK and I let it run it.  I was able to have a session, but when I restarted there was no grub menu, and in fact I wasn't able to load ANY operating system.

The following showed up:

```

No module name found.
Aborted.  Press any key to exit.
Intel UNDI, PXE-2.1 (build 083)
Copyrith (c) 1997-2000

Realtek PCIe 6BE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media Test failure, check cable
PXE-MOF: Exiting PXE ROM
Operating System not found.

```

I'm able to boot into a liveCD.  Running "sudo fdisk -l" provides the following:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe64000e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       11689    78487034+   7  HPFS/NTFS
/dev/sda4           11689       60802   394499073    5  Extended
/dev/sda5           11689       58809   378488832   83  Linux
/dev/sda6           58809       60802    16009216   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Running the bootinfo script provided at 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net")
gives the following:

```
ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   187,774,393   156,974,069   7 HPFS/NTFS
/dev/sda4         187,774,974   976,773,119   788,998,146   5 Extended
/dev/sda5         187,774,976   944,752,639   756,977,664  83 Linux
/dev/sda6         944,754,688   976,773,119    32,018,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        942E6C132E6BED24                       ntfs       RECOVERY                      
/dev/sda3        B4CA6E37CA6DF650                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b447d9f4-e2fc-4f08-835d-f94853ff53f0   ext4                                     
/dev/sda6        469b5f1e-65c8-4ffb-bf6b-89002b17512f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/b447d9f4-e2fc-4f08-835d-f94853ff53f0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b447d9f4-e2fc-4f08-835d-f94853ff53f0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 942e6c132e6bed24
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b447d9f4-e2fc-4f08-835d-f94853ff53f0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=469b5f1e-65c8-4ffb-bf6b-89002b17512f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 433.4GB: boot/grub/core.img
 431.4GB: boot/grub/grub.cfg
 433.4GB: boot/initrd.img-2.6.32-21-generic
 433.6GB: boot/initrd.img-2.6.32-22-generic
 433.7GB: boot/initrd.img-2.6.32-23-generic
 433.4GB: boot/vmlinuz-2.6.32-21-generic
  99.5GB: boot/vmlinuz-2.6.32-22-generic
 122.8GB: boot/vmlinuz-2.6.32-23-generic
 433.7GB: initrd.img
 433.6GB: initrd.img.old
 122.8GB: vmlinuz
  99.5GB: vmlinuz.old
ubuntu@ubuntu:~/Downloads$ 

```

Any suggestions would be greatly appreciated.

---

### Post by celldweller1591 on 2010-07-01
Try this :-
Boot live and open a Terminal and type in the following commands. 

> sudo grub[INDENT] 
    > find /boot/grub/stage1         /*finds grub location on the  drive */

    > root (hd0,5)

    > setup (hd0)

    > exit[/INDENT] Note that hd0,0 implies the first  hard drive and the first partition on that drive, which is where you  probably installed grub to during installation. If not, then adjust  accordingly. 
Reboot after removing the livecd, and your boot menu should be back.

---

### Post by dankdave on 2010-07-01
I ran
> 
sudo apt-get install grub

and then after running sudo grub in the terminal ran into the following:
> 
grub> find /boot/grub/stage1

Error 15: File not found

grub> 


---

### Post by SoFl W on 2010-07-01
Err 15
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

---

### Post by RJARRRPCGP on 2010-07-02
> **dankdave said:**
> Hi,

I've been running this Dell Inspiron for a while on dual boot.  I have the 64-bit 10.04 Ubuntu with Windows 7 installed on the other partition.

Today when I booted into Windows it wanted to run CHKDSK and I let it run it.  I was able to have a session, but when I restarted there was no grub menu, and in fact I wasn't able to load ANY operating system.

The following showed up:

```

No module name found.
Aborted.  Press any key to exit.
Intel UNDI, PXE-2.1 (build 083)
Copyrith (c) 1997-2000

Realtek PCIe 6BE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media Test failure, check cable
PXE-MOF: Exiting PXE ROM
Operating System not found.

```


Looks like to me that you need to check the CMOS battery and jumper.

---

### Post by dankdave on 2010-07-02
Thanks for the response, but I have no idea what the CMOS battery and jumper is or how to check it.

---

### Post by dankdave on 2010-07-02
By the way - when I put in a liveCD, I get 

No module name found.
Aborted.  Press any key to exit.

and then after hitting a key, it's willing to load the liveCD.  The BIOS is set up to first look at the hard drive.

---

### Post by dankdave on 2010-07-02
> **SoFl W said:**
> Err 15
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

Thanks for the link.  I followed the directions here, using sda5 for where the bootloader is and everything worked out fine!

---

### Post by RJARRRPCGP on 2010-07-02
Looks like your BIOS forgot its settings and now looks for a nonsense LAN boot.

---

### Post by dankdave on 2010-08-26
Although I was able to get back into ubuntu, next time I booted into Windows 7, they decided to corrupt the bootloader.

If you remove Dell Data Safe from the windows install, then the boot loader stays intact.  See

[http://ubuntuforums.org/showthread.php?p=9767420#post9767420](http://ubuntuforums.org/showthread.php?p=9767420#post9767420)

---

