---
title: "Install on primary partition possible or not"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by even.raghu on 2010-06-17
3 months ago i register here and ask for help because i am new to Linux world. Thanks to member here who give the link to Ubuntu official guide and i read that book. From April i use Ubuntu and widows 7.

I manage to learn 20-30% about Linux with the help of book. Now i think time to use Ubuntu only. And new version also here.

My Question
===========
1.in my 500Gb hdd and i make partition c: (35gb),d: (100gb),e: (300gb)
C: drive contain windows 7. i think i delete this partition and with this free space i install new Ubuntu 10 version there. After install on primary partition should i access my rest of drive in Linux?

2. can i install realtek high definition driver and nvidia geforce 9800 driver on new linux?

---

### Post by howefield on 2010-06-17
> **even.raghu said:**
> After install on primary partition should i access my rest of drive in Linux?

You will be able to access the rest of the drive from Ubuntu. Ubuntu will read NTFS drives.

> can i install realtek high definition driver and nvidia geforce 9800 driver on new linux?

Not sure about the realtek (loading up the Live CD should give you an idea if the sound works) but the 9800 appears to be supported. 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by darkod on 2010-06-17
One thing you didn't specify in your post is how are you using ubuntu right now. From the partitions C:, D: and E: it seems all are ntfs. That would mean you have only installed wubi inside windows.

In that case, you can't remove windows because wubi is inside.

You could delete the 35GB ntfs partition and create / and swap in that space, either by manual partitioning or let is use Use Largest Available Free space option.

But you need to be aware that wubi install is different from full ubuntu install.

Yes, ubuntu will be able to see all ntfs partition you have.

---

### Post by even.raghu on 2010-06-17
dude i remove ubuntu 2days ago. bcz i want to install fully in c:

Thanks for support. Thanks man..:p

---

