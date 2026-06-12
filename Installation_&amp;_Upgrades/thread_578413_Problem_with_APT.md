---
title: "Problem with APT"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by lybbe on 2007-10-17
Hi,

I'm running Ubuntu Server, and ever since i tried Zenoss my apt been messed up. Every time i install/upgrade any packages i get the following:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up update-manager-core (0.59.25) ...
/var/lib/dpkg/info/update-manager-core.postinst: 6: pycentral: not found
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 update-manager-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

In the install guide for Zenoss it says the following:

```
10. Feisty Fawn ships with Python 2.5, but certain dependencies of Zenoss are
    unable to build properly with this version. Once Zenoss has been installed,
    it will run just fine under 2.5, but we'll need to change the symlink for
    the installation. Run:

      unlink /usr/bin/python && ln -s /usr/bin/python2.4 /usr/bin/python
```

Which i did, and after install:

```
Switch back the Python symlinks:

      unlink /usr/bin/python && ln -s /usr/bin/python2.5 /usr/bin/python
```

Since then APT is messed up. How can i restore this to make it work again?

Thanks in advance

---

### Post by lybbe on 2007-10-17
Nevermind. Case solved by reinstalling python2.5

---

