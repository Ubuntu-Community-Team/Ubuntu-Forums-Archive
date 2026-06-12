---
title: "Windows XP and partitioning"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by theosam on 2010-06-07
I have a Windows XP system and I wanted to install Ubuntu without using wubi and without overwriting Windows XP. I asked plenty of people if it is safe to resize a partition in Windows XP. I get two answers. I am planning to install Ubuntu 10.04.

1. No, it is not safe. If you resize the partition, it will erase some of window's stuff. You should stick with Wubi.

2. Yes it is safe.

This is driving me crazy. Which one is it?

---

### Post by SlidingHorn on 2010-06-07
Well any time you're messing with your hard drive, you want to be sure that you back up your information.  If you don't want to use the wubi installer, I'd suggest giving this a read and making your decisions from there: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by darkod on 2010-06-07
During any partitioning operation sometimes problems can happen. So nobody can give you 1000% guarantee.
But in general, there is no problem resizing WinXP partition. And you would have to do it with third-party application or tool because XP doesn't have a built-in (MS started to include one from Vista).
In this case, running the ubuntu cd in live mode and using Gparted should do the job, XP doesn't have the tool anyway.
Some people say you should defragment XP first, others say it makes no difference. Up to you.

PS. You are right for not wanting to use wubi. It's nothing but trouble. Unfortunately many people seem "attracted" by the "easy install" without worried about the issues later.

---

### Post by theosam on 2010-06-07
I defraged, checkdisk, and backed up data. I am ready to go. Thanks very much for the info.

---

