---
title: "Near my end with Ubuntu"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2010-10-06
Let me first by saying that I'm very upset.  I'll try to keep my temper.  I have been running Ubuntu for years.  I have used it as my main system for all that time.

Some of the upset is directed at me, because though I read everything and I have done this type of install many times, I found today that changes to Ubuntu can be very negative--to the point of serious data loss.

Earlier in the day, I started an upgrade in Ubuntu (from the desktop).  After rebooting the system wouldn't work.  This alone was enough to frustrate me.  Due to me having a seperate home partition (which I thought was safe) I decided to delete the OS partition and install into the free space.  

In the past, when you wanted to use the free space during an install you just did so.  I booted from the Ubuntu Live CD, started gparted, and deleted the OS partition along with the swap partition.  Then I rebooted the computer using the Live CD and began the install.  What I expected was an option that said to use the free space.  That choice apparently doesn't exist any longer.

In the past you opened the installer and told it the drive and said to use the free space.  This recent change to the installer doesn't have that option, and because of that it creates a scenario where I believe many people will become very confused and wipe out their data.  So, I would warn everyone away from doing any install of Ubuntu 10.10 without first triple and quadruple checking their options and realize that the installer will wipe their partition without really telling them.

The problem is that the installer appears to only operate on partitions.  This installer's options are not the same, the choice is to install next to another OS or use entire disk.  If you chose to install next to an existing OS then you are provided with options that are quite confusing.  And, if you don't choose correctly you could wipe out the partition you don't want destroyed.  That's what happened to me.

Needless to say my home parition was destroyed and everything I had on it is gone.  I told it to use the entire partition (I was very careful about ensuring I chose that).  That's really the only viable choice.  When I did this it showed me a block illustrating the partition that would be used.  It had shown my large home partition first with the amount of space used by it and in the graphic following that there was what appeared to be the Ubuntu partition it would create.  The installer should not have illustrated the drive like that as the empty space was at the front of the drive and the home partition was at the end of the drive (as it had been for the past couple years).  That tells me that the installer is confused and/or is trying to simplify this for the user, but by not depicting it correctly it can create a lot of confusion.

When I selected to continue I didn't receive any warning that it would delete the contents of the partition.  I got a progress bar indicating that it was setting up the partition then I received an error dialog box that said something about the drive being busy and then it told me to click ignore or cancel.  I chose one then the other and tried to close it, but no luck.  It wouldn't close.  I couldn't go any further.  So I rebooted the computer thinking I'd have another try at it.  To this I noticed the partition space spanned the whole drive and that gparted would crash when I tried to load it.

Your only other choice is to set up the partitions manually, which, due to how Linux sets up 3 partitions you can easily spend more time then you want trying to figure out exactly what needs to be done.

My frustration here is that this set up didn't need to be changed.  The options should have been left alone.  In the past that is what I was able to do.  It was easy.  Click the option to use free space and go.  Now it is confusing and convoluted to the point that it has cost me a serious amount of important files that I can never get back.

Canonical needs to understand that to add options is not always a good thing.  Canonical seems to have taken something that was simple and turned into something too confusing for those of us not tasked with developing the OS.

So, be wary of this new installer.  Maybe it was the same way the last time in 10.04 I don't know, but the last time I can remember doing an install to a HDD with existing files where I knew there was free space I was able to accomplish it without this very significant loss.

I'm nearly at the point that I don't want to use Linux any more and I have been an advocate for it for a long time.  This should not happen and any installer that will erase the contents of a partition needs to tell you and warn you more than once.  I was never warned.  The choices were too confusing.

Anyone know how to undo this debacle?  How to get back the partition and the contents?  Right now all partition editors say it is a "bad" partition.

---

### Post by aeronutt on 2010-10-06
Sorry to hear your mix up. And I agree, the installer is very confusing when trying to manually load to a particular partition or try to use free space.

---

### Post by e79 on 2010-10-06
I do not intend to insult you in any ways, but in all those years you've been running Ubuntu, haven't you done ANY kind of backups of your /home directory ? If so, simply do a fresh install and copy back your data. Though the installer options might have change since the last time you used it, you cannot blame anyone but you for losing all your data if you never backed it up.

Also as it happens on Windows as well, doing a fresh install instead of upgrading (as many many posts here suggest) is usually the best way to ensure everything goes smoothly. Nonetheless, I feel sorry for you and totally understand your frustration.

You could try Photorec  and try and recover your data, couple of posts speaks about it.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by tommcd on 2010-10-07
> **jimbo99 said:**
> 
Your only other choice is to set up the partitions manually, which, due to how Linux sets up 3 partitions you can easily spend more time then you want trying to figure out exactly what needs to be done.

The obvious solution here is that you need to learn how to use manual partitioning. It is not hard to learn at all.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
You will need to do some reading to get the most out of any linux distro.
The easy way is simply to have 3 partitions: root, swap, and home. When you reinstall Ubuntu, simply reformat and reinstall to the root partition. Choose *not to format* the home partition. And choose mount point /home for the home partition. 
I have never had this problem; but I researched how to do this before I messed with my computer.

---

### Post by Bruce S on 2010-10-07
I did some searching about formating and partitioning before I tackled it.
I have a detailed article that I keep handy for when I do a re-install and follow it closely.
I am a non Geek user but with a bit of reading and searching I can get what I need for most of my problems with Ubuntu.

If not, then I have my trusty Computer serviceman who can handle Linux problems.

Compared to Microsoft OS and its problems , Ubuntu is a pleasure for me.:)

---

### Post by lechien73 on 2010-10-07
First of all, I'm sorry for your trouble. I think everyone knows the pain of losing vital data, and I'm not going to make it worse by asking if you had a backup, or by saying that it wasn't Ubuntu's fault.

Practically, I would suggest making a clone of the disk before you do anything. If a Clonezilla LiveCD will make a complete clone of the disk and structure - bad partition and all - then you can work on that to try and recover the data. That way, when you have a working solution, you can try it on your primary drive.

You could try R-Linux, which is free from here: [http://www.r-tt.com/data_recovery_linux/](http://www.r-tt.com/data_recovery_linux/)  I haven't used it myself, but it's been recommended to me on several occasions.

Hope you manage to recover something!

---

### Post by aeronutt on 2010-10-07
For the future, the correct fix is also the easiest, clarify the installer instructions and options. If the community ever wants Linux/Ubuntu to move closer to mainstream use, the basics must be clear and foolproof, without need to surf directions/information on the web for hours prior to use.

---

### Post by NotWindows on 2010-10-29
I agree that it is way to confusing. I want to reformat a partition and reinstall Ubuntu because the current will not load. I posted a thread and I am not getting much help. A few months ago I did an upgrade and lost Ubuntunu, I don't know if it was a faulty update or what. At that time a gentleman helped me and it seemed pretty straight forward. I can't find the post now and I need to do it on a couple of computers. I know it was all about setup in the partition menues.

---

### Post by peyre on 2010-10-29
> **aeronutt said:**
> For the future, the correct fix is also the easiest, clarify the installer instructions and options. If the community ever wants Linux/Ubuntu to move closer to mainstream use, the basics must be clear and foolproof, without need to surf directions/information on the web for hours prior to use.

Agreed.  Clarifying the installer is a good idea.  I'd also like to see another option for the manual partitioning--instead of giving you a blank slate, set it the way Ubuntu would default it, and let the user modify the default settings.

FWIW, before I upgrade *buntu, I always back up all my data.  I use an external hard drive for that; it's inexpensive, effective, and simple.  I take the same precaution with Windows upgrades of course.  I don't trust either OS 100% with my data.

---

### Post by Quackers on 2010-10-29
Part of the problem I think is that the little check box that is to tell you which partitions are going to be formatted is really quite faint. It is difficult to tell there is a check mark in it. It certainly doesn't help when it is "greyed out" at an important part of the proceedings. And that's if you chose the manual option.

---

