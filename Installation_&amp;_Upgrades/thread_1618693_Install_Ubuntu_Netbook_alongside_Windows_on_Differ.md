---
title: "Install Ubuntu Netbook alongside Windows on Different Partition"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by btsinbr on 2010-11-10
I want to install Ubuntu Netbook Edition alongside Windows 7.  My netbook has a manufacture partitioned drive.  I deleted the second partition and it is now free space.  When I go to install Ubuntu, I am only given one drive: /dev/sda.  What partition is this.  I want to install this on the free space area that was originally the second partition.  I originally tried to do this, before I deleted the partiton, however, I still had the same issue.

Thanks!

---

### Post by akand074 on 2010-11-10
/dev/sda is the entire hard drive, each partition is then on numbered. For example, windows could be on sda1, your recovery partition on sda2 etc. The auto-installer may find this unused space and use it for installing Ubuntu, but I'm not very familiar with the auto-installer. I would do a manual install, it would show you all the partitions there where you can manually pick and choose. Make sure you read up on how to do a manual install and do a backup before attempting it though.

---

### Post by Quackers on 2010-11-10
Welcome to UF :-)
First of all, what was on partition 2?
At the partitioning stage of the installation you should select the manual option. In the next screen look for the unallocated space that your deleted partition left. If you are happy that you have the correct space you can install Ubuntu there, but be very careful! If you make a mistake you WILL over-write something! Nothing is changed until you click on the final screen, which is after all your proposed changes are recapped.
If you are in any doubt please boot from your live cd and choose "try Ubuntu" then go to the site below and download the boot script to your DESKTOP and then run it in a terminal using the command given on the first page of that site.
This will create a results.txt file on your desktop.
Please copy the contents of that file and paste it in between CODE tags in your next post.
For CODE tags click on New Reply and then on the # symbol in the toolbar.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by laurenbanjo on 2010-11-10
Which partition did you delete? 'cause I have a netbook and I know that it has a partition for system recovery...

---

### Post by btsinbr on 2010-11-11
When I went to specify the partitions manually, it only gave me one drive /dev/sda.  In Windows I made a new partition which was the free space.  I still only see /dev/sda.

---

### Post by Quackers on 2010-11-11
Delete the new partition and leave it as unallocated space, then try again with the installation.

---

### Post by paall on 2012-08-07
@btsinbr did u figure out how to finally install ubuntu on netbooks? I am facing a similar problem. 

> **btsinbr said:**
> I want to install Ubuntu Netbook Edition alongside Windows 7.  My netbook has a manufacture partitioned drive.  I deleted the second partition and it is now free space.  When I go to install Ubuntu, I am only given one drive: /dev/sda.  What partition is this.  I want to install this on the free space area that was originally the second partition.  I originally tried to do this, before I deleted the partiton, however, I still had the same issue.

Thanks!

---

### Post by coffeecat on 2012-08-07
@paall, btsinbr has not logged in for about 18 months. Please start a new thread for yourself, giving details of your particular netbook and as much about the current partition layout as you can, and someone will be able to help you.

Old thread closed.

---

