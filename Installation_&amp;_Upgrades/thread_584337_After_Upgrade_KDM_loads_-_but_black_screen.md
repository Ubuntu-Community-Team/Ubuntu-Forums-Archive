---
title: "After Upgrade: KDM loads - but black screen"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Merritt.kr on 2007-10-20
I started the upgrade to Gutsy.. ran into way too many problems. Had to download some of it through the Adept Updater after it crashed the computer a few times... installed what it had downloaded... etc.... 

Finally managed to get I think 95% of it done. Rebooted... boots up the gutsy kernel, shows splash screen, shows a breif verbose message saying logging in.... this is where I believe it loads KDM, but it only shows me a black screen. 

Waited, nothing. Rebooted, again, nothing. Switched back to the .20-15 kernel and it boots into KDM successfully and I can log into the system. Though in that kernel everything is going reeaaallly slow, as if it was a 10 year old computer (it's less than a year old)

Any advice?

I do have an ATI card (x1400) and am wondering if this could be why it's frelled. Was however working before upgrade, and still loads (if slow) on the old kernel.


Thank you in advance for any advice!


EDIT:
Reconfigured xorg.conf to use vesa drivers. Resolution sucks, doesn't work great, but I'm in. The new (and hopefully improved) ATI driver should be out in a few days.. I can stick it out til then and hopefully it will fix it all!

---

### Post by myoungf1 on 2007-10-23
Go here;

[http://kubuntuforums.net/forums/index.php?topic=3087650.0](http://kubuntuforums.net/forums/index.php?topic=3087650.0)

This worked to get my bootsplash working again.  I have it set to see the text but should work to get the boot splash up and running as well.

---

