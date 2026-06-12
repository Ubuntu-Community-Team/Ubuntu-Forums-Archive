---
title: "Error on upgrade or install a package"
date: 2024-01-18
forum: Installation &amp; Upgrades
---

### Post by krmnmaria on 2024-01-18
Hi to all, 

I´ve encountered a problem when I try to upgrade or install any package:

This is the result to execute the command ***sudo apt update && sudo apt upgrade***:

[I]Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 61996 files and directories currently installed.)
Preparing to unpack .../libc6_2.35-0ubuntu3.6_amd64.deb ...
dpkg (subprocess): unable to execute new libc6:amd64 package pre-installation script (/var/lib/dpkg/tmp.ci/preinst): Permission denied
dpkg: error processing archive /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb (--unpack):
 new libc6:amd64 package pre-installation script subprocess returned error exit status 2
dpkg (subprocess): unable to execute new libc6:amd64 package post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error while cleaning up:
 new libc6:amd64 package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


I followed these steps to try to fix it:
1. sudo chmod 1777 /var/lib/dpkg/
2. sudo rm -rf /var/lib/dpkg/tmp.*
3. sudo dpkg --force-all -i /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb (to force the instalation without preinstalation scripts)
At this point I obtain a similar error
4. Repair unmet dependencies: sudo apt --fix-broken install
At this point I obtain a similar error (permission denied)
5. Reboot the system
Nothing works

Has anyone faced something similar? 
Please, any help will be apretiated.

Thnx
Carmen

---

### Post by krmnmaria on 2024-01-18
Hi. community
the problem is solved!:
[I]
Fixed fstab file, as the /var/ partition was mounted as noexec
[/I]

---

