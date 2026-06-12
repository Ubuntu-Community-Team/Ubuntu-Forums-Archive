---
title: "Cannot dual boot Win7 and Ubuntu 9.10"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by mr.vanker on 2010-01-20
Alright, I've tried everything before posting here, but I don't think that I can do it myself. ..

I just upgraded my Inspiron 6000 laptop hdd from the stock 60GB to a WD 320GB. Now that I have enough room, I want to dual boot Ubuntu.

So, I restored my Windows partition from an image made with Win7 backup. I resized the partition to split evenly between Ubuntu and Win7. Then I tried installing Ubuntu from my external HDD. I got a Grub error saying that it couldn't find the partition to boot. It didn't give me any boot options.

Next, I was finally able to burn the ISO to an actual CD and try the installation. Still nothing. So I tried to use EasyBCD to boot, and still nothing. Anybody have experience with a similar issue? Do I need to make the Ubuntu partition a logical partition instead of primary? :confused:

---

### Post by darkod on 2010-01-20
> **mr.vanker said:**
> Then I tried installing Ubuntu from my external HDD. I got a Grub error saying that it couldn't find the partition to boot. It didn't give me any boot options.


How exactly did you try to install it from the external HDD? Usually you would use CD or usb stick.

Then you say you used a cd and still nothing. Can you give more details what that nothing means and what happens?

Also when you split the disk I hope you didn't leave the space for ubuntu formatted as ntfs and allocated to a partition. It's best to be unallocated.

---

### Post by mr.vanker on 2010-01-20
Yeah, sorry, I need to give more details...

I was installing from the HDD using unetbootin.

And no, I didn't format it in Windows, I used GParted, to format it. I've tried Ext2, Ext3 and 4 filesystems. I read on the EasyBCD website that Ext3 was the only filesystem that would work.

When I say nothing, I'm sorry... I wasn't being specific. I get errors. with EasyBCD it says that the partition cannot be booted. If I try to used Grub to boot, it says that the partition does not exist.

Honestly, I like Ubuntu, but I have _never_ had a simple install. I always have to screw around with it. Sometimes it can be a bit frustrating.

---

### Post by presence1960 on 2010-01-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Before doing anything it would be advisable to see your setup & boot process. If you just blindly attempt fixes you may make matters worse.

---

### Post by Maheriano on 2010-01-20
Install Ubuntu, then install Windows 7. Then search posts on my username and Windows 7 to see how I fixed the dual boot MBR issue.

---

### Post by mr.vanker on 2010-01-20
Here is the info from the script.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #312480315 on boot drive #1
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 413209243 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,477,392   312,477,330   7 HPFS/NTFS
/dev/sda2         312,480,315   625,137,344   312,657,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="f2f23c22-22e5-41ae-bdbe-1041f029675b" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 159.9GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
 159.9GB: boot/initrd.img-2.6.31-14-generic
 159.9GB: boot/vmlinuz-2.6.31-14-generic
 159.9GB: initrd.img
 159.9GB: vmlinuz
```

I would try installing Win7 first, but I am using my backup image, so I don't want to do fresh win7 installation.

Also, when I try to reinstall grub (to write over the MS MBR), the terminal says that grub cannot be found, and that I must install it.

---

### Post by presence1960 on 2010-01-20
> **mr.vanker said:**
> Here is the info from the script.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #312480315 on boot drive #1
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 413209243 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,477,392   312,477,330   7 HPFS/NTFS
/dev/sda2         312,480,315   625,137,344   312,657,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="f2f23c22-22e5-41ae-bdbe-1041f029675b" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 159.9GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
 159.9GB: boot/initrd.img-2.6.31-14-generic
 159.9GB: boot/vmlinuz-2.6.31-14-generic
 159.9GB: initrd.img
 159.9GB: vmlinuz
```

I would try installing Win7 first, but I am using my backup image, so I don't want to do fresh win7 installation.

Also, when I try to reinstall grub (to write over the MS MBR), the terminal says that grub cannot be found, and that I must install it.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR="Red"]Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #312480315 on boot drive #1[/COLOR]
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 413209243 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

You should have installed GRUB to MBR of your disk. Whatever else you added (was it Easy BCD?) see red above- get rid of that. Then boot the 9.10 Live CD & choose 'try ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sda2 /mnt
```
This will mount your Ubuntu partition. Now in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB on MBR. Reboot without the CD and when Ubuntu loads open a terminal and run ```
sudo grub-update
```
You should be good at that point.

---

### Post by mr.vanker on 2010-01-20
Well, I did what you said. However, I couldn't run the grub-update command:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
ubuntu@ubuntu:~$ sudo grub-update
sudo: grub-update: command not found
```

Is what I highlighted in red a problem? I'm not very knowledgeable on boot record stuff, so I'm not sure, just a hunch...

And I now cannot boot into either Windows or Ubuntu. Any other suggestions?

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
[COLOR="Red"]    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 413209243 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /boot/grub.[/COLOR]
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,477,392   312,477,330   7 HPFS/NTFS
/dev/sda2         312,480,315   625,137,344   312,657,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="f2f23c22-22e5-41ae-bdbe-1041f029675b" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 159.9GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
 159.9GB: boot/initrd.img-2.6.31-14-generic
 159.9GB: boot/vmlinuz-2.6.31-14-generic
 159.9GB: initrd.img
 159.9GB: vmlinuz
```

---

### Post by presence1960 on 2010-01-20
did you remove Easy BCD first?

---

### Post by mr.vanker on 2010-01-20
Yes, I deleted the entry for Ubuntu, and then uninstalled it.

---

### Post by presence1960 on 2010-01-20
> **mr.vanker said:**
> Yes, I deleted the entry for Ubuntu, and then uninstalled it.
I hate to do this but can you run another boot info script & post the new results for me please.

---

### Post by presence1960 on 2010-01-20
Nevermind I see you already did that. What happens when you boot? Do you get an error. I am thinking your BIOS can't read past 137 GB and you boot files are at 158 GB.

Older BIOS can't read past a certain point usually 137 GB even though the disk may be larger. The solution is to create a separate boot partition at the beginning of the hard disk. But that would involve repartitioning and reinstalling Ubuntu and restoring your image of windows. Give me some time to look up your model and see what I can find.

P.S. sometimes a BIOS update will fix the issue.

---

### Post by presence1960 on 2010-01-20
OK, that model is pre 2005 because the BIOS update on the dell site is from 2005. I kind of think that is your problem. Your BIOS can not read past 137 GB no matter how large your disk is. If you want to dual boot you are going to have to create a separate /boot partition at the beginning of the disk to overcome the older BIOS limitation. You can do this when you install Ubuntu.

I looked at the BIOS update on the site and under fixes it did not specifically address the readable area on the disk for BIOS, so I am not certain updating the BIOS will help. You may want to contact Dell to find that out.

In the meantime you can get windows up and running by booting the windows DVD and fixing the MBR. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to Vista/windows 7) and follow the instructions.

---

### Post by presence1960 on 2010-01-20
Here is a [link]("http://www.pcguide.com/ref/hdd/bios/size.htm") to help you understand the BIOS limit on reading hard disks. You have to understand at the time of manufacture of those computers disk sizes that we use today were unheard of, hence a lot of older machines BIOS can't read past a certain point on the hard disk depending on when the computer was manufactured & the date of the BIOS

---

### Post by mr.vanker on 2010-01-21
>  **After reading the previous posts:**

Whoops... I didn't see that the thread went to a second page after my post... I'll take a look at what you wrote.

I do understand the BIOS restrictions... at least to the extent that the way the ASM they used for the BIOS can't handle that much HDD space.

Right now, I'm moving the Windows partition over so I can put a boot partition at the beginning of the drive. I'll try re-installing Ubuntu when that's done, and post the results.

So, I may have made some progress... I now only get a Grub error 17. And I have a different error from the boot_info_script. Any more ideas?

thanks a lot for your help already, it was Presence's grub-update post that got me where I am now. However the grub-update command wouldn't work.
```
ubuntu@ubuntu:~$ sudo grub-update
sudo: grub-update: command not found

```
was all I got...

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 413209243 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,477,392   312,477,330   7 HPFS/NTFS
/dev/sda2         312,480,315   625,137,344   312,657,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="f2f23c22-22e5-41ae-bdbe-1041f029675b" SEC_TYPE="ext2" TYPE="ext3" 

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


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2f23c22-22e5-41ae-bdbe-1041f029675b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f2f23c22-22e5-41ae-bdbe-1041f029675b /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 159.9GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
 159.9GB: boot/grub/stage2
 159.9GB: boot/initrd.img-2.6.31-14-generic
 159.9GB: boot/vmlinuz-2.6.31-14-generic
 159.9GB: initrd.img
 159.9GB: vmlinuz
```

---

### Post by presence1960 on 2010-01-21
```
[COLOR="Red"]=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.[/COLOR]
sda1: ________________________________________________________
```

GRUB should look to partition #2- sda2 that is where ubuntu is installed. Boot the Live CD again & go to desktop as before. Open a terminal and run
```
sudo mount /dev/sda2 /mnt
```
Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda 
```

Do not run sudo update-grub from the Live CD. Reboot without the Live CD and boot to ubuntu. Then run ```
sudo update-grub
```

Note that this still may not work as your files needed to boot are still outside the 137 GB limit:

```
=================== sda2: Location of files loaded by Grub: ===================


 159.9GB: boot/grub/core.img
 159.9GB: boot/grub/grub.cfg
 159.9GB: boot/grub/stage2
 159.9GB: boot/initrd.img-2.6.31-14-generic
 159.9GB: boot/vmlinuz-2.6.31-14-generic
 159.9GB: initrd.img
 159.9GB: vmlinuz
```

If this does not work your best bet is to format and repartition the disk since you have an image of windows 7. I would setup partitions like this:
sda1 200MB /boot ext2
sda2 20 GB extended 
sda5 18GB / ext3 ot ext4
sda6 2 GB swap
sda3 Windows 7 NTFS
sda4 shared data NTFS

sda5 & sda6 are logical partitions in side the extended partition (sda2)
This scheme will have all files needed to boot at the beginning of the disk and all OS inside the 137 GB limit. If you need help setting this up post back.

---

### Post by mr.vanker on 2010-01-21
Sounds good, I'll go ahead and give the disk repartitioning a try.

I do have a question about partitions though. What is the benefit of using a logical partition?

Also, what do you guys think about a swap partition? I have 2GB of ram on my laptop, and that is more than enough for my processor. If I understand swap correctly, it's like a page file in Windows. On another website, a guy brought up the fact that using a swap partition, puts wear on your drive and on certain setups uses CPU resources that wouldn't be needed if you didn't have the parition... any thoughts?

---

### Post by presence1960 on 2010-01-21
> **mr.vanker said:**
> Sounds good, I'll go ahead and give the disk repartitioning a try.

I do have a question about partitions though. What is the benefit of using a logical partition?

Also, what do you guys think about a swap partition? I have 2GB of ram on my laptop, and that is more than enough for my processor. If I understand swap correctly, it's like a page file in Windows. On another website, a guy brought up the fact that using a swap partition, puts wear on your drive and on certain setups uses CPU resources that wouldn't be needed if you didn't have the parition... any thoughts?

you will only need swap if you do a lot of resource intensive work or if you want to use suspend or hibernate. If you want to use suspend/hibernate features I recommend the same amount for swap as your installed RAM (2 GB)

Swap does no harm to your disk, that is an old wives tale. I have 4 GB of RAM and I could get away with no swap. But I use hibernate frequently so I have a 4 GB swap partition.

---

### Post by mr.vanker on 2010-01-21
Okay, I'll take the swap into account when I get everything working.

So, I deleted everything on my drive, and restored Windows. I then moved the Windows partition to the end of the drive, made a boot partition at the front of the drive, and a root as the second partition. But now it says Missing Operating System when I boot it up.

Latest Boot Script Results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 64675 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /grub.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    312,673,095   625,137,344   312,464,250   7 HPFS/NTFS
/dev/sda2                  63       208,844       208,782  83 Linux
/dev/sda3             208,845   312,673,094   312,464,250   5 Extended
/dev/sda5             208,908   312,673,094   312,464,187  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8" TYPE="ext2" 
/dev/sda5: UUID="62b81d8b-897e-412a-b2e7-010723d06961" TYPE="ext4" 

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


============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 62b81d8b-897e-412a-b2e7-010723d06961
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8
	linux	/vmlinuz-2.6.31-14-generic root=UUID=62b81d8b-897e-412a-b2e7-010723d06961 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8
	linux	/vmlinuz-2.6.31-14-generic root=UUID=62b81d8b-897e-412a-b2e7-010723d06961 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-14-generic

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
UUID=62b81d8b-897e-412a-b2e7-010723d06961 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8 /boot           ext2    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'll keep playing around, and see what I can come up with. Any suggestions are appreciated as always.

---

### Post by presence1960 on 2010-01-22
> **mr.vanker said:**
> Okay, I'll take the swap into account when I get everything working.

So, I deleted everything on my drive, and restored Windows. I then moved the Windows partition to the end of the drive, made a boot partition at the front of the drive, and a root as the second partition. But now it says Missing Operating System when I boot it up.

Latest Boot Script Results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda2 and 
                       looks at sector 64675 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #2 for /grub.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a9ba56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    312,673,095   625,137,344   312,464,250   7 HPFS/NTFS
/dev/sda2                  63       208,844       208,782  83 Linux
/dev/sda3             208,845   312,673,094   312,464,250   5 Extended
/dev/sda5             208,908   312,673,094   312,464,187  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32B86E19B86DDC3B" TYPE="ntfs" 
/dev/sda2: UUID="0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8" TYPE="ext2" 
/dev/sda5: UUID="62b81d8b-897e-412a-b2e7-010723d06961" TYPE="ext4" 

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


============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 62b81d8b-897e-412a-b2e7-010723d06961
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8
	linux	/vmlinuz-2.6.31-14-generic root=UUID=62b81d8b-897e-412a-b2e7-010723d06961 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8
	linux	/vmlinuz-2.6.31-14-generic root=UUID=62b81d8b-897e-412a-b2e7-010723d06961 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32b86e19b86ddc3b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-14-generic

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
UUID=62b81d8b-897e-412a-b2e7-010723d06961 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=0e6a0a9c-14a3-407d-a132-f5d9f60c7cf8 /boot           ext2    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'll keep playing around, and see what I can come up with. Any suggestions are appreciated as always.

You moved windows now it is not where the bootloader thinks it should be. I gave you a mock up partition scheme to use at the end of post #16. You need to keep windows and the /boot partition within the 137 GB boundary for both to boot. You also want to install GRUB to MBR (/dev/sda) not a partition like you did.

---

