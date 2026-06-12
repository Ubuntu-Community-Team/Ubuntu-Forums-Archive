---
title: "Switching from XP to Ubuntu, Odd Twist.."
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by ACMarina on 2008-04-18
Okay, I've been working on a solution for a friend and came up with a thought, but I'm not exactly sure if it will work or not..

User currently has Windows XP running on a set of SATA drives in RAID 1.  I installed Virtualbox and Ubuntu and configured it for him, and he says it's working perfectly for what he needs.

My mind says to unhook one of the SATA drives, wipe the installed drive clean and install Ubuntu, configure it for his taste, then hook up the other drive, copy over what he needs, then wipe that other drive and rebuild the RAID 1.  Sound good??

Okay, here's the kicker.  User has a USB D-link Skype/phone adapter that only seems to run on Windows.  I've not tried to hook it up without that yet, but most of the D-link stuff that I've tried to use didn't go so well.  Could I run it in wine, do you think??  Failing that, could I install virtualbox in Ubuntu, then install windows as a virtual machine, and install the device in virtual windows?  I've not used virtualbox enough to see if it will work with different USB devices..

Smile upon me, Ubuntu-gurus!!

---

### Post by dstew on 2008-04-18
> My mind says to unhook one of the SATA drives, wipe the installed drive clean and install Ubuntu, configure it for his taste, then hook up the other drive, copy over what he needs, then wipe that other drive and rebuild the RAID 1. Sound good??I am assuming this is a FakeRaid (hardware-assisted softRAID). You might be able to do it, but it will depend on the ability of the new Ubuntu to read files on the disk that was pulled out of the RAID. Since it is RAID-1 (mirrored) you would think it would be able to do that. However, the partition table on the disk might be non-standard, and the drive might not be mountable by Ubuntu in that state. If you really need files that are on the RAID, it might be better to back them up to another disk, and get them back from there.

You can install Ubuntu to a functioning FakeRaid. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). It is not very easy though, you have to build the Ubuntu system by hand. You can also install Ubuntu on a regular partition, if you can create one, and get it to recognize and read data from the RAID. Then maybe you could wipe out XP and rebuild the RAID.

About the Skype phone adapter, you will have to look on the forums for that, I have no experience. However, getting "windows only" hardware to work on a virtualized windows would be tough, I think. I couldn't find any success stories in my brief survey.

---

### Post by ACMarina on 2008-04-18
Thanks dstew!  

What about this idea - take out secondary drive currently in RAID 1, stick it in a SATA drive enclosure.. install Ubuntu to single drive, transfer everything essential from enclosure - then wipe old SATA drive and use it to back up primary HDD on a regular basis.. would that be a better idea??

The skype adapter is a Dlink DPH-50U, for anybody else who'd stumble this way..

---

### Post by ACMarina on 2008-04-18
Well, it looks like the SATA drive in backup should do just fine for that purpose - I just have to resolve this skype adapter thing and I'm golden..

---

### Post by ACMarina on 2008-04-19
Looks like I might be playing guinea pig on this one myself.. I guess I'll try Wine first, then a virtualbox install of XP..

---

