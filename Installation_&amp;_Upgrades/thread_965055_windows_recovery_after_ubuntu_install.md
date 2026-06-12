---
title: "windows recovery after ubuntu install"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Aimbob on 2008-10-31
Hi, 

I bought a MSI wind netbook earlier this week, and there were 2 partitions on the HD. One for windows(140gb) and one for windows recovery(10gb).

I partioned the windows partition to install ubuntu, I also made an extra partition for reinstalling windows xp later on. I installed Ubuntu and it runs just fine. But when I press F3 to start windows recovery it doesn't do anything.

I was told that the master boot record is changed and that the recovery isn't included in this.

How can I add the windows recovery to the master boot record in Ubuntu so I can install windows xp on my free partition?

---

### Post by oldos2er on 2008-10-31
You'll need to edit your /boot/grub/menu.lst file to add the partition.

---

### Post by caljohnsmith on 2008-10-31
First open up a terminal (applications > accessories > terminal), and open up your Grub's menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom of the file, add:
```
title Windows Recovery
root (hd0,X)
chainloader +1
```
But replace X with the partition number minus one. Thus if the recovery partition is the 1st one, use (hd0,0), if it is the 2nd partition use (hd0,1), etc. If you run into problems, then please post:
```
sudo fdisk -lu
```
And by the way, depending on how your recovery partition works, you may only be able to boot the recovery partition once and it will overwrite Ubuntu and restore Windows to your drive. Just a word of caution. Anyway, let me know how it goes.

---

