---
title: "General install questions"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by bardoksan on 2007-09-11
1) Why can't I choose certain packages when doing a fresh install?

2) Is installing from the live cd(dvd) desktop the only way to install?

3) How do I make the cd(dvd) a source for the adept package manager?

---

### Post by rivalarrival on 2007-09-11
1. By default, only certain repositories are active after a fresh install. edit /etc/apt/sources.list and uncomment to add other repositories.

2. No. Google "wubi" for a method to install directly from windows. You can also use a USB stick. In one specialized application, I was able to simply write an entire disk image to a drive.

3. See 1.

---

