---
title: "Has anyone dual booted windows with ubuntu 18.04?"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by steveeq1 on 2019-04-20
I want to dualboot windows with ubuntu 18.04. However, I also want my ubuntu partition encrypted but the installer insists on partitioning the whole drive for ubuntu. Normally, I would just use gparted to reduce the size of the partition, but the lkm/luks thing is throwing it off. I tried going through several guides to no avail.

Is there something simple I am missing. I would imagine a ubuntu/windows pairup would be quite common.

---

### Post by Rubi1200 on 2019-04-20
Hi,

Are you saying that when you wanted to install you were only given the option to install on the whole drive? No option to install alongside or something else?

What version of Windows do you have?

Without repairing anything, from the liveCD/USB run the boot info summary and post it here so we can get a better overview of the current setup. Link is in my signature (just the summary please, no repairs).

Thanks.

---

### Post by steveeq1 on 2019-04-22
That is correct. If you install fresh ubuntu installation a drive, and specify "encrypt" on the installation, the ubuntu installer removes ALL partitions on the drive, and creates a bunch of new ubuntu-related partitions. These partitions use luks and lvm. I cannot resize the partition after installation because of luks apparenly makes the whole partition full so gparted can't reduce the size of the partition. There is no option during installation to install to a smaller partition, although that option is given when you DON'T encrypt.

I am using windows 10

---

### Post by Rubi1200 on 2019-04-22
I've never used LVM/LUKS so cannot properly advise you on that.

Please start by referring to the documentation here:
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

---

### Post by oldfred on 2019-04-23
I do not use LVM nor encryption as I only have desktops.
But saved some links which should still be valid:
       2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows) 
    
Lots of info on encrypted install, but not dual booting:
       [https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

