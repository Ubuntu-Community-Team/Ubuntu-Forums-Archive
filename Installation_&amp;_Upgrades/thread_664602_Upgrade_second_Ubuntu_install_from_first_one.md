---
title: "Upgrade second Ubuntu install from first one"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by scientist47 on 2008-01-11
I would like to have two Ubuntu installs on my computer - one of the current release, and one development release. 
In order to avoid security risks, I want to maintain upgrades on both installs from one of the installs. 
One way to do this would perhaps be to install an extra apt, that reads package information from, and installs packages to the second Ubuntu install. 

What would be the best and easiest way to solve this?

I think this solution would be interesting for anyone who has a strict security policy they must follow.

---

### Post by PmDematagoda on 2008-01-11
What you are attempting to do is rather dangerous and will break your "stable" Operating System, I do not even think that the current systems allow it.

If you want to keep up-to-date then using a developmental version or upgrading to it is less riskier than using incompatible repositories in an attempt to keep up-to-date.

---

### Post by scientist47 on 2008-01-11
I did not mean to use the same repository for both installs. 

My idea:

I use Hardy in my daily work (programming). If something breaks, I am able to fall back on Gutsy, which is installed on a separate partition. If Hardy works well, it may be long between my Gutsy boots, and when I boot Gutsy after a long time, it will be outdated and insecure. 
From Hardy, I can check the Gutsy package information, and upgrade the Gutsy install from the Gutsy repositories. 

Maybe I can use chroot to set the root to Gutsy's root, and then run apt:
From Hardy:
```

chroot /mnt/ubuntu-current
apt-get update && apt-get upgrade
```

---

