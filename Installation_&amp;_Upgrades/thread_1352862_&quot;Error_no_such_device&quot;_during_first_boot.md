---
title: "&quot;Error: no such device&quot; during first boot"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Dan Turton on 2009-12-12
Hi All, I'm a total noob to Ubuntu, but it saved my files from an XP crash and so I wanted to install it as my OS. Install seemed to go fine until the mandatory restart at the end. Early in the restart I got the following message after seeing "GRUB something" on the screen...

Error:  no such device: 40700f13-1216-403e-9c8c-2ffcda60ed2e
Failed to boot default entries.
Press any key to continue...

Pressing a key doesn't help. The bios is set to read from the hard disk first (where my ubuntu is!)

Please help!

---

### Post by earthpigg on 2009-12-12
did you have another hard drive or thumb drive plugged into the computer when you installed ubuntu, one that is not there now?

alternatively, after you finished installing ubuntu but before you restarted... did you use the partition editor to change anything?

---

### Post by presence1960 on 2009-12-12
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Dan Turton on 2009-12-12
No external HD or USB stick used.

I did overwrite an existing partition on install though

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> No external HD or USB stick used.

I did overwrite an existing partition on install though

run the boot info script & post the results!

---

### Post by Dan Turton on 2009-12-12
Thanks for your help!

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,168,134    75,168,072  83 Linux
/dev/sda2          75,168,135    78,140,159     2,972,025   5 Extended
/dev/sda5          75,168,198    78,140,159     2,971,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2050 MB, 2050560000 bytes
64 heads, 32 sectors/track, 1955 cylinders, total 4005000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32     4,004,351     4,004,320   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="40700f13-1216-403e-9c8c-2ffcda60ed2e" TYPE="ext4" 
/dev/sda5: UUID="1269350a-626b-4443-9149-4ab78b104e59" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="04C3-DC7A" TYPE="vfat" 

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
/dev/sdb1 on /media/04C3-DC7A type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 40700f13-1216-403e-9c8c-2ffcda60ed2e
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40700f13-1216-403e-9c8c-2ffcda60ed2e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=40700f13-1216-403e-9c8c-2ffcda60ed2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40700f13-1216-403e-9c8c-2ffcda60ed2e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=40700f13-1216-403e-9c8c-2ffcda60ed2e ro single 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=40700f13-1216-403e-9c8c-2ffcda60ed2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1269350a-626b-4443-9149-4ab78b104e59 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by presence1960 on 2009-12-12
Everything seems to be in order. Maybe try reinstalling GRUB2 from the Live CD/USB. Boot that and choose "try Ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```

Then run this command ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

When completed reboot and see what happens. I am thinking maybe GRUB messed up or something during install.

---

### Post by earthpigg on 2009-12-12
thank god for you grub gurus :D

---

### Post by Dan Turton on 2009-12-12
Sorry for my silly question, but... Grub2 is what I'm already trying to install right?

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Sorry for my silly question, but... Grub2 is what I'm already trying to install right?

Yes my instructions will install GRUB2.

---

### Post by presence1960 on 2009-12-12
> **earthpigg said:**
> thank god for you grub gurus :D

Thank the community for their documentation. drs305 for the tutorial also. And meierfra for sharing some links & info he came across. That's why this community is as strong as it is!

---

### Post by Dan Turton on 2009-12-12
Here's the output:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
```

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Here's the output:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
```

did you reboot and see what happens?

---

### Post by Dan Turton on 2009-12-12
Not just then (I did last night).

Thanks for staying with me!

I'll do a fresh install now and follow your instructions from above again... and then post the results

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Not just then (I did last night).

Thanks for staying with me!

I'll do a fresh install now and follow your instructions from above again... and then post the results

?????????????? reboot from the live cd and see if you can boot into ubuntu

---

### Post by Dan Turton on 2009-12-12
Sorry for the misunderstanding and my general noobness.

I am currently in ubuntu (by booting from the live CD)... how do I now see if I can boot into ubuntu?

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Sorry for the misunderstanding and my general noobness.

I am currently in ubuntu (by booting from the live CD)... how do I now see if I can boot into ubuntu?

click the shutdown button- should be upper right on top panel and choose Restart. It should prompt you to remove CD then hit enter. machine will then reboot.

---

### Post by Dan Turton on 2009-12-12
Done that... that led to the "no such device" error... which flashes up.

Now I'm at a screen with four options: Ubuntu generic, ubuntu generic recovery mode and 2 memory tests.

The two ubuntu options both lead to the same "no such device error"

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Done that... that led to the "no such device" error... which flashes up.

Now I'm at a screen with four options: Ubuntu generic, ubuntu generic recovery mode and 2 memory tests.

The two ubuntu options both lead to the same "no such device error"

I don't know why, but there must be a reason! Everything looked good in your script output. maybe a fresh install is in order, unless someone else has an idea.

---

### Post by Dan Turton on 2009-12-12
Thanks so much for your help! A friend suggested trying an older version of Ubuntu in case that is more compatible with my old laptop... maybe I'll try that

---

### Post by presence1960 on 2009-12-12
> **Dan Turton said:**
> Thanks so much for your help! A friend suggested trying an older version of Ubuntu in case that is more compatible with my old laptop... maybe I'll try that

I would try 8.04 (Hardy LTS)- very stable and as long as you don't need the newest, bleeding edge apps is a great one. Or 9.04 Jaunty.

---

### Post by jdf022 on 2009-12-13
I'm a semi-experienced Ubuntu user but a first-time poster.  I came across this thread after my own issue with an IBM Thinkpad x31.  I found this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)

Perhaps there is going to be a line that you can delete - as mentioned in these instructions - that will let you run Ubuntu?

I'm in the process on testing their suggestions - compy #2 is booting up...

---

### Post by Dan Turton on 2009-12-13
Please let me know if you have success!

I tried ubuntu 8.04.3 too and had even more problems. I also tried xp install (not repair) and that didn't work either. There must be some funny things about the thinkpads

---

