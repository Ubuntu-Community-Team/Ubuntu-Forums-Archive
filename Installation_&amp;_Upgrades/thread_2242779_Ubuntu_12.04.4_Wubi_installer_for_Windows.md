---
title: "Ubuntu 12.04.4 Wubi installer for Windows"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by panjgoori on 2014-09-03
Hello everyone. I need wubi installer for Ubuntu 12.04.4. I found one from here [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) but its for 12.04.5. If anyone can give me its link. Thanks.

---

### Post by uRock on 2014-09-04
12.04.5 is 12.04 with updates applied, so that users don't have so many updates to do when they install. It also gives them a chance to fix any installer bugs they are having.

---

### Post by yancek on 2014-09-04
You don't indicate which windows you are using.  If you have windows 8, it won't work according to the Ubuntu site.  Probably will with earlier windows although i understand it is not being developed any longer and will not be supported.

---

### Post by panjgoori on 2014-09-04
> **uRock said:**
> 12.04.5 is 12.04 with updates applied, so that users don't have so many updates to do when they install. It also gives them a chance to fix any installer bugs they are having.

i know but i have a slow connection thats why i don't want to download 12.04.5. and the wubi installer present at the link which i gave above require 12.04.5.

> **yancek said:**
> You don't indicate which windows you are using. If you have windows 8, it won't work according to the Ubuntu site. Probably will with earlier windows although i understand it is not being developed any longer and will not be supported.

Oops sorry. I'm using Windows 7. i know that wubi doesn't support Windows 8 thats why im not using it.

---

### Post by fantab on 2014-09-04
WUBI is not supported anymore. It is recommended that you DON'T use WUBI. Instead install Ubuntu on its separate partition and setup a 'true' dual-boot with win7.
Backup your data and [uninstall Wubi]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")... Then install ubuntu to its own partition.

---

### Post by mörgæs on 2014-09-04
... and if you do a real dual boot I recommend 14.04.1 and not the 12.04 family.

---

### Post by kansasnoob on 2014-09-04
> **mörgæs said:**
> ... and if you do a real dual boot I recommend 14.04.1 and not the 12.04 family.

+1!

Those who do want or need Precise need to be aware of LTS HWE:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Installing Precise with either the 12.04.2, 12.04.3, or 12.04.4 images will land a user in HWE EOL with an unsupported kernel:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

Those who install using the latest 12.04.5 images will be on the Trusty HWE stack anyway so they might as well give Trusty a try.

Those who require an older kernel or X stack can get the original 3.2 series kernel and matching X stack (which is supported until April 2017) only by installing with the archived 12.04 or 12.04.1 images:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by panjgoori on 2014-09-06
is there easy way to do manual install of Ubuntu 14.04 without losing my files stored in HDD ?

---

### Post by kansasnoob on 2014-09-06
> **panjgoori said:**
> is there easy way to do manual install of Ubuntu 14.04 without losing my files stored in HDD ?

Some Windows 7 OEM's used 4 primary partitions so I suppose we should start with some very basic info. Do you have a current Wubi install running on that machine? Or do you have any Ubuntu live DVD's laying around that you could use to gather info from a live session?

---

### Post by panjgoori on 2014-09-06
> **kansasnoob said:**
> Some Windows 7 OEM's used 4 primary partitions so I suppose we should start with some very basic info. Do you have a current Wubi install running on that machine? Or do you have any Ubuntu live DVD's laying around that you could use to gather info from a live session?

i have 3 partitions in my HDD. I haven't installed Wubi yet and yes I have a DVD which contain Ubuntu 12.04.

---

### Post by yancek on 2014-09-06
If you currently have 3 partitions in use by windows 7, you should be able to create an Extended partition with logical partitions in it on which to install Ubuntu.
I use windows on rare occasions so based on reports from other, run disk defragmenter and may chkdsk on windows then from windows 7, shrink the windows partitions so that you have free/unallocated space on which to install Ubuntu.  The link below is to a very detailed tutorial on installing Ubuntu 14.04 and also contains a lot of information on Linux and partitioning:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Mark Phelps on 2014-09-06
Not that I don't believe you, but with preinstalled Windows 7 systems, there is nearly always a FOURTH partition near the front of the disk.  It's small, usually does NOT have a drive letter, and contains the Windows loader and boot code.

To see if it is there, open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one).

---

### Post by yancek on 2014-09-06
> with preinstalled Windows 7 systems, there is nearly always a FOURTH partition

Nearly but not always.  My HP Pavilion Desktop had a boot, system, and recovery partition so maybe he only has three and will be able to create the Extended.

---

### Post by Mark Phelps on 2014-09-06
> so maybe he only has three and will be able to create the Extended. 

Maybe so ... but the results of the command will show us for sure.

---

### Post by panjgoori on 2014-09-07
> **yancek said:**
> If you currently have 3 partitions in use by windows 7, you should be able to create an Extended partition with logical partitions in it on which to install Ubuntu.
I use windows on rare occasions so based on reports from other, run disk defragmenter and may chkdsk on windows then from windows 7, shrink the windows partitions so that you have free/unallocated space on which to install Ubuntu. The link below is to a very detailed tutorial on installing Ubuntu 14.04 and also contains a lot of information on Linux and partitioning:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

So you mean that i have to shrink a partition to create a another drive with free space and then install ubuntu in that drive. Will this effect my files stored in my laptops HDD ?

> **Mark Phelps said:**
> Not that I don't believe you, but with preinstalled Windows 7 systems, there is nearly always a FOURTH partition near the front of the disk. It's small, usually does NOT have a drive letter, and contains the Windows loader and boot code.

To see if it is there, open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one).

well I agree with you. there is indeed one small drive size of 100mb but its hidden in My Computer and only visible when im removing/re-installing Windows.

---

### Post by hakuna_matata on 2014-09-07
> **panjgoori said:**
> i know but i have a slow connection thats why i don't want to download 12.04.5. and the wubi installer present at the link which i gave above require 12.04.5.

IMHO current Wubi for 12.04.5 installs all point releases of 12.04, if you disconnect internet connection while running wubi.exe

[http://bazaar.launchpad.net/~bcbc/wubi/lp1043607/revision/274](http://bazaar.launchpad.net/~bcbc/wubi/lp1043607/revision/274)

---

### Post by Mark Phelps on 2014-09-07
>  there is indeed one small drive size of 100mb

See, there are FOUR partitions, not three, as I suspected!  Meaning, you already have the maximum number of partitions allowed, and if you try to force the creation of a fifth, using Windows, you will then transform all your Basic Disks into Dynamic Disks -- something you do NOT want to do.

---

