---
title: "Error 16, (and 17, and 15, and 18)"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by 2benglish on 2008-03-23
I have been using Ubuntu for a year or so. In October? I did a clean install of 7.10

About two weeks ago, after having the computer witched on for about a week, I turned it off. When trying to restart in the morning it went through GRUB and soon stopped with Error 16 Inconsistent filesystem.

There are two hard disks in the machine. XP is on the first and Ubuntu is on the second. HD1 is formatted to htfs, HD2 is ext3. There is a second partition on HD2.

I have tried booting the different partitions, only XP works. Recovery mode gives me the same Error 16.

I used the live CD and logged in as myself with the help of dstew [URL="http://ubuntuforums.org/showthread.php?t=637126&highlight=grub+error"]http://ubuntuforums.
org/showthread.php?t=637126&highlight=grub+error[/URL]. This enabled me to back up my data.

I have since tried fixing things with Super Grub, but with no joy (as I don't really know what I'm doing).

I have also tried testdisk, nut had the same result. 

I am now prepared to wipe HD2 and load it again, but this seems like I am backing away from the problem and not solving it.

What confuses me is that I had been using GRUB and 7.10 for months with no problem. Would this issue have arisen from an upgrade that occured in that final week?

If I go the route of reinstall, how can I make things easy for myself in getting the software that I have been using until now? I know how to save my passwords and bookmarks in firefox. Is there an easy way to get the system back to where it is now?

Thanks in advance for any help.

---

### Post by housam on 2008-03-23
Sometimes upgrading causes this problem. try to [[COLOR="Red"]_restore grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
and to backup your system and data use [[COLOR="Red"]_this guide_[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by hyperair on 2008-03-23
Well if it complains of an inconsistent file system, why don't you try fscking it? You know...
```
sudo fsck -r /dev/sda1
``` or something?

---

