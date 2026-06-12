---
title: "Fresh install of ubuntu 14.04 and opening windows is very slow"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by glen8 on 2015-08-13
Hi, 
I just installed 14.04 on an old Dell that had xp on it. Problem is after it was installed every time I click on something the window opens and closes very slow (fps). the computer has an intel video driver. I'm wondering if anyone can help me out. Thanks!

---

### Post by QIII on 2015-08-14
Hello!

Could you give us the hardware specifications of the machine?

If the machine is old enough, it may simply not be up to the task of running Unity, in which case a lighter flavor like Xubuntu or Lubuntu might be more appropriate.

---

### Post by Bucky Ball on 2015-08-14
Welcome. Please open a terminal and type or copy/paste this:

```
sudo lshw -C video
```

Hit return and post the output here between code tags, thanks (see the last link in my signature).

PS: Ninja-ed by QIII! :)

> **QIII said:**
> If the machine is old enough, it may simply not be up to the task of running Unity, in which case a lighter flavor like Xubuntu or Lubuntu might be more appropriate.

^^^
This.

---

### Post by glen8 on 2015-08-14
Don't know the specs. Actually posting from a different pc. I'll attach a pic of the dell. It might be too old.

---

### Post by Bucky Ball on 2015-08-14
Please see post #3 and post the results thanks. A picture is not much help. You can also run:

```
lspci
```

... and that will give us all the specs. There will be a model number on the back of the box also.

We can only provide support on the strength of the information you give us and a photo of an old computer doesn't give us much. :)

---

### Post by QIII on 2015-08-14
Looks like an Optiplex GX260 SFF.  If it is:

P4 @ 2.4GHz
512MB RAM
40GB HDD
Integrated Intel graphics, probably very weak.

It will almost certainly struggle to even start Unity.  I'd go for Lubuntu.  But even with that it will not be a speed demon.

Vintage around 2000 - 2004.

---

### Post by glen8 on 2015-08-14
Model dhp 
2003 computer

---

### Post by QIII on 2015-08-14
DHP refers to a range of models in the GX series.

If you can get us the official specs as Bucky Ball has asked, we can be more specific.  In any case, it is not going to be up to Unity.

---

### Post by glen8 on 2015-08-14
what if I upgrade the ram?

---

### Post by QIII on 2015-08-14
That will do very little, if any, good with getting Unity to run.  Unity as a graphics-heavy Desktop Environment (DE).  It requires a relatively modern graphics adapter.

You really need a lighter DE or even a Window Manager (Enlightenment is nice) instead.

As I said, Lubuntu would be a good place to start.  The LXDE DE might be light enough.

---

### Post by glen8 on 2015-08-14
just started the lubuntu install. Thanks for the help!

---

### Post by QIII on 2015-08-14
Let us know how it goes.  We can find a lighter option, like a WM, if need be.  There are also some very light weight Ubuntu-based distros out there, like Bodhi Linux.

---

### Post by glen8 on 2015-08-14
never heard of those. Thanks again. I appreciate it

---

### Post by Bucky Ball on 2015-08-14
Let us know how you go. 512mb of RAM will probably not be the greatest computing experience, even if you manage to get it installed and booting. RAM would help that, but as QIII says, your options are limited re. graphics and therefore desktop environment. :)

With Ubuntu and a couple of Gb of RAM (or even one at a pinch) you should get along fine.

PS: If Lubuntu is still sluggish, you can go one step lighter with the [Lubuntu-mini]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). Trickier to install but may improve the situation. Good luck.

---

