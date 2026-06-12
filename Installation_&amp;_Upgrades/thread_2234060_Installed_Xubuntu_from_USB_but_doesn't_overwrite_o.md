---
title: "Installed Xubuntu from USB but doesn't overwrite old intallation"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by ryan94 on 2014-07-12
Hi all,

I've just downloaded Xubuntu OS which is a really nice system but the problem I'm having is that it is not being installed on the hard drive. When I installed Xubuntu, it asked me if I wanted to overwrite Windows 7, which I do, and so I selected that option. However, if I boot my computer without the usb attached, it loads up Windows 7 again. I thought the idea was that once I'd installed it I didnt need the usb anymore. Can anyone suggest what I have done wrong? 

I installed using UNetbootin on a Dell Inspiron. 

Thanks in advance for help.

---

### Post by yancek on 2014-07-12
Something went wrong with the bootloader installation for Xubuntu.  Use the Ubuntu flash drive and google 'bootinfoscript'.  That will take you to the site where you can download and run the bootinfoscript which outputs a results.txt file.  This file will have detailed information on drive/partitions boot files and other pertinent info.  You can post it here for assistance.  It must be run on a Linux system.  There is a link in the Description box at the site, explaining how to use it.

---

