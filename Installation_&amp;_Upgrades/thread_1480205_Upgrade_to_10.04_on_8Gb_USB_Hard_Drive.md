---
title: "Upgrade to 10.04 on 8Gb USB Hard Drive?"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by LMCELHINEY on 2010-05-11
I have a Dell Latitude D630 onto which I applied an installation of **Ubuntu 9.10** on an** 8GB** external USB hard disk (mechanical, not FLASH) with now problems.  It has been working beautifully, but I upgraded last night to **Ubuntu 10.04**.  I had it run overnight and believe that I ran out of hard disk space, as I have less than **100MB** left on the drive.

-I'd like to ensure that the installation completed properly so that I can run it for further modification/repair/reinstall.

-I know that this free space is inadequate and would like to either properly remove unneeded files or restart with a minimal installation of **Ubuntu 10.04**.

Is there anyone who could make suggestions as to where to start this process, please?

Thanks much for your time!

Larry

---

### Post by dino99 on 2010-05-11
8 Gb is enough to install the system alone (5 might be the minimum) but depend on how many extra packages (softwares) you have installed, so some can be removed i guess (look at software center).
Then, is the swap partition on this stick too ? if so you can reduce it.

of course, clean the installation and make room first: autoclean, autoremove, gconf-cleaner and bleachbit can help

---

### Post by Sven6210 on 2010-05-14
A clean install of 10.04 from a USB stick will be no problem.

Running an update might however be difficult. You already have Ubuntu and some other files on your harddisk and I assume you are using 6 GB of the existing 8 GB. When you make an online update from 9.10 to 10.04 Ubuntu first wants to downloads all updates (e.g. 4 GB) and then runs the installation of the updates. I admit that this is only a guess, but I expect Linux to work this way. So in your case the system tries to download 4 GB but only has 2 GB left. Obviously you will run out of space.

Maybe you want to consider a clean install. I did so on my EeePC with 16 GB SSD (I replaced the original slow 8 GB SSD with a much faster 16 GB SSD) and it was no problem. And 8 GB is definitely enough for an installation of 10.04

---

