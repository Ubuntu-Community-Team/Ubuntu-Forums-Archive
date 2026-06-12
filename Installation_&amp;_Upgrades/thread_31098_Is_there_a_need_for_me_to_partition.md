---
title: "Is there a need for me to partition?"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by oniko0 on 2005-05-01
Hello, all!

I would like to place Ubuntu on my D: drive, which is an empty, FAT32 space.

1) Since Linux can write on FAT file systems, would I still need to re-partition my disks ( I am VERY reluctant to change my disk settings, as I have no computer background)?

2) Would I run the risk of erasing anything on the C: drive?

3) Does anyone foresee a complication that may arise while installing Ubuntu? 

I apologize if these sound like simply questions. 

Thank you so much for helping me!

Oniko

---

### Post by momo66 on 2005-05-01
[QUOTE=oniko0]Hello, all!

I would like to place Ubuntu on my D: drive, which is an empty, FAT32 space.

1) Since Linux can write on FAT file systems, would I still need to re-partition my disks ( I am VERY reluctant to change my disk settings, as I have no computer background)?

2) Would I run the risk of erasing anything I don't want to?

3) Does anyone foresee a complication that may arise while installing Ubuntu? 

I apologize if these sound like simply questions. 

Thank you so much for helping me!

Oniko[/QUOTE]
 The Ubuntu installation will partition your drive.  I would recommend changing the FAT32 to ext3 and add some swap space.  Ubuntu has an option that will recommend the appropriate partition format and size.  I would go with that.

---

### Post by dave9191 on 2005-05-01
1) You cant install Linux on a Fat32 partion. It uses a different file system structure. Although you can write to fat32 partitions, Linux needs its own ext2 or ext3 partion to work. 

2) There is always some risk of messing up, so always keep a backup of the most important files. 

3) As long as you leave some unpartioned space on the drive, pop the cd in and nothing goes wrong, you'll have a dual booting system in no time. 

Never appologise for asking (unless its been asked time and time again). We all started in the same place at some point. 

If you are running win xp and you dont have anything on your d drive. then you can use computer managment (start, right click on my computer, manage, disks) to delete the partion through a nice gui. Make sure that you delete the right one. And b4 clicking yes, check, double check and check again. And keep a backup :) That never hurts. 

Then you can pop the ubunut cd in, boot, follow the on screen installer and it should configure the system for dual boot with windows in no time.

---

### Post by oniko0 on 2005-05-01
Thank you, Dave and Momo!

Your responses sort of brought up two more questions:

4) How big should my swap spaces be?

5) Since I have an E: drive, what would happen after I delete the D: partition? E: becomes D:, right? But I already have 2 GB of data on E:, would I still be able to properly create new partitions out of E:?

So question 5 really becomes: Could I reformat D: (from FAT32 to ext#) without deleting the partition?

Thank you again!

---

### Post by dave9191 on 2005-05-01
Your swap partition should be the same size as the amount of RAM on your system. But the ubuntu installer should sort that out for you. 

If you delete the partion where drive D is, then partion where drive E is will be uneffected. Windows may rename it for your from E to D tho. And you can reformat the partition to another format without deleting it. But you need a min of 3 partitions for linux, a boot, swap and file. So if you dont have unpartioned space somewhere on  your drive, it would prolly be best to remove the d partion and let ubuntu sort it slef out. 

Dave

---

### Post by oniko0 on 2005-05-01
Thank you, Dave. I really appreciate your timely and accurate responses!

---

### Post by dave9191 on 2005-05-01
No probs. Good luck with the install.

---

### Post by az on 2005-05-01
Edit:  This tab has been opened for about twenty minutes and it looks like I missed the boat...  Anyway...

"I would like to place Ubuntu on my D: drive, which is an empty, FAT32 space."

It is irrelevant that it is a fat32.  It could be NTFS, it could be HFS, it does not matter.  You are going to blow it away by installing ubuntu on top of it.  Now, if you had data there that you want to keep, you would have to shrink the partition and create some free space.


"1) Since Linux can write on FAT file systems, would I still need to re-partition my disks ( I am VERY reluctant to change my disk settings, as I have no computer background)?"

You will not have to change any settings.  The installer will show you all your disks and suggest to install on top of the first disk.  Say no and pick the second one.


"2) Would I run the risk of erasing anything I don't want to?"

You run the same risk every day you use your filesystem.  If you press thr wrong button....  Just make sure you tell the installer to use the correct disk.

In linux, your first hard drive is known as
/dev/hda

If you have several partitions on a disk, they are laid out like:
/dev/hda1 /dev/hda2, etc...
Depending on where your cdrom is on your ide setup, your D: drive could be either
/dev/hdb
/dev/hdc
or /dev/hdd (if you have two cdroms in between your two drives in your ide setup.

Anyway, there is no danger of screwing up cdroms, they are not disk drives...


"3) Does anyone foresee a complication that may arise while installing Ubuntu?"

No.


"I apologize if these sound like simply questions."

The first time I installed linux, I needed to preserve my windows partition.  I had to use FIPS to split a fat partition.  I pondered it for days and took five minutes checking and double checking what was on the screen to make sure it was what I had on the paper before pressing enter.

My heart punded, but my drive got split without a problem.  The Ubuntu installer is much much more advanced.  You should be fine.  Just make sure you delete the correct drive, then you will be shown the free space.  Select guided partitioning and everything will be done for you...

---

