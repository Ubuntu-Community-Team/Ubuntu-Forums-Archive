---
title: "IBM thinkpad R31 - problems"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2010-09-13
have been given one of these, with 248Mb RAM. It's Running XP fine - a tad slow, but fine.

Am struggling to install 10.04 from the LiveCD. It takes about 20 minutes to load to the desktop, and is painfully slow. When I do manage to walk through the install it freezes at 95% ... restarting the machine shows GRUB2 is installed, and I can boot into XP, but the Ubuntu asks for my password, then hangs.

Surely if the machine can run XP, it can run Ubuntu ?

Can anyone suggest why it's acting this way. Memtest shows no errors, and XP is running 100%.

---

### Post by Rubi1200 on 2010-09-13
Hmm, "248Mb" is really not an awful lot, even for Ubuntu.

I suggest you give Lubuntu a try instead.

And you do say XP runs "a tad slow."

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Fafler on 2010-09-13
Do as Rubi1200 says and get Lubuntu instead. And when you burn the disc, do it at low speed. Some older drives have a hard time reading CD-R discs and writing at low speed sometimes improve compatibility.

You should look into getting some more memory for it. It takes up to two 512 mb modules for a total of 1 gb. Memtest can tell you if you have one or two modukes installed at the moment. [http://www.thinkwiki.org/wiki/Category:R31](http://www.thinkwiki.org/wiki/Category:R31) and [http://www.thinkwiki.org/wiki/PC-133](http://www.thinkwiki.org/wiki/PC-133)

---

### Post by lukeiamyourfather on 2010-09-13
Xubuntu is another good option. Also you could upgrade to 512MB of memory for about $40. Well worth it if you plan to use the machine much.

---

### Post by Jethro_uk on 2010-09-16
Thanks for the tips guys. In the end I downloaded Lubuntu, burned it as slow as my drive would go (I selected 1x, but it insisted on 8x) and it installed fine. Doesn't run too bad.

When I said XP ran "a tad slow" I meant for someone who is used to running 4GB of RAM with dual-core etc etc etc. I'm sure it was perfectly acceptable in 2001. I was a bit taken aback by that reply, as everyone who has every tried to sell linux to me (techie types at work, mainly) have always trumpted the fact that it needs less memory and performs better than Windoze, for any given hardware.

---

### Post by Rubi1200 on 2010-09-16
> **Jethro_uk said:**
> Thanks for the tips guys. In the end I downloaded Lubuntu, burned it as slow as my drive would go (I selected 1x, but it insisted on 8x) and it installed fine. Doesn't run too bad.

When I said XP ran "a tad slow" I meant for someone who is used to running 4GB of RAM with dual-core etc etc etc. I'm sure it was perfectly acceptable in 2001. I was a bit taken aback by that reply, as everyone who has every tried to sell linux to me (techie types at work, mainly) have always trumpted the fact that it needs less memory and performs better than Windoze, for any given hardware.
Yes and no; it depends on the overall hardware setup, especially RAM and graphics cards.

There are Linux distros which will happily run on that amount of RAM; I am thinking of Puppy Linux, Tiny Core, SliTaz etc.

When you have the time, you may want to check them out too.

Anyway, glad things worked out for you :)

---

