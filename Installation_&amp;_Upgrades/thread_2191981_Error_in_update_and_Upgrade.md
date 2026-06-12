---
title: "Error in update and Upgrade"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by bte_rajan on 2013-12-05
When I use

 sudo apt-get update && sudo apt-get upgrade

I got following error message. [COLOR=#ff6600][/COLOR]

Do you want to continue [Y/n]? y
(Reading database ... 273809 files and directories currently installed.)
Preparing to replace linux-firmware 1.79.7 (using .../linux-firmware_1.79.9_all.deb) ...
Unpacking replacement linux-firmware ...
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.79.9_all.deb (--unpack):
 trying to overwrite '/lib/firmware/ar3k/ramps_0x31010000_40.dfu', which is also in package bt-dw1705-firmware 0.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_1.79.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help, how can i resolve the issue ??

---

### Post by fantab on 2013-12-05
What version of Ubuntu are you using?

See if the following commands offer any help:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

If you still get the same error then:
```
gksudo nautilus
```
Navigate to folder /var/cache/apt/archives and locate the file 'linux-firmware_1.79.9_all.deb'. Delete it.
Then repeat the above commands.

---

### Post by bte_rajan on 2013-12-05
Thanks a lot

---

