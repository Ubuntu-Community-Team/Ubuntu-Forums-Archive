---
title: "Feisty to Gutsy opendchub upgrade problem"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by G4HZA on 2007-10-22
I have upgrated from Feisty to Gutsy and have one residual problem.  opendchub will not update properly.  I have shown the output from a manual attempt.  Does anyone have any suggestions on resolving this?

Roger

apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  opendchub
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 103kB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe opendchub 0.7.15-1 [103kB]
Fetched 103kB in 2s (37.1kB/s)
(Reading database ... 144890 files and directories currently installed.)
Preparing to replace opendchub 0.7.14-2ubuntu1 (using .../opendchub_0.7.15-1_i386.deb) ...
Stopping Open DC Hub: opendchubTerminated
invoke-rc.d: initscript opendchub, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 143
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/opendchub_0.7.15-1_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Starting Open DC Hub: opendchubEnter port number to listen for connections.
Ports below 1024 is only for root: dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 /var/cache/apt/archives/opendchub_0.7.15-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

