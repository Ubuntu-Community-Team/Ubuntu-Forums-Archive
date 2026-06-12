---
title: "Whats better installing ubuntu 10.10 in windows or out of windows?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by jcer93705 on 2010-10-12
Wanted to know i installed ubuntu 10.10 in windows because i'm lazy of going to the store and buy blank cd. Now if I uninstall it and boot a ubuntu disk then create my own partition and what not. Would I tell if it speeded up or not? Does it make any differnt?

---

### Post by garvinrick4 on 2010-10-12
A partition install is a better experience than WUBI. It will use the RAM you have better and
runs on its own not inside of Windows. Wubi is just a folder in C; drive and using windows grub to boot from. If you have not tried a partition install give it a whirl.

---

### Post by lechien73 on 2010-10-12
Wubi is good, in my opinion, if you're planning on testing Ubuntu before you "commit" to a full install.

There is a slight performance degradation inside Windows, because the Linux filesystem is built on top of the Windows filesystem. This also means that you could be more vulnerable to data corruption if you lose power or Windows doesn't shut down properly.

As an older post, which pretty much sums up my attitude regarding wubi said:

> As for long term use, I would consider wubi as a mid-term solution. You can use it happily for weeks and months...if you find yourself using Ubuntu quite heavily, you might want to do a full installation later on...If you have a free partition or a spare hard disk and are confident about partitioning and ISO burning there is no much reason to use Wubi, just go straight for the full installation via live CD. But for people that do not know what a partition is, wubi is probably the best solution to date.

---

### Post by moorebounce on 2010-10-12
I actually like running Ubuntu inside windows because at least when it boots up it gives me a choice of all the OSs I have on my machine in one menu. When you do a clean install of Ubuntu you have to go through two menus to choose another OS.

---

