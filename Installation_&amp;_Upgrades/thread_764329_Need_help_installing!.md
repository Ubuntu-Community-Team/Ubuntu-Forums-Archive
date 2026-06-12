---
title: "Need help installing!"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by new_at_linux on 2008-04-23
Hello,
After much thought and consideration I have decided to install Ubuntu (7.1) on my computer while keeping my Windows XP. At step 4/7 I was asked to make a disk partition. I was only given two options:

Guided - Use entire disk
Manual

So naturally I clicked manual, since "use entire disk" probably involves wiping my disk of my XP, even though I have no idea what to do. This is what came up:

DEVICE--------TYPE-----MOUNT POINT------SIZE---------USED
/dev/sda
- /dev/sda1----fat16----/media/sda1------57 MB--------33 MB
- /dev/sda2----ntfs-----/media/sda2------156198 MB----unknown
- /dev/sda3----fat32----/media/sda3------3742 MB------3400 MB

How am I supposed to know which one has Windows XP on it, and which one is free space? What is "Type"? Which one should I click??

Thank you for any help you can give .

---

### Post by teryowen on 2008-04-23
well the type will tell you the partition type so in the case of windows XP it uses ntfs, which on your hard drive is the 2nd partition. Now Im not sure how you plan on going about this. Basically if it were me I would resize the 2nd partition to give room for the Ubuntu installation.

Once you have about 10GB of free space or more make one partition type ext3 with mount point "/" (without the quotes) and about 1GB for swap space. that should be it.

EDIT: make sure you shut down your windows properly without any errors. as well its always a good idea to back up.

---

### Post by tyblu on 2008-04-23
i recommend referring to one of the excellent guides:

[http://www.google.ca/search?hl=en&q=dual+boot+ubuntu+7.10+windows+xp](http://www.google.ca/search?hl=en&q=dual+boot+ubuntu+7.10+windows+xp)

--> [https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

---

### Post by new_at_linux on 2008-04-23
Thank you for your help so far!

So, I resized my ntfs partition and now I have 10 GB of free space.  When I try to make a new partition, regardless of whether it's swap or ext3, the leftover space is no longer "free space" but is now "unusable", and I am unable to make the second partition.  I can have a swap partition, or a ext3 partition, but not both at once.  Am I not allowed to have more than a certain number of partitions or something?  What can I do?

Thank you.

EDIT: After some searching I found there is a 4 primary-partition limit.  What's the difference between a primary partition and a logical partition?

---

### Post by teryowen on 2008-04-23
with the free space (of 10GB or however many) make it into an extended partition and withing that have the 2 logigcal partitions one being ext3 and the other swap. should work now. Use gparted it would probably be easier instead of doing it through the installer.

---

### Post by new_at_linux on 2008-04-23
> **teryowen said:**
> with the free space (of 10GB or however many) make it into an extended partition and withing that have the 2 logigcal partitions one being ext3 and the other swap. should work now. Use gparted it would probably be easier instead of doing it through the installer.

One more problem apparently.  I did all this and got the following error:

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 28034 (55960 expected); size of FATs is 110 sectors (219 expected)."

Should I ignore this?  Will Windows still work?

EDIT: I ignored it and my computer now works perfectly.  Problem solved!

---

