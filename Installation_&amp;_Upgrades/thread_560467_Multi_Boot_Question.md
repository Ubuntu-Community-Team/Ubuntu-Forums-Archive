---
title: "Multi Boot Question"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by zaden.winkler on 2007-09-26
Hey,

I have installed Windows Vista, Then Windows XP, Then Kubuntu hoping the grub would detect the other operating systems.

 Well when grub boots i get the linux boot lists fine and then i have Other Operating systems and then i have Windows Vista/Longhorn (loader)


The Windows Vista/Longhorn boots up my windows XP, and the other operating systems does nothing.


How can i correct this and set it up right.


title,          ,         Windows Vista
root,         ,         (hd0,3)
savedefault
makeactive
chainloader   +1






Thanks.

---

### Post by confused57 on 2007-09-27
If you know which partition Vista is installed, you could try hiding each of the Windows OSes from each other:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)

If you're not sure which partition is installed to, you can open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by zaden.winkler on 2007-09-27
Thanks that webpage helped my solve the problem i been having.

---

