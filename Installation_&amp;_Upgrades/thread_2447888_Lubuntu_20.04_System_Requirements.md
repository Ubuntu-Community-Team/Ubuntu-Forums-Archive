---
title: "Lubuntu 20.04 System Requirements"
date: 2020-07-28
forum: Installation &amp; Upgrades
---

### Post by SageOfSmeg on 2020-07-28
Couldn't find this anywhere on the release page for Lubuntu 20.04.

I plan to have 2 partitions: / and /home
Will 20GB HDD be enough for / (root) ?

Thanks

---

### Post by dino99 on 2020-07-28
you can set / around 15 GB

---

### Post by SageOfSmeg on 2020-07-28
Excellent, thanks.

---

### Post by ActionParsnip on 2020-07-28
Lubuntu is very small. Could probably get away with a 10Gb root folder if you keep your applications under control

---

### Post by guiverc on 2020-07-28
The size you need will depend on what you install, and what you use your machine for. 

 What programs will you use?  will they involve other libraries being added to your system? (*taking extra space*), be containerized? (snaps etc, *needing extra disk space*), do you keep a lean system? or hear about some package/program, and need to install it to *give it a spin*?

My Lubuntu *groovy* system is 27GB for / (*not counting a separate /home partition*) and I've had to spend 90+ mins over the last fortnight trying to trim my files on / so I can re-login. It's not fun.

I'm using a *development* release which is *very* slightly larger (debug/developer libraries), but my real problem is *bloat* and my constantly adding software that I only use very rarely (*commonly used in supporting others*) etc, or occasionally added to *try*.

You'll also need plenty of space come *release-upgrade* time, as it's free space that allows the next release to download onto your machine, packages get expanded and installed - all of them; before the clean up occurs, and space is returned. If you're going to re-install come *upgrade* time, a leaner system is fine.  If you plan to *release-upgrade* in-place on your disk, keep plenty of free disk space available for this purpose (*or allow yourself time to create this space; disk space is usually cheaper than time*).

I personally recommend 24-32GB, but that's based on my actual use. Consider what you'll use the box for, how long you'll be using it for, and if you're going to *nuke and install* come upgrade time, or *release-upgrade*.   There is no *one-size-fits-all, *I for one would want more than 20GB given how I use my system.   I did a QA-test install of Lubuntu 20.04.1 today, and the installed / used only 5GB of disk space... but that's without anything added.

20GB should be good.

---

### Post by SageOfSmeg on 2020-07-28
I tend to use the machine to monitor my home network and record CCTV. I don&#8217;t load much software, it&#8217;s basically a bare-bones unit, typically running headless. I have an old spare 20GB IDE drive that&#8217;s no good for anything else, hence my query. Currently I&#8217;m running Lubuntu 14.04, just wanted to move to 20.04 when I next do a fresh reinstall. Once installed, the system is unlikely to grow.

---

