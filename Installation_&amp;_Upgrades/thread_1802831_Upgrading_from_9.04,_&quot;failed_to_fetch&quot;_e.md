---
title: "Upgrading from 9.04, &quot;failed to fetch&quot; errors"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Baryon on 2011-07-12
Hello,

I'm sorry that there are actually at least two problems here and they probably aren't related. I want to upgrade from 9.04, and I understand I have to go to 9.10 first and then all of the individual versions thereafter. However, when I run the Update Manager, it says "New distribution release '10.04.2 LTS' is available". I'm definitely running 9.04, and I know it's supposed to say '9.10' first, and I remember the days when it did say this, so I'm not sure why it's suddenly skipped a version.

Anyway, I also understand I'm supposed to do all the updates for my current distribution first, and this is where I am getting the following errors (also when running aptitude update). I am getting these errors regardless of which server I use. Needless to say, network connection problems are not the cause:

```

Failed to fetch [http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/non-free/source/Sources](http://mt.archive.ubuntu.com/ubuntu/dists/jaunty/non-free/source/Sources)  404 Not Found [IP: 91.189.88.40 80]
...
Failed to fetch [http://mt.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://mt.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

I'd be very grateful if anyone can help.

---

### Post by snowpine on 2011-07-12
Easiest solution is often a fresh reinstall of the new version.

If you want to upgrade your existing system, you'll need the following instructions as 9.04 is "end of life."

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

