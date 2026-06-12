---
title: "apt updates - Release notes?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by displaced on 2008-08-21
Hi,

I currently have **cron-apt** set up to check for updates regularly and email me whenever updates are available.  I've then got a Webmin custom command to let me trigger the actual package update.

This is great - but there's one thing I feel I'm missing and I hope is available.  Although the output from apt tells me what packages are available to be installed, it doesn't give me any idea what's changed or what the update addresses.  Is there any way to get this information about an updated package on apt?

Many thanks,
Chris

---

### Post by Partyboi2 on 2008-08-21
Maybe you could use something like apt-listchanges

```
sudo apt-get install apt-listchanges
``` ```
sudo dpkg-reconfigure apt-listchanges 
```
[http://blog.unixlore.net/2007/10/updating-your-debian-or-ubuntu-desktop.html](http://blog.unixlore.net/2007/10/updating-your-debian-or-ubuntu-desktop.html)

---

