---
title: "Software center stuck after trying to install dropbox"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by Dominicus on 2014-09-05
Running Ubuntu 12.04LTS.
I uninstalled an old version of dropbox, which I had installed from a .deb package.
I then selected the dropbox version listed in the software center for installation.
I thought this had gone fine, but at a later reboot, I get warning about partial updates.
Now the Software Center is stuck with the following screen:
[ATTACH=CONFIG]256159[/ATTACH]

The circular arrows alert to progress, but seems stuck there.  Closing/rebooting, same.

How do I clear up or restart the update manager?

---

### Post by spronkc on 2014-09-05
I am having similar problems.

---

### Post by egeezer on 2014-09-05
Had similar thing happen myself.  Cleared it up with
```
sudo su
```

followed by
```
# dpkg --purge nautilus-dropbox
```

I had tried with plain sudo, but without success.  In the end, I gave in and installed from the tarball I found for version 2.10.29 in the Dropbox forum.  On another box, I just used the commands for the server install on the Dropbox site.

Hope this helps!

---

