---
title: "IBM ThinkPad T41 - error: Out of disk &gt; Grub Rescue prompt"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2010-12-22
A friend of mine has an old lappy as above with windows xp. It turns out that it runs Ubuntu 10.10 just fine as the only OS (but he needs winxp University studies), and Windows XP as the only OS.

The problem is that he can't dual boot because of the error listed in the title.  After many tries and a bunch of googleing it seems that the problem is that no kernel (from ANY OS) can be loaded if it's located above cylinder 1024.

I read hints about making a /boot folder and putting certain files there would fix the problem but I can't find a specific howto or help page on getting this done.

Can someone please work with me on this?

I restored his original XP install from a disk image and no Linuxware is currently on his HD.

I'm hoping to start from scratch armed with information that will make this work.

---

### Post by sikander3786 on 2010-12-22
So, from a booted Live CD, we need to see the output of fdisk.

```
sudo fdisk -lu
```

And as you plan to do a fresh install, /boot is not an absolute necessity unless you definitely need it. Let '/' partition handle all that stuff and you need not to worry about disk space for /boot.

How are you planning to install Ubuntu now? I mean partitioning scheme? And which version?

---

### Post by crjackson on 2010-12-22
> **sikander3786 said:**
> So, from a booted Live CD, we need to see the output of fdisk.

```
sudo fdisk -lu
```

And as you plan to do a fresh install, /boot is not an absolute necessity unless you definitely need it. Let '/' partition handle all that stuff and you need not to worry about disk space for /boot.

How are you planning to install Ubuntu now? I mean partitioning scheme? And which version?

Okay, first I want a fresh install of winxp, then a fresh install of 10.10.

The partitions were supposed to be 25gb win / 15 gb ubuntu.

When doing the above, the install proceeds normally, but the end result is a non-working system with the error indicated in the title.

Currently only xp is installed from a backup disc image. I don't really know how to move forward since I've tried many different grub repairs. I can only conclude that since the laptop doesn't support LBA, it can't load either kernel once grub is installed.

---

### Post by sikander3786 on 2010-12-22
Then we need to see the output of bootinfoscript.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

