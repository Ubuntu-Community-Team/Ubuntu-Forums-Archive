---
title: "Update to 20.04 problems on dual boot system - GRUB failed"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2020-10-04
Yesterday I (tried to) posted a thread to this forum about the problems I had with an update I performed. My post was lost. Strange.

Anyway, I got notified that Ubuntu 20.04 was ready for installation. I started it and ran it in the background. But after some time the installation halted, and later on my computer froze. I rebooted, burned an installation DVD on Windows 10, and installed it using the DVD. At the end however I got a "GRUB installation failed" notification. I got a desktop, but not the one I was used to. 

Edit: When I booted again my boot process stuck on a black screen. 
Edit 2: Dual boot, dual disk system

What are my options? Try to install again from DVD?

---

### Post by Macamba on 2020-10-04
ATM I am in the installer, and watching at my partition table. It looks like:

```
/dev/sda
    free space                1 mb
    /dev/sda1/    swap    16,382 mb
    /dev/sda2/    ext4     40,960 mb       Ubuntu 20.04.1 LTS
    /dev/sda3/    ext4     3,943,441 mb   ... my data partition ...
```

It complains it wants 'No root file system detected'. But when I want to use sda2 for that I get no change to assign '/' to it (only different file systems, like ext 4 journaling system). I have the option to format the partition, but I am a bit afraid for that step.

---

