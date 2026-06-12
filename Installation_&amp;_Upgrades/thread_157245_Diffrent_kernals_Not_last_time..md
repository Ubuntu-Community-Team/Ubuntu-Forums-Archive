---
title: "Diffrent kernals? Not last time."
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by iAlta on 2006-04-08
Hi, I am just installing Ubuntu,(not for the first time) an in the prosess of installing, I get an option wich I haven't ever gotten before I can choose between diffrent kernals:
Linux-386
Linux-image-386
Linux-image-2.6.12-9-386
What should I choose, and what is the difrenca?

---

### Post by outlawtanker on 2006-04-08
Well, I don't know the deep down difference of them, but I suppose the first 2 are just generic versions, someone correct me if I'm wrong. I used the last one, because I got an error with the 1st, although I'm installing the 32 bit edition onto a pc with a AMD Athlon X24400+. I would use the 3rd choice, but that's just me. It's easier to keep track of what version your kernel is if you have compatiblity issues after an update, that way you know where to go back to.

---

### Post by iAlta on 2006-04-08
can I change it back later?

---

### Post by Sutekh on 2006-04-09
[QUOTE=iAlta]Hi, I am just installing Ubuntu,(not for the first time) an in the prosess of installing, I get an option wich I haven't ever gotten before I can choose between diffrent kernals:
Linux-386
Linux-image-386
Linux-image-2.6.12-9-386
What should I choose, and what is the difrenca?[/QUOTE]
**linux-386** depends on the latest complete kernel available, specifically the latest **linux-386-image** and **linux-restricted-modules-386** packages

**linux-image-386** depends on the latest kernel image, which at the moment is **linux-image-2.6.12-10-386**

**linux-image-2.6.12.-9-386** is the kernel that comes installed with Ubuntu 5.10.


So basically **linux-386** will always get you the **latest complete kernel**

**linux-image-386** will always get you the** latest kernel image**

**linux-image-2.6.12-9-386** will get you the **kernel image version 2.6.12-9-386**


To stay up to date, install the** linux-386** package if you require the -restricted-modules- (basically you need this package for non-free modules for NVIDIA/ATI video cards or Winmodems), or the **linux-image-386** if you don't need the restricted-modules package.


[quote=iAlta] 	can I change it back later?[/quote]
When you install a new kernel you always have the option of booting Ubuntu using the new kernel or the old kernel, from the GRUB menu.  

If at a later date you are satisfied that the new kernel is working for you, you can remove the old kernel.  You can always keep it too if you like.

(Hope the bold was helpful rather than annoying :))

---

