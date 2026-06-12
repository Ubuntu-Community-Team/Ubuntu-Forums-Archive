---
title: "ubuntu 12.04 having issues after synaptic package manager upgrade"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2014-04-14
HI all
 i have recently tried to update my package via synaptic package manager, but something was broken and i am left with a red icon on the top of my screen
the exeption below when trying to fix it.
I got notified , after an error in installing upgrades, to run apt-get install -f but i got this message. anyone could assist pls?

```

marco@marco-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  default-jre-headless
The following NEW packages will be installed
  default-jre-headless
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,328 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 263457 files and directories currently installed.)
Unpacking default-jre-headless (from .../default-jre-headless_1%3a1.6-43ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-1.6.0-openjdk', which is also in package openjdk-6-jre-headless 6b24-1.11.5-0ubuntu1~11.10.1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
marco@marco-laptop:~$ 

```

---

### Post by Ubi_one_2014 on 2014-04-14
my first impression:
apt-get remove [COLOR=#000000][FONT=Ubuntu Mono]default-jre-headless[/FONT][/COLOR]

---

