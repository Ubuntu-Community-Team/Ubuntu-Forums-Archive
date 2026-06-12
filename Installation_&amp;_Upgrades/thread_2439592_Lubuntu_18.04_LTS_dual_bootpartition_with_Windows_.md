---
title: "Lubuntu 18.04 LTS dual boot/partition with Windows 7"
date: 2020-03-30
forum: Installation &amp; Upgrades
---

### Post by ReFranz on 2020-03-30
My desktop is a 2009 HP business desktop 64 bit, which came with Windows 7 . I currently have Ubuntu 16.04 LTS installed in a partition. I want to remove it and install Lubuntu 18.04 LTS in a partition. 16.04 was installed after removal of 14.04 LTS, but I can't remember the procedure. I found the following documentation, which doesn't address removal of existing partitions before creating a new partition.

[https://docs.lubuntu.net/lubuntu_installation](https://docs.lubuntu.net/lubuntu_installation)

My initial solution tor removal of existing partitions was to use Windows and simply delete them, but 1) I can't tell which partition is Windows, and I don't want to delete it, and 2)it occurred to me that simple deletion might wreak havoc with my machine. Question 1: is the documentation above authoritative/factual? Question 2: what is the correct way to remove the Ubuntu partition(s), and leave Windows 7 intact before creating a partition and installing Lubuntu?

---

### Post by guiverc on 2020-03-30
First I'll suggest using Lubuntu's site ([http://lubuntu.me/](http://lubuntu.me/)) instead of the site you are using. If you're unsure which is the correct site to use, rather than use a search engine, ask ubuntu.com which will send you to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will correctly go the official site for each flavor.  ubuntu.com is under Canonical's control thus is accurate, we cannot control search engines (ie. google.com)

Lubuntu's documentation can be found at 

Chapter 1 Installing Lubuntu - [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)
Chapter 1.1 Retrieving the image - [https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
Chapter 1.2 Booting the Image - [https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
Chapter 1.3 Installation - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

however that will be for the latest stable release (currently 19.10) so it won't perfectly apply to Lubuntu 18.04 LTS.

If you do want Lubuntu 18.04 LTS, which is supported until 2021-April (3 years from 2018-April as it's a flavor, 5 years applies only to Ubuntu desktop/server/cloud but not flavors), I would use the 'something-else' option, and select your existing partitions.

If it was me, I'd boot your existing system, grab an envelope from recycling, and jot down the partitions in use, then use those when you install your existing system. If you want to keep your settings, or files, I'd use something-else as already stated, and ensure 'format' box is unchecked.

This will
- make a note of your additional packages (added post install of existing system)
- erase system directories (not user directories unless 'format' was checked)
- install system
- add back your additional packages (if available for your new release)
- ask to reboot

If you plan on using this system after 2021-April or the EOL (*end-of-life*) of 18.04 LTS, you might want to consider installing Lubuntu 19.10 (following the manual), as it has an upgrade path to 20.04 LTS.  

Lubuntu 18.04 LTS was the last release using LXDE, and requires re-install to upgrade. If your box is x86 (32-bit or i386) which I think unlikely, Lubuntu 18.04 LTS is the way to go. However my box is from 2009 and is x86_64/amd64 being intel core2quad, so I'd use amd64.

---

