---
title: "Ubuntu over Slackware -Format questions"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by goofeedude on 2005-10-18
Hi,
 I currently dual boot Slackware 10.2 and WinXP pro. I am going to install Ubuntu 5.10 very soon, and I have practiced a few installs in a virtual machine, but every time, the partition utility leaves me with a queezy uneasy feeling (unfamiliar interface, very 'automatic').

Right now, Slackware is using ReiserFS, and has a 1 GB swap partition. I DO NOT want to repartition the disk, I only want to format Slack's partition to Ext3 and install Breezy to it. How can I skip the "partitioning" step? Even If I don't resize, delete, or make any changes to the partition table, but instead just change the FS type to Ext3, I am sure the program will say "Writing partition table to disk..." I only need formatting, not partitioning, and it's super important to me because I have data on that drive in NTFS partitions that I have no means of backing up.

Do you have any tips? How can I just format and install without have to use the included partitioning utility (like perhaps using mkfs and format instead or something)? Thanks for reading! :smile:

---

### Post by matthew on 2005-10-18
[quote=goofeedude]the partition utility leaves me with a queezy uneasy feeling (unfamiliar interface, very 'automatic').

Right now, Slackware is using ReiserFS, and has a 1 GB swap partition. I DO NOT want to repartition the disk, I only want to format Slack's partition to Ext3 and install Breezy to it. How can I skip the "partitioning" step? Even If I don't resize, delete, or make any changes to the partition table, but instead just change the FS type to Ext3, I am sure the program will say "Writing partition table to disk..." I only need formatting, not partitioning, and it's super important to me because I have data on that drive in NTFS partitions that I have no means of backing up.

Do you have any tips? How can I just format and install without have to use the included partitioning utility (like perhaps using mkfs and format instead or something)? Thanks for reading! :smile:[/quote]

1) if you change the format of a partition, i.e. from ReiserFS to ext3, by definition it WILL erase everything on the partition.

2) you can choose to "manually edit partitions" in the boot process and choose precisely which partitions are modified and which are not and how they are modified. That might ease a bit of the fear.

IF YOU DON'T WANT TO LOSE YOUR SLACKWARE DATA don't change the formatting of that partition.

---

### Post by SickTwist on 2005-10-18
[QUOTE=goofeedude]Hi,
 I currently dual boot Slackware 10.2 and WinXP pro. I am going to install Ubuntu 5.10 very soon, and I have practiced a few installs in a virtual machine, but every time, the partition utility leaves me with a queezy uneasy feeling (unfamiliar interface, very 'automatic').

Right now, Slackware is using ReiserFS, and has a 1 GB swap partition. I DO NOT want to repartition the disk, I only want to format Slack's partition to Ext3 and install Breezy to it. How can I skip the "partitioning" step? Even If I don't resize, delete, or make any changes to the partition table, but instead just change the FS type to Ext3, I am sure the program will say "Writing partition table to disk..." I only need formatting, not partitioning, and it's super important to me because I have data on that drive in NTFS partitions that I have no means of backing up.

Do you have any tips? How can I just format and install without have to use the included partitioning utility (like perhaps using mkfs and format instead or something)? Thanks for reading! :smile:[/QUOTE]

You bring up an interesting point--the "partitioning utility" could use a better name because it does so much more than just editing the partition table.

The easiest thing for you do do would be to try using the partitioning utility during the Ubuntu installation. When the first question about partitioning appears, choose the option to manually configure the partition table. The next screen will present a list where each line represents a partition. By selecting a line and pressing Enter, you can change the filesystem used (EXT3/ReiserFS/etc.) without changing the size and location of the partition itself.

[COLOR="Red"]**If you change the filesystem, you will loose all data stored on that particular partition.**[/COLOR]

You can also select how each partition is mounted ( /, /home, etc.) and other options. After the list of partitions looks the way that you want it to look, continue to the next screen which will list the changes that are about to be made. The changes will only take place if you accept them here.

If any of this seems confusing just remember that you can play with the partition utility without making any changes to the HDD. There are plenty of opportunities to bail out if you are worried. If you need more detail about any of these steps just ask.

---

### Post by goofeedude on 2005-10-18
Thank you guys so much for your replies, that's all I needed to know.

I know reformatting will erase all the data on the drive, Slackware is nice, but I'm a student, not a full time OS hacker (lol). Apt-get > source based package management.

Thanks again for your speedy and helpful replies!

---

### Post by SickTwist on 2005-10-18
No problem. I used Slackware once upon a time as well--it's a great system for learning the in's and out's of Linux. However, once I wanted to try new programs, keep the system patched or upgrade to the next version, Slackware's lack of dependency handling became too painful for me to deal with.

---

### Post by goofeedude on 2005-10-18
Just wanted to say thanks again for the replies- the reformat and installation went without a hitch. I am very happy with my new installation of Ubuntu Breezy. :D

---

### Post by matthew on 2005-10-18
Cool. I'm very glad to hear it went well for you.

---

