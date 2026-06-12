---
title: "Quad boot partition size"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by albertkao on 2010-01-02
My Acer X1800 computer has Intel Core 2 Quad Processor Q8200, 4G RAM, integrated NVIDIA GeForce 7100 graphics card and a 640GB harddisk with Windows 7 preinstalled.
I want to install kubuntu 8.0.4, 9.10 and fedora 12 to make it quad boot.
Is that possible?
What are the procedures and caveat?
How should the partitions be allocated (size and type)?
e.g.
Windows 7 - 200GB 
kubuntu 8.0.4 - 145GB
kubuntu 9.10 - 145GB
fedora 12 - 145GB
Should Windows 7 partition be C and D (instead of C only)?
If the Windows 7 partition has C and D, how is 200GB allocated between them?
Should linux partitions be / (root), /home, swap and /usr?
How big should they be?

---

### Post by oldfred on 2010-01-02
I think having data partitions for data that then can be shared easily makes the most sense. For the last 3 years I dual booted win & ubu and had a shared FAT partition for my photos and profiles for thunderbird and firefox. I was then able to boot either and have the same data.
My upgrade to Karmic I did a clean install and moved to a separate /home but also created a data directory for all my linux data. Now I am not sure I even need a separate /home as all the data is in /data and only the hidden config files are in /home and it is less than 1GB. I cannot now recommend FAT but I also converted my win shared to NTFS. Some do not recommend keeping any data in the win boot partition. I do not think you need a separate /usr. You can share swap if you do not hibernate as the other boot would overwrite your hibernation.

If you have separate data partitions each linux install can be 15 or 20GB. You cannot share home but can link all the data into home for all the linux installs. I also mount my windows data partition into /home, so home has all my data but it is really on separate partitions.

You can make the data partitions as large as possible but you have to decide how much you may share with windows and how much you will only share with other linux installs.

---

### Post by ajgreeny on 2010-01-02
I agree with oldfred.  If you are putting all your data files, docs, photos, videos, music etc etc on a separate single partition, it will be the best move you can make.  You may need to create a "mail" folder there as well, and link all the various "mail" folders in your mail client, eg ~/.mozilla-thunderbird/rqxrmg4n.default/Mail to that universal folder, but the need for that will depend on how you get your emails.

I still suspect that a separate /home partition for each distro is worthwhile just in case you need to reinstall them at any time, and don't forget that much of your configuration of the system, and all your emails etc etc are stored in home; if it's separate, it makes life simpler, in my view.

---

### Post by albertkao on 2010-01-03
> **oldfred said:**
> I think having data partitions for data that then can be shared easily makes the most sense. For the last 3 years I dual booted win & ubu and had a shared FAT partition for my photos and profiles for thunderbird and firefox. I was then able to boot either and have the same data.
My upgrade to Karmic I did a clean install and moved to a separate /home but also created a data directory for all my linux data. Now I am not sure I even need a separate /home as all the data is in /data and only the hidden config files are in /home and it is less than 1GB. I cannot now recommend FAT but I also converted my win shared to NTFS. Some do not recommend keeping any data in the win boot partition. I do not think you need a separate /usr. You can share swap if you do not hibernate as the other boot would overwrite your hibernation.

If you have separate data partitions each linux install can be 15 or 20GB. You cannot share home but can link all the data into home for all the linux installs. I also mount my windows data partition into /home, so home has all my data but it is really on separate partitions.

You can make the data partitions as large as possible but you have to decide how much you may share with windows and how much you will only share with other linux installs.

Only one linux partition for swap and boot are allowed, aren't they?
What are the installation procedures and caveat?
Master Boot Record (MBR) should be put in the boot partition, shouldn't it?
Are the following partition sizes and arrangement reasonable?
Windows 7 - 200GB 
   C - 100GB (program). ntfs
   D - 100GB (data). ntfs
Linux - 450GB
   swap - 6004MB
   /boot - 200MB. Resiser FS
   /data - rest of drive
kubuntu 9.10
   / - 40GB. ext3
   /home - 10GB. ext3
kubuntu 8.0.4
   / - 40GB. ext3
   /home - 10GB. ext3
fedora 12
   / - 40GB. ext3
   /home - 10GB. ext3

---

### Post by oldfred on 2010-01-04
You cannot share /boot so having multiple installs should have their own boot in the root. I created a large root and installed lots of programs and still have used 5.4GB with separate  /home and two data partitions. /home with all data linked in is less than 1GB. I have my system set up so I can link all the same data in all my Ubuntu installs.

---

### Post by albertkao on 2010-01-05
> **oldfred said:**
> You cannot share /boot so having multiple installs should have their own boot in the root. I created a large root and installed lots of programs and still have used 5.4GB with separate  /home and two data partitions. /home with all data linked in is less than 1GB. I have my system set up so I can link all the same data in all my Ubuntu installs.

Master Boot Record (MBR) should be put in the boot partition, shouldn't it?
My partition sizes should be like:
Windows 7 - 200GB 
   C - 100GB (program). ntfs
   D - 100GB (data). ntfs
Linux - 450GB
   swap - 6004MB
   /data - rest of drive
kubuntu 9.10
   / - 80GB. ext3
   /home - 1GB. ext3
kubuntu 8.0.4
   / - 80GB. ext3
   /home - 1GB. ext3
fedora 12
   / - 80GB. ext3
   /home - 1GB. ext3

---

### Post by oldfred on 2010-01-05
MBR is not a partition but just the first sector of the hard drive. It does not count as part of the four primary partitions or three primary and one extended containing many logical partitions. 
Systems boot from the BIOS, to the MBR of the first/master hard drive which then tells which partition/files to continue the boot process.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
h
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

Edit:
If you are going to keep a separate /home it should be larger than 1GB that is about what mine is currently. I was just saying that with data elsewhere the separate /home is not so large as to be easy to backup for reinstalls. The separate data partition(s) mitigate the need for a separate /home as normally home is full of all your data as well as the user settings.

---

