---
title: "Resizing Windows Disk"
date: 2004-10-29
forum: Installation &amp; Upgrades
---

### Post by marsopia on 2004-10-29
Hi people!!

I want to know if it is safe to resize a Windows disk (C) in this case, using Ubuntus installer, to install Ubuntu on free space.

Thanks

mariano

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=marsopia]Hi people!!

I want to know if it is safe to resize a Windows disk (C) in this case, using Ubuntus installer, to install Ubuntu on free space.

Thanks

mariano[/QUOTE]


Its impossible to do with the Installation CD.  You may install on existing freespace that you have now.  Them mount a small /home directory also.  Afterwards when the install is complete.  There are several programs to resize partitions.  Once you resize them.  Delete the /home mount point you created.  With this existing free space create a much larger /home drive.

Links:  [www.freshmeat.net](www.freshmeat.net)

---

### Post by jdong on 2004-10-30
Ubuntu's installer does not have that feature. SystemRescueCD has qtparted, which is a free Partition Magic clone. It can resize Windows partitions.

[http://sysresccd.org/](http://sysresccd.org/)

---

