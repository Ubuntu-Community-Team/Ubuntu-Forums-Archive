---
title: "Lost X while updating to 10.10 beta"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by laserbeam on 2010-09-06
Hello everyone.
Last night I updated to Maverik beta, but when I rebooted after it finished I pretty much found out X got screwd.

Basically, it 'Can not load module "fglrx"', so as far as I can tell, the driver got busted.
Ok, I tried reinstalling the driver but it kept going wrong about the latest kernel installed during the update (2.6.35-19), so I removed this, stuck to my old one (i think 2.6.32-24 but I'm not sure) and driver installation apparently went through flawlessly, but X still can't load that module? any ideas?

Other things i reinstalled and reconfigured: fglrx-amdcccle, fglrx-modaliases, xserver-xorg-video-ati and that's about it I think.

I currently have a ATI HD4850 card in my box, which worked flawlessly until the update, so other drivers and such should exist.

PS If you need any other details like logs and stuff, please tell, I really don't know which ones I should add here.

---

### Post by mörgæs on 2010-09-06
This is probably a better forum:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by laserbeam on 2010-09-06
Oops... yeah... Looked around but didn't see that forum, anyways thx, found the problem... apparently fglrx doesn't yet work with Xorg 1.9 (should be fixed in a couple months though).

I'll probably just backup and reinstall lucid, and mark this thread as solved...

---

