---
title: "Kernels 2.6.24-30 &amp; 2.6.24-31"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2012-03-18
I haven't updated my system for a few weeks, and the list of updates available shows both 2.6.24-30 and 2.6.24-31 kernels. Do I need to install both?

---

### Post by ajgreeny on 2012-03-18
I assume from those kernel versions that you really are still running Ubuntu 8.04, Hardy Heron.  This is no longer supported, so you may find that it will not be possible to update any more, unless you have enabled the "end of life" repositories.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I would suggest that you upgrade to a later version of Ubuntu, which is still supported.  10.04 will be the nearest to your current version, and still has just over a year of support to come.  The current version 11.10 runs unity desktop, which is very different from the gnome-2 of Hardy, but you may like it.  Try it out with a live CD or USB.

---

### Post by Old_Grey_Wolf on 2012-03-18
I assume you are running the 8.04 Hardy Heron server version that is supported until April 2013. ;)

You should be able to skip the 2.6.24-30 kernel; however, I usually don't skip kernel updates. The few times I skipped a kernel update didn't cause any problems, YMMV.

@ajgreeny, the server version is supported for **5 years** unlike the desktop version that has 3 years of support. The 2.6.24-31 kernel update was only released about 2 weeks ago.

---

### Post by RegUB on 2012-03-19
Thanks for your replies. I am still getting notified of updates, so I assume I must be on the server version - although I only use it as a desktop. I am reluctant to upgrade until absolutely necessary, since I had a job getting my wireless adapter working (via ndiswrapper, etc) and I am afraid that upgrading may upset this. Should I be worried about this?

---

### Post by Old_Grey_Wolf on 2012-03-19
On the old versions; such as 8.04, it was common for upgrades to the kernel to break changes made using ndiswrapper. It happened to me so frequently that I wrote a script to re-install the wireless driver after a kernel upgrade.

You may want to consider using a newer version of Ubuntu if you are using the server version like a desktop version anyway.

---

