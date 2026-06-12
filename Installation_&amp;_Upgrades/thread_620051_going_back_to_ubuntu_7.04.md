---
title: "going back to ubuntu 7.04"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2007-11-22
I have been using 7.10 gutsy since shortly after its release. Today was the last straw and I am going back to feisty until gutsy is more reliable. 

The main problem seems to be gnome, esp. nautilus and panel. The problems are hard to characterize: desktop hangs (reboot required) and nautilus looping with no window displayed. .xsession-errors is full of spookey looking stuff (typically not anything useful except for the developer/debugger). 

The last straw was the sudden appearance of DVD / iso9660 file system errors for no apparent reason. Somewhere in the middle of the disk, all files become unreadable. Apparently the directory entries beyond a certain position all point to garbage. The same DVD works fine on the same PC with feisty. I tried this multiple times to be certain, and I am convinced the problem is in gutsy.

DVD mounting takes much longer on gutsy, and scanning a DVD / iso9660 file system for errors runs at 3.8 MB/sec on gutsy (when it works at all) and 8.3 MB/sec on feisty. 

It seems there have been changes in the DVD driver, the iso9660 file system library, or growisofs, and these are not fully debugged.

---

