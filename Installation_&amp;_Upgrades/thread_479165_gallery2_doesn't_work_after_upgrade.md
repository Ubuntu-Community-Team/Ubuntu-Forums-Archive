---
title: "gallery2 doesn't work after upgrade"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by briguy on 2007-06-20
I've recently upgraded my server from 6.06 to 7.04 (through 6.10) and after the upgrade gallery2 no longer works.  The files are still there, I've tried dpkg-reconfigure, but it just gets a 404 message when I browse the /gallery2 in Firefox.  Any ideas?

---

### Post by briguy on 2007-06-20
Ok, I solved the question myself.  A symbolic link went AWOL somewhere during the upgrade.  I just had to do a ln -s /usr/share/gallery2 /var/www/. to fix it.
 
Now if I can just get the NFS working again, the upgrade will be complete...

---

