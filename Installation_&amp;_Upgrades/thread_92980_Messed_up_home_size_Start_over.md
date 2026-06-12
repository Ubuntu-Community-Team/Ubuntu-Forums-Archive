---
title: "Messed up /home size? Start over?"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by Colorado_Wino on 2005-11-20
I have a successfull install of Kubuntu. I'm very happy. This is the first linux distro that worked out of the box with my intel proset wireless chipset that is in my laptop.

My only problem is that I fat fingured my /home partition!

I made it 15 MB instad of 15GB. Is There an easy way, perhaps using parted to resize /home to 15GB? there is only one partition after /home and that is my /windows fat32 area, which I can blow away. After that is free space.

TIA

---

### Post by aysiu on 2005-11-20
Yes, get a live CD (either Ubuntu's live CD or, better yet, Knoppix) and resize it with QTParted. Make sure the drive you're trying to resize is **not mounted**. This is also why you need a live CD to do it, because when you're using the Ubuntu installation, the /home and / are mounted by definition.

---

### Post by Colorado_Wino on 2005-11-21
I'll give that a try. 

Thanks!

---

