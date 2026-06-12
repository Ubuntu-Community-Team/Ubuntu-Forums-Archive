---
title: "Is there a simple guide for setting up an Encrypted /home post install?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Arthur Archnix on 2007-12-15
I've been running a fully-encrypted system that is setup through the Gutsy Alternate CD. Although you're not given much options in terms of partitioning, I'm really impressed how easy the Ubuntu guys/gals have made setting up a fully encrypted system. Kudos to them. 

Anyway, I don't really need a fully encrypted system, and am not pleased with the performance hit. I just want to encrypt my home partition. I'm wondering if there's a simple guide or some good instructions? I've been browsing the forums and the next, but nothing I found is for Gutsy specifically. 

As a finished product I'm looking for
   9 GB     /                      ext2
   9 GB     /mnt/hardy     ext2
0.7 GB    /swap
  60GB    /home              ext3

During setup I plan on setting the /mnt/hardy to home and leaving the 60GB unused. Then I want to encrypt it. Copy home to it. Change fstab to point to it. Setup pamount to automount it after succesffuly login. That's the broad outline... I'm looking for some help painting in the details.

Tips or pointers are greatfully appreciated.

---

