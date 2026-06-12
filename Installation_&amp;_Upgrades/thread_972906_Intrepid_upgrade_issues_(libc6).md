---
title: "Intrepid upgrade issues (libc6)"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by jacobleonardking on 2008-11-06
8.04 had problems on my laptop, so I wanted to upgrade 7.10 -> 8.10.

As normal, I did s/gutsy/intrepid/g on /etc/apt/sources.

The packages downloaded, but then:
```

root@thor:~# apt-get update
...
root@thor:~# apt-get dist-upgrade
...
E: Internal Error, Could not perform immediate configuration (2) on libc6

```

So, I ran:
```

root@thor:~# apt-get install libc6
...
E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.

```

Running on a 64-bit system.

Suggestions?

Thanks,
Jacob

---

### Post by jblackthorne on 2008-11-06
Maybe check out this post and see if it helps:

[http://ubuntuforums.org/showthread.php?t=653177](http://ubuntuforums.org/showthread.php?t=653177)

esentially, it says to install libstdc++6 instead of libc6

Hope this helps.

---

