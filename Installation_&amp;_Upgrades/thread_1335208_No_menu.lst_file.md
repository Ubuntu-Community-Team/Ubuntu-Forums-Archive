---
title: "No menu.lst file"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by irfannp on 2009-11-23
hi 

[SIZE=2]I am using Ubuntu 9.10 and now everything is fine.While searching some stuff on grub , every where i found edit the "*/boot/grub/menu.lst*" ..but i can't see such a file in my system but everything is working fine.I want to know why this happens. I found a file grub.cfg in that folder which looks like a shell script BUT it is written in the first line that don't edit the file. So where is my grub file?

I am using dual boot with windows 7 in Dell inspiron 1525 laptop.[/SIZE]

---

### Post by phillw on 2009-11-23
> **irfannp said:**
> hi 

[SIZE=2]I am using Ubuntu 9.10 and now everything is fine.While searching some stuff on grub , every where i found edit the "*/boot/grub/menu.lst*" ..but i can't see such a file in my system but everything is working fine.I want to know why this happens. I found a file grub.cfg in that folder which looks like a shell script BUT it is written in the first line that don't edit the file. So where is my grub file?

I am using dual boot with windows 7 in Dell inspiron 1525 laptop.[/SIZE]

Grub.lst has gracefully retired :D

Grub has a whole new incarnation - To learn more about it, here's a quick list of good places.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

As you will guess, drs' *IS* Grub2 for all of us lesser mortals and has put a lot of time and effort into those how-to's and on-going support. He's a really nice guy, as well.

Regards,

Phill.

---

### Post by sisco311 on 2009-11-23
never mind

---

### Post by irfannp on 2009-11-23
Thanx for such a quick reply 

Actually my intention was to get the file to edit the grub.Because today i done kernel upgrade 2.6 .28 to 2.6.31 now during the start up grub lists my old version also .I want to remove that .what should i do?

---

### Post by JustinR on 2009-11-23
I'm having the same problem irfannp!

---

### Post by snowpine on 2009-11-23
> **irfannp said:**
> Thanx for such a quick reply 

Actually my intention was to get the file to edit the grub.Because today i done kernel upgrade 2.6 .28 to 2.6.31 now during the start up grub lists my old version also .I want to remove that .what should i do?

This is not a "problem"; it is always a good idea to keep an older kernel as a spare while you are testing the new kernel. I recommend always keeping at least two kernels. The extra kernel will not harm your system in any way (except using a small amount of hard drive space).

If you decide to remove the old kernel, you may do so through the Synaptic Package Manager.

---

### Post by phillw on 2009-11-23
If you select totally remove via synaptic of your old kernel (as mentioned - allways keep at least one spare) the use section 7 of the how-to  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Regards,

Phill.

---

### Post by presence1960 on 2009-11-23
> **irfannp said:**
> Thanx for such a quick reply 

Actually my intention was to get the file to edit the grub.Because today i done kernel upgrade 2.6 .28 to 2.6.31 now during the start up grub lists my old version also .I want to remove that .what should i do?

kernel 2.6.28 is a Jaunty 9.04 kernel

kernel 2.6.31 is a Karmic 9.10 kernel

I would remove the 2.6.28 kernel and then use update manager to update your system. There is already a kernel update for Karmic, which would leave you with 2 Karmic kernels.

Use Synaptic to remove the 9.04 kernel - mark for complete removal linux-image-2.6.28.x-generic and linux-headers-2.6.28.x-generic

---

