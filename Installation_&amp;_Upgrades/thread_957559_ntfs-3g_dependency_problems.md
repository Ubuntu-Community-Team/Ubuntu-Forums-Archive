---
title: "ntfs-3g: dependency problems"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by chinnusan on 2008-10-24
i.. am santosh from bengaluru..
i have installed dapper drake on windows xp sp2.. and i am unable to write in the ntfs windows from ubuntu dapper drake so i changed lines in the fstab as

/dev/hda2       /media/hda2     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda5       /media/hda5     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda6       /media/hda6     ntfs-3g defaults,locale=en_US.utf8 0 0

but it is not working.. before by default it was atleast able to read the ntfs windows partitions but now am unable to open also.. please help me out immediately.. am using pentium celeron 766mhz processor and total 384mb sd ram and 80 gb segate harddisk..
and am getting error for ntfs-3g also as::

[SIZE="5"][SIZE="6"]E: fuse-utils: subprocess post-installation script returned error exit status 1
E: ntfs-3g: dependency problems - leaving unconfigured
E: ntfs-config: dependency problems - leaving unconfigured[/SIZE][/SIZE]

---

### Post by Partyboi2 on 2008-10-24
Dapper drake is a older release of ubuntu, I would suggest upgrading to hardy which is the nest long term release version. You can upgrade from dapper to hardy by following [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS")

---

### Post by mikewhatever on 2008-10-24
Where did you get an ntfs-3g package for Dapper and how did you install it? A quick look through the repositories revealed that ntfs-3g in not included. It's possible that the problem lies in the wrong package or incorrect installation.

PS: Three post on the same issue are probably not needed.
[http://ubuntuforums.org/showthread.php?t=957531](http://ubuntuforums.org/showthread.php?t=957531)
[http://ubuntuforums.org/showthread.php?t=957523](http://ubuntuforums.org/showthread.php?t=957523)

---

