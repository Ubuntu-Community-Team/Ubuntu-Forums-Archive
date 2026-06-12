---
title: "Upgrade to natty fails (ubuntu, kubuntu, xubuntu installed)"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by poljpocket on 2011-04-29
Hi all,

I have a problem, because installation of ubuntu 11.04 will fail if I try to.

I have also Kubuntu and Xubuntu installed, which I regret a lot because I cannot uninstall them as well...

The problem is that I have installed a one-time-activation proprietary software so a fresh install is no option.

The error when upgrading is, that "xubuntu-desktop" cannot be marked for upgrade!

Thanks for help, grz ppocket

---

### Post by dino99 on 2011-04-29
wait next week, servers are too busy right now

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by snwbeast on 2011-05-10
I was having the same issue and what worked for me was to un-install Xubuntu-desktop via the command line:

sudo aptitude remove xubuntu-desktop


After that I restarted the Upgrade Manager and am currently 30% done with my upgrade.

HTH,

-- C

---

