---
title: "Partition Editing"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by deadowl on 2007-07-25
Okay, so I have way too many partitions, and I want to install Ubuntu Feisty fresh.
I know I have Kubuntu Feisty on sda6 (which I want to use).
I know which partitions are for grub and swap.
However, I am confused about 2 partitions:
sda1 or sda2 (I believe is Windows), but then there's another partition that's actually a lot bigger than any of the other partitions, and that's sdb. Could sdb be my external hard drive? I'm a bit confused. It would be nice if the partition editor could open the partition in the file manager so I could see the contents, but it just doesn't do that.

Okay, nevermind, I installed gparted, and sdb is my external hard drive.

---

### Post by kidders on 2007-07-27
Hi there,

One other way of identifying devices is to use **udevinfo**. For instance...

```
$ udevinfo -an /dev/sda | grep model
    ATTRS{model}=="ST3500841AS     "
$ udevinfo -an /dev/video0 | grep name
    ATTR{name}=="Logitech QuickCam Pro 4000"
```

Using gparted (or similar) for block devices is often more straightforward, but this is a more general tool, which walks an entire device tree, spitting out all the information it can find.

---

