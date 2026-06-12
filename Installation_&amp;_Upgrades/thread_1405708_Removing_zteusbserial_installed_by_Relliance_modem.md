---
title: "Removing zteusbserial installed by Relliance modem"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by unnipk on 2010-02-13
I am unable to run upgrade or synaptic package manager because of a software "zteusbserial' installed when I used a Relliance netconnect modem.
When i try to remove this through the Synaptic Package manager the error message is:

**E: zteusbserial: subprocess installed post-removal script returned error exit status 1**

Running  apt-get remove gives:
[B]sudo apt-get remove zteusbserial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  zteusbserial
0 upgraded, 0 newly installed, 1 to remove and 122 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
[/B]
sudo killall zteusbserial gives:

**zteusbserial: no process found**

I tried the solution provided in "http://ubuntuforums.org/showthread.php?t=1276312&highlight=Uninstall+ZTE-AC2726+modem", but that too didn't work.

---

