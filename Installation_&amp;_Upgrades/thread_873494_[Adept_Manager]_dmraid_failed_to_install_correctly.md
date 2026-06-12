---
title: "[Adept Manager] dmraid failed to install correctly"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by castor_fou on 2008-07-29
From a fresh install of kubuntu (8.04.1), I want to access my raid 1 data disk.
For that I have started Adpet Manager, and selected dmraid to be installed.
When applying the changes, a window appears saying:
```

Could not commit changes - Adpet Manager
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
```

However dmraid is installed, I can detect and mount my raid partitions.
Each time I install something through Adept Manager, I encounter this error (due to dmraid).

In command line, here is the output (with an example installing tree):
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  tree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 28.4kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com hardy/universe tree 1.5.1.1-1 [28.4kB]
Fetched 28.4kB in 0s (106kB/s)
Selecting previously deselected package tree.
(Reading database ... 93968 files and directories currently installed.)
Unpacking tree (from .../tree_1.5.1.1-1_i386.deb) ...
Setting up dmraid (1.0.0.rc14-0ubuntu3.1) ...
 * Setting up DMRAID devices...                                                 invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error processing dmraid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tree (1.5.1.1-1) ...
Errors were encountered while processing:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems dpkg tries to (re)configure and for a reason it fails at the start command.
Any help would be appreciated.

---

### Post by kuja on 2008-07-29
Try to remove the dmraid package, then attempt again at installing (either through adept, or use "[color=gray]sudo dpkg -r dmraid[/color]" or "[color=gray]sudo apt-get remove dmraid[/color]" in a shell if it doesn't work there) Afterwards, clear the downloaded package cache ("[color=gray]sudo apt-get clean[/color]"), update, and try to install dmraid again.

---

### Post by castor_fou on 2008-07-30
> **kuja said:**
> Try to remove the dmraid package, then attempt again at installing (either through adept, or use "[color=gray]sudo dpkg -r dmraid[/color]" or "[color=gray]sudo apt-get remove dmraid[/color]" in a shell if it doesn't work there) Afterwards, clear the downloaded package cache ("[color=gray]sudo apt-get clean[/color]"), update, and try to install dmraid again.

I go on vacations tonight, I won't have time to test that but I will (end of August).
However I am quite sure I have tested that and I cannot uninstall dmraid because it tries to stop dmraid and it fails. However I will do it again and will post the messages.

---

