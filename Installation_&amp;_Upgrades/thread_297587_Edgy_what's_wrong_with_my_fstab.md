---
title: "Edgy: what's wrong with my fstab?"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2006-11-11
Hi,
I'm on a fresh installed Kubuntu Edgy (dual boot).
As initially, I couldn't access my Windows partitions, I ave added th respective entries in the /media folder and (as root) added the last two lines to my /etc/fstab. 
I intended to provide user (non root) ro access o these partitions, yet I can't mount (as root) even the first one.

Please advise!

TIA


------------my /etc/fstab-----------
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c12a182f-8413-4b01-8f2c-55d9ecec9029 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=b5c0965f-1523-449e-9109-fae3179cb98c /home           ext3    defaults        0       2
# /dev/sda2
UUID=8f49b6b3-0bdd-4e6e-96d9-de43c5f83b2d none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda3       /media/win_data ro, user                ntfs    defaults        0       0
/dev/sdb4       /media/misc     ext3    defaults        0       0

---

### Post by bulldog on 2006-11-11
Maybe this can help you?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kidders on 2006-11-11
> 
/dev/sda3 /media/win_data ro, user ntfs defaults 0 0
/dev/sdb4 /media/misc ext3 defaults 0 0


It looks as though you have some syntactical errors ...

[LIST]
[*]Remove the space between "ro," and "user"
[*]Switch "ro,user" and "ntfs"
[/LIST]

**Edit:** As one additional minor tweak, may I suggest switching the "user" mount option for /media/win_data to "user**s**". Since you want to allow user-level read only access to this filesystem, using "user" would prevent someone remounting it as himself, *after* someone else had done so.

---

### Post by mibadt on 2006-11-12
Thanks both of you,
Following the link and your advice, I solved the problem.

---

