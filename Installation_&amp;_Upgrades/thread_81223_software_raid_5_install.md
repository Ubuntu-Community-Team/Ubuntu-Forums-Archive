---
title: "software raid 5 install"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by gotrice on 2005-10-24
Hey hey. Thsi is my very first post and I am having some trouble with my very first instal. I am installing ubuntu and want to use software raid 5. Is there a walk through that I can get to help me with the partitioning of the drives? I have 4 200gig drives that I want to use and it is not letting me set up anything. I am a complete numpty at this so if there is anything that would help I would be greatful.

---

### Post by jaripetteri on 2005-10-28
Have you installed your RAID5 already? I have tried it two ways both end up booting just fine. Not a walk through just some things I did. Don't know is that the best way to go anyway...

1) I had 4 250GB SATA drives and I made two partitions on each of them. one 500MB and the rest about 249,5GB. I RAID5ed those 4 big partitions and first of small partitons I made /boot and rest of the small partitions I made SWAP. So I end up for one 500MB /boot, three SWAP and about 750GB RAID5.

2) I add one 160GB PATA drive which was left over for my old server and I made it my backup drive. Also used it as boot and SWAP. So this setup I end up with 4 totally RAID5ed SATA drives with only one partition on each and 200MB /boot and 1GB SWAP partitons on that extra PATA. Rest of PATA driver I mounted as /backup.

I used ext3 as RAID5 filesystem and I was wondering is it the best choice for me? I'm using this pc as fileserved with MythTV, also web and maybe mail server. Some MythTV HowTo said that xfs might be good choice for the fs but how reliable it is with RAID5? So what filesystem should be used with RAID5 or RAID in general?

I have one about 750GB partition as / so is this ok or am I just digging hole to myself with partition that big?

---

### Post by durward on 2006-01-14
I am trying to figure out how to use mdadm to set up a RAID5 array. I have searched the forum for help. There seems to be many people trying to do what I am trying to do and need the instructions.

Everyone that answers seems to want to tout their set-up RAID0, RAID4, RAID5, or RAID10; BUT NO ONE will list the steps needed to do any of the RAIDS except RAID0.

I am getting tired of people writing book-length of how great RAID is. What many of us need is a list of steps to do to get a RAID installed.

There is a web site that stepped through setting RAIDs 0 to 5, using mkraid which has been phased out in favor of mdadm. However, the commands and tables are different and no one wants to explain how they are different.

HELP!!

Durward Stockman

---

### Post by lha on 2006-01-15
If you are doing are fresh install then [this page]("https://wiki.ubuntu.com/Installation/RAID1") helps you. I used [this]("http://deb.riseup.net/storage/software-raid/") and [this]("http://juerd.nl/site.plp/debianraid") page as guides when doing my first experiments with raid. None of those sites provide a complete step-by-step walkthrough but they have necessary information. Raid's not too hard to set up. Don't give up easy.

---

