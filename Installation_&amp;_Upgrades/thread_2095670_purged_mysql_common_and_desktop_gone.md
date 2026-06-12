---
title: "purged mysql common and desktop gone"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by psychowants2bgeek on 2012-12-17
I wanted to uninstall mysql completely to install mariadb, and now system is locked. I did apt-get purge mysql-server mysql-common mysql-client in Kubuntu, it deleted all the dependencies, so, I wanted to install mariadb according to instruction, but before adding the source list I got dpkg lock error for sudo. I tried to resolve it by dpkg --configure, it didn't help, so, I reboot the system. After reboot the system loads but fails to load kubuntu desktop, I tried to edit source list in recovery mode, the terminal says it only has read power even though being root. 
I again reboot the system and hit Ctrl-Alt-F1 to login as root, i did sudo apt-get update and it shows internet connection error. 
I manually edited the network config file again no internet connection. In between I get 
```
sd 5:0:0:0: [sdb] Asking for cache data failed
sd 5:0:0:0: [sdb] Assuming drive cache: write though
```
any help would be appreciated, and the system doesn't connect to internet to do ap-get updates or installs

---

