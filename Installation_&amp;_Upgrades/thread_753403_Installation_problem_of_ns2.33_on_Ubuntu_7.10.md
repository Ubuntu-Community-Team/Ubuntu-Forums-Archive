---
title: "Installation problem of ns2.33 on Ubuntu 7.10"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by fiqbal on 2008-04-12
Hi,
i have installed Ubuntu 7.10 and wanted to install ns-allinone-2.33. I have downloaded it from sourceforge.net and followed the commands:

$ tar -xzvf ns-allinone-2.33.tar.gz
$ cd ns-allinone-2.33
$ sudo apt-get install build-essential autoconf automake libxmu-dev

During executing it asked to insert Ubuntu 7.10 CD, after that the following error lines are printed on terminal. (Note that i have installed it using superuser mode)

Media change: please insert the disc labeled
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/p/patch/patch_2.5.9-4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Looking forward to have a solution
regards,

Fiqbal

---

### Post by Partyboi2 on 2008-04-13
Open up Software Sources, (System>Admin>Software Sources) on the first tab at the bottom under "Installable from cd-rom/dvd) untick the cdrom box and then close Software Sources.
Then continue with the install.

---

