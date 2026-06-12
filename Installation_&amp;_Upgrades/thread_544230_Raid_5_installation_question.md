---
title: "Raid 5 installation question"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by pnotequalsnp on 2007-09-06
Thanks for taking time to answer my question.

I was wondering if I have Raid 5 (software) set up on 4 Sata drives and the OS installed on a separate IDE drive (no raid), if the IDE drive fails can I swap in another IDE drive and reinstall Ubuntu so that I get the Raid 5 back online.

I am trying to find a way to not have the OS installed on my Raid setup and on another drive but I want to still maintain redundancy.

---

### Post by tootlet on 2007-09-06
Greetings,
I have a similar setup on OpenSUSE 10.2 only I have a single SATA that boots, 3 for RAID 5. You would have to replace the booting drive, then mount the Raid 5. Should work fine from there. I haven't had a failure yet so I can't really say. But that's my plan!
Tom

---

### Post by pnotequalsnp on 2007-09-08
Thanks for the experience.  The situation where the OS drive fails and it wont load the raid 5 arrays is exactly why I am hesitant.  If anyone has had the unfortunate experience of restoring any raid setup this way (with an OS disk that is not on a raid), please post.

---

### Post by gnomeza on 2007-09-09
Have you considered putting the OS on a RAID-1 pair?

Cheap, redundant, bootable.

---

