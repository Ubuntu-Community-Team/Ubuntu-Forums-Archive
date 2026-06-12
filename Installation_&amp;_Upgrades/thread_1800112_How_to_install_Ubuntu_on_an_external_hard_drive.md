---
title: "How to install Ubuntu on an external hard drive?"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by expunk on 2011-07-08
[FONT="Tahoma"][SIZE="2"]So I just finished installing Ubuntu on my 500 GB HDD. Everything works fine. 
I am able to boot into and use Ubuntu. However, when I booted into Windows, my HDD wasn't getting detected.

I want to be able to access my HDD in Windows as well as run Ubuntu from it. How do I go about this? 

Thanks in advance.[/SIZE][/FONT]

---

### Post by TeoBigusGeekus on 2011-07-08
Windows (still :rolleyes:) cannot detect/read/write drives with linux filesystems.
Create a 20~30gb partition in your 500gb disk in which you can install linux and format the rest of it as ntfs; this way, both windows and ubuntu can read & write in it.

---

