---
title: "[OT] Does anybody know what GPT Labels are"
date: 2009-01-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-08
Hi all, 
 Yesterday I came across something known as GPT Label. 

Seems to be part of intel EFI (BIOS) thing. Found a wikipedia page on the same. 

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Has anybody any experience and shed some more light on the matter performance-wise or anything.

---

### Post by MaX on 2009-01-08
> **ShirishAg75 said:**
> Hi all, 
 Yesterday I came across something known as GPT Label. 

Seems to be part of intel EFI (BIOS) thing. Found a wikipedia page on the same. 

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Has anybody any experience and shed some more light on the matter performance-wise or anything.

Am I the only one getting sick of these OT posts from ShirishAg75???
What does this have to do with Jaunty in any way?

The rule of thumb is, if it's NOT On topic then DON'T post it...

---

### Post by ShirishAg75 on 2009-01-08
It actually is part of the larger picture. I read somewhere that libparted (which is one of the depends on ubiquity) is going to have support for GPT label hence need to know what it is. 

Also want to know how people feel about it so when making a purchase decision (for a motherboard) should one go for EFI based mobo or not need to know.

So this is not just for jaunty but jaunty and going forward/beyond that.

---

### Post by plun on 2009-01-08
Well... I dont find it OT and it keeps our brains working...:D

GPT is something from Intel and MAC/EFI as I understands it...

[http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)

> Every GPT-formatted disk is supposed to have an EFI System Partition, and Apple’s tools create one at the beginning of the disk. However, Mac OS X doesn’t actually use it; the EFI System Partition is completely empty on a standard Intel Mac. Apple has added a HFS+ file system driver to its firmware, and the firmware boots Mac OS X directly from the partition it is installed on.

Also see above; Mac OS X can boot from a MBR-only disk with no trace of an EFI System Partition.

There is still some uncertainty about firmware updates, though. So far no one has investigated how they work in detail, and some people believe they require the EFI System Partition to be present. 


I am waiting for gparted which also now supports EXT4 (and GPT)

---

### Post by cariboo on 2009-01-08
Macintoshes use EFI (Extensible Firmware interface) as a replacement for the BIOS, so unless your using a mac, I would worry about it.

Jim

---

### Post by MaX on 2009-01-08
I still don't see the point of your post?
Will libgparted have this support in Jaunty (source)? If so then this might be On Topic, but nothing is mentioned in the original post about libgparted or it's support. If not, then this does not belong in Jaunty discussion. Could we focus on actually testing stuff in Jaunty intstead?

EFI is not available unless you are on a new Mac or a IA-64 system.
If you found the Wikipedia page on it you could have google:ed it and found out that it's pretty much a non issue.
Sure some MSI motherboards have EFI on them but you could have found out that by searching the web.

---

### Post by ronacc on 2009-01-08
Max he is asking for information and clearly lableled the post as Off Topic , I sometimes ask OT questions here myself because I know that the people who are most likely to know what is going on are to be found here .

---

### Post by |{urse on 2009-01-08
GPT = GUID partition table

GPT is usually used on large arrays > 2tb. I've typed that command "mklabel gpt" so many times i might as well get it tattoed on my forehead.. hey i think i will!

So far as the recent bug, I dont know anything about that.

---

### Post by MaX on 2009-01-08
> **ronacc said:**
> Max he is asking for information and clearly lableled the post as Off Topic , I sometimes ask OT questions here myself because I know that the people who are most likely to know what is going on are to be found here .

Well then you are no better... Then we need another forum, "Computer questions of a generic type" or something.

There's so much junk in the Development forums and so many doublet threads it's hard to keep track of what's important. Having clearly marked off topic posts doesn't help.

I'm jumping on this thread because in the last 4 days I saw 3-5 posts from the same guy asking different off-topic questions that are more suitable for a IRC channel then a forum.

I'll stop replying here so this post can dissapear from the first page at least.

---

### Post by Rocket2DMn on 2009-01-08
Thread Closed.  For future reference, this part of the forums is for discussions about Jaunty development and testing, please take other questions to the primary support areas of the forum, and off topic stuff to the Community Cafe.

---

