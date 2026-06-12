---
title: "&quot;Unique&quot; grub XP issue."
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by drex5483 on 2007-06-22
I installed XP on my inspiron hdd. Partitioned it into a 30gig (XP) and a 10 gig (empty/saved for feisty) partition using the XP boot CD. 

After XP is on the 30 gig part, the 10 gig part was visible as an empty, separate drive (empty 10gig was "C:", 30gig with XP was "D:" drive according to Windows). 

This is where the first problem may have been. I've had dual boot XP/dapper before and the other partition was never seen by XP.

XP ran fine, no problems. I installed Feisty with no problems onto the 10gig. But now the 30 gig XP part is showing up as a drive (called sda5) on the Feisty desktop and when I open it, all the XP files are there. Windows is not recognized by grub. I did the usual grub fix to add XP but won't boot.

Question: Am I totally screwed with being able to see both partitions on Feisty? I don't think I should be able to see all the Windows files on the drive. I don't mind doing a total reinstall but what should my partitioning be since obviously what I did was incorrect?

Things I don't know and don't know how to get: How I did "swap" or other partitions when I installed XP. I know there was a 30gig and 10gig part. That's all I remember. 

Things I don't know but can find out if it will help:  The error I get when selecting Windows from grub.

Any help is greatly appreciated.


- D.

---

### Post by ajgreeny on 2007-06-22
No problem with seeing the windows files in Ubuntu as the system will mount the windows partition by default, allowing you to read but not write to it.

It sounds as if the windows install is on the second partition of the disk and feisty on the first partition, ie, at the beginning of the drive. If you open gnome partition manager in your Ubuntu install it should confirm or not that situation.  It may be worth trying to put grub on to the other partition using the live CD (see attached txt file) but I don't think that will help.  Try it and see.

If it doesn't do the trick, I think you have you have two options:-

1.  reformat the whole drive having backed up, and reinstall windows on the whole drive, then install Ubuntu again and use the manual partitioning option to reduce the windows partition and make a new ext3 one for Ubuntu.  This should ensure that windows is at the beginning of the drive and overcome that possible problem.

2.  Download the Gparted live CD (it's a newer version than the Ubuntu one) and boot to that and delete the Ubuntu partition.  Then try moving the windows partition to the start of the drive.  Make sure you still have your 10GB partition, but this time at the end of the drive, and now install Ubuntu on that.

---

### Post by drex5483 on 2007-06-22
Thanks for the help. I won't have an install CD around me for a while so I'll have to wait and see if those options will work.

Two things: 

1: The fact that XP is on sda5 and Feisty is sda6 according to System > System Monitor > File Systems tab doesn't mean that XP is first and Ubu is second? I agree that XP seeing the 10gig as "C:" and the 30gig as "D:" is contrary to this, but ???.  Any way to see where the partitions are on the disc without the boot CD?

2: Can I follow the directions on the attached .txt file without the boot CD? Don't see why not but don't want to try without knowing first.

Thanks again. :)

---

### Post by ajgreeny on 2007-06-23
Gparted on the ubuntu live CD will show you the positions of partitions on the drive as far as I know.
I also think you can do the grub installation with a running install of Ubuntu.  I've never tried it but it certainly works for the first commands so I imagine it should go all the way through.

---

