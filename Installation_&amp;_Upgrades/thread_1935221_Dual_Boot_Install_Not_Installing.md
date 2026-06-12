---
title: "Dual Boot Install Not Installing"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by rs321 on 2012-03-03
HP Pavilion G Series Laptop
Win 7
10.04.2

Folks,

Having spent about four hours vainly searching for an answer I'll risk being repetitively redundant and just ask:

I'm trying to make a dual boot on a new laptop.  I shrank the Windows part to free 225 gigs, made all the backups, and Ubuntu won't install anywhere other than over Win 7, erasing Win 7 in the process.  As tempting as that may be I won't do it but it won't allow me to check the box that will put it in the newly-created free space.

Anybody got a clue as to how to get it there?  

-Randy

---

### Post by darkod on 2012-03-03
These days HP ships the laptops with all 4 primary partitions used. Usually:
100MB System Reserved partition
Win7 system partition, C:
Restore partition
HP Tools partition

Open Disk Management and confirm if you have 4 primary partitions existing. If you do, it can't install because it can't create a fifth one. In this case your options are:
1. Use the backup software to make a set of restore DVDs and then you can delete the restore partition. If in the future you need to do the factory restore, you can use the DVDs. This way you also can use the space taken by the restore partition which in some cases is up to 20GB.
2. Leave the restore partition, delete the HP Tools partition instead. I'm not sure if there is anything useful on it, you might want to investigate first.

Whatever you do, DO NOT delete the small System partition. It has win7 boot files on it and it will not boot without it.

---

### Post by rs321 on 2012-03-03
Darko,

Thanks for your prompt reply; I've read a number of your posts and your advice always seems sound.

I have already made the restoration DVDs you mentioned so that's not a problem but once I delete the restore partition will I be able to use the 225 gig partition for Ubuntu or will I be limited to only the ~20 gigs from restore?  Also, I've used 10.04.2 in the past and enjoyed the experience, which is why I'm considering it for this install, but I noticed you're using 11.10 64 bit.  My laptop is also 64 bit and I considered a later version of Ubuntu in 64 bit but wasn't certain I could run everything under it.  Do you recommend I go that route?

Amazing how one question can spawn several more but I suppose this is where they should be asked.

Thanks again,

-Randy

---

### Post by darkod on 2012-03-04
Deleting the partition makes it possible the ubuntu installer to create an extended partition with root and swap inside it as logical partitions. You can install on the bigger space. It should automatically use the largest available unpartitioned space, ignoring the smaller ones.
If the restore partition is physically next to your unpartitioned space, it will become a single joined unpartitioned space which is better because you can use all of it.

I use 64bit mainly because I have 6GB of memory and 32bit can only use up to 4GB (in fact more precisely 3.5GB). This is a limitation of 32bit and it doesn't depend on ubuntu, it's the same in windows.
So depending how much ram you have, and whether you plan to upgrade in near future, make the decision. There is also 64bit version for 10.04 so you can use that version if you want.

---

### Post by rs321 on 2012-03-04
Darko,

Sorry to take so long to get back but I've been working on the installation.  There are indeed four partitions on my hard drive and the only one I am able to use is the one in which Win7 is located, and using it would delete Win7, which I'm not ready to do.  I have tried manually selecting the other partitions but they lack the necessary files to install Ubuntu.

I'm getting in way over my head here.  I tried deleting one of the partitions yesterday, the one with the "restore" stuff on it because I made backup DVDs but the data, not the partition, went away.  I thought I was deleting the partition because Windows asked me if that's what I wanted to do but it went nowhere.

I'll figure out how to delete the entire partition and then figure out how to install Ubuntu.  I've read many posts on that in the last few days and I think perhaps I read a few too many.  Nothing will make me happier than to mark this as SOLVED!

Thank you very much for your assistance getting me as far as I've gotten.

-Randy

---

### Post by darkod on 2012-03-04
You should be able to delete it with windows Disk Management without any problems.

Alternatively, you can boot the ubuntu cd in live mode, open Gparted and delete it.

Which ever method you select, just make sure you delete the correct partition!!!

---

### Post by rs321 on 2012-03-05
Darko,

Thank you ever so much for your assistance and advice.  I installed 10.04 64 bit and it seems to be working and if there are any issues with it I'll search and\or make a new post.  I finally built the nerve to remove an unnecessary partition and installed them side-by-side, which worked for me in the past, and now all I need to do is configure it and start getting updates.

Thank you again.

-Randy

---

