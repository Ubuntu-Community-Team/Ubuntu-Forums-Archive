---
title: "Cannot mount /dev/sda1 in Live CD"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2011-06-08
In a desperate attempt to play Tomb Raider, I have shrunk the /dev/sda1 with GParted in Maverick Live CD (the same one I used to install) then installed WinXP on it. Unfortunately for reason X, XP simply does not boot.
So again I am in the Live CD, I have deleted the XP partition and am now trying to fix Grub2. In all the tutorials, you need to mount the normal partition. Which is what I am trying to do, but:
```
sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```So there in nothing that I can do. Under "Places" I see my *489GB file system* but I cannot mount it.

At least I am getting Internet through the Live CD and I always have Knoppix on hand.

Thank you very much!

EDIT: I should tell you that there is a *boot* flag on the /dev/sda1.

---

### Post by 3602 on 2011-06-08
Detached *boot* flag.

---

