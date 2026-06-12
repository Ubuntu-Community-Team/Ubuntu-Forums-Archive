---
title: "UUID &amp; sdx vs hdx (please make sticky)"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by autocrosser on 2007-04-22
I've seen several threads about non-boot problems during the upgrade from Edgy to Feisty. Halfway thru Feisty's development cycle the kernel was changed to use the SATA load stack instead of the IDE/ATA load stack. This changes the /etc/fstab /dev/hdx listing to /dev/sdx. UUID was fazed in during Edgy development & is the recomended way to refer to drives (more accurate than /dev/whatever).

My /etc/fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc                                      /proc           proc  defaults                           0       0
# /dev/hdb1
UUID=d4c465e8-62a9-47cd-89fc-11035d656290 /               ext3  defaults,errors=remount-ro,noatime 0       1
# /dev/hdb2
UUID=77dc92d4-3448-4bc6-8582-6c04b0face4b /home           ext3  defaults                           0       2
# /dev/hda1
UUID=D4A0829AA082832A                     /media/Windows  ntfs  defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 /mnt/Edgy       ext3  defaults                           0       2
# /dev/hdb5
UUID=18c26e08-7085-4e50-a881-3d6d74b19c04 none            swap  sw                                 0       0
#/dev/hde1
UUID=4b0139b9-6d5e-4a00-bf38-06d1002e3325 /media/Storage  ext3  defaults                           0       2 
#/dev/sda1
UUID=b51b9252-a78c-416f-a734-9651fe2b7a27 /media/USBDrive ext3  defaults                           0       2

To change your /etc/fstab to UUID:
Do a grep UUID of your /dev/whatever-it-is:

<code example>  sudo /sbin/dumpe2fs /dev/sda2 | grep UUID  Will give a result like:

dumpe2fs 1.40-WIP (14-Nov-2006)
Filesystem UUID:          1b31b23b-4db9-42c1-84a8-fd1f21992500

Take the UUID number & include it in the /etc/fstab as my example above.

Take your time & double check everything  BEFORE rebooting....

---

### Post by autocrosser on 2007-04-22
Also a side note: Older CD readers "may" not work with the SATA stack that Feisty is using.

---

### Post by autocrosser on 2007-04-22
Shameless bump to keep the information where people can find it.......

---

