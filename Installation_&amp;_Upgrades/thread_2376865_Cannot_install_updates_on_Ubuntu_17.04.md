---
title: "Cannot install updates on Ubuntu 17.04"
date: 2017-11-06
forum: Installation &amp; Upgrades
---

### Post by dshvets1 on 2017-11-06
When I go to **Ubuntu Software | Updates** and try to run updates by clicking Install button, at fist nothing happens and then I got the following error message:

*E: The package linux-image-extra-4.10.0-38-generic needs to be reinstalled, but I can't find an archive for it.*

It started happening after attempt to upgrade from 17.04 to 17.10. If I try to reinstall the package by running apt install --reinstall, I get the same error.

The same error if I run *update-manager* in the terminal.

---

### Post by raja.genupula on 2017-11-07
May be you should try by clearing apt cache. 

> sudo apt-get clean

And try again.

---

### Post by RobGoss on 2017-11-07
Try changing your download source Software & Updates, Other software 

Choose a better source for your location

---

### Post by dshvets1 on 2017-11-13
Thanks for the replies. I was able to solve this by running:

sudo dpkg --remove --force-remove-reinstreq linux-image-extra-4.10.0-38-generic

---

### Post by vasa1 on 2017-11-13
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

