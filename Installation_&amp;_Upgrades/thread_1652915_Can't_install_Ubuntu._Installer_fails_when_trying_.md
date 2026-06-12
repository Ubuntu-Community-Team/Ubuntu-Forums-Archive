---
title: "Can't install Ubuntu. Installer fails when trying to write to hard-drive!"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by na5h on 2010-12-25
Hi! I'm trying to install Ubuntu Maverick on an Acer Travelmate laptop with Windows Vista on it. Every time I try it, the installer gives me an error message when trying to write/install the files to the hard-drive. I know that the CD is not faulty, I have used it during several installations before. I also know that there is nothing wrong with the laptops cd/dvd drive, because I get the same error when trying to install from a bootable USB-stick. Recently, I have also started to get one of those "SMART hard-drive failure predicted"-messages when I boot up the laptop (after trying to install Ubuntu and failing).

I set up the partitions in advance using Vista. Then I just used the Ubuntu Installer to manually specify swap and ext4 from the unallocated space that I "reserved". But Ubuntu just can't seem to write anything to the hard-drive when it starts to install. 

What could be wrong? Could the hard-drive really be defect? I got the "SMART" messages at boot after trying to install Ubuntu several times and failing (never before). Everything works "fine" in Vista (it's Vista so it's never fine, but...you get the idea). I have installed Ubuntu on several computers, but never before encountered anything like this. :confused:

---

### Post by Quackers on 2010-12-25
Have a look at the website of the hard drive manufacturer and see if they have a hard drive test program (most do) and run it. That may confirm or deny any HDD problem.

---

### Post by JC Cheloven on 2010-12-25
hi na5h, 

Perhaps you are trying to define more than 4 primary partitions in the disk? If unsure about what I mean, please post the output of ```
sudo fdisk -l
```(from live) so that we can have a look.

---

### Post by gringo guy on 2011-01-14
Are you referring to the "[Errno5] Input/Output error" message? If so, this error is very misleading, and has been a problem for years. Some people report that *removing* some memory helps, but that didn't work for me. Go get the alternate install CD--this uses a different install interface, and it should work fine. 

There are a lot of serious problems with the ubiquity installer (over 1,500 open defects, and [only TWO in progress]("https://bugs.launchpad.net/ubuntu/+source/ubiquity")??!) Thank goodness for the alternate CD! I sure hope that some of the Ubuntu derivatives begin using an alternate install strategy also.

---

