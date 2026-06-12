---
title: "Upgrades take ages"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by keevill on 2013-02-17
I'm looking for advice regarding smooth upgrades to 12.04 usually from 10.04. 
I have several users and so far, each upgrade has been problematical.
Namely: The upgrade process takes a long time - several hours in fact. Even doing the upgrade using a CD media disk takes ages.
Even though I select the option to keep programs and settings, many things are lost, Thunderbird accounts, printers installed and several other things.
This means that because of the disruption to users, I have to select the day very carefully to do these upgrades.
Is there someone able to give me some pointers towards smooth fast upgrades ?

---

### Post by Bucky Ball on 2013-02-17
Yep, upgrades take several hours generally. Normal. I have edited your thread title as you have said 'updates' instead of 'upgrades'. Confusing as they are two very different processes.

You also use both 'upgrades' and 'updates' throughout your post. Please edit it and use one or the other for clarity and to help us help you. Thanks.

BB

PS: Much quicker (and often less problematic) to backup important personal files and install the new version, in your case 12.04 LTS.

---

### Post by keevill on 2013-02-18
> **Bucky Ball said:**
> Yep, upgrades take several hours generally. Normal. I have edited your thread title as you have said 'updates' instead of 'upgrades'. Confusing as they are two very different processes.

You also use both 'upgrades' and 'updates' throughout your post. Please edit it and use one or the other for clarity and to help us help you. Thanks.

BB

PS: Much quicker (and often less problematic) to backup important personal files and install the new version, in your case 12.04 LTS.

yes you are correct to point out my misuse of terminology. I have edited my post , hopefully correct now.
So if the upgrade takes so long, then indeed it is the best alternative to install the new version from a CD medium.
Thanks,

---

### Post by MrKaliman on 2013-02-18
Just for info ....
You are not using a crucial ssd v4 as harddisk?
Installing/updating/upgrading ubuntu on this ssd disk is waiting like ages

---

### Post by Frogs Hair on 2013-02-18
Bucky Ball has a good idea as far as backup and clean installation. The 10.04 to 12.04 upgrade can be messy and time consuming because of the change from Gnome 2 to 3. If you have custom Gnome 2 themes they won't work any more. You will see complete removal of some features on the desktop and in nautilus.

---

### Post by SeijiSensei on 2013-02-18
Seeing as you have several users, if you don't have a separate /home partition, this might be the time to make one.  Having /home on a separate partition means you can make changes to the operating system that don't affect the contents of users' home directories.  If you don't have a separate /home, then upgrading to 12.04 will require you back up your current /home anyway.  When you get to the partitioner in the installer, choose "manual".  Usually I have a 512 MB /boot partition with ext2 as the first primary, swap as the second primary, and assign the rest of the disk to extended.  In there I create a 10-20 GB partition for / and use all or most of the rest for /home.  Both of those use ext4.

---

