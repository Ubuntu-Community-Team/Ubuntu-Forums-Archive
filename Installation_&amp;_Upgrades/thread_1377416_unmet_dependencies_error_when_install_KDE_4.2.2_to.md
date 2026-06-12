---
title: "unmet dependencies error when install KDE 4.2.2 to KDE 4.3.2"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by peyek on 2010-01-10
the complete message in terminal was :

tony@tony-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-plasma python-dev libeet1 kdebase-bin libqzion0 python2.6-dev
  libqedje0 qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin
Suggested packages:
  plasma-scriptengines
The following packages will be upgraded:
  kdebase-workspace-bin
1 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
Need to get 0B/3273kB of archives.
After this operation, 2970kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 202828 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ 


What should I Do?, anybody help me please...

---

