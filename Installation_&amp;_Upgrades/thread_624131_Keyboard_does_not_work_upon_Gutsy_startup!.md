---
title: "Keyboard does not work upon Gutsy startup!"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by checho4 on 2007-11-26
My keyboard on my Inspiron 1501 is no longer working in Kubuntu Gutsy 64bit.  Everything seems to load up fine.  At the login screen, I can press alt+ctrl+Fx to open up a command prompt and run tasks there.  However, as soon as I log into KDE, my keyboard stops working.

Also, using the on-screen keyboard (and clicking on each key with my mouse), I can execute "ping google.com" successfully, showing me that I AM connected to the internet.  However, when I try to log onto the internet, no network is found.

Also, when I try to shutdown, I get an error that says something along the lines of:
Unmounting local filesystems
"/" device is busy

The shutdown process just hangs there.


Any help is GREATLY appreciated!!!  Thank you!

---

### Post by checho4 on 2007-11-26
I think I found the problem, though I don't know WHY it's the problem.  I set kNetworkManager to NOT startup automatically, and then I restarted [using the power button].

Upon logging in, everything worked.  Then, I started kNetworkManager to connect to the internet.  That worked.  I rebooted [via KMenu => Restart] and everything went smoothly.  Could it be a bug in kNetworkManager?

---

### Post by checho4 on 2007-11-28
Well, after messing with it some more, I found that it is my restricted driver for my wireless card.  On my Inspiron 1501, I used the bcm43xx-fwcutter, which would cause network-manager to do something funky.  It would lock up my keyboard and would not let me shut down, stating that " / is busy ".  After removing the restricted driver, everything seems to be working alright again.

I guess I'll just have to go back to the ndiswrapper method until this driver is fixed.

---

### Post by checho4 on 2007-11-28
Well, after messing with it some more, I found that it is my restricted driver for my wireless card.  On my Inspiron 1501, I used the bcm43xx-fwcutter, which would cause network-manager to do something funky.  It would lock up my keyboard and would not let me shut down, stating that " / is busy ".  After removing the restricted driver, everything seems to be working alright again.

I guess I'll just have to go back to the ndiswrapper method until this driver is fixed...

---

### Post by clong83 on 2008-01-15
I just had a similar keyboard/mouse problem.  My keyboard would "stick" keys occasionally, making typing difficult.  ALso, my mouse would go out of control and click on things at random sometimes.  It was quite a nightmarish bug.  But I removed bcmxx-fwcutter and all my problems were solved.  But, like you, I can't think of a good reason why wireless drivers of all things would screw with my keyboard.

Does anybody have any clue as to WHY bcmxx-fwcutter might cause input problems like these?  Any input would be appreciated...

---

