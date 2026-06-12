---
title: "Dependency troubles due to kdesvn on xenial"
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by reggler on 2017-11-04
Hi,

Okay, here's the story: I'm on xenial and need kdesvn which is not part of the repos... (I've been trying out other alternative svn GUIs but didn't find nothing I liked).
Since that system is behind a firewall and access to PPAs is blocked, I compiled kdesvn on a different system (xenial too) where access to PPAs is fine following this: [https://askubuntu.com/questions/971056/failure-to-compile-kdesvn-from-source/971587?noredirect=1](https://askubuntu.com/questions/971056/failure-to-compile-kdesvn-from-source/971587?noredirect=1) which worked like a charm. I then copied the final binary to the initial system, tried to start the binary but got:
```
kdesvn: /usr/lib/x86_64-linux-gnu/libQt5Xml.so.5: version `Qt_5' not found (required by kdesvn)
kdesvn: /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5: version `Qt_5' not found (required by kdesvn)
kdesvn: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5: version `Qt_5' not found (required by kdesvn)
kdesvn: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5: version `Qt_5.6' not found (required by kdesvn)
kdesvn: /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5: version `Qt_5' not found (required by kdesvn)
```
so I'm obviously missing dependencies (as expected). I googled and found that **libqt5xml5** contains the missing libQt5Xml.so.
But when I tried to apt install it, I got:
```
$ sudo apt install libqt5xml5
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt5xml5 is already the newest version (5.5.1+dfsg-16ubuntu7.5).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
So...
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpthread-stubs0-dev:i386 libx11-dev:i386 libxau-dev:i386 libxcb1-dev:i386 libxdmcp-dev:i386 libxext-dev:i386 libxfixes-dev:i386 libxtst6:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
444 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n]
(Reading database ... 303598 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
and then
```

$ sudo apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.

```
How can I get this resolved? I've tried **update** & **upgrade** but that doesn't get me any further either...

---

### Post by oldos2er on 2017-11-04
I'm guessing the package you need is libqt5xmlpatterns5-dev. Do you have that installed?

---

### Post by ian-weisser on 2017-11-04
> **reggler said:**
> 
Unpacking **kde-config-telepathy-accounts** (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package **account-plugin-google** 0.12+16.04.20160126-0ubuntu1

Those two packages conflict. You cannot have both installed at the same time.

Most package conflicts are caused by non-Ubuntu software, but seeming not this time Both version numbers look like they came from Ubuntu.

Seems like a real bug: Please file a bug report against *both* packages (on the same report).

---

### Post by vasa1 on 2017-11-05
Just wondering if *entw*'s answer in [https://ubuntuforums.org/showthread.php?t=2374270](https://ubuntuforums.org/showthread.php?t=2374270) will work.

---

### Post by reggler on 2017-11-08
No, I got this:
```

$ sudo dpkg -r account-plugin-google
dpkg: dependency problems prevent removal of account-plugin-google:
 unity-scope-gdrive depends on account-plugin-google.

dpkg: error processing package account-plugin-google (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 account-plugin-google

```
so i tried to remove unity-scope-gdrive
```

$ sudo apt remove unity-scope-gdrive
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
and
```

$ sudo apt remove kde-telepathy-minimal
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ron@jpax-build07:~$ sudo apt remove kde-telepathy-minimal
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ron@jpax-build07:~$ sudo apt remove kde-telepathy
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ron@jpax-build07:~$

```
**but this let me remove stuff seemingly succesfully:**
```

ron@jpax-build07:~$ sudo apt remove kde-telepathy-minimal kde-telepathy

```

---

