---
title: "Can't install to particular HDD"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by sideaway on 2010-04-30
Hey there I can't seem to install Ubuntu to the Hard drive that I'd like.

I have 6 hard drives, 1.5tb, 2x1tb, 2x500gb and a 200gb. the 200gb is the one I'd like to use.

It has 3 partitions (and swap space) a 30gb, for ubuntu, 60gb for windows and 100gb for /home. However as seen in the screenshot below I cannot install it to the 200gb hard drive, any idea why?

[[IMG]http://imgur.com/MVsyMl.jpg[/IMG]](http://imgur.com/MVsyM.png)

---

### Post by sideaway on 2010-04-30
I ran sudo apt-get remove dmraid, and it fixed it, it now correctly detects my HDD... strange.

---

### Post by Salisburybs on 2010-04-30
> **sideaway said:**
> I ran sudo apt-get remove dmraid, and it fixed it, it now correctly detects my HDD... strange.

That worked for me as well. After uninstalling dmraid it correctly detected my remaining drives. Strange how it found my 500GB HDD and 2GB USB thumb drive.

---

### Post by sideaway on 2010-04-30
It detected all drives of mine with only one partition - it was the multi partitioned drives that were the issue. I hope a bugs been filed - it sounds like a pretty serious issue.

---

### Post by Salisburybs on 2010-04-30
> **sideaway said:**
> It detected all drives of mine with only one partition - it was the multi partitioned drives that were the issue. I hope a bugs been filed - it sounds like a pretty serious issue.
Now that you mention it, the drive that didn't get detected had two partitions on it as well. I tried to install 9.10 a few days ago and that didn't work either (same problem) so I figured with 10.04 right around the corner and being busy I would just wait and see if it had been fixed.

---

