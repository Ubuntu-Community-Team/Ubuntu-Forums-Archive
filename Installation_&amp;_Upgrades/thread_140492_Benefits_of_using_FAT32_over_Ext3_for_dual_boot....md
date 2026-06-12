---
title: "Benefits of using FAT32 over Ext3 for dual boot..."
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by Arkolm on 2006-03-06
If I'm duel booting with xp and ubuntu, most places say to go FAT32, but I don't really understand the benefits. Furthermore I can't seem to get ubuntu to install on FAT32, but it installs fine on Ext3. As a linux beginner, I was hoping that I could get some explainations as to why to use which, and if I should keep trying to get it to setup on FAT32.

Thanks.

---

### Post by Stealth on 2006-03-06
What they probably mean is to have an extra partition in FAT32. FAT32 is a format that both Ubuntu and Windows can read and write. So if you put your music there, for instance, you can listen to them in Windows, go into Ubuntu and do the same, delete some songs, edit the tags on some others, and get back in Windows and see the changes fine without any data corruption (like what could happen if you tried writing to NTFS).

---

### Post by Adrian on 2006-03-06
You are not supposed to install Ubuntu on a FAT32 partition. The idea is to use a specific partition ext3 partition for the Ubuntu system, and an additional FAT32 partition for the data that you want to share between Ubuntu and Windows.

In the past, this was the only reliable way to share data between the two operating systems. However, now there is very good software for Windows that makes it possible to access ext2/ext3 partitions. This is my favourite:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
It is working for me and many others without problems.

If you use the FAT32 method, you don't need a Windows driver and it has been tested a million times. However, it's recommended to NOT use FAT partitions larger than 32GB. In fact, Windows XP will refuse to format such large partitions as FAT.

The ext2/3 method is not as well tested, and it requires you to install a third-party driver in Windows. Also, sharing your Ubuntu system partition (and not just data) can give you problems since access control isn't maintained.

Me? I share my ext3 data partition with Windows, but not the system partition.

---

