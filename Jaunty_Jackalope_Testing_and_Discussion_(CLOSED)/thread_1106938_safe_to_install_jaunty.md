---
title: "safe to install jaunty?"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2009-03-26
is it stable enough to go ahead and install it now?  and if i do can i upgrade to the full release when it comes out in the software channel?  i just reinstalled intrepid yesterday and don't want to get all my customizations in just to upgrade in a month which i plan on formatting to ext4 anyway and losing everything

---

### Post by skymera on 2009-03-26
I've been running Jaunty for over a month, been stable and fine.

You can do a straight upgrade now i believe.
Go to:

System > Administration > Software Sources
On updates, choose all distribututions not just LTS.

Now:
```
 update-manager -d 
```

---

### Post by taavikko on 2009-03-26
always use /home in separate partition, so you won't lose any data/custom settings.

But for using Jaunty as only OS, I wouldn't suggest to do.
When basic skills are more toned, I would advise to do so, to test and report bugs.

ps. these posts, belong to Jaunty dev subsection in the forums.

---

### Post by mamamia88 on 2009-03-26
so if i install alpha 6 and the beta releases after i install it i can upgrade to it?  also, the sticker on my laptop says amd 64 but it only has 2gb ram should i still use the i386 version?

---

### Post by mamamia88 on 2009-03-26
anyone?  this is important if i install alpha can i upgrade to the full release of jaunty when it hits the software channel or will i have to download jaunty and burn the iso and install all over again?

---

### Post by jerrylamos on 2009-03-26
> **mamamia88 said:**
> so if i install alpha 6 and the beta releases after i install it i can upgrade to it?  also, the sticker on my laptop says amd 64 but it only has 2gb ram should i still use the i386 version?

Best bet is to install in a different partition so if it doesn't work (see all these postings with problems people have....) you can still boot whatever you have.  I can do a fair amount in a 5G partition.

Too many people have just one running partitin, do an "upgrade", and wind up with a dead system.  Look at the Install & Upgrade forums.  They have to salvage what they can with CD Live.

I tried sharing home partitions but it didn't work for me since there's lots of hidden setup files in "home" that relate to a particular version.  I have 2 (at least) boot partitions and a third partition will all my data in it which I access through "places".

No, it's not "safe", but then from my experience with Intrepid etc. neither is the first final release.  There tend to be a few final "gotcha's" which get fixed when tons of people report the same problem.

Hence two bootable Ubuntu (Xubuntu, Kubuntu, ...) partitions.

Cheers, Jerry

---

### Post by taavikko on 2009-03-26
> **mamamia88 said:**
> anyone?  this is important if i install alpha can i upgrade to the full release of jaunty when it hits the software channel or will i have to download jaunty and burn the iso and install all over again?

While using search function you would have founded the answer.

But yes, by apllying updates you always have the latest version what repos have to offer.

---

### Post by mamamia88 on 2009-03-26
thats the thing i have debian, xp, and intrepid running on my machine.  since i installed all 3 over again last night after a trial with fedora i didn't care for i figured i'd just install jaunty instead of losing all my personalization.  so i should create a root partition, a home partition, and if i create a usr partition all my installed programs will still be installed?

---

### Post by KCG102282 on 2009-03-26
> **mamamia88 said:**
> so if i install alpha 6 and the beta releases after i install it i can upgrade to it?  also, the sticker on my laptop says amd 64 but it only has 2gb ram should i still use the i386 version?

Yes you can. As far as using 64-bit that is up to you.

---

### Post by andrewabc on 2009-03-26
Wait until Beta is released and install from that.
I would not recommend getting alpha 6 (700mb download), then installing and having to download/install many updates to get up to date. More chance of problems occuring.

yes once you install beta (or alpha or RC), as long as you keep up to date with updatesyou will end up with final.

For example, lets say you get alpha 6, install hundreds of updates/mb, then say next week something happens and your install breaks and you need to format/install agin. You'll end up either installing from alpha6, or downloading beta.

Wait until beta released, it will be much easier than installing from alpha 6.

And if you are asking if it is safe to use jaunty, it is not for production, but assuming you just formatted and installed Intrepid, I'm guessing you have no important files on computer (are backed up), if so, using jaunty would be a good thing since nothing worth losing.

---

### Post by xebian on 2009-03-26
Looks like the beta release builds were done 2 days ago.  So if you updated since then you have the beta release already.

---

