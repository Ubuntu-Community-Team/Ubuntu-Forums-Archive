---
title: "Ubuntu after formatting xp"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by linuxiano on 2011-09-06
Hello

i installed Ubuntu inside windows xp ,it's on different disk now i want to format xps disk.what will happen to ubuntu? how can i boot to it ?

---

### Post by Neutrosider on 2011-09-06
> i installed Ubuntu inside windows xp
do you mean inside a virtual machine?
if yes: then ubuntu will be deleted
if no: ubuntu will stay, because it can't be installed on the same partition as ubuntu

---

### Post by YannBuntu on 2011-09-06
Hello
if you installed Ubuntu in XP via Wubi, even on a different disk, you will loose access to Ubuntu if you delete XP. See [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

In any case, I recommend you save all your important data on external drive (CD, DVD, USB disk..) before formatting XP.

---

### Post by bcbc on 2011-09-06
> **linuxiano said:**
> Hello

i installed Ubuntu inside windows xp ,it's on different disk now i want to format xps disk.what will happen to ubuntu? how can i boot to it ?

The important part of a Wubi install is the root.disk (possibly other .disk files if you split /home or installed on a FAT32 partition). So as long as it's on another partition or disk, you can safely reformat the XP partition.

BUT... you will lose the ability to boot Ubuntu while XP is down.  And it's not intuitive on how to get a wubi install back booting, even though it's not strictly difficult or a formally documented procedure.

There is another option... if you are reinstalling Windows it's a good time to partition and [Migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi install to its own partition.

Maybe you can explain more about what you intend to do.

---

