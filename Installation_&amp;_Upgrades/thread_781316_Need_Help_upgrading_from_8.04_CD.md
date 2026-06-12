---
title: "Need Help upgrading from 8.04 CD"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by stevh0 on 2008-05-04
I have burnt the ISO but im having difficulty upgrading from the Cd ..

It also does not pop up when i insert it. 

Ive checked it in vmware for any defects and it works perfectly

ill pop in gksu "sh /cdrom/cdromupgrade" as per the Ubuntu.com site and the package manager pops up..

what should i be doing to get the ball rolling?

also what causes the following error?

Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...6/Packages.bz2](http://archive.ubuntu.com/ubuntu/dis...6/Packages.bz2) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...6/Packages.bz2](http://archive.ubuntu.com/ubuntu/dis...6/Packages.bz2) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ce/Sources.bz2](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.bz2) Hash Sum mismatch

---

### Post by Pumalite on 2008-05-04
First check your connection. Second, remove all third parties from /etc/apt/sources.list. You can try a different Server.
System>Administration>Software Sources>Dowload From>Other>Let it choose the best for you.

---

### Post by stevh0 on 2008-05-04
okay .. its working now.. but it still wants me to download the packages. i need upgrade from my disc

---

### Post by Pumalite on 2008-05-04
Below 'Download From' is CD. Check it.

---

### Post by stevh0 on 2008-05-04
on the download from I have only 7.10 showing there.

how do i add the new medium in there?

---

### Post by Pumalite on 2008-05-04
System>Administration>Software Sources>Check CD
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

