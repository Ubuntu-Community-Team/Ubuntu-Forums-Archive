---
title: "Heads UP apt-get Upgrade Seg fault"
date: 2009-05-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-05-10
Got the following after an update today, now apt-get upgrade fails with seg fault

> 
May 10 06:25:11 toshsat kernel: [  498.026230] update-manager[4076]: segfault at 1286812d ip b7f8362b sp bfbf6cbc error 4 in libc-2.9.so[b7f0c000+15c000]
May 10 06:25:11 toshsat kernel: [  498.302102] apt-check[5647]: segfault at 17dbb12d ip b7de062b sp bff5549c error 4 in libc-2.9.so[b7d69000+15c000]
May 10 06:25:20 toshsat kernel: [  507.146487] update-manager[5650]: segfault at 1565612d ip b7df762b sp bfa6cbdc error 4 in libc-2.9.so[b7d80000+15c000]
May 10 06:25:24 toshsat kernel: [  511.508346] update-manager[5654]: segfault at 1569412d ip b7e3562b sp bfbaad1c error 4 in libc-2.9.so[b7dbe000+15c000]
May 10 06:25:27 toshsat kernel: [  514.152946] update-manager[5658]: segfault at 156e612d ip b7e8762b sp bfcfae6c error 4 in libc-2.9.so[b7e10000+15c000]
May 10 06:25:54 toshsat kernel: [  541.280292] apt-get[5683]: segfault at 17f4112d ip b7d5362b sp bfc7715c error 4 in libc-2.9.so[b7cdc000+15c000]
May 10 06:25:55 toshsat kernel: [  542.618419] apt-check[5695]: segfault at 17e0a12d ip b7e2f62b sp bfba40ec error 4 in libc-2.9.so[b7db8000+15c000]
May 10 06:26:01 toshsat kernel: [  548.379897] apt-get[5697]: segfault at 17e1912d ip b7c2362b sp bfe46e8c error 4 in libc-2.9.so[b7bac000+15c000]

---

### Post by skierkyles on 2009-05-10
hu, im at all the latest packages, and everything is working fine here.

---

### Post by Peter09 on 2009-05-10
This one came out of the blue - not sure if its going to mean a complete rebuild - perhaps I could just get the faulty .deb and rebuild that.

---

### Post by gnomeuser on 2009-05-10
in my experience it is unfortunately a bit hard to avoid dpkg occasionally getting in a bad state. It is some what fragile.

It works here, for now.

---

### Post by Peter09 on 2009-05-11
Well I am still getting this crash - can any one suggest away to get out of it so that I can continue to upgrade.

---

### Post by paul_in_london on 2009-05-24
Something to try (assuming a reboot hasn't fixed it).

If you have any *.bin files in /var/cache/apt/ delete them.

Then sudo aptitude update && sudo aptitude upgrade should work again. It's done the trick for me anyway.

See [http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/](http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/)

HTH

---

### Post by Peter09 on 2009-05-24
Argggg........ to late ...... did a complete re-install.

---

### Post by paul_in_london on 2009-05-24
Sorry about that! Maybe it'll help if it happens again.

When aptitude segfaults, I sometimes find that apt-get update still works and then I can just run aptitude update again.

rm -vf /var/cache/apt/*.bin definitely helped me out yesterday anyway...

---

### Post by Peter09 on 2009-05-25
I'll remember for next time,
thanks for the tip anyway.

---

### Post by Randall on 2009-05-26
thank you paul_in_london! I just had a fresh install of Hardy 8.04.2 start segfaulting when trying an upgrade. Deleting the .bin files fixed the problem.

---

### Post by dslink on 2009-05-31
really sad how the ubuntu team released this version with such critical 
bugs.  its going to turn alot of people off to linux.  segfaults on jfs, ext3 and ext4 and missing data, back to debian

---

### Post by ghindo on 2009-05-31
> **dslink said:**
> really sad how the ubuntu team released this version with such critical 
bugs.  its going to turn alot of people off to linux.  segfaults on jfs, ext3 and ext4 and missing data, back to debianYou realize that this forum is for the **alpha** release of Ubuntu 9.10, right?

---

### Post by Nullexe on 2009-09-26
Thanks paul_in_london, 

Removing the bin files worked on my 9.04 system.

---

### Post by wuhaa on 2009-10-16
> **Nullexe said:**
> Thanks paul_in_london, 

Removing the bin files worked on my 9.04 system.

Second that... Had the same issue on a 9.04 x86_64 server and removing the *.bin files seems to do the trick.

---

