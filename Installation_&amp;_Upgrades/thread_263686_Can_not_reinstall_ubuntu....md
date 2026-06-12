---
title: "Can not reinstall ubuntu..."
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by bubi1980 on 2006-09-23
--------------------------------------------------------------------------------

Hi all,

I have (had) a dual boot system with 2 harddisk. Ubuntu and Xp were installed on the same harddisk.
I tried to reinstall ubuntu with the LiveCD. I did the following things:
1. Put the ubuntu cd and booted from it
2. After ubuntu loaded, I run Gparted and deleted the existing Linux partitions (/home, /root and /swap).
3. I made new ones in place of them and formated them to ext3 and swap (still with Gparted)
4. Closed Gparted and clicked "install", chose language, time zone, filled in name and user password etc..
5. Chose "manual edit partitions" and the scanning process of "prepare partitions" started (you know that orange block moving left to right and back)
And what now happens is that the process freeze (at the "scanning all devices"...!! First i thought the Cd was not ok, but i rewrited it.

If i run fdisk from the terminal with the Ubuntu CD, i see on the list all the partitions. If I delete the partitions with Gparted then is the list empty, except Windows Xp partitions.

Dont know what to do, how to solve this problem.

---

### Post by meng on 2006-09-23
I would not approach it that way - instead I would do steps 1, 4, 5 and take it from there. Step 5 should take the place of steps 2 and 3.

---

