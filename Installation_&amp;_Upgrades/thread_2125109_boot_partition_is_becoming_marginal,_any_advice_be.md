---
title: "boot partition is becoming marginal, any advice before it fails"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by rtrask on 2013-03-13
-- Quick summary for the impatient --
I think that the raid 0 array must be failing, I got a (error: hd0 out of disk space) when attempting to boot. I was eventually able to get it to boot again. But I'm afraid the writing is on the wall. Any advice on imaging the raid 0 partition to provide a short cut to restoring it later.

-- Details for the rest of us --
 
I should not have bragged about how stable my desktop system had been for the last year. 

I set up my system like this: 
2 SSD 90 gig stripe raid 0 
2 HDD 1 terabyte mirrored raid 1

On the raid 0 array is Windows 7, and Ubuntu 12.04 desktop
On the mirrored disks are my home directory and data
I've tried to make sure that the SSD had only software / OS that could be reloaded.

There are reasons for this set up, but I won't go into that right now.
The SSD's are both OZC 90 gig, but slightly different versions, I think Agility, and Vertex. Which is obviously less than ideal, but as long as I put the Agility first in sequence everything seemed to work for at least 18 months. But today my system froze, and recovered partially, so I decided a reboot was in order. When I tried, it would not come back up. It was failing with "HD0 is out of disk". On a couple of attempts a version on grub would come up, but it did not have Windows 7, and was not right not sure where it came from. It would fail and leave me at the grub CLI prompt.
 
I downloaded an alternative cd, and booted off of that & went into recovery mode. From the shell I ran "dmraid -ay" and one of the raid sets would not become active. I was able to mount the Lunix system partition, though and chroot to it. Looking around it seemed OK to me. I then attempted to reload grub. That failed. I thought well I'm going to need to rebuild the system. -- Tried to boot one last time -- and it just came up normally.

So I don't have much time I'm sure. Any advice? Is there something akin to Ghost that I could image the raid 0 partition to that would save me time restoring the system and all the software I've loaded / configured? I've looked around a bit and seen relinux, Remastersys, and  clonezilla. I don't think the first 2 will help with the Windows partition, but possibly nothing will. What are your thoughts?

---

### Post by rtrask on 2013-03-13
No takers? No one has any advice on a quick way to backup / restore a dual boot system?

---

