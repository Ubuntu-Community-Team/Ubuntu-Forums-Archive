---
title: "Cannot create extended partition from gparted livecd"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by nuxweevil on 2013-07-19
I am using gparted livecd to create the partitions I want for a dual boot. I have a modestly sized NTFS primay  with Windows 7 installed, Now I need to create an extended partition from my logical partitions which will serve Ubuntu 13.04. Unfortunately, while in the new partition window,  the option to select extended partition is grayed out.There is no swap partition mounted.How do I overcome this? What more need I tell you?Thanks.

---

### Post by nuxweevil on 2013-07-19
I have solved my problem. I had two blocks of unallocated space, and one of them was already an extended partition. As soon as I noticed that, I realized that I must only be able to create one extended partition. I resized that partition and created logical partitions from there.

---

