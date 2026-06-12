---
title: "Updates are not being installed"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by auscanstom on 2011-02-09
Hi all,

I am a recent convert to Ubuntu and have the Ubuntu 10.10 version installed on my computer. All has been going on well until I installed FreePops. Since then, when I check for updates through the Update Manager, it shows that it's searching for updates but then it brings up a pop up stating the following "Failed to download repository information" and under this the following is mentioned "W:Failed to fetch [http://ppa.launchpad.net/marco/freepops/ubuntu/dists/10.10/main/binary-i386/Packages.gz](http://ppa.launchpad.net/marco/freepops/ubuntu/dists/10.10/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead."
I have removed FreePops from Synaptic Package Manager but the above mentioned error still appears and updates cannot be installed. I have rebooted my computer also and performed the updates but the error still appears. Can someone help to have this resolved?

---

### Post by kansasnoob on 2011-02-09
Open Update Manager and click on the Settings button in the lower left hand corner, then click on the Other Software tab in the Software Sources gui. Then look for the freepops entry, something like this:

```
http://ppa.launchpad.net/marco/freepops/ubuntu/dists/10.10/main/binary-i386/Packages.gz
```

Make sure it's unchecked, then close the Software Sources gui and you'll be asked to Reload. Do so and see what happens.

---

### Post by auscanstom on 2011-02-09
> **kansasnoob said:**
> Open Update Manager and click on the Settings button in the lower left hand corner, then click on the Other Software tab in the Software Sources gui. Then look for the freepops entry, something like this:

```
http://ppa.launchpad.net/marco/freepops/ubuntu/dists/10.10/main/binary-i386/Packages.gz
```

Make sure it's unchecked, then close the Software Sources gui and you'll be asked to Reload. Do so and see what happens.
Thanks a lot for the response. It did the trick. That was a quick fix. Really impressed with the support received.

Thanks again.

---

