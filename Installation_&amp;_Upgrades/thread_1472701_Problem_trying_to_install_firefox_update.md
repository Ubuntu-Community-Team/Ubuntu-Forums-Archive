---
title: "Problem trying to install firefox update"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by rsanchez1 on 2010-05-04
I've been having problems with the Update Manager ever since it tried to install an update for firefox a few days ago. I'm on Hardy, and I tried to completely remove the firefox package using Synaptic, and re-installing it, and I always get the same error. Maybe it might have something to do with ubuntuzilla? I know I used that a while back to install Firefox 3.5/3.6, since the only one I was getting from the package manager was 3.0. Anyway, here is the error:

E: /var/cache/apt/archives/firefox_3.6.3+nobinonly-0ubuntu1~mfs~hardy2_i386.deb: trying to overwrite `/usr/bin/firefox', which is also in package firefox-mozilla-build

I can't make heads or tails of this, so your help will be greatly appreciated. If this question was posted before, please direct me to the solution. Thanks!

---

### Post by nanotube on 2010-05-05
The obvious solution is to "sudo apt-get remove firefox-mozilla-build"...

---

### Post by rsanchez1 on 2010-05-06
Thanks, it's resolved now.

---

