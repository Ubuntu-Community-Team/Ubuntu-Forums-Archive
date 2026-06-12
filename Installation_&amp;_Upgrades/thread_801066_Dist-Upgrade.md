---
title: "Dist-Upgrade"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by civillian on 2008-05-20
This area of the forums seems to be the right place to ask this question, so here goes:

How much danger is there that I will brick my system if instead of installing fresh (latest) ubuntu I run dist-upgrade? I have only installed packages from the repos that are standard (although I have non-free and multiverse enabled in synaptic) and the only application I have installed myself (froum source) is libgpod 0.6.0?

I read some blogger's article saying as long as you kept an eye on old/dead/broken packages in your system you should be fine, but I hesitate to take the advice of one man, since I have used many other distros that offer a similar dist-upgrade system, and often I have been told it would be better to do  fresh install, (although it's often a hassle, since I have perpetual issues with my hardware and setting up the base system can take a while; drivers and whatnot) most notably linux mint, which is a derivative of ubuntu.

Anyway, thankyou for your advice, 
Civ: a returning ubuntu user.

---

### Post by muadnu on 2008-05-20
In my case, I did an upgrade from Gutsy to Hardy (beta at the time) with no problems whatsoever. I think many people have had problems, but not me. I upgraded for reasons similar to what you said in your post (not to lose my hardware and other configurations), and everything worked out.

In any case, you could try upgrading and if it doesn't work do a fresh install. Since if you plan to do a fresh install you'll need to backup your data first (unless you have it in a different partition), you can back it up anyway to begin with, and then run dist-upgrade and see how it goes. The only thing you can lose is some extra time doing the upgrade and then, eventually, doing a fresh install...

---

### Post by avtolle on 2008-05-20
I've one more piece of advice if you don't mind; before doing a dist-upgrade, be sure your current system is completely updated; then do the backups as recommended, and go for it. As was said above, all you have to lose is a little time (assuming that you have your data, etc., backed up). If you have created a separate /home partition in the past, that makes backing up and upgrading (regardless of the method) a bit less painful, IMO. Good luck.

---

### Post by zvacet on 2008-05-20
Since **muadnu** and **avtolle** advised you well I want to make one suggestion (one more option to you).You can make upgrade with alternate CD and if something goes wrong you have CD for fresh install.If all goes well you still have CD which can be useful in future.

---

### Post by civillian on 2008-05-21
Thankyou, to summarise tne advice totalled the following steps:
1. Back up (i do this already although probs not as much as I should...)
2. ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
3.reboot and check install is a-okay if all good proceed to step 5, if failed continue to step 4
4.Install from fresh cd
5.Enjoy updated/upgraded ubuntu

Thankyou for your help, I was just wondering since the last time i tried it was a while ago, and while it all worked, it was after a fresh install of 6.04 (to 6.10) and with little to no extras installed, so I just thought I'd check.

Thankyou all for your help!

---

