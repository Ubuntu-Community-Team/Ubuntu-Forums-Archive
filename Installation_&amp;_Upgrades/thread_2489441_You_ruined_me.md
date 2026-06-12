---
title: "You ruined me"
date: 2023-07-30
forum: Installation &amp; Upgrades
---

### Post by tardyquark on 2023-07-30
I have a Dell Optiplex 755, which was running Win7 and Win10 in a multiple boot system, with three hard drives, two primaries (a,c) and a backup (b drive).  I wanted to try Ubuntu, and deleted a Win 8 partition on the backup drive.  After installing 12.04.1, which is the only one certified for that machine, I found the primary drive wiped to FREE SPACE, and no way to get to the previous multiple boot startup.  I had U.S. Patents on that drive, including partitions for Win7, Win10 and literally a half-million work files.  I was writing a book, and had stored several web sites and hundreds if not thousands of images.    
YOU RUINED ME
I don't know if I can ever get it all back.  I was careful, and specified the b drive in setting up the new ext4 partitions in the old Win8 partition that I deleted.  I gave no one permission to wipe the a drive.  
What your software did to me was pure evil.  
May you someday meet a God to give you service in kind.

---

### Post by ne29914 on 2023-07-30
"Son,** real men** don't do backups. But they do cry a lot."

Now take a deep breath and get your pulse down. I'm sure your stuff is there somewhere and can be reinstated.
Where did you get the idea that only 12.04.1 is "certified" for your machine? Just use the latest version (22.04 LTS). Period. I know there are silly lists like this floating around on the interwebs. I fell into that trap as well, but had the sense to ask here first before proceeding.

I've no experience with multi-boot systems (I love KISS), but this is surely a partition table problem that can be fixed.

---

### Post by ajgreeny on 2023-07-30
I find it hard to believe that anyone would attempt to install another OS with no backups of their valuable data, so surely you must have a backup of all your files that you are telling us were lost when installing Ubuntu. If you had no backups the files can not have been of any value to you!

Incidentally Ubuntu 12.04 lost all support about 8 years or even longer ago so would have been a pointless install and would have been impossible to update in any way or to add any new applications to it.

---

### Post by ian-weisser on 2023-07-30
If your data is truly valuable, then take your hardware to a professional recovery service.

Do not bother trying to recover it yourself. Your likelihood of success is low. You are more likely to further damage any recoverable data.

We suggest that your next system, whatever the operating system, have your data properly backed up to a different device.

That seems the only relevant advice we can offer.

You called us "evil" and wished horrors upon us, so any further discussion does not seem worthwhile.

---

### Post by aljames2 on 2023-07-30
> **tardyquark said:**
> I have a Dell Optiplex 755, which was running Win7 and Win10 in a multiple boot system, with three hard drives, two primaries (a,c) and a backup (b drive).  I wanted to try Ubuntu, and deleted a Win 8 partition on the backup drive.

Umm, you deleted a Win 8 partition "on your backup drive".  A backup drive should not contain another OS, nor should such a drive be used for anything other than storing your data.  My backup drives are on a separate machine and do not even mount automatically.

+1 per ian-weisser.  Hire a pro to try to help you recover.

---

### Post by grahammechanical on 2023-07-30
It is recommended that we that we use Windows tools to manage Windows partitions and then defragment the drive. And then use Linux tools to manage Linux partitions. What tools did you use and what work did you do with them?

Did you by chance decide to create a new partition table? That would wipe out the index table that an OS would use to find the locations of files. 

The Ubuntu installer gives us the option to erase disk and install Ubuntu. That would wipe everything on the disk. The other option would be "Do something else." With that option we pick and choose what partition to install Ubuntu in. 

Also, Ubuntu Linux installers have big problems recognising Windows partitions if Windows is hibernated. Which is what Windows Fast Startup does.

Regards

---

### Post by DuckHook on 2023-07-30
Thread provisionally closed for staff assessment.

---

### Post by QIII on 2023-07-31
"We" did nothing to you.  "We" didn't write the software.  "We" did not fail to maintain backups of your critical data.

"We" do not know how you went about your installation.  "We" do not know what "A", "B" or "C" drives you might be talking about since the installer uses "partitions".  "We" do not know if you followed instructions.  "We" do not know if you missed something.

You are NOT welcome to impugn or indict the members of this community.  This thread will remain closed.

Should you decide to request help in a respectful manner, you may try again in another thread.

---

