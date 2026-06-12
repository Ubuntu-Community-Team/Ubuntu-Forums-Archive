---
title: "Lucid Lynx: ext3 or ext4 ?"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by mod-jkl on 2010-04-25
Hi,

I will install Lucid Lynx when it will be available in a couple of days. What is the best choice for the file system, ext3 or ext4 ?
I'm looking for something completely stable for this pc, so maybe ext3 is still "better" ?

When a previous released  came out(don't remember if it is Jaunty or Karmic), Linus Torvalds said that ext4 was not ready for production, did he changed his mind or said something else about ext4 since ?

Any information that could help in this choice is appreciated.

Thanks for any help

---

### Post by zvacet on 2010-04-26
Since Karmic Ubuntu use ext4.

---

### Post by mod-jkl on 2010-04-26
Yes, but we can read on this forum, that on Karmic, there still was some stability problems with ext4 , so, who knows for Lucid..

---

### Post by gradinaruvasile on 2010-04-26
I used ext4 in Xubuntu and had some problems with it...
I came to the conclusion that its is good for secondary partitions, but IT IS NOT as the system partition - i lost panel/configuration settings a few times and some smaller files.
The biggest problem is that sometimes the system just wouldnt boot (some file system corruption even once when i restarted it  with the reboot command), and a forced fsck was needed.
Using it as a data partition its ok - i never had problems with it this way (but i did change the OS to Debian in the meantime). It feels faster and uses less CPU than ext3 - but as far as stability goes i am not so sure. In Ubuntu i had unpleasant surprises with it.
Id say stick with ext3 for the main system partition.

---

### Post by necromonger on 2010-04-26
I use ext 4 on my sata drives with no problem.

---

### Post by mod-jkl on 2010-04-26
> **gradinaruvasile said:**
> I used ext4 in Xubuntu and had some problems with it...
I came to the conclusion that its is good for secondary partitions, but IT IS NOT as the system partition - i lost panel/configuration settings a few times and some smaller files.
The biggest problem is that sometimes the system just wouldnt boot (some file system corruption even once when i restarted it  with the reboot command), and a forced fsck was needed.
Using it as a data partition its ok - i never had problems with it this way (but i did change the OS to Debian in the meantime). It feels faster and uses less CPU than ext3 - but as far as stability goes i am not so sure. In Ubuntu i had unpleasant surprises with it.
Id say stick with ext3 for the main system partition.

Yes, I will use ext3, don't really know how is ext4 but ext3 is sure rock stable.

---

