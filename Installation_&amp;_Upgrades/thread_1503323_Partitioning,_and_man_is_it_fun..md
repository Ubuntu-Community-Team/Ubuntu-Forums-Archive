---
title: "Partitioning, and man is it fun."
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by PromptSquirrel on 2010-06-06
First off I'm running Ubuntu 10.04 LTS off a live CD as I post this. 
I think it's kinda funny, but anyways. 

I'm looking to run a duel boot system with XP. I've read a lot of material, but I'm afraid to make a partition because I have NO idea what to do. I included a picture, that's what I'm working with. 

If someone has already made a topic about this, I'm sorry. I *did* search. Just post a link?

---

### Post by darkod on 2010-06-06
You won't be able to make a partition until you shrink /dev/sda1 (the XP partition) because it's taking almost the whole hdd.
The triangle warning mark means there is some problem with it, maybe something small, however, Gparted will not touch it until it's there.
Try right-click /dev/sda1 and select Check. That might show you message with instructions. Usually it says to boot XP and run the windows chkdsk tool.

After that boot again in live mode and open Gparted. If the symbol is not there, you've done the first step and you're ready to shrink.

Make a calculation how big you want /dev/sda1 to remain, how much to shrink. Ubuntu works on very little space but in order to have enough space for the future use you should plan at least 30GB for ubuntu.

Do not create any partition in the unallocated space left after the shrink. After the shrink make sure you reboot XP few times, it will want to do the disk checks again.

Only after that start the ubuntu installer and just use the Use Largest Available Free space option. That will install it into the unallocated space left after the shrink.

---

### Post by PromptSquirrel on 2010-06-06
So, I ran the check and instead of a alert symbol (I guess you would call it that?) a little key symbol replaces it. I'm guessing that means it's locked? 

Any idea on how I would shrink my XP partition? Microsoft said something about doing it, but you need to have a CD. A CD in which I don't have. 

Thanks for the assistance though, I'm glad you read and posted a reply.

---

### Post by darkod on 2010-06-06
The key is used when a partition is mounted in linux. Perhaps it was mounted in order to check it.
Try right-click, Unmount. I have no idea if it fixed the 'problem' though.

PS. You can shrink it with Gparted but not while it has the key symbol, or the triangle. It has to be without any errors, and not mounted (unmounting is easy).

---

### Post by Bucky Ball on 2010-06-06
Before shrinking any Windows partition, make sure you back up and DEFRAG THE PARTITION!!

That last part is very important. You should be able to shrink with System->Administration->Partition Editor, which you'll find in Ubuntu.

---

### Post by PromptSquirrel on 2010-06-06
Great It's saying I have physical damage and some other wonderful messages. 

So run the file check, and YES I defragged my comp.

---

### Post by darkod on 2010-06-06
Do it from XP. Boot XP and unless a disk check starts automatically, open command prompt (windows button + R, type cmd, Enter), and do:

chkdsk c:/r

That might say it will run on next boot, so just restart to make it run. See what it says.

[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

---

### Post by PromptSquirrel on 2010-06-06
I ran the check once more, and booted up Ubuntu through the LiveCD. Still same exact problem. 
Dude, I think my hardrive is unrepairable.

---

### Post by oldfred on 2010-06-06
It was my understanding that the check disk only fixes one thing at a time. You have to run it until it gives no errrors.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

