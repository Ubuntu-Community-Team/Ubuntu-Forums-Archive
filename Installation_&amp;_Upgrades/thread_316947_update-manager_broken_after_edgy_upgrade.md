---
title: "update-manager broken after edgy upgrade"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by philosophia on 2006-12-11
I tried to upgrade from dapper to edgy.  The upgrade seems only partly successful.  When I reboot after the upgrade, I'm not able to run update-manager.

I get:> 
root@tangerine:/home/possum# update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 59, in ?
    import dbus
  File "/var/lib/python-support/python2.4/dbus/__init__.py", line 1, in ?
    from _dbus import *
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 48, in ?
    from proxies import *
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 2, in ?
    import introspect_parser
  File "/var/lib/python-support/python2.4/dbus/introspect_parser.py", line 1, in ?
    import libxml2
  File "/var/lib/python-support/python2.4/libxml2.py", line 1, in ?
    import libxml2mod
ImportError: /var/lib/python-support/python2.4/libxml2mod.so: undefined symbol:
xmlXPathContextSetCache

I followed this guide when upgrading.
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

I tried
gksu "update-manager -c" 
to upgrade first - but it did not seem to work.  When I rebooted I was still in dapper.

I then tried the apt-get upgrade method on this page.
It seems to have worked partly. 
> 
root@tangerine:/home/possum# lsb_release -r
Release:        6.10

but I still get the update-manager problem, and I'm not sure what else may be broken.  Anyone else experience this problem?

I have already tried reinstalling ubuntu-standard, ubuntu-minimal and ubuntu-desktop.  It tells me that these packages are already upgraded to the latest version.

I have also tried reinstalling update-manager with synaptic.  It tells me I need also reinstall ubuntu-desktop.  I remove and reinstall ubuntu-desktop, then I attempt to reinstall update-manager.  When I try to reinstall update-manager I get an error:
> 
E: update-manager: subprocess post-installation script returned error exit status 127


---

### Post by philosophia on 2006-12-12
I'm bumping this, still having this problem.

I'd really avoid having to wipe this machine just to get update-manager working again.

---

### Post by rtmie on 2006-12-26
I had a similar problem, but not form after I upgraded. All was fine then for a while but something I did obviously broke things ( It may have been to do with something I was installing at some point). 
Here's the work around I found for now:
 I found that by checking the link dependenies of libxslt 
(ldd /usr/lib/libxslt.so.1) that it was dependent on a version of libxml2 in /usr/local/lib, rather than the one in /usr/lib.
Checking both of these librarires for symbols shows :
# nm -D /usr/lib/libxml2.so.2|grep xmlXPathContextSetCache 
00000000000780a0 T xmlXPathContextSetCache
# nm -D /usr/local/lib/libxml2.so.2|grep xmlXPathContextSetCache

does not locate any symbol for xmlXPathContextSetCache

So what I did was to cd to /usr/local/lib
sudo mv libxml2.so.2 libxml2.so.2.orig
sudo ln -s /usr/lib/libxml2.so.2


This solves the scrollkeeper update problem in apt-get , and I have seen no bad effects. I am still not sure how I have 2 libxml2's and how libxslt is pointing at the wrong one, may be related to some other thing I installed but I have no recollection. It would be interesting to see what those ldd's return on a pristinely upgraded edgy.

Rob

---

