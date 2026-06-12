---
title: "Installation error"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Fustigate on 2011-08-03
Hi.

I'm trying to install Ubuntu on my I: drive so I can see all my Windows folders and things because if I installed onto my C: it didn't work but I got told if I did it on my I: I would. Anyway, I downloaded the installer, and then I get this error: 
[img]http://i.imgur.com/54gAC.jpg[/img]

I've got the logs too if you need them.

Thanks in advance.

---

### Post by gordintoronto on 2011-08-03
Yes, post the log file.

What is your I: drive?

Since Windows is involved, it appears that you are doing a WUBI install. Is that correct? (WUBI is intended for people who just want to have a look at Ubuntu, not really for long-term usage. Personally, I think booting from a LiveCD is just as useful.) One thing you want to be sure of with WUBI, is that you allocate enough space to meet your needs. I would begin with 12 GB, assuming you are going to spend a few weeks of part-time playing around with Ubuntu.

---

### Post by bcbc on 2011-08-03
You can't install on dynamic drives. Ubuntu doesn't see them and you can damage whatever data you have on them. (With or without wubi).

---

