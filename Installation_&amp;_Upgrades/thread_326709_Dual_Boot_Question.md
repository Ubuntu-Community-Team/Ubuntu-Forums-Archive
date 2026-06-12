---
title: "Dual Boot Question"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by peebs on 2006-12-28
Hi,

This is a bit of a "noobie" question, so I appreciate your help.

I'm currently running Win XP and I plan on completely formatting my system and installing Windows XP and Ubuntu for a dual boot. Are there any detailed tutorials on doing a dual boot from a fresh format?

I understand that I am to make at least (3) partitions: Windows XP, swap, and Ubuntu. Is it recommended that I make additional partitions for, say, a media drive. And if so, would that media drive be visible on both boots?

I apologize for such rudimentary questions. 

Thanks.

---

### Post by K.Mandla on 2006-12-28
[This]("https://help.ubuntu.com/community/WindowsDualBoot") one is pretty good. There are a lot out there. ;)

---

### Post by K.Mandla on 2006-12-28
> **peebs said:**
> I apologize for such rudimentary questions.
No need to apologize! You're welcome to ask any and all questions you have here. :D

> **peebs said:**
> I understand that I am to make at least (3) partitions: Windows XP, swap, and Ubuntu. Is it recommended that I make additional partitions for, say, a media drive. And if so, would that media drive be visible on both boots?
Basically what happens is, you install Windows like you normally would, saving some space on the disk for Ubuntu. 

When the Ubuntu installer sees unpartitioned space, it will automatically set it up for itself -- creating the other two partitions you mentioned: Ubuntu (system area) and swap (like a paging file).

If you want a "shared" area between the two, you can partition off a part of the space on your drive and make it accessible to both systems. It will need a certain file system -- FAT32, although NTFS is readable (and writable, really) -- and there's a little legwork to making it available to Ubuntu.

---

### Post by peebs on 2006-12-28
Thanks for the quick replies!!!

I have no problem with legwork in regard to getting a shared drive to work properly, but is there a preferred way to share files between operating systems? I imagine its a common need.

---

### Post by K.Mandla on 2006-12-28
From my experience, a single FAT32 partition is the easiest way to get the job done. I set up a few machines with Windows at the front, then a shared FAT32 slice and finally Ubuntu at the outside. 

Both Ubuntu and Windows can read and write to FAT32, so it's a common language, so to speak. Reading NTFS is also possible from a default installation, but at the last I heard, writing to NTFS was still a new thing. I never needed to write to NTFS, so I can't vouch for it.

Another thought: If you have an extra drive, you might consider installing Windows on one and Ubuntu on the other ... rather than playing games with partitions. And if you had space for a third drive, you could set that as the common meeting ground for the two.

---

### Post by peebs on 2006-12-28
I have 2 hard drives: a 200 gig and an 80 gig, so I assume the 200 gig will be partitioned in some manner. Is it possible to have the swap on some portion of that and keep the 80 gig in tact for, say, the Windows boot.

I'm just contemplating which drive might get filled up quicker (but thats neither here nor there). I'd ultimately like to make Ubuntu my primary operating system, but as I do a lot of Photoshop and 3D work (XSI), I may have to concede to Windows.

But, if I format both drives for FAT32, they should be accessible to both OS's? Or was your point about a "shared slice" in regard to that shared media drive I was talking about?

Thanks.

---

### Post by K.Mandla on 2006-12-28
> **peebs said:**
> I have 2 hard drives: a 200 gig and an 80 gig, so I assume the 200 gig will be partitioned in some manner. Is it possible to have the swap on some portion of that and keep the 80 gig in tact for, say, the Windows boot.
Sure. In general Ubuntu doesn't need nearly the space Windows wants. You can get by on a pure Ubuntu installation on a partition as small as 2Gb, with swap space as small as ... well, as small as the amount of memory as is available in your machine (which is just a good rule of thumb).

> **peebs said:**
> I'm just contemplating which drive might get filled up quicker (but thats neither here nor there). I'd ultimately like to make Ubuntu my primary operating system, but as I do a lot of Photoshop and 3D work (XSI), I may have to concede to Windows.
If it were me, I would put both Windows and Ubuntu on the 80Gb drive, and build the entire 200Gb as shared space. I think that simplifies things in a way, even if it's just on a mental level. 

> **peebs said:**
> But, if I format both drives for FAT32, they should be accessible to both OS's? Or was your point about a "shared slice" in regard to that shared media drive I was talking about?
Yes, to both questions. Since both Windows and Ubuntu can read and write FAT32 natively, you shouldn't have any problems setting up both operating systems. Ubuntu (unless I'm mistaken ... it has been a while since I used FAT32 under Linux) should detect it on installation and automatically add it to your system profile.

> **peebs said:**
> Thanks.
My pleasure. :-D

---

