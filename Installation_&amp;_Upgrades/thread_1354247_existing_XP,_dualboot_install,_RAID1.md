---
title: "existing XP, dualboot install, RAID1"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by dez93_2000 on 2009-12-13
Hi all. Because I enjoy complication and reading hundreds of pages of text online, I've decided to try to install ubuntu9.10 as a secondary booting partition on my drive, which is a two-identical-mirrored-drives RAID1 SATA setup.

Installing ubuntu 9.10 on RAID1: easyish, use the alternative CD and fakeraid: [https://help.ubuntu.com/community/FakeRaidHowto#preview](https://help.ubuntu.com/community/FakeRaidHowto#preview)
And installing ubuntu as a secondary boot on an existing xp install: [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
But both at once?

Problem I had when trying link 1 was that the partition manager thought my windows partition (which takes up all the drive) was using all of it. I now suspect that it just means that the partition takes up all the space, irrespective of whether or not it's full. Either way, it didn't seem to want me to be able to resize it.

Can I add the necessary partitions using the guided part of the live CD or gparted CD then go back into fakeraid and select the partition I created?
-Despite reading all of this [http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649) and other threads, I'm still unsure what partitions I have to create manually. Ideally I'd like to leave the xp install as it is, with media on there...which linux could access...?...but I don't know whether I'll have to manually create the linux partitions or whether I can have guided partitioning do it for me. I know I need a 2.5gb swap, I still don't know what the /home is for or whether I need it,  or whether I can let linux use the windows ntfs as file storage.
You know when you know a little and you have a vague idea of what the deal is, then you read loads and instead of making you more knowledgeable it just makes you confused? That's me now.

Any form of mentally decluttering pointers would be greatly appreciated, ideally along the lines of (e.g.)
1. checkdsk /r & defrag twice
2. use liveCD to guided partition in the following configuration (?)
3. reboot to alternative ubuntu cd and install, following fakeraid instructions
[-o<
Thanks in advance. I know that there's loads of info out there, but it all seems to be for one or other installation type, not both.

---

### Post by darkod on 2009-12-13
Because the full capacity of your drives is assigned to your RAID1 array, I doubt you can shrink it the way you shrink ordinary single hdd to make unallocated space for ubuntu.

---

### Post by phillw on 2009-12-13
I'm not 'into' RAID, but from the threads posted - there are some 'issues' with Grub2 and RAID.

Acouple that may be of help...

[http://ubuntuforums.org/showthread.php?p=8411264](http://ubuntuforums.org/showthread.php?p=8411264)

[http://ubuntuforums.org/showthread.php?p=8486640](http://ubuntuforums.org/showthread.php?p=8486640)

The issue of RAID and Grub2 does seem to be hot topic, at the moment.

Hope the above helps you.

Regards,

Phill.

---

### Post by dez93_2000 on 2009-12-20
Thanks guys. Thinking the way forward might be to ditch my raid setup (since i backup everything to an external HDD so double redundancy might be a bit, um, redundant). That would leave me with one completely blank drive; I could have XP booting from drive1, make the partitions for linux on drive2, then migrate files from the windows partition to the shared documents partition in my own sweet time. This would also give me 500 extra gb, which would be nice.

---

### Post by gilson585 on 2009-12-20
check out my post if you still want instructions for a fakeraid install using 9.10 [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

