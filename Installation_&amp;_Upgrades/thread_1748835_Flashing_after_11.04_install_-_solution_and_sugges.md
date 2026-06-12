---
title: "Flashing after 11.04 install - solution and suggestion"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by snaggle145 on 2011-05-04
Hi,

I updated from 10.10 to 11.04 to discover my desktop icons flashing intermittently over the desktop background, with no Unity or other menus or panels.

The solution was to go to recovery mode, drop to root shell, and use (from memory):
Xorg -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
X
to setup my graphics card. At this point, X told me my graphics card wasn't up to running Unity and put me into Classic mode. Tada! Usable system. However, in the mean time in an attempt to solve my problem I've spent a lot of time on this and performed a complete re-installation.

I'm the only user of my computer and I had the system set to automatic login. It seems that if I'd had the login screen turned on I could have easily selected "classic" at this point and solved the problem. Unfortunately no such option or warning was given at any stage in the installation process. Interestingly, the Live CD ran just fine, defaulting to Classic mode without giving an explanation.

**So my point is this** - wouldn't it be nice if the update or the installation CD recognised that your graphics weren't up to scratch, told you, and turned Classic mode on for you automagically? Is this the place to suggest such things?

lspci | grep VGA
01:06.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro NVS 280 PCI] (rev a1)

---

### Post by mörgæs on 2011-05-04
Hi, welcome to the fora. 

Here
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)
you will see a forum for 11.10-development after a few days. There you can post your idea (which is a good one).

---

### Post by snaggle145 on 2011-05-29
Hi mörgæs,

Thanks for the reply  :)

I've taken a look at that link but no 11.10 forum just yet. I'll keep checking back.

My point was more with regards to the 11.04 distribution though. My understand is that even though 11.04 is "released", tomorrow's installation will differ from today as bug fixes etc are made... (correct me if I'm wrong). So wouldn't it be nice to save someone with a crummy graphics card the distress of trying to work out what went wrong by modifying the installation or upgrade process just very slightly? Is there anywhere to suggest this for 11.04?

Cheers,
 Simon

---

### Post by mörgæs on 2011-05-29
Sorry, wrong link. The correct one is here:
[http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403)

11.10 does not by default have the choice between Gnome and Unity, just Unity, so there is no option of switching.

My own 'switching' means going to Xubuntu, when support for 10.10 is running out :-)

---

