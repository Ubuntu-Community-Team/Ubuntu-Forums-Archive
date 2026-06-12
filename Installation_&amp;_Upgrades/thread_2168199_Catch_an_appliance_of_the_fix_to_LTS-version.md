---
title: "Catch an appliance of the fix to LTS-version"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by sbar on 2013-08-16
Hi

I'm not a user of Ubuntu but my parent uses it. There is one [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1208132") in the Linux kernel and I want to catch the situation when the fix will be applied to LTS-version of the distro to install an update with the fix for my parent. How can I do this? I've already asked it in the bugreport but didn't get any useful answer.

To moderator: sorry if I've posted in the wrong part of the forum, I didn't find anything better. Please move it if I'm wrong.

Thanks.

---

### Post by ibjsb4 on 2013-08-16
According to your link, kernel 3.5.0-37 has the fix built in.  That kernel is in ubuntu 12.04 repositories (software center), you can upgrade to that kernel.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1208132/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1208132/comments/16)

---

### Post by tgalati4 on 2013-08-16
If you have subscribed to the bug with a valid email, then you will get notification of any updates to the progress, any others adding comment to this bug, and lastly, any fixes.  It could take a while.

Reading through the comments there are several work-arounds proposed that work for folks:  upgrade BIOS on the computer, apply updates to get to 12.04.2, or backport the kernel fix (which is not easy to do).  

There should be an update coming soon for this bug, since a patch has already been applied to the current version of Ubuntu.

---

