---
title: "[SOLVED] 8.04lts installation on acer notebook"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Nailhac on 2008-10-02
I already have 8.04 installed on desktop and wish to instal on acer notebook with 1.256gb ram and 40gb hdd. this computer has been fat32 configured.
the installation halts with black screen showing only 
running local boot scripts (/etc/etc.local)   [OK]

that is the last line and I have attempted this 3 times. Is this a problem with fat32 and should I do a complete reformatt of hdd to ntfs and attempt. Help would be appreciated. Thanks

---

### Post by kruisa7 on 2008-10-02
Is this message from running the live CD / DVD, or from trying to install 8.04 directly onto the laptop?

The fat32 filesystem should not make any difference as Ubuntu can use ntfs, fat32 and many others.  To install permanently, Ubuntu will have to write a new filesystem to your disk such as ext3, plus create a swap partition.  It is helpful to have a separate partition for /home too.

Try the live CD first - it should give you an idea of what hardware works and what does not.  Then you can figure out how to get the hardware to work and install Ubuntu to the hard disk.

---

### Post by Nailhac on 2008-10-02
thanks kruisa7 the message previously indicated was for live cd. I have attempted to install full but cannot do that either ends up with a message "to access official ubuntu documentation visit ....ubuntu.com To run a command as administrator (user "root")..................for details.
I cannot get to install full or live. I had no similar problems installing into desktop pc. I would appreciate any suggestions.

---

