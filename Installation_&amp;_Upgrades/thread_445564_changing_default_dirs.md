---
title: "changing default dirs"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Eagleon on 2007-05-16
Hi everyone,

I don't know if this is even possible, but how would I go about changing the default paths of major folders in linux? I am quite new so I don't know much. Let me explain a but better. I plan to partition my drive like so:

8 GB Windows NTFS
8 GB Linux EXT
2 GB Linux SWAP
82 GB Shared NTFS

The shared partition is NTFS since windows can't access ext, and linux can still access ntfs. What I usually do when  install windows is go to regedit and change the path for my documents, program files, application data (and so on) to point to the shared partiton. I do this because windows is very unreliable and can get damaged anytime. My question is, could I possibly do the same with linux. In linux, my motive is different. It is not because it is unreliable, but because stupid windows can't read ext. It is too tedious to keep moving files back and forth, and I would really like it if there was a way I can have my /home folder in the shared NTFS partition somehow. Also, when I install something using synaptic, I would like the programs to be installed on the shared folder as well to save the Linux partition from getting too big. Since I am still new to linux, I install all kinds of software to experiment (our of curiosity). 

Thank you for taking the time to read this post, and I would really appreciate any advice you can give. I assume that what I am asking is not even recommendable, but any suggestions on how to get around this problem would greatly appreciated. Thank you once again (in advance).

Eagleon

---

### Post by deanjm1963 on 2007-05-16
windows indeed can access ext3, there's a driver for it [http://www.fs-driver.org/]("http://www.fs-driver.org/") . Linux won't install programs onto NTFS as linux cannot modify permissions on NTFS, sure, it can "read and write", but I wouldn't be too trusting as "even though it's fairly stable" NTFS is not a linux file system.

You'd be better off having a FAT32 parttition to share data which both OSs can read and write too natively.

---

### Post by Eagleon on 2007-05-16
thank you for the link and the advice deanjm1963. I never knew about this driver... how awesome! I agree with you about not trusting NTFS too much. I am not too fond of FAT32 either, so I think I will just install the driver you suggested. That will solve the problem, and I can install linux on the big partition.

---

