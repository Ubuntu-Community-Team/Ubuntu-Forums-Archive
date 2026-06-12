---
title: "Xserver-common-lts-raring"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by addison2 on 2013-09-05
Running ubuntu 13.04 (2007 IMac)

"Could not install 'xserver-common-lts-raring'
The upgrade will  continue but the 'xserver-common-lts-raring' package may not be in a  working state. Please consider submitting a bug report about it." 

can not update, upgrade, or remove the "xserver-common-lts-raring" package or other packages since it is in an unusable state.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'xserver' can't be removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39 linux-headers-3.5.0-39-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-common-lts-raring
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,645 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 224326 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by adam7 on 2013-09-06
I'm having the same problem, just upgraded to 13.04 from 12.10 on a Toshiba ultrabook. In the meantime I was able to install other packages manually by running

```
sudo apt-get download <package_name>
sudo dpkg -i <downloaded_package_file>
```

---

### Post by adam7 on 2013-09-06
Some googling around led me here: [http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

Solution was to edit the file "/var/usr/dpkg/info/xserver-common-lts-raring.postrm" and remove the dpkg-divert command entirely. sudo apt-get autoremove was then able to uninstall the package correctly. Seems to have worked, I'm able to install packages normally now.

---

### Post by anastasia2 on 2013-09-17
Hi! I am having exactly the same problem, and I tryied to do what you are saying but there is no change...When I remove the dpkg-divert command the file cannot be saved...What is happening?

---

### Post by destroyerzx12 on 2013-09-27
to edit the file you need to go to terminal and type sudo nautilus             it will ask for your password then after that a window will pop up go to the file from there and you can edit it. I tried it but am still having the same problem

---

### Post by sertorassa on 2014-01-22
On my machine the directory where to find the postrm file is /var/[COLOR=#ff0000]**lib**[/COLOR]/dpkg/info

---

