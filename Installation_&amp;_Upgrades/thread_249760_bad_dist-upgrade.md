---
title: "bad dist-upgrade"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by tun on 2006-09-03
hello:

I tried doing an apt-get dist-upgrade on my server installtion a little while back (dapper), which went bad.  It gave me an error message, which i stupidly ignored.  The server still boots fine, but now its coming back to bite me in the rear. Here is why:

I have a /boot directory, but it doesn't have /boot/grub!  I don't even know how the computer boots...

How can i fix this?  This is giving me a hard time with backups.  Here is my setup:

/boot (100 MB)
swap 1.5 gigs
/ 245 gigs

Thanks
tun

---

### Post by wangbin on 2006-09-03
what your /etc/fstab looks like?
Is an noauto option added in your /boot partition?

---

### Post by tun on 2006-09-03
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


it doesn't look like it...

---

