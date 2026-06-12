---
title: "re install system"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by terranz on 2006-09-06
is there a way I can back up my system updates and use them after a re install to save from having to download them again?

---

### Post by yota on 2006-09-06
Sure, backup the folder /var/cache/apt/archives and then restore it after the reinstall.

Hope this helps!

---

### Post by terranz on 2006-09-06
so if I copy those files back to that directory then the system will update automatically?

I could copy those files to a machine stuck on dial up?

---

### Post by yota on 2006-09-07
Archives is like a cache for .deb packages, when the system needs a package it first checks on that dir and if it's not available will try to download it.

So solely placing files there will not upgrade nothing, but when update manager will try to update the system (actually installing the content of that files), or if you mark all updates in synaptic the downloading time will be saved.

Beware that this doesn't give 100% assurance that 0 file will be downloaded: if one is needed and is not present in archives (most likely this can happen for some difference in the configuration between the two installs) you'll end up in the need of a connection anyway.

---

### Post by terranz on 2006-09-07
Thanks for the info  .  I'm not trying to achieve 0 download but rather I want to avoid a few hundred MB of downloading.

---

