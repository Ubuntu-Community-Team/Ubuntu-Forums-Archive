---
title: "Mapper inconsistant /home partition,is, then is not Mapped!  No Auto mount,"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2007-04-17
Using updated Feisty, Kernel 2.6.20-15.27 I first had this occur on Kernel 2.6.20-15.25, I could not mount my /home partition sda5. I ran
ls /dev/disk/by-uuid/ -alh , with this output:

drwxr-xr-x 2 root root 140 2007-04-14 18:07 .drwxr-xr-x 6 root root 120 2007-04-14 14:04 ..
lrwxrwxrwx 1 root root 17 2007-04-14 18:04 07D4-0C0C -> ../../mapper/sdb1
lrwxrwxrwx 1 root root 10 2007-04-14 18:07 18c79eac-b4e4-4fea-a502-786ce82af86e -> ../../sda5
lrwxrwxrwx 1 root root 17 2007-04-14 18:04 8bd36f06-7967-47e4-9933-669abf52b03f -> ../../mapper/sda6
lrwxrwxrwx 1 root root 17 2007-04-14 18:04 ae513c0e-9646-47f3-8ffe-17c18555b26b -> ../../mapper/sda7
lrwxrwxrwx 1 root root 17 2007-04-14 18:04 CAF012F3F012E58B -> ../../mapper/sdb2

Updated to Kernel 2.6.20-15.27 and my 1st output was this:

drwxr-xr-x 2 root root 140 2007-04-17 23:11 .
drwxr-xr-x 6 root root 120 2007-04-17 19:11 ..
drwxrwxrwx 1 root root 17 2007-04-17 23:11 07D4-0C0C -> ../../mapper/sdb1
lrwxrwxrwx 1 root root 17 2007-04-17 23:11 18c79eac-b4e4-4fea-a502-786ce82af86e -> ../../mapper/sda5
lrwxrwxrwx 1 root root 17 2007-04-17 23:11 8bd36f06-7967-47e4-9933-669abf52b03f -> ../../mapper/sda6
lrwxrwxrwx 1 root root 17 2007-04-17 23:11 ae513c0e-9646-47f3-8ffe-17c18555b26b -> ../../mapper/sda7

I have to manually Mount sda5

AFTER A RE-BOOT sda5 was not mapped, could not mount at all

Re-Boot again sda5 is mapped and I must manually mount.

/etc/fstab

# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda6 :
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
#UUID=07D4-0C0C /media/hdb1 vfat iocharset=utf8,umask=000 0 0
# /dev/hdb2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hdb2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb3 -- converted during upgrade to edgy
#/dev/hdb3 /media/hdb3 vfat iocharset=utf8,umask=000 0 0
#/dev/hda7

All other partitions and drives are mounting except /home sda5

I reported as Bug, any suggestions

Thanks

---

