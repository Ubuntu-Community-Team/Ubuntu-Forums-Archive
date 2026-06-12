---
title: "How to download packages &amp; dependencies and install via DVD/USB on a standalone box?"
date: 2019-06-09
forum: Installation &amp; Upgrades
---

### Post by benbrockn on 2019-06-09
Basically,

I usually use a large script that I wrote to add a ppa, install a bunch of packages via repos, install packages via .debs, compile from git clones, etc...

What I really want to do is be able to pre-download all the packages, dependencies, and git cloned repos to a single folder (or like a .ISO file), and then do a regular install of Ubuntu and install them from that folder (or .ISO) instead of re-downloading all of them. This would help for multiple installs but also for computers that need to be standalone boxes (not connected to the Internet).

How can I accomplish this?

---

### Post by TheFu on 2019-06-09
I don't know, but you might want to check out **apt-cacher-ng**.
Installing .deb files directly can be hazardous to your APT dependencies. Whenever I've done that, usually in 3-6 months, I had to uninstall those packages so my system could be maintained.

---

