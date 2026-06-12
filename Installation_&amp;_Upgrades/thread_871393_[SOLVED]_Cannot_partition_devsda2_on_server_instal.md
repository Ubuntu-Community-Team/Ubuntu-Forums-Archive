---
title: "[SOLVED] Cannot partition /dev/sda2 on server install"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by victorbrca on 2008-07-26
I tried installing Server 8.04 yesterday and I run into a problem. After partitioning the first part of my hard drive the remaining space became unusable. It actually showed by the partition manager on the install that it was unusable. 

One thing I noticed is that it would no allow me to flag the first partition bootable. My work around was to boot into a live CD and partition manually.

I'm installing a second server right now and am getting the same problem. Anyone knows why this is happening?


Thanks,

Vic.

---

### Post by Pumalite on 2008-07-26
Boot your Live CD and post a screenshot of Partition Editor.

---

### Post by victorbrca on 2008-07-26
> **Pumalite said:**
> Boot your Live CD and post a screenshot of Partition Editor.

Can't... it's on the server install... no gui.

---

### Post by Pumalite on 2008-07-26
'My work around was to boot into a live CD and partition manually.'
??

---

### Post by victorbrca on 2008-07-26
Couple of things I noticed: 

1- When editing the first drive it does not give me the option to set as primary or secondary partition. I don't get the following screen:

[IMG]http://www.debianadmin.com/images/ubuntulamp/17.png[/IMG]


2- On the main "drive edit" page I do not get the option to set a bootable flag:

[IMG]http://www.debianadmin.com/images/ubuntulamp/19.png[/IMG]


3- When I go back to the main disk setup page the second partition shows as unusable:

[IMG]http://www.debianadmin.com/images/ubuntulamp/22.png[/IMG]


4- When trying to edit the unusable partition I only get the option "Show cylinder/header/sector information"

[IMG]http://www.debianadmin.com/images/ubuntulamp/15.png[/IMG]

[B]
Note: These pictures are of a normal install and do not show the problem I'm having, but where the problem is.[/B]


Vic.

---

### Post by victorbrca on 2008-07-26
> **Pumalite said:**
> 'My work around was to boot into a live CD and partition manually.'
??

The problem is during Server version 8.04 install. When I was not able to do it there I booted into a normal Ubuntu desktop LiveCD and used the normal formating tools (fdisk, mkfs, mkswap...).


Vic.

---

### Post by Pumalite on 2008-07-26
There is a Partition Editor in your Live CD. You can use it to give me a screenshot. I want to see how your drive looks and maybe I can tell you why you can't use the space.

---

### Post by victorbrca on 2008-07-26
> **Pumalite said:**
> There is a Partition Editor in your Live CD. You can use it to give me a screenshot. I want to see how your drive looks and maybe I can tell you why you can't use the space.

Sorry about that! 

Would terminal outputs work? This is the PC I was having problems. After configuring the partitions with LiveCD I was able to install the server with no problem. I have no GUI on it:



```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.1G  716M  4.2G  15% /
varrun                252M   56K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   52K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sda2             1.9G   35M  1.8G   2% /home
/dev/sdc1             2.4G   68M  2.2G   3% /media/ftp
/dev/sdb1             2.0G  326M  1.6G  18% /media/www
```


```
# fdisk -l

Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0514

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         670     5381743+  83  Linux
/dev/sda2             671         914     1959930   83  Linux
/dev/sda3             915        1027      907672+  82  Linux swap / Solaris

Disk /dev/sdb: 2111 MB, 2111864832 bytes
255 heads, 63 sectors/track, 256 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8c4e2ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         256     2056288+  83  Linux

Disk /dev/sdc: 2577 MB, 2577383424 bytes
16 heads, 63 sectors/track, 4994 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x91819181

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4994     2516944+  83  Linux
```

---

### Post by HotCupOfJava on 2008-07-26
I understand what you are saying......he wants you to take a Live CD (not the server version you are trying to install, but another version) and use the GParted partitioner on it to look at the drive you are trying to install the server OS on. He doesn't want you to install from the live CD, just use the tools on it to figure out what might be going wrong with your server install.

You may have to use a Live CD again to set up the filesystem for the second install you are doing.....

---

### Post by victorbrca on 2008-07-26
> **HotCupOfJava said:**
> I understand what you are saying......he wants you to take a Live CD (not the server version you are trying to install, but another version) and use the GParted partitioner on it to look at the drive you are trying to install the server OS on. He doesn't want you to install from the live CD, just use the tools on it to figure out what might be going wrong with your server install.

You may have to use a Live CD again to set up the filesystem for the second install you are doing.....

I understood what Pumalite wanted too, just not why? No matter what the installer partitioner should be able to overwrite any settings that the hard drive may hold.

Anyways, I was able plug the HD on my laptop and set the partitions from there. 

I appreciate the interest and hope I ddn't waste anybody's time. I was more curious than anything else. Wanted to know if anyone had this issue before.

Cheers,

Vic.

---

### Post by Pumalite on 2008-07-26
Congrats!

---

