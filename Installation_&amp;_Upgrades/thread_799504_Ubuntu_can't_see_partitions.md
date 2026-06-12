---
title: "Ubuntu can't see partitions"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by berdwin on 2008-05-19
hi :)
I couldn't find an answer so I'm posting.
I've used vista to partition free space to install ubuntu to.. but when I go to install ubuntu it cannot see the partitions set up and viewable when in windows.
here's a screen of what windows see and what ubuntu install sees:
[IMG]http://i32.tinypic.com/15gf7u0.jpg[/IMG]
also, the two 500 gb drives are raid together so in windows it's one big partition.
why doesn't ubuntu see my raid?
thanks :D

---

### Post by housam on 2008-05-19
Use the Gparted tool ( in ubuntu live cd ) for partitioning your drive , it is more suitable for ubuntu than vista partitioner.
before partitioning backup your data and defrage your HDD 2-3 times.
create three partitions for ubuntu : 
10 Gb or more for ubuntu root ext3 format with the sign ( / )
2  GB for the swap
10 GB or more for the /home ext3 format.
during installation when it comes to partitioning choose the manual way and assign the partitions you made.

---

### Post by berdwin on 2008-05-19
I've also tried viewing partitions using the tool in livecd.  It shows the same thing you see when installing via the alt disc.
If I install ubuntu with it's own partitions on top of what it sees (two 500gb drives with no partitions) then won't vista and it's partitions get messed up?
I'm trying to dual boot vista and ubuntu.

---

### Post by dstew on 2008-05-19
The Ubuntu installer will not respect your RAID, so if you try to partition your disks, your RAID and Vista installation will be destroyed.

If you want to install Ubuntu onto the RAID, and dual-boot with Vista, there is a way to do it. You need to use the Live CD, and install the program **dmraid** onto the Live CD system using the Synaptic package manager. Using dmraid, you can get Ubuntu to recognize the RAID. However, the installer cannot use dmraid, so you have to install Ubuntu "by hand". It is not extremely difficult, but I would not recommend it for a novice. The instructions are here in the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

All this assumes your RAID is a FakeRaid (hardware RAID with software assistance). If your RAID is pure software, you might be able to install to it using the Alternate Install CD.

---

