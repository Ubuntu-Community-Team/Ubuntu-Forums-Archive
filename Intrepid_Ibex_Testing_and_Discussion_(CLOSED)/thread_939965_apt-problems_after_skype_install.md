---
title: "apt-problems after skype install"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Johnsie on 2008-10-06
Hi, I tried to install skype from the skype website and now I'm having problems with apt:

> john@john-eee:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libqt4-test libqt4-core libqt4-gui
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  g++-4.3 gcc-4.3 libgcc1 libqt4-dbus libqt4-designer libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-svg
  libqt4-xml libqtcore4 libqtgui4 libstdc++6 libstdc++6-4.3-dev
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg gcc-4.3-multilib
  libmudflap0-4.3-dev gcc-4.3-locales libgcc1-dbg libgomp1-dbg libmudflap0-dbg
  libqt4-dev libstdc++6-4.3-doc
The following packages will be upgraded:
  g++-4.3 gcc-4.3 libgcc1 libqt4-dbus libqt4-designer libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-svg
  libqt4-xml libqtcore4 libqtgui4 libstdc++6 libstdc++6-4.3-dev
16 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
8 not fully installed or removed.
Need to get 0B/20.2MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 161282 files and directories currently installed.)
Preparing to replace libgcc1 1:4.3.2-1ubuntu8 (using .../libgcc1_1%3a4.3.2-1ubuntu9_i386.deb) ...
Unpacking replacement libgcc1 ...
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.3.2-1ubuntu9_i386.deb (--unpack):
 unable to make backup link of `./usr/share/lintian/overrides/libgcc1' before installing new version: Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.3.2-1ubuntu9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm kinda hoping that I wont have to do a reinstall. Anyone have any suggestions for fixing this?

Thanks in advance,

John

---

### Post by linomac on 2008-10-08
IMHO
1. try dpkg --configure -a for the broken installations
2. never use apt-get again
3. use aptitude in its place
aptitude install
aptitude update
aptitude full-upgrade
it has much better dependency resolution and it proposes u various solutions

---

### Post by Johnsie on 2008-10-09
Thanks, I tried the those methods and also using aptitide to fix it. Unfornately it didn't work. I was also having some probems with the gnome-keyring and network manager so I just did a re-install. Luckily it was just my eeepc and ont a production machine. I think Ubuntu needs to have some kind of system restore mechanism so that people can backtrack if their system gets broken. That is one of the good features of Windows that I've  missed during the las t three years of using Ubuntu.

---

