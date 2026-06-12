---
title: "Ubuntu always courrupts Windows :("
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Lamez on 2007-06-29
Ok, I have been trying to do a dual boot between windows and ubuntu, I alwas install windows first (as I have been told to..), then I login to windows. Then I restart with ubuntu live cd, and have a sucessful install. Then when I reboot, I try to re-log into windows, and it says there is somthing wrong with the partition, or somthing along those lines.

I also have tried to setup my partitons manually.

I set up my partitions as so:

[SIZE]    [SYSTEM]  [FILE SYS.] [MOUNT]
137Gb - Windows - NTFS -       What ever mount it is, never looked
1Gb     - SWAP     - SWAP-       none (should I mount it to somthing?)
162Gb - Ubuntu   - ext3  -       /

I am very new to linux, farly new to partitons, but still need help in these areas!

-Thanks Guys! ;)

---

### Post by scrooge_74 on 2007-06-29
Probably windows did not shut down properly even when it seems it did.  Are you mounting the ntfs partition on  ubuntu and making changes to it?

---

### Post by Lamez on 2007-06-29
I shutdown windows properly ever time, I have done this installions of both O\S's over at least 10 (no joke, I like to experiment)

I do not edit any of the windows partition, I leave them on the file system of NTFS.

---

### Post by lisati on 2007-06-29
I have dual-boot with Windows XP and Ubunto 7.04 on both my desktop (Compaq with a recovery partition as well as the WIndows & Ubuntu partitions) and on a Toshiba a100-somthingorother.  Windows reported a problem the first time I restarted it on my Desktop - you might want to ask Windows to do a CHKDSK on its partition and then restart. See how you get on.

---

### Post by Lamez on 2007-06-29
well I never did a stand alone chkdsk command, I did chkdsk /f

and that got me no where.

I will try that.

---

### Post by balleyne on 2007-06-29
I don't have any links on hand to back this up, but I believe that Windows XP has a feature/annoyance that sort of keeps track of it's surroundings, so when you boot into Windows after resizing the partitions it's a little disoriented and all "woah guy.. something... something's... different......" (picture someone returning to their office after the weekend and noticing that the wall has moved 5 feet inwards). A "chkdsk /f" should fix it (though I think when you run the command, and then it'll set the chkdsk to actually run the next time you boot up since you're running it on the drive that windows is currently using).

*shrugs* hope that helps

---

### Post by Lamez on 2007-06-29
I have already tried that.

Am I mounting my partitions right?

when I ran a partition check, it say the partition that windows was on was unmounted.

I do not know, I just got done reinstalling windows..again.

Thanks for the suggestions.

---

### Post by balleyne on 2007-06-29
Hmm, why do you need to configure the partition tables manually? Couldn't you let the Ubuntu installer handle it (by selecting the resize windows partition option)? Then, if you wanted to make any changes later (e.g. increasing the swap) you could use a tool like gParted. This would avoid setting up any of the tables manually *shrugs*

---

### Post by Lamez on 2007-06-29
Well, I have a 300Gb hard drive, and Windows XP SP1 only supports up to 137Gb, so I want to use my unpartitions space on Linux.

Why shrink it when I have tons of unused space.

---

