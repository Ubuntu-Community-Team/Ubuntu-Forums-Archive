---
title: "Problems upgrading/removing tor"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by sleight82 on 2007-04-15
I am having difficulty removing tor after upgrading from Dapper to Edgy. The tor daemon cannot be stopped. I tried manually stopping the tor daemon as well. /var/lib/tor only has a file called cached-directory.

[INDENT]root@matsumoto:/var/lib# sudo apt-get remove tor
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tor
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  tor
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1147kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 140531 files and directories currently installed.)
Removing tor ...
 * Stopping tor daemon (tor)...                                                                         [fail]
invoke-rc.d: initscript tor, action "stop" failed.
dpkg: error processing tor (--remove):
 subprocess pre-removal script returned error exit status 1
debian-tor uid check: ok
debian-tor homedir check: ok
 * Starting tor daemon (tor)...                                                                                Apr 15 11:50:05.787 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
                                                                                                        [ ok ]
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

---

