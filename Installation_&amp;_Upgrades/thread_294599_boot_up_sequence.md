---
title: "boot up sequence"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by MacPC on 2006-11-06
Hi,

Currently, my PC is set up for triple boot. Windows 2000 Pro, Windows XP Pro and Ubuntu.

I am just wondering if I can simplify the boot up sequence.

Right now, when I boot up, the Grub comes up first, it will automatically boot into Ubuntu if I don't take any action. If I choose to boot up in Windows, the the Windows boot.ini will ask me to choose between 2000 or XP.

What I like to do is have one page give me the list of three choices like
Windows 2000
Windows XP
Linux

I try to modified the boot.ini, added C:\ Linux = "Linux" as one item after Windows, but when I choose Linux, it will take me back to the Grub.

Do I need to eliminate Grub all together? How?
Do I need to get rid of boot.ini and modify the Grub? How?

Thanks in advance.

MacPC

---

### Post by ReaderRat on 2006-11-06
The fact that you are getting choices that work with a triple-boot amazes me. I would leave well enough alone.

EDIT: Of course, This is just what ***_I_*** would do.

---

