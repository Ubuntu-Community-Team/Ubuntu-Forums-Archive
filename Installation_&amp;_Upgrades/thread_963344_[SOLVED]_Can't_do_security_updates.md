---
title: "[SOLVED] Can't do security updates"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-10-30
Using Ubuntu 8.04.1

There are 9 important security updates, but I can't do them because I'm on dialup. The size for these updates is over 50 Mb

Next week I _may_ have access to a fast computer connection.

Can someone please advise how I can ..

1.  Determine the packages that need updating
2.  From step 1, resolve the URL for downloading the .DEB files
3.  I can them download the files to a USB stick
4.  How do I then update my version of Ubuntu, using the DEB files on the USB stick.

Oygle

---

### Post by oygle on 2008-10-30
[This how-to]("https://stage.maemo.org/svn/maemo/projects/haf/trunk/apt/doc/offline.sgml") may be of help, especially the part down the bottom ..

> The basic idea is to create a disc that has only the archive files downloaded from the remote site. This is done by using the --print-uris option to apt-get and then preparing a wget script to actually fetch the packages.


I opened that file in Firefox, but it doesn't display too well. It says up the top ..

```
<!-- -*- mode: sgml; mode: fold -*- -->
<!doctype debiandoc  PUBLIC  "-//DebianDoc//DTD DebianDoc//EN">
<book>
<title>Using APT Offline</title>

```

what tool can I use to display this file, so that it is easier to read, please ?

---

### Post by Partyboi2 on 2008-10-30
You could use [[COLOR=Blue]synaptic package manager download script [/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")to upgrade your system. Or have a look at [[COLOR=Blue]keryx [/COLOR]]("http://keryx.betaserver.org/")

---

### Post by oygle on 2008-10-31
> **Partyboi2 said:**
> You could use [[COLOR=Blue]synaptic package manager download script [/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")to upgrade your system. Or have a look at [[COLOR=Blue]keryx [/COLOR]]("http://keryx.betaserver.org/")

Thanks for that link to the download script. There were 9 updates showing that needed to be done (but I can't with dialup). Followed the instructions from the downloadscript docs, went into Synaptic Package Manager ..

Edit |  Mark all upgrades    (nine were showing)
File |  Generate package download script

saved the file, and then opened in in text editor ..

```
#!/bin/sh
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.32_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.24.21.23_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.24.21.23_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-21-generic_2.6.24.14-21.51_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.24.21.23_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-21_2.6.24-21.43_all.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-21-generic_2.6.24-21.43_i386.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.24.21.23_i386.deb
```

The 9 update files were all showing in the shell script. Fantastic, this is _EXACTLY_ what I needed. Now I can d/load those files on another computer, add to USB stick and update them back here, following the [Installation section of the download script instructions.]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")

Thanks very much, this is great.  :popcorn:

Oygle

---

