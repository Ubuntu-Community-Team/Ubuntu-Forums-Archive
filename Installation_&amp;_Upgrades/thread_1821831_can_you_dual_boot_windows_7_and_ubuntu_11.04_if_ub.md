---
title: "can you dual boot windows 7 and ubuntu 11.04 if ubuntu is already installed?"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by boywithsling on 2011-08-09
I was wondering if there is a way to dual boot windows 7 and Ubuntu 11.04 when Ubuntu is already installed. I have Ubuntu on my computer but need windows for several things. It's probably easy but I don't want to take any chances. Any help will be greatly appreciated.

---

### Post by YesWeCan on 2011-08-09
Sure. On the same disk? It will need some empty space and you will need a free primary partition slot ([http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)). Install it from the Windows CD. Then the issue is booting into Ubuntu.
Boot of Ubuntu CD and reinstall Grub to the MBR: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) section 12.2

Always back up vital files beforehand.

---

### Post by Basher101 on 2011-08-09
I did almost the same thing (rather just having my OSs on small partitions and a BIG shared one for movies,downloads ect.). Make sure to give windows 7 around 30 GB. Trust me, once all your updates are installed, free space will get slim. I got a fresh install of Win 7 home premium with all updates, MS office 2010, Adobe reader, and another 2gb of programs. It takes 26 of 30 GB. 
Wanted to give you a pointer for the size.

---

### Post by KurtCho on 2011-08-09
just to add, the best thing to do is to use gparted to make free space then make a new partition. Then all you need is the win7 setup disk:D

---

### Post by Redblade20XX on 2011-08-09
> **KurtCho said:**
> just to add, the best thing to do is to use gparted to make free space then make a new partition. Then all you need is the win7 setup disk:D

Also a ubuntu live disk to reinstall grub if you want to use it! :KS

- Red

---

### Post by YannBuntu on 2011-08-09
> **KurtCho said:**
> the best thing to do is to use gparted to make free space

No. The safest way to reduce Windows partitions is to use Windows tools.

Gparted is perfect to reduce Linux partitions.

---

### Post by Mark Phelps on 2011-08-11
> **YannBuntu said:**
> No. The safest way to reduce Windows partitions is to use Windows tools.

Gparted is perfect to reduce Linux partitions.

While you're correct in your statements, I guess you missed the part where the OP stated ... > when Ubuntu is already installed

... meaning, they want to shrink the Linux partition(s), not MS Windows.

---

