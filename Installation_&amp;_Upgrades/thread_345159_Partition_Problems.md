---
title: "Partition Problems"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by FeNoM on 2007-01-23
Well, I decided to dual-boot into Linux along-side Windows XP, only problem is that I already have 3 Partitions on my hard drive,an XP partition, XP recovery partition, and another partition that I don't know. I go to create [manually because I don't have the other option and don't want to start from scratch] a partition and set aside 40 GB for the 3 other partitions I have to create [root,swap, and boot]. 

After setting aside the space I go to create the Swap partition at 2GB and its successful. I go to create the Boot at 500MB and I get an error that I cannot have more than 4 Primary partitions. Can I get rid of the other two, but then again, I know  I don't need the recovery but don't know about the 3rd partition, I don't know what's on it.

Can I override this? I just need some help. Hopefully some of you can help on my journey to dual boot!

---

### Post by ucsdrake on 2007-01-23
what you can do is create whats called an "extended Partition" (vs a primary partition like you were creating) this allows you to continue partitioning like you planned but all within the extended partition

im not entirely sure on what organization/location would be the best as to the root, boot and swap to be fit in the extended partition vs which to have as a primary ... ill leave that for somebody else to answer seeing as im not sure on the finepoints of linux operations

and im guessing youre third partition from windows would be its boot partition (is it small and on the right side of the bar?) ... look if it has any flags

---

### Post by FeNoM on 2007-01-23
Yup, small partition. Well, would having an extended partition affect the way Linux operates or the way Windows operates in any way?

---

### Post by ucsdrake on 2007-01-23
to my knowledge, none at all ... its just a way to get more partitions involved in the process but id wait till some more information comes in just to geta second opinion on the matter ... more knowledge can only ever help

---

### Post by FeNoM on 2007-01-24
I agree. Well, since you can only create one more primary partition, which one do you recommend using it for? Swap, Root, or Boot?

---

### Post by ucsdrake on 2007-01-24
i personally dont know enough to give you a decent answer (it would truthfully just be a guess) ... my advice is that if somebody doesnt respond here and the topic goes dry ... try in the Absolute Beginner Forum ... you might get a more helpful responce there!

---

