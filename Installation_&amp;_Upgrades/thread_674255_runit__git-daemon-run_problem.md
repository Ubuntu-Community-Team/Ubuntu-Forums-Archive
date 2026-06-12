---
title: "runit / git-daemon-run problem"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Hugh Mulqueen on 2008-01-21
Hi, 

Hope someone could help.
today i started installing a program called rdesktop and I ran into a problem.

I used apt-get and got this in return:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
rdesktop is already the newest version.
The following packages were automatically installed and are no longer required:
  nautilus-actions lame
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing git-daemon-run (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help!!!!!
Thanks

---

### Post by Hugh Mulqueen on 2008-01-21
Okay I fixed it, 

All you have to do is uninstall RUNIT with Synaptic (git-daeomon-run will also be uninstalled) and everything will just be the way you left it.

:guitar:      

Good Luck!!!

---

