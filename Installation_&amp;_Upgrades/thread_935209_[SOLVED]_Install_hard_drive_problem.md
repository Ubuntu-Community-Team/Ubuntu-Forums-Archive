---
title: "[SOLVED] Install hard drive problem"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by nathand28 on 2008-10-01
When I try and install Ubuntu on my laptop, on the partitioner screen, Windows is set to take up 60% (22gb) of the hard drive, and Ubuntu 40% (17gb).I have a 40gb HD on my laptop. But when I try to drag the slider so that the amount Windows takes up on the HD, I can't. If I just leave it at this, and try to go to the next screen, it comes up with the message, "Too small size."
I don't know how to use the manual partitioner, so I was wondering if there is any way to fix this or a very easy to use guide on the manual partitioner table?

Any help appreciated.

---

### Post by tonyh6243 on 2008-10-01
Have you tried using GParted to adjust the size of your hard drives before you install Ubuntu?

---

### Post by nathand28 on 2008-10-01
> **tonyh6243 said:**
> Have you tried using GParted to adjust the size of your hard drives before you install Ubuntu?

I need a simple way to partition because I don't understand it and if I do it wrong, I might screw Windows up.

---

### Post by tonyh6243 on 2008-10-01
GParted will resize any of your existing partitions without compromising the data in that partition. You can download the latest copy from their website.

---

### Post by nathand28 on 2008-10-01
> **tonyh6243 said:**
> GParted will resize any of your existing partitions without compromising the data in that partition. You can download the latest copy from their website.
I don't know how to install it, or if I have to burn it to a CD, as I can't find anything understandable on the website.

---

### Post by tonyh6243 on 2008-10-01
No problem, download the latest copy from their website [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) Make sure to get the live CD version. burn that to a CD and place it in your CD/DVD drive. Restart your computer and the CD will load before the operating system. One cheviot of this is that you may need to change the order of the boot process in your bios. Just watch your screen as you boot up and it should say that in order to enter the bios you need to hit F8, F12, etc.

---

