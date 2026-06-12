---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-10-16
forum: Installation &amp; Upgrades
---

### Post by afkintzer on 2015-10-16
Got this error when trying to install Wine 1.7. Error actually shows up during any installation, but this is part of the Wine package apparently. File does not exist according to `dpkg -L ttf-mscorefonts-installer`

Any ideas?

Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package ttf-mscorefonts-installer (--configure):
 package ttf-mscorefonts-installer is not ready for configuration
 cannot configure (current status `half-installed')
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by slickymaster on 2015-10-16
Hi afkintzer, welcome to the forums.

Can you please try, in a terminal window:```
sudo apt-get clean
sudo apt-get install --reinstall ttf-mscorefonts-installer
```When presented with the End User License Agreement (EULA) in the Terminal, press the <Tab> key to select the "<Ok>" button, then press <Enter>.

---

