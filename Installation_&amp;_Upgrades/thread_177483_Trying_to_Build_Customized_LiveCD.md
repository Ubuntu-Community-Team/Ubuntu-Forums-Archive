---
title: "Trying to Build Customized LiveCD"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by TroyMW on 2006-05-16
I'm trying to build a customized LiveCD.  I've been trying to follow the instructions in these two links:  [http://homepage.mac.com/bner/iblog/B1570693677/C1271976503/E1448650622/](http://homepage.mac.com/bner/iblog/B1570693677/C1271976503/E1448650622/) and [https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo).  I'm getting some errors that I can't figure out.  I'm using the ubuntu-5.10-live.i386.iso image.

1.  Under the section "Preparing the chroot" I get the following error:
     command - sudo mount -t proc proc mnt/home
     error - "mount: mount point mnt/proc is not a directory"

2.  Under the section "Installing Additional Packages" I get the following error:
     command - sudo cp /etc/resolv.conf mnt/etc
     error - "cp: accessing 'mnt/etc': Input/output error"

     In fact, I get "Input/output" on all of the directories in the extracted file system

Any suggestions?

---

