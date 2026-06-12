---
title: "can't update grub2 configuration."
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Alexander.Luya on 2011-08-03
After installing windows XP,I did some googling to try to get ubuntu back,but seems messed something up.
   Right now,every time to boot system,I have to press "e" on first entry in boot menu,then press "e"s to do these two modifications to startup ubuntu corrently:

1,root (hd0,0)
----------------------------
(hd0,0)  ===>> (hd0,4)
----------------------------
2,kernel /boot/... root=/dev/hd0 ro ..
------------------------------------------
/dev/had0  ===>>  /dev/sda5(this is partition where ubuntu has been installed)

After logged in,I try to do something:
1,
>grub
grub>root (hd0,0)

Here,got error:
-------------------------
Error 21: Selected disk does not exist 
-------------------------

2,then try to modify /boot/grub/grub.cfg:
change all root (hd0,0) to (hd0,4)

(don't know and find where to change:"kernel /boot/... root=/dev/hd0 ro ..")
and restart,thing is being same as before,so how can I get gr
ub2 configured right?

---

### Post by Beacon11 on 2011-08-03
Read [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and you'll learn that /boot/grub/grub.cfg isn't meant to be changed by you. Edit /etc/default/grub and then run sudo update-grub.

---

### Post by Duncan Williams on 2011-08-03
I would recommend that you burn the cd.
It's only a small download and has pulled me out of a few major problems when my grub has stuffed up.

**Supergrub-2** (for grub 1.9 - 2) 

more info:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by Beacon11 on 2011-08-03
> **Duncan Williams said:**
> I would recommend that you burn the cd.
It's only a small download and has pulled me out of a few major problems when my grub has stuffed up.

**Supergrub-2** (for grub 1.9 - 2) 

He can boot fine... why does he need this? There aren't partition or even grub problems, he just needs to update a grub config file.

---

### Post by Duncan Williams on 2011-08-03
do you want say 3 reasons:
1. It does actually repair broken grubs.
2. It lets you do other things and learn a bit more about the grub.
3. If your grub locks up or corrupts in the future you can easily boot into your system to repair it, etc.

and there is a forum in there dedicated to grub issues.


*He can boot fine... why does he need this? There aren't partition or even grub problems, he just needs to update a grub config file.*

op
*`Right now,every time to boot system,I have to press "e" on first entry in boot menu,then press "e"s to do these two modifications to startup ubuntu corrently'*

---

