---
title: "Installing Ubuntu 14.04.1L on existing Ubuntu partitions in Windows Vista"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by jpedro2 on 2014-10-05
How does one go about installing Ubuntu 14.04.1L desktop i386 on existing Ubuntu partitions in Windows Vista dual-boot using WUBI?

Help

Jose

---

### Post by Vladlenin5000 on 2014-10-05
Hi, welcome.

You don't and if you used WUBI to install it in the first place then you don't have a dual-boot either. Ubuntu is installed inside Windows.
WUBI is no longer supported.

---

### Post by oldfred on 2014-10-05
Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

The last supported version of wubi is 12.04. While a few advanced users have installed newer versions with wubi it is not an easy to install for beginners system anymore. Better to create new partitions and do a full partitioned install.

Even the original developer of wubi does not expect you to continue to use Wubi.
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by jpedro2 on 2014-10-05
Hi Vladlenin5000,

Thanks for the reply. I created a dual-boot Windows Vista Home Edition and an older Ubuntu which I cannot upgrade from Ubuntu anymore.
I installation was not done using WUBI. I was thinking of installing the 14.04.1L on the partitions currently used by the older Ubuntu.
It may seem very difficult (or impossible) and I may have to delete these partitions and recreate them for 14.04.

Regards

Jose

---

### Post by jpedro2 on 2014-10-05
Hi oldfred,

Thanks. I may go ahead and delete the existing Ubuntu partitions from Windows, restore the MBR and re-create them from the Ubuntu installation disk.

Jose

---

### Post by oldfred on 2014-10-05
If you have existing partitions you can use the manual install or Something Else. You just have to select your current / (root) partition, choose ext4 for format, mount as / and it should find an existing swap automatically.

Better to only use Windows partition tools to modify the existing NTFS partition size if you want and reboot immediately so it can run chkdsk. All other partitioning should be done from gparted which is on live installer or you can download as its own liveCD.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Vladlenin5000 on 2014-10-05
Deleting partitions just to recreate them later seems a waste of time. You can use the existing partitions by selecting "something else" in the installer, then select the partions to use and among those which ones are to be formated.

---

