---
title: "ubuntu 12.04 instalation crash"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by 6iixjjpU on 2013-11-28
I'm trying to dual boot ubuntu with my windows 8 on a dell Inspiron 15 3521. When I go into the boot menu and select to start with the instalation disk, i get white diagnal lines and it gets stuck there. I also have an iMac where I installed ubuntu on with the same disk. It also get simular lines but after a minute or less it did continue to the instalation without any problems.

[EDIT]
My laptop specs are:
6GB RAM
i5 3337U
Intel(R) HD Grapfics 4000 (I think this is the primary gpu)
AMD Radeon HD 8730M
[IMG]http://i.imgur.com/JrFB8vS.jpg[/IMG]

---

### Post by fantab on 2013-11-28
Post details about your laptop specs, like RAM, CPU Graphics etc.
In Windows 8 have you disabled '[FastStartup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")?

---

### Post by 6iixjjpU on 2013-11-28
I did and it didn't help, I also updated my post

---

### Post by fantab on 2013-11-28
You have [Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics"). Sometimes it is necessary to have the AC plugged in to power primary GPU.

For now use '[**Nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132")' option and see if it helps.

If it doesn't help then wait for some expert advice...

---

