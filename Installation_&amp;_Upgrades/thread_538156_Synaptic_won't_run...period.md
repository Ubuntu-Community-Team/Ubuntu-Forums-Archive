---
title: "Synaptic won't run...period"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by roachkv on 2007-08-29
Synaptic won't run from the desktop or terminal (w/ or w/o sudo). When I try to run it in a terminal window I get "Segmentation fault (core dumped)".  From the desktop, it just closes w/ no error message.

This occured after installing samba from within synaptic.

Any thoughts???

---

### Post by be4truth on 2007-08-30
Please read this 2 posts and see if they help. Otherwise come back.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424")

[http://ubuntuforums.org/showthread.php?t=472511]("http://ubuntuforums.org/showthread.php?t=472511")

---

### Post by mckryptyk on 2007-08-30
Are you running Gutsy Gibbon ? If so:

Then you are running a developmental version of ubuntu that will have bugs that need working out.
You may need to update to a non-segfaulting version when it is available if that is the case.

You may have to use aptitude to update and upgrade.

If you have to use aptitude, do this.

```
sudo aptitude
```

You should post back here with more information first before doing so.

Cheers.

---

### Post by SoPa on 2007-08-30
What about the logs, do they show anything unsual after you ran synaptic?

Try to check the syslog after you ran synaptic and get a segmentation fault. You have 2 way to do it, either in the console (something like "tail /var/log/syslog") or using the "System Log" tool from the System->Administration menu.

I had a similar problem once because I ran out of space in my /var partition, make sure it's not corrupted and/or running out of space (maybe a quick "apt-get clean" to clear the cache? )

---

