---
title: "New Install and Upgrade of 7.04 help"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Yoguess on 2007-05-06
Hi,

Just got my ThinkPad T60P and I was trying to dual install Ubuntu 7.04.
First partition I have XP Pro and second partition Ubuntu 7.04.
I first tried to do a clean install from live CD, but when I tried to boot from live CD GUI never started and I received and error or X failed.

So next I tried to install Ubuntu 6.10 from a live CD which worked. As soon as I restarted I wsa asked to install the updates, then I saw that I can upgrade to 7.04 as well, so I did. 
Everything worked fine until  I rebooted now I get same error about startX failing so no GUI.

I tried StartX which doesnt work, I tried the recoverymode which also doesn't work.

Any ideas? how to fix this or do a clean install?:confused:

---

### Post by pay on 2007-05-06
Post ```
nano /etc/X11/xorg.conf
```If you can. It would probably be easiest to use a liveCD and mount your drive and then post it.

---

### Post by jerrylamos on 2007-05-06
Any chance "safe graphics mode" might get you up?  That uses graphics controller driver VESA which is fairly safe.  If you can get up at all then you can try drivers that are for your graphics controller (do lspci to see what the graphics controller is).

Now I'm running Feisty here (after a bunch of fixes) and have Feisty on a Thinkpad R31 (with fixes) however I'm not sure offhand what would be more useful on Feisty 7.04 than Edgy 6.10.

Some people wireless works better on 7.04, some people it breaks while they run on 6.10 O.K.  The stated goals of Gutsy 7.10 are to smooth over Feisty 7.04 rather than adding new packages so you might want to wait, unless you're looking for bruises like me (I've an early Gutsy level on another computer).

Cheers, Jerry

---

