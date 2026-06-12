---
title: "[SOLVED] Windows+Ubuntu+Grub Problems"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by vbman11 on 2008-09-30
Ok, so I have Vista(sda1) and Ubuntu(sda6) on my computer with a recovery(sda2) partition. When I upgraded to 8.10 my kernel updated and I had a Dialog asking weather I wanted it to recreate menu.lst or not. Well I said yes and it removed the vista and recovery items from the list. I have tried sudo update-grub, grub-install, and a bunch of commands in grub but none of them add the items back in for vista or recovery. And when I first installed Ubuntu it automatically added the vista and recovery items. How can I get it to do that again?:(

---

### Post by caljohnsmith on 2008-09-30
As far as I know, I don't think there is a way to get Grub to automatically recognize your Vista partition and add it to the menu.lst after the installation, but I could be wrong. I would simply open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the end:
```
title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```
Based on what you said, that should be all it takes to be able to boot Vista again. If that doesn't work, then please post your menu.lst and also:
```
sudo fdisk -lu
```
Let me know how it goes.

---

### Post by vbman11 on 2008-09-30
well that works! Now I only want the recovery item

---

### Post by caljohnsmith on 2008-09-30
OK, for the Vista recovery partition:
```
title Vista Recovery Partition
root (hd0,1)
chainloader +1
```

---

### Post by vbman11 on 2008-10-03
thank you so much!:D

---

