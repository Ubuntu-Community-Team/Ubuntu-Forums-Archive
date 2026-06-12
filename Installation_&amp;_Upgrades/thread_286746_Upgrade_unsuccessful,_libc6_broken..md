---
title: "Upgrade unsuccessful, libc6 broken."
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by indridi on 2006-10-28
Hello

I am trying to upgrade from dapper to edgy on my thinkpad R40. As suggested [here]("https://help.ubuntu.com/community/EdgyUpgrades"), I updated my sources.list, and ran
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```
It downloaded lots of packages, and installed some of them (happened in the night, was sleeping), but when upgrading libc6, an error occured, complaining about libdl.so.2
Now, when I run dist-upgrade, I get this
```

[indridi@edelstoff][...home/indridi] sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12) but 2.3.6-0ubuntu20 is installed
E: Unmet dependencies. Try using -f.

```
Running apt-get -f install, I get this:
```

[indridi@edelstoff][...home/indridi] sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 1690 not upgraded.
2 not fully installed or removed.
Need to get 0B/5253kB of archives.
After unpacking 233kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 409126 files and directories currently installed.)
Preparing to replace libc6 2.3.6-0ubuntu20 (using .../libc6_2.4-1ubuntu12_i386.deb) ...
Unpacking replacement libc6 ...
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: error while cleaning up:
 subprocess pre-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
which is the same error as when I ran dist-upgrade for the first time.
libdl.so.2 is in it's place (/lib/libdl.so.2), and I have no idea what to do next. My system is up and is now probably running some weard cross-bread between dapper and edgy (and yes, I have done the reboot-thing, which doesn't change anything as it would with some other OSes)

\begin{edit}
As seen [here]("http://www.ubuntuforums.org/showthread.php?t=286599"), the update-manager -c method is supposedly preferred, but I didn't know that yesterday, and now it doesn't work, because of the broken package, but instead advises me to run apt-get -f install
\end{edit}

please help
Indriði

---

### Post by greew on 2006-10-28
I just pasted my problem in [http://ubuntuforums.org/showthread.php?t=286751](http://ubuntuforums.org/showthread.php?t=286751) but I can see that this problem is quite similar to mine, so I'll just follow along!

---

### Post by indridi on 2006-10-30
greew, I'm not sure this is the same problem, but anyways, I found the solution.
In my .bashrc, I had a variable name LD_ASSUME_KERNEL (=2.4.1), this is some hack to matlab to work (doesn't seem to be necessary anymore), and this f***s up the libc6 upgrade. As soon as I had unset this variable, the rest of the upgrade went smoothly.

---

