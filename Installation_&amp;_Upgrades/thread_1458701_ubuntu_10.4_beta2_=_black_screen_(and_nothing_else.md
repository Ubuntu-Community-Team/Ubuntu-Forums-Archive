---
title: "ubuntu 10.4 beta2 = black screen (and nothing else)"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by guano on 2010-04-20
Hi all, today I just tried a liveCD of lucid beta2. Unfortunately,just like with alpha5, all I got was a black screen, and nothing else. I tried to switch to terminal with crtl-alt-F1,F2... but it seems to be disabled (why?)

I,m running 9.10 on a Samsung r20 notebook, with an ATI-Radeon Xpress 1250.

any help will be much appreciated, since 10.4 is about to be released, and I really want to upgrade.

---

### Post by dabl on 2010-04-20
One of the "F" keys is "Safe Graphics" mode -- is it F5?  Try that.

Also, you'll be needing this:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by guano on 2010-04-20
You mean keeping F5 pressed during boot? No change. After the initial screen (try without installing..).. all goes black.

Also, the proprietary drivers won't work for me, since the support for my card model was descontinued by ATI. (and due the fact that if I can't get any thing besides the black screen, including ttys, there's no way to change the driver)

cheers

---

### Post by dabl on 2010-04-20
Have you tried any of the video framebuffer boot options, like vga=785?  When Live CD presents the first menu, press F6, then enter the option vga=785, then press Enter.  Other framebuffer options are here:  [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

### Post by guano on 2010-04-22
thanks dabl, but still not working, although this time I got stuck in some bug (msg: BUG! CPO0 stuck for XXs...) and couldn't go any further..
I hope the devs fix this by release date.

---

### Post by dabl on 2010-04-22
The devs are not supposed to be fixing anything on 10.04, at this point, although there's apparently an xserver-xorg problem that they have to deal with:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODE3MA)

So if your video isn't working today, it's not going to work next week either.  :(

Can you get to the logs at /var/log and maybe find out more about that "bug" message?

---

