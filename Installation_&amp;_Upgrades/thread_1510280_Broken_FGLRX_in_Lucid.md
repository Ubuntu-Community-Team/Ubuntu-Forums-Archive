---
title: "Broken FGLRX in Lucid"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2010-06-15
Just in case this is still an issue: [http://ubuntuforums.org/showthread.php?t=1443078](http://ubuntuforums.org/showthread.php?t=1443078)

The reason that you can't install FGLRX is because FGLRX will not support your card.  So, you have to either use Hardy Heron (8.04 LTS and FGLRX) or the opensource drivers in Lucid (10.04 LTS).

If you've tried to install FGLRX and it failed and THEN you try to "install" the opensource drivers, it is likely that you have all sorts of conflicts -> system crash.

Ubuntu is smart enough to detect if your hardware can run proprietary binary drivers, so you shouldn't have tried to install FGLRX.  Oh well, the past being the past, you now have to ensure you REMOVE ALL traces of the broken FGLRX install.  Don't worry, you are not alone - see this wiki: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Then you should be good to go.  If you've edited your xorg.conf file, you may have to regenerate it, or simply rename it (same as deleting, but recoverable).

After you get the opensource drivers to run, you could try out the latest and greatest versions (several "comfort" levels - read the PPA description) here (just this one): [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers) , **or** if you don't want to get too crazy, just try the next two (both, together) -> here: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only) and here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Good Luck,
CH

---

