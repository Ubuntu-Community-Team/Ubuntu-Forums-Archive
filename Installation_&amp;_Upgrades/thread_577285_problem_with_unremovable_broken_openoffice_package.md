---
title: "problem with unremovable broken openoffice packages"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by lucian303 on 2007-10-16
I'm getting the following error after trying to uninstall broken openoffice packages:

E: openoffice.org-calc: subprocess post-removal script returned error exit status 2
E: openoffice.org-impress: Package is in a very bad inconsistent state - you should
E: openoffice.org-writer: subprocess post-removal script returned error exit status 2

I cant upgrade the system until I get rid of these broken packages, but nothing seems to be able to remove them. I've also tried reinstalling them. Any ideas? 

How do I get rid of them so I can upgrade my system?

---

### Post by FredB on 2007-10-16
Try sudo apt-get install -f

It could help a little.

---

