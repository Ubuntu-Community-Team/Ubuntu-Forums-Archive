---
title: "Quick Dual Boot (GRUB) Question"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by ziadoz on 2007-03-03
Hi,

I want to dual boot Ubuntu but using the Windows XP NT Loader. I know I have to install GRUB to the Ubuntu partition, and then get the first 512 bytes, add a new line to the Windows XP bootloader pointing to the file etc. My only problem is how do I change the location of the GRUB installation? Can I do it at this point during the Live CD install process?

[IMG]http://debianadmin.com/copper/albums/edgy/22.png[/IMG]

I can edit the text in the box. If say I changed this to hd0,1 would it install in the second partition of the first hard disk?

---

### Post by louieb on 2007-03-03
You just answered your own question. When using the Ubuntu Live CD thats exactly how to tell the installer where to put GRUB.
BTW any reason the installer is not formatting a swap partition?

---

### Post by ziadoz on 2007-03-04
I took the screenshot of a random website. Its not my actual installation of Ubuntu. :) So that will **definitely** put GRUB onto the second partition if I change it to hd0,1?

---

### Post by louieb on 2007-03-04
> **ziadoz said:**
> ...  that will **definitely** put GRUB onto the second partition if I change it to hd0,1?
That's how you do it. The installer  will put GRUB where you tell it whether you wan it there or not. Don't forget the parenthesis (hd0,1).
BTW all my answers come with this warranty. If it breaks you get to keep both pieces. :)

---

### Post by ziadoz on 2007-03-04
Its ok. I have an image of my XP setup, including MBR, just don't fancy the hassle of restoring them all. I'll give it a whirl. Thanks for your advice. :)

---

