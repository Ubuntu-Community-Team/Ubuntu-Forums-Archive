---
title: "error processing /var/cache/apt/archives/libc6_2.10.1-0ubuntu16_i386.deb"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by yasokrish on 2010-04-16
[B]My system instructed me to try this command when i tried installing lamp server
 
sudo apt-get -f install[/B]
 [B] and the output of the above command is: 

[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 247 not upgraded.
3 not fully installed or removed.
Need to get 0B/4,958kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
[B]Preconfiguring packages ...
(Reading database ... 116183 files and directories currently installed.)
Preparing to replace libc6 2.10.1-0ubuntu15 (using .../libc6_2.10.1-0ubuntu16_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6_2.10.1-0ubuntu16_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.10.1-0ubuntu16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What error is this and how do i rectify it??
Please do help me in fixing this error and install lamp-server.

thank u,
yasokrish.

[/B]

---

