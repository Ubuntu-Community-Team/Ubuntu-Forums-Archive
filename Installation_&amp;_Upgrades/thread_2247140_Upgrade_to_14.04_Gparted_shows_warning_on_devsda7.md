---
title: "Upgrade to 14.04 Gparted shows warning on /dev/sda7"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2014-10-05
Hey y'all

I'm trying to upgrade to 14.04 while keeping 12.04. I'm using the live CD for the side-by-side install. The first attempt had a problem with  Flash, so I closed out the install. Then, on a second attempt, it created multiple partitions and /dev/sda7 shows a warning flag. I spent a lot of time trying to find out the problem and how to fix it, but have not found a clear explaination. For obvious reasons I don't want to wipe the entire drive, so if I can get a little help I'd appreciate it.
The HDD is 600 GB and when I installed it, I made 2 partitions - roughly  328 gb and 268 gb. I've been using 12.04 on the large partition and have nothing on the other one.

So, when I started the second install of 14.04 and saw multiple drives AND the warning flag I don't know what to do. Here are the Gparted screenshot and the warning I got.

I looked at the "information" panel for /dev/sda7 but I have no idea how to read that info.
Help?


[ATTACH=CONFIG]256976[/ATTACH][ATTACH=CONFIG]256977[/ATTACH]

---

### Post by Dennis N on 2014-10-06
You have more than the two partitions you mention so it is a bit confusing here and the sizes you give don't match very well.  So there are questions: Where is your 12.04 installation, sda6? Is sda1 where 14.04 was installed in your second attempt? If so, does it boot and run correctly?
If it does, you could just delete the bad partition sda7 with gparted. It may be a remnant from the aborted first install.

---

