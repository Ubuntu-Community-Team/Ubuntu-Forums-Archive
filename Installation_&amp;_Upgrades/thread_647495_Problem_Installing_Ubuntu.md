---
title: "Problem Installing Ubuntu"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by aughmed on 2007-12-22
Merry Christmas Everyone!! I got a problem thats been bugging me for some time! Every time i try to install ubuntu on my Dell Dimension L600cx, xorg doesn't initialize! I tried using the new 7.10 live cd and tried using the 6.06 LTS text based installer! Its got me stumped! I wonder if its the ATI radeon 9250 pci card, but it seemed to do the same thing with the on-board graphics chip! Can anybody help me please!!

---

### Post by jken146 on 2007-12-22
Can you be more specific about the problem with xorg not initialising?  Have you tried ```
dpkg-reconfigure xserver-xorg
```?

Merry Christmas to you too :)

---

### Post by aughmed on 2007-12-22
Well, when I try booting up the installation disk, the boot process goes smooth until the point the video is initialized. The tty responds, but the xorg doesn't. is there a special boot parimeter that i can use??

---

### Post by aughmed on 2007-12-22
I see what i did wrong! I thought i had the text based installer, but i accidentally had the live cd. I got the text based installer running, but as far as i can go is the partitioning! I never had a problem with partitioning before! The program justs hangs! I can get it up to the point that its going to write the partitioning information to disk, and then it just stops responding! i wonder if its my hard drive controller? But it seems to run fine when i boot windows! I tried installing ever since 6 in the morning! I thinl I rebooted the computer 20 times so far....! LOL!!!

---

