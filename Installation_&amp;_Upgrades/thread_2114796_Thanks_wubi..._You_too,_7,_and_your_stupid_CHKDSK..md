---
title: "Thanks wubi... You too, 7, and your stupid CHKDSK..."
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by Rowdy Revenant on 2013-02-11
So i installed ubuntu on my old Toshiba Sattelite A215, and everything was going awesome till a week ago. After squeezing Ubuntu into the partition, i used Ubuntu until i needed to use something back on Win7. I boot up 7, and CHKDSK starts going, and when its done, it renders Ubuntu USELESS. I dont actually have my machine in front of me now, but what i did was just reinstall through Wubi.

What i really want to know is, how do I start from scratch on my machine, using only Ubuntu, no Win7???

---

### Post by kurt18947 on 2013-02-11
Start a live install, open gparted (I think it's there by default), delete any partition(s) you no longer want, press go then recreate an  ext* partition for Ubuntu.  Install in the new partition.  That should do it AFAIK.

---

### Post by darkod on 2013-02-11
If you want only ubuntu on the machine it's even easier. Boot with the ubuntu cd and start the install. When asked which method you want to use, select the one that sounds like Replace Windows, or Erase and use whole disk, etc.

That will ERASE all data on the disk and install only ubuntu on the whole disk.

If you want more control of partition sizes or to install with separate /home for example, you will have to use the manual method, Something Else.

---

