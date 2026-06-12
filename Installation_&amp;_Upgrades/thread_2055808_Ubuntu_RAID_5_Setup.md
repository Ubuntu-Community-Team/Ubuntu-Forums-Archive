---
title: "Ubuntu RAID 5 Setup"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by ritchie888 on 2012-09-10
Sorry if this has been asked before, I searched and found nothing. 

First things first, I'm on **Ubuntu 12.04 64 bit**, with my OS installed on a SSD. I'm about to purchase two Seagate 2TB HDD and I wish to mirror them to each other using **RAID 1**. Having recently lost 1.2TB of movies and TV shows (hopefully nothing that can't be replaced!) I want to reduce my risk of loss and protect my data the best I can. 

I have a **Gigabyte GA-Z77-D3H** which has a RAID controller onboard. First of all, I'm seeing a lot of talk about fake or hybrid hardware controllers, but couldn't find any information if my motherboard falls under that category, does it?

I'm also seeing a lot of hardware vs software discussions, one of the reasons I'm more incline to use hardware based methods is that if I mess my OS up I want to be able to remove the HDD and plug them in somewhere else and be able to retrieve my data immediately, rather than relying on getting my OS up and running again. I have a HDD dock and would love to be able to remove my HDD from my desktop, slot it in, and see the data on any OS, Linux or Windows. 

So a few questions: 

1) Am I right in thinking that if one HDD fails, as the data is mirrored across both drives my data is safe (unless they both break)? Will the OS even notice if a drive is dead if Ubuntu only can only see the two drives as one? Is it really as simple as thinking the two drives are exactly the same, meaning I can remove either and use it singularly within there being dependencies on the other HDD?

2) Would anyone recommend using the motherboard hardware method over the software method? It seems software is more preferable, but given my points above would hardware be more suitable? 

3) My OS is installed on a SSD and no system files will be installed on my two HDD RAID drives, they are purely for data storage. More tutorials I've found online are getting very technical with RAIDing two drives, one of which already contains their OS. Can I assume my needs are much easier? 

4) Using a 64 bit Ubuntu 12.04. Lots of things I've found are trickier to do with the 64bit OS over 32bit. Is this one of them? Any differences or problems?

5) In the event of a HDD failure, which can't be recovered, what happens when I put a new HDD in it's place? Does data copy across from the good HDD automatically to the new one, renewing the mirror, or do I have to do something to make it aware of the situation?

Will be receiving the drives on Wednesday and intend to tackle the RAID then. Any suggestions, step by step guides, or tips would be most appreciative!

---

### Post by SlugSlug on 2012-09-10
With 2 drives it will be a RAID1

If one drive fails your data will still be accessible

Read over this guide

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by ritchie888 on 2012-09-10
Sorry, my mistake, that's what I meant, made an edit. 

I've read through that tutorial, thanks for linking. Seems perfect for if I decide to for with the software method, but piecing together the right methods for now.

Cheers.

---

