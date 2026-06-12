---
title: "How to fix broken dpkg packages and dependencies?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by snakyjake on 2008-01-24
NOTE:  Resolution listed at end of post.  Contributing to those who might run into a similar issue.

I'm trying to update my distribution using "aptitude upgrade".  

I receive error messages after installing "bittorrent".

Error messages:
```

root@home-linux-2:~# **aptitude upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: **package python-bittorrent: already exists**: /usr/
lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2
.4/site-packages/BitTorrent/Choker.py
**dpkg: error processing python2.4-minimal (--configure):**
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/       lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2       .4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4

```

How do I fix this?

Tried the following:

**_apt-get install -f _**

```

root@home-linux-2:~# **apt-get install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**_dpkg --configure -a_**
```

root@home-linux-2:~# **dpkg --configure -a**
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4

```

**_aptitude -f remove_**
```

root@home-linux-2:~# **aptitude -f remove**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4

```

**_Using aptitude and then option "g"._**
```

root@home-linux-2:/var/cache/apt/archives# **aptitude**
(Reading database ... 96764 files and directories currently installed.)
Removing acroread ...
Removing firefox ...
Removing libldap2-dev ...
Removing libnss3 ...
Removing libnspr4 ...
Removing mozilla-thunderbird ...
Removing thunderbird ...
Removing libnspr4-0d ...
Removing wine ...
Removing amarok ...
Removing amarok-xine ...
Removing libtunepimp5 ...
Removing libofa0 ...
Removing fftw3 ...
Removing libgpod1 ...
Removing libifp4 ...
Removing libmtp5 ...
Removing ruby ...
Removing ruby1.8 ...
Removing libruby1.8 ...
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
pycentral rtinstall: package python-bittorrent: already exists: /usr/lib/python2.4/site-packages/BitTorrent/Choker.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4-2ubuntu7); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4

```

**_[SIZE="3"]*** SOLUTION ***[/SIZE]_**

Removed the originating package that started to give me the errors

```
dpkg -r bittorrent
```

```
aptitude upgrade
```

```

root@home-linux-2:/var/cache/apt/archives# aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python2.4-minimal (2.4.4-2ubuntu7) ...
Linking and byte-compiling packages for runtime python2.4...

Setting up python2.4 (2.4.4-2ubuntu7) ...

```

Problem with aptitude resolved (still have to resolve the BitTorrent issue, but that would be another thread).

---

