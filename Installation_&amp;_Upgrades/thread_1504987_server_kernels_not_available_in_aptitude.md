---
title: "server kernels not available in aptitude"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by azide on 2010-06-08
I recently checked the kernel versions available on my server, and I saw that the most recent server kernel installed was 2.6.28.18. I would expect to see version 2.6.32.22. I also have the generic-pae kernel installed, which is up to date and currently being used.

upgrade and dist-upgrade both provide no updates. I tried purging linux-image-server and reinstalling, which worked fine but did not include the installation of any actual kernel images.

aptitude search shows no available server kernels. I have cleaned and updated the cache. I have also checked sources.list, which looks normal (to me).

I just upgraded from 9.10 to 10.04, but I am not sure exactly when linux-image-server stopped upgrading.

Any suggestions on where to go from here?

---

