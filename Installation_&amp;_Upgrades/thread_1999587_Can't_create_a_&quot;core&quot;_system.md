---
title: "Can't create a &quot;core&quot; system"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Richard Krehbiel on 2012-06-08
I'm trying to rebuild the OS platform for some embedded PCs (500MHz Geode, 512M DRAM, 2GB flash disk).  I thought Ubuntu Core would be a good new starting point.  (The last time I used Fedora 8.)

I picked up the core filesystem from [http://cdimage.ubuntu.com/ubuntu-core/releases/12.04/release/ubuntu-core-12.04-core-i386.tar.gz](http://cdimage.ubuntu.com/ubuntu-core/releases/12.04/release/ubuntu-core-12.04-core-i386.tar.gz).

I followed the instructions at [https://wiki.ubuntu.com/Core/InstallationExample](https://wiki.ubuntu.com/Core/InstallationExample).

I managed to download the proper linux-image, and all the dependent package .deb files.  ("apt-rdepends" to identify them, "apt-get install --print-uris --reinstall" to find dependent .deb files).

I'm at the point where I've chroot'ed to my newly created root filesystem and I'm trying to install the linux image.  I can't get dpkg to succeed.

The major sticking point is that the procps package is complaining that it can't be "started", so it's not configured and won't satisfy further dependencies.

I'm stuck.  Who's managed a 12.04 Ubuntu Core install?  What am I missing?  Thanks.

---

### Post by dino99 on 2012-06-08
you should directly ask on launchpad, where devs can answer. Use "ask a question" on top right pane.

---

### Post by Richard Krehbiel on 2012-06-08
Thanks, I'm going there now.

---

