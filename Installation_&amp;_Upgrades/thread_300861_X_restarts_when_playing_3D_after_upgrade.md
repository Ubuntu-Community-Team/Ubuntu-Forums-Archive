---
title: "X restarts when playing 3D after upgrade"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by Tachyon_ on 2006-11-16
I upgraded last night, it contained linux restricted-modules (which I think are related to this). Now, when opening frozen-bubble, slune, ppracer... screen goes black and logs me out.
 I think I should reinstall nvidia drivers, I did so by removing, then reinstalling, running the commands descripted in the help. It were no help.
 After installing, now I get the wonderfull gray splash, so drivers should be working, right? If I change back to "nv" in the xorg.conf, my cpu load jumps  100% (hard to tell, dual core...) so that it laggs every 5 sec.

Kubuntu edgy with nvidia, please help, Im quite sure this is related to upgrade.

EDIT: I used nvidia-beta driver (that's not offical repository if I remember correctly?), but when trying to reinstall, I dont think that is beta. Im not using XGL/Beryl or anything.

---

### Post by Tachyon_ on 2006-11-16
I got it to work, the bad thing is, that I don't have any idea how... :)

I googled for sites, saw info about Beryl. there was a story about how ubuntu repo updates considering restricted modules would not work with their nvidia, so I should install old version. (or not update on the first place). Their drawback method did not work, so I figured out howto do it myself.
Next thing I knew that X wouldnt start, complaining about X version incompability or something. I installed the very lates again, and thought :(. But what, then, it worked! Just that my widescreen laptop didn't exactly scale Frozen Bubble to fullscreen. Then I ran dpkg-reconfigure xserver-xorg, and checked the 1024x768 box, it worked.

Now everything is back to normal. I think I update my information about the compability before updating anything else.

---

