---
title: "Incorrect partitions size (trying to install on a win8 system)"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by roee88 on 2012-10-25
Hi,

I'm trying to dual boot windows 8 and ubuntu.

System has only one 500GB HD.

Initially windows 7 and OSX were installed on disk. 160GB used for OSX and the rest for Windows 7.

I then decided to replace both with windows 8 (from dreamspark) and give it the entire HD space. So far all good.

Trying to install ubuntu alongside windows 8:
* The installation partitioning tool showed partitions similar to the old set up (160GB as /dev/sda2 unknown and the rest as /dev/sda3 ntfs). Installation failed in the resize partition step.
* Went back to windows 8. Disabled hibernation used windows' disk management to create a 50GB of free space (to be used by ubuntu)
* Ubuntu partitioning tool still shows the older partitions and installation still fails. Using the "Try ubuntu" options I can see the file explorer itself does see the correct disk size.
[IMG]http://i48.tinypic.com/2q9zxvc.png[/IMG]
[IMG]http://i46.tinypic.com/25as1aw.png[/IMG]

Any help would be appreciated ;)

---

### Post by darkod on 2012-10-25
Doesn't OSX work only on gpt tables? If you had gpt table on the disk, and then during win8 install you switched it to msdos table, be careful seems windows doesn't seem to delete the backup gpt table and leaves a big mess on disks that were once gpt.

Linux can detect this backup table and is confused whether the disk is msdos or gpt and which table to follow. This might explain seeing "old" partitions. However, I can't say it for sure.

One tool to get rid of this backup gpt table (if this is the case with you), is fixparts run from live mode:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Just run it and it will offer to remove it for you.

if you are using UEFI boot also be careful, since you need to boot the ubuntu cd in uefi mode to install uefi dual boot.

---

### Post by roee88 on 2012-10-25
It worked. Thank you darkod.

---

