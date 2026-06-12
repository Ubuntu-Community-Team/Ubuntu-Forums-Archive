---
title: "PhotoShop CS2 after installation error"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by ShereKhan on 2008-05-04
Hello,

A little intro shouldn't harm anyone :)
I'm trying hard to switch to UBUNTU. Some of my friends are using it already and I found also it's a great OS. As a previously Windows user everything is new for me and I don't feel able to resolve one of the main issue for me. I could do it with searching as I did so far, but this is one which is making me the most trouble and can't wait anymore to resolve it by my self.

Trying to run PhotoShop CS2 on UBUNTU using Wine latest version, whatever it is the latest :)

Error message I get after starting PhotoShop is:
*An error has been detected with required application library and the product cannot continue. Please reinstall the application.*

I'm not sure if this could be resolved by reinstalling PhotoShop, so far I understood that many issues with not working sound, graphics and other application is resolved by downloading additional libraries.

p.s. my apologizes to moderators if my thread is not in the right category, saw other similar thread in this one...

---

### Post by z0mbie on 2008-05-04
Here's a helpful place to look for [Photoshop CS2 support]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631").

If you have a little patience by June we're expected to have CS2 working under Wine. Google is involved in the process of making Photoshop CS2 major goal for the Wine 1.0 stable release in June.

---

### Post by ShereKhan on 2008-05-04
Thank you very much z0mbie,

It works for me...

I would like just to say again...

**The following error message after starting PhotoShop CS2:**
An error has been detected with required application library and the product cannot continue. Please reinstall the application.

**Can be resolved with:**
The workaround is to give the command:

$ sudo sysctl -w vm.mmap_min_addr=0

This fixes the problem until the next time you reboot. (It also reduces security slightly.)

To avoid having to give that same command every time you reboot, also edit the file /etc/sysctl.conf, e.g. with the command

$ sudo gedit /etc/sysctl.conf

and change the line that reads:
vm.mmap_min_addr = 65536

to:
vm.mmap_min_addr = 0

That will apply the workaround for you when the system starts.
Distributions may wish to include this workaround when they package wine.

**For more info visit:** [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by D. Satoshi on 2008-07-05
So... I've taken your advice and my desktop no longer loads up.

Every time I start Ubuntu, it loads it up, and instead of taking me to the graphical user login screen, the login prompt just shows up underneath all the run code (as if I'm running DOS or Terminal).

Needless to say I need a fix, as I am crying and dying inside XD

But seriously, I am quite new to Ubuntu and have looked all over for a solution. I figure that this would be the best place to ask, as it was by this method (the suggestion above) that I have rendered my desktop "unappearable".

So please... if anyone has a solution, it would be greatly appreciated.

---

