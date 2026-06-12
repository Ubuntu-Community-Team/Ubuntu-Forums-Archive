---
title: "Windows System Reserved Partion mounting in ubuntu 12.04"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by vicky3p on 2012-05-22
Guys I've installed windows 7 with ubuntu 12.04 lts and both are  working good.... the only issue i have is that whenever i boot into  ubuntu...at booting it says...
  The disk drive for /windows is not ready yet or not present. continue to wait ,or press S to skip mounting or M for manual recovery.
  After pressing S it boots n works great....but it shows the windows system reserved partion and if i click on it....it mounts...
  what i want to do is get rid to that annoying message and hide my windows system reserved partion...
  I know it has to do something with fstab but i'm new to ubuntu so don't want to go messing about things..
  THANKS for your help in advance This is my fstab...




# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=8e5b0c69-2c42-4e11-9991-73da7a7aae3c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=f074d97f-2309-44e7-a397-25a5f7e98e3b /home           ext4    defaults        0       2
# /windows was on /dev/sda6 during installation
UUID=FECA-7D83  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=0ad1446c-5d05-490a-9aea-e6dbf0ac2019 none            swap    sw              0       0

---

### Post by oldfred on 2012-05-22
A # will convert a line to a comment, so lets do that first.

# backup current version
sudo cp /etc/fstab /etc/fstab.backup
# edit fstab
gksu gedit /etc/fstab

Add # to front off the line with the /windows entry and save

> # /windows was on /dev/sda6 during installation
[COLOR=Red]#[/COLOR]UUID=FECA-7D83  /windows        vfat    utf8,umask=007,gid=46 0       1


If Windows 7 it has to be NTFS not fat so that may be part of the problem.

Post this also
# Find your UUID:
sudo blkid -o list

---

### Post by darkod on 2012-05-22
This line in fstab seems to be mounting a FAT32 partition:
UUID=FECA-7D83  /windows        vfat    utf8,umask=007,gid=46 0       1

If you don't want to mount it at boot, simply delete it or put # in front. The # sign makes it non-executable, that way you can still keep it in fstab in case you want to enable it again in future, but temporarily it will not be executed.

---

### Post by Morbius1 on 2012-05-22
> but it shows the windows system reserved partion and if i click on it....it mounts...
  what i want to do is get rid to that annoying message and hide my windows system reserved partion...Excuse the interruption but there are 2 different issues here.

** Something is wrong with the vfat line.

Wrong UUID ?
No /windows directory created?

** The System Reserve partition is showing up in Nautilus as mountable.

Create a line in fstab for that partition and make sure it doesn't mount at boot:
```
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
```Run the following command to get the right UUID number:
```
sudo blkid -c /dev/null
```And create the mountpoint:
```
sudo mkdir /mnt/SysRes
```

---

### Post by vicky3p on 2012-05-22
ok i added # infront of [COLOR=Red]#[/COLOR]UUID=FECA-7D83  /windows        vfat    utf8,umask=007,gid=46 0       1

it got rid of the message at startup but system reserved partion is still there n i want to hide or not to be shown in ubuntu...

---

### Post by vicky3p on 2012-05-22
OK added the line UUID=7C7C735D7C7310DE /mnt/SysRes ntfs defaults,noauto 0 0
and it worked...system reserved is now not shown in ubuntu...Thanks guys..

---

