---
title: "How do I disable LVM?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by wonko on 2006-06-04
I'm not sure this is the right forum for this question, but it was the one I felt was closest related...
I'm using an old laptop with a 20GB hd and have absolutely no use for LVM. But when I installed (Dapper, Xubuntu) I let the wizard do the formatting and partitioning. Now my boot-up is pretty slow, and I'd like to disable some services by following the howto: 
[[howto] Speed up ubuntu boot process - the way you can feel it. - updated]("http://ubuntuforums.org/showthread.php?t=89491")
One of the processes I'd like to get rid of is lvm, but I'm not sure if it's used by the system. 
Anybody know how to find out?
And if it's being used, does anyone know how to "unistall" it, or something, so I can disable this process?

---

### Post by ubuntu_demon on 2006-06-04
People who use lvm will know that they are using it so you are not using it and you can use the guide you refer to to disable lvm from starting up

$sudo sysv-rc-conf

Find the line which starts with "lvm" and remove all "x"-characters.

---

### Post by wonko on 2006-06-04
Thanks!
Disabled it, and everything seems working fine!

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=wonko]Thanks!
Disabled it, and everything seems working fine![/QUOTE]
great!

---

