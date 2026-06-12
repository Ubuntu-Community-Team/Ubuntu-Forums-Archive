---
title: "distribution upgrade hangs: 7.10 to 8.04.1 alternate cd"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by janx on 2008-10-20
I am trying to upgrade with the alternate CD (no working Internet connection)...

After the first step (Preparing to upgrade) the window is greyed out, no response...

Here is what I find in /var/log/dist-upgrade/main.log
*ERROR Cache can not be locked (E:Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)*
....

What can I do?

---

### Post by vijaym on 2008-10-20
depending on how you are doing the upgrade you might need to sudo

---

### Post by janx on 2008-10-20
This what I did:
gksu "sh /cdrom/cdromupgrade"

What's wrong?

---

### Post by janx on 2008-10-21
After removing the lock (removing the file), I have managed to go a bit further with synaptic and the alternate CD. However the upgrade stops on this error:
*E:/var/cache/apt/archives/human-theme_0.18_all.deb: trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver*

Is it possible to remove these packages? ... otherwise I guess the most likely solution is to reinstall Ubuntu from scratch...

---

