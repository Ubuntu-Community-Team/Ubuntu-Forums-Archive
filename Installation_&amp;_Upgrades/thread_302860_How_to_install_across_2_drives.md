---
title: "How to install across 2 drives"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by CallsignBaron on 2006-11-19
My system has 2 60GB harddrives. I used to dual boot with WinXP. I have since dumped WinXP and want to install Edgy across both drives. I would like to install all of Edgy on the first drive and then have the second drive as /vault so that it could easily be accessed from nautilus. I am an ametuer photographer and would like to have the /vault partition on all of the second drive to store photos. I did this with Debian at install because the installer allowed me to select more than one drive but when I try to install Edgy it only allows me to pick one or the other. Is there anyway I can set this up during the install process so that I don't have to create this after install then try to mount the partition? Editing fstab is not something I am very good at and would prefer if I could set this up during the install process and have it ready at first boot. I would appreciate any help I could get from all you Ubuntu Gurus. :)

Thanks,
Baron

---

### Post by confused57 on 2006-11-19
I'm not a guru by any means, but you should be able to use the manual partitioning option:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You should be able to set up your partitions for Edgy installation on hda(or sda), partition your second drive(hda?) and set a mount point during the partitioning.  You might want to go to the homepage of the above link and check out the section on "Plan Partitions".  You might want to read over the links, then post back how you plan on setting everything up before you actually begin the install.

I've read in other posts that if you set the mountpoint as /media/vault, there will be an icon for the drive partition on the desktop; if you select /mnt/vault, you won't have an icon on the desktop, but you should be able to access the drive(partition) in nautilus...as I mentioned, I'm not an expert ...just wanted to give you some suggestions.

I've never installed with the desktop live cd, I prefer to use the alternate cd...here's some excellent screenshots, using the alternate install:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Also, the above website has some excellent information for filesystems and mounting, especially for the Edgy fstab entries:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by CallsignBaron on 2006-11-20
That is the info I was looking for confused57. Thank you very much. I don't know how I missed that option to manually edit the partition table but that is what I was looking for. Thanks again.

Regards,
Baron

---

