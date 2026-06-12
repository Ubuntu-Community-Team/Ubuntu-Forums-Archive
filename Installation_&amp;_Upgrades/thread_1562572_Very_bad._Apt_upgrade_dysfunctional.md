---
title: "Very bad. Apt upgrade dysfunctional"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by kakyoism on 2010-08-27
This morning a chromium-browser update choked forever at 
```
 Unpacking chromium-browser-ffmpeg....
```

After I killed the process, my aptitude is locked
then I unlocked, and reset dpkg. I was told that some packages are at very bad conditions and then sudo aptitude update; sudo aptitude safe-upgrade gives the results below:

```

E: I wasn't able to locate a file for the chromium-browser-inspector package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the chromium-browser-inspector package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download

```

Now I cannot update packages at all!
Please help!!

---

### Post by kakyoism on 2010-08-27
I manually uninstalled chromium and restarted the update, but just found that not just chromium, unpacking anything takes forever. I tried quite a few repos and the problem persists.

Any ideas????

---

### Post by kakyoism on 2010-09-04
not just upgrade.

Now every new package install hangs at this "Unpacking" stage!!!

---

### Post by kakyoism on 2010-09-05
It seems to be related to busy USB drive.
which is another thread I posted!!

After reboot (a code reboot, argh, because the busy USB drive prevented system from rebooting normally), the package seems to be able to be unpacked.

BUT, all in all, it's not supposed to be this hard to work with USB drives.

---

