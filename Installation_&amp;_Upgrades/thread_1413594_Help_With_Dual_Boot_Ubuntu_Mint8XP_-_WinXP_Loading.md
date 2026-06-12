---
title: "Help With Dual Boot Ubuntu Mint8/XP - WinXP Loading as a read only"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by JC-TC on 2010-02-22
I need some help.  First off let me say I am a newbie, however I am LOVING UBUBTU Mint!  

WinXP Partition loading as a read only and can't fix it with PYSDM (storage device manager)

 Let me provide some history as to how everything was installed: 

From my old WIN XP hard drive I used clonezilla to clone the drive to a partition on my new hard drive for Linux. Windows is on SDA4 which is the last partition of the drive, it is mounted at sda4/windows using ntfs. I then loaded Mint 8 gnome on the 2nd partition sda2 using ext3 mounted at /, sda1 is my Linux swap, and sda3 is mounted at /home using ext3. While installing I selected to mount Linux ext3 at / 

When I choose to load winXP from the grub boot loader I get dev/sda4 no such device 10CDR36778638F73. Also when I try to unmount from disk utility I get the following error: Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=10CDF36778638F73 from /windows Seemslike I need to rename the drive but it won't let me in disk utility. 

My Problem is that within PYSDM (storage device manager) I uncheck Mount file system (sda4/windows) as a read only but it will not stay unchecked. I have unchecked it hit unmount and mount and it still is checked to mount as a read only. This is the code in options for sda4 in PYSDM (storage device manager) nls=utf8,umask=007,gid=46 

I know you guys can fix this easily but I don't know what else to do, please help me. I need some guidance on this and someone to be there while I am doing this if at all possible. Thank you very much in advance, Janice

---

### Post by oldfred on 2010-02-22
While PySDM makes it easy to add an enry into fstab, you still need to understand fstab and mounting:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Did you chown the mount point, it needs to be unmounted to change?
sudo chown yourusername:yourgroupname /mnt/new_directory/

# modify fstab to mount directory
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a

These are my entries:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768                      /media/cdrive      ntfs-3g      defaults,locale=en_US.UTF-8,fmask=0111,dmask=0000         0  0

---

