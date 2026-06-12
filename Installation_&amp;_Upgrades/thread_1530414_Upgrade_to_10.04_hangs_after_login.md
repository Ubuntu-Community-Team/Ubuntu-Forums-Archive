---
title: "Upgrade to 10.04 hangs after login"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Relysis on 2010-07-13
I just upgraded from Karmic, and the upgrading seemed to go smoothly.  Upon restart the login screen comes up as normal and accepts my user name/pw.  Then it fades to a strange white cloud dream looking thing and hangs.  I don't see a cursor or my desktop.  I can get to console from there, but I don't know how to fix it.  I have an old dell laptop that ran Karmic perfectly.  It has an ATI X300 graphics card, but I was using the open driver.

Any suggestions?

---

### Post by Relysis on 2010-07-13
I've been working on this all afternoon, and could really use some help.  I've tried everything I've found on the forums, and nothing works.  Even a small suggestion would help.

---

### Post by Relysis on 2010-07-14
Final pre-windows 7 bump.  Just got an iphone, so I either need Windows or Lucid for syncing.  I was really hoping for the latter.

---

### Post by Relysis on 2010-07-15
I never found a solution to this, so I did a clean install.  It booted up this time in my maximum resolution (1920x1200).  Everything was working fine, so I went to change the resolution to 1680x1050, which is the resolution I was using before the upgrade.  Immediately, the same thing happened.  The screen faded to a white-ish cloud shape.  Both resolutions are 16:10.  I can't explain this.  I'm not using any proprietary driver.  I guess the moral of the story is to stay away from 1680x1050, but I'd like to know why, and if I should file a bug report.

EDIT: All the other 16:10 resolutions cause this to happen, other than the 1920x1200 that Ubuntu defaults to.  I haven't tried the others, since this is a widescreen monitor.  This resolution is way too high for me, even with enlarged fonts, etc.

---

### Post by dioxholster on 2010-07-15
maybe its because of the graphic card? like doesnt that need drivers? and i think its best to use maximum resolution.

---

### Post by Relysis on 2010-07-16
I'm sure it's the graphics card.  It's legacy from Ati, but the open driver was working fine in 9.10.  While everything is sharper at higher resolutions, I can't read anything at 1920x1200 on a 15" screen.

Anybody else using the X300 with 10.04?

---

### Post by dino99 on 2010-07-16
remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

add this ppa to synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade, then check driver activation:

system -> admin -> hardware driver

*** ATI dropped fglrx driver support for that chipset over a year ago. ****

---

### Post by Relysis on 2010-07-16
Thanks for the reply.  Unfortunately, the X300 is no longer supported like you said, so there is no proprietary driver to be used.  I removed xorg.conf and added that repository.  It installed several new updates, so I tried to change the resolution again.  Unfortunately, the same thing happened and I had to boot into safe mode.  

Thanks for the repo though.  If there's any chance of a fix coming down the line through that, I'll keep it updated.

EDIT: Now I can only boot into Ubuntu through safe graphics mode.  Is there any way to change the root graphics configuration while in this mode?  I changed it to the working resolution in this mode and rebooted, but the regular login still hangs.  Of course when I tried to change the configuration file when loading safe mode, it wouldn't let me select it.

---

