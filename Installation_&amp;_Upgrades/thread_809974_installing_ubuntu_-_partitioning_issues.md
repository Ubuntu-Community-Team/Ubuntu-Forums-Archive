---
title: "installing ubuntu - partitioning issues"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by SchitzoJoe on 2008-05-27
Basically, I'm switching to Ubuntu from Windows. Downloaded the 8.04 iso from the Linux homepage, burned it, stuck it in, everything was going fine, until I got the partitioner screen.

Nothing was there.

I couldn't select any of the options (they were greyed out), and there were no apparent partitions.

Anyone know how to fix this?

Screenshot attached.

[B][COLOR="Red"]SOLVED.

HOW I SOLVED THIS PROBLEM: Change the jumper settings on your HDD to "Cable Select." The jumper settings are changed by moving the jumper on your HDD on the pins to a specific place, often specified on the outside of your HDD or in the manual. Thanks for everyone's help.[/COLOR][/B]

---

### Post by louieb on 2008-05-27
Usually when that happens its because of a non-standard partition table.

Please post your partition table. To do that open Applications>Accessories>terminal and run

```
sudo fdisk -l
```(lowercase -L at the end) 
Depending on what it shows will have some suggestions on what to do next.

---

### Post by SchitzoJoe on 2008-05-28
still nothing.

nothing shows up.

ss attached.

EDIT: I tried DBANing it last night, it didn't change anything whatsoever. Should I just download/burn the non-live CD and try that one out? Or would I have the same problem?

---

### Post by Kevbert on 2008-05-28
Have you performed a checksum on the iso file that you downloaded ?  You can check this with: [https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24)
Also have you burnt the CD at the slowest speed ?  Errors do occur, so you'll need to check the disk before installing.  Its one of the menu items when you boot to CD.

---

### Post by SchitzoJoe on 2008-05-28
> **Kevbert said:**
> Have you performed a checksum on the iso file that you downloaded ?  You can check this with: [https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24)
Also have you burnt the CD at the slowest speed ?  Errors do occur, so you'll need to check the disk before installing.  Its one of the menu items when you boot to CD.

I checked with the option at the boot menu, and it said there were no errors. Also used winMD5sum, both hashes came up the same.

---

### Post by hts3813 on 2008-05-28
sudo fdisk - did not work with me when I tried to install on 80g disk with 3 partitions. Yet instalation went smoothly when using my older 40g drive with only two partitions. I still think the catch is with the number of partitions. I am new to linux...just sugesting.

---

### Post by louieb on 2008-05-28
> **SchitzoJoe said:**
> still nothing....nothing shows up...

Wow! haven't seen fdisk do that before.  The Ubuntu live CD has pretty good hardware detection.  Even if the drive had no partitions it would still list the drive or a dozen or more - the fdisk command reports what it finds.  Have you check the connections to the drive? Have to tried another Linux live CD. 

Its about a 50 MB download I would try   [DSL Linux]("http://damnsmalllinux.org/") its hardware detection is based on  [Knoppix Linux]("http://www.knoppix.net/"). Both are very good at detecting hardware.   But what puzzles me is its your hard drive any Linux distro   should pick it up. 

What kind of pc is it?  What OS is currently on it?

 **hts3813 **On a side note as long as the partition table is  a standard msdos table then it should list the partitions. If its not fdisk should still report the drive and give a waring that the partition table is messed up.

---

### Post by SchitzoJoe on 2008-05-29
there is absolutely no OS running on it right now, just running a live session.

running an HP Pavilion with an AMD Athlon 2800+ XP processor ~2.1ghz, nVidia Geforce 6600GT card, 1 gig of ram, 110gb hard drive. some form of hp pavilion, can't remember the model number as of now though as i'm not on my home computer.

i'm going to try the non-live cd tomorrow night whenever i get home, i'll report back with progress.

p.s.: to get rid of my windows partition, i popped in my windows cd, deleted the windows partition, so i have like a 112gb unpartitioned space. is this a problem?

---

### Post by louieb on 2008-05-29
HP pavilion is a pretty mainstream PC. I'm almost out of things to check. Its odd that your Windows CD can see the drive and Ubuntu can't. 
One more thing to look at. Go into the BIOS setup.   Look for the hard drive description. ** Type** should be set **Auto **and **mode** set to [B]LBA.  

[/B]Let us know how the text based installer worked out. Good Luck.

---

### Post by SchitzoJoe on 2008-05-29
So, I tried the text-based install CD today.

Didn't work. Still had a blank list of stuff.

Also opened up Gparted a few minutes ago, and it showed no devices were found.

Also, in my BIOS setup I don't have those options. -_-

This is turning out to be a very bad day.

---

### Post by wpshooter on 2008-05-29
> **SchitzoJoe said:**
> there is absolutely no OS running on it right now, just running a live session.

running an HP Pavilion with an AMD Athlon 2800+ XP processor ~2.1ghz, nVidia Geforce 6600GT card, 1 gig of ram, 110gb hard drive. some form of hp pavilion, can't remember the model number as of now though as i'm not on my home computer.

i'm going to try the non-live cd tomorrow night whenever i get home, i'll report back with progress.

p.s.: to get rid of my windows partition, i popped in my windows cd, deleted the windows partition, so i have like a 112gb unpartitioned space. is this a problem?

Get [www.killdisk.com](www.killdisk.com) and WIPE that drive completely clean and I bet the Ubuntu O/S will install perfectly.

I suspect that somehow your DBAN program is not working or actually running to completion.  I have seen that problem with DBAN before.  Killdisk is simpler but all you need to WIPE the drive of all contents.

Good luck.

P. S. - I just noticed one of your last posts.  Make sure that you can see the drive in the BIOS.  If you can NOT let us know and we will discuss further.

---

### Post by SchitzoJoe on 2008-05-29
When looking at the BIOS again, I was able to find the drive. Settings were on what you all had suggested.

Going to try killdisk in a bit.

---

### Post by SchitzoJoe on 2008-05-29
Update:

Killdisk did not work. But I discovered something that could potentially help alot.

The "Unpartitioned" space of the disk is only 10mb. The other 111.8gb is still partitioned and labeled in the Killdisk Partition Manager thing as "Unknown Disk" or "Unknown Primary" or something like that, but there's nothing on it, and I don't know how to get rid of that partition back to an unpartitioned space. That partition is also the primary partition, and it's also called, in another menu, the "Logical C:" drive. The reason it's doing this, I believe, is because I unpartitioned it with Windows instead of Linux. Now it's formatted in NTFS or something, so Linux can't read it.

That's just my theory, I'm probably completely wrong.

But now that we've discovered this, any advice on where to go from here?

---

### Post by wpshooter on 2008-05-30
> **SchitzoJoe said:**
> Update:

Killdisk did not work. But I discovered something that could potentially help alot.

The "Unpartitioned" space of the disk is only 10mb. The other 111.8gb is still partitioned and labeled in the Killdisk Partition Manager thing as "Unknown Disk" or "Unknown Primary" or something like that, but there's nothing on it, and I don't know how to get rid of that partition back to an unpartitioned space. That partition is also the primary partition, and it's also called, in another menu, the "Logical C:" drive. The reason it's doing this, I believe, is because I unpartitioned it with Windows instead of Linux. Now it's formatted in NTFS or something, so Linux can't read it.

That's just my theory, I'm probably completely wrong.

But now that we've discovered this, any advice on where to go from here?

Point killdisk to the entire for the drive itself (not any one of the partitions) and then WIPE the ENTIRE drive.  ALL partitions now gone.

Good luck.

---

### Post by louieb on 2008-05-30
> **SchitzoJoe said:**
> ...But now that we've discovered this, any advice on where to go from here?

Sure sounds like a hardware problem.  Open up the case.  Check the connector. Try another drive just to see if it get detected by GParted.  See what kind of drive HP put in it. Go to the manufactures web site and get their diagnostic utility.

---

### Post by SchitzoJoe on 2008-05-30
> **wpshooter said:**
> Point killdisk to the entire for the drive itself (not any one of the partitions) and then WIPE the ENTIRE drive.  ALL partitions now gone.

Good luck.

All partitions were gone. But it still didn't work. Couldn't find the drive like originally.

And what do you mean, louieb, about trying another drive? And the HDD put in by HP was some "Ultra DMA 120gb" drive. Not sure, can't find the specs. And I don't know what diagnostic tool to use. -_-

This is blah.

---

### Post by SchitzoJoe on 2008-05-30
AHA! I have a Western Digital WD1200 drive.

Searched some stuff, and someone said changing the jumper settings helped fix this. How do I change those? They said to change the Jumper settings from "Master, single drive" to "Cable Select" but I'm not sure how to do that.

EDIT: My stepdad knows how to change the settings to Cable Select, so I think we're in business. After we get it done, I'll let you know how it goes.

This trouble might soon be over. :D

---

### Post by SchitzoJoe on 2008-05-31
It worked.

All I had to do was change my jumper settings on my HDD to "Cable Select," which took no longer than 5 minutes.

Thanks for everyone's help in this matter, never met a kinder, more helpful community. :)

---

### Post by louieb on 2008-05-31
:) Thanks for letting us know. I didn't think about checking the jumper settings.  Have fun.

---

