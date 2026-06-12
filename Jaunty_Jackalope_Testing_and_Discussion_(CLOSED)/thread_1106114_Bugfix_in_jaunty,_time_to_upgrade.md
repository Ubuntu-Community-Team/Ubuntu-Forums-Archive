---
title: "Bugfix in jaunty, time to upgrade?"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wire42 on 2009-03-25
I've encountered the "[heavy memory leak in gvfsd-http]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225615")" bug several times on intrepid (8.10). Apparently, this bug has been fixed upstream (by the gvfsd developers) and the latest version is available as part of ubuntu 9.04.

Is fixing this bug a good reason to upgrade? Is there a better way to just upgrade gvfsd-http without switching to an alpha release? Will this break my ability to upgrade in the future?

---

### Post by cariboo on 2009-03-25
The Jaunty beta is supposed to be released March 26/09. So far Jaunty has been pretty stable, and a lot faster if you use ext4 partitions. If you are able to fix anything that might crop up between now and the final release, I would suggest backing up your important files and doing a clean install.

Jim

---

### Post by wire42 on 2009-03-25
A little googling and it's clear that any performance gains from ext4 are negated by its ability to *wipe out data* on crashes:
[http://www.automaticable.com/2009-03-12/testing-ubuntu-jaunty-and-ext4-without-trashing-your-data/](http://www.automaticable.com/2009-03-12/testing-ubuntu-jaunty-and-ext4-without-trashing-your-data/)

I think I should be looking at installing the newer version of gvfsd-http in intrepid. Is there a guide that might help?

EDIT: Did some research ... package containing the bugfix is called gvfs-backends. Intrepid version is 1.0.2-0ubuntu2, while the Jaunty version is 1.2.0-0ubuntu1.

EDIT2: Added a comment to the already existing [backport request for gvfs](https://bugs.launchpad.net/intrepid-backports/+bug/312283)

---

