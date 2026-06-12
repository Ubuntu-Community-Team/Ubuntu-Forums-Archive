---
title: "how to uninstall ispell and some other softwares or even reinstall"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by strugglingman on 2006-12-06
hi,

the latest memory i could get is that i might install some language support packages, but i do not think that it is the reason of the problem that i meet now. Now i can not install any new packages or uninstall some softwares, first, i try to make a test, such as apt-get install emacs or remove emacs or some other softwares, but i falied to do that, some broken packages always prevent me from new installation, i even can not reinstall or remove completely those broken packages, i have tried several methods to  do that.
First, according to hint, i used the following command and got the following result:

root@wxw:/home/xinwei# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tetex-bin (3.0-13ubuntu6) ...
Running fmtutil-sys. This may take some time. ...
Running updmap-sys. This may take some time. ...
updmap failed. Output has been stored in
/tmp/tetex.updmap.XXK6Hl8J
Please include this file if you report a bug.
dpkg: error processing tetex-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on tetex-bin (>= 2.99); however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
Setting up dvipng (1.5-2.1) ...
install-info: No such file or directory for TeX
dpkg: error processing dvipng (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ispell (3.1.20.0-4) ...
install-info: No such file or directory for Emacs
dpkg: error processing ispell (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-brev:
 tetex-brev depends on tetex-bin; however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-brev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tetex-bin
 tetex-extra
 dvipng
 ispell
 tetex-brev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Second, i open the synaptic package manager, click custom, choose the broken button, try to remove, remove completely or reinstall, but none of them works...when i want to remove ispell, other problems in above list jump and prevent removing.
it always gives the result such as:
E: dvipng: subprocess pre-removal script returned error exit status 1
E: ispell: subprocess pre-removal script returned error exit status 1

What could i do now, i do not want to reinstall the whole system...


Any help will be appreciated!

---

### Post by strugglingman on 2006-12-08
well, i have fixed this problem:)

---

