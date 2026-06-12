---
title: "mysql install fails"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by mofojones on 2006-03-25
I'm migrating my server from arch linux to ubuntu, but I've run into a big stopper.  MySQL does not install.

"Package mysql is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package mysql has no installation candidate"

I have breezy-updates, main, restricted and universe enabled in my sources.list

Any hints?

---

### Post by soce_32 on 2006-03-25
sudo aptitude search mysql

You will find that you are most likely looking for mysql-server and mysql-client.  There are many mysql related packages that you may be interested in.

sudo aptitude install mysql-server mysql-client

will get you started

---

### Post by mofojones on 2006-03-25
Thanks, I thought it might be something like that.

---

