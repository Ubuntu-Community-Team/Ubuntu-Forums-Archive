---
title: "In need help in Installing Ubuntu - Thanks"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by biggerlense on 2008-03-09
I have 4 partition on the 500GB HD. As usual Windows XP reside in C.  I want to install Ubuntu on D:. Ubuntu wants to create a new partition on C: which I do not want. But I have no choice.  How can I install in on D:  Thanks.

---

### Post by Pumalite on 2008-03-09
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by Rocket2DMn on 2008-03-09
Have you checked this out? [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
When you get to the disk selection, you will choose your primary hard disk, then after clicking Forward will select the correct partition listed to install on.
In linux we don't use drive letters to recognize partitions, but rather devices that you mount on your file system.  You will need to figure out which partition listed is the one you want to install to.  For more info on that, open a terminal from the LiveCD and run
```
sudo fdisk -l
``` and show us the output.

---

### Post by Pumalite on 2008-03-09
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by biggerlense on 2008-03-09
> **Rocket2DMn said:**
> Have you checked this out? [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
When you get to the disk selection, you will choose your primary hard disk, then after clicking Forward will select the correct partition listed to install on.
In linux we don't use drive letters to recognize partitions, but rather devices that you mount on your file system.  You will need to figure out which partition listed is the one you want to install to.  For more info on that, open a terminal from the LiveCD and run
```
sudo fdisk -l
``` and show us the output.

Hi,

Your (-1) switch did not work, I used  (-l) instead, which gave me the following :

DEVICE BOOT    START           END               BLOCKS          ID                SYSTEM

/dev/sda1*                 1          6375           51207156           7            HPFS/NTFS
/dev/sda2             6376        60801         437176845           f            W95Ext'd (LBA)
/dev/sda5             6376        12750           51207156          7             HPFS/NTFS
/dev/sda6           12751        25498         102398278+       7             HPFS/NTFS
/dev/sda7           25499        51582         209519698+       7             HPFS/NTFS
/dev/sda8           51583        60801           74051586         7              HPFS/NTFS

I tried to install using /dev/sda5 which is the preferred partition, but I got the following :

"No Root file system is defined. Please correct this from the Partition Menu"

I think I have to study more.  Thanks for your help

---

### Post by Rocket2DMn on 2008-03-09
That is a lowercase L, it just looks a 1 (one) under the code region, sorry for not pointing that out to begin with.  
When you install, you have to give a root partition ( denoted by a / rather than a drive letter ) and a swap partition.  The root partition should be formatted as "ext3" (it can't be on NTFS - that partition needs to be deleted), and the swap partition has its own, awesomely named filesystem called "swap".

---

