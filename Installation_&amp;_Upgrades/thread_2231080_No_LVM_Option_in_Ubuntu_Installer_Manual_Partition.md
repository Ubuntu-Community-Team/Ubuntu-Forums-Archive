---
title: "No LVM Option in Ubuntu Installer Manual Partitioning"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by Xander314 on 2014-06-23
I am trying to manually set up partitioning for a new Ubuntu install, and would like to use LVM. However, I can't seem to find the LVM option. Having selected manual partitioning, I can add partitions and am presented with a dropdown menu. It lists various file systems, and the option to create an encrypted volume, but there is no mention of LVM. I know LVM is supported by the install disk as the automatic partitioning successfully creates an LVM volume. Why doesn't this option show up as it should? I know I could open a terminal and do it manually, but if I start down that route then I might as well go back to Gentoo... :)

Thanks!

---

### Post by slickymaster on 2014-06-23
[HowTo: Set up Ubuntu Desktop with LVM Partitions]("https://help.ubuntu.com/community/UbuntuDesktopLVM")

---

### Post by Xander314 on 2014-06-23
Thanks. Decided to give up on the GUI installer and did it manually as described there.

---

### Post by slickymaster on 2014-06-23
Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by oldfred on 2014-06-23
@slickymaster
You can only use the link for the alternative text based installer with LVM with 12.04. 
The alternative installer has been discontinued with newer versions.

I think the issue is related to the type of partition tools needed to edit partition. The Ubuntu installer is based on gparted which does not currently work with LVM nor RAID type partitions. You must use those tools to create partitions.
Not sure if you create partitions in advance that then the installer will let you use them?

 13.10 LVM install - Herman
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)


       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by slickymaster on 2014-06-23
> **oldfred said:**
> @slickymaster
You can only use the link for the alternative text based installer with LVM with 12.04. 
The alternative installer has been discontinued with newer versions.

I think the issue is related to the type of partition tools needed to edit partition. The Ubuntu installer is based on gparted which does not currently work with LVM nor RAID type partitions. You must use those tools to create partitions.
Not sure if you create partitions in advance that then the installer will let you use them?

 13.10 LVM install - Herman
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)


       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm


Thanks for the heads up oldfred.

---

### Post by oldfred on 2014-06-23
Just noticed this in another thread.

  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)

---

