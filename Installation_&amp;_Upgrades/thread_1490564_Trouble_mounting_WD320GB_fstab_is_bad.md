---
title: "Trouble mounting WD320GB fstab is bad"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by oohbuntoo on 2010-05-22
I recently tried to mount a Western Digital 320GB HD in Disk Utility and received this error message:

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 15 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Line 15 reads:
/dev/sdb1    /media/Lucid 10.04  vfat    defaults    0  0  

This "/Lucid 10.04" folder does not exist in my /media folder.  Is there a way to edit the fstab file to get rid of Line 15?

---

### Post by dino99 on 2010-05-22
force a fsck on next boot: sudo shutdown -F -r now

if this hdd have physical formatting issue, install partedmagic on a cd or usb stick, then boot with it and check the disk  ( [http://partedmagic.com/](http://partedmagic.com/))

make a basic fstab, then install mountmanager to set your prefs with devices and partitions (system admin mountmanager)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oohbuntoo on 2010-05-22
> **dino99 said:**
> force a fsck on next boot: sudo shutdown -F -r now

if this hdd have physical formatting issue, install partedmagic on a cd or usb stick, then boot with it and check the disk  ( [http://partedmagic.com/](http://partedmagic.com/))

make a basic fstab, then install mountmanager to set your prefs with devices and partitions (system admin mountmanager)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

Thanks!!!

---

