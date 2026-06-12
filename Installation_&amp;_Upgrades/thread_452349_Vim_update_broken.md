---
title: "Vim update broken"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by kliklik on 2007-05-23
Vim update broke my system..

```
$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vim-common
The following packages will be upgraded:
  vim-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/186kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 114367 files and directories currently installed.)
Preparing to replace vim-common 1:7.0-164+1ubuntu7 (using .../vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb) ...
Unpacking replacement vim-common ...
dpkg: error processing /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb (--unpack):
 unable to make backup link of `./usr/share/vim/vimcurrent' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
$ sudo ls -l /usr/share/vim/vimcurrent 
b--x--xr-x 24450 973133638 2955436774 252, 55 1970-02-21 18:01 /usr/share/vim/vimcurrent
```

How can I fix this?

---

