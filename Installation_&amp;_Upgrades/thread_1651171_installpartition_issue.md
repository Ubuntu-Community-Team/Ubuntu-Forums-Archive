---
title: "install/partition issue"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Flash__Gordon on 2010-12-22
I am having an issue installing Ubuntu on a laptop that I just installed a 1TB drive on. I installed windoze 7 on a smaller partition at beginning of drive. (had to as this was from recovery disks which create a hidden partition at beginning also). I then attempt to install ubuntu onto the partition I have for it (around 800 GB) which is already ext4. When I tell Ubuntu to install on this partition I get the following message. 

 "The partition /dev/sda3 assigned to / starts at an offset of 2048 bytes from the minimum alignment for this disk, which may lead to very poor performance. 

 Since you are formating this partition, you should correct this problem now by realigning the partition, as it will be difficult to change later. To do this, go back to the main partitioning menu, delete the partition, and recreate it in the same position with the same settings. This will cause the partition to start at a point best suited for this disk." 


I have done as asked SEVERAL times and to no avail. I have even reformatted entire drive, reinstalled windoze and then told the installer for Ubuntu to "install side by side" and still have same message. 

  I did have it come up with the offset of 3072 a few times while trying different partition sizes. 

Please tell me someone else has had this issue and resolved it. 

Thanks in advance, 
 Flash

 It is 10.04.1 and I also tried with alternate install disk.
 Laptop is Asus A72F, i3-370m, 2.4 ghz, 4 GB ram

---

### Post by Flash__Gordon on 2010-12-22
anyone?

---

### Post by oldfred on 2010-12-22
Is this one of the new 4k drives, not our old standard of 512 sectors.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

I also do not recommend a 800GB root partition. System will perform better if all the system files are closer together on the drive and you do not need that much.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. The extra root partition(s) are good for testing next version of Ubuntu or experimenting with other Linux.

You just may need the newest version of gparted.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Flash__Gordon on 2010-12-22
> **oldfred said:**
> Is this one of the new 4k drives, not our old standard of 512 sectors.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

I also do not recommend a 800GB root partition. System will perform better if all the system files are closer together on the drive and you do not need that much.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. The extra root partition(s) are good for testing next version of Ubuntu or experimenting with other Linux.

You just may need the newest version of gparted.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://partedmagic.com/](http://partedmagic.com/)

  Thanks for the info. I will look into the links and try the suggestions you have given. 

Flash

---

### Post by srs5694 on 2010-12-23
Please post the output of the following command:

```

sudo fdisk -lu

```

This will show us what you're dealing with.

There was a post a couple of days ago from somebody who was getting a similar message to yours, and it was spurious. In that case, it was triggered by the fact that an extended partition was not aligned to a 2048-sector (1 MiB) boundary, but that fact was irrelevant; all the primary and logical partitions were properly aligned. It could be the same thing is happening to you.

---

### Post by jspitanga on 2011-01-04
Same problem here, with a 640GB hard disk. Workaround was to use Reiserfs or XFS instead of ext4.

---

