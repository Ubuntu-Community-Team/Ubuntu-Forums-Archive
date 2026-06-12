---
title: "Windows drives stopped showing"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by ibethebear on 2007-10-30
I'm running v7.10, and everything was fine until I installed Google Earth.  After the install I rebooted and now my windows drives no longer show nor can I get them to show. Fstab is not affected. I have a BU copy of fstab and it's all ok.  

fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sdb1
UUID=e07b02f6-6a15-4ce0-ae5a-a1ed6b17bc4b /  ext3  defaults,errors=remount-ro  0   1
#
# /dev/sdb5
UUID=b629f686-c798-4176-b226-c185d3d80bc8 none  swap  sw   0   0
#
/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto,exec   0   0
/dev/scd1   /media/cdrom1   udf,iso9660 user,noauto,exec   0   0
/dev/fd0    /media/floppy0  auto    rw,user,noauto,exec    0   0
/dev/sda1   /drives/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
/dev/sdc1   /drives/sdc1   ntfs-3g   defaults,locale=en_US.utf8   0   0

Thanks for any help
Ibethebear

---

### Post by ibethebear on 2007-10-30
So, Cool.

I did some more research and found through these forums that I had a bad windows shutdown.  This caused linux to think the ntfs drives were still in use. I did a new reboot to windows, and did a normal shutdown of windows. Now Linux works great and all of my windows drives show fine now in ubuntu.

I hope this helps someone else

Ibethebear

---

