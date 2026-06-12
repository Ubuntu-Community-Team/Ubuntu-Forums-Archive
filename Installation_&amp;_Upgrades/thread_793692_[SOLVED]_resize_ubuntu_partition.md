---
title: "[SOLVED] resize ubuntu partition"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by 0range0rca on 2008-05-14
Hi all,

I am using ubuntu 7.10 on a 16gb partition. I am unable to expand it to 26gb using the free 10gb unallocated space before it. gparted does not show the resize option. qparted does not even detect the hard disk.any other way of doing it ?

thanks

---

### Post by forestpixie on 2008-05-14
You need to use the gparted on the livecd or get gparted and burn it as an iso so boot with it. You can't work on a mounted partition.

---

### Post by 0range0rca on 2008-05-14
gparted does not show resize option when run from the ubuntu live cd. 
Ill try the iso option. I have an older version of gparted on cd, will try that.

---

### Post by forestpixie on 2008-05-14
Yea - I had some problems with gparted tbh - I use partedmagic now

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Might also be extended partition - which you have to work with slightly differently from memory

---

### Post by housam on 2008-05-14
> **0range0rca said:**
> gparted does not show resize option when run from the ubuntu live cd. 
Ill try the iso option. I have an older version of gparted on cd, will try that.

Use the Gparted live CD as forestpixie advised you. but use the newer version which will allow you to resize from the front end of ubuntu partition.

---

### Post by Pumalite on 2008-05-14
Try 0.3.7-2:
[http://sourceforge.net/project/showfiles.php?group_id=115843](http://sourceforge.net/project/showfiles.php?group_id=115843)

---

### Post by 0range0rca on 2008-05-14
Thanks everyone, using the latest version of gparted iso (cd rom) worked well.

---

### Post by Pumalite on 2008-05-14
Good luck.

---

