---
title: "32 bit vs 64 bit"
date: 2018-03-13
forum: Installation &amp; Upgrades
---

### Post by jebattheminister on 2018-03-13
Hi, Im still new in Linux environment and about to get an opinion from other experts here. After a spoil knowledge of mine, Im running a -
$ uname -a
my output is =
4.13.0-36-generic #40~16.04.1-Ubuntu SMP Fri Feb 16 23:26:51 UTC 2018 i686 i686 i686 GNU/Linux

which telling Im running a 32 bit OS on a 64 bit machine. my question is there any complication in future for this mistakes?
Im in plan to run Liquorix or Xanmod kernel with my old machine capable to run Nvidia Optimus gforce gt 620M and 6004512 kB of RAM (grep MemTotal /proc/meminfo)

Thanks for the valuable opinion.

---

### Post by Tadaen_Sylvermane on 2018-03-13
If your machine can run 64, best to use it. 32 bit wont stick around forever.

---

### Post by papibe on 2018-03-13
Hi jebattheminister. Welcome to the forum ):P

Some thoughts:

6004512 kB of RAM is your virtual RAM, not the actual physical RAM. Try this instead:
```
free -m
```

If you have more than 4Gib of RAM, you'd be better off using a 64bit kernel, so you can use your whole RAM (without [PAE]("https://en.wikipedia.org/wiki/Physical_Address_Extension") kernel extensions).

Unless you need some legacy software, I'd recommend  going with 64bit, 

Best Regards.

---

### Post by deadflowr on 2018-03-13
nvidia will soon(-ishly?) be dropping 32-bit support:
[https://www.phoronix.com/scan.php?page=news_item&px=32-bit-NVIDIA-Drop-Dropping]("https://www.phoronix.com/scan.php?page=news_item&px=32-bit-NVIDIA-Drop-Dropping")
for what it's worth.

---

### Post by mörgæs on 2018-03-14
32 bit binaries for Nvidia will still be available. There just won't be more new functionality added. 

Jebat, I suggest that you keep the 32 bit Ubuntu as it is. When you some day decide that you are switching to 18.04 then you could do a fresh install of the 64 bit version. Plenty of time.

---

