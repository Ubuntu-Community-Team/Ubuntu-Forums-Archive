---
title: "Can't 'do-release-upgrade' from 22.04 to 24.04 LTS (broken packages/dependencies)"
date: 2024-11-07
forum: Installation &amp; Upgrades
---

### Post by massimiliano-polito on 2024-11-07
Dear all,

As I wrote in this thread I'm having problems in fresh installing Ubuntu Studio 24.04 LTS so I decided to install 22.04 and do-release-upgrade from there.

Unfortunately, I ran into troubles because of some packages and their dependencies. I solved some issues but not the one with 'fontconfig-config'. Below are my attempts. Can you help me in understanding what's going on and how to fix it?

```

**max@ASUS-v221ic:~$ sudo apt clean**
[sudo] password for max: 
[B]max@ASUS-v221ic:~$
max@ASUS-v221ic:~$
max@ASUS-v221ic:~$ sudo apt autoremove[/B]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libfontconfig1 : Depends: fontconfig-config (>= 2.15.0-1.1ubuntu2)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[B]max@ASUS-v221ic:~$
max@ASUS-v221ic:~$
max@ASUS-v221ic:~$ 
max@ASUS-v221ic:~$ 
max@ASUS-v221ic:~$ sudo apt --fix-broken install[/B]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
 cyclist fonts-liberation2 foo-yc20 freeglut3 gamin genisoimage irqbalance libdbusmenu-gtk3-4 libdns-export1110 libgamin0 libisc-export1105 libkf5baloowidgets-data p7zip ppa-purge python3-pbr ubuntustudio-installer vlc-l10n vocproc
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
 fontconfig-config
The following packages will be upgraded:
 fontconfig-config
1 upgraded, 0 newly installed, 0 to remove and 1019 not upgraded.
12 not fully installed or removed.
Need to get 37,3 kB of archives.
After this operation, 68,6 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 fontconfig-config amd64 2.15.0-1.1ubuntu2 [37,3 kB]
Fetched 37,3 kB in 1s (62,9 kB/s) 
dpkg: warning: files list file for package 'fontconfig-config' missing; assuming package has no files currently installed
(Reading database ... 459810 files and directories currently installed.)
Preparing to unpack .../fontconfig-config_2.15.0-1.1ubuntu2_amd64.deb ...
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed

**[...]**

dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Unpacking fontconfig-config (2.15.0-1.1ubuntu2) over (2.13.1-4.2ubuntu5) ...
dpkg: error processing archive /var/cache/apt/archives/fontconfig-config_2.15.0-1.1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/etc/fonts/conf.d/10-sub-pixel-rgb.conf', which is also in package ubuntustudio-default-settings 22.04.26.3
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.

**[...]**

dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'fontconfig-config' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Errors were encountered while processing:
 /var/cache/apt/archives/fontconfig-config_2.15.0-1.1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[B]max@ASUS-v221ic:~$ 
max@ASUS-v221ic:~$[/B]

```

Thanks.

Ciao,
Max

---

### Post by ActionParsnip on 2024-11-07
Try:
```

sudo apt --reinstall install fontconfig-config

```
Then retry

---

### Post by ActionParsnip on 2024-11-07
Ah, this is the issue
```

dpkg: error processing archive /var/cache/apt/archives/fontconfig-config_2.15.0-1.1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/etc/fonts/conf.d/10-sub-pixel-rgb.conf', which is also in package ubuntustudio-default-settings 22.04.26.3

```
You have two packages with the same file. You can force upgrade fontconfig-config or remove one. Neither is great. Is there a bug for this?

---

### Post by massimiliano-polito on 2024-11-07
> **ActionParsnip said:**
> Ah, this is the issue
```

dpkg: error processing archive /var/cache/apt/archives/fontconfig-config_2.15.0-1.1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/etc/fonts/conf.d/10-sub-pixel-rgb.conf', which is also in package ubuntustudio-default-settings 22.04.26.3

```
You have two packages with the same file. You can force upgrade fontconfig-config or remove one. Neither is great. Is there a bug for this?

Thank you very much!

I've found [this thread]("https://askubuntu.com/questions/1501240/cannot-upgrade-ubuntu-studio-24-04-bcs-of-unmet-dependencies") on AskUbuntu that seems to have a good solution to fix it. I'll try it tonight and be probably back tomorrow with some good news :)

UPDATE: no...it doesn't work, updating from 22.04 to 24.04 seems impossible. However, I retried using a USB bootable stick and this time I succedeed. So somehow the problem is now solved.

Ciao,
Max

---

