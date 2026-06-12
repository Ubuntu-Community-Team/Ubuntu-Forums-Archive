---
title: "need help on configuring ubuntu installation"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by squiddy on 2008-08-18
hi guys.. Newbie here..

screenshot for better understanding :
```
http://img515.imageshack.us/my.php?image=screenshotmr5.png
```

as it seen, i have 3 partition; '/', '/home', and swap partition.
can someone give some steps on how to re-installing ubuntu without touching the '/home' partition? so, the new ubuntu installation will only happen on '/' partition.

Thx

---

### Post by Qtips on 2008-08-18
Hi,

Click on the partition /home and then delete (the trash-bin icon).
Click on the partition / and then delete.
Click on apply to accept the changes.
Click on the free space you just make and create a new partition with the New icon.
Make sure you have the ext3 filesystems and the / mount point for this partition.
When done, click apply to accept the change and your done !

---

### Post by sam1948 on 2008-08-18
> **Qtips said:**
> Hi,

Click on the partition /home and then delete (the trash-bin icon).
Click on the partition / and then delete.
Click on apply to accept the changes.
Click on the free space you just make and create a new partition with the New icon.
Make sure you have the ext3 filesystems and the / mount point for this partition.
When done, click apply to accept the change and your done !

HI
I'm not sure what r u'r intentions but the friend here wants to keep his /home directory don't tell him to delete !!!

hope it's not too late

---

### Post by Qtips on 2008-08-18
Whoooo, a read too fast...SORRY !!!!
I hope you don't do it :( ! Tell me that you don't do this !
I've read that you just want the / and swap partitions...and not the /home...very sorry about that.

---

### Post by squiddy on 2008-08-18
:) nah it's not too late mate :)

so, any idea ? i want to keep my data on /home partiton.

---

### Post by squiddy on 2008-08-18
> **sam1948 said:**
> HI
I'm not sure what r u'r intentions but the friend here wants to keep his /home directory don't tell him to delete !!!

hope it's not too late

thanks for your attention :)

---

### Post by sam1948 on 2008-08-20
fine so it's all good now(:
u'r "/home" dir is in a completely different partition then the "/" dir
so just install a fresh installation in the current "/" partition
make sure that u choose the right one (the 10Gb partition)   
as a "/" mount point it should be flaged with format check-box during the installation.
_option 1_:
after u done installation, look in these forums for "how to fstab"
and in the /etc/fstab file add the line that will mount the 60Gb partition as "/home"

_option 2_: during the installation when choosing partitions for u'r os
u can choose the mount point for each partition make the 60Gb mounted as "/home", I would recommend this as it is the simple one
ATTANTION make sure that this partition is NOT flaged for format !!!

bests

---

### Post by squiddy on 2008-08-20
thanks for the help :)

i've done it with option no.2. and all went fine for me.

---

