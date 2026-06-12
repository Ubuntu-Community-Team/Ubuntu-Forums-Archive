---
title: "Installing Ubuntu causing PC to restart every 10-20seconds"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by a2930314 on 2014-09-13
Hey everyone, just as stated in the title, I'm trying to install ubuntu(first time using/installing it) through USB, but it is now restarting my PC every 5-10seconds. At first I was able to run the trial part, I guess it would be called, fine without crashing or restarting, but now I can barely do anything before the PC restarts(when Ubuntu runs). This is also a brand new build with no OS installed..

It is an MSI motherboard, which I've heard has had issues with Ubuntu, here are my specs
MSI A55M-E33
AMD A6-6400k 
8GB of Ram
250GB SSD
If there is more that you guys need let me know...

Can anyone help me? I read that by adding a command line "radeon.dpm=0" will fix it, and as I said I'm completely new to this and nowhere can I find information on how to do it.
I really want to love Ubuntu, but trying to find a solution to this problem for 2 hours is really taking a toll on that love. Please and thanks in advance!

Edit: I should also add that I followed the guide from Ubuntu's site to get the iso onto the USB

---

### Post by fantab on 2014-09-14
That is a bug in 14.04 wrt certain MSI boards, AMD APU's and some intels as well.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578)

Try the 'workarounds' suggested on the bug page.

You can also try Ubuntu [12.04-lts]("http://old-releases.ubuntu.com/releases/12.04.0/"), which has support upto 2017...
12.04 the first release
12.04.2 with 12.10 Hardware enablement stack or [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
12.04.5 with 14.04 Hes... and so on.

Try the latest 12.04.5 first and work your way backwards...

---

