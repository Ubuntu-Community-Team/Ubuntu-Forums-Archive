---
title: "Installer keeps crashing"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by Red.Rabbit on 2007-08-09
I can get to part 6/7 (the part where you create a log in account) fine, but once I fill everything out on that page and click forward the installer crashes.

Does anyone know what's wrong?

---

### Post by merlinus on 2007-08-09
You might check the cd for errors at the live cd bootup screen.

-merlin

---

### Post by dabl on 2007-08-09
Guess #1 = bad ISO file (check it with md5 checksum)

Guess #2 = bad CD burn (you gotta burn 'em slow, 4X is recommended speed).

---

### Post by Red.Rabbit on 2007-08-09
I did and it didn't find anything wrong.

EDIT: I didn't burn the CD, I had it sent to me.

---

### Post by Odrodzona-Sarmacja on 2007-08-09
I just might have an idea.

I had installer crashing on me, when I was trying to install Ubuntu for second, third and so on n:th time. It seems it was something wrong with gparted tool comming with Ubuntu 7.04!

My work around was:

-turn all ext3 partitions into fat32
-secure format fat32
-use another partion tool to preformat ext3 partitions

Then instalation worked.

Then I did run latest version of gparted lifecd to check and fix on ext3 partitions any problems resulting from activity of gparted during install.

---

### Post by Red.Rabbit on 2007-08-09
I'm not sure how to do that (I'm still new to a lot of this), could you give me a step by step guide to do that?

Btw, I'm trying to dual-boot ubuntu with Windows XP if that helps any.

---

