---
title: "Partitioning"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by rasmus91 on 2008-02-09
Hey.

I have a problem partitioning, i would like if any one would tell me how to take a part of the windows harddrive and install ubuntu 7.10 on it, without deleting any files?

---

### Post by mikewhatever on 2008-02-09
What is the problem?

---

### Post by Pumalite on 2008-02-09
If Vista, allocate space for Ubuntu with Vista's partitioner. If XP, get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP and choose 'resize' from the menu. In the new space, make 3 new partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Install Ubuntu, go Manual and use the already prepared partitions.
Backup everything first.

---

### Post by lswest on 2008-02-09
first, defragment the XP partition, as it minimizes possible problems.  Then when you're done, boot to the liveCD, and then resize the XP partition during the partitioning stage (it will ask you were you want to install ubuntu to) and you can also choose the option "resize partition"  (i usually do "manual") or so (not entirely sure, been a while since i installed ubuntu XD and i never used that option).  Basically then it takes the XP partition, shrinks it, and creates the partitions for linux in the free space.

---

### Post by rasmus91 on 2008-02-09
... yeah, still got problems, can any of you guys tell me what a root filesystem is?...

i also need to be sure that youve noticed that i DO NOT WANT to delete Windows. i just want to take a small part of the HD and install Ubuntu on it.

---

### Post by lswest on 2008-02-09
a root filesystem is the filesystem that is mounted at "/" in linux and which stores all information (excluding /home files if you make a seperate partition for that) and yes, we know you don't want to delete XP, that's why our advice has been on shrinking XP's size so you have room for Linux.  Don't worry, we're pretty good at reading posts^^

---

### Post by rasmus91 on 2008-02-09
Yeah.... but how do i change the size of the xp partition, xp runs in the NFTS system,but if i press resize its like all of the partitions is turned into free space, and i cant create a NFTS partition for windows... What do i have to do please tell me a little detailed. Do i just have to erease all partitions or what?

also: if i have too make a Ubuntu partition, please tell me what to mount. im booting from the live 7.10 version cd, just to make sure you know

---

### Post by mikewhatever on 2008-02-09
> **rasmus91 said:**
> Yeah.... but how do i change the size of the xp partition, xp runs in the NFTS system,but if i press resize its like all of the partitions is turned into free space, and i cant create a NFTS partition for windows... What do i have to do please tell me a little detailed. Do i just have to erease all partitions or what?

also: if i have too make a Ubuntu partition, please tell me what to mount. im booting from the live 7.10 version cd, just to make sure you know

You do not have to erase Windows, just follow this guide and you should be fine --> [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by rasmus91 on 2008-02-09
Thank You!

---

### Post by rasmus91 on 2008-02-09
this doesnt help me very much... i cant get the "space line" where you choose how big a partition i wantto create, to apear. it just says something about the root file system has to be configured.

any suggestions?

---

### Post by Pumalite on 2008-02-09
In the 'space' you have, choose about 20000 and give it a mount point of '/'. Then /swap with mount point '/swap', then /home (the rest) with mount point '/home'

---

### Post by mikewhatever on 2008-02-09
> **rasmus91 said:**
> this doesnt help me very much... i cant get the "space line" where you choose how big a partition i wantto create, to apear. it just says something about the root file system has to be configured.

any suggestions?

You have to do what it says. Root is the partition where Ubuntu OS lives, so to speak. You can't omit it.

---

