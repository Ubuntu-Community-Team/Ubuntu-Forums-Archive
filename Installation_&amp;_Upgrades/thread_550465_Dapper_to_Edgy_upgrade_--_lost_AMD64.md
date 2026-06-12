---
title: "Dapper to Edgy upgrade -- lost AMD64?"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by hardmath on 2007-09-13
At the end of last month I used the official method (gksu "update-manager -c") to initiate an upgrade to Edgy Eft from an AMD64 bit version of Dapper Drake.  This is on an HP L2000 laptop.

Although the basic process seemed to go smoothly enough using the update manager, I see a couple of strange things now.

Quirk 1 is that the splash screen is now in grey scale rather than color.  I could play around with the boot options, but I don't know what file has those in it.  I did try reinstalling usplash, but it did not seem to make any difference.

Quirk 2 is more interesting, in that the new kernel (as seen in the boot options and from uname -r in a terminal instance) is 2.6.17-12-generic.  The previous boot option reads 2.6.15-28-amd64-generic, and I confirmed that if I boot into that old option, uname -r gives that string as well.

So, did I lose the 64bit kernel when I upgraded using the "official method"?  Or is there no longer a distinction in the uname strings?  The gist of this was already raised in an unanswered thread here from another forum member:

_[http://ubuntuforums.org/showthread.php?t=407805](http://ubuntuforums.org/showthread.php?t=407805)_

Thanks in advance, hardmath

---

### Post by rsambuca on 2007-09-14
You still have the 64bit kernel after upgrading.  Ubuntu dropped the different kernel designation names after dapper, but the generic one has been compiled to make use of SMP and all that fun stuff.

---

### Post by hardmath on 2007-09-15
Thanks, rsambuca.  Quirk 1  (grey-scale splash screen during kernel boot) turns out to be a _[known bug on AMD64](https://bugs.launchpad.net/ubuntu/+source/usplash-theme-ubuntu/+bug/67545)_ hardware.

regards, hardmath

---

