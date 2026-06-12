---
title: "Software RAID (mdadm) causes boot failure on Feisty"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Selfish Meme on 2007-09-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have been trying for several days to get software RAID going and thought I would share my experiences.

System
AMD X64 AM2 Processor
Nvidia nForce 430 chipset (Asus M2N-MX SE) (has fake RAID but not utilising)
DDR2 800 RAM
2x 160GB Western Digital SATA Drives

**1. Using Alternate i386 iso and trying to setup RAID through partitioner.**

When configuring the machine this way (the recommended way) you can make the partitions, and you can tell it to configure software RAID, it creates md0 wether or not you have told it to create an md device yet, and it creates it using entire drives not RAID partitions, so you end up with md0 as being 160GB sda/sdb. If you try and create other md devices it will warn you that there are no free RAID partitions. Needless to say you can't install onto this md0 drive.

I have found it is possible to drop back to the shell and manually fix many of the issues and even create the proper md devices, at that point I can even get it to install without error. However at boot it will eventually after several minutes fall over to initramfs, none of the procedures (linked at end) I have found  to fix this, that I was actually able to accomplish, will get me any further.

*cat /proc/mdstat* will only show md0
*cat /proc/partitions* shows that no other partitions are detected and not even running */scripts/local-top/mdadm from-udev* will make them appear.

**2. Installing system to non RAID drives and then setting up RAID afterwards.**

The partitions are setup using the partitioner, even the RAID partitions. Instead of trying to configure RAID I just installed to the non RAID partitions. This works fine, the machine boots and I updated to the latest packages, until you try and install mdadm, again it creates md0 without asking, a reboot at this point will cause the system to dump again to initramfs after several minutes.

I tried putting the sleep 10 command in /usr/share/initramfs-tools/init and updating initramfs to no avail, if mdadm was installed the machine refused to boot.

:confused:

**Links**

[http://currents.soest.hawaii.edu/uhdas_fromships/oceanus_atseaweb/programs/adcp_doc/ubuntu_docs/thirdparty_html/ubuntu_raid.html](http://currents.soest.hawaii.edu/uhdas_fromships/oceanus_atseaweb/programs/adcp_doc/ubuntu_docs/thirdparty_html/ubuntu_raid.html)

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html)

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681)

[http://ubuntuforums.org/showthread.php?p=2236181#post2236181](http://ubuntuforums.org/showthread.php?p=2236181#post2236181)

---

