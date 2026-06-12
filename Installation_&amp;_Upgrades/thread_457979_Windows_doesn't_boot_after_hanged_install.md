---
title: "Windows doesn't boot after hanged install"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by hsophie on 2007-05-29
Hello,

I'd like to share a problem and its solution on the forum for the benefit of others:

Problem:
While installing Ubuntu 7.04 as dual-boot on a Windows XP machine, the LiveCD installer app stopped functioning, i.e. it hanged.
On reboot, without the cd loaded, I would get the following error: "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device".

If I booted with the LiveCD, it would load the LiveCD normally. I was able to see my Windows disks and their data from the LiveCD as well.

Also, running fdisk showed me my NTFS partitions as well as my Linux and swap partitions. However, the linux partition had been marked bootable.

Solution:

Searching the forums I found some references to running fdisk, grub, using the Windows Restore Cd, etc. etc. but I didn't feel comfortable changing anything manually, especially since some solutions suggested to look at the /etc/grub directory, which didn't exist on my system! Perhaps, the installer had died before it could create the relevant files to that directory.

In any case, I wanted to restore my windows installation so that I could do a clean re-install of Ubuntu. 
From the LiveCD, I opened up a terminal window and ran gparted [Gnome's partitioning utility]. 
GParted also showed all of my NTFS partitions intact. I simply set the bootable flag on the partition which contained the XP OS and restarted the system. This time it booted from Win XP without any problems! :p

I intend to reinstall Ubuntu now. I was thinking of cleaning up the ext3 and swap partition created during the last install and then re-running the installer. Is there anything else that I should be worried about?

Thanks.

P.S. I have 2 suggestions: 
1. I wasn't able to find any help on troubleshooting installation problems. I think such a section somewhere on the support pages would really help.
2. The partitioning screens on the liveCD installation wizard are confusing. If the options could be reworded to make them simpler to understand, it would help non-technical users immensely.

---

### Post by Yoeri on 2007-05-29
Have you thought about just restoring the windows bootloader?

Simple instructions can be found here: [http://www.neowin.net/forum/lofiversion/index.php/t292614.html](http://www.neowin.net/forum/lofiversion/index.php/t292614.html)

---

