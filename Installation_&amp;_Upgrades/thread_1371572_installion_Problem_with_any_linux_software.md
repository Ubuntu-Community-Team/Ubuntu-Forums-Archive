---
title: "installion Problem with any linux software"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by aaydinalp on 2010-01-03
I want to  install ifuse software to ubuntu and then I got broken  system
I can't install any software and I can't upgrade either
I used sudo apt-get install -f
It didn't work
and I also try remove ifuse it didn't work
Now I have broken  system in ubuntu
I am using ubuntu  10.04 alpha 1
Please help me What can I do
I can't use cd  too
it says can't mount either
what can I do
It says like that[B]
root@anil-laptop:~$ sudo apt-get remove ifuse
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ifuse-dbg: Depends: ifuse (= 0.9.4-1ubuntu3~j) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

[/B] [B]root@anil-laptop:/home/anil# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libusbmux0
The following NEW packages will be installed:
  libusbmux0
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0B/32.6kB of archives.
After this operation, 135kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 190782 files and directories currently installed.)
Unpacking libusbmux0 (from .../libusbmux0_1.0.0-rc1-1ubuntu3~j_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmux0_1.0.0-rc1-1ubuntu3~j_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmuxd1 0:1.0.1-0ubuntu1~j
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmux0_1.0.0-rc1-1ubuntu3~j_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

---

### Post by garryknight on 2010-01-03
> **aaydinalp said:**
> [B]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
...
[/B] [B]root@anil-laptop:/home/anil# apt-get install -f
[/B]

Spot the error.

---

### Post by iTheBadGuy on 2010-01-03
Yeah, it says "-f install" not "install -f"

---

### Post by aaydinalp on 2010-01-04
okay I did something and I solved problem 
I used synaptic package manager 
and I search ifuse and then delete it
my problem stopped

---

