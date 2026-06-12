---
title: "best partition type and filesystem for file sharing"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by greg28 on 2014-05-22
Hi. I have a shared folder called \office on my Ubuntu 12.04, which is a folder on the root of filesystem. I'd like to have it on a separate partition for two reasons. First if needs be I can reinstall Ubuntu if it gets really stuffed without losing this data in \office. Second I want to use DRBD to mirror the \office data to another server. So the desired situtation will be a new partition called office which is separate from all the linux/ubuntu stuff. What type of partition should I create and what filesystem should I create on it ? It will hold documents and similar.

---

### Post by tgalati4 on 2014-05-22
What other computers are on your network?  If you have any Windows computers, you might want FAT32 or NTFS, otherwise ext4 is fine for Linux, Mac, and Android/iPads and phones.  I'm not familiar with drbd, can you provide a link?

I found this:  [https://help.ubuntu.com/community/HighlyAvailableNFS](https://help.ubuntu.com/community/HighlyAvailableNFS)

Perhaps overkill for home use.

---

### Post by greg28 on 2014-05-22
[www.drbd.org](www.drbd.org). Actually it will be used in my office of 8 people as part of a failover/clustering with two ubuntu servers used only as fileservers. We have a bunch of windows computers too. I'm a recent convert from Windows Server 2003 which was the simple choice 5 years ago. I'm now older and wiser.

---

### Post by mastablasta on 2014-05-23
DRBD seems to work on linux.

why does file system matter for data? you can have extfs and them miror the data on extfs on ntfs and vice versa.

---

