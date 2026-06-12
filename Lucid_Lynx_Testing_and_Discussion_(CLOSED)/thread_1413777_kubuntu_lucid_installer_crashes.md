---
title: "kubuntu lucid installer crashes"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by todak on 2010-02-22
I have downloaded the daily-live for kubuntu lucid and when I try to install from the default desktop, I first get the installation screen. Then upon clicking the "forward" button, the icon busy indicator spins for a few seconds and then the installer screen disappears and I am looking again at the desktop. There is no crash handler or anything to indicate that anything went wrong. However, looking in /var/log/installer I find a file entitled "debug". Here are the contents. There are many "**trying to create local folder /root/.kde: Permission denied**" lines, but there are messages interspersed, so please do not scroll quickly through and miss them. ;)

```
Ubiquity 2.1.23
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /root/.kde: Permission denied
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Couldn't create index file "/var/tmp/kdecache-root/kpc/kde-icon-cache.index" 
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Permission denied
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
trying to create local folder /root/.kde: Permission denied
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
trying to create local folder /var/tmp/kdecache-root/kpc: Permission denied
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Couldn't create index file "/var/tmp/kdecache-root/kpc/kde-icon-cache.index" 
FIXME, medianotifier unload port to KDE 4
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
kubuntu-ubiquity(5942): Failed to lock file "/var/tmp/kdecache-root/kpc/kde-icon-cache.lock" , last result = 2 
QSocketNotifier: Invalid socket 13 and type 'Read', disabling...
KCrash: Application '' crashing...
Warning: connect() failed: : Permission denied
KCrash cannot reach kdeinit, launching directly.
drkonqi(6781) SystemInformation::runLsbRelease: found lsb_release
drkonqi(6781) KCrashBackend::constructCrashedApplication: Executable is: "/usr/bin"
drkonqi(6781) KCrashBackend::constructCrashedApplication: Executable exists: true
drkonqi(6781): The specified process does not exist. 

```

Any clue as to what is happening and what solution there is to enable installing? I have tried installing as sudo and even tried installing directly from the boot menu, but I always wind up back at the default desktop.

---

### Post by VMC on 2010-02-22
You could open a terminal and try running ubiquity that way.
Are you using the manual method for partitioning or letting the installer decide?

---

### Post by todak on 2010-02-22
I don't even get past the main installer screen. As soon as I click on the "Forward" button, it crashes. Running from a terminal, a shell, root shell or any other method results in the same debug message.

---

### Post by VMC on 2010-02-22
> **todak said:**
> I don't even get past the main installer screen. As soon as I click on the "Forward" button, it crashes. Running from a terminal, a shell, root shell or any other method results in the same debug message.

What text is inside the terminal after it crashes?
Also do you have Windows using partition #1?

---

### Post by todak on 2010-02-22
> **VMC said:**
> What text is inside the terminal after it crashes?
Also do you have Windows using partition #1? 

Absolutely nothing appears in the terminal window. And, no, I do not have any windows on any of my drives, partitions or any other device. I build my systems myself, so they are unmolested by Microsoft. I install one OS per physical drive, so that partitioning errors are alleviated. That being said, I have discovered that if I use the command ```
ubiquity kde_ui
``` in a terminal or click on the desktop icon (which invokes the same command) the crash occurs. If I just type in ```
ubiquity
``` the system installs with no problem at all (well, other than the slideshow disappearing and taking me back to the desktop, but the install continues as if everything is hunky-dory)! After the install is complete, a restart dialog pops up, so that I know that the install completed. Just to confirm, I changed the command for the desktop shortcut to **ubiquity** from ***ubiquity kde_ui*** and the install goes without a hitch (save for the installer progress and slideshow disappearing during the actual install)! So, it appears that the error occurs when using the **kde_ui** option of the command. :confused: I have not tried with just *kde* or *kde4* as an option, though.

---

