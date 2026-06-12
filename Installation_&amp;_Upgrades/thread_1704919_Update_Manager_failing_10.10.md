---
title: "Update Manager failing 10.10"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by craynium on 2011-03-11
just recently started having problems with Update Manager. Getting this error on many packages while attempting upgrade.
I receive the same errors when using main or US server setting.

Running 10.10 with 2.6.35-27-generic


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.27-2ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.27-2ubuntu3.1_i386.deb) Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.4.1-3ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.4.1-3ubuntu1_all.deb) Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.14.3-0ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.14.3-0ubuntu1.2_i386.deb) Size mismatch

---

### Post by cjejuni on 2011-03-11
i think i had a few hours ago! if your system usable at least to see internet, hold your upgrading mouse. there is something array with the dpkg, apt-get, aptitude, synaptic pkg manager lists, config files! somehow they are using the same files. look/see with aptitude where it is broken, kinda look like windows3.1 (no pun intended.) 
post the error so other can help too.
good luck.

---

### Post by cjejuni on 2011-03-11
try this thread:

[http://ubuntuforums.org/showthread.php?t=1705101](http://ubuntuforums.org/showthread.php?t=1705101)

cj

---

