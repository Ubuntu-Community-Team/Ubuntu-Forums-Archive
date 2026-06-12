---
title: "Partition issue"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Then on 2008-04-05
I have two hard drives, one is 30 gig, the other is 150gig.
I have windows XP installed on the 30gig.
What I'm trying to do is creating a partition giving windows 20gig and ubuntu 10gig.

So ran the installer and now windows runs on a 20gig partition. The other 10gig is just labeled "free-space". From here I want to install ubuntu on this "freespace", the problems being:
I can't change it to NFTS like my other drives.
When I try to go forward with the installation I get a message than says: No root system is defined. Please correct this in the partitioning menu.

I'm pretty sure this is easy to fix, but I'm really inexperienced with things of this like. Could someone here please lend a helping hand?? 
Thank you very much!!:)

---

### Post by mikewhatever on 2008-04-05
You have to assign / character to Ubuntu system partition which an alternative notion for root. It's probably worthwhile to mention that Linux can't be installed on NTFS partitions, so use ext3 instead. [http://psychocats.net/ubuntu/images/feistydual12.png](http://psychocats.net/ubuntu/images/feistydual12.png)

---

### Post by Then on 2008-04-05
Wow, that was a fast response! Thank you!
Does it matter what mount point I use? Will just / suffice? 

Tyvm!

---

### Post by mikewhatever on 2008-04-05
Yes it does. I must be / for the system partition, however, for a data ones pretty much anything is good.

---

