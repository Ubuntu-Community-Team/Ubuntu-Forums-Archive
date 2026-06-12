---
title: "Can not format USB stick in FAT32"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by davidavida on 2013-06-12
Hi everyone.
I am trying to make a Ubuntu boot disk on a USB stick to install in another pc.
I can not format it in FAT32.

(1) First I used the start up application
(2) Selected the iso and sdc1 where the usb is
(3) Asked to erase the disk as it said it was full, and it was not but anyway I chose the option (the disk was already formated in FAT32 by default anyway)
(4) It did not make it, it says: "org.freedesktop.UDisks.Error.Inhibited: Daemon is inhibited"
(4) There is this other error to:"org.freedesktop.UDisks.Error.FilesystemToolsMissing: Error creating file system: Cannot run mkfs: cannot spawn 'mkfs.vfat -I /dev/sdc1': Failed to execute child process "mkfs.vfat" (No such file or directory)"

Now if I open gParted to format the disk the option FAT332 is not available.
The usb stick is unmounted when I do this process. In fact it does not mount anymore.

####################################
I am using Ubuntu 12.04
Usb mounted on /dev/scd1
####################################

Any ideas

Thanks in advance.

---

### Post by ubfan1 on 2013-06-12
Try installing the dosfstools package to get mkfs.vfat
sudo apt-get install dosfstools
Then the format should work.

---

### Post by davidavida on 2013-06-13
Yeah it worked.
Thanks a lot.
Sorry about the double post, my bad.

---

