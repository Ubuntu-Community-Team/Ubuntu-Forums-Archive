---
title: "Forced Into Partial Upgrade and Remove DeVeDe"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Bugs318 on 2009-12-07
Hi,

After several days of using devede with no problems, today update manager wouldn't do a proper update and required a partial upgrade which, to complete, necessitated removing devede saying it was out of date.

I tried reinstalling devede from apt-get and the same problem arose on attempting an update.  Should I install the newest version as a .deb from the devede website or is there a better way to get a newer version from the repositories that won't hinder my updates?

Thanks in advance!

BTW: 64-bit 9.10 in case that matters!

PS Just realized this "Intsallation and Upgrades" category was for distro upgrades, not all upgrade problems, but can't find how to switch it... my apologies!

---

### Post by william_nbg on 2009-12-08
I just got the same problem. There most be a conflict with some other package somewhere. I have to go to work, but if I figure anything out later I'll let you know.:popcorn:

---

### Post by rlogan on 2009-12-08
I just tried installing DeVeDe here on 64bit Karmic and it worked fine for me.

I had to install MPlayer before it would work though.

---

### Post by william_nbg on 2009-12-08
Devede works fine on my system too, it just when I run an system update it is removed?

---

### Post by Bugs318 on 2009-12-15
Updates continue to remove devede, so I installed the debian package (a newer version anyway), but now it stops just after starting encoding and says:

"Conversion failed. It seems a bug of mencoder."

Any help either getting the repository version to remain installed or to resolve this problem with the newer version from the devede site would be greatly appreciated!

---

### Post by william_nbg on 2009-12-15
I simply installed the devede package from:

[http://www.getdeb.net](http://www.getdeb.net)

and not it all works seems to work fine.

:P

---

### Post by Bugs318 on 2009-12-15
That is the same version I installed and still the same conversion failure blamed on mencoder.

---

### Post by Bugs318 on 2009-12-15
Something must have been fixed in the update manager, because after several days of continual removal and forced partial upgrades, I now removed the getdeb version and tried reinstalling through apt-get from the repositories.  Now this version works properly and also no longer forces an uninstall and partial upgrade.

Thanks all for suggestions.  I will flag as solved and hope this reversion advice helps others!

---

