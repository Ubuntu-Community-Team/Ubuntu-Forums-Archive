---
title: "apt-get can't finish getting packages"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Wej on 2011-11-12
So I need to unzip a file on my server, which oddly doesn't have the unzip package installed. So I typed apt-get install unzip, and it downloads the first 131072 bytes of the 181kb total size. I thought maybe the package was broken, so I tried something else, and it downloads part of it and stops. I tried deleting the file from the /var/cache/apt/archives/partial directory (5 times, actually) and started it again, but it gave me the same issue.

It is needing to get the packages from old-releases.ubuntu.com, and the server is able to download files from other sites no problem, just not with apt-get. Anyone know why it would this?

My sources.lst file:
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

# Optional
deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
```

I also tried to manually browse to the path where the package should be: [http://old-releases.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/](http://old-releases.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/) but that doesn't have all the packages listed separately.

---

### Post by leeper69 on 2011-11-13
try dpkg to fix a broken install with the following command.
in the bash terminal type sudo dpkg --configure -a
Let me know if it helped.

---

### Post by Wej on 2011-11-15
It never even finished downloading the .deb file so dpkg could work with it.

I figured out it was my modifications to /usr/lib/apt/methods/http that was the problem. I had been using trickle to rate-limit the downloads for apt-get, using [this method](http://ubuntuforums.org/archive/index.php/t-20342.html). Once I reverted, it worked fine. I decided to limit it with squid on the internet facing router instead of at each individual server to save me time and effort.

---

