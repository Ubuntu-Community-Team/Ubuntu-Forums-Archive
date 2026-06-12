---
title: "&quot;Unable To Set System Clock&quot;"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by linux4me on 2007-10-27
I notice after upgrading to Gutsy while grub is loading everything I get:

> unable to set system clock

Once in gnome, the clock is there and appears to be working fine.

I never got this error in Feisty. I searched the forums but couldn't find anything relating to this error. Is there a fix?

---

### Post by linux4me on 2007-10-28
I may have found a fix for this [in this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43661") It got rid of the error message on boot, but only time will tell if my clock is behaving. 

If you're having the same problem, you might try editing /etc/init.d/hwclock.sh and adding the parameter "--directisa". Here's how:

First open the file hwclock.sh for editing by opening a terminal window and typing:
> sudo nano /etc/init.d/hwclock.sh

Scroll down until you see the line:
> HWCLOCKPARS=

Change it so that it looks like this:
> HWCLOCKPARS=--directisa

Push Ctrl+O (as in Open, not a zero) to write the file, then press Enter to keep the existing name.

Push Ctrl+X to exit nano.

Restart and look for the error. For me, it was gone, though the line "Setting system clock" appears twice. 

If someone who knows something about this could comment, that would be great!

---

### Post by prem1er on 2008-04-09
No good for me.  I'm running Gutsy and I still get the error after the suggested changes.

---

### Post by bolted on 2008-07-19
Try doing the same to the /etc/init.d/hwclockfirst.sh if it exists on Ubuntu. I had to do this on Debian Lenny (not on earlier Debian versions, so I guess it's something new)

[http://blog.dhampir.no/hardware-clock-fix-debian-mac-mini](http://blog.dhampir.no/hardware-clock-fix-debian-mac-mini)

---

