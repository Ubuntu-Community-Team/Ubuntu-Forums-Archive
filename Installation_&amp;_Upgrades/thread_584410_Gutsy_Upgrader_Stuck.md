---
title: "Gutsy Upgrader Stuck"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by sdlvx on 2007-10-20
Alright, so, my upgrade isn't going very smooth.  I'm using Kubuntu, going from 7.04 to 7.10.

Firstoff, I had wxdial or something enter an infinite loop or something.  It just sat there using 100% of a core.  So, I just closed the process for the wxdial configure from ksysguard.

That fixed it.  Next, I get a problem about Ubuntu-Minimal not being able to be installed.  I'm assuming this is just a meta package, and I'm going to be ok.  Will I?  I have a lot of important stuff on this thing.

Lastly, and this is what is really scaring me, the updater thing got stuck at mtr-tiny or something.  So, I cancelled the GUI upgrader, and I wanted to see if there was another way to continue, as I was at 57% and I figured a reboot would be a borked system.

So, I ran sudo dpkg --configure -a, and it seems like it's upgrading.  Is there anything I should be doing or any extra things I have to run or do to make sure my install doesn't go borked?  I'd sure HATE to have to rummage through my old kubuntu install and try and salvage all my important school stuff.

EDIT: it finished, and it's telling me errors in:

alsa-base (i manually installed and compiled version 15
ubuntu-minimal
lib-apache2-mod-php5
php5-mysql
php5-gd
phpmyadmin
php5-mcrypt

Does someone want to help me out here and tell me if there's anything I need to do before I do what is terrifying me and reboot to my death?

---

### Post by sdlvx on 2007-10-21
After much frustration with fglrx, that method seems to have worked.  At least, I'm on the new kernel, lol.  Is there someway to tell that it worked?

Adept tells me I need to upgrade, yet I am using the new kernel.

---

