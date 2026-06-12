---
title: "Separate partitions for /home etc."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by cliowa on 2009-12-21
Hey all,
I am about to install Ubuntu on a 1TB drive alongside Win7. I have read about creating a seperate partition for /home. I have done this before, but never during the actual installation process (only afterwards, by copying files).
This is why I wanted to ask:
1) When creating the partitions (manually, during install), does it suffice to create one with mount point /home for Ubuntu to put my user's home folders there? (If yes, could you point me to an official source, because I have only found [http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide) so far)
2) Is it sensible to create seperate partitions for other directories as well (like /usr)? Under what circumstances?

Thanks for your help, regards...Cliowa

---

### Post by hugmenot on 2009-12-21
1) Yeah. That should do it.
2) You can make a /boot partition. 200 MB is plenty for that.

---

### Post by itang sanjana on 2009-12-21
> **cliowa said:**
> .. 1) When creating the partitions (manually, during install), does it suffice to create one with mount point /home for Ubuntu to put my user's home folders there? (If yes, could you point me to an official source, because I have only found [http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide) so far) ..

Yes it does. See [https://help.ubuntu.com/9.10/installation-guide/i386/apcs03.html](https://help.ubuntu.com/9.10/installation-guide/i386/apcs03.html) and [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). For the second link, ignore the "Resize/Move" and "Using the new partition" part.

> **cliowa said:**
> 2) Is it sensible to create seperate partitions for other directories as well (like /usr)? Under what circumstances?

Yes it is. See [https://help.ubuntu.com/9.10/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/9.10/installation-guide/i386/directory-tree.html)

---

### Post by oldfred on 2009-12-21
Unless you are installing a server you do not need to install any of the other system directories as partitions. That was standard years ago and then linux was primarily for servers. Now you can share the space in one partition and the total install is less than about 5GB. We recommend 10GB as a minimum for future growth and 20 or so if you have lots of space. 

/boot is only now required for ubuntu if you have an older pc that has the old BIOS limits where the boot has to be at the front of the drive. If you ever want other operating systems /boot may be required and you cannot use a /boot for more than one system.

Many recommend the separate /home and after 3 years of upgrading I did a clean install to houseclean all the old cruft. But I also moved all my data to a data partition and have another shared partition for some windows stuff. Now my /home is about 1GB and I do not see much need for a separate /home as I can easily copy it. But my data partition is 42GB and my shared another 20GB.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

