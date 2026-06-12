---
title: "I'm helping a friend..."
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Garjon on 2008-09-10
She just got a Toshiba L305-S5875 laptop. Since she's not stuck in her ways about operating system, and primarily using it for school; I was going to install 8.04, with a shipped CD. But no matter what option I choose on the boot menu, I get "udevd-event[1537]". Anyone know what this mean, and more importantly, how to fix it? 

She's got Vista on it now, can't stand it, and she gets a little jealous seeing some of the things I can do on my Ubuntu install.

---

### Post by Crafty Kisses on 2008-09-11
What are the system specs?

---

### Post by Sef on 2008-09-11
Try updating her Vista and see if that takes care of her problem.  

Does the message say anything else?

Update:  >  I choose on the boot menu, I get "udevd-event[1537]

By boot menu, you mean the one on the Live CD?   If that is what you mean, you may need to use the alternate cd.   There is a problem installing to some [Toshibas]("http://ubuntuforums.org/showthread.php?t=793195").  To get the alternate cd, just check the box below the green Start arrow at the [Ubuntu download site]("http://www.ubuntu.com/getubuntu/download").

---

### Post by Garjon on 2008-10-08
Thanks Guys, got it installed with the alt CD, but now there's another issue.
It's dual booting Vista and Ubuntu. 
Vista finds the network card, ID's it as an Atheros AR5007EG, and uses it fine.
Ubuntu ID's it as (with lspci | grep theros) a AR242x, and it doesn't show up as a wireless option in nm-applet, and I don't know enough to get it to work with (iw/if)config. I tried even compiling and installing Madwifi, but that seems to be getting nowhere.
Help?

---

### Post by Mike_Longbow on 2008-10-12
I got an Atheros AR5007eg, too. To get it to work I just followed this instructions (you need to be connected to the internet):

First of all, go to System > Administration > Hardware Drivers and make sure "Atheros Hardware Access Layer (HAL)" is unselected, then:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz

tar xfz madwifi-hal-0.10.5.6-r3861-20080903.tar.gz

cd madwifi-hal-0.10.5.6-r3861-20080903

make

sudo make install
```

Now reboot, and that's it.

I hope that helps.

---

### Post by Garjon on 2008-10-15
That did it! Works now!
Thanks a bunch!

---

