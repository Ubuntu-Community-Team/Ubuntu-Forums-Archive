---
title: "transmission-daemon update error"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by bgabga on 2010-08-04
I have an error when I try to update or remove transmission-daemon package. 
Please help!
Here are some logs:

root@ubuntu:~# apt-get --reinstall install transmission-daemon
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libopenraw1 gthumb-data linux-headers-2.6.32-21-generic cu librrd4 linux-headers-2.6.32-21 ttf-dejavu libopenrawgnome1 openbsd-inetd
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  transmission-daemon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 217kB of archives.
After this operation, 4,096B of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe transmission-daemon 1.93-0ubuntu0.10.04.1 [217kB]
Fetched 217kB in 1s (206kB/s)
Selecting previously deselected package transmission-daemon.
(Reading database ... 227059 files and directories currently installed.)
Preparing to replace transmission-daemon 1.92-0ubuntu2.1 (using .../transmission-daemon_1.93-0ubuntu0.10.04.1_amd64.deb) ...
/etc/init.d/transmission-daemon: 11: -g: not found
invoke-rc.d: initscript transmission-daemon, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/etc/init.d/transmission-daemon: 11: -g: not found
invoke-rc.d: initscript transmission-daemon, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/transmission-daemon_1.93-0ubuntu0.10.04.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/etc/init.d/transmission-daemon: 11: -g: not found
invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/transmission-daemon_1.93-0ubuntu0.10.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




root@ubuntu:~# apt-get --purge remove transmission-daemon
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libopenraw1 gthumb-data linux-headers-2.6.32-21-generic cu librrd4 linux-headers-2.6.32-21 ttf-dejavu libopenrawgnome1 openbsd-inetd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  transmission-daemon*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 553kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing transmission-daemon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bgabga on 2010-08-09
If I go to Synaptic Package Manager, transmission-daemon is marked as Broken!
How can I remove transmission-daemon 1.92-0ubuntu2.1 from my system?
Thank you,

---

### Post by bgabga on 2010-08-13
Found it!

I did:

dpkg -L transmission-daemon

then I removed the files:


/var/lib/transmission-daemon
/var/lib/transmission-daemon/info
/var/lib/transmission-daemon/downloads
/usr/share/man/man1/transmission-daemon.1.gz
/usr/bin/transmission-daemon
/etc/default/transmission-daemon
/etc/init.d/transmission-daemon
/etc/transmission-daemon
/var/lib/transmission-daemon/info/settings.json  (not sure)
/usr/share/doc/transmission-daemon


then from System Package Manager I selected the transmission-daemon broken package to be updated (if you select remove, will not work)

---

