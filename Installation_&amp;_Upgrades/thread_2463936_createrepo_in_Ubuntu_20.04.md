---
title: "createrepo in Ubuntu 20.04"
date: 2021-06-21
forum: Installation &amp; Upgrades
---

### Post by jauling on 2021-06-21
Hi everyone.

I've been maintaining a severely outdated Ubuntu 14.04 server that is a local DEB and RPM repository for our RHEL and Ubuntu systems. It's about time I migrate these services to a more modern distribution, and 20.04 has been the target Ubuntu version that we chose for all our Ubuntu systems out there. This seems to have been fine, until we started looking at this repo server.

Apparently, the createrepo package is no longer available in 20.04, due to a combination of the fact that this distro version now runs Python 3 as well as the fact that the createrepo package is being migrated to a different codebase. I'd like to know if it is possible (or advisable) to possibly to do one of the following:

[LIST=1]
[*]Install Python 2 on Ubuntu 20.04 to hopefully leverage the createrepo package that ships with 18.04
[*]Somehow get createrepo-c to work in 20.04 (it's in 21.04 from what I hear)
[*]Assume defeat and either downgrade to Ubuntu 18.04 or run my repo server using a current RHEL version
[/LIST]

I'd prefer not to consider the 3rd option. Has anyone had first hand experience with either the 1st or 2nd options? Are there other possibilities that I should consider?


[https://answers.launchpad.net/createrepo/+question/690448](https://answers.launchpad.net/createrepo/+question/690448)

---

### Post by Impavidus on 2021-06-21
I've got no experience with any of those options.

1: Python 2 is still available from the repos. If the createrepo package from 18.04 installs without dependency issues, it may very well work. No guarantees though. You could try.
2: The createrepo-c package from 21.04 has some dependencies, in particular libcreaterepo-c0 and libmodule-md2, that are not available on 20.04. You may get those from 21.04 too, but they have even more dependencies not available on 20.04. Not something I would try.
3: This could be the easiest solution.

---

### Post by jauling on 2021-06-23
Well, I went with the arguably dumbest way to go about this, but it seems to work for the time being. I guess I'll know what kind of a pickle I've gotten myself in when I start to have some real issues?

Since we maintain our own Ubuntu APT mirror on this server, having all the deb packages locally made finding and resolving apt install dependencies pretty easy. I just started with the latest available createrepo deb package, and then satisfied the subsequent dependencies, until apt install allowed me to install. I completely understand mixing packages from different releases is highly frowned upon, and if I run into issues I'm pretty much on my own, but the install procedure was painless. Only time will tell if this proves to be an elegant workaround or if this turns into a huge infected wound that needs amputation.

```
# apt install ./createrepo_0.10.3-1_all.deb ./deltarpm_3.6+dfsg-1build6_amd64.deb ./python-deltarpm_3.6+dfsg-1build6_amd64.deb  ./python-lzma_0.5.3-3_amd64.deb ./python-sqlitecachec_1.1.4-1_amd64.deb ./yum_3.4.3-3_all.deb ./python-urlgrabber_3.10.2-1_all.deb Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'createrepo' instead of './createrepo_0.10.3-1_all.deb'
Note, selecting 'deltarpm' instead of './deltarpm_3.6+dfsg-1build6_amd64.deb'
Note, selecting 'python-deltarpm' instead of './python-deltarpm_3.6+dfsg-1build6_amd64.deb'
Note, selecting 'python-lzma' instead of './python-lzma_0.5.3-3_amd64.deb'
Note, selecting 'python-sqlitecachec' instead of './python-sqlitecachec_1.1.4-1_amd64.deb'
Note, selecting 'yum' instead of './yum_3.4.3-3_all.deb'
Note, selecting 'python-urlgrabber' instead of './python-urlgrabber_3.10.2-1_all.deb'
The following additional packages will be installed:
  debugedit libdw1 liblua5.2-0 libpython2-stdlib libpython2.7 libpython2.7-minimal libpython2.7-stdlib librpm8 librpmbuild8 librpmio8 librpmsign8 libsqlite0 python-is-python2 python-libxml2
  python-pycurl python-rpm python-sqlite python2 python2-minimal python2.7 python2.7-minimal rpm rpm-common rpm2cpio
Suggested packages:
  rpm-i18n libcurl4-gnutls-dev python-pycurl-dbg python-pycurl-doc python-sqlite-dbg python2-doc python-tk python2.7-doc binfmt-support alien elfutils rpmlint rpm2html
The following NEW packages will be installed:
  createrepo debugedit deltarpm libdw1 liblua5.2-0 libpython2-stdlib libpython2.7 libpython2.7-minimal libpython2.7-stdlib librpm8 librpmbuild8 librpmio8 librpmsign8 libsqlite0
  python-deltarpm python-is-python2 python-libxml2 python-lzma python-pycurl python-rpm python-sqlite python-sqlitecachec python-urlgrabber python2 python2-minimal python2.7
  python2.7-minimal rpm rpm-common rpm2cpio yum
0 upgraded, 31 newly installed, 0 to remove and 174 not upgraded.
Need to get 6,106 kB/6,866 kB of archives.
After this operation, 29.9 MB of additional disk space will be used.
```

---

