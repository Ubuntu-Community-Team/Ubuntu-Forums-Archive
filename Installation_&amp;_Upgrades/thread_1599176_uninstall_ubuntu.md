---
title: "uninstall ubuntu"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by mappila on 2010-10-17
Dear all,
I  am new to this forum and ubuntu.
I was using windows xp sp3. Then last week I installed ubuntu 10.04 in my system as there was some problem with windows xp. 2 -3 days I played with ubuntu, but I could not solve sevaral things as I was a beginner to this OS.Then I installed windows xp sp3 again and started working. But I have found that now ubuntu is not coming at all even in the starting of the computer and I have found that one of my partion is lost(disappeared). Previously there were C(60 GB), F(15 GB), I(60 GB) and J(15 GB) partition with my data distributions in all. But after this reinstall of xp, the ubuntu is not at all coming at the time of starting of computer and it starts with xp. Also, the space for partition I is reduced to 37 GB and partition J is disappeared totally. My sevaraldata are in I drive and please help to reget my hard disk space.
Along with this, I want to install ubuntu parallel with xp.


I am a beginner to this ubuntu and forums. Please help me

:confused:

---

### Post by ronparent on 2010-10-17
Welcome to the forum. 

Windows does not see a Linux/Ubuntu partition. Also when Windows is installed after Ubuntu you have overwritten your grub boot loader. You would have to reinstall grub to get back into Ubuntu.

In your case, since you want to remove Ubuntu, simply boot to a Ubuntu live cd. Then use System >Administration >GParted from the menu header to delete the Ubuntu partitions (the one with the install and the Swap). This will create unallocated space, Now, from GParted, merely expand a windows partition to fill the now unallocated space. Just be careful - because a hasty action could delete or wipe out something you want. Good luck.

---

### Post by ronnielsen1 on 2010-10-17
> Along with this, I want to install ubuntu parallel with xp.

[This]("https://help.ubuntu.com/community/WindowsDualBoot") might help on setting up a dual boot system

---

