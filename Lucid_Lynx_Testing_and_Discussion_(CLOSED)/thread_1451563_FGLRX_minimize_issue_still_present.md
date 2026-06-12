---
title: "FGLRX minimize issue still present?"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by !@!@! on 2010-04-10
Hi Ubuntu community. :)

After fresh installing to 10.04 b2, and getting fglrx set up, I found out the minimize issue is still present (lag when unminimizing & maximizing windows). In Karmic is was fixable by adding the no-backfill ppa, but I've Google'd and Google'd and it seems there is no such ppa for Lucid. Could some one help me out?

Thanks.


[SIZE="5"]**Solution-**
The old patch made for xorg 1.6.3 still works on 1.7.6.
To use it, follow the instructions here: [http://ubuntuforums.org/showthread.php?t=1434064&page=12](http://ubuntuforums.org/showthread.php?t=1434064&page=12) (thanks uBeer!)

If you are very lazy and trust me with root access, you can install my amd64 build.

[http://www.mediafire.com/?nehan2tzmty](http://www.mediafire.com/?nehan2tzmty)[/SIZE]

---

### Post by dcstar on 2010-04-10
> **!@!@! said:**
> Hi Ubuntu community. :)

After fresh installing to 10.04 b2, and getting fglrx set up, I found out the minimize issue is still present (lag when unminimizing & maximizing windows). In Karmic is was fixable by adding the no-backfill ppa, but I've Google'd and Google'd and it seems there is no such ppa for Lucid. Could some one help me out?


What "issue"? I use the ATI fglrx driver and it works fine.

Many others also use this driver, and I haven't noticed any posts about this.

---

### Post by !@!@! on 2010-04-10
> **dcstar said:**
> What "issue"? I use the ATI fglrx driver and it works fine.

Many others also use this driver, and I haven't noticed any posts about this.
[quote=OP]I found out the minimize issue is still present (**lag when unminimizing & maximizing windows**)[/quote]

This has been a problem for many people since Jaunty.

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill) is the general fix, but they do not have packages for Lucid.

Here are the same problem in karmic & jaunty
[http://newyork.ubuntuforums.org/showthread.php?p=7553081](http://newyork.ubuntuforums.org/showthread.php?p=7553081)
[http://swiss.ubuntuforums.org/showthread.php?t=1259817](http://swiss.ubuntuforums.org/showthread.php?t=1259817)

---

### Post by dcstar on 2010-04-11
And where is the bug report for the people who make the ATI driver to actually resolve it?

This looks like (yet) another issue where instead of following the proper procedure to actually get it fixed by the people who have the power to do this, the "resolution" is some bogus workaround that requires continuous revision for every version change.

---

### Post by Kazade on 2010-04-11
> **dcstar said:**
> And where is the bug report for the people who make the ATI driver to actually resolve it?

This looks like (yet) another issue where instead of following the proper procedure to actually get it fixed by the people who have the power to do this, the "resolution" is some bogus workaround that requires continuous revision for every version change.

Trust me, the ATI people know about this (ATI devs visit the Phoronix forums a lot where this is discussed over and over). Anyway, ATI only have an "unofficial" bug tracker, the bug is reported on Launchpad, complete with 414 comments: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

This issue is the reason I've been using the open source drivers, it's been around for over a year now and ATI haven't pulled their finger out to fix it. :(

---

### Post by !@!@! on 2010-04-11
> **Kazade said:**
> Trust me, the ATI people know about this (ATI devs visit the Phoronix forums a lot where this is discussed over and over). Anyway, ATI only have an "unofficial" bug tracker, the bug is reported on Launchpad, complete with 414 comments: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

This issue is the reason I've been using the open source drivers, it's been around for over a year now and ATI haven't pulled their finger out to fix it. :(
Exactly.

Since ATI has no intention to fix it, a "bogus workaround" is all I can ask for. :| And since I can't find one for Lucid, I'm here.

---

### Post by uBeer on 2010-04-11
Here is a work around:
[http://ubuntuforums.org/showthread.php?t=1434064&page=12](http://ubuntuforums.org/showthread.php?t=1434064&page=12)

One or 2 pages further I have posted a little script that compiles and installs the 'fixed' xserver.

---

### Post by !@!@! on 2010-04-11
> **uBeer said:**
> Here is a work around:
[http://ubuntuforums.org/showthread.php?t=1434064&page=12](http://ubuntuforums.org/showthread.php?t=1434064&page=12)

One or 2 pages further I have posted a little script that compiles and installs the 'fixed' xserver.
Compiling now!

We will see if it still works... wish me luck. :P

---

