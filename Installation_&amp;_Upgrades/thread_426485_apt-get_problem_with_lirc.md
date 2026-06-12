---
title: "apt-get problem with lirc"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by unregistr3d on 2007-04-28
hi,
i installed lirc, but it has problems on the installprocess  (subprocess post-install script returned error exit status 1), so i tried to deinstall it with "apt-get remove", which also has an error ( subprocess post-removal script returned error exit status 1).

So, i tried "apt-get install lirc" again........this was my bigest mistake i ever made on Ubuntu

now apt-get would like to replace it, but it can't......
```

unregistr3d@ubuntu-laptop1 ~ % sudo apt-get --purge remove lirc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lirc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1683kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing lirc (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)
100 unregistr3d@ubuntu-laptop1 ~ % sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/364kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package lirc.
(Reading database ... 120139 files and directories currently installed.)
Preparing to replace lirc 0.8.1+cvs20070310-0ubuntu2 (using .../lirc_0.8.1+cvs20070310-0ubuntu2_amd64.deb) ...
Unpacking replacement lirc ...
dpkg: error processing /var/cache/apt/archives/lirc_0.8.1+cvs20070310-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/share/doc/lirc/changelog.gz', which is also in package liblircclient0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lirc_0.8.1+cvs20070310-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
so, how can i make apt-get working :mad:, i tried "dpkg --purge --force-all lirc", "apt-get remove lirc", "apt-get --purge remove lirc", "apt-get upgrade", pinning it on /etc/apt/preferences and lots of other stuff

edit: `/usr/share/doc/lirc/changelog.gz', doesn't exists

thx
Mfg, unregistr3d

---

### Post by unregistr3d on 2007-04-28
i solved the problem with:

sudo mv /var/lib/dpkg/info/liblircclient0.list /var/lib/dpkg/info/liblircclient0.list~
sudo apt-get upgrade
sudo mv /var/lib/dpkg/info/lirc.postrm /var/lib/dpkg/info/lirc.postrm2
sudo dpkg -i --force-all /var/cache/apt/archives/lirc_0.8.1+cvs20070310-0ubuntu2_amd64.deb
sudo mv /var/lib/dpkg/info/lirc.postrm /var/lib/dpkg/info/lirc.postrm2
sudo dpkg --purge --force-all lirc
sudo mv /var/lib/dpkg/info/liblircclient0.list~ /var/lib/dpkg/info/liblircclient0.list
sudo rm /var/lib/dpkg/info/lirc.postrm2

---

