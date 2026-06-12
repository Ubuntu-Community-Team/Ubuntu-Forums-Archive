---
title: "Missing boot loader"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by DeepSix on 2009-11-25
So I'm attempting to dual boot ubuntu with vista. I formatted a Win 7 RC (that was apparently the main booter) to put ubuntu on that drive. I assumed that grub would load fine and they're be no issue in booting. Instead I have no boot loader and am incapable of repairing vista to just use it's as I'm running into errors there too...So how do I get grub to work? Or maybe another issue that I'm not aware of.

Also worthy of note, this machine has been having boot loading problems for a while that has survived formats. It would not find one just as it is now. I found a cheesy work around involving putting in a OS disk in my drive and as it was looking for the disk and the subsequent ask for user input to load the disk I guess "tricked" it, because it would then load the OS, without that bootable disk though, it would be Missing Boot Mgr

---

### Post by presence1960 on 2009-11-25
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by DeepSix on 2009-11-25
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3739ffc1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ce0db70

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x079bcd93

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    74,862,899    74,862,837  83 Linux
/dev/sdc2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdc5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="5284D08E84D07647" LABEL="Storage Disk 2" TYPE="ntfs" 
/dev/sdb1: UUID="828456B58456AB83" TYPE="ntfs" 
/dev/sdc1: UUID="d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d" TYPE="ext4" 
/dev/sdc5: UUID="0889b070-def7-4da1-9e7b-3bf2bb88ec2c" TYPE="swap" 

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
/dev/sda1 on /media/Storage Disk 2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/828456B58456AB83 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0889b070-def7-4da1-9e7b-3bf2bb88ec2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

Just fyi, the 500gb drive contains no OS.

---

### Post by presence1960 on 2009-11-26
> **DeepSix said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3739ffc1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ce0db70

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x079bcd93

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    74,862,899    74,862,837  83 Linux
/dev/sdc2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdc5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="5284D08E84D07647" LABEL="Storage Disk 2" TYPE="ntfs" 
/dev/sdb1: UUID="828456B58456AB83" TYPE="ntfs" 
/dev/sdc1: UUID="d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d" TYPE="ext4" 
/dev/sdc5: UUID="0889b070-def7-4da1-9e7b-3bf2bb88ec2c" TYPE="swap" 

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
/dev/sda1 on /media/Storage Disk 2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/828456B58456AB83 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=d82ae4d5-c9e8-4dd7-a506-89b76a2b3d5d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0889b070-def7-4da1-9e7b-3bf2bb88ec2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

Just fyi, the 500gb drive contains no OS.

This is what i would do. I would reinstall GRUB 2 to sdc. See [here]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")- you will need 9.10 Live CD/USB.

You can also try [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

Then when rebooting go into BIOS and set your sdc disk (40 GB) as first disk to boot in hard disk boot order. Save changes to CMOS and continue booting. GRUB menu should appear.

---

### Post by DeepSix on 2009-11-26
So I didn't really understand what I was supposed to do with the first link, I did go ahead and do the 2nd one, but unfortunately they asked me to verify via the method of the first link. After that I followed your advice on boot order and changed sdc to boot 1st. Limited success occurred, a boot loader was found, specifically GRUB...but...no Windows OS was seen and ubuntu though listed, wasn't found:

error:no such device: d82ae-4d-c9e8-4dd7-a506-89b76a2b3d5d

---

### Post by drs305 on 2009-11-26
> **DeepSix said:**
> So I didn't really understand what I was supposed to do with the first link, I did go ahead and do the 2nd one, but unfortunately they asked me to verify via the method of the first link. After that I followed your advice on boot order and changed sdc to boot 1st. Limited success occurred, a boot loader was found, specifically GRUB...but...no Windows OS was seen and ubuntu though listed, wasn't found:

error:no such device: d82ae-4d-c9e8-4dd7-a506-89b76a2b3d5d

If you can at least get to the Grub 2 menu, or a prompt, you can probably boot into Ubuntu. From the menu, you can press "e" to edit the highlighted entry. You may need to change the "set root=(hdX,Y)" line, remove the "search" line if one exists, and change the "root=/dev/sdXY" lines to get G2 to point to the correct place. 

Or you can drop to the Grub 2 command line and boot that way. Both methods are detailed in the G2 community doc.
[https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")
Same page as referred to in earlier posts, but a different section.

---

### Post by DeepSix on 2009-11-26
> **drs305 said:**
> change the "root=/dev/sdXY" lines to get G2 to point to the correct place. 

I did not see this line on the menu, nor did I see in the example screen from your first link. Was I supposed to add it? If so which line? I did the other suggestions and got:

error: cannot get C/H/S values

Again, I wasn't sure what I was supposed to do with the cmd line. I tried "linux" cmd and got an error message, which I *believe* was could not find.

---

### Post by drs305 on 2009-11-26
> **DeepSix said:**
> I did not see this line on the menu, nor did I see in the example screen from your first link. Was I supposed to add it? If so which line? I did the other suggestions and got:

error: cannot get C/H/S values

Again, I wasn't sure what I was supposed to do with the cmd line. I tried "linux" cmd and got an error message, which I *believe* was could not find.

If you press "e" to edit the entry, it should look something like this:
> 
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5a880a39-36a1-46f5-b106-e979608f295a
linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=5a880a39-36a1-46f5-b106-e979608f295a ro   
initrd	/boot/initrd.img-2.6.31-15-generic

Change it to the following (delete the red, change the blue):
> 
insmod ext2
set root=([COLOR="Navy"]**hd0,1**[/COLOR])
[COLOR="Red"]search --no-floppy --fs-uuid --set 5a880a39-36a1-46f5-b106-e979608f295a[/COLOR]
linux	/boot/vmlinuz-2.6.31-15-generic root=[COLOR="Navy"]/dev/**sda1**[/COLOR] ro   
initrd	/boot/initrd.img-2.6.31-15-generic


You might be able to simplify it even more by making it look like this:
> 
insmod ext2
set root=([COLOR="Navy"]hd0,1[/COLOR])
linux	/vmlinuz root=[COLOR="Navy"]/dev/sda1[/COLOR] ro   
initrd	/initrd.img


As for trying to boot to the command line, you are essentially buiding each line, one at a time, to create something similar to the one above. 

When you typed the "linux" line and got the file not found, the line should have been something like:
> linux /vmlinuz root=/dev/sda5 ro
before you hit ENTER. 

Remember that in Grub 2 for the "(hdX,Y) entries, the first drive is 0 and the first partition is 1.

---

### Post by DeepSix on 2009-11-26
Well I got ubuntu to load from said method, thanks, but I feel as if there's something else that must be done. For instance am I gonna hafta go through this everytime?

---

### Post by drs305 on 2009-11-26
> **DeepSix said:**
> Well I got ubuntu to load from said method, thanks, but I feel as if there's something else that must be done. For instance am I gonna hafta go through this everytime?

No you won't, but you are correct that you will need to fix the menu.

First run "sudo update-grub" to generate a new menu. That may take care of it right away.

Run "sudo blkid" and compare the UUID's to what's in /boot/grub/grub.cfg.

Another thing to do is to create a menuentry in /etc/grub.d/40_custom that you know works. Copy the /boot/grub/grub.cfg entry for your Ubuntu kernel, copy it to 40_custom and then modify it however you did on the command line to get it to boot. That way you will have a working menuentry even if the automatic one gets screwed up.

Since the 40_custom file is not updated automatically, it's best not to use a specific kernel. Use the format I gave near the end of the previous post (making the necessary changes):
> 
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img 


Run "sudo update-grub" to add the 40_custom menuentry to the Grub 2 menu. Check /boot/grub/grub.cfg to see if it was added.

Ideally, the first update-grub will have fixed your menu so it will work without any tweaking, and that is our goal. Making the entry in 40_custom is our "insurance policy". 

If the problem is the "search" line, I think we are still looking for a permanent solution from the devs on that one. If it's something else, hopefully update-grub fixed it.

If while looking at your files you don't understand any of it, just read up on G2 in the community doc or my other links and if you still need help  - ask away!

---

### Post by DeepSix on 2009-11-27
> **drs305 said:**
> First run "sudo update-grub" to generate a new menu. That may take care of it right away.

Run "sudo blkid" and compare the UUID's to what's in /boot/grub/grub.cfg.

It didn't, and I'm not sure what I'm to compare.

> **drs305 said:**
> Another thing to do is to create a menuentry in /etc/grub.d/40_custom that you know works. Copy the /boot/grub/grub.cfg entry for your Ubuntu kernel, copy it to 40_custom and then modify it however you did on the command line to get it to boot. That way you will have a working menuentry even if the automatic one gets screwed up.

Just copy and paste the entire .cfg?

---

### Post by oldfred on 2009-11-27
Are you still getting the C/H/S error. That indicates in BIOS you said you wanted to manually configure the hard drive.  I have not had to do that for 10 years and you should change the drive setting to auto in BIOS. Perhaps some systems ignored that setting and still worked before.

You would only copy one or two entries into 40_custom where the auto generated ones were not quite correct so you could edit them. Seems to be required for windows and other operating systems in some configurations.

typical windows entry might be (but you have to have the correct partition and UUID. And sometimes edit out then entire uuid line:

menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" { 
    insmod ntfs 
    set root=(hd1,[COLOR=DarkRed]1[/COLOR]) 
    search --no-floppy --fs-uuid --set [COLOR=DarkRed]828456B58456AB83[/COLOR]
    drivemap -s (hd1) ${root} 
    chainloader +1 
}

---

### Post by DeepSix on 2009-11-27
> **oldfred said:**
> Are you still getting the C/H/S error. That indicates in BIOS you said you wanted to manually configure the hard drive.  I have not had to do that for 10 years and you should change the drive setting to auto in BIOS. Perhaps some systems ignored that setting and still worked before.

Um, I've gotten it, but I can't remember how to reproduce it. I checked, by the "manually configure" you mean those settings like cylinder and the like? That's always been on auto, I just checked.

> **oldfred said:**
> You would only copy one or two entries into 40_custom where the auto generated ones were not quite correct so you could edit them. Seems to be required for windows and other operating systems in some configurations.

typical windows entry might be (but you have to have the correct partition and UUID. And sometimes edit out then entire uuid line:

menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" { 
    insmod ntfs 
    set root=(hd1,[COLOR=DarkRed]1[/COLOR]) 
    search --no-floppy --fs-uuid --set [COLOR=DarkRed]828456B58456AB83[/COLOR]
    drivemap -s (hd1) ${root} 
    chainloader +1 
}

So um add:
 
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	linux /vmlinuz root=/dev/sdc1 ro
	initrd /initrd.img

menuentry "Vista (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 828456B58456AB83
drivemap -s (hd1) ${root}
chainloader +1
}

to the 40_custom file?

---

### Post by oldfred on 2009-11-27
You really should not need the Ubuntu entry, I have only seen entries required for other linux installs the osprober could not find.

You are missing the } at the end of the Ubuntu entry. It must be on a separate line like the windows entry.

---

### Post by DeepSix on 2009-12-04
I let the problem stagnant because I had a working OS, however I'm missing my windows. So needed or not for Ubuntu, the entry worked, but the windows one did not.

---

### Post by DeepSix on 2009-12-06
So let me elaborate a little more, windows shows up in GRUB, but if I click I get the error "BOOTMGR is missing". I'm getting the point where I'm just gonna nuke Ubuntu and put windows on this drive. I've ran into countless problems trying to use this OS the past week, on top of which a new error where 2 files in /var/local/ are taking up 14 GB per. So if I can't even some sort of dual boot working, I'll just go to single boot.

---

### Post by oldfred on 2009-12-06
Grub cannot boot a bad windows. Your Vista install does not look complete. I would set the window drive to be first in BIOS so it is supposed to boot windows and run the windows repair. Make sure the boot flag is on for the windows partition before trying to repair. Then when you switch the BIOS to the Ubuntu drive first you and run the update-grub and it will find it or the manual entry will work.

I like having multiple operating systems on different drives with the MBR of that drive set to boot that operating system. Grub is more flexible at booting other systems so I make the the default boot drive and let it find other systems. If ever the hard drive has issues I can switch drive order in BIOS and still boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Did you previously have another windows install that you deleted?  Windows combines its boot into the one windows with the boot flag on. If you delete that copy of windows the other will have to be repaired to work.

---

### Post by DeepSix on 2009-12-07
> **oldfred said:**
> Grub cannot boot a bad windows. Your Vista install does not look complete. I would set the window drive to be first in BIOS so it is supposed to boot windows and run the windows repair. Make sure the boot flag is on for the windows partition before trying to repair. Then when you switch the BIOS to the Ubuntu drive first you and run the update-grub and it will find it or the manual entry will work.

I like having multiple operating systems on different drives with the MBR of that drive set to boot that operating system. Grub is more flexible at booting other systems so I make the the default boot drive and let it find other systems. If ever the hard drive has issues I can switch drive order in BIOS and still boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Did you previously have another windows install that you deleted?  Windows combines its boot into the one windows with the boot flag on. If you delete that copy of windows the other will have to be repaired to work.

My Vista has worked, but loaded of windows 7 bootloader. It can't find vista in the normal repairer, I tried that right away. Also what is a boot flag? I followed the instructions on the links.

I tried:
```
bootrec.exe /fixboot
```

"Element not found"

```
bootrec.exe /fixmbr
```

Did work.

should I do:

```
bootrec.exe /RebuildBcd
```

?

Also worthy of note, now my ubuntu is unbootable. Am I to do what I did before to get it working again?

---

### Post by oldfred on 2009-12-07
I do not understand, do you have both Vista and Win7? Or is your windows working ok.

I would make your third drive first in the BIOS if you can select it. Then install grub2 to the MBR of that drive. grub2 works slightly better if it is in the same drive as the install of ubuntu. Plus I prefer that configuration as if a drive fails you can switch drives and still boot your system since the windows boot loader is still in the windows drive. After you reinstall grub run the update-grub command.

The boot flag is vital to windows. It uses it to determine what partition to boot from. You can set the boot flag with gparted.

If you have multiple windows installs the booting is combined into one partition. The other windows will not boot without the first. If you are installing a second windows there is a work around that will let you boot both windows from grub, but not both from windows.

---

### Post by DeepSix on 2009-12-08
> **oldfred said:**
> I do not understand, do you have both Vista and Win7? Or is your windows working ok.

I would make your third drive first in the BIOS if you can select it. Then install grub2 to the MBR of that drive. grub2 works slightly better if it is in the same drive as the install of ubuntu. Plus I prefer that configuration as if a drive fails you can switch drives and still boot your system since the windows boot loader is still in the windows drive. After you reinstall grub run the update-grub command.

The boot flag is vital to windows. It uses it to determine what partition to boot from. You can set the boot flag with gparted.

If you have multiple windows installs the booting is combined into one partition. The other windows will not boot without the first. If you are installing a second windows there is a work around that will let you boot both windows from grub, but not both from windows.

I have Vista, I had 7, when I had 7 Vista loaded fine, I installed ubuntu in the same drive 7 was, thus overwritting it and it's bootloader, Vista has not loaded since. The boot flag was already on via gparted. Also the none-booting other ntfs file system is also flagged as boot...hmmm.

I'm also wondering, if perhaps the earlier menuentry I created was incorrect, you asked me to compare the partition and UUID. Well I did ensure the UUID was correct, but I'm not satisfied I choose the correct partition, how am I to be sure?

---

### Post by oldfred on 2009-12-08
If you go back and look at your result.txt. See Presence's original comments. You need to fix the Vista boot on the windows hard drive then make the Ubuntu drive first and install grub there.

---

### Post by DeepSix on 2009-12-08
> **oldfred said:**
> If you go back and look at your result.txt. See Presence's original comments. You need to fix the Vista boot on the windows hard drive then make the Ubuntu drive first and install grub there.

Yes ok, I see. sdb1. But I had to state which hdd/partition three times. 
/dev/sdb1
set root=(hd1,1)
drivemap -s (hd1) ${root} 

How am I to ensure those last two are accurate? 

Also as I said I've tried repairing Vista, I changed boot order, I tried that advice from one of your links: bootrec.exe /fixboot Did not work. I successfully used bootrec.exe /fixmbr but to no effect. I asked if bootrec.exe /RebuildBcd would work, then I'm not quite sure what it would be doing either, google didn't really explain. I might also mention bootrec.exe /ScanOs did locate it.

---

### Post by oldfred on 2009-12-08
I am not familiar with the repair of Vista but normally the fixboot, fixmbr works. This also mentions the rebuildbcd.

How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

