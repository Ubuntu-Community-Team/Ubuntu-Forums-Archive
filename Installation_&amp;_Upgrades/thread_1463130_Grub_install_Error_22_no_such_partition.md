---
title: "Grub install Error 22: no such partition"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by maremmano on 2010-04-26
Hi, i'm new of this forum, I have a big problem and I hope you can help me to find out a solution...
I'm backing up my old grub of ubuntu in my /dev/sda5 (ext3) after a Windows installation in my /dev/sda1 (ntfs), of course now I can only boot Windows. I use a Cd live of Ubuntu and these are my command:

sudo grub
> find /boot/grub/stage1
   (hd0,5)
>root (hd0,5)
>setup (hd0)
.........
.........
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst".... failed

Error 22: No such partition

So, what can I do? I don't find any such problem, please help me....:-((
Sorry for my english....;-)

---

### Post by zvacet on 2010-04-27
See if [this]("http://members.iinet.net.au/~herman546/p15.html#22") can help you.

---

