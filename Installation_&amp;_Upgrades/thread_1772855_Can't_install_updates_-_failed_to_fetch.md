---
title: "Can't install updates - failed to fetch"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by schildkrote on 2011-06-01
Hi,

I'm unable to install updates and new packages. I receive messages such as the following:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb)
  404 Not Found [IP: 91.189.92.161 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-17-generic_2.6.27-17.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-17-generic_2.6.27-17.46_i386.deb)
  404 Not Found [IP: 91.189.92.161 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.27-17.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.27-17.23_all.deb)
  404 Not Found [IP: 91.189.92.161 80]

I recently had windows vista taken off my hard drive and my partitions realigned to create more storage space on my hard drive. I don't now if this is related. I was able to install upgrades previously.

Any help much appreciated!

---

### Post by pontifor on 2011-06-01
I have been having the same problems all of a sudden..

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-dev_2.6.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-dev_2.6.2-0ubuntu1_i386.deb)  404 Not Found [IP: 91\
.189.92.171 80]

This is for an older release ( 9.04 ) but it should still work.

S

---

### Post by ivanovnegro on 2011-06-01
> **pontifor said:**
> I have been having the same problems all of a sudden..

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-dev_2.6.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-dev_2.6.2-0ubuntu1_i386.deb)  404 Not Found [IP: 91\
.189.92.171 80]

This is for an older release ( 9.04 ) but it should still work.

S

Dont mix the repositories. Python is in the official 11.04 repos and it is on a higher number, 2.7 and not 2.6

To the OP, remove these files from your sources list, they are showing an error and then update your system.

---

### Post by santoshbarwa@gmail.com on 2011-06-01
> **schildkrote said:**
> Hi,

I'm unable to install updates and new packages. I receive messages such as the following:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6.3_i386.deb)
  404 Not Found [IP: 91.189.92.161 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-17-generic_2.6.27-17.46_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-17-generic_2.6.27-17.46_i386.deb)
  404 Not Found [IP: 91.189.92.161 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.27-17.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.27-17.23_all.deb)
  404 Not Found [IP: 91.189.92.161 80]

I recently had windows vista taken off my hard drive and my partitions realigned to create more storage space on my hard drive. I don't now if this is related. I was able to install upgrades previously.

Any help much appreciated!


_**answer**_:

1.go to application->software center->click on edit->click on software sources->other software->add source->check or uncheck some of the application.

after that you try,surely you get a result.
:guitar:santosh barwa

---

### Post by schildkrote on 2011-06-01
Thanks..I tried what you suggested - played around with checking and unchecking boxes but I still get the same messages.

Any other ideas?

---

