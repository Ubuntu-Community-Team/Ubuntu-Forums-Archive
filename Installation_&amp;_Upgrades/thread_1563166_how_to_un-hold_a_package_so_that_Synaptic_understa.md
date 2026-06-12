---
title: "how to un-hold a package so that Synaptic understands"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2010-08-28
(64-bit LucidLynx)
So i followed the instructions here, [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) on how to hold (or pin) and unhold a package.

For example:
echo doggy hold    | sudo dpkg --set-selections
echo doggy install | sudo dpkg --set-selections

work beautifully with regards to apt-get, aptitude, Synaptic, and Update Manager knowing whether to install or be grayed out,
except Synaptic still shows this package with a grayed out exclamation mark. 

"Mark all Upgrades" will mark this package and install, but the 
grayed out exclamation mark icon does not change to the normal green square.
So Synaptic is partially behaving, although it still thinks
you are forcing the non-default version to be installed.

I've reloaded, shut down Synaptic and restarted.
I have even Synaptic-->Packages-->Lock, then unlock.
But that particular status icon does not go away.

Where does Synaptic store this little gem of information such
that I can squash it?

This file, /var/lib/synaptic/preferences, is currently empty, and I think didn't exist at all until i did the Synaptic-->Packages-->Lock/UnLock.

---

