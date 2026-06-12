---
title: "Package system broken"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by fourhendrik on 2016-03-25
Hi I can't update any longer, and  sudo apt-get -f install
gives me below. any ideas? I think it's something with me previously having installed an arm cross compiler package

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libstdc++6-armhf-cross
The following packages will be upgraded:
  libstdc++6-armhf-cross
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
2 not fully installed or removed.
Need to get 0 B/210 kB of archives.
After this operation, 77.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 363896 files and directories currently installed.)
Preparing to unpack .../libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++6-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) over (4.8.2-16ubuntu4cross0.11) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:i386 4.8.4-2ubuntu1~14.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks, Hendrik

---

### Post by fourhendrik on 2016-03-25
Nevermind, fixed with
sudo dpkg --remove --force-remove-reinstreq libgcc1-armhf-cross libgcc1-dbg-armhf-cross libgomp1-armhf-cross libgomp1-dbg-armhf-cross libsfasan0-armhf-cross libsfatomic1-armhf-cross libsfgcc-4.8-dev-armhf-cross libsfgcc1-armhf-cross libsfgomp1-armhf-cross libsfstdc++-4.8-dev-armhf-cross libsfstdc++6-armhf-cross libstdc++-4.8-dev-armhf-cross libstdc++6-armhf-cross linux-libc-dev-armhf-cross

followed by update.

---

