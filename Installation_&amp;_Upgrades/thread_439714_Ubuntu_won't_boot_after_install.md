---
title: "Ubuntu won't boot after install"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Broken9754 on 2007-05-10
I'm trying to do a dual boot with Windows XP and Ubuntu. I installed Ubuntu onto a partition on my D: drive, windows is on C:. When I restart my computer, I don't get the grub menu, it just boots straight to windows xp. Any thoughts?

---

### Post by confused57 on 2007-05-10
If you have 2 hard drives, try setting bios to boot to the Ubuntu drive first, but if you only have one hard drive, boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Broken9754 on 2007-05-10
> **confused57 said:**
> If you have 2 hard drives, try setting bios to boot to the Ubuntu drive first, but if you only have one hard drive, boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

I tried the bios settings the last time I tried this (about a week ago) and I got an error that I can't remember but that ended my efforts to install. I tried it this time and it worked like a charm. *shrug* Thanks! Hope that wasn't too easy for you.

---

### Post by confused57 on 2007-05-11
> **Broken9754 said:**
> I tried the bios settings the last time I tried this (about a week ago) and I got an error that I can't remember but that ended my efforts to install. I tried it this time and it worked like a charm. *shrug* Thanks! Hope that wasn't too easy for you.

Glad it worked...I like easy.  Enjoy your Ubuntu.

---

