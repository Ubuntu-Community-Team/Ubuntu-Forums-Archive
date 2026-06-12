---
title: "Unable to correct dependencies after upgrade"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by biotomas on 2017-02-17
Hi,

I upgraded from 14.4 to 16.4 recently and package manager stopped working.

If I run "apt-get upgrade" I get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gstreamer1.0-clutter : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libstdc++-5-dev : Depends: libstdc++6 (>= 5.4.1-2ubuntu1~14.04) but 5.4.0-6ubuntu1~16.04.4 is installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.1-2ubuntu1~14.04 is installed
              Breaks: libstdc++6:i386 (!= 5.4.0-6ubuntu1~16.04.4) but 6.2.0-3ubuntu11~14.04 is installed
 libstdc++6:i386 : Breaks: libstdc++6 (!= 6.2.0-3ubuntu11~14.04) but 5.4.0-6ubuntu1~16.04.4 is installed
E: Unmet dependencies. Try using -f.

```

"apt-get install -f" gives me
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 gstreamer1.0-clutter : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libstdc++-5-dev : Depends: libstdc++6 (>= 5.4.1-2ubuntu1~14.04) but 5.4.0-6ubuntu1~16.04.4 is installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.4) but 5.4.1-2ubuntu1~14.04 is installed
              Breaks: libstdc++6:i386 (!= 5.4.0-6ubuntu1~16.04.4) but 6.2.0-3ubuntu11~14.04 is installed
 libstdc++6:i386 : Breaks: libstdc++6 (!= 6.2.0-3ubuntu11~14.04) but 5.4.0-6ubuntu1~16.04.4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I get the same messge as above for "apt-get dist-upgrade", "apt-get autoremove -f", "apt-get purge", ...

What can I do?

---

### Post by oldfred on 2017-02-17
Do you have any ppas in use?
Those always cause issues on upgrades. You have to turn them off. Then enable in new version as not all of the have new version or correct configuration.

       Check sources & ppas
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

