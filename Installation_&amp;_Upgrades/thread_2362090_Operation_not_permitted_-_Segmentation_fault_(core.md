---
title: "Operation not permitted - Segmentation fault (core dumped)"
date: 2017-05-24
forum: Installation &amp; Upgrades
---

### Post by ldbrizzle on 2017-05-24
Whilst performing a routine upgrade of components on an Ubuntu server hosted in Microsoft Azure, I received the following.

```

ldadmin@azr-ext-web01:/var/www$ sudo -s
root@azr-ext-web01:/var/www# apt-get update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
Reading package lists... Done

```

```

root@azr-ext-web01:/var/www# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
linux-headers-4.4.0-78-generic : Depends: linux-headers-4.4.0-78 but it is not installed
E: Unmet dependencies. Try using -f.

```

Fair enough, not out of the ordinary. However, when I run apt-get -f install:

```
root@azr-ext-web01:/var/www# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-cloud-tools-4.4.0-75 linux-cloud-tools-4.4.0-75-generic linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-70 linux-headers-4.4.0-70-generic linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-64-generic linux-image-4.4.0-66-generic linux-image-4.4.0-70-generic
  linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-66-generic
  linux-image-extra-4.4.0-70-generic linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-78
The following NEW packages will be installed:
  linux-headers-4.4.0-78
0 upgraded, 1 newly installed, 0 to remove and 49 not upgraded.
4 not fully installed or removed.
Need to get 0 B/9,968 kB of archives.
After this operation, 70.5 MB of additional disk space will be used.
Do you want to continue? [Y/n]
(Reading database ... 240373 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-78_4.4.0-78.99_all.deb ...
Unpacking linux-headers-4.4.0-78 (4.4.0-78.99) ...
[COLOR=#ff0000]dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.4.0-78_4.4.0-78.99_all.deb (--unpack):[/COLOR]
[COLOR=#ff0000] unable to open '/usr/src/linux-headers-4.4.0-78/arch/mips/include/asm/mach-ip27/cpu-feature-overrides.h.dpkg-new': Operation not permitted[/COLOR]
Segmentation fault (core dumped)

```

I have tried "apt autoremove", clearing "/var/cache/apt/archives" and running "dpkg --configure -a" to no avail.

I am reluctant to restart the server at this point in case it fails to come back up again.

---

### Post by ldbrizzle on 2017-05-24
Bump

---

### Post by ldbrizzle on 2017-06-05
Nothing?

---

