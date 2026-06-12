---
title: "Problem with upgrading Ubuntu from 18.10 to 19.04"
date: 2019-08-06
forum: Installation &amp; Upgrades
---

### Post by horizn on 2019-08-06
I am trying to upgrade Ubuntu 18.10 to 19.04 using commands:
```

 pkexec do-release-upgrade -m desktop -f DistUpgradeViewKDE & 

```
or
```

 sudo do-release-upgrade -m desktop

```
both with the same failure: Your python3 install is corrupted, please fix the '/usr/bin/python3' symlink.
Python3(.6) installation seems to be fine. I have also installed Python  3.7. Manually removed and re-created symlinks with no effect.
Also
```
apt-get install --reinstall python
```
or
```
update-alternatives --remove-all python
```
didn't help.
Any ideas how to perform upgrade to 19.04?

---

