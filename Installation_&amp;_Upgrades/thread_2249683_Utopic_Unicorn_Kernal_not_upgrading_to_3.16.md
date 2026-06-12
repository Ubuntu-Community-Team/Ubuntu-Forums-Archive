---
title: "Utopic Unicorn: Kernal not upgrading to 3.16"
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by spacesamurai2 on 2014-10-23
Just upgraded to Utopic Unicorn, and found my Kernel was still at 3.13. Reading the release notes, Utopic Unicorn is releasing with 3.16. 3.16 adds support for Haswell Systems, so this is something I wanted. To get the current kernel installed:

```

dave@desktop:~$ sudo apt-get install linux-generic linux-image-generic linux-headers-generic
dave@desktop:~$ sudo reboot

```

After reboot:
```

dave@desktop:~$ uname -r
3.16.0-23-generic

```

Hooray!

---

### Post by ibjsb4 on 2014-10-24
Hooray :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

