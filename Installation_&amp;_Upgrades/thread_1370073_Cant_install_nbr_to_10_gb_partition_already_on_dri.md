---
title: "Cant install nbr to 10 gb partition already on drive?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by xiake on 2010-01-01
Hey i made a 10gb partition last time i had linux installed on my netbook. im trying to install ubuntu nbr on that partition when i try to select the 10gb partition(comes up as free space) it says "No root file system is defined please correct this from the partitioning menu" ? I dont get it last time i installed it i had the option to resise my windows partition thats how i made it. any help appreciated thanx :)

---

### Post by pastalavista on 2010-01-01
> **xiake said:**
> Hey i made a 10gb partition last time i had linux installed on my netbook. im trying to install ubuntu nbr on that partition when i try to select the 10gb partition(comes up as free space) it says "No root file system is defined please correct this from the partitioning menu" ? I dont get it last time i installed it i had the option to resise my windows partition thats how i made it. any help appreciated thanx :)

You need to use the MANUAL installation option and designate the partition as "/" which is the root directory.

---

### Post by presence1960 on 2010-01-01
use the manual option as pastalavista said. Right click the partition you want to install to and choose Change. A window will open. For "Use as" select filesystem you want to use, usually ext3 or ext4-but there are other linux filesystems available to use. Any windows filesystem will not work. Tick the format box. At the mount point selection use the drop down box to select /. Now you will be good to go.

---

