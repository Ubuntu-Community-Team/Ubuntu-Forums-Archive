---
title: "can not upgrade distribution (think I know why)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Kymus on 2010-04-30
Since 9.10 was available, I've been unable to upgrade to the next distribution. Today I actually took the time to copy down and make note of the error given.

The pop-up error is this:

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
**E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages**.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Speaking of held packages, I haven't updated xserver-org since 8.10. When I first upgraded to 9.04 I suffered from the driver issues since I had an old ATI card and [so I followed directions to fix this]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue") by blocking xserver-org updates. Well now I've got a nice new NVIDIA card and this work around isn't necessary anymore anyway, so perhaps by reversing this, I can update finally?

I'm just not sure how to undo what was done in the tutorial.

---

### Post by Kymus on 2010-05-08
bump

---

### Post by Kymus on 2010-05-12
bump

---

### Post by roti_xavier on 2010-05-12
Same here I'm unable to get the download the ubuntu 10.04. Is downloading the iso image and then reinstall the os the only option?

---

