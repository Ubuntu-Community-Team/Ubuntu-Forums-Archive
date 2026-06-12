---
title: "Ubuntu and other OS"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by aliboy on 2011-05-23
If I copied one partition from different hard disk with working ubuntu and another partition with working windows OS into my two partitioned HD, is it posssible to make the two system working?:confused:

---

### Post by Hedgehog1 on 2011-05-23
Good New/Bad News:

Ubuntu will move from one PC to another without much fuss; you may have to change the video driver.

Windows is another story.  Windows uses drivers for the chip-sets on the mother board, and if you put that partition on a system that has a different chip set, Windows will not boot (and it give some ugly errors in the process).

Hope this Helps.

***The Hedge***

:KS

---

### Post by aliboy on 2011-05-24
ok, 
what if thesituation is like this:

I have 1 PC (PC1) and 3 HD (HD1=20GB, HD2=20GB, HD3=40GB)

Using PC1 I install windows OS in HD1 (during the installation, HD2 and HD3 is disconnected)

Then after a while I install ubuntu in HD2 (during the installation, HD1 and HD3 is disconnected)

what if I partition HD3 into two, copy the the whole HD1 in the first partition and HD2 in the second partition. Is there any way that PC1 with HD3 can be fix to become dual boot?

---

### Post by dFlyer on 2011-05-24
If I understand you correctly, you have 3 hard drives.

Drive 1: Windows
Drive 2: Linux
Drive 3: No OS

You want to partition drive 3 so that you can clone windows to 1 partition and linux to another, so you can dual boot.

Why not leave Drive 3 empty for future use and dual boot just drive 1 and 2.

Grub can be setup to do it either way, but it would be a waste of time and space to add a dual boot to drive 3, when drives 1 and 2 are setup and ready.

---

### Post by aliboy on 2011-05-24
If I have to put HD1 to PC2 and HD2 to PC3. I really need to copy HD1(20GB/ubuntu) and HD2(20GB/windows) into HD3(40GB/2partition)

So if copying is done, is there a way to make HD3 working dual boot?

---

### Post by aliboy on 2011-05-24
anyone?

---

### Post by Hedgehog1 on 2011-05-24
In theory it can be done, but it is a tricky business.

OK - I think I have a way you can do this:

Use the **dd** command and copy the entire 20 gig windows drive to the 40 gig hard hard.

Remove the 20 gig windows drive, and boot from the 40 gig windows drive.

Now you can install Ubuntu from scratch to fill the rest of the 40 gig drive.

If you don't want to reinstall Ubuntu, have the 40 gig drive and the Ubuntu 20 gig drive in the PC. You can use Clonezilla to copy the Ubuntu partitions (there are 2 or 3 of them) from the 20 gig drive to the open space on the 40 gig drive.

Remove the 20 gig Ubuntu drive, and then install grub from the Ubuntu LiveCD to turn the 40 gig drive into a dual boot.

Now, in all honesty, copying windows using dd and then installing Ubuntu on the free space left on the 40 gig drive is the simplest.

***The Hedge***

:KS

---

