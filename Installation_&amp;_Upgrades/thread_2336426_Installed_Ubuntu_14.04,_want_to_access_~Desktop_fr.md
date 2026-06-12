---
title: "Installed Ubuntu 14.04, want to access ~/Desktop from Windows..."
date: 2016-09-08
forum: Installation &amp; Upgrades
---

### Post by thacoda on 2016-09-08
Hi,

New to this forum, my first post, I am hoping to get some expert opinion and/or advises how to perform the following:

I installed Ubuntu v14.04 with *unetbootin* tool on a USB-stick. Reserved persistent space as well (casper-rw). Works all just fine. 

What I hope is possible, is to access the /home/ubuntu/Desktop directory from the Windows OS, before I boot up in Ubuntu and run the trial option (thus, no install). Ideally write a text file to this /home/ubuntu/Desktop directory in Windows OS, assuming this file will appear on the desktop of Ubuntu when started/booted up (choosing trial option @ boot menu). Like it would, if I do this action in Ubuntu, instead of Windows. Vise-versa, I can access the SSD drive where Windows is installed, from Ubuntu, no problem.

Obviously, I already browsed through all the folders in that USB-stick with Windows Explorer, but I came across no directory named as "Desktop". I better not elaborate where this or the actual Ubuntu OS possibly is located on this USB-stick, since I know jack about that obviously. My technical know-how on this subject is zero. 

So, can I access ~/Desktop of Ubuntu in Windows or am I just a silly dreamer?

Thanks.

---

### Post by yancek on 2016-09-08
Ubuntu on a flash drive is a read-only filesystem.  You can write to the persistent partition and access it.  If you have a persistent partition, it will be a Linux filesystem.  A windows default system is not capable of reading much less writing to a Linux filesystem.  Linux systems are capable of reading and writing to ntfs or vfat partitions.

As you noticed, the directories and files on the Ubuntu installation media are not the same as those on an installed Ubuntu so you will not see a 'Desktop directory until you boot Ubuntu.

If you want a text file you have created on windows on the Ubuntu persistent flash drive, boot Ubuntu and select to try Ubuntu and go to the windows system and copy it to your Ubuntu Desktop.  If you have persistence, it should be there on reboot.

---

