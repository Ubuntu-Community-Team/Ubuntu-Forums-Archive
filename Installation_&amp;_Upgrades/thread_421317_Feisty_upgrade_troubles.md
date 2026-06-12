---
title: "Feisty upgrade troubles"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by x1a4 on 2007-04-24
Hi,

I've two issues upgrading to Feisty.

1) One of the Sources.gz files in the repository doesn't seem to be a gzip file: 

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  Sub-process gzip returned an error code (1)
Fetched 36.9kB in 3s (9893B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) Sub-process gzip returned an error code (1)

2) I've two conflicting packages. 

**thunar-volman-plugin** -- needs to be, but is not, installed
**thunar-volman** -- is installed and will not allow the above to be installed

When I try to remove **thunar-volman** it wants to remove **xubuntu-desktop** (which is now broken).  

I tried using *apt-get* and *aptitude* in a variety of ways, with a variety of options.  Now I'm stuck with close to 400 packages not upgraded and some 40 not installed.  

Please help.  Thank you.

**EDIT:** I ran *apt-get -f upgrade*, *apt-get -f dist-upgrade*, *apt-get -f install* a bunch more times, and managed to upgrade most everything, but now it seems I can't go any further, and **xubuntu-desktop** is still broken, some 60 packages are not yet upgraded, or a broken.  Thunderbird, for example, closes immediately after opening it with error 139.  The exact error I get is: 

DOUBLE-CLICK: 300 --> -1 THRESHOLD: 8 --> -1 DOUBLE-CLICK: 300 --> -1 THRESHOLD: 8 --> -1 Segmentation fault (core dumped)
Exit 139

---

### Post by x1a4 on 2007-04-24
Figured it out.  

I forgot I upgraded Xfce from a third-party repository.  Once I remembered, I enabled it (I disabled all third-party repositories for the upgrade) then reinstalled **thunar-volman** to make sure it is the way it should be, then used *dpkg* to purge it.  Once it was gone, the volume manager from the Ubuntu repository (**thunar-volman-plugin**) installed correctly, along with everything else.

---

