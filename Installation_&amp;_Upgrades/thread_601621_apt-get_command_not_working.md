---
title: "apt-get command not working"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by jdg.gehrig on 2007-11-03
Hello,

I am having a problem with the "sudo apt-get" command everytime i try to use it or adept(i run kubuntu) my computer crashes and I have to reboot. The apt-get command quits after it  says which applications it's going to install and adept quits after i say apply changes. I have already tried dpkg --configure -a but it doesn't work, Any Ideas?

Any help would be appreciated, John.

---

### Post by Pumalite on 2007-11-03
Check the file: /var/lib/dpkg/status
And see what's going on there.

---

### Post by jdg.gehrig on 2007-11-03
What should I do with that file,

Also I'd post it but it's WAY too long.

(I'm new to linux)

---

### Post by Pumalite on 2007-11-03
Check for packages that don't say 'installed..ok..installed'
Make a list. They will have to be removed.

---

### Post by jdg.gehrig on 2007-11-03
Package: jfsutils
Status: purge ok not-installed
Priority: optional
Section: admin

Package: ubiquity-ubuntu-artwork
Status: purge ok not-installed
Priority: optional
Section: admin

Package: user-setup
Status: purge ok not-installed
Priority: extra
Section: admin

Package: language-pack-es
Status: purge ok not-installed
Priority: optional
Section: translations

Package: libfuse2
Status: purge ok not-installed
Priority: optional
Section: libs

Package: ubiquity-casper
Status: purge ok not-installed
Priority: optional
Section: misc

Package: language-pack-kde-xh-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-kde-xh
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-kde-de-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-kde-de
Status: purge ok not-installed
Priority: optional
Section: translations

Package: xfsprogs
Status: purge ok not-installed
Priority: optional
Section: admin

Package: qtparted
Status: purge ok not-installed
Priority: optional
Section: x11

Package: os-prober
Status: purge ok not-installed
Priority: extra
Section: utils

Package: libdebconfclient0
Status: purge ok not-installed
Priority: optional
Section: libs

Package: ubiquity-frontend-kde
Status: purge ok not-installed
Priority: optional
Section: admin

Package: casper
Status: purge ok not-installed
Priority: extra
Section: misc

Package: language-pack-pt-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-xh
Status: purge ok not-installed
Priority: optional
Section: translations

Package: ntfsprogs
Status: purge ok not-installed
Priority: optional
Section: otherosfs

Package: libdebian-installer4
Status: purge ok not-installed
Priority: optional
Section: libs

Package: discover1-data
Status: purge ok not-installed
Priority: optional
Section: libs

Package: xresprobe
Status: purge ok not-installed
Priority: optional
Section: x11

Package: language-pack-kde-es-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: discover1
Status: purge ok not-installed
Priority: optional
Section: admin

Package: libdiscover1
Status: purge ok not-installed
Priority: optional
Section: libs

Package: language-pack-kde-pt
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-kde-pt
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-xh-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-es-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-de
Status: purge ok not-installed
Priority: optional
Section: translations

Package: ubiquity
Status: purge ok not-installed
Priority: optional
Section: admin

Package: language-pack-pt
Status: purge ok not-installed
Priority: optional
Section: translations

Package: language-pack-de-base
Status: purge ok not-installed
Priority: optional
Section: translations

Package: libntfs9
Status: purge ok not-installed
Priority: optional
Section: libs

Package: fuse-utils
Status: purge ok not-installed
Priority: optional
Section: utils

Package: language-pack-kde-es
Status: purge ok not-installed
Priority: optional
Section: translations

I searched all instances on not-installed

What should I do next

---

### Post by Pumalite on 2007-11-03
sudo dpkg --remove --force-remove-reinstreq <packagename>
Until you finish the list. Then:
sudo apt-get update
sudo apt-get upgrade

---

### Post by jdg.gehrig on 2007-11-03
That doesn't work it says the package isn't installed

---

### Post by Pumalite on 2007-11-03
Looks like a reinstall unless somebody comes up with a better answer.

---

### Post by jdg.gehrig on 2007-11-03
Can I just reinstall apt-get or do I have to reinstall the whole system?

---

### Post by Pumalite on 2007-11-03
You can't install just apt-get because apt-get is not working.

---

