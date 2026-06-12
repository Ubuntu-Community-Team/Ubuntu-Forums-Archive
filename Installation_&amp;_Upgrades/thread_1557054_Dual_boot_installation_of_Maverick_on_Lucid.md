---
title: "Dual boot installation of Maverick on Lucid"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by sharathcshekhar on 2010-08-20
Hi All,
I am currently using Ubuntu 10.04. I wanted to test Ubuntu 10.10 and installed Maverick Alpha-3 on a separate partition. Now grub shows up both Ubuntus at the start up. I will continue to use Lucid for my work and test out Maverick only once in a while. 
So I was just wondering if my Grub shipped with Maverick was reinstalled on my MBR when I installed it?
**I don't want to take any risks with using a unstable Grub on my system. Should I reinstall the Stable Grub packed with Lucid? **
This is the version of Grub shown when I log into my Lucid.
```

$ grub-bin2h --version

grub-bin2h (GRUB) 1.98-1ubuntu7

```

If I have to reinstall, please suggest me how I should do it. 
My root partition of Lucid is installed in /dev/sda1, /home being at /dev/sda5, and whole of Maverick in installed in /dev/sda9

Any help is appreciated. Thanks in Advance.

Sharath C

---

### Post by dagdeniz on 2010-08-20
No, you don't have to. Both Lucid and Maverick use version 1.98 (you can compare from Ubuntu page in Distrowatch). 
If you still want to try, you can run 
```
sudo grub-install /dev/sda
sudo update-grub
```when you're in Lucid.

---

### Post by sharathcshekhar on 2010-08-21
Thanks dagdeniz.
I reinstalled Grub from Lucid. Thanks. 
Before reinstalling Grub as you suggested, I was getting Grub-1.98-2010xxx on the Grub Menu, and after I reinstalled I am getting Grub-1.98-ubuntu7. Anyway I appreciate your help. Thanks.

---

### Post by decent2110 on 2010-08-21
cool stuff dagdaniz........its doing awesome......thnx in advance...
 
 
now its time to run....
 
good luck
 
 [B][FONT=Arial][SIZE=2][URL="http://www.relaxhouse.com.au"]
[/URL][/SIZE][/FONT][/B]

---

