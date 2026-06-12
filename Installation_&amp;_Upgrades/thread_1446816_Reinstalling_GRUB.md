---
title: "Reinstalling GRUB"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by OhDearAudrey on 2010-04-04
I upgraded my windows installation to windows 7, afterwards i went to repair / reinstall my GRUB and none of the tutorials involving the live cd has worked. Can anyone help me or walk me through reinstalling, i just want my ubuntu back :(

---

### Post by earthpigg on 2010-04-04
can you specify which tutorials you looked at, what version of ubuntu, and what specifically didn't work?

we need more details.

error messages would be great.

---

### Post by OhDearAudrey on 2010-04-04
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

This was the tut i used, steps and results in order:

1.Mounted, 634 GB filesystem, 

2. After typing mount | tail -1, this is what pops up : /dev/sdb1 on /media/af8fa248-038f-491a-93b5-876f9d0272f4 type ext4 (rw,nosuid,nodev,uhelper=devkit)

3.  After typing ls /media/af8fa248-038f-491a-93b5-876f9d0272f4 this is what comes up: 

bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old

4. After typing  sudo grub-install --root-directory=/media/af8fa248-038f-491a-93b5-876f9d0272f4 /dev/sda

this is what comes up, 
Installation finished. No error reported.
This is the contents of the device map /media/af8fa248-038f-491a-93b5-876f9d0272f4/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

Will edit after restarting...

---

### Post by OhDearAudrey on 2010-04-04
Hmm, worked that time, ebfore it was giving me an error, oh well, now i don't have windows 7 in the grub menu only the old XP install.

---

### Post by oldfred on 2010-04-04
IF you have two windows installs, the boot of both is thru the first install with the boot flag. Windows boot loader only can boot to that first primary boot partition and the second install moves essential files into that partition to allow the second to boot:

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

