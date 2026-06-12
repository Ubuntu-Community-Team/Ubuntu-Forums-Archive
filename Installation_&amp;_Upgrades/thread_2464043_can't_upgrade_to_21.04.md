---
title: "can't upgrade to 21.04"
date: 2021-06-23
forum: Installation &amp; Upgrades
---

### Post by OldSmoky2 on 2021-06-23
I cannot upgrade from Ubuntu 20.10 to 21.04. When I try, I get an error because a package is held back. It says, "the following packages have been kept back: dh-python." From some research I've done, it seems this is because the system wants to default to "python-is-python2." I've tried the Software Updater and apt with the same result. Any ideas? Thank you.

---

### Post by TheFu on 2021-06-23
Held packages need to be unheld or removed.  Do that, then fully update the system, reboot if needed, then attempt the do-release-upgrade process again.

So ...
```
sudo apt remove dh-python
sudo apt update
sudo apt full-upgrade

```# reboot, if necessary. Login again
```
sudo do-release-upgrade
```

If there is a failure anywhere in the prior steps, stop. Fix that issue.  OS upgrades do not fix prior problems. They make them worse.

And it should go without saying, but backup anything you cannot lose before starting and before the do-release-upgrade step.  Bad things can happen during open heart surgery, even for the healthiest person. Any illness makes bad things more likely to happen.

---

### Post by OldSmoky2 on 2021-06-25
Thank you. That worked perfectly.

---

