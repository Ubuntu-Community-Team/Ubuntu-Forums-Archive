---
title: "chrome installation problem"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by buzan on 2009-12-12
after installing chrome in Koala, i cudnt start it. When I type google-chrome in command line this is what i get.

> :~$ google-chrome
[14877:14877:2056754716:FATAL:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/chrome/browser/browser_main.cc(610)] Check failed: profile. Cannot get default profile.
Trace/breakpoint trap

Help.

---

### Post by Belizeian on 2010-02-06
I am getting the same result.

---

### Post by ikt on 2010-02-06
Where did you download/install from?

edit: the fix is here: [http://crunchbanglinux.org/forums/post/47826/#p47826](http://crunchbanglinux.org/forums/post/47826/#p47826)

> $ chown -R replaceTHISwithyourusername: ~/.config/google-chrome

---

### Post by Belizeian on 2010-02-06
Thanks that got it, I installed from the PPA.  I had been running it fine and not as root that's for damn sure.  Not sure how the permissions got changed guess it's time to look at the logs closely.

---

