---
title: "Question about reinstalling"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by Sahil Tandon on 2012-07-28
Hi, Im currently on a 32bit ubuntu 12.04 machine. I would like to reinstall ubuntu in a 64bit mode so I can take advantage of ram etc.

NOTE: I also have windows 7 on my other SSD

The things is:

1) Is it a simple matter of formatting the partition and installing it freshly?

2)Does a 64bit ubuntu utilize all cores when booting and does it allow more than 16GB of ram?

Thanks!!

---

### Post by Elfy on 2012-07-28
1) Is it a simple matter of formatting the partition and installing it freshly?
Yes.

2)Does a 64bit ubuntu utilize all cores when booting and does it allow more than 16GB of ram?
Yes.


Backup data that you want to keep.

Boot with install medium.

Make sure you know which partition has the install on it currently. Running 

sudo fdisk -l

from a terminal will tell you your partitions.

Start the install - when you are prompted where to install, choose Something Else

Select the partition that has current install on it.

Edit/Change - choose suitable filetype - ext4 - select format partition option and choose / from the mountpoint options.

Proceed and the 64bit install will overwrite the 32bit install.

---

