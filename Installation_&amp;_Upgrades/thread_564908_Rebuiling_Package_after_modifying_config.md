---
title: "Rebuiling Package after modifying config"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by ture_atlantis on 2007-10-01
I am attempting to rebuild the 'tora' package to enable oracle support.  when rebuilding, do i need to do anything else besides 'dpkg-buildpackage'?  Here is my workflow.

cd /usr/src
apt-get source tora
cd tora-1.3.21
*modify debian/rules*
dpkg-buildpackage

It seems like its building correctly, but it trows this error:

configure: error: Qt () (library qt-mt) not found.
      Please check your installation! For more details about this problem,
      look at the end of config.log.Make sure that you have compiled Qt with thread support!

but as you can see, it is installed:
root@atlantis-laptop:/usr/src/tora-1.3.21# dpkg-query --list |grep qt | grep mt
ii  libqt3-mt                                  3.3.8really3.3.7-0ubuntu5.2                Qt GUI Library (Threaded runtime version), V
ii  libqt3-mt-dev                              3.3.8really3.3.7-0ubuntu5.2                Qt development files (Threaded)
ii  libqt3-mt-psql                             3.3.8really3.3.7-0ubuntu5.2                PostgreSQL database driver for Qt3 (Threaded


Any ideas?

---

