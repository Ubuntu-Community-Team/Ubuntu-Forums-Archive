---
title: "Attempted update to Karmic Koala still using kernel from Jackalope"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by stednick on 2010-11-27
I am using a Dell Latitude 2100 that shipped with Jaunty.  I tried to upgrade to to Karmic and things seemed to look good.  There are some bizarre issues (touchpad mouse stopped working, xinput reports "Cannot connect to X server") which both I think are related to the issue that my kernel somehow remains stuck in the [Jaunty kernel]("http://ubuntuforums.org/showthread.php?p=8939202").

```
uname -r
2.6.28-11-generic
```

This is the only kernel listed when I go into GRUB.  Am I right to assume that the older kernel is largely contributing to these problems?

---

### Post by mörgæs on 2010-11-27
Rather than struggling with old (and obsolete) versions and a long chain of upgrades I would go for a fresh install of 10.04 or 10.10.

---

### Post by Rubi1200 on 2010-11-27
I tend to agree with mörgæs on this one. Tracking down and attempting to fix the source of the problems could be a very frustrating, and, ultimately, futile experience.

I recommend you backup all important data and install 10.04, which is an LTS release supported on the Desktop until 2013.

---

### Post by stednick on 2010-11-28
Thanks for the advice, on the one hand it was quite frustrating.  On the other hand, I learned more about differences in grub and grub2 than I ever thought possible (or imagined I would want to learn)

---

