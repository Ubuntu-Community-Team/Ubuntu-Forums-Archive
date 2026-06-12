---
title: "[SOLVED] Hardware RAID 0 Install"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Siyfion on 2008-01-31
I currently have an Adaptec 1430SA SATA II RAID controller card, with 4 disks paired off into 2 separate RAID 0 arrays. I have installed Vista on, lets call it the "master" RAID 0 disk, and purposely left some room to install Ubuntu on there as well.

When I start the LiveCD it sees the drives as 4 separate drives, although this is NOT a "fakeRaid". I am a little bit stumped now as to how to actually install Ubuntu onto the disk, even more so, without destorying my Windows install/partition.

---

### Post by Siyfion on 2008-01-31
Shameless *bump* as this is stopping me from joining the Ubuntu "clan" lol

---

### Post by Siyfion on 2008-01-31
After doing some digging, on here: [http://www.adaptec.com/en-US/products/sata_tech/entry/AAR-1430SA/](http://www.adaptec.com/en-US/products/sata_tech/entry/AAR-1430SA/)

It looks at though it utilizes HostRAID technology.. Isn't that supported by dmraid?

---

### Post by Siyfion on 2008-02-01
Anyone!?

Please, please, please help! :(

---

### Post by Siyfion on 2008-02-01
Ok, think im going to give up now. :(

---

### Post by Siyfion on 2008-02-03
Ok, after doing it a different way... Dmraid, then Admin->Partition Setup (or similar) it shows me each drive individiually, but ALSO shows me the two raid 0 drives. I tried to create an ext3 and a swap partition though and it failed and then crashed. :S Idea's?

---

### Post by polmir on 2008-02-03
Read all posts from this tread
[http://ubuntuforums.org/showthread.php?t=666968]("http://ubuntuforums.org/showthread.php?t=666968")

---

### Post by Siyfion on 2008-02-03
Ok so after following that guide, I have done this:

```

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "ddf1_Master Drive" already active
RAID set "ddf1_Slave Drive" already active

```

Although now I am unsure as to how to partition the master drive.. I can't use /dev/sda or /dev/sdb as that would only partition the single drive. So what do I use to partition the Master drive with a ext3 and swap partition?

---

### Post by Siyfion on 2008-02-03
The plot thickens, after trying to fdisk the drives they wouldn't work. Turns out that I think the problem was because the drive labels had a " " character in them, so I re-made the RAID 0 drives, installed dmraid, and now even the installer's manual partition shows the drives, allows me to set the partitions up, but now fails on the screen attached.

EDIT: Attached screenshot of how the drives were partitioned in the installer.

---

### Post by Siyfion on 2008-02-03
Somone must know what this error message means? What is the installer for Ubuntu called, maybe i'd be best off quizing the forums of that?

---

### Post by polmir on 2008-02-03
You read sites from this link:
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")
[http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0")

---

### Post by Siyfion on 2008-02-04
> **polmir said:**
> You read sites from this link:
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")
[http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0")

I did, and none of them had anything about the error message I am now getting.. (Not that I could find anyways, but some of the pages are quite large.)

And since I can't get past partitioning the drive.. Im a bit stuck. (Well... Mounting the swap partition anyways.)

---

### Post by Siyfion on 2008-02-04
Ok, solved it finally. After trying about 7 different ways, this one: 

[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid](http://ubuntuforums.org/showthread.php?t=630644&highlight=raid)

seemed to provide the best solution. I have it installed and booting. :)

---

