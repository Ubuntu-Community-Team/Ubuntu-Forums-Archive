---
title: "Best partition for dual Win 7 &amp; Ubuntu"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by joecape on 2010-01-14
I just got Windows 7 installed on an 80Gb NTFS partition of my 1/2 Terabyte hard disk, thanks to help on this forum, and have Ubuntu running directly off the CD. Ideally I'd like media files to be accessible to both of them (maybe 250Gb) after I install Ubuntu. Firstly, what is the best way to format the partition for Ubuntu, and should I just make one more partition, or several? I remember doing this previously (installing ubuntu on an EeePC), I made three partitions: one for the Ubuntu OS, another tiny one, the purpose of which eluded me, and a third for media. This in fact came in handy when the OS crashed and I could replace just that without destroying anything on the third partition. 

As the Windows NTFS partition does seem to be accessible from the Ubuntu set-up, should I consider expanding that to, say, 330Gb so as to keep films, music and so on that I want to access from either win 7 or Ubuntu on that drive?

One more thing: it mentions on the Ubuntu download, performing an MD5 hash on the iso you download to check there are no errors. Is this necessary?

---

### Post by darkod on 2010-01-14
Yes, Ubuntu reads and writes ntfs fine but just as a precaution I wouldn't access the windows system partition too often from it. It's a good option to have another ntfs partition and put everything you want to share on that one. The size will depend on how much data you share.
Depending if you have a recovery partition on the computer, that's already 3 partitions, out of 4 allowed.
You will set up ubuntu in an extended partition (standard way), and you can have the root, swap and media partitions if you want. Just be advised that the partition with media files, if it's ext4, windows won't be able to access it.
There are some tools for windows to see linux partitions, but the difference is: the tool to read ntfs from linux is embedded in the OS and is tested and working. The tool to read linux from windows is probably from enthusiasts, not included in windows and not supported by them. Do you wanna go that way?

You might consider dropping the plan for separate media partition for ubuntu. Just have the standard root and swap, and all your media files you want shared will be on the ntfs partition created for that purpose. That way it's also safe from any OS failure because the shared files are neither on windows or ubuntu system partitions.

---

### Post by joecape on 2010-01-14
Thanks, I'll try that. What is the swap partition for?

---

### Post by darkod on 2010-01-14
It's a space dedicated on the hdd for when your ram gets filled (if it does), it uses swap next. Similar to windows which has swap file on C:, in linux you have a partition. You could also not use a partition and use a swap file in linux too, but a partition is the standard way.

---

