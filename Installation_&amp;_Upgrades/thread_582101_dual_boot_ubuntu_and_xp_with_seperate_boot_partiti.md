---
title: "dual boot ubuntu and xp with seperate /boot partition"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by donald7777 on 2007-10-19
hello everyone. I have a 120 gig ide hd and i have it partitioned as follows:
100 meg /boot partition
1024 meg swap file
50 gig ubuntu partion 7.10 ext3
a 50 gig extended partion for xp ntfs

Now I am trying to install xp and it keeps poping up the messege that it needs a windows xp compaible partition. WTF
i have tryed leaving the space free and creating a partition with xp, created a fat32 with qparted, and a ntfs with qparted and it still doesn't work.

please help.

sorry to the people who say ditch xp but its needed.

---

### Post by Bliepo32 on 2007-10-19
Windows only works with a primary partition for as far as I know.

---

### Post by jimc52 on 2007-10-19
As I was just posting a question myself, I may not be the best answer since I have been a Fedora user who is switching to Ubuntu, but to answer your question, please let me explain:

You must ALWAYS install XP first!  Never try to install Linux and then XP.
The reason why is because the Microsoft product does not have a dual boot installer for XP and Linux, but Linux detects XP and will easily install with XP.  So the RULE is, always install XP first, let XP make its own
NTFS partition, and then use your Linux installer to re-partition your drive AFTER you have installed XP.

Don't worry, if you have the FULL VERSION of XP, not an upgrade!...the XP installer can wipe your hard disk clean, even if you have previously partitioned with Linux.  Just create one BIG primary partition for now and install XP on C: primary partition.  After you have finished with your XP installation, then you can go back and install Ubuntu.

But first, make sure that you run Disk Defragmenter.  Run XP defrag
and then check your disk for errors.  At the terminal (command prompt) type:

chkdsk c: /F/V/R

XP will tell you that NTFS is locked and ask if you want to perform a check disk on your next reboot...enter "y" without quotes for yes
and then reboot.  Let XP check your partition and make sure everything is in order.

Now, you have made sure your hard disk is organized.  You might want to make an XP System Restore Point and then make an XP boot CD to backup NTDLR and other files.  Look on the internet with Google for how to make an XP boot CD...it can be time consuming, but much easier than reinstalling XP!!!!! ... if things get messed up.

Once you have defragged, checked your disk for errors and made a backup CD for XP, then proceed to do your install with an iso disk of Ubuntu.

Ubuntu installer should detect all hard disks and your single C: NTFS partition and allow you to create /boot, swap and ubuntu partitions by repartitioning.  Remember, you can only have 4 partitions on a single hard disk under XP (or under Microsoft file systems!).  So do not try to create more than the 1 NTFS partition with XP and the 3 partitions for Ubuntu.

Hope this helps :)

---

### Post by donald7777 on 2007-10-19
I was worried about that d*m microsoft. oh well it was only a couple of hours installing ubuntu with everything. thankyou for your help.

---

