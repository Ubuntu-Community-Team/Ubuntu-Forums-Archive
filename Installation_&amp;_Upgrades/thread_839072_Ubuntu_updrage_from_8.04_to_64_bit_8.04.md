---
title: "Ubuntu updrage from 8.04 to 64 bit 8.04"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by amitmo on 2008-06-24
i would like to know the procedure from changing ubuntu i386 to ubuntu 64 bit 8.04............

---

### Post by Kobalt on 2008-06-24
You cannot upgrade from one architecture to another, you will need to reinstall your whole system.
In this case, like in many others, having a separate /home partition would save your personal data and make your system change a breeze. You might consider doing this as you reinstall your system.

---

### Post by amitmo on 2008-06-24
i have dual boot system with windows, do i need to re install windows also or i can re install ubuntu independly?

Morever how to create separate \home partition?

---

### Post by Kobalt on 2008-06-24
Your windows install doesn't need any change, this is all about Ubuntu.

When you install Ubuntu, when you reach the partition process select the custom partitioning option. From there, you will need to create three partitions:
/ where your system and programs will install
/swap
/home where you'll keep your personal files

As size matters, / is usually between 6 to 10 GO, depending on your needs (a basic Ubuntu install is bellow 3Go).
/swap can be as low as 256Mo if you have a really recent computer, more if your computer is older...
/home can be as big as you want, depending on your storage needs.

Both / and /home should be formated as ext3.

There are lots of discussions among the forums about partitioning schemes, some more elaborated than others... You could read some if your interested in make a very tweaked system, but the classic / /swap /home partition scheme is sufficient IMHO.

---

