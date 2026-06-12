---
title: "Just installed Ubuntu; Want to delete Debian"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Liesmith Loki on 2008-02-26
Hello. I'm a bit new with Linux, or just suck at it entirely, so I feel really stupid for asking this question... But uh, I just installed Ubuntu, and previously I had Debian, but hated it, since I could never get anything to work right. But um, when I boot, Debian still shows up as a boot point. I want to get rid of Debian. It looks like it's being kept on dev/sda1 partition. I was wondering how I should go about reformatting that particular partition. I'm going to need specific answers, because I'm not really familiar with how to get around of Linux.

I heard something about Gparted. What's that?

---

### Post by Pumalite on 2008-02-26
Post:
sudo fdisk -lu (from the Terminal)

---

### Post by jken146 on 2008-02-26
gparted is a GUI application for dealing with partitions.  You can install it through Add/Remove, Synaptic or in the terminal.  The terminal way is:
```
sudo aptitude install gparted
```

To run gparted, you'll find it in System -> Administration -> Partition Editor.


You'll probably want to make sure that Debian is indeed on sda1.  In gparted, Ubuntu's partition will show up as /.  If you're in doubt about which partition is which, please post the output of the command ```
sudo fdisk -l
```

You can use gparted to delete or format the partition that Debian is on.  You can then use the space as you like.

---

### Post by Liesmith Loki on 2008-02-26
Thanks a bunch! It was indeed sda1. =] Thank you again.

---

