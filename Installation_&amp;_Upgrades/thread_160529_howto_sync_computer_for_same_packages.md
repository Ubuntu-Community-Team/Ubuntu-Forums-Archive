---
title: "howto sync computer for same packages"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2006-04-15
I'm using a desktop at work and a notebook at home, both running Dapper.  I recently had to reinstall my notebook but would like it to be running all the same packages as my desktop.  Is there a file or files that I can copy from the desktop to my notebook to ensure that it will be updated, using apt-get or synamptic, to have all the same packages installed?

Thanks a bunch, like Ubuntu more every day.

Jim

---

### Post by jamaas on 2006-04-19
Figured this one out if it helps anyone.  If you copy the contents of 
/var/cache/apt/archives

from one computer to another and then do
sudo apt-get upgrade

both computers will have same packages.




[QUOTE=jamaas]I'm using a desktop at work and a notebook at home, both running Dapper.  I recently had to reinstall my notebook but would like it to be running all the same packages as my desktop.  Is there a file or files that I can copy from the desktop to my notebook to ensure that it will be updated, using apt-get or synamptic, to have all the same packages installed?

Thanks a bunch, like Ubuntu more every day.

Jim[/QUOTE]

---

