---
title: "Install .deb packages from hard drive (use copy of CD or DVD as local repository)"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by homunq on 2007-06-07
My computer has no CD drive and very slow net access. I have a copy of the DVD in a partition of my hard drive, mounted at /dev/hda2. I want to install applications from there.

All the following commands are in a root shell, either prefix each with sudo or do a sudo -i at the start.

First try:

dpkg -i /dev/hda2/pool/main/someletter/someletterpackagedir/someletterpackage.deb

... but it doesn't check dependencies.

Second try:

sudo -i
cd /dev/hda2/pool/main
dpkg-scanpackages . /dev/null > Packages
cp /etc/apt/sources.list /etc/apt/sources.list.backup
echo "deb file:/media/sda2/pool/main ./" > /etc/apt/sources.list

and then I try to

aptitude install somepackage

but get the error "No candidate version for somepackage" (or something, I get it in Spanish).

Is there an easier way? What am I doing wrong?

---

### Post by homunq on 2007-06-07
By "the dvd" I obviously mean "the ubuntu 7.04 install dvd".

---

