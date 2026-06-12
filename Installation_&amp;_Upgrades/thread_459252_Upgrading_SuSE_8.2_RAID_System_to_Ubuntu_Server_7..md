---
title: "Upgrading SuSE 8.2 RAID System to Ubuntu Server 7.04"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by seffyroff on 2007-05-30
Hi there!

I'm hoping to upgrade a SuSE 8.2 system with RAID to Ubuntu Server 7.04.  The system has a regular root partition / which is fine, I'll format that and install Ubuntu there.  However it also has a RAID partition which I'd like to keep intact.  If I type "df -h" on the SuSE box it returns the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              17G  2.0G   15G  12% /
/dev/md0              224G   37G  188G  17% /fileserver2
shmfs                 125M     0  125M   0% /dev/shm

How can I carry the /dev/md0 RAID partition safely over to Ubuntu? I had a quick check of the install process and the RAID part seemed to only let me either create a new array or delete an old one.  Also, I don't now how the current RAID array is configured (system was preconfigured) - I'm guessing it's RAID0 but I could be wrong.  I don't have much experience of administering RAID on Linux so I don't know what tools are available for information gathering.

---

### Post by seffyroff on 2007-05-31
Slight update, I noticed that if I went into the RAID conf part of the Ubuntu Server install wizard, then went back from it, a RAID 0 volume has magically appeared in the partition list of the manual partition editor.  Perhaps I've uncovered a little bug?

---

