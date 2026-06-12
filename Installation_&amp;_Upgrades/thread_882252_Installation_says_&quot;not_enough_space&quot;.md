---
title: "Installation says &quot;not enough space&quot;"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by hgfdsa on 2008-08-06
I get to step four out of seven of installation and decide to go with the first guided option which installs ubuntu alongside xp with default partition settings but get that error. Whenever i change the partition settings and hit forward, they go back to the defaults and I can't use them. My computer only has a single 200gb drive with one partition I am aware of. (ubuntu's folder navigator shows some other 6.5 gb folder along with my main partition.) My partition is formatted with NTFS, which i have heard ubuntu can have problems with. Anyway, any suggestions on what to do? Also, my USB wireless network adapter doesn't show up in ubuntu. Thanks.

---

### Post by pytheas22 on 2008-08-06
You have to make a separate partition for Ubuntu--you can't install Ubuntu inside the NTFS (Windows) partition.  The Ubuntu installer should auto-detect how much free space you have on your NTFS partition and make a suggestion regarding how much you want to shrink it to make room for Ubuntu; you can modify that suggestion as you like.  You can also choose to do partitioning completely manually if you want.

Also, keep in mind that another option that may interest you is [wubi]("http://wubi-installer.org/"), which allows you to install Ubuntu inside your Windows partition and avoid all of the partitioning issues of the normal installation.

---

### Post by skullmunky on 2008-08-06
The other 6.5 gb partition is probably a recovery or utility partition for restoring your Windows installation to factory defaults when it chokes and dies.  I've never actually had trouble with resizing an NTFS partition, myself.  Check to make sure you actually have enough free space on that drive - if all 200GB are already full, there may not be enough room.

You may have to defragment the drive in Windows first, also, particularly if you've had the computer for a little while already.  Even if you only 50 GB actually used, those 50GB could be all over the place on the drive, so defragmenting it tidies that up and moves everything to the front of the drive so there's enough room for the ubuntu installer to resize the partition.

btw, after you succeed installing ubuntu, don't forget that the first time you boot into Windows again it will run the disk check utility automatically, because the partitions have changed.  This looks terrifying but is normal.

---

### Post by hgfdsa on 2008-08-06
> **skullmunky said:**
> The other 6.5 gb partition is probably a recovery or utility partition for restoring your Windows installation to factory defaults when it chokes and dies.  I've never actually had trouble with resizing an NTFS partition, myself.  Check to make sure you actually have enough free space on that drive - if all 200GB are already full, there may not be enough room.

You may have to defragment the drive in Windows first, also, particularly if you've had the computer for a little while already.  Even if you only 50 GB actually used, those 50GB could be all over the place on the drive, so defragmenting it tidies that up and moves everything to the front of the drive so there's enough room for the ubuntu installer to resize the partition.

btw, after you succeed installing ubuntu, don't forget that the first time you boot into Windows again it will run the disk check utility automatically, because the partitions have changed.  This looks terrifying but is normal.

I talked to my brother about it, and he suggested defragmentation as well, considering I have 80 gb free, but only because I deleted a lot of large .iso and movie files very recently to make room for ubuntu. I also read on the forums that the automatic partitioner isn't the best option, and some people appear to have had problems with it. If I'm willing to dedicate 75 gb to ubuntu, what is the best way to allocate that space? How big does the linux swap need to be? Thanks.
> **pytheas22 said:**
> 
Also, keep in mind that another option that may interest you is [wubi]("http://wubi-installer.org/"), which allows you to install Ubuntu inside your Windows partition and avoid all of the partitioning issues of the normal installation.
I heard about that, but I thought it ran as program inside windows, which wouldn't really help me since I'm getting ubuntu as an alternative to reinstalling xp, which has become pretty slow and cluttered over the years especially when booting up.

---

### Post by pytheas22 on 2008-08-06
> Hi, i already done the installing the problem now is that i not even know wheter my wireless is on or off, because i have this easy-launch buttons that seems doesn't work including the wireless button...

Don't worry, wubi is a real installation of Ubuntu.  It doesn't run inside Windows and there's no virtualization involved; it's identical to a regular installation except that it runs from a disk image inside your NTFS partition, as opposed to a dedicated Linux partition.  See the wubi [frequently asked questions]("http://wubi-installer.org/faq.php") for more information.

> If I'm willing to dedicate 75 gb to ubuntu, what is the best way to allocate that space?

First of all, as others have said, make sure you defragment your NTFS partition (luckily in Linux defragmentation is not necessary).  Then run the installer and shrink your NTFS partition down to about 125 gigabytes, leaving 75 for Ubuntu.

After that, you simply create the partitions you need for Ubuntu.  Generally your swap partition should be twice the size of your RAM, and the best place to put it is between the NTFS partition and the Linux one.  Then you can make the rest of the free space into a Linux partition (you can choose to use ext3 or reiserfs filesystems; each has its advantages and disadvantages), setting the mount point to /

You may also want think about creating a separate partition for /home--this makes it easier if you have to reinstall Ubuntu for some reason, because your user's settings and files get preserved through reinstallations without a problem.  If you want to put /home on its own partition, create a third Linux partition from your empty space, and make the mountpoint /home.

---

### Post by hgfdsa on 2008-08-07
> **pytheas22 said:**
> Don't worry, wubi is a real installation of Ubuntu.  It doesn't run inside Windows and there's no virtualization involved; it's identical to a regular installation except that it runs from a disk image inside your NTFS partition, as opposed to a dedicated Linux partition.  See the wubi [frequently asked questions]("http://wubi-installer.org/faq.php") for more information.



First of all, as others have said, make sure you defragment your NTFS partition (luckily in Linux defragmentation is not necessary).  Then run the installer and shrink your NTFS partition down to about 125 gigabytes, leaving 75 for Ubuntu.

After that, you simply create the partitions you need for Ubuntu.  Generally your swap partition should be twice the size of your RAM, and the best place to put it is between the NTFS partition and the Linux one.  Then you can make the rest of the free space into a Linux partition (you can choose to use ext3 or reiserfs filesystems; each has its advantages and disadvantages), setting the mount point to /

You may also want think about creating a separate partition for /home--this makes it easier if you have to reinstall Ubuntu for some reason, because your user's settings and files get preserved through reinstallations without a problem.  If you want to put /home on its own partition, create a third Linux partition from your empty space, and make the mountpoint /home.
I rushed ahead and already installed ubuntu after defragmentation
so how do I delete ubuntu and split my current main linux partition into /home and /?

---

### Post by meindian523 on 2008-08-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

