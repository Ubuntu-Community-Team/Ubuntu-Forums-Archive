---
title: "Update to 15.04 from 14.04 fails due to file size mismatch"
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by wes11 on 2015-10-15
I was trying to update to 15.04 from 14.04 but the install fails due to file size mismatch:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+15.04.20150415.1-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+15.04.20150415.1-0ubuntu2_all.deb) Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/friends/friends-facebook_0.2.0+14.10.20140714.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/friends/friends-facebook_0.2.0+14.10.20140714.2-0ubuntu1_all.deb) Size mismatch

I would appreciate any help otherwise I will stick with 14.04 which is very nice.
Thanks,

Wes

---

### Post by deadflowr on 2015-10-15
I'd say stick with 14.04, because to get from 14.04 to 15.04 you would need to go through 14.10, which hit end of support a while ago.
Double bumps with upgrades are timid enough as they are, but to have a middle bump be end of life is probably more so.

Of course the alternative, if you truly want to move up to 15.04 would be to do a re-install of a fresh 15.04.
(But, really, I'd wait a few weeks and do a fresh install of 15.10 instead; 15.04 will only be supported until the end of this year)
And of course, that is what you might have been trying, but you weren't clear on the method of the upgrade.

---

### Post by v3.xx on 2015-10-15
You cannot upgrade direct to 15.04, you must first upgrade to 14.10 and then in a few days 15.10 will come out and require you to upgrade again.

14.04 is a LTS release and can be upgraded direct to the next LTS release (16.04) when it comes out six months from now.

What upgrade method are you using?

---

### Post by ajgreeny on 2015-10-15
Why upgrade to 15.04?  It will lose support in January 2016 and you would then need to upgrade again to 15.10.  You can not upgrade in one step from 14.04 to 15.04 using the update-manager but would have to do it in two moves, the first of which would be to 14.10 which is already unsupported so the repos for that are already archived and not available in the usual way.

As 14.04 is "very nice" as you called it, I would recommend you stay with it and then upgrade or clean install the next LTS version, 16.04, which is only 6 months away.

Many users, including me, use only the LTS versions as our working OS, though I do always install the intervening versions as virtual systems in VirtualBox just to have a good look and play.

EDIT:
Between starting and submitting my post two others had already said more or less what I did, ie, stick with 14.04, but it's your machine so do what you prefer.  We are here to help and you do now understand the difficulties of what you proposed.

---

### Post by wes11 on 2015-10-16
Well, I was using the default Ubuntu upgrade mechanism and since it notified me that an upgrade was available...
Either way, I guess I will stay using and learning 14.04 for a bit longer.  I do appreciate your help and advice, Thanks.

---

### Post by Bucky Ball on 2015-10-16
> **wes11 said:**
> Well, I was using the default Ubuntu upgrade mechanism and since it notified me that an upgrade was available...
Either way, I guess I will stay using and learning 14.04 for a bit longer.  I do appreciate your help and advice, Thanks.

Good plan. LTS releases actually have five years support while interims, like 15.04 and 15.10, nine months. Good luck. :)

---

