---
title: "Question about wubi installation"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by ctbear on 2010-11-03
Hi,

I'm new to ubuntu (or linux in general) but ubuntu seems really promising so I'm considering running it on my laptop :)
I'm aware that besides Virtualbox, I have 2 ways of installing ubuntu: wubi and dual boot
Dual-boot is very self-explanatory, but I'm kind of confused about wubi.
It seems like through wubi, ubuntu is installed as a windows application, and can be uninstalled like other software. But being an OS, does wubi installation creates a separate partition?
What are the disadvantages of using wubi compared to using dual-boot option?
Thanks.

---

### Post by Rubi1200 on 2010-11-03
Hi and welcome to the forums :)

Wubi creates a virtual disk **within** Windows allowing you to experience Ubuntu without worrying about partitioning or installing another operating system directly to the drive.

However, Wubi was never intended as anything other than a means to try something different. As such, there are performance issues in the long term as well as problems with upgrading the install (at least with the last 2 versions).

I suggest you first try Ubuntu as a LiveCD and decide if you like what you see and whether it works with your hardware configuration.

If yes, then come back and we will walk you through setting up a dual-boot system.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Mark Phelps on 2010-11-03
As Rubi1200 indicated, Wubi does NOT create a separate partition -- and ironically, that is both it's major strength and major weakness.

It's a "stength" from the perspective that if your faced with a preinstalled Vista/Win7 box that already has the limit of 4 primary partitions in place (something the OEM's seem to be fond to do), you don't have to mess around with repartitioning your box -- and possibly losing something valuable in the process.  

But ... it's a "weakness" from the standpoint that it's subject to any filesystem/boot problems affecting MS Windows.  Windows crashes (which can happen with something as simple as a routine Windows Update), you lose access to Ubuntu as well.

As to other strengths ... even if you aren't up against the 4-partition limit, a Wubi install prevents you from having to deal with partitioning in any way.  So, you don't run what seems to be a risk gaining in frequency with the new installer -- accidentally wiping out your Vista/Win7 installation as a byproduct of installation.

Finally, you don't mess up your MBR because you don't replace it.  Thus later, should you decide to remove Ubuntu and go back to strictly Vista/Win7, you don't have to deal with the problem of replacing the MBR to remove GRUB.

As to other weaknesses ... it can be a little slower, but you'll probably not notice the difference in performance.  

Also, since it uses its own version of GRUB4DOS, you can't take advantage of current GRUB2 enhancements.

What's up for debate now is whether or not it's really a long-term solution.  We used to say it was only for short-term trials, but then we got lambasted by folks who claimed to have used it from release to release to release.

And finally, I've also read that upgrading recent Wubi versions has been problematic as well ... but folks will be quick to tell you that doing in-place upgrade of "regular" Ubuntu installations is also a bad idea.

Myself ... I would NOT use it.  But I prefer, and have a LOT of experience with, multi-boot solutions.

---

### Post by sikander3786 on 2010-11-03
+1 to everything said by Rubi1200.

A complete install is always better than Wubi as there is a major performance difference as well as some upgrade problems as suggested above by Rubi.

---

### Post by ctbear on 2010-11-03
Thanks for the replies. I'm currently running 10.10 in VirtualBox, and expectedly it lags every once in a while. I wonder if it is the same with Wubi?
I'm definitely going to try the LiveCD option later on.

---

### Post by wilee-nilee on 2010-11-03
> **ctbear said:**
> Thanks for the replies. I'm currently running 10.10 in VirtualBox, and expectedly it lags every once in a while. I wonder if it is the same with Wubi?
I'm definitely going to try the LiveCD option later on.

Both Rubi1200 and Mark gave very good descriptions. Wubi will run hardly noticeably slower but, if you didn't know this you would never know really. It will run better then the Vbox generally, not knowing the amount of ram you have allocated or the video memory.

Being experienced enough now that multi-booting is not a problem I stay with regular installs and a virtual for XP, and natty narwhale.

---

### Post by tommcd on 2010-11-04
> **Rubi1200 said:**
> 
However, Wubi was never intended as anything other than a means to try something different. As such, there are performance issues in the long term as well as problems with upgrading the install ...

 A +1 on that. This is essentially what the developer of Wubi, Agostino Russo, has said:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
Ctbear,
Try Ubuntu in VirtualBox, or from the Live CD. If you want to install Ubuntu, do a real install to a dedicated partition on your hard drive. Here are 2 great websites to get you started:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for dual booting with Windows:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

