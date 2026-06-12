---
title: "Ubuntu hangs at black screen after loading!  HELPPP!!"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by yesjoshyes on 2007-11-23
Okay so I installed Ubuntu and was messing around with it for a little while, mostly audio drivers and what have you.  I rebooted and now it just goes through the loading screen and then to a black screen with a flashing underscore at the top left.

I googled it, and most people suggest to do:

sudo dpkg-reconfigure xserver-xorg

which I've done multiple times, but still no dice.  I'm really starting to get desperate here, and am not sure what to do next.  I need major help!  thanks.

---

### Post by derby007 on 2007-11-23
Press :
> Ctrl Alt F1
Then do :
>cd /etc/X11

See if you have a back-up or a few back-ups of xorg.conf, ie. xorg.conf.backup or whatever, the system might have backed-up a previous xorg.conf if it was changed.
Then :
sudo cp xorg.conf xorg.conf.notworking
sudo cp xorg.conf.backup xorg.conf

ie. make a copy of existing xorg.conf, then replace it witha back-up, you could also get one from the Internet, print it off & make changes.

Note: What graphics card have you?

---

### Post by yesjoshyes on 2007-11-23
I'm not sure my xorg.conf is the problem for a couple reasons.

First, i did that procedure before, and it was to a copy i KNOW was good.  Same result

Second, hitting control f1 or control alt f1 at that blinking screen does absolutely nothing.

However, I can get to the command line through recovery mode.

Any other suggestions?  thanks btw.

---

### Post by derby007 on 2007-11-24
Some of your 'messing around' has fluxed up something. Best to start looking thru some log files. /var/logs. Graphics problems could be in Xorg.0.log.

---

### Post by stinger30au on 2007-11-24
if you have nothing important on the machine, i would scrub it and reinstall.

if you have important gear, boot  of the cd, copy data and reformat and install again.

this time, dont go messing round

---

