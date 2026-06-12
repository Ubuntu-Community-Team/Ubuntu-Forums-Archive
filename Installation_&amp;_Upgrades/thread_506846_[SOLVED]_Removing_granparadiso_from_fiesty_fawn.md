---
title: "[SOLVED] Removing granparadiso from fiesty fawn"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by troelskn on 2007-07-22
Hi.

Apologies in advance for [cross posting](http://ubuntuforums.org/showthread.php?t=504052) this, but I figured that I've posted in the wrong forum the first time around.

I followed the instructions on this page: [http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html](http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html) and I'm now running granparadiso. It's interesting and all, but I'd rather have my old (v.2) Firefox back. Unfortunately, I'm clueless. Please help.

---

### Post by troelskn on 2007-07-28
I finally figured it out. In case any body else is having this problem, here's how I solved it:

```

# sudo unlink /usr/bin/firefox
# sudo dpkg-divert --rename --remove /usr/bin/firefox
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
# sudo unlink /usr/bin/mozilla-firefox
# sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

```

---

