---
title: "resetting grub"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by Jargv on 2008-09-05
I currently have 2 linux distributions on my computer (and 2 flavors of windows). The first linux that I put on the machine was Ubuntu. When I put the second distribution on my computer it took over the grub installation, so now grub is using the /boot/grub/menu.lst file of the new linux installation. 

I want to get rid of the second distribution and free up a 30g partition, but I know that this will break grub.

How can I reset grub to use the /boot/grub/menu.lst file of the original ubuntu installation/partition so that when I remove the other linux distro it will not effect my working ubuntu installation?

thanks,

-jargv

---

### Post by caljohnsmith on 2008-09-05
From Ubuntu, just do:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return the partitions of both your Linux distros in the form (hdX,Y), just choose the one that is Ubuntu, and then:
```
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you need more info/details.

---

### Post by Jargv on 2008-09-05
Worked like a charm! Thanks!

---

