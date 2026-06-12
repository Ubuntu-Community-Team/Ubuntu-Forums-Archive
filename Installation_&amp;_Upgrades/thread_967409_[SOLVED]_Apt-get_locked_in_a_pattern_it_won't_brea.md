---
title: "[SOLVED] Apt-get locked in a pattern it won't break out of."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by karldiechmann on 2008-11-02
Hey, so my apt-get is rendered useless by a backlog that won't go away.  Anyone have any idea how I can make it sort through all this?
```

karl@karl-desktop:~$ sudo apt-get install
[sudo] password for karl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
91 not fully installed or removed.
Need to get 0B/187kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 190705 files and directories currently installed.)
Preparing to replace gnome-applets 2.24.1-0ubuntu1 (using .../gnome-applets_2.24.1-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
/var/lib/dpkg/info/gnome-applets.postrm: 30: update-gconf-defaults: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 30: update-gconf-defaults: not found
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 30: update-gconf-defaults: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2008-11-02
Try moving the gnome-applets.postrm out of the way then reinstalling the package
```
sudo mv /var/lib/dpkg/info/gnome-applets.postrm /var/lib/dpkg/info/gnome-applets.postrm.old
```then
```
sudo apt-get --reinstall install gnome-applets
``````
sudo apt-get install -f
```

---

