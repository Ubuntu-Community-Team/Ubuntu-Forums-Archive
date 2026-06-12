---
title: "Problem upgrading from version 7.04 to 7.10"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Denis O'Connor on 2008-11-24
I have just attempted to upgrade from Ubuntu 7.04 to 7.10.

Downloaded 1021 of 1024 files.

Got message saying" not all updates can be installed" Did "partial upgrade " to get the rest and got " failed to fetch":

[http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7).
dgfs.1-0ubuntu5.1_i386.deb Size mismatch

[http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dgfs.1](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dgfs.1)
-0ubuntu5.1_i386.deb Size mismatch

[http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplp/hplp-data_2.7.7dgfs.1](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplp/hplp-data_2.7.7dgfs.1)
-0ubuntu5.1_all.deb Size mismatch

This happens every time I try to finish the upgrade.

Does anybody have any simple solution to this?  I am a very new inexperienced user so any help would be appreciated if it was in very simple instructions.

Thanks
Denis

---

### Post by lemming465 on 2008-11-25
Open a terminal session (Applications -> Accessories -> Terminal) and try ```
sudo apt-get update
sudo apt-get upgrade --fix-broken
```
If that doesn't do it, and you can afford more download time, then try```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
If that still doesn't fix it, write back.

---

### Post by Denis O'Connor on 2008-11-28
Dear Lemming 465.

Thanks for your suggested fix(es).
Prior to trying them I went back to update manager and saw that instead of still needing the 3 that had size mismatch  previously, it now said I still needed 1004 to 1024.  Said ok and this time it downloaded them all ok and installation now completed and up and running on 7.10.  I had tried several times before to download and kept getting the same 3 mismatch files.  Maybe the only difference was that I shut the machine down for a couple of days till i went back to it today.  Mystery!

Anyway, I appreciate your offer of help. I am sure i will have more questions in the future.

I would be interested to know what your "fixes" were going to do if you have the time to reply.

Regards
Denis

---

### Post by lemming465 on 2008-11-28
apt-get is a command line front-end tool to the underlying "dpkg" suite of utilities that Debian and Ubuntu use for package management. "update" tells it to check the locally cached package lists against the repositories listed in /etc/apt/sources.list.  "upgrade" tells it to download and install newer versions of stuff you have.  "--fix-broken" tells it to be more aggressive about resolving problems with partially installed packages.  "clean" tells it to delete local copies from /var/cache/apt, so that it will download fresh copies next time you run "upgrade".
"dist-upgrade" enables some additional conflict resolution rules to handle cases where new versions of packages have different dependencies than old versions; this is primarily the case during upgrades between different versions.

---

