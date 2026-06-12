---
title: "Installation Headache"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by SummermoonUK on 2008-05-24
Well if the solution to this has been posted elsewhere I can't find it so here I go:

Tried Ubuntu 8.0x for a couple of weeks now, liked it, went to install permanently, became a little confused about the guided install because it would not see the HD that I wanted Ubuntu on. So went to Manual and found it there, filled everything in and off the installation went.

The install finished and then there came the error message Gnome not found on HD0! I have no HD0 only SDA, SDB, SDC, and SDD. SDA & SDB are Raid0 where my WinXP Install is.

So even if I disconnect the RAID 0 drives The Pc still won't boot to Ubuntu unless I have the CD in and the Bios is set back to boot from CDROM.

So my PC Setup is this:

4 Sata Drives, each 500Gb. The first 2 are setup as RAID0 with WinXP Home SP3. 

The third drive is for media files etc., 

The fourth drive is split in half with the first partition being for Games Saves etc., The second I partitioned for Ubuntu.

The second partition was set first by PartitionMagic.

IVe never seen a "GRUB" menu or found a way to find this.

I would also like to duel boot with WinXP as default and Ubuntu 2nd. (Only because most of the games I play won't work in Ubuntu) but I can't find instructions on how to dual boot with a RAID0 setup.

I have no IDE drives either. The DVD drive is SATA.

So I would like to:

1 Install Ubuntu
2 Duel Boot with Windows 1st, Ubuntu Second
3 One day ditch Windows.

Setting this up is the first problem I've had but then first dates don't always go as planned.

Hope someone can help
D

---

### Post by Pumalite on 2008-05-24
This will get you started:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

---

