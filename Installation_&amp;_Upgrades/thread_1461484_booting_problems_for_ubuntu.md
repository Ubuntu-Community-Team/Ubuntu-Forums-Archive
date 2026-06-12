---
title: "booting problems for ubuntu"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by rajesh.kanakabandi on 2010-04-24
hey all,
      i used to have a windows xp and ubuntu installed in separate partitions on my desktop computer.i fell into really big problems after i formatted the windows partion.now my system has no single file related to windows,still it says "ntldr missing press alt+ctrl+del" im using the live cd version of ubuntu 9.04.is there a way to set up my ubuntu? i dont need windows any more.

thanks in advance.

---

### Post by ronnielsen1 on 2010-04-24
Did you give the space you formatted to Ubuntu? It sounds like you need to reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rajesh.kanakabandi on 2010-04-24
> **ronnielsen1 said:**
> Did you give the space you formatted to Ubuntu? It sounds like you need to reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i eaven tried to re install the grub, i used the following commands

sudo grub
>root (hd0,0)
>setup (hd0)
Error 17: cannot mount selected partition.

---

### Post by joeoshawa on 2010-04-24
> **rajesh.kanakabandi said:**
> i eaven tried to re install the grub, i used the following commands

sudo grub
>root (hd0,0)
>setup (hd0)
Error 17: cannot mount selected partition.
I know probably half what these guys do but it sounds to me like if you use the install cd to repartition the hdd purely for linux and install it you should be fine you do not need windows anymore right, so i would just repartition and install right of the cd.

---

### Post by rajesh.kanakabandi on 2010-04-24
> **joeoshawa said:**
> I know probably half what these guys do but it sounds to me like if you use the install cd to repartition the hdd purely for linux and install it you should be fine you do not need windows anymore right, so i would just repartition and install right of the cd.

yes, i've decided not to use windows any more. and started to install ubuntu again from the cd. but i want to partition my disk into
1.root directory for the os
2.swap area
3.ext3
4.ext3
5.ext3

what mount points am i supposed to specify for the last 3 partitions?

i used to get these disks mounted in 
/media/disk1
/media/disk2
/media/disk3

do i have to mention it that way?

---

