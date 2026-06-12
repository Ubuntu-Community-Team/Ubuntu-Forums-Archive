---
title: "Copy packages from one machine to another?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by maestrobwh1 on 2007-10-13
Not sure if this is the right place to post, although I guess I could have used "General."  

I have several machines that are not on a common network and want to upgrade my Gutsy partition, as I have waited about a month since I have done it last because I finally had a stable system that I was happy with.  Since the release candidate is out and is pretty much past the experimental phase now, I would like to do a update && safe upgrade on the machine that is on the fastest network, open the var/cache/apt/archives/ copy the files to a pen drive , then simply copy those files to a new machine.  Granted, some won't be needed and a few others will be when I do an upgate && upgrade.

I did this before and apt [adept, synaptic, aptitude] on the other machine did not recognize the files there and went to the net for all of them.  I kind of figured this would happen:-)  But it was fast and easy enough to try.

I am sure there is a way to rebuild the package list, but after researching apt and dpkg, I can't find the specific instructions.

I suppose I could have done a dpkg -i *.deb && dpkg --configure -a on the pen directory, but that seems messy and could lead to problems because it would install everything.

---

### Post by ThrobbingBrain66 on 2007-10-13
I would download the alternate cd for the release candidate and use that to upgrade:
[https://help.ubuntu.com/community/GutsyUpgrades?#head-93ac2e597b9e0c5ff78111d4fd2bbe34a35799c7](https://help.ubuntu.com/community/GutsyUpgrades?#head-93ac2e597b9e0c5ff78111d4fd2bbe34a35799c7)

This will only upgrade packages that are on the cd, so it won't include packages in universe or multiverse.  So for your application, the DVD might be the best way to go.

---

