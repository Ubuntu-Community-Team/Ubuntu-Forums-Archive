---
title: "Boot errors after last grub update 9.10"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by pfwd.tech on 2009-12-09
I have recently done a fresh install of 9.10.
This morning the Update manager had a grub update amoungst others.
After updating and restarting my machine I can  no longer boot into the OS.

The boot process as is
1. Loads grub
GNU Grub version 1.97~Beta4
Linux-Header 2.6.31-16-generic
Linux-Header 2.6.31-16-generic (recovery)
Linux-Header 2.6.31-15-generic
Linux-Header 2.6.31-15-generic (recovery)
 Linux-Header 2.6.31-14-generic
 Linux-Header 2.6.31-14-generic (recovery)
  
2. It doesn't matter which  header i boot into I still get the following
White Ubuntu logo in the middle of a black screen

3. After a minute or two it says something along the lines of:
Gave Up wating for root device
- Common problems:
boot args(cat/proc/cmdline)
Alert! /dev/sdb5 dows not exist
dropping to shell

Busy box v1.13.3
Initramfs

How do I resolve this?

Thanks in advance

---

### Post by Fafler on 2009-12-09
From the grub menu, select a kernel, press e to edit the boot parameters. Remove the word silent. Press enter and b to boot. The kernel should now boot without the splash image and tell you a lot more. Look for something harddrive related. Maybe the partition isn't sda5? Maybe the kernel gives some reason for not finding it?

I don't have computer here i can reboot, so some of the things might look a little different.

---

### Post by pfwd.tech on 2009-12-09
> **Fafler said:**
> From the grub menu, select a kernel, press e to edit the boot parameters. Remove the word silent. Press enter and b to boot. The kernel should now boot without the splash image and tell you a lot more. Look for something harddrive related. Maybe the partition isn't sda5? Maybe the kernel gives some reason for not finding it?

I don't have computer here i can reboot, so some of the things might look a little different.

Thanks for the reply,
I dont have the word 'silent'
This is what I have:
```
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb5 ro quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
```Any ideas?

---

### Post by darkod on 2009-12-09
How about booting with the LiveCD and in terminal executing:
sudo fdisk -l

to look at your partitions.

---

### Post by presence1960 on 2009-12-09
Since the problem is relating to booting & your hard disk run the boot info script. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by pfwd.tech on 2009-12-09
> **darkod said:**
> How about booting with the LiveCD and in terminal executing:
sudo fdisk -l

to look at your partitions.
This gives me:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x077cca48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         365     2931831   82  Linux swap / Solaris
/dev/sda2             366       12634    98550742+   5  Extended
/dev/sda3           12635       24792    97659135   83  Linux
/dev/sda5             366       12634    98550711   83  Linux
ubuntu@ubuntu:~$ 

```

---

### Post by pfwd.tech on 2009-12-09
> **presence1960 said:**
> Since the problem is relating to booting & your hard disk run the boot info script. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This gives me:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x077cca48

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     5,863,724     5,863,662  82 Linux swap / Solaris
/dev/sda2           5,863,725   202,965,209   197,101,485   5 Extended
/dev/sda5           5,863,788   202,965,209   197,101,422  83 Linux
/dev/sda3         202,965,210   398,283,479   195,318,270  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="09f8e79b-13db-429f-994e-f8377e775423" TYPE="swap" 
/dev/sda3: UUID="08072934-73bd-450e-adff-cc84ef2ae823" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ba019888-ef6c-4279-a7d4-157d2e3380b1" TYPE="ext4" 

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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro single 
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
UUID=ba019888-ef6c-4279-a7d4-157d2e3380b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=09f8e79b-13db-429f-994e-f8377e775423 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



=================== sda5: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.31-14-generic
   3.0GB: boot/initrd.img-2.6.31-15-generic
   3.0GB: boot/initrd.img-2.6.31-16-generic
   3.0GB: boot/vmlinuz-2.6.31-14-generic
   3.0GB: boot/vmlinuz-2.6.31-15-generic
   3.0GB: boot/vmlinuz-2.6.31-16-generic
   3.0GB: initrd.img
   3.0GB: initrd.img.old
   3.0GB: vmlinuz
   3.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

I removed the fstab entries for security reasons ( They had ips etc)

---

### Post by darkod on 2009-12-09
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic [COLOR=Red]root=/dev/sdb5[/COLOR] ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}

You have only one hdd (at the moment), /dev/sda but in your grub.cfg root is set to /dev/sdb5 instead of /dev/sda5. Did you have another drive when you installed ubuntu?

While booted with the LiveCD go into your installation and try update-grub. I'm not experienced with this but from what I've seen you need to:

sudo mount /dev/sda5 /mnt
sudo chroot /mnt update-grub

Presence will correct me if wrong. This would be the first step and grub2 should sort itself out. If that doesn't work, we'll see...

---

### Post by presence1960 on 2009-12-09
> **pfwd.tech said:**
> This gives me:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x077cca48

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     5,863,724     5,863,662  82 Linux swap / Solaris
/dev/sda2           5,863,725   202,965,209   197,101,485   5 Extended
/dev/sda5           5,863,788   202,965,209   197,101,422  83 Linux
/dev/sda3         202,965,210   398,283,479   195,318,270  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="09f8e79b-13db-429f-994e-f8377e775423" TYPE="swap" 
/dev/sda3: UUID="08072934-73bd-450e-adff-cc84ef2ae823" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ba019888-ef6c-4279-a7d4-157d2e3380b1" TYPE="ext4" 

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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro single 
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
UUID=ba019888-ef6c-4279-a7d4-157d2e3380b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=09f8e79b-13db-429f-994e-f8377e775423 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



=================== sda5: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.31-14-generic
   3.0GB: boot/initrd.img-2.6.31-15-generic
   3.0GB: boot/initrd.img-2.6.31-16-generic
   3.0GB: boot/vmlinuz-2.6.31-14-generic
   3.0GB: boot/vmlinuz-2.6.31-15-generic
   3.0GB: boot/vmlinuz-2.6.31-16-generic
   3.0GB: initrd.img
   3.0GB: initrd.img.old
   3.0GB: vmlinuz
   3.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

I removed the fstab entries for security reasons ( They had ips etc)

Your Ubuntu entries in grub.cfg seem incomplete. See mine and compare them to yours:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-16-generic
```

Did you choose the option when asked during the grub-pc update to use the package maintainer's version? At any rate I would try to reinstall GRUB from Live CD. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by pfwd.tech on 2009-12-09
Oh I do feel a bit silly.
I had look at the drives and found a sata cable out of socket.
Put that back in and it all works.

At least I've learnt how to investigate boot errors.

Thanks
for your help.

---

### Post by presence1960 on 2009-12-09
> **pfwd.tech said:**
> Oh I do feel a bit silly.
I had look at the drives and found a sata cable out of socket.
Put that back in and it all works.

At least I've learnt how to investigate boot errors.

Thanks
for your help.

Well if that is the worst thing that happens today you are fortunate indeed. :popcorn:

---

### Post by izzzzzz6 on 2009-12-11
Hi, i appreciate that you guys are trying to solve programming issues HOWEVER!!!!! Isn't this meant to be easy simple stuff? That is why i got recommended Ubuntu. I am completely lost and whoever posted this thread obviously spent 3 or four days mind boggling, to me thats enough to throw all computers in the bin and live a life in the woods. How bloody frustrating!!!! So i have this old laptop and i want it to pickup the internet via a usb dish antennae and retransmit ~(talk) to my ethernet router so that the computers in our shared house can all access the internet via the old laptop. First thing was that the old (packard bell easynote laptop) laptop had a screwed drive, it was partitioned in half so that the bad sectors were no longer a problem, then we installed ubuntu (which to me sounds like some african or jungle type word, a pretty cool word but not really ooozing the concept of technology, which obviously i'm not really into anyway, all this high teck stuff has cost me more time in my life than it will ever seem to pay back so far, whatever that means!!!))) So whats the point of all of this anyway???? Well so far i9 loaded ubuntu onto the laptop and it didn't work, GREAT!! So we were trying to get it to connect to the internet but it doesn't recognise the network card, my flatmate did something and now it just says:
  Loading, please wait.....

  BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
  Enter 'help' for a list of built-in commands.

  (initramfs)

So all this is gobbaldygook to me, i just want something that works and i don't want to spend two weeks trying to find out why it is so complicated. Why can't this stuff just work it all out, why doesn't it just work!!!!! if all the answers are on here then why can't they just be in the program, why do i have to waste my time brainstorming this crap when i just want to connect!!! What is the point of ubantu anyway apart from the cool name????? If someone can make sense of this big waste of time and effort then please tell me how and why?????? Yes this is bloody frustrating. I just don't get it

---

### Post by presence1960 on 2009-12-11
> **izzzzzz6 said:**
> Hi, i appreciate that you guys are trying to solve programming issues HOWEVER!!!!! Isn't this meant to be easy simple stuff? That is why i got recommended Ubuntu. I am completely lost and whoever posted this thread obviously spent 3 or four days mind boggling, to me thats enough to throw all computers in the bin and live a life in the woods. How bloody frustrating!!!! So i have this old laptop and i want it to pickup the internet via a usb dish antennae and retransmit ~(talk) to my ethernet router so that the computers in our shared house can all access the internet via the old laptop. First thing was that the old (packard bell easynote laptop) laptop had a screwed drive, it was partitioned in half so that the bad sectors were no longer a problem, then we installed ubuntu (which to me sounds like some african or jungle type word, a pretty cool word but not really ooozing the concept of technology, which obviously i'm not really into anyway, all this high teck stuff has cost me more time in my life than it will ever seem to pay back so far, whatever that means!!!))) So whats the point of all of this anyway???? Well so far i9 loaded ubuntu onto the laptop and it didn't work, GREAT!! So we were trying to get it to connect to the internet but it doesn't recognise the network card, my flatmate did something and now it just says:
  Loading, please wait.....

  BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
  Enter 'help' for a list of built-in commands.

  (initramfs)

So all this is gobbaldygook to me, i just want something that works and i don't want to spend two weeks trying to find out why it is so complicated. Why can't this stuff just work it all out, why doesn't it just work!!!!! if all the answers are on here then why can't they just be in the program, why do i have to waste my time brainstorming this crap when i just want to connect!!! What is the point of ubantu anyway apart from the cool name????? If someone can make sense of this big waste of time and effort then please tell me how and why?????? Yes this is bloody frustrating. I just don't get it

Just my opinion: maybe you should go back to windows. I don't mind helping people, and I understand people get frustrated. But opinions like those you have expressed will keep quite a few people from replying to help you.

We were not trying to solve programming issues BTW. Linux (Ubuntu included) is not for everyone. One of the biggest mistakes (again my opinion) was when those who are developing Linux decided to market it as ready for windows users because they decided to make it a little windows like. Thank God linux is not like windows, that is exactly why I use it. Read [this]("http://linux.oneandoneis2.org/LNW.htm").

Don't take this personally but you have two choices. if you want to try and learn linux then make a commitment to stick it out and learn & work through issues. Or go back to windows.

Most windows users today are spoiled because they have a recovery partition or recovery disk(s) which not only installs Windows but contains and installs all the drivers for their specific hardware devices. Try installing windows from an installation CD/DVD and then start pulling your hair out getting drivers for your devices because they are not most likely contained in the windows OS or the install disk. If you have never installed windows from an installation CD/DVD rather than a recovery  partition/CD/DVD then you have never installed the Windows OS yourself. I call recovery partitions/CD/DVDs "installs for dummies." Even though the end user has no choice in the matter because the manufacturers made that decision. But that decision has spawned a whole generation of users who know absolutely close to nothing about installing an Operating System and who have little appreciation of just how trying and technical it can become to actually install an OS and get everything working. When those type of computer users come to Linux they are usually lost.

BTW this is your first post here? You have a strange way of asking for help! I would say welcome to our community but my opinion is you are not going to last here.

---

