---
title: "Ubuntu on an external Hard Drive?"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by doomsayer97 on 2008-04-20
Hey everyone. I was just wondering something.... I want to install Ubuntu on my external hard drive but I am also using it as a back up for 2 of my computers. I was just wondering if when I partitioned the drive during the installation whether or not I could access those files because most of the files on my hard drive are files that I need, whether it be for school or for work or something. So, can I still get to those files if I have partitioned the drive? I need to access them from both my Ubuntu and XP computers... I'm thinking that if I mount it, I should be able to go into it and open the files, and if I boot from the hard drive that I'll go into Linux.

---

### Post by Rocket2DMn on 2008-04-20
If you partition the drive correctly to keep the old partitions by resizing them to make room for Ubuntu partitions (root and swap), you should be able to pull it off.  I would be very careful though, make sure you backup all that important data somewhere else before you attempt to repartition and install.  Things can go sour, or more commonly, you might screw up the repartitioning scheme on accident and delete your files.
Since you want to access them from both linux and windows, you should just keep them as ntfs partitions.  FAT32 works, too, but has the 4GB file size limit.

---

### Post by Spartan.II.117 on 2008-04-20
also make sure you setup a small partition on your internal drive for /boot, unless your computer is set to boot from usb before the hard drive.

---

### Post by unutbu on 2008-04-20
These pages may answer some of your questions

[https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed](https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed)
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html)

I would recommend backing up all the data on the external hard drive before you attempt to install Ubuntu. If you are experienced with repartitioning and installing Ubuntu then backing up may not be technically necessary, but things go wrong for enough people enough of the time that I feel confident that backing up first is a sound idea.

After the successful installation of Ubuntu, you'll have at least 3 partitions: a data partition (readable by XP and Ubuntu), the Ubuntu root partition, and a swap partition. 

You can configure Ubuntu to act as a file server with the XP machines as clients.
You'll need to install the samba package.

---

