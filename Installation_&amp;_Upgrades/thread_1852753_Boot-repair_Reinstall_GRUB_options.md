---
title: "Boot-repair Reinstall GRUB options"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by This parrot is dead on 2011-09-30
Hi ya all,

I have Win XP and Ubuntu Natty installed on sda. I installed Ubuntu after XP, from a CD where I burned the ISO. I want to install Mint as well and so I reduced the Windows partition, using Easus Partition Master, to make some free space. Then, following the advice I read (I'm a total newbie to Linux), I wanted to save my MBR. I used [Boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482") Had some problems, thought something was wrong and chose "Restore MBR" and wound up with the following: [http://paste.debian.net/1309701](http://paste.debian.net/1309701). I'm not sure I need to provide that link, so I put it just in case.

I thought "Restore MBR" would invoke the MBR image in my /clean folder and put that back where it was, found out it's not the case. Now my PC boots in Windows, GRUB is gone and I want to reinstall it.

I don't want to screw up so I ask... In the "Main options" tab I will check the "Reinstall GRUB" box, but then what about the "Repair file system" box? Do I need to check that or not? I don't know what that does. That is question 1.

Then when I go to "GRUB location" tab I have two questions.

At the "OS to boot by default" button, all I have is for an option is "Ubuntu 11.04". Pressing the little arrow does not give me the other option. Is it normal that Windows is not listed there? Because if possible, I wanted to chose Windows as the default OS. That is question 2.

My other question is, in the picture that's in the thread I linked to above, there is a button underneath that says "Separate /boot partitions", with the option sda2 chosen. Now I did not see that button/option in Boot-Repair last time I loaded it, only the one underneath called "Place GRUB into". Here the options Boot-Repair gives me are quite simply sda, sdb, and sdc (this last being my USB key, I presume).

Yet, as I said, I do have three partitions on sda ( I checked and Easus sees them all right). Then, is it normal that Boot-Repair does not give me the button "Separate /boot partitions"? That is question 3.
My guess is that it does not really matter and I will simply "Place GRUB into" sda, right? That is question 4.

But the absence of that button puzzles me a bit and I want to understand what I'm doing and what's happening the best I can. So I ask :-)

Perhaps I should add that my aim is to first install Mint and after that install GAG bootloader.

I hope I have been clear and precise enough so that you can help me with these questions. If you need to know anything else, just ask me.

---

