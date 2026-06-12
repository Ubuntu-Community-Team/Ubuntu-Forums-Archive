---
title: "After upgrade 18.04 to 19.04"
date: 2019-06-21
forum: Installation &amp; Upgrades
---

### Post by richoandika on 2019-06-21
I've been upgrade to 19.04 using terminal but why when I check in the terminal the version doesn't change, still 18.10
```

richoandika@hp:~$ lsb_release -a
LSB Version:    core-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic

```

---

### Post by DuckHook on 2019-06-21
Note that you are no longer in Bionic (18.04) but Cosmic (18.10), so you *did* actually upgrade by one version.

You cannot go directly from 18.04 to 19.04 because you cannot leapfrog standard versions. Going from LTS to LTS would have been better, but the next LTS is 20.04 (next year April).

Now that you are on 18.10, you must upgrade to 19.04 soon. 18.10 runs out of support at the end of July after which it will no longer be in the main repos and will no longer be upgradable without taking special measures.

If 18.04 was working fine for you, it was not advisable to switch to standard releases. This now puts you on the upgrade-every-six-months treadmill along with the reduced stability/reliability of standard releases.

---

