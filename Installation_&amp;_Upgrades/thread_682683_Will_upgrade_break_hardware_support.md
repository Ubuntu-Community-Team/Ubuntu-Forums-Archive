---
title: "Will upgrade break hardware support?"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by zepol on 2008-01-30
First off, I've learned a lot by reading these forums, though this is my first post. A little background: I used RedHat at home from 1995 to 2000, but I haven't done anything with linux since then. Things have certainly changed ;)

I recently installed Ubuntu on a Gateway ML3706 notebook. Using the live CD for the latest version, 7.10, I experienced hard crashes upon wireless network identification, and sound didn't work. So I tried 6.06 instead and wireless worked out of the box. Sound still didn't but I fixed this by manually compiling and installing the alsa sound drivers. Now everything works great.

My question is, is there a way to update to Ubuntu version 7.10 without breaking wireless and sound? Are there apt-get commands that I should avoid or risk undoing my hard work setting up my system?

Thanks in advance,

Rob

---

### Post by PmDematagoda on 2008-01-30
All the official and pretty much the safest methods of upgrading are mentioned [here]("http://www.ubuntu.com/getubuntu/upgrading").

But keep in mind that the upgrade may not go that well so it is always a good idea to backup before performing the upgrade.

Also, one more thing, it is not necessary to risk breaking your working Ubuntu 6.06 install just to use Ubuntu 7.10 since Ubuntu 6.06 will be supported until about mid 2009. So if you are happy with your current Ubuntu 6.06 install then stick with it.

---

### Post by blazercist on 2008-01-30
why not download and burn gutsy to a cd and use it to create a small 5 gig partition for testing?

---

### Post by zepol on 2008-01-30
Thanks for the responses. If I upgrade I would definitely follow the recommended path (i.e., not just editing the sources and running apt-get). I know that I could try this on a separate partition, and I may wind up taking this path, but getting that partition up to where I am with 6.06 would take some work.

My question is, would upgrading using the recommended path a) replace my manually configured sound drivers with the default configuration that didn't work and b) break wireless?

Another way to ask this is what are the differences in hardware support between a system upgraded from a customized 6.06 to 7.10 and one where 7.10 is installed at the beginning?

---

### Post by PmDematagoda on 2008-01-30
Concerning both questions a and b, the answer is that if the upgrade works well then you will not face problems concerning sound and wireless. But if the upgrade does not go well then both sound and wireless may not fare well and you may face some extra problems as well. Also upgrading your PC to Ubuntu 7.10 would cause more problems than would be normal on an average upgrade since your PC was not able to cleanly install Ubuntu 7.10 so this might mean more problems by upgrading to Ubuntu 7.10.
> 
Another way to ask this is what are the differences in hardware support between a system upgraded from a customized 6.06 to 7.10 and one where 7.10 is installed at the beginning?

Because your PC works well with Ubuntu 6.06 there may not be much of a difference, but on the overall view, Ubuntu 7.10 should support more hardware than Ubuntu 6.06.

But all this comes down to one thing and that is:-
If you are happy with Ubuntu 6.06 and it works the way you want it to then stick with it instead of trying to do an upgrade and causing everything to break. And since Ubuntu 6.06 has more time to go before running out of support you would not be affected by vulnerablilites or such until support runs out.

---

### Post by hums07 on 2008-01-30
> **zepol said:**
> My question is, would upgrading using the recommended path a) replace my manually configured sound drivers with the default configuration that didn't work and b) break wireless?

Unfortunately, the stories of upgrading does not always have a happy ending. There are some threads about gutsy does not work as well as feisty (In my case, I get better system with Gutsy). So I can understand people just suggest you to stick with what you have or try the new version in a separate partition.

---

### Post by zepol on 2008-01-30
To summarize what I've heard it sounds like upgrading from my working 6.06, even using the recommended method, might break my hardware drivers. No one has recommended a solution that upgrades the distribution but keeps specified drivers in place.

Since the setup I have now works great I will hold off on attempting anything rash. If I chose to upgrade I will certainly test out the process in a spare partition, and if I find a way that works I will post the method on these forums.

Cheers and thanks again.

Rob

---

