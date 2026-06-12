---
title: "problem after try to install ubuntu"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by fire planet on 2012-04-12
I have a Dell xps 1530 and windows7 on it. I'm beginner to linux and i encountered a problem after i tried to  install ubuntu.  recently i run ubuntu installer and after some steps ,  partitioning page displayed . on that page i changed a part of my "C:  drive" from "ntfs" to "ext4" ! but before completion i pressed the  "quit" button . and after that when i start my computer "windows boot  Manager"  came up after the dell logo and it says:
    Windows Failed to start. A recent hardware or software change might be the cause.
  Status: 0xc000000f Info: the boot selection failed because a required device is inaccessible.
    It gives me the option to start up using the Operating System CD and  try reparing it , but none of repairing option help me. i'm afraid to do  anything else since i have tons of files related to my work in it and i  REALLY don't want to loose them.
  Now i have neither ubuntu nor win7 and i dont know what happend to my hard disk and if my files are still accessible or not! Is there any suggestions to find my files?
  help,please :(((

---

### Post by darkod on 2012-04-12
The C: drive is not actually a drive as Microsoft calls it, it is a partition. If you changed the type of the partition from ntfs to ext4, you might have lost your windows.

You install ubuntu on separate ext4 partition, you can't have the same partition with both ntfs and ext4.

First of all, to make sure what you have, boot with the ubuntu cd in live mode (Try Ubuntu), open Terminal and post the output of:
sudo fdisk -l (small L)

---

