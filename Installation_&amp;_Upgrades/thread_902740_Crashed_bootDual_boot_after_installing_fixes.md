---
title: "Crashed boot/Dual boot after installing fixes"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by thusgaard on 2008-08-27
Hi. 

My newly converted (almost) brother in law let Ubuntu update some packages (which are not know at this time) after rebooting his dual boot with XP does not work. That is XP works, but Ubuntu says: 

Booting Debian GNU/Linux, Kernel 2.6.24-19 Generic
Filesystem type is ntfs, Partition type 0x7 kernel
/vmlinuz-2.6.24-19-Generic
Root = UUID = CA84192E84191E8F loop = /Ubuntu/disk
S/Root.Disk ro quiet Splash

Error 15: File not found

Press Any key to Continue 



Does anyone have any idea both he and I are quite new at Linux. 

J;-)

---

### Post by prshah on 2008-08-27
> **thusgaard said:**
>  loop = /Ubuntu/disk
S/Root.Disk ro quiet Splash

Error 15: File not found


Looks like you're running it in Wubi (Not a true dual boot, but anyway...)

Can you check if "c:\ubuntu\disks\root.disk" exists or not? Or have you installed it to some other drive?

---

### Post by thusgaard on 2008-08-28
> **prshah said:**
> Looks like you're running it in Wubi (Not a true dual boot, but anyway...)

Can you check if "c:\ubuntu\disks\root.disk" exists or not? Or have you installed it to some other drive?

Yes he is running Wubi and yes c:\ubuntu\disks\root.disk can be found!

J;-)

---

