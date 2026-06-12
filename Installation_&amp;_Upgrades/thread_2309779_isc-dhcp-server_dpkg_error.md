---
title: "isc-dhcp-server dpkg error"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by xWEkxhW on 2016-01-13
My system is encountering a dpkg error while attempting to update the isc-dhcp-server package. Any ideas how to solve? Thanks


```
The following packages will be upgraded:
  isc-dhcp-server
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
9 not fully installed or removed.
Need to get 360 kB of archives.
After this operation, 71.7 kB disk space will be freed.
Do you want to continue? [Y/n]
Get:1 http://gb.archive.ubuntu.com/ubuntu/ wily-updates/main isc-dhcp-server amd64 4.3.1-5ubuntu3.1 [360 kB]
Fetched 360 kB in 0s (821 kB/s)
Preconfiguring packages ...
(Reading database ... 228170 files and directories currently installed.)
Preparing to unpack .../isc-dhcp-server_4.3.1-5ubuntu3.1_amd64.deb ...
Failed to stop isc-dhcp-server6.service: Unit isc-dhcp-server6.service not loaded.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop isc-dhcp-server6.service: Unit isc-dhcp-server6.service not loaded.
dpkg: error processing archive /var/cache/apt/archives/isc-dhcp-server_4.3.1-5ubuntu3.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 /var/cache/apt/archives/isc-dhcp-server_4.3.1-5ubuntu3.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

