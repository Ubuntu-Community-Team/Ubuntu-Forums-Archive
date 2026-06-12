---
title: "GTK 2 updates leave screen a mess."
date: 2010-01-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2010-01-14
After today's updates GTK 2 looks a mess - anyone else getting this - by the way I am using the testing version as requested on this forum.

---

### Post by pferraro on 2010-01-14
Disable the ubuntu-desktop ppa, and manually revert your gtk packages:

cd /var/cache/apt/archives
sudo dpkg --install gtk2-engines-pixbuf_2.19.2-1ubuntu1_*.deb libgail-common_2.19.2-1ubuntu1_*.deb libgail18_2.19.2-1ubuntu1_*.deb libgtk2.0-0_2.19.2-1ubuntu1_*.deb libgtk2.0-bin_2.19.2-1ubuntu1_all.deb libgtk2.0-common_2.19.2-1ubuntu1_all.deb

Or, just wait for this recent upload to hit the repos:
[http://launchpad.net/distros/ubuntu/lucid/+source/gtk+2.0/2.19.3-1](http://launchpad.net/distros/ubuntu/lucid/+source/gtk+2.0/2.19.3-1)

---

