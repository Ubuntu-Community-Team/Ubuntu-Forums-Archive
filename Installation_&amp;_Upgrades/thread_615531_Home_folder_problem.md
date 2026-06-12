---
title: "Home folder problem"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by Mancman on 2007-11-17
Hi,

I had Edgy set up with a separate 'home' partition, which appeared in Nautilus quite unsurprisingly as 'Home'. However, I seem to have somehow carelessly messed up when installing Gutsy. 
I've rebooted after installation, and now when I go into Nautilus there is an automatically generated new 'Home' folder consisting of folders named 'Examples', 'Music', 'Videos', etc etc....while my *real* Home folder is shown as sda5, further down the tree. 

This is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5c99ff96-29d3-4a13-a206-4249a37b90cf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5C78C46678C4410E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=dc28bfa8-ea5d-45fa-91d7-de0ba02e33c0 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=c1213a76-ac49-43e0-914c-00082d94ad5b /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=46AD-AB3C  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=8817ac66-0bd3-45c5-b814-b65a2a520521 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


I'm sure (hope) there's a simple solution to enable me to have my Home folder showing correctly, I'm hoping a minor tweaking of fstab will put things right. Can anybody give me a nudge in the right direction, please ?

---

### Post by aa.ivanov on 2007-11-17
check what's in /media/sda5 and in /media/sda6 If instalation has not erased your old home partition chances are that one of these will be your old home partition. If so from terminal do 'sudo umount /media/sda#' and edit fstab correcting '/media/sda#' to '/home' then reboot and you'll have your old home.

---

### Post by Mancman on 2007-11-17
Yes, that's fixed it.....thanks very much !!  ):P

---

