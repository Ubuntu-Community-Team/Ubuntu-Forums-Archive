---
title: "bzip2 security upgrade fails"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Dean Powell on 2008-03-26
Hi:

I have been trying to install a security update to bzip2.  I get the following:

(Reading database ... 152021 files and directories currently installed.)
Preparing to replace bzip2 1.0.3-6build1 (using .../bzip2_1.0.3-6ubuntu0.1_i386.deb) ...
Document `bzip2' is not installed, cannot remove.
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Document `bzip2' is not installed, cannot remove.
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/bzip2_1.0.3-6ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: No such file or directory for General Commands
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-6ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of bzip2:
 bzip2 depends on libbz2-1.0 (= 1.0.3-6build1); however:
  Version of libbz2-1.0 on system is 1.0.3-6ubuntu0.1.
dpkg: error processing bzip2 (--configure):
 dependency problems - leaving unconfigured


I have tried reloading the sources list.  No luck.
I now cannot run the upgrade manager at all.  I am running Feisty.  The latest security download was attempted March 26, 2008.

Any ideas?

---

### Post by zvacet on 2008-03-26
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dean Powell on 2008-03-26
Hi.

Thanks for the tip, but no joy.  From your suggested commands, I get:

Fetched 159kB in 7s (20.5kB/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bzip2: Depends: libbz2-1.0 (= 1.0.3-6build1) but 1.0.3-6ubuntu0.1 is installed
E: Unmet dependencies. Try using -f.

So I try sudo apt-get update && sudo apt-get upgrade -f

This gives me:
Correcting dependencies... Done
The following packages will be upgraded:
  bzip2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/266kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]

Saying 'Y' returns:
(Reading database ... 152021 files and directories currently installed.)
Preparing to replace bzip2 1.0.3-6build1 (using .../bzip2_1.0.3-6ubuntu0.1_i386.deb) ...
Document `bzip2' is not installed, cannot remove.
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Document `bzip2' is not installed, cannot remove.
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/bzip2_1.0.3-6ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: No such file or directory for General Commands
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-6ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is the same error as before.

Any idea what's wrong?  Can I completely rebuild the aptitude database from scratch without resorting to a total re-install?

Thanks for any information.

---

