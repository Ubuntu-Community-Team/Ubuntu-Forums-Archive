---
title: "Having problems installing ubuntu on hardware raid-1"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Mad Professor on 2011-05-25
Good Day All. 

Linux newbe here looking for help and advice.

I have tried installing both 10.04 and 11.04 64bit server on my old server without any luck. 

I get as far as setting up the partitions, and I then get the following Warning.

> 
parted was unable to re-read the partition table on /dev/mapper/sil_bhafdhcafccb (no such
file or directory).   This means Linux won't know anything about the modifications you made.


As said this happends on both 10.04 and 11.04 64bit server.

Can anyone please advice a newbe on where to start to get this problem sorted. 
 
Thanks for your time. 
 
Best Regards.

---

### Post by Mad Professor on 2011-05-25
I have just tried again with 11.04, but this time I unmade the raid, and removed the 2nd drive so I was left with only one drive. 
 
This time it installed and boots fine. 
 
So the problem has to be related to my hardware raid.

The motherboard is a [Tyan Thunder K8SD Pro (S2882-D)]("http://www.tyan.com/product_board_detail.aspx?pid=127") <Click for link.

Can this problem be sorted, or do I have to buy a hardware raid card? 
 
Thanks for your time. 
 
Best Regards.

---

### Post by Mad Professor on 2011-05-26
So looking on the forums, and google, it seems that you do not class this as a true hardware raid, but class it as FakeRAID. 

The Tyan Thunder K8SD Pro (S2882-D) motherboard has the latest bios (v3.09), This also includes the Sil3114 rom v5.0.64.

I have just looked on Silicon Image's web site, and see that the latest rom version is v5.0.73.

Can anyone tell me if it is possible to upgrade the Sil3114 rom to the lastest version, or will I have to see about getting a custom bios rom made with the updated Sil3114 rom.

Thanks for your time. 
 
Best Regards.

---

### Post by Mad Professor on 2011-05-27
I have just flash my motherboard with a custom bios with the Sil3114 rom v5.0.73, from [bios-mods.com]("http://www.bios-mods.com/forum/Thread-Tyan-Thunder-K8SD-Pro-S2882-D")

I am still getting the same problem when trying to install ubuntu with Raid-1.

---

