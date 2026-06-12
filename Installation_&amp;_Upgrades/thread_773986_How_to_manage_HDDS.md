---
title: "How to manage HDDS"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-04-29
I installed 8.04 yesterday. Clean install, single boot. My last setup was a dual boot Win XP and Ubuntu. I meant to install Ubuntu on all three HDDs. But I'm suspecting that I've only installed Ubuntu on one of them. I have to mount two of them and they have the same name as i gave them in XP. So they're not partitioned during the install. And i have a mystical forth one (see attachment). Not sure what that is. I would really like all discs to be Ubuntu partitions.

And if someone have advice on why or why not i should make more partitions they are welcome as well :)

---

### Post by mikewhatever on 2008-04-29
Can you clarify why you want three installations of Ubuntu on one computer?

---

### Post by peakshysteria on 2008-04-29
My bad. I explained it badly. During the install of Hardy i meant to wipe all three HDDs. I was pretty sure the install then made three partitions (at least this i was told beforehand). But now it looks like Ubuntu resides only on one HDD and the two others are the old XP partitions. I have no XP OS anymore. Thats for sure. So i would like to the two remaining HDDs to be linux partitions as well. No i have to mount the two HDDs each time I'm in need of files there. I would like to move freely between the HDDs. One of them are also a Fat32 partition. I'm kinda new to this, but Isn't there some advantages in using ext3?

And what on earth is the fourth device? It looks to be a copy of the main partition/dev/sda1 which is ext3.

So no, I'm not looking for three separate Ubuntu installs. It just doesn't seem right that I have two windows partitions on a linux system.

---

### Post by mikewhatever on 2008-04-29
Automatic Ubuntu installation creates two partitions, one for the system and the other for swapping. These two are created in the designated free space, and the rest of the space is unaffected by the installer, thus letting you preserve data. You may want to review one of the guides next time before installing.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Here is a guide for mounting other partitions so that they are accessible after bootup: [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)

You can't convert ntfs or fat32 partitions to ext3. If you don't need the data on those partitions, reformat them with GParted Live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by peakshysteria on 2008-04-30
Thanks man. I'll look into those links :)

---

