---
title: "2nd hard drive won't boot (karmic koala)"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by FatLabs on 2010-01-03
i have 2 hard drives on my machine (1 with ubuntu & 1 with win xp) & would like to create a boot menu to select either at startup, but this isn't working.

here is the order of how i setup my system:
1.  installed win xp on drive1
2.  disconnected drive 1 & installed ubuntu 9.10 on drive2
3.  set ubuntu as master drive & win xp as slave drive

i've read about modifying menu.lst to get a boot menu, but as far as i can tell this is no longer valid in 9.10.

i've also installed startup manager, which gives me a boot menu *but* when i select the win xp option at the boot menu, i get an error.  i'm assuming this error is due to the fact that i am using 2 hard drives (instead of the more common 2 partition on 1 hard drive).

Here is what my boot option says:
Microsoft Windows XP Professional (on /dev/sdb1)

Here is what commands run when I select this option:
drivemap -s (hd0) ${root}
chainloader +1

Here is the error that results:
ERROR: INVALID SIGNATURE

is it possible to get a boot menu with 2 hard drives using 9.10?
any solutions out there?  it's worth mentioning that i am a brand new user to linux.

thanks

p.s. the reason i didn't go for a partition on 1 hard drive from the start is that the ubuntu partitioner did not recognize any free space on my win xp drive.

---

### Post by gsmanners on 2010-01-03
What happens if you set the XP drive as master and the Ubuntu drive as slave?

---

### Post by FatLabs on 2010-01-05
I have both drives on cable select on an "80" IDE cable, so after swapping their positions so that XP is the master & Ubuntu the slave this is what happened:
1.  without changing the bios startup disk order, it booted straight into windows
2.  after changing the bios startup disk order, it booted to the ubuntu selection menu & when i picked XP i got the same error message as before.  booting into ubuntu worked fine.

I have a feeling if I need to edit the command line in the ubuntu startup menu, but I don't know nearly enough about the syntax to do this.

anyone out there have any ideas?

---

### Post by gsmanners on 2010-01-06
Sounds to me like you can boot the XP as master no problem, so then all you need to do is to "recover" that drive like in the following article:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by presence1960 on 2010-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by FatLabs on 2010-01-11
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Below are the results of the boot info script.  As a reminder:

[LIST]
[*]sda is my windows drive (master)
[*]sdb is my ubuntu drive (slave) --- for some reason, if I don't have this drive as slave, my storage drive automounts as read-only.
[*]sdc is my storage drive
[/LIST]
 
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xebf4ebf4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders, total 19999728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x024e024d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,037,024    19,036,962  83 Linux
/dev/sdb2          19,037,025    19,984,859       947,835   5 Extended
/dev/sdb5          19,037,088    19,984,859       947,772  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x010b657c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="2EE039A4E03972E7" LABEL="Main" TYPE="ntfs" 
sdb1: UUID="292a6e40-1d4f-4d28-aeaf-028c86c6d616" TYPE="ext4" 
sdb5: UUID="3a6b2a41-95cc-41ca-93b2-f9f7cf8b62a7" TYPE="swap" 
sdc1: UUID="AE1C9F021C9EC52D" LABEL="500GB Network Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee039a4e03972e7
    drivemap -s (hd0) ${root}
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
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda1 during installation
UUID=292a6e40-1d4f-4d28-aeaf-028c86c6d616  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=3a6b2a41-95cc-41ca-93b2-f9f7cf8b62a7  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs         nls=iso8859-1,users       0  0  

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by presence1960 on 2010-01-11
> **FatLabs said:**
> Below are the results of the boot info script.  As a reminder:

[LIST]
[*]sda is my windows drive (master)
[*]sdb is my ubuntu drive (slave) --- for some reason, if I don't have this drive as slave, my storage drive automounts as read-only.
[*]sdc is my storage drive
[/LIST]
 
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xebf4ebf4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders, total 19999728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x024e024d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,037,024    19,036,962  83 Linux
/dev/sdb2          19,037,025    19,984,859       947,835   5 Extended
/dev/sdb5          19,037,088    19,984,859       947,772  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x010b657c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="2EE039A4E03972E7" LABEL="Main" TYPE="ntfs" 
sdb1: UUID="292a6e40-1d4f-4d28-aeaf-028c86c6d616" TYPE="ext4" 
sdb5: UUID="3a6b2a41-95cc-41ca-93b2-f9f7cf8b62a7" TYPE="swap" 
sdc1: UUID="AE1C9F021C9EC52D" LABEL="500GB Network Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee039a4e03972e7
    drivemap -s (hd0) ${root}
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
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda1 during installation
UUID=292a6e40-1d4f-4d28-aeaf-028c86c6d616  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=3a6b2a41-95cc-41ca-93b2-f9f7cf8b62a7  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs         nls=iso8859-1,users       0  0  

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

Once you get GRUB coming up you will need to do 2 things: reinstall GRUB2 and then boot into Ubuntu and change permissions for sdc so you can have read/write access.

Reinstall GRUB2: 

Boot from Ubuntu Live CD & choose try ubuntu without any changes. When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sdb1 /mnt
```
this will mount ubuntu partition. Then run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

This will put GRUB2 on MBR of sdb. Reboot and set the 10 GB (sdb) as first hard disk to boot.

You want the sdb (10 GB) disk to boot first in the hard disk boot order. Change that in BIOS or if you can't do it in BIOS then do it with whatever method you are using for those two IDE disks: either with jumpers or Cable select or IDE ports on mobo. 


After that is done boot into Ubuntu and open a file browser (Places > Computer). Highlight your sdc in the left pane. When highlighted you will see its directories which means it is mounted. Now open a terminal and run ```
gksu nautilus
```

You are now running nautilus as root- be careful now! Navigate to Filesystem > media > (name of sdc disk). Right click in sdc disk and choose properties. Choose permissions tab and change permissions on Owner to you and choose create & delete files for folder access. This will change permissions to read/write for sdc. I also change group to my group and set folder access to access files. Close both file browsers and you may need to reboot for permissions to take effect.

Also run in terminal from Ubuntu ```
sudo update-grub
``` to refresh the grub.cfg

P.S. next time you install Ubuntu do not unplug any disks- that is not necessary. Also that may confuse GRUB as the disk designations may change depending on how you put them back ( i.e. sda may become sdb, etc)
Windows is another story- you need to make the disk you are installing to first in BIOS boot order because windows will try to write to the MBR of the first disk to boot.

---

### Post by FatLabs on 2010-01-11
Hey Thanks for the last message.  Only I'm not sure I have to do it anymore because, it turns out the grub menu is now allowing me to boot into windows.  Earlier today Update Manager installed some updates & now the option to go to Ubuntu or Windows is working.  I'm happy, but I also know that having Ubuntu as slave isn't ideal.

1.  Do you recommend I go ahead with the instructions above to make sure everything is clean or should I just leave it as is since it's now working?
2.  I did notice that there were some errors with the updates (something messages about using device map came up).  I haven't quite figured out where the error log for this is stored.  Again -- do you think I should hunt this down as well?

Thanks again.

---

### Post by presence1960 on 2010-01-11
> **FatLabs said:**
> Hey Thanks for the last message.  Only I'm not sure I have to do it anymore because, it turns out the grub menu is now allowing me to boot into windows.  Earlier today Update Manager installed some updates & now the option to go to Ubuntu or Windows is working.  I'm happy, but I also know that having Ubuntu as slave isn't ideal.

1.  Do you recommend I go ahead with the instructions above to make sure everything is clean or should I just leave it as is since it's now working?
2.  I did notice that there were some errors with the updates (something messages about using device map came up).  I haven't quite figured out where the error log for this is stored.  Again -- do you think I should hunt this down as well?

Thanks again.
As long as both your OSs are booting from GRUB I would leave it be. If it isn't broke don't fix it! But if you are still having problems with sdc write permissions I would do what I suggested to change those permissions. I gave you a graphical way to do it since I didn't know your expertise level.

After that is done boot into Ubuntu and open a file browser (Places > Computer). Highlight your sdc in the left pane. When highlighted you will see its directories which means it is mounted. Now open a terminal and run ```
gksu nautilus
```

You are now running nautilus as root- be careful now! Navigate to Filesystem > media > (name of sdc disk). Right click in sdc disk and choose properties. Choose permissions tab and change permissions on Owner to you and choose create & delete files for folder access. This will change permissions to read/write for sdc. I also change group to my group and set folder access to access files. Close both file browsers and you may need to reboot for permissions to take effect.

---

### Post by FatLabs on 2010-01-12
Thanks gsmanners & presence1960!  I'm gonna go with the "don't fix it 'till it's broke".  I'm happy enough that the updates got it working.  Now I'm working on getting samba going!

---

