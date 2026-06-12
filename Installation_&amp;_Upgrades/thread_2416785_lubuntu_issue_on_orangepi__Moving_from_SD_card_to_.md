---
title: "lubuntu issue on orangepi : Moving from SD card to SDD, problem with size of /"
date: 2019-04-15
forum: Installation &amp; Upgrades
---

### Post by sundeepgoel on 2019-04-15
[TABLE="width: 1661"]
[TR]
[TD="class: t_f"][CENTER][COLOR=#999999]Edited by sundeepgoel at 2019-4-12 16:49[/COLOR][/CENTER]
Hi,

On my orangepipc install, I have moved from SD card to SSD following [https://elinux.org/Transfer_system_disk_from_SD_card_to_hard_disk](https://elinux.org/Transfer_system_disk_from_SD_card_to_hard_disk) and now have **/ **pointing to** /dev/sda1**, however, the filesystem size is not increasing **even after running [COLOR=#222222][FONT=Arial]resize2fs[/FONT][/COLOR]**

[COLOR=#222222][FONT=Arial][SIZE=2]**output of mount**[/SIZE]
[/FONT][/COLOR]/dev/sda1 on / type ext4 (rw)
[COLOR=#ff0000]/dev/sda1 on / type ext4 (rw) <- / mounted to SSD i.e. sda1[/COLOR]
none on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
devtmpfs on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/sda1 on /dev/root type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/108/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lightdm)


**output of parted - l**
Model: External USB3.0 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
[COLOR=#ff0000]1      1049kB  32.2GB  32.2GB  primary  ext4  <- size of sda1[/COLOR]
2      32.2GB  120GB   87.8GB  primary


Model: SD SL16G (sd/mmc)
Disk /dev/mmcblk0: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      21.0MB  64.0MB  43.0MB  primary  fat16
2      64.0MB  3670MB  3606MB  primary  ext4


**output of df -h**
Filesystem      Size  Used Avail Use% Mounted on
[COLOR=#ff0000]/dev/root       3.4G  3.3G     0 100% /   <- core issue, i.e. size of / or /dev/root due to which getting disk full error[/COLOR]
devtmpfs        374M  4.0K  374M   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            101M  656K  100M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            502M     0  502M   0% /run/shm
none            100M  4.0K  100M   1% /run/user
overflow        1.0M  4.0K 1020K   1% /tmp
/dev/sda1        30G  3.0G   26G  11% /dev/root

please advise on how to resize /dev/root mapped to /?

note : have posted this on the orangepi forum at : [http://www.orangepi.org/orangepibbsen/forum.php?mod=viewthread&tid=4263&extra=page%3D1](http://www.orangepi.org/orangepibbsen/forum.php?mod=viewthread&tid=4263&extra=page%3D1), however, due to no reply there am posting to this forum.[/TD]
[/TR]
[/TABLE]

---

### Post by ubfan1 on 2019-04-15
If your sda2 is empty, delete it, expand the sda1 to fill the space, then run resizefs (if the partition tool you use does not do it automatically for you).

---

### Post by sundeepgoel on 2019-04-16
sda1 is already 32.2 GB, and resizefs had not effect there. but i will try as suggested and post back results.

---

### Post by sundeepgoel on 2019-04-16
**Did as advised. sda1 is now 120GB**

  Model: External USB3.0 (scsi)
  Disk /dev/sda: 120GB
  Sector size (logical/physical): 512B/512B
  Partition Table: msdos


  Number  Start   End    Size   Type     File system  Flags
  1      1049kB  120GB  120GB  primary  ext4


However, df -h still shows old problem
  root@orangepi:/home/orangepi# df -h
  Filesystem      Size  Used Avail Use% Mounted on
  [COLOR=#ff0000]/dev/root       3.4G  3.3G     0 100% /  <-- Issue[/COLOR]
  devtmpfs        374M  4.0K  374M   1% /dev
  none            4.0K     0  4.0K   0% /sys/fs/cgroup
  none            101M  652K  100M   1% /run
  none            5.0M     0  5.0M   0% /run/lock
  none            502M     0  502M   0% /run/shm
  none            100M  4.0K  100M   1% /run/user
  overflow        1.0M  4.0K 1020K   1% /tmp
  [COLOR=#ff0000]/dev/sda1       111G  3.0G  103G   3% /dev/root  <-- Shows correct[/COLOR]

---

### Post by sundeepgoel on 2019-04-16
Did some further research, getting some clues :-

**cat /proc/cmdline**, give :-
earlyprintk=ttyS0,115200 loglevel=8 console=ttyS0,115200 console=tty0 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait

which means that root is still pointing to /dev/mmcblk0p2, and not /dev/sda1

the line root = /dev/sd1 in** /boot/cmdline.txt does not seem to be having desived effect**... 

**dmesg **output has "Ignoring tag cmdline (using the default kernel command line)"

Any suggestions ?

---

### Post by ubfan1 on 2019-04-16
Your /proc/cmdline does not show a BOOT_IMAGE=...,Check which kernel grub is booting, if it's on the mmcblk, then a mount of sda1 is done over /, that might explain what's happening. Try running update-grub to see if that points the grub kernel to the one on sda1.

---

### Post by sundeepgoel on 2019-04-18
>  Check which kernel grub is booting

How do i check this, sorry for the newbie question .

---

### Post by ubfan1 on 2019-04-18
In the file /boot/grub/grub.cfg, the first boot entry follows the line starting with "menuentry 'Ubuntu'...".   In that menuentry, look for the line "root = ..."  and see if it refers to the hard disk hd0 or the mmcblk0 Maybe just post that whole menuentry section here.  The running kernel may be found with the terminal command "uname -a"   , and the mounted devices with the command "df"  Output of those commands is of interest too.

---

