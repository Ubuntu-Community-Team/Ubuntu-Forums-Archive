---
title: "Really Slow boot and no reboot?"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by rpaster1 on 2010-01-19
I have a desktop PC with an Intel 3.2 Ghz Pentium 4 CPU. 1.5 Gb of RAM, and 2 - 200 Gb Seagate HDD (1 is Windows XP only, the other is NTFS and Ubuntu partitions). It is a dual boot system using GRUB, with Windows XP the first item on the menu.lst file, and the latest Ubuntu 9.10 kernel and previous kernels the following items.

My problems are twofold since I upgraded from 8.10 to 9.04 to 9.10 of Ubuntu. First extremely slow boot to Ubuntu (multiple minutes to get to the login screen and then almost the same after login). Over all it may take up to 5 minute to get to a usable Ubuntu running. Once I'm in to Ubuntu, things seem to be okay. 

Second problem is when I reboot with the "restart" from the panel, the only way I can reboot to either Ubuntu or Windows XP is to physically turn off the power switch on the back of the computer. If I don't do this the machine never restarts it just tries to start and doesn't ever get to grub start up. After powering off, and then back on the normal reboot, with grub starting and giving the menu.lst options works fine.

Any help on either or both of these would be greatly  appreciated!!!

---

### Post by rpaster1 on 2010-02-02
I have some additional information, that maybe someone can help me with. During boot, after selecting Ubuntu from the grub menu, and maybe 5 minutes have passed I get an error that says "ureadahead-other main process terminated with status code 4".

Since i'm pretty much a novice at this, I don't have any idea how to fix this or what it means???

Please help

Bob

---

### Post by Sef on 2010-02-02
It's a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677").   A solution is [here]("http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html").

---

### Post by rpaster1 on 2010-02-20
Thanks for the help & pointers to "fixes".

I ended up finding out that my second hard disk is "struggling" with bad sectors, so I re-installed Ubuntu 9.10 on the same drive Windows XP is on and the problem is gone. Much faster boot and operation.

Thanks for the help,

Bob

---

