---
title: "[SOLVED] 7.10 Dual - Xubuntu and Ubuntu"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by jennymanda on 2007-10-21
I have had Ubuntu 7.10 release running nicely for a a few weeks (now smack bang up to date via updates).

I want to use Xubuntu's different programs from time to time in an XFCE environment.

In other words, dual boot NOT just changing desktops via session selection.

So I installed 7.10 Xubuntu on a spare partition and kept the common swap partition for both Gnome and XFCE installs to use.

XFCE runs fine, and GRUB allows me to chose Ubuntu or Xubuntu. However, part way through the Ubuntu load, Ubuntu falls over with a "fsck UUID" fatal error 8 (or something along those lines). The UUID displayed appears to be correct for the original UUID in menu'lst, and this is still OK in GRUB.

So - how do I fix this? I don't mind reinstalling both to achieve genuine dual boot. Is it something to do with sharing a Swap partition? Has the Automagix tool overwritten or changed something I simply cannot see? To me, nothing looks wrong. 

I cannot find anything on the search - I don't want one platform and two desktops - I want two platforms.

TIA

---

### Post by jennymanda on 2007-10-21
Attached blkid and menu.lst

The first 3 entries are Xubuntu, the last two are Ubuntu

---

### Post by logos34 on 2007-10-21
Maybe ubuntu is having a problem not with the root partition UUID but that for the spare partiton (now xubuntu)...It might be trying to mount it with the old UUID, which should have changed since xubuntu install (formatting changes the uuid).

Post you ubuntu fstab file.

---

### Post by jennymanda on 2007-10-21
For expediency, where is fstab?

---

### Post by logos34 on 2007-10-21
/etc/fstab

---

### Post by jennymanda on 2007-10-21
OK - got it

---

### Post by jennymanda on 2007-10-21
sdb1 is now Xubuntu - it used to be Mandriva (perhaps this is the issue?)

sdb2 is Ubuntu

sdb3 is shared swap

---

### Post by jennymanda on 2007-10-21
This is fstab from Xubuntu

---

### Post by logos34 on 2007-10-21
try changing the fstab entry for sdb1:  

**gksudo gedit /media/sdb2/etc/fstab**  (substitute your path to ubuntu's fstab if different)

replace 

> # /dev/sdb1
UUID=0fc677c1-d401-497f-8f3c-46373403c9ad /media/sdb1     ext3    defaults        0       2

wth this:

> # /dev/sdb1
UUID=[COLOR="Blue"]0d608a0c-517d-4d99-8841-05ea41963c2a[/COLOR] /media/sdb1 ext3 defaults 0 [COLOR="Blue"]0[/COLOR]

or (omitting UUID altogether):

> /dev/sdb1 /media/sdb1 ext3 defaults 0 0

---

### Post by jennymanda on 2007-10-21
Yep, that did it!

Once I had noticed the previous Mandriva UUID, my thoughts were about changing fstab to reflect the new UUID of Xubuntu.

Not sure what the two fields of "Default" mean - why did I have to change 0 2 to 0 0?

Thanks for that - much appreciated!!

A beer for you....

---

### Post by logos34 on 2007-10-21
The last '0' is fsck option.  I had you change it just to make sure it woudn't cause a problem.  You really don't need it as Xubuntu already does an fsck on it.  But you can change it back if you want.

info on fstab:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

