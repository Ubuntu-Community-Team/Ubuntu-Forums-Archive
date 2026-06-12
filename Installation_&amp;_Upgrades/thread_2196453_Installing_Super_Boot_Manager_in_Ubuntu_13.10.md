---
title: "Installing Super Boot Manager in Ubuntu 13.10"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by andytlong on 2013-12-29
For those with Saucy and who love Super Boot Manager, I did a little tinkering to get it installed and working on 13.10. As it stands currently, there is no installation for Saucy so we will be using the one for Raring. Simply do what I did.

First, you'll need to add the source:
```
sudo nano /etc/apt/sources.list
```

Next, add this to the end of the file:
```
deb http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu/ raring main
```

Save your changes, and update your repositories.
```
sudo apt-get update
```

Finally, install Super Boot Manager!
```
sudo apt-get install super-boot-manager
```

You should be good to go! Happy modifying!

---

### Post by dieferman on 2014-04-17
Thanks For The Tip... It Work Flawlessly !!!!

---

