---
title: "Not able to create extended partition"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by R J on 2007-12-11
I have never created an extended partition before, so I am not sure what I am doing wrong. I have searched here and the web, but I don't see any solutions. 

Anyway, I have a 100GB partition that I want to install ubuntu on. I already have 4 primary partitions, so I need to create an extended partition in the 100GB partition that I have set aside for ubuntu. The problem is, when I run diskpart to create the extended partition, it keeps telling me "There is insufficient free space to create a partition at the specified size and offset. Specify different size and offset or don't specify either to create the maximum sized partition."

I have tried running the command "create partition extended" without specifying the size, and it continues to give me the same message. There is about 2.5GB of unallocated space. 

Could this be a limitation of the diskpart utility? (because of the size of the partition)

Any help would be appreciated.

BTW, the extended partition is for the swap drive.

---

### Post by jimrz on 2007-12-11
> **R J said:**
> I have never created an extended partition before, so I am not sure what I am doing wrong. I have searched here and the web, but I don't see any solutions. 

Anyway, I have a 100GB partition that I want to install ubuntu on. I already have 4 primary partitions, so I need to create an extended partition in the 100GB partition that I have set aside for ubuntu. The problem is, when I run diskpart to create the extended partition, it keeps telling me "There is insufficient free space to create a partition at the specified size and offset. Specify different size and offset or don't specify either to create the maximum sized partition."

I have tried running the command "create partition extended" without specifying the size, and it continues to give me the same message. There is about 2.5GB of unallocated space. 

Could this be a limitation of the diskpart utility? (because of the size of the partition)

Any help would be appreciated.

BTW, the extended partition is for the swap drive.

You can only have 4 primary partitions, one of which may be an extended partition to contain numerous other partitions, on the same hdd. Is the 100Gb partition currently empty ? or does it contain only data you do not need to keep? If so, first delete the current partition then, in it's place, create your extended partition. You can then create your ubuntu partitions within the new extended partition. I would suggest three for ubuntu, "/" +"/home" (keeping this separate is frequently handy should you need/want to do a re-install) + "swap" (if this is on a laptop make sure it = at least 1.5 times your amount of ram, so that you may be able to use suspend)

Welcome ... good luck and enjoy your new toy ;)

---

### Post by R J on 2007-12-11
> **jimrz said:**
> You can only have 4 primary partitions, one of which may be an extended partition to contain numerous other partitions, on the same hdd. Is the 100Gb partition currently empty ? or does it contain only data you do not need to keep? If so, first delete the current partition then, in it's place, create your extended partition. You can then create your ubuntu partitions within the new extended partition. I would suggest three for ubuntu, "/" +"/home" (keeping this separate is frequently handy should you need/want to do a re-install) + "swap" (if this is on a laptop make sure it = at least 1.5 times your amount of ram, so that you may be able to use suspend)

Welcome ... good luck and enjoy your new toy ;)

Thank you very much for the reply. When I load up disk part and enter the command to create the extended partition, it first wants me to select a disk. This is why I created the primary partition for Ubuntu, so that I could select that partition when creating the extended partitions. So, what primary should I select when creating the extended partitions for Ubuntu? Or should I be using another command besides create partition extended?

---

### Post by jimrz on 2007-12-11
> **R J said:**
> Thank you very much for the reply. When I load up disk part and enter the command to create the extended partition, it first wants me to select a disk. This is why I created the primary partition for Ubuntu, so that I could select that partition when creating the extended partitions. So, what primary should I select when creating the extended partitions for Ubuntu? Or should I be using another command besides create partition extended?

An extended partition is actually counted as of of your 4 allowable primary partitions. So all you  should need do is delete the one you made for ubuntu which will create unallocated space for your extended partion to be created in and get you down to where, after creating the extended partition, you will not be trying to exceed the max number of primary/extended partions allowable. Then you may proceed to create your ubuntu partitions, described above, within your extended partition. In case you are concerned, ubuntu will boot just fine from the  "/" partition even though it is within your extended partition. I have not used disk part (used to use partition magic, until I discovered the g-parted "live" cd which is all I ever use now) so am not sure of the exact command that you would be looking for.

If you would like a copy, g-parted "live" cd is available for download [[COLOR="Sienna"]*** here***[/COLOR]]("http://gparted.sourceforge.net/livecd.php") from sourceforge.org.

---

### Post by R J on 2007-12-11
> **jimrz said:**
> An extended partition is actually counted as of of your 4 allowable primary partitions. So all you  should need do is delete the one you made for ubuntu which will create unallocated space for your extended partion to be created in and get you down to where, after creating the extended partition, you will not be trying to exceed the max number of primary/extended partions allowable. Then you may proceed to create your ubuntu partitions, described above, within your extended partition. In case you are concerned, ubuntu will boot just fine from the  "/" partition even though it is within your extended partition. I have not used disk part (used to use partition magic, until I discovered the g-parted "live" cd which is all I ever use now) so am not sure of the exact command that you would be looking for.

If you would like a copy, g-parted "live" cd is available for download [[COLOR="Sienna"]*** here***[/COLOR]]("http://gparted.sourceforge.net/livecd.php") from sourceforge.org.

Thanks very much again. I did create the GParted CD, but I wasn't sure how to get started. When you boot up the disk, you get a startup screen that is fairly confusing. You have to choose from a bunch of options and I wasn't sure what to choose, or what whould happen when I make a choice. I see in the documentation it recommends to choose the first option, but I wasn't sure what "auto-configuration" means; I was afraid that it was going to start making changes on it's own...


Anyway, I guess I will roll the dice and give it a try.

---

### Post by jimrz on 2007-12-11
> **R J said:**
> Thanks very much again. I did create the GParted CD, but I wasn't sure how to get started. When you boot up the disk, you get a startup screen that is fairly confusing. You have to choose from a bunch of options and I wasn't sure what to choose, or what whould happen when I make a choice. I see in the documentation it recommends to choose the first option, but I wasn't sure what "auto-configuration" means; I was afraid that it was going to start making changes on it's own...


Anyway, I guess I will roll the dice and give it a try.

It won't do anything on it's own. I think the auto config is to get the live cd running, from there you can do the actual work and you input the instructions for the changes that you want to make.

---

### Post by R J on 2007-12-11
> **jimrz said:**
> It won't do anything on it's own. I think the auto config is to get the live cd running, from there you can do the actual work and you input the instructions for the changes that you want to make.

It's probably an effective technique to get people to read the manual before starting.

OK, I have another question. You mentioned creating three partitions, "/", "/home" and one for swap. I guess I will make the swap drive 4GB since I have 2GB of RAM? What sizes should I make the other partitions (I have 100GB to work with)? Also, what do I install on the "/home" partition? During the ubuntu installation, I only saw the option to select one partition for installing.

---

### Post by R J on 2007-12-11
I was checking out this page which gives me a good idea of what to do: [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Actually, I think I'll just use the same partition for my home directory. I can do a more advanced setup later if I need to.

Thanks a lot for the help.

---

