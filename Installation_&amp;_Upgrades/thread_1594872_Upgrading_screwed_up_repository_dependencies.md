---
title: "Upgrading screwed up repository dependencies?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by underling08 on 2010-10-12
Hi, I just upgraded my 9.10 karmic through 10.04 lucid and then finally to 10.10 meerkat. My computer is almost brand new, so while I was running 9.10 I didn't have the opportunity to mess with the repositories that much. I might have enabled restricted drivers and extras, but that's about it. Anyway, with my fresh upgrade of ubuntu I decided to install some new software. But almost every time I have attempted to do anything in synaptic, I get very strange messages about inter-dependencies. For instance, I tried to install the game 0 a.d. the other day, which has its own repository, so I added the repository and did ```
sudo apt-get install 0ad
``` Terminal spat back a message about it being dependent on an older version of binutils than I had, and on 0ad-data, both of which 'would not be installed'.

Similar messages have turned up everytime I try to update the repos or install new packages.  I'm considering just doing a clean install of 10.10, but if there's some way of fixing this without downloading, I would greatly appreciate it.

---

