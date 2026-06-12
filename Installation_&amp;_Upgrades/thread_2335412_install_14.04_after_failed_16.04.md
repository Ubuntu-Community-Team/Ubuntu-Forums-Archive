---
title: "install 14.04 after failed 16.04"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2016-08-28
I chose install 14.04 along 16.04 and now I have 2 additional devices in /media
one has all of my old /home with user accounts
the second one appears to be the old OS which has old 14.04 and maybe the failed 16.04.

I like having the user accounts in a separate partition, but how do I set it up so that the user dirs will go to that partition. should I modify the fstab?? what i have now is:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=03c3fa16-5d6c-4f58-919b-462d893334af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=c34776d4-2e36-47fc-bf57-13ca62a53508 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

ls /media/stephen
d643d632-c987-444a-8b49-8c96746cbb9b  e84b7617-152d-4d50-8f84-c1db5b9beced

the first one has the user folders. is it safe to delete the second one and how do I recover the space? I want to use it for user files.

so, should I try to setup a mount for the first device as /home ?? if yes do I refer to it as /media/stephen/d643d632-c987-444a-8b49-8c96746cbb9b in fstab or sth else??

thanks.

---

