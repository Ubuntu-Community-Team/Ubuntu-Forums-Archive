---
title: "Raid Install"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by drwoo on 2008-07-29
Hello,


So, this is what I want to do, and I'm stuck on the Linux part of it. Currently, I have winXP running and I'm planning on installing Vista, server 03, and Linux today. My issue is that XP and Vista will be on a raid (striped). Linux and server will be on a 300GB drive, and the other two will be on a 1.5TB striped raid. 

The RAID is a hardware RAID that is built on to the motherboard. (nvidia), came with a Asus Striker II Formula motherboard. My question is this, What is the best solution to boot all the OS's, I was told that grub would be a good option however, will grub detect the raid and the OS's that are installed on it? If so, would installing Linux last be the best option? Or is there another boot manager that would be a better option? 

Thanks in advance,
Dr. Woo

P.S.
To make sure I have the correct version of Ubuntu, I want to make sure it has a gui at install. I know some of the commands in command prompt mode, but the last time I used Linux, was slakware installed from diskettes. So I want to make sure it has the gui till I get used to it again.
Thanks again

---

### Post by amenszer on 2008-07-29
Yes, 
From my experience, grub is the most versatile boot loader. I would recommend installing Ubuntu last, as its installation manager will not have any problems (at least from my experience) detecting your other operating systems. 
All you really need to do is tell Ubuntu where it will be installed, and it pretty much does the rest. 
And the Ubuntu Server LiveCD has a GUI that is very easy to use.

---

### Post by drwoo on 2008-07-29
I just do not want to end up in a situation where I can only get into Linux. After installing 3 other OS's this would be a huge pain. That's why I'm just making sure this will work before I actually do it.

Dr. Woo

---

